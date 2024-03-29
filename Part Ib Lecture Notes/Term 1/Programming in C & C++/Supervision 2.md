1. Arenas are a useful tool for amortizing allocated memory discovery, and have the side effect of potentially more efficient cache usage through the introduction of an array for item storage. I would use one when I have a data structure that may contain cyclic sections or sections where a given item is pointed to twice from another item (DAG) - in which case traversing the structure myself at the end becomes complex & error prone, and can result in memory leaks if not carefully thought through. Arenas trade-off complexity with memory usage, as we must allocate a large array of items (the size being the maximum number of items the program could use) to eventually deallocate. An example control flow would be creating a graph, every time I create a node I add it to the arena (wherein we already specified the max possible number of items) incrementing the current value in the arena - then when finished with my data structure I free the arenas elements array and free the arena itself.
2. In mark and sweep garbage collection we store an list of "root" nodes (items that are alive, and we'd like to keep alive) and an list all nodes (these may be the lists). In the mark phase we iterate through all the root nodes, and mark all nodes reachable from each root node (i.e. depth first exploration, stopping when we hit a marked node). Then in the sweep phase, we step through our list of all the nodes and free any unmarked nodes and unmark any marked ones. When we next run the garbage collector the nodes still alive will form our roots.
    - a.) A conservative garbage collector is one who scans the execution stack, and upon finding a value that **looks like **a pointer to the heap - if there is an object at that pointer, the collector must mark it. This conservative estimation is that this is a pointer to the heap and not (say) an integer value. This is necessary many reasons, including:
        1. C lets you easily convert from values to pointers, so we can't know if in future the programmer will use that int as a pointer to an item in heap memory.
        2. The garbage collector should **never **alter the execution of the code, and storing extra blocks of useless memory is better than deleting a useful block. Especially considering that if the value on the call stack is not a pointer, it is likely to change at which point the memory can be freed. 
    - b.) Garbage collection solves the issue of cyclic data structures that reference counting cannot - under reference counting, two cyclic items pointing to each other can maintain a pointer count of 1 each even if there is no way of accessing either item (all pointers to those items has been removed) - thus these marooned items cant be freed resulting in a memory leak. Garbage collection stores all the nodes, and will find these items to be unmarked in the sweep phase - thus they will be freed.
3. Show how a struct of arrays performs better than an array of structs when traversing the elements of the form ```c
struct entry { int id; double val; };
typedef struct entry Entry;

struct struct_of_arrays {
	int *id_array;
	double *val_array;
};

Entry *array_of_struct = malloc(sizeof(Entry) * NUM_ITEMS);

struct struct_of_arrays Struct_of_Arrays;
Struct_of_Arrays -> id_array = malloc(sizeof(int) * NUM_ITEMS);
Struct_of_Arrays -> val_array = malloc(sizeof(double) * NUM_ITEMS);
```
    - For simply iterating through the array of struct, we have an int of size 4 bytes and a double of size 8 bytes - this will then be padded to size 16 bytes. So we can fit 4 entries into a single cache line before getting a miss (whether we're storing an int & a double or only an int/double) - alternatively if we iterate through the id_array and then the val_array, we first have 4 byte ints to iterate through - resulting in 16 items before getting a cache miss - and secondly 8 byte items, resulting in 8 items before a cache miss. 
    - $\text{array of structs}: \frac{n}{4} \text{ cache misses}$ 
    - $\text{struct of arrays}: \frac{n}{8} + \frac{n}{16} = \frac{3n}{16} \text{ cache misses}$ 
    - So as $\frac{3n}{16} < \frac{n}{4} = \frac{4n}{16}$ we'll have less cache misses in our second solution, and as cache misses are hundreds of times more costly than arithmetic operations - our struct of arrays will perform better.
4. Describe loop blocking and when it's useful:
    - Loop blocking is a technique for deconstructing accesses of large contiguous data structures into smaller chunks which can be stored in cache lines. The first access of each chunk will result in a cache miss, but subsequent accesses wont. In short it attempts to introduce spatial locality of data, for fast accesses.
    - The technique is useful when a given array access scheme jumps around a lot, and does not return to a chunk of memory for a long time (at which point the cache line can have been cleared). Alternatively, your method of jumping could cause conflicts within the cache and force eviction of prior cached lines. In general, loop blocking is useful for items with poor spatial locality.
5. [1998 Paper 6 Question 6](../../../y1998p6q6.pdf.md)
    - a.)
        - Memory corruption 
        - Hard to read programs 
        - Security liability
    - 
        - Low level control
        - 
    - b.)
        - Forgetting to deallocate sensitive data?
        - Memory leaks
    - 
6. [2010 Paper 3 Question 6](../../../y2010p3q6.pdf.md) 
    - a) 
        - ```c
typedef struct node* Node;
struct node {
    int value;
    Node xor_pointer;
};
Node head;
Node xor_addresses(Node a, Node b) {
    return (Node) ((long long)a ^ (long long)b);
}
void add_value(int value) {
    Node new_node = malloc(sizeof(Node));
    new_node->value = value;
    new_node->xor_pointer = head;
    head->xor_pointer = xor_addresses(head->xor_pointer, new_node);
    head = new_node;
}
Node get_next(Node prev, Node current) {
    return xor_addresses(prev, current->xor_pointer);
}
void traverse() {
    if (head==NULL) return;
    Node current = head->xor_pointer;
    Node prev = head;
    printf("%i  ", head->value);

    while (current != NULL) {
        printf("%i  ", current->value);
        if (current->xor_pointer == 0)
            break;
        Node temp_prev = current;
        current = get_next(prev, current);
        prev = temp_prev;
    } 
    printf("\n");
}

void delete(int value_to_del) {
    if (head==NULL) return;
    Node current = head->xor_pointer;
    Node prev = head;
    
    if (head->value == value_to_del) {
        if (current->xor_pointer != 0) {
            current->xor_pointer = get_next(head, current);
        }
        free(head);
        return;
    }

    while (current != NULL) {
        if (current->xor_pointer == 0) {
            if (current -> value == value_to_del) {
                prev->xor_pointer = 0;
                free(current);
                return;
            }
        }
        if (current -> value == value_to_del) {

            Node next = get_next(prev, current);
            Node prev_prev = xor_addresses(prev->xor_pointer, current);
            prev->xor_pointer = xor_addresses(prev_prev, next);
            Node next_next = xor_addresses(current, next->xor_pointer);
            next->xor_pointer = xor_addresses(next_next, prev);
            free(current);
            return;
        }
        Node temp_prev = current;
        current = get_next(prev, current);
        prev = temp_prev;
    } 
    printf("Node not found to delete\n");
}

``` 
        - b.)    Comment on this form of linked list. Consider the comparative speed, memory overheads, maintenance and other advantages or disadvantages of the XOR doubly-linked list approach when compared with an approach that stores both previous and next pointers  
        - 
        - In this form of doubly-linked list, each node takes up less space - while before they store two pointers and a payload now they store only one , resulting in less overall memory usage of the new data structure. (16 bytes vs 24) For large lists, one list being two thirds the size of another while accomplishing the same thing could be important.
        - However, if you want to hold specific nodes to edit later - you need to hold that node **and **the previous node if you want to be able to traverse from your node and edit preceding nodes - this makes it harder to maintain, as management of individual nodes is more complex. Additionally, traversing the list is more expensive in the XOR doubly-linked list as we must compute an XOR every time (which is admittedly a relatively cheap operation). 
        - You could make the argument the XOR doubly-linked list is more secure, as you can pass your node value to another function safe in the knowledge it cannot destroy any other of your nodes as it will have no way of traversing to them. 
7. [1996 Paper 5 Question 5](../../../y1996p5q5.pdf.md) :
    - a.) Pre-processor macros and conditional compilation:
        - ```c
#define BIT64 1

#if BIT64==0
#define BIG_INT (64*1024*1024)
printf("%i", BIG_INT);
#else
#define BIG_INT (1024*1024)
#endif

// This defines a macro BIT64 set to 1, and chooses different definitions of BIG_INT depending on the value of said macro
``` 
    - b.)
        - ```c
char t = 'a';
char *p2 = &t;
int *res = (int*) p2;

// We created t, which holds the a character. Then we instantiated a char pointer to t. Then we created an int pointer res, and cast the char pointer to an int pointer.
``` 
    - c.)
        - ```c
// This is a single line comment
/*
	This is a multi-line comment
	!!!
*/
``` 
    - f.)
        - ```c
jmp_buf current_env;    
int sam = 0;
int val = setjmp(current_env);
printf("%i\n", val);
longjmp(current_env, sam++);

// This code infinitely loops printing 0, 1,2,3...
// setjmp copies the PC and stack pointer into the jmp_buf current_env, then we print sam and finally we longjmp back up to int val = setjmp(current_env); val will then be overwritten with the value of sam+!
```
    - g.)
        - ```c
unsigned int sam = 3;
switch (sam) {
    
    case 0:
        printf("Sam less than 2");
        break;
    case 1:
        printf("Sam less than 2");
        break;
    default:
        printf("Sam more than 2 ;( ");
        break;
}
// if the unsigned int sam is 0 or 1 we print "Sam less than 2", otherwise we print "Sam more than 2 ;( ".
// In this case we'll print the latter, as sam is 3. Each constant case is checked against the value in the switch()  braces and a case is selected. 
// The breaks ensure the default case doesn't always run.
``` 
8. [2014 Paper 3 Question 3](../../../y2014p3q3.pdf.md)   :
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zB0WVJroIQK0RkHQzho8zvjIfCkmXtlmIL3jLz1ZOLw0MoLHOFDLFaEUh1PaKLG-bc64iVhJIajoLCoCy2b996jK4MoffBw6nDR-nU2P_UYxEe8qrzNow4mU46s9QqRk.png)
    - ```c
char revbits(char to_reverse) {
    int working = (int) to_reverse;
	int result;
    for (int exp=7; exp>-1; exp--) {
        if (working > 1<<exp) {
            working -= 1<<exp;
            result += 1<<(7-exp);
        }
    }
    return (char) result;
}
``` ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4EncOulylcP3ibS2i2YvFWOnzfLIxKEKnPaaiubqq7GDBEapF3kAEAU-uD7XBSla7UjDwumB_HkKu4FrEu1z6Zt9XdJ1EG6EnsNg07bjh9XbeYN6QInE3JQbCpm6AdPo.png)
    - ```c
void revbytes(char *ls, int num_bytes) {
    int left = 0, right = num_bytes-1;
    while (left <= right) {
        if (left == right) {
            ls[left] = revbits(ls[left]);
            break;
        } else {
            char temp = ls[left];
            ls[left] = revbits(ls[right]);
            ls[right] = revbits(temp);
            left++, right--;
        }
    }
}
``` ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5CvOkCE8ymJEeAFOsAjUVCQ44LCbCUtbJYWKdAgIN0OS8u2Wsy8ILFqk3zp-DPTbnJzLqlTcGVHd5dTnEuRc-4ql_tRA0umkx1Z9W4pm4vhHkDiAUYf7cgRiqiUI5SfJ.png)
        - The problem here is the file is left open after the result is returned, we should change the block to:
        - ```c
if (...) fclose(p); return ERR_MALFORMED;
``` 
9. [1995 Paper 5 Question 5](../../../y1995p5q5.pdf.md)  
    - This is an attempt at an implementation of quicksort.
    - ```c
typedef unsigned long int thing;
// Bad unilluminating variable name
``````c
 #define swap(p,q) v = p; p = q; q = v;
 // the type of v is not defined, this will result in an error.
```
    - ```c
		/**********************
int i, j; * Declare variobles! *
thing v; **********************/
// int i,j and thing v will be commented out here. Also incorrect spelling of variables
``` 
    - ```c
i = left, j = write;
// i & j are not given types
``` 
    - ```c
 while (a[++i] < v};
 // Wrong ending bracket, should be  while (a[++i] < v) 
```
    - ```c
while (a[++i] < v};	
while (a[--j] >= v);
if (i < j) swap(a[i], a[j]);
else break;

// I believe what they intended was:
while (a[++i] < v} {
	while (a[--j] >= v) {
		if (i < j) swap(a[i], a[j]);
		else break;
	}
}

// What they achieved simply repeatedly increments i until a[i] >= v, and repeatedly increments j until a[j]<v and then swaps a[i] & a[j]

// ALSO these should be a[i++]... and a[j--]... . Otherwise we dont test the initial values of i & j.
``` ```c
 write would more sensibly be named right
```
- 
- Questions from lectures:
    - In the lecture on reference counting, the lecturer builds a binary tree using:
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/crzic95YRyiryiMHGIrmxmqkDggUe_2KbJnaftk-5YUTWrhbDsP0rUPfufcy8XmrHUAHD9C9DPDpkqALR3EPC4UDY5wVP-WUnHm3WYEhxJX-Ea59BIvdWIrXP6XKJJO9.png)
    - But wouldn't this mean, If I edit a value on the tree (other than the root) I'm actually editing two? Given that both left & right point to the same node. Sure the tree is build, but it can't be used.
- 
- 
- $$\text{speedup}(n) = n(1-B)+B$$ 
