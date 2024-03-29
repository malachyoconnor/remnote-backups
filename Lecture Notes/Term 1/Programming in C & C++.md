- 
- Supervision 3
    1. ** 2015 Paper 3 Question 1:**   
        - a.) It encourages the compiler to immediately evaluate the function inline. However, it gives no guarantee that the compiler will actually do that. Can waste space if an inline function is reused many times, less space efficient than creating a stand alone function to be run.
        - b.) ```cpp
 #include <tgmath.h>
 int receive_int() {
    unsigned int result = 0;
    for (int i=31; i>=0; i-- ) {
        result += receive_bit() * pow(2, i);
    }
    return result;
}
```
        - c.) ```cpp
template <class T, int len>
T receive(void) {
    T result = 0;
    for (int i = 0; i < len; i++) {
        T bit = receive_bit();
        result += bit * pow(2, i);
    }
    return result;
};

ans = receive<short, 8>;
ans = receive<unsigned long,32>;
``` d.) 
            - Line 6: buf is a value on the stack, thus the value returned will be lost once the function returns.
            - Line 4: fuel is never initialized
            - If Message is not 1 or 2 the function will not return a value, when it's supposed to return a char
            - Line 5: THRUST will overrun buf, as buf doesn not have space for the /0 that ends the string
    2. **2015 Paper 3 Question 2:**
        - a.) The differences between C pointers and C++ references. [Hint: Consider issues of syntax, initialisation, mutation and safety in your answer.] [5 marks]
            - Pointers are created using the * syntax, while references use the & syntax: 
            - ```cpp
int x[] = {1,3,5,7};
int* ptr = &x[0];
int& ref = x[0]; 
```
            - References act as aliases to the data item in questions, meaning they can only affect the value they are initialized to reference - references cannot be changed to reference a different data item. On the other hand pointers act as an address to the data item, an address which can be changed to point to somewhere else in memory:  
            - ```cpp
ptr++;
printf("%i ", *ptr); // outputs 3 as ptr is now pointing to the second array item
ref++;
printf("%i ", ref); // outputs 2, as this incremented the 1st array item 
```
            - Where references point to is an immutable feature, because can only change the value they point to they are much more safe than pointers - arithmetic of pointers can be done in error, resulting in the changing of arbitrary bits in memory.
            - ```cpp
ptr+=10; // pointer now points to an arbitrary place in memory
printf("%i ", *ptr); // unkown output
ref+=10; // Increments the 1st array value by 10
printf("%i ", ref); // outputs 12 
```
        - b.) extern "C" {} tells the compiler that the enclosed code should be linked as C, not C++. Declaration and definitions can then be grouped inside the scope. This has the limitation when combined with C++ name mangling, i.e. C++ uses name mangling to allow for default arguments and overloading for functions - this gives each possible combination its own symbol name. If the C function name clashes with an overloaded function, a compile time error will occur. 
        - c.) Implementation defined behaviour means the creators of the compiler have documented the behaviour of the compiler when facing certain incorrect code, and the compiler will adhere to that behaviour. Unspecified behaviour means the C compiler can do whatever it wants and there is no specified behaviour. An example of implementation defined behaviour is the size of all data types char, short int etc. Examples of unspecified behaviour include how inline functions are handled, the order that operators like ++i i++ are evaluated when combined. ^^This loosely specified behaviour allows for more freedom for optimizations by the compiler.^^ - not sure about this
        - d.) Interactive debuggers give you a large range of tools for fast debugging, including stopping the program if assert conditions are not met, get the value of variables during running, stepping through the program, getting the trace of function calls.  A breakpoint gives the line of code where application will pause, a watchpoint allows you to set a data item such that the program will pause if it changes. The symbol table keeps track of the location of variables and stack offset for function callstack inspection.   
    3. **2013 Paper 3 Question 3:** 
        - b.) ```cpp
 class T {
    const int n;
    public:
    T (int n=0) : n(n) {
        printf("%i", n);
    }

    virtual ~T () {
        printf("%i", n);
    }
};
```
        - Fields and constructors cannot have the virtual tag. Virtual destructors are useful for when a class is derived from, and when the static class varies from the dynamic class with a non-virtual destructor undefined behaviour can occur. 
        - ii.)   T Objects are allocated to the heap using new, and removed using delete ```cpp
 T value = new T(1);
 delete value;
```Delete runs the destructor and then deallocates from the heap. New allocates to the heap and runs the constructor. Stack constructors are run when a scope is entered, and destructors are run on exit. Static store is used by writing static C x. Virtual is essential for destructors when a class is derived from. Try finally ensures the finally block is always run at the end of a block, similarly stack allocated objects run their destructors when they go out of scope.
    4. **2012 Paper 3 Question 3:**
        - a.) 
            - i.) What is the difference between a local and global variable in C? (Consider variable scope, storage and initialisation.)
                - A local variable is one who can only be accessed within the current scope, after the end of the scope the allocated memory is removed. 
                - A global variable is one who can be accessed anywhere in the program, they are initialized to zero and consume storage throughout the program.
            - ii.) What are the properties of a static member variable in a C++ class?   
                - A static member variable only has one instance of the variable, rather than one instance per variable. 
        - b.) 
            - i.) The section of memory the pointer addresses can be changed using pointer arithmetic: ```cpp
 int * p1, p2; // integer and int pointer declared not two int pointers
 
 int sam = *p1; // pointer uninitialized 
```
            - ii.) A pointer can be used to point at an array, and you can use array syntax with pointers - however a pointer is a variable (you can reassign it), while an array name is not.
        - d.) 
            - i.) void * can point to anything, any data item. ```cpp
void sort(void *arr, int nitems, int size, bool (*compar)(const void *, const void*));
```
            - ii.) void * has no type checking in C, C++ helps this using template functions:  ```cpp
template <class myType> 
myType GetMax (myType a, myType b) {  
	return (a>b?a:b); 
}  
```
        - e.)
            - i.) We can "copy" instances using simple assignment, meaning all the values are copied - however if some of the values are pointers this may not be the desired behaviour. Thus, a copy constructor could solve that problem by properly dealing with those items.
            - ```cpp
Dog::Dog(const Dog& old_dog) {
	bark = old_dog.bark;
	name = new char[5];
}
``` ii.) 
As in i.) when one class instance is assigned to another, variables are overwritten and this behaviour may not always be desired.
```cpp
Test& operator = (const Test &t) {
    cout<<"Assignment operator called "<<endl;
    return *this;
} 
``` 
    5. **2009 Paper 3 Question 1:**  
        - e.) Pointer arithmetic is the manipulation of the pointer address, the main (good) use is to manipulate an array using pointers - however there is no bounds checking so precautions must be taken: 
        - ```cpp
int sam[3] = {1,2,3};
int *ptr = sam;

printf("%i", *ptr); // print 1
printf("%i", *(ptr+2)); // prints 3
``` 
        - d.) ```cpp
class dog {

    int age;
    const char* name;
    public:
    
    dog (int age, const char *name) : age(age), name(name) {
        printf("Constructor run");
    }

    void bark(char* msg) {
        printf("%s", msg);
    }

};

int main() {
    const char * name = "Apollo";
    dog* Apollo = new dog(5, name);
    Apollo->bark(name);
    return 1;
}
``` 
        - c.)  New and delete are features of the language that call an objects constructor or destructor - malloc() and free() are functions, and are not features of the language but are provided from a library. Malloc and free manipulate a large data structure (a heap) to allocate data for variables, while new and delete need not use this external data structure.
        - f.)   Catches take a single argument and allow for the escape of a code block to a predefined location if an error occurs```javascript
int main () {   
	try {     
		throw 10;   
	}   
	catch (int e) {     
		cout << "Exception number " << e << '\n';   
	}   
	return 0; 
}  
```
    - 
- Supervision 2
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
    5. [1998 Paper 6 Question 6](../../y1998p6q6.pdf.md)
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
    6. [2010 Paper 3 Question 6](../../y2010p3q6.pdf.md) 
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
    7. [1996 Paper 5 Question 5](../../y1996p5q5.pdf.md) :
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
    8. [2014 Paper 3 Question 3](../../y2014p3q3.pdf.md)   :
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/zB0WVJroIQK0RkHQzho8zvjIfCkmXtlmIL3jLz1ZOLw0MoLHOFDLFaEUh1PaKLG-bc64iVhJIajoLCoCy2b996jK4MoffBw6nDR-nU2P_UYxEe8qrzNow4mU46s9QqRk.png)
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
``` ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/4EncOulylcP3ibS2i2YvFWOnzfLIxKEKnPaaiubqq7GDBEapF3kAEAU-uD7XBSla7UjDwumB_HkKu4FrEu1z6Zt9XdJ1EG6EnsNg07bjh9XbeYN6QInE3JQbCpm6AdPo.png)
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
``` ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5CvOkCE8ymJEeAFOsAjUVCQ44LCbCUtbJYWKdAgIN0OS8u2Wsy8ILFqk3zp-DPTbnJzLqlTcGVHd5dTnEuRc-4ql_tRA0umkx1Z9W4pm4vhHkDiAUYf7cgRiqiUI5SfJ.png)
            - The problem here is the file is left open after the result is returned, we should change the block to:
            - ```c
if (...) fclose(p); return ERR_MALFORMED;
``` 
    9. [1995 Paper 5 Question 5](../../y1995p5q5.pdf.md)  
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
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/crzic95YRyiryiMHGIrmxmqkDggUe_2KbJnaftk-5YUTWrhbDsP0rUPfufcy8XmrHUAHD9C9DPDpkqALR3EPC4UDY5wVP-WUnHm3WYEhxJX-Ea59BIvdWIrXP6XKJJO9.png)
        - But wouldn't this mean, If I edit a value on the tree (other than the root) I'm actually editing two? Given that both left & right point to the same node. Sure the tree is build, but it can't be used.
    - 
    - 
    - $$\text{speedup}(n) = n(1-B)+B$$ 
- Supervision 1
    1. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/5x-kpFtSmurzNUmXPlR8GMTKt44S-pGI_uXQn-loC5FTlBbwH2KnTOZb_8vHNtz5Vc-B7ENcAojGyI83lmpHfPa1uVKKFQiiso5afgZZSAndShPRGx_1n1jctwLtBL13.png) 
        - 'a' is a char while "a" forms a string literal - e.g. an array of chars terminated with a null terminator \0.
    2. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Y7TUSDPht8rMMmjwyibGk-4zzDDtqFry6U0sB0wSGHN80olxqx8IhSL4w7q1B7AwdfL5s1F1G8LzJ8q7-K3oTPmuVAZMovFSPG6aKrPGL5mZ2dLldl2lZEglvvYQf7oj.png) 
        - Yes, it will terminate when j equals 5 (e.g. the 5th ASCII character) as long as the two chars were initialized to 0 (which is not guaranteed). This is because you can store integer values in chars, ranging from -128 to 127 for unsigned chars.
    3. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/dpZ64aPO1RH5e4EsS1UpUmsF6S1j8sYlwLx6vDShfHV1sW0kweO6ow9QUln0VP0NK6dzaTv2HQGT_siYVBxZQugXD5dBNPaOHMVYXAvK5T_8rvmGEmV0otOOn9oYFKxz.png)
        - ```c
#define SWAP(t,x,y) {\
    t temp = x;\
    x = y;\
    y = temp;\
}
```
    4. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/wnEQh3sjj-ggBtFu8O9dNmiI2bL6F-ycmM394KL46Q4W-zJ1YH1L8zb5AuhRQgO0yH7tmlkZoS4jhEaKhz0CZSQcIHphGvCgeGCD5LGCuKrC4Cx7S9oxORSzpGNZE18s.png) 
        - No, the i++ will be evaluated twice - meaning the x in the second line of the macro will differ from the x in the third line of the macro (unless the values of v[i+1] and v[i+2] are the same). Similarly, if f(x) changes when it's called twice we will be getting different indices of w.
    5. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/29dC0HQ66WGsn2vo69u4gNIJZt9N4FnfT5RwFJfM_G3BW7d5EhdsZOHsXWNjWacNu5zL96DZhIyb0C6NbtTEcqJ-TlSKnzxtwO9zn0fVU-ErJJFrKkkTJH3OY9HJb7no.png) 
        - ```c
#define SWAP(t,x,y) {\
    x = x - y;\
    y = y + x;\
    x = -x + y;\
}
``` 
    6. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/VjH7bsEoeEXOb-ZAO4st3yXVKrJqqTgta_w8kMyod9Oe22Y2SY3BN4_UwFKmCzzzfdD_XCnzJG4-JQsuy9qVOjbjp3QFCvNPX9JwYgL0iIb2bJSPIhuJLUjEDjsW6djw.png)
        - p[-2] means the value two items before the pointer, this is legal if p is a pointer inside an array - this works because arrays allocate a contiguous block of memory which we can simply step along (pointer-wise) to reach earlier array-items.
    7. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/6xCzQuVGM16QjzvbI4VY4CytzsorrFvjZX1148C4R1ovPU0H4YfSVTLPf1cagxhM-sD31wpTXg6cKaq74aQ609n_mIrRaPIb0Yvmv8tjBgN0IUPrbDjxPksgy8rh1VM-.png)  
        - ```c
char *strfind(const char *to_find, const char *to_search) {

    for (int i=0; i <= strlen(to_search) - strlen(to_find); i++ ) {
        int bookmark = 0;
        while (to_search[i+bookmark] == to_find[bookmark]) {
            if (bookmark == strlen(to_find)-1) {
                return to_search[i];
            }
            bookmark++;
        }
    }

    return NULL;
}
``` 
    8. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/GtHkEKbpOG6jIjweOng_l6W05H7Yu9StIWUwwxs9dLB2QzAVtBTakVMQh-pHkARbLFo5t3z56QsppajKkhummkk_929JjfaKqROSQEgcZnq0Z_E6z2HzmF_wMr1mqUGD.png) 
        - A const pointer to an int is a pointer that cannot be changed, e.g. it will always point to that integer. However, the integer value itself can be changed. A pointer to a const int means the pointer can be changed to point at something else but the integer value cannot be changed. For a const pointer to a const int, neither the pointer nor the integer value can change.
    9. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/ux0pai4I1dl1vDxBhD-cTy9Pz5Ne3eDRwJRRZ6_oW7PPjGjn5gxRXK5Yci7-xFVq4OFPnbgim5O5YHtj-Atp0MF37r5LXuplWnJQLl4xKYwVvp2RaesqucxNl1jgu8zW.png)
        - You could pass the values as const:
        - ```c
int adds_wont_change(const int *x, const int *y) {
    return *x+*y;
}
``` However, this is only an indication not a promise - the function still has it within its power to alter the arguments using casts.
    10. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/q7tzntYJoJxSzhSjxKKL5xo7tQqMM2aUb8ggmcPB4hgSru1O59WOwTIIP62lL9UZ0YPkGiR0WsTifUx0OSi5me7cNjbveENoAqi5HehC-Vkt1tGajaBGdTSkVhekzIGE.png)
        - ```c
char* read_a_file(char input_filename[]) {
    FILE *file;
    file = fopen(input_filename, "r");
    char *string = malloc(1001);
    int memory_len = 1000;
    int currently_used = 0;
    if (file) {

        char c;
        while ((c = getc(file)) != EOF) {
            if (currently_used >= memory_len) {
                memory_len += 1000;
                string = realloc(string, memory_len);
            }
            string[currently_used] = c;
            currently_used++;
        }
        string[currently_used] = '\0';

    }

    fclose(file);
    return string;
}
``` 
    11. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/0P3QCnLO7m_QReMJWnZiOuxdyR3x8rUtd4bSxrgQch_t8UEhDy3_iGE_cLCbN7043bbQXt9NcOorpBdzmfdQnEzNhkW0RsMTM0Ltx9cSEdIhb1jvO9vaDtXgTKXoCGka.png)
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/gcBE6wQaCcIKAs4I7o-7BUREOglWeWiNw8BVM06fB5iiiNPfsSRYKNJn0vki2qk-RDt2nyizBGi96ckZmwg_rQFMd10Tci3VUG2wwnunH84ZH-_MHy6VY6QWxUhE4njR.png)
        - Func1 can pass the pointer to the array to bar as the array still exists while bar runs, however when Func1 attempts to return the pointer to the array it's memory on the stack will be deallocated and thus any local variables will be lost and the values the pointer points to will be undefined - that is it's very possible they will be overwritten.
    12. ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/KmKDW7D5NUYnv6HW7bY0Ut9L2F_PSp9sxF8ykkzky4_dUrWqcETQTVvt38Ziv905iqB3iSvV7SQEiPUOhrVvgJ79DOcg_jc1y26c4jvSACgavfpB3Sdz3ZP4AHY3UU-C.png)
        - Declaration simply tells the compiler a variable with the given name is going to be defined at some point, while definition allocates an area of memory for the variable. 
    13. 
        - a.) ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/BlbZtBHf-NMCqx0Ni45FvW9jsJN0z5SnOn0pjG_FusfpndxTwr2s-jl7bfzlokLtRs-Q0rR3NqUjvoXWEm5YZkOonm8F1twD90e2am_nDGl_2sn6oatalYCCy3Zahj_l.png) 
        - **i is the integer value 78 0c 00 00 - which is  c78 which is 8 + 7*16 + 12 * 256 = 3192
        - p⇒c[2] is 62 in hex = 6*16 + 2 - slightly confused by this one, how does the compiler know to move 2 bytes along (as if its working with a char) rather than 9 bytes along (as if it was working with a struct i2c)
        - &(*pps)[1] is 0x18 + 2 = 16+8+2 = 26 (we move 2 forwards because we're dealingiwth a short)
        - ++p⇒i is 3192 + 1 = 3193 
        - 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/01AJtT87kPJuaTX5C5XZt2fkDMlszM_KcOj76VYkPP3spld9TxWz8igbTte2mVcT__CsI1CFlFlr5dQEdpgf-iLHbBo6NlIEVf1o_opvopjYa6F9XEK7M8kOF47i33A5.png)
            - First we cast our manager pointer to an employee pointer, however when we call wage(e) it sill uses the wage calculating function wage_man as the address not wage_em (we never changed the function being pointed to in the cast) - this then casts our pointer back to a manager pointer and calculates 40*10 + 20 = 420.
    14. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/8zVLbpTXRupf0NULVKpgctjp9VkjS4ZcHNDQLuTRUyCGgd-edbhLPclwFXnuh2uXkjhKEDkIJdy5lWAaQEGJWZsfd_psK0fXIA_-BxK-hqwe3y9Ljza6RhcTgKYN287h.png)
            - ```c
#define CONCAT(a, b) (a b)
```
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/tic3LFyhReYVg9QlQVNVKS7tIwEUZBzjUdDYyiQSwuZ9_n2oEAijrte48htdQ-JcRmPa7VhPCys-1hnYCqOysIGcx4ATPZnLFITqbksPDrIto3T51OM49qsvJWNfTpJj.png)
            - Line 3 would not work, as CONCAT only works by leveraging the fact that string literals next to each other get concatenated in c - e.g. "a" "b" ⇒ "ab". All CONCAT does is paste the values next to each other and let the language do the rest - however CONCAT(b, a) will result in CONCAT("UoCCL", a) and the compiler cannot simply infer the value of a to combine the strings (not a string literal). 
            - Line 4 would not work, as j is not a pointer and you are thus taking the integer value of the pointer that concat(a,b) returns. 
            - concat(a,b) allocates memory on the heap and creates a list of chars, while CONCAT simply places two string literals next to each other (uses stack memory). concat(a,b) returns a pointer to the char array while CONCAT(a,b) will evaluate to the combined string literals. 
    15. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Yc7pDYou5sDFsk8G-vXRMbYZJZkvIvoPnxYzVJzVgAFYuEB1gHaD_VDxY8yvyAernjZfJxRStzCKWnlxhKLebEBiAt38UsEs5HBe0iDRIrJeeAJE7wnMXcHI_ZDczi3L.png)
            - 500 bytes: (4 + 1 bytes) * 100. sizeof(struct Elem) =  5 bytes. long is 32 bits - compiler supports unaligned access, unlike all below.
            - 800 bytes: 32 bit machine, the long is 4 bytes, char is 1 byte. sizeof(struct Elem) =  8 bytes - but as 32 bit machine have to use two 4 byte words. Resulting in 100 * (4 + 4) = 800. 
            - 1200 bytes:  ^^48 bit machine, the long is 6 bytes, char is 1 byte, sizeof(struct Elem) =  12 bytes - but as 48 bit machine have to use two 4 byte words. Resulting in 100 * (6 + 6) = 1200. ^^ - possible answer but more likely: long 64 bits but aligned to 32 bits - 4+4+4 = 12
            - 1600 bytes: 64 bit machine, the long is 8 bytes, char is 1 byte sizeof(struct Elem) =  16 bytes- but as 64 bit machine have to use two 8 byte words. Resulting in 100 * (8 + 8) = 1600. 
        - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/Ep4ntJAbb4n94rCUys5-sCXlO1A_qHTJLLNhp1VaSOwwGa6LU1mKBgnyYGPDlAocg7j39QT7M7vUoPh_zTSCQKRoMdoaB5ne8E74h4aC1Mc6_P7-HdZsak0E_be6VYwQ.png) 
            - The fundamental changed is converting the file that was created by a compiler using unaligned access to one that does not support unaligned access (no need for the added complexity when memory so abundant).  Also assumed little-endian.
            - ```c
struct Elem { signed long val; char flags; } v[NITEMS];
char temp[5*NITEMS]; // Each byte in the 5 byte line is going to become it's own item
fread(file, 1, size_of(temp), temp); // First we read the file and get every byte as a char value in our temp array
for (int i; i<size_of(result); i++) {
	
	v[i].val = temp[5*i] | temp[5*i+1]<<8 | temp[5*i+2]<<16 | temp[5*i+3]<<24; // This line combines them using bitwise ors - consider 00001010 | 1010000, combines the values as the zeroes are ignored
	v[i].flags = temp[5*i+4]; // last value is an actual char as we want it
}

``` We could simply have a flag to compute this for or not depending on if we're using this outdated format or not.
    - 
-  _**Lecture 1**_ 
    - Primitive Types in C ↓ 
        - What are the three primitive types?↔Numbers, Characters and pointers
        - Are there primitives of composite types in C?↔NO
    - The **Stack **and **static locals** {{are built in}}, the **heap **is implemented {{by a library}}. 
    - Sizing of various types ↓ 
        1. Char→≥8 bits
        2. Int→≥16 bits
        3. Float→Single precision
        4. Double→Double precision
    - Type operators meaning ↓ 
        1. unsigned―Makes the value unsigned
        2. short―Synonymous to short int, varies but is at least 16 bits
        3. long―8 bytes
        4. const↔Informs the compiler that this value will not be changed, can still be changed using pointers though
        5. volatile↔Means the storage can change at anytime, compiler must check it every time it's used
    - How do you specify different types of number in C? ↓ 
        - long―123L
        - float→123e10F OR 12.5F
        - double→123e10 or 1.4
        - octal→053
        - hex→0x54
        - 
    - **Enumeration**
        - ```c
enum boolean {TRUE, FALSE};
enum override {TRUE=1, FALSE=5, T=5}
``` One can define Booleans, they are indexed from 0 by default - but this can be overridden. 
        - What items in a enum need to be distinct and what don't→Names must be distinct but values need not be.
    - **Declaration**
        - Variables must be declared before they are definition, where definition means giving them storage. They can be declared, defined and initiated inline.```c
 int i = 5;
 char a, b, c;
```
        - What's the different between Declaring, defining and initiating a variable? ↓ 
            - Declaring↔Telling the compiler this variable name will be used
            - Defining↔Setting aside storage for a variable
            - Initiating↔Putting a value in that variable
        - What does the extern keyword do?→It declares but doesn't define a variable, means the variable will be defined elsewhere - i.e. we allocate it no storage.
        - What does the **static keyword** do in regards to
            - **Static functions**→Usually functions are global, however static functions can **only be accessed within the file they're declared in** 
            - **Static variables**→Static local variables **don't lose their contents when they go out of scope** - so functions can reuse their values when called a multiple time. Static global variables are only seen in the file they're defined in
        - 
    - **ALL OPERATORS RETURN A RESULT INCLUDING ASSIGNMENT**!```c
 int y;
 int x = (y = 3);
 // x = 3
```
    - **Type Conversion**:
        - Type conversion occurs when a binary operator takes in two elements with varying sizes. The operator will return a value with the same size as the larger of the two elements - e.g. short + int ⇒ int.
        - However, narrowing is possible.```c
int x = 1234;
char y;
y = x + 1;
// y is overflowed and is the last 8 bits of x+1, in this case -45 in denary.

// CASTING:
y = (char) 1234;
``` 
    - **Expressions and statements**
        - What is an expression?↔An expression is a formula in which two or more operands are combined with an operator.
        - What is a statement↔A statement is an Expression ended by a semicolon
        - What type and value will this expression take on?```c
int x;
short y;
x = 5, y = 3
```↔The expression has type short and value 3. (The rightmost expression)
    - 
    - **Arrays and strings**
        - Strings or arrays are created using this syntax:```c
 int x[10];
```
        - Give 3 facts about string arrays ↓ 
            - They must end in "/o"
            - No bounds checking is performed
            - The compiler places them on a contiguous chunk of memory
        - What does the following result in and why does it work?```c
 char x[] = "abc" "def";
 printf("%s", x);
```↔This results in abcdef, it works because string concatenation is done by default. "abc" and "def" are set to strings using double quotes. This happens at compile time
    - **goto statement**
        - Works but shouldn't be used```c
 some_label:
 	printf("We used a goto")
 goto some_lable;
```
    - 
- 
-  _**Lecture 2 (Only address space layout)**_ 
    - 
    - **Address space layout** 
        - 
        - The **four most important areas of memory** within a **compiled x86 C** program→The **Stack**, the **heap**, the **static variables** and the **C binary code**.
        - Describe the **layout **of the **heap**, the static **variables**, the **stack **and the **C binary** code within the address space of a c**ompiled x86 C program**.→![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/9EqclGaeJ229axupOmXVqqvMy9SUdPUX7V3UUJKfqAvlQamJKCqsY20bbll3HJaaplmHBKojGNlm-veoZGeWqEKPswm8cEwA_HSec_wpoL4PW054VXI79WQoWA_A92Yu.png) 
Start at 0xffff ffff the top of the address space
The stack grows downwards
The heap Grows upwards
0x0 is often mapped to an illegal address to cause a seg fault if accessed
        - Describe the **features **of the** heap **→The heap is **manually managed**, using malloc and free - it is **generally larger than the stack**.
        - Describe the **features** of the **stack **→The stack is **managed by the compiler** and holds temporary local** variables** **declared in the body of a function** which are freed when they go out of scope. It **grows downwards on the address space**. It grows and shrinks as function calls push and pop their values.
        - Describe the **features **of the **data segment **→The data segment holds **global and static variables** who have a value.  
        - Describe the **features **of the **BSS**→The **BSS **stores **uninitialized local** or global variables initialized to 0. 
    - **Unspecified behaviour is **→behaviour where the C standard give's 2 or more options of implementations - the implementation chose can be decided by the compiler. It gives more freedom to optimise code for a given architecture. Some examples are whether to implement inline, evaluation order of function arguments, order and contiguity of memory in the heap. Memory layout of storage of function arguments.
    - **Undefined behaviour is**→behaviour not described by the C standard, when a compiler is faced with such behaviour it can do **anything it likes**. An example is modifying a string literal (string literals are in read only memory) or i++ + ++i.
    - 
    - 
-  _**Lecture 3 (Only unions)**_ 
    - 
    - **Unions**
        - A union variable is a variable can store {{one of multiple types}}, the size of a union variable is equal to the {{size of it's largest member}}, the type retrieved must be {{the last value set }}. The syntax for fetching from a union is {{the same as for structs (⇒ and .)}}. The syntax for defining a union is {{ union u {int i; char p; short x;};}} The type stored within a union can change {{during the execution of the program}}.
    - 
    - **Bit-fields**
        - Bit fields are used for {{low-level control over bits of memory}}. They are useful when {{memory is limited}}. Bit fields are defined within {{structs}}. The syntax for bit fields is {{struct fred{int x : 4; int y : 10;};}}  The details of bit fields is very {{implementation specific}}. Bit field members do not have {{addresses}}.
    - 
    - 
- 
- **The C Pre-processor**
    - The C pre-processor executes {{before the program is converted to an object file}}, it examines lines beginning with # and does textual replacements. It can be used for debugging by setting a DEBUG variable to 1 or 0, and having if (debug) printf(...) - these are optimized away if debug is set to false. 
    - 
- 
-  _**Lecture 10:**_  
    - C++ is said to be: 
        - Better than C
        - Supports data abstraction
        - Supports OOP
        - Supports generic programming
        - Much is familiar with Java with subtle differences
    - Use C or C++ ↓ 
        - Don't want two conflicting IO libraries active
        - Using a standalone library coded in C is fine
        - Code with different metaphors in C & C++
        - C code may not expect an exception to bypass their tidy-up code ?
        - DECIDE AT THE START OF A PROJECT
    - C++ vs Java ↓ 
        - Speed or safety
        - More vs fewer features
    - Java trying to follow C++ with value types - types as values (like int or string) not wrapped in classes
    - **Types:**
        - A lot like C types, but additionally: 
            - Character literals 'a' type char (int in c) 
            - New bool type
            - Reference types: New type constructor &
            - enum types are disticnt, not just synonyms for integers
            - New type constructor class 
            - Names for enum, class, struct and union can be used directly as types - e.g. struct sam{...} can just use sam not struct sam
            - Member functions (method) can specify this to be const - can say this method does not mess with contents fo this
        - Auto and thread_local:
            - auto now means, the type of the initializing expression - like type inference```cpp
 auto sam = 5;
```
            - thread_local is an additional storage class e.g. only one thread sees that same value, opposite of static
        - C++ booleans:
            - bool types true (1) and false(0) when cast to integer.
        - C++ enumerations:
            - ```cpp
enum flag {is_keyword=1, is_static=2, ...}
``` Defines a new type where you can use it's name: flag f = is_keyword
            - Implicit type conversion **not allowed**: ```cpp
f = 5; // WRONG
f = flag(5); // ALLOWED, enum secretly is a bitmap
``` 5 is allowed because bitmaps have explicit max and min values based on the max / min binary values contained in the.
        - References:
            - Alternative name (alias) for a variable
            - Generally used for specifying parameters to functions and return values as well as overloaded operators.
            - Reference declared with &:```cpp
 int i[] = {1,3};
 int *ptri = &i[0];
 int &refi = i[0]; // NEW
```
            - Must be initialized when it's declared!  
            - You cannot change what a reference refers to after creation. E.g.: ```cpp
 refi++; // Results in i[0]=2
 ptri++; // Results in ptri point to 3
```
            - Can think of reference types as pointers **with implicit use of * each time.** 
        - References in function arguments:
            - When used as a function parameter, the value is not copied: ```cpp
 void foo(int& i) {i++;}
 
 //Same as
 
 void fooTwo(int* i) {*i++;}
```
            - Declare a reference as const, when no modification takes place. 
            - It can be noticeably more efficient to pass a large struct by reference than by value.
            - Implicit type conversion into a temporary occurs for const references but errors otherwise: ```cpp
 float fun1 {float&};
 float fun2 {const float&};
 void test() {
 	double pi = 3.14159;
 	fun1(pi); // ERRORS 
 	fun2(pi); // ALLOWED because it knows the value is not going to be changed. Implicity type converts to float. 
 }
 
``` 
        - Overloaded functions:
            - Works just like java, functions with varying argument type but same name.
            - Type conversion is used to find the best match, but that isn't always possible: ```cpp
 void f(double);
 void f(long);
 void test() {
 	f(1.0);
 	f(1L);
 	f(1); // Fails, f(double) or f(long) ?
 }
```
            - Can also overload built-in operators, such as assignment and equality
        - Scoping and overloading:
            - Overloading does not apply to functions declared in different scopes. ```cpp
 void f(int);
 
 void test() {
 	void f(double);
 	f(1); // calls f(double);
 }
```
        - Default functions arguments: Uses overloading, creating two separate functions.
            - ```cpp
double log(double v, double base=10.0);
// Like python, non-default cannot follow default:
double log(double base=10.0, double v); // NOT ALLOWED

// A DECLARATION does not need to name the variable:
double log(double v, double=10.0);
// Obviously when I actually DEFINE the function I would need to do:

double log(double v, double a) 
{... // do some stuff};
// where log(1) same as log(1, 10)


// But beware of lexical interactions between * & = 
void f(char*=0); // Wrong *= is assignment
``` 
    - **Namespace:**
        - Related data can be grouped together in a namespace,  not the same as a class as we can't create an object of the namespace type - just a logical grouping of values & functions.
        - ```cpp
namespace Stack{//header file
	void push(char);
	char pop();
}

namespace Stack {//implementation
	const int max_size = 100;
	char s[max_sizez];
	int top = 0;
	
	void push(char c) { ... }
	char pop() { ... }
}

void f() {//Usage
	Stack::push('c');
}
``` Ensures we don't have clashes of external functions, namespace formalizes naming conventions (gm_openscreen meaning graphics manager openscreen for example). 
        - ```cpp
using namespace Stack; // imports everything to the scope

int main() {
	pop();
	push('a');
}
``` More like java packages than modules in java.
    - Using Namespace: 
        - Scope and expresses logical program structure - collect together related pieces of code.
        - A namespace without a name limits the scope of vars, functions and classes within it to the local execution unit.
        - Can declare the same namespace in multiple source files.
        - Can be defined more than once.
        - Global function main() cannot be inside a namespace.
    - Linking C & C++ code: 
        - extern "C" specifies that the declaration should be linked as C NOT C++ Code: ```cpp
 extern "C" int f();
 
 extern "C" {
 	int globalvar;
 	int f();
 	void g(int);
 }
```
        - 'Name munging' for overloaded functions.  A C compiler typically create a linker symbol '_f' for the f above, this gives the compiler a namespace the programmer cant use (funcs beginning with _). A c++ compiler generates '__Z1fv' function of length 1 that takes a void argumeny.
        - Function calling sequences can differ, e.g. exceptions.
        - If we want to write a library in C, and specify it to be importable into both C & C++: ```cpp
 #ifdef __cplusplus
 	extern "C" void myfn(int, bool);
 #else
 	include <stdbool.h> //No boolean in C
 	extern void myfn(int, bool);
 #endif
```
        - Care must be taken with pointers to functions and linkage - if I pass a C++ function to a extern "C" piece of code, could get errors.
-  _**Lecture 11:**_ 
    - **Classes and objects in C++**:
        - ^^C++ classes are somewhat like java.^^
        - ^^**Two**^^^^ main components^^ of classes↔^^Data members^^ and ^^member functions^^ which act on the data. Both data members and member functions can be static.
        - The^^ 3 access controls^^ of C++ members are→^^private, protected and public^^ 
        - **Class and struct are almost synonyms** in C++, the only difference is→class members are by default private while struct members are private by default.
        - ^^Classes ^^are ^^created ^^with→^^**class or struct keywords**^^**:** 
            - ^^Struct^^ ^^members default to ^^→^^public^^ access ^^^^
            - ^^class members default to ^^→^^ private^^. 
        - A ^^constructor ^^is simply a↔^^Member function with the same name as the class^^ 
        - C++ supports overloading on both→constructors and member functions
        - A **destructor **is named with↔the same name as the class prefixed with a **tilde **(~)**.** 
        - Big differences from Java:
            - ^^Values of class types are^^→^^ ^^^^**not references to objects**^^**, but**^^** the objects themselves**^^**. **
                - So we ^^access members with C-style . (dot)^^ ( using -> more convenient when we have pointer to objects). 
            - We ^^can create an object of class C,^^ two ways  ↓ 
                - ^^On the stack by declaring a variable C x;^^^^^^
                - ^^On the heap: new C() ^^^^**which returns a pointer to C.**^^ 
            - If a function is ^^**statically resolved**^^** **it means→the code to execute for a given function name is ^^**generated at compile time (or linked at link time) not runtime**^^.
            - If a function is ^^**dynamically resolved **^^it means→the code to be executed will be ^^**determined at run-time**^^. 
            - ^^Member functions by default are resolved ^^→^^**statically**^^. For java-like code ^^**declare them virtual.**^^ 
            - The virtual tag and the dynamic resolution allows for→runtime polymorphism.
            - ^^Member functions can be ^^^^**declared **^^^^{{**inside a class**}}^^^^** **^^^^but ^^^^**defined **^^^^{{**outside it using : : **}}^^^^  ^^ 
            - C++ uses {{new }}to allocate and {{delete }}to de-allocate. No garbage collector.
        - Example (emphasising differences from Java):
            - ```cpp
class Complex {
	double re, im;
	public:
		Complex(double r=0.0, double i=0.0);
};

Complex::Complex(double r, double i) : re(r), im(i) {
	// This is the preferred form of constructor initialization
	// NECESSARY FOR CONSTANTS
}

Complex::Complex(double r, double i) {
	re=r, im=i;  // DEPRECATED initilization by assignment
}

int main() {
	Complex c (2.0), d, e (1, 5.0);
	return 0;
} // local objects c,d,e are deallocated on scope exit!!
  // IMPORTANT - STACK ALLOCATION
```
        - The preferred form of **constructor** **initialization in C++ **is (somehow). **It MUST BE USED WHEN**...→```cpp
 Complex::Complex(double r, double i) : re(r), im(i) {...}
 
 // You MUST use it when itializing
 // const and reference members
```
        - In java, **constructors only **{{**initialize heap storage**}}** **(which has to be pointed to), only way to update is {{x.f = updated_val}}; 
        - In C++ because objects values are "first-class-citizens"→there are more update behaviours
            - In "C x;" x is initialized using→The default constructor   
            - In "C x = y;" x is initialized using→The copy constructor
            - We need to worry about what "x = y" does. 
            - We split class definitions into separate behaviours and control them to→Preserve **class invariants **(If I can define an object, with no members initialized - certain invariants may not hold) and **object encapsulation** (All the behaviour of the class should be held within the class)
        - **Default Constructor ** 
            - Default constructors are called when→you type "C x;" or if you do "new C();" i.e. with no arguments.
            - If no default constructor is specified→The compiler creates one, with little to no initialization.
            - To disallow users to use the default constructor we→define the default constructor and set it to private.
        - **Destructors **
            - destructor are called→when a stack-allocated object goes out of scope **INCLUDING when an exception causes this to happen**, when a heap allocated object is deleted
            - There can only be {{one}} destructor for a class
            - Make destructors **virtual** when→The class has subtypes or super-types - as we'll want to inherit the destructor
            - Stack allocated objects, with {{destructors}}, are a good way of freeing memory after the scope is exited.
        - **Copy Constructors**
            - ```cpp
// Initialization methods:
Complex c(1,2);
// VS
Complex d = c; // Copy constructor evoked
``` 
            - To augment the default copy constructor use the following syntax→```cpp
class Complex {
	Complex (const Complex& c) {...} 
}
// we don't pass a value
``` This is useful when I have member variables with pointers in for example. Don't just wanna copy everything
            - To **disallow **copying of objects→Make the copy constructor **Private!** Note, can still use assignment );
            - ^^IMPORTANT NOTE:^^ Assignment (d = c) differs from invoking the copy constructor: Complex d = c. **Does not** use the copy constructor.
        - **Assignment operator**
            - By **default **when the assignment operator is used→all the **non-static** members of a class are **overwritten **(x = y;). 
                - This may not be desirable if the class contains pointers, when I copy a dog I want it to have a pointer to its own dog bowl?
            - You can implement your own assignment operator this syntax (for the class Complex)→```cpp
Complex& Complex :: operator=(Complex& c) {...}
// We take the input to the right hand and return a reference
// e.g in x = y, c = y
``` 
        - **Constant member Functions**
            - **Member functions** can be declared **const **→This prevents the function from modifying any object members.
            - The syntax for constant member functions is (for a function real in the Complex class )→```cpp
 double Complex::real() const {
 	return this->re;
 }
 // Note that if you declare beforehand you need to include the const:
 double real() const;
```
        - **Arrays and heap allocation**
            - If we want to create an array of objects, the class needs a {{default constructor}}.
            - To create and delete objects on the heap, we use this syntax→```cpp
 Complex* c = new Complex(1.0);
 // To delete them we use
 delete c;
 // This invokes the object destructor !!
```
            - We **need **a method for **array heap deletion** because→C doesn't distinguish between a **pointer to an object**, and a **pointer to an array of objects**. 
            - Array heap deletion is done using the following syntax→```cpp
 delete[] c;
```
            - Deleting objects using the array heap deletion invokes→the object destructor on each object.
        - **Operators and Virtual (11.2)**
            - **The "this" pointer**
                - 'this' is used much like self in python (while in python you need to explicitly pass it, C++ does that behind the scenes). Useful for many tasks. Such as overloading in the body of a function:
                - ```cpp
&Complex Complex::operator*=(Complex input) {
	this->re *= input.real();
	this->im *= input.imag();
	return *this;
	// Note this returns a reference NOT the object itself
}
``` 
                - Remember, at its core this is a {{POINTER}}.
            - **Class instances as member variables:**
                - Consider a class with objects as member variables Complex a, how do we initialize said objects? I.e. how do we call the constructor?→```cpp
class Example {
	Complex a;
	Complex b;
	Example(double im, double re) : a(1.0, 0.0), b(im,re) {
		...
	}
};
``` 
            - **Temporary Objects**
                - Jesus Christ. 
                - Temporary objects exist for the duration of a {{full expression}}, after which they are lost.
                - What is wrong with ```cpp
string a("abd"), b("def");
 const char* SCARY = (a+b).c_str(); // c_str converts a c++ string to a c string
```→Temporary objects are things such as: ```cpp
 string a("dsadsa"), b("dsadfsadsaadsa");
 // THE TEMPORARY OBJECT BELOW IS FORMED FROM (a+b)!!!
 const char* SCARY = (a+b).c_str();
 // c_str() just returns a pointer to the objects string value
 // HOWEVER, because its temporary the value is lost!!!
 // SCARY don't got nothin' in it
```
            - **Friends**
                - Within our class, we can define another class to be our **friend, **this means→Code within the other class, can **access the private and protected members** of our class: ```cpp
class A {
	friend B;
	private:
		int myPrivateNumber = 3;
};
class B {
	static doStuff(A someObject) {
		// Because their friends, they share the number
		A.myPrivateNumber;
	}
}
```  
                - We can even define non-member functions to be friends, this means→that functions defined elsewhere can access our private methods: ```cpp
 class a {
 	friend void outputTheNumber();
 	private: 
 		const static int myPrivateNumber = 3;
 }
 
void outputTheNumber() {
	std::cout << a::myPrivateNumber << std::endl; 
}
```
                - Note: Friendship is **not symmetric** 
            - **Operators**
                - **Operator Overloading** 
                    - C++ allows for {{operator }}overloading, this is syntactic sugar.
                    - It can be done outside the body of the class, using the following syntax→```cpp
bool operator==(Complex a, Complex b)
	return a.real() == b.real()
		&& a.imag() == b.imag();
``` 
                    - Or it can be done inside the class, in which case we can use the following syntax→```cpp
 bool Complex::operator==(Complex a) {
 	return re == a.real() && im == a.imag(); 
 }
```
                    - Operator overloading can be done on almost all operators.
                - **Streams**
                    - Streams output the {{left argument}}, this allows for {{chaining }}of streams.
                    - ```cpp
std::cout << "Like this" << std::endl;
``` 
                    - We can use overloading with streams like the built in type using either syntax below: The difference is:→```cpp
const char* s = "Hello World";
cout.operator<<(s);
cout.operator<<(std::endl, s);
// The << operator is overloaded, if we pass one value it behaves differently to two (in this case it would pass &s[0])
```
            - **Inheritance** 
                - C++ inheritance works much like java
                - The syntax for C++ inheritance is→```cpp
class Animal {
	int legs;
	public:
		Animal(int l) : legs(l) {}
};
class Dog : public Animal {
	int ears;
	// Could have lost 1+ ears
	public:
		Dog(int e) : Animal(4), ears(e) {}
};
``` 
            - **Virtual Functions** 
                - What will the following code output?```cpp
class Animal {
    public:
        void makeNoise() {
            std::cout << "A noise!" << std::endl;
        }
};
class Dog : public Animal {
    public:
        void makeNoise() {
            std::cout << "BARK" << std::endl;
        }
};

void makeAnimalBark(Animal* a) {
    a->makeNoise();
}

int main() {
    Animal* a = new Animal;
    Dog* d = new Dog;
    makeAnimalBark(a);
    makeAnimalBark(d);
}
```→The problem is, makeAnimalBark isn't virtual, so the output will be - "Bark" "A noise!". Note this is **only **the case if we pass a pointer - if makeAnimalBark took the value it would work.
                - Non virtual member functions depend on the {{static type}} of the arguments. 
                - We need the virtual keyword because→a pointer to a subclass can be cast to the base class, then the base class cannot see the overridden function. 
                - To get polymorphic behaviour we must→define the function as virtual in the superclass. Then it will be dynamically evaluated at runtime.
                - **Non-virtual** member functions are called depending on {{the static type }}of the variable, pointer or reference. Since a pointer to a derived class can be cast to a {{pointer to a base class}}, calls at base class do not {{see the overridden function}}. To get polymorphic behaviour, {{declare the function virtual}} in the {{superclass}}. 
                - To enabe **virtual functions **the C compiler must→generate a "virtual function table" or vtable. This table contains the function to call for **each object instance**. This adds **run-time overhead **as every function call **must go via the vtable.** 
                - Why does C++ give the option of none virtual overridden functions?→It's a **trade off of performance vs Programmer conceptualization** - dynamically** type checking at run-time can be slow**, so if it's not explicitly needed we don't want to do it. Instead of a function call in machine code, its an indirect function call - While at first glance this is not much slower, the **effect on the cache and branch predictor can be large** 
                - **Enabling Virtual Functions**
                    - To enable virtual functions, C++ uses→a vtable or virtual function table. These store a pointer to the specific function to call for every object instance. They are slower.
                    - C++ vtables also encode RTTI - runtime type information about the class in question. Can ask if an object has the same type as another.
            - **Multiple Inheritance and Casts (11.3)**
                - **Abstract Classes** 
                    - Works like java but with a different syntax 
                    - In C++ it is verboten to {{instantiate }}an abstract class.
                    - What is the syntax for C++ abstract classes→```cpp
 class shape {
 	public:
 		virtual void drawTheShape() = 0;
 }
 
 // Inherit it as normal
 class Triangle {
 	public:
 		void drawTheShape () {...};
 } 
```
                    - When can a derived class be instantiated?→When all the abstract functions are implemented. If some of them are, you cannot instantiate the class. 
                - **Multiple Inheritance**
                    - In C++ you may inherit from multiple classes, if you have a name clash you must...→```cpp
class Car {
	public: void noise() {cout << "Beep";}
};
class Bike {
	public: void noise() {cout << "Toot";}
};
class Cabike : public Bike, public Car {};

// Explicit Naming is required
Cabike.Car::noise();
// or
Cabike.Bike::noise();
```
                    - The Diamond problem with multiple inheritance→Is when a subclass contains two instances of another class. E.g. two sets of the same variables. It can be achieved like so ```cpp
 class A {int someInt;};
 class B : public A {};
 class C : public A {};
 class D : public B, public C {};
 //We can do the following:
 D dInstance;
 dInstance::B.someInt = 3;
 dInstance::C.someIne = 4; 
```
                    - If we have a case of the diamond problem in C++→All variables from the "top" of the diamond, must be chosen explicitly in order to be used. E.g. we need to know which A class to choose from if we have two instances.
                    - **Virtual base classes**
                        - Virtual base classes allow for only {{one instance}} of the "top" class within inherited classes. 
                        - Virtual base classes mean that↔any class that **inherits **from multiple classes **containing the same virtual base class**, will share that class instance without ambiguity.
                        - The syntax for virtual base classes is simply ```cpp
 class A {public: int a};
 class B : virtual public A {};
 class C : virtual public A {};
 class D : public B, public C {};
 
 // Means we can do:
 D d;
 cout << d.a;
```
                - **Casts**
                    - ```cpp
double* p;
int i = (int)*p; // fine
int j = *(int*)p; // Undefined - we've lied about the type of the pointer and then got the value of the supposedly int pointer
```
                    - In C++ the role of casts and constructors can overlap, casts can be seen as implicit calls to the constructor. Give an example with Complex→```cpp
 double x = 0.1;
 Complex s = x; // Because there is a constructor that take a single double
 
 // Similar to this: (which simply does the cast)
 int a = int(x);
 int b = x; // Implicit cast!
 
```
                    - To disallow ```cpp
 double x = 0.1;
 Complex a = x;
``` we must→Declare the constructor **explicit.** Implicit vs explicit casts.
                    - If I want to allow casts from a class type to a default type I do the following→Overload the operator of the type we wish to cast to, e.g.: ```cpp
Complex i(0,1);
double x = (double)i; // TYPE ERROR

Complex {
	double operator double () {
		return a->re;
	} 
} 
``` 
                    - **New forms of casts in C++** 
                        - Problems with C-style casts include  ↓ 
                            - They do no type checking
                            - They are hard to find in the code
                        - Describe what these do ```cpp
dynamic_cast<T>(e)
static_cast<T>(e)
reinterpret_cast<T>(e)
const_cast<T>(e)
```→```cpp
dynamic_cast<T>(e)
// This uses RTTI and performs runtime checks
// when casting pointers within an inheritance 
// hierarchy
Car car;
dynamic_cast<Vehicle&>(car);

static_cast<T>(e)
// This is very similar to C, does it's best effort
// at compile time: static_cast<int>(3.14)

reinterpret_cast<T>(e)
// Explicitely flags re-use / reinterpiration of bit pattern

const_cast<T>(e)
// remove const or volatile from a type, allowing you to edit it as you please
// Specifically for const pointers
```
                - 
                - 
                - 
                - 
        - 
-  _**Lecture 12:**_ 
    - **Exceptions and RAII**
        -  _Exceptions_ 
        - Done just like java, but **throw object values** not object references - the reason for this is→if you **run out of storage**, a reference requires the creation of an object in storage... 
        - The **principal of exceptions** is a given piece of code (**a library**) may  _encounter an error and not know what to do with it_  - the user code may know how to handle it.
        - One portion of code **throw**s an exception, another **catch**es it.
        - If an exception is thrown, the **call stack** is→unwound until a function that can handle the exception is found
        - An uncaught exception results in the program **terminating**.
        - **Throwing Exceptions**
            - Exceptions in C++ are just {{normal values}}, matched by type. Often a {{class}} is used to define a particular error type.
            - An instance of the class can then be thrown, caught and possibly rethrown. The syntax for these is→```cpp
 class myError() {
 	public:
 		int X;
 		myError(int x) : X(x) {}
 };
 
 void f() { throw myError(10); }
 
 try {
 	f();
 }
 catch (myError) {
 	//handle the error
 	throw; // re-throw
 } 
```
            - The thrown type can carry information ```cpp
 try {f();}
 catch (myError instance) {
 	std::cout << instance.X; // outputs 10
 	// We could simply make myError a struct so all members are public
 }
```
            - The syntax for catching multiple errors is the following (also what does catch(...) do?)→```cpp
 try {...}
 catch (errorA) {...}
 catch (errorB) {...}
 catch (...) {} // is a wildcard that catches all exceptions - discouraged, what have I caught?
```
            - Class hierarchies can be used to express errors→e.g. someError > myError. However, this requires runtime-type-information!
        - **Exceptions and local variables**
            - When an exception is thrown, that **stack is unwound** this **differs **from **stepping down the stack** as→all  _local variables we meet call their destructor_ . This plays the role of try - finally (in java finally frees memory)
            - It is **good practise** to wrap locks, open file handles, heap memory etc. in **stack allocated objects** - this is because→when the stack is  _unwound the destructor of the stack allocated object_  will be called and all the  _memory can be freed. _  
            - RAII is→**Resource acquisition is initialisation** (this is a terrible name), actually means  _memory is freed once the object is out of scope_  - done by  _wrapping resources in stack allocated objects_ .
    - **Templates**
        - Templates support **metaprogramming**, this is where→code can be  _evaluated at compile time_  rather than run time
        - Templates support **generic programming**, this is where→ _types are_   _parameters _ to a program
        - Generic programming in **void * pointers** has the **disadvantage**→that we lost type-checking
        - **Class templates**
            - The syntax for defining and instantiating a class template is→```cpp
 template<typename T> class Stack { ... };
 // Or alternatively, this is the same
 template<class T> class Stack { ... };
 
 // We can the instantiate the Stack
 Stack<int> stack = ...;
 
 // the template parameter T could be any C++ type - hence preferring typename to class
```
            - Stack could then be implemented like: ```cpp
 template<typename T> class Stack { 
 	struct Item {
 		T val; // the important bit
 		Item* next;
 		Item(T v) : val(v), next(0) {}
 	}
 	...
 	public:
 		void push(T val);
 		T pop();
 };
```
        - **Template richer details** 
            - What is the syntax for setting a specific template type?→```cpp
template<int i> class ... 
```
            - How do you give a template several parameters?→```cpp
 template<typename T, int i> class ...
```
            - How do you declare a subsequent argument with a template argument?→```cpp
 template<typename T, T x> class...
```
            - What's the syntax for a template function with a default value?→```cpp
template<typename T, int x=100> class ...
```
        - **Templates behave like macros**
            - Templated classes are **type checked** when→the template is instantiated. 
            - Template **definitions are often placed** in the→header file, because if we had it in one file and another file used it - we'd end up having to recompile a load of files whenever we updated the template. Additionally, it makes separate compilation impossible.
            - The **difference between java and C++ templates** is→** Java does type erasure** setting all the types to Object, while C**++ works like a macro** where the type is replaced and the new function for that type is added to the binary 
        - **Templated specialisation**
            - What does **Template specialisation allows** **us to do** and what is the **syntax**?→It allows us to define **different definitions of a class** depending on the type parameter passed. 
The syntax is: ```cpp
struct Test{};

template<typename T> class someClass {
    void stuff() {std::cout << "HI!" << std::endl;}
};
// NOTE, the missing typename T is ON PURPOSE
// You must have empty angle brackets
template<> class someClass <Test> {
    void stuff() {std::cout << "NO!!" << std::endl;}
};
```
        - **Templated functions**
            - The syntax for defining and instantiating a template class is→this:```cpp
template<typename T> void sort(T arr[], const unsigned int& len);

// The type of the template is then inferred from the argument types:
int sam[] = {4, 1, 2};
sort(sam, 3);
sort<int>(a,3); 
```
            - Unlike template classes, template functions have {{type inference}}. 
            - Two benefits and a negative of using **templates for functions**  ↓ 
                -  _Better type checking_  than using void *
                -  _Larger binaries_  if multiple different types of sort() are invoked
                -  _Potentially faster code_  than runtime type inference as we don't have vtables for functions - we know the type of the function at compile time
            - **Overloading templated functions** 
                - Templated functions can be overloaded with {{templated }}and {{non-templated}} functions. Resolving an overloaded function call uses the "most {{specialised}}" function call
        - **Template specialisation enables metaprogramming** 
            - ![](local://C:/Users/malac/remnote/Malachy_O'Connor/files/_qsNY9_ag-ZhMMnJoBIlTBcdNHf3yUahT-AMm2TonL3ay1_mtpzUixn0ACOUbvzuRBBUliHrc1qG9hED_MVdo29srt_WOUI7DZfbgABrzZ47XkYigIPhHplmm7HBr46h.png) 
            - Meaning templates are a Turing complete compile-time programming language! However the type you seek to evaluates value must be known at compile time - like enum or static
        - 
        - 
    - 
