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
    - f.)   Catches take a single argument and allow for the escape of a code block to a predefined location if an error occurs```
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
