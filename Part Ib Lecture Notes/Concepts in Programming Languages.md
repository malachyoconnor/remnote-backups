- ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4A5MVQ9NBysmMY9eglKY_EDuO5Yiilb-z7KgWZ76X-Qype4kTpeEYNoZX0R3OiDc76GwFC-jIGVfrlaO9cEZwvNlUqsSSI2z0iqwG1JOXf1EGkhbhL-mJxtX6XNaGN7l.png) 
- **Lecture 1.1** (short)
    - There are many reasons for having multiple languages, evolution, special purposes, personal preference and the fact that no one language is good at expressing all programming styles.
    - Three main reasons Languages evolve ↓ 
        - Changes in hardware 
        - Changes in attitude to safety and risk 
        - New ideas from academia or industry
    - Language Standardisation
        - How can we tell what is a valid piece of code? We must read the reference manual!
        - What is timeliness―When do we standardize a language? We may want to let it settle in first.
        - What is Conformance―What does it mean for a program to adhere to a standard, and a compiler to compile a standard? 
            - A language standard is a  __treaty__  setting out the rights and obligations of the programmer **and **the implementer. 
        - What is Obsolescence and how is it handled?―When does a standard age and how does it get modified? Language creators deprecate features to encourage developers to stop using them.
    - 
- **Lecture 1.2**(Fortran)
    - Fortran  
        - The first {{high level programming language}} - heavy focus on {{execution efficiency}} to help uptake over Assembly. Easier to optimize than C.
        - Remains the main language for scientific computing.  
        - Compilation 
            - How is a fortran program compiled, and why was it a done this way?―Fortran by combining the main program and subprograms. These were all compiled separately and then linked into a single executable (like C). This was done due to lack of **memory resources.** 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MinTKUWOIZKzfKNXXY6uMsggdPlD9cJ9_b5YXidh6WQiWS79Ya5G2Qz2UCIvbU3D73danpa-3cAqeVX8jOm8gk6tzMU1_VWtDeHsKKXYw3ss54YzACiodkRMMHTxe3Zc.png) 
        - Data types and storage allocation 
            - Numerics - Integer, real, complex, double-precision real 
            - Booleans (called logical)
            - Arrays (of fixed declared length)
            - Character strings (of fixed declared length)
            - Files 
            - Fortran 90 added 'derived data types' like C structs 
            - How were data types allocated initially and why?―Originally **all data types were allocated statically**, including local variables. This was because computers didn't have  _index registers_  and so couldn't have a cheap stack ⇒ Leading to having no recursion, meaning no on the fly allocation. 
            - Modern Fortran has recursion and a heap.
        - Control Structure 
            - FORTRAN 66 - labels and GOTO, did have DO (for) loops.
            - FORTRAN 77 - added if-then-else and other modern structures. No WHILE, no recursion.
            - FORTRAN 2008 - support for concurrency and objects
        - Variables need not have their t{{ype declared}} - implicit naming convention determined their {{type}}. IMPLICIT NONE could disable this. 
        - Fortran 90 provided a module system to combat―link/runtime failures due to separate compilation. 
        - Function parameters passed by {{reference (like & in C++)}}. Fortran 2003 added pass-by-{{value }}for C interoperability.
        - Program consistency checks 
            - Describe the type checking ↓ 
                - Static type checking used, checking incomplete. Many language features not statically checked, including common blocks (because subprograms compiled independently).
                - Constructs not statically checked left unchecked at runtime, focus on  _speed!_  
        - Parameter-passing mode 
            - What are formal-parameters and actual parameters―pass by reference where the formal param is an alias to the actual one. FORTRAN pass by reference by default.
            - Why can formal parameters be a source of bugs in Fortran?―If a formal param is changed, it must be a variable - however this is a huge source of bugs due to lack of cross-module compilation checking. 
            - Modern Fortran added call by value.
        - 
- **Lecture 1.3 **(Lisp)
    - Lisp 
        - Stands for List Processing (circa 1960). A scheme for representing partial recursive functions of a certain class of symbolic expressions.
        - Motivating problems were―symbolic computation like differentiation and logic.
        - Programming language phrases 
            - Expressions - a syntactic entity that can be evaluated to find it's value 
            - Statements - A command that alters the state of the machine in some explicit way
            - Declaration - A syntactic entity that introduces a new identifier, often specifying one or more attributes.
        - LISP contributions were  ↓ 
            - LISP is an **expression-based **language, conditionals are done using  __conditional expressions__ . 
            - Lists - dynamic storage allocation
            - Recursive functions
            - Garbage collections
            - Programs as data
            - Self definitional interpreter
        - LISP overview 
            - Values are either atoms (X, FOO, NIL), or cons cells with two values. 
            - Programs are just special case of LISP values known as S-expressions - an S-expression is either an atom or a NIL terminated list of S-expressions e.g.:```lisp
 ((1 X ) NIL ((1 2) 3))
``` 
This means **Programs are just data**/. We can construct values and then execute them as a program.
            - Programs represented as S-expressions are evaluated, the head of the list is the function and the rest are arguments.
            - What does the following program output? ```c
(APPEND (QUOTE (FOO 1 Y)) (CONS 3 (CONS `Z NIL)))
```
QUOTE, tells LISP not to evaluate the s-expression within the quote - so the first argument to APPEND is (FOO 1 Y).
CONS `Z NIL (` is shorthand for QUOTE, so we don't lookup the value of Z) gives ( Z ) we then cons 3 on that giving (3 Z)
The final result is then (FOO 1 Y 3 Z).
            - What converts ` to QUOTE?―The READ function converts all `. It's not actually part of the syntax.
            - Example LISP program:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-8dSoGGOagarB9wSPyGLhEUUhq_s3cgQi5tXG-kDl-1o-0kJc6Z1MOYiCKMOm5GaawRSWF3krMaoxFAqWfTSxR4dXCdjS3hL8GutAiBhL9pP-ZtlEd6ENj_MVZKeLFVS.png) 
        - Core LISP primitives 
            - CONS, CAR, CDR - for working with lists. CAR gets the first item from a cons cell, CDR gets the next
            - CONSP, ATOM - boolean tests for being cons cells or atoms.
            - EQ - identity test for equal atoms
            - COND - conditional expression e.g. (COND ( (EQ X Y) (X 5)) (T NILL)). Any number of (CONDITION EVALUATE) pairs to be tested (will evaluate up the first TRUE one). Note that COND disallows evaluating the second argument until we check the first. 
            - DEFUN top-level form for recursion:
DEFUN F (X Y Z) <BODY>
            - LAMBDA (X Y) (+ X Y)
            - APPLY F ` (1 2)
            - Explain the following code: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bsFQN6onduwP8h0gsndeGBQ_pln2gTqu65ZCtOyFM2rgCs--UxvyK-ahf3fP9Sb6tlV_3rkkB2RnJx6ebvc3_riRHlEk_dcIFrB0x0NekCBEKZfJn8DmnLhu8UgqF3Z9.png)―This substitutes x for y in z recursively. If z is an atom (we've recursed down to an easy substitution) if z and y are the same (and we should replace) then return x otherwise return y.
The rest is obvious.
        - Static and dynamic scope 
            - Describe the two main ways of finding the declaration of an identifier  ↓ 
                - Static scope - use the closest enclosing scope value.
                - Dynamic scope - a global identifier refers to the declaration associated with the most recent environment.
            - What would main () evaluate to in the following code? ```c
(DEFUN g (x myfn) (apply myfn ()))
(DEFUN f (x) (g 2 (lambda () x)))
(DEFUN main () (f 1))
```―The questions is if the interpreter looks up the free variable x in its static scope (getting 1) or dynamic scope (getting 2).
Newer dialects use static scoping for this situation. However, top-level defvar can be used to mark a variable as using dynamic binding.
        - Abstract machines 
            - What is an  __abstract machine__ ?―This refers to an idealised machine that can execute a specific programming language directly. Consider the JVM.
            - Describe the LISP abstract machine―the abstract machine for LISP had a heap and garbage collection. 
However, static locations were used to store variables - variables used by a recursive function were saved on entry and restored on exit ⇒ leading to **dynamic scope**.
        - Programs as data 
            - Programs can build data structures, then evaluate that structure as if it were part of the program using  _EVAL_ .  
            - What problem can arise when using EVAL?―The environment of an EVAL program is the environment of it's calling program - this means **if the EVAL expression has free variables issues can arise.** 
            - LISP is defined within itself.
        - Parameter passing in LISP 
            - Function parameters are transmitted either all by {{value }}or all by {{text}}  (QUOTE).
            - Only built-in functions (QUOTE, LAMBDA) should use pass-by-test, why?―Because a special variant of EVAL is used that evaluates the argument in the calling environment.
            - Pass by text is similar to call by name.
            - What two ways of delaying execution are there?―Using QUOTE, and putting the expression in a lambda function to be evaluated.
        - Dangers of eval 
            - Describe the perils of the following code: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VOahZM194oYf2JGBTK-FufvxtMhMgd5ArhFGx72Z2BNX77LiUuR2y22hc4Pe3WaTzxLF-OoUpf2dHuqMx1OE7P7EW5-m3-HeYWsIm31e-7dxADFKhNbyJTOjIOyWsdZ9.png)―The question is, should eval e return 11 or 12. This depends on if it uses dynamic or static scope. 
Thus, use of eval needs to be very careful and should be considered a security hole.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/K_5LeNAExMOi9Q7-J5DJiPJR-rDj57Iyab2lR1ocyExK6HrTp88aXOJNMwyP_jYx-9AvXRnNnQoIDkLdBFjYvyq2Yr3HZjJ-WLaqGaFxPk_S7dX98hDeOZbncuH-gZJP.png) 
- **Lecture 2.1 **(Algol and Pascal?)
    - Parameter passing 
        - What is call by value?―The actual parameter is evaluated and the value is stored in a new location (which the formal parameter can use).
        - What is call by reference?―The formal parameter is an alias to the actual parameter.
        - What is call by value/result?―Same as call by value - but at the end the final value is copied back to the actual parameter on procedure exit.
        - What does this code test for? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TSudNz72hrJ2zXpdmevYpU7QbPHn7Uvxkajv0jBOfKiRs65UcWx3gB6ctiUQmjQQSf9LMBIElqNReO1rIygSAYW_EOtTEy_XqE-17hmgfpwL5PQutRLCOslo5p4Lo4RE.png)―Test for call by reference - e.g. if x `== y.` 
        - The three main considerations of call-by-value vs call-by-reference are―**efficiency **(don't want to pass massive arrays by value), **side-effects** and **aliasing **(multiple inputs pointing to the same variable).
        - Algol 60 uses {{call-by-name}}, this can cause side-effects. Lazy functional languages handle this by having no {{side effects}}, and maintains speed by  {{caching }}evaluated functions.
    - Positional vs named matching 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q6hlLxXxAbifCRvpzNV9dJWQMBZ3RMoJa_bLlmAOrzSHneJmbySU_CtdrjbFxQtueqniC78H1XwwZ2em7Ad_6NvZtOOFKO4g7nXQdSyXLROcBf2Hcqah1iHUkM1QvmwE.png) 
    - Algol 
        - **Main characteristics are **   ↓ 
            - Algol attempted to be a middle-ground between Fortran and Lisp. 
            - Semicolon separated sequence of statements
            - Block structure - with scoping rules for local variables which followed the lambda calculus. Can have nested blocks!
            - Functions & procedures - with recursive subroutines.
            - Static typing
            - Explicit type declaration
            - Call-by-value and call-by-name 
        - Algol shortcomings 
            - Give 2 shortcomings of Algol ↓ 
                - If a function was an argument of another function, the type of input that function took was not specified. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Bg1_I62kp-crNjARwPAGPu_TmujPx7EPLO43004P10NXO_Qn9SFqjsXxApPNGs6Fsb9W8UWhYwtRq2JiHPoVb3_ddFUfDgv1gFXCQtdAJ6cT4sRF83phAUyEoR7BJA07.png)
E.g. if p takes strings here we'll have an error. 
                - An array parameter to a procedure is given type array - **without array bounds!** 
    - Algol 68 
        - Used a stack for local variables and explicitly allocated heap storage. They were also reclaimed by garbage collection.
        - Parameters were passed by value, with pass-by-reference accomplished with pointer types.
        - To complicated and hard to compile for it's time
    - Pascal 
        - Quasi-strong, statically typed language. Rich set of  data-structuring concepts: enumerations, sets, sequential files etc.
        - More expressive than Algol 60 but less than Algol 68 (easier to compile).
        - First language to propose index checking - the index type giving the range of values was associated with the array.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jqiL-HwYE10oEnjtYfRup6My83VHWyaoagtAijbLeHBvlRmcdzMH9voeoOCzLaBz9O7MlCjPFMV7BH-DylbiC3ixKTAFY7Fy5xEUeIlkKD8eWeDLajP6BBBWeqacXHoP.png) 
        - What weaknesses did variant records introduce? ↓ 
            - Compilers didn't check if the value in the tag was consistent with the state of the record - e.g. if it actually had an integer in.
            - Do you update the tag field or the state first? Dangerous for concurrency
            - Tag fields were optional - if omitted, no checking was possible at runtime to determine which variant was present.
        - Similar to struct and union in C.
    - 
- **Lecture 2.2 **(OOP Languages)
    - Basic concepts in OOP Languages 
        - **Four main concepts** 
            - Dynamic lookup is―When a method is called, dynamically at runtime the implementation of the method is chosen. In c++ this is done using a vtable.
            - Abstraction in OOP is―implementation details are hidden to a caller.
            - Subtyping is―Allows values of one type to be used in place of values of another.
            - Inheritance is―the ability to use the definition of one object, to define another one. This saves the effort of duplicating code.  
        - Can we have inheritance without subtyping and vice versa? ↓ 
            - One can  __simulate __ inheritance using #include to avoid code duplication. 
            - You might be able to use an int in place of a double, without having an idea of inheritance. 
    - Behavioural Subtyping 
        - If I have a bag type, and I override it so that values cannot be repeated (creating a set type) should the set be a subtype? Java says yes.
        - What is behavioural subtyping?―Where members of a subtype have the same base behaviour as the supertype. For example, a set subtype will behave differently than it's array supertype - so is not a behavioural subtype.
        - Why is behavioural subtyping important for security and verification?―If I proved properties of one type (memory safety etc.) if a new subtype has different qualities those proofs are useless.
    - History of objects 
        - SIMULA was the first OOP language - it introduced the idea of objects. Initially designed for simulation.
        - Smalltalk was a dynamically typed OOP language.
        - OOP in simulation: 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4SNsVF_-A3SoagoyjrOfh-Ih0rUPj6TNNYvIQPzDR6pqi4ph8bh44pbSeRao52JNqmuVfrvmLVVd1gZhsN9VonCKqCdKwhK2wKfgqDB1N2I0VL4pcYmPkzMlU5F6QZy8.png) 
        - SIMULA features:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FJlHzoUwjlEqz5Z6mgje51xi4hrn8Mxn41O5vQejrkD18t8qN9k8a-UY12ntuU6CQD6XHckRgPsfVBgh7xiNoZFVoitN5vo2oioItHv9aj89cy6Kefyvj_8IA80LMomB.png)  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hGR5XNyviz-e2VV1NOWL-oX9foIr_-_lbboV2_QFEY2y-N6hhpgA49QZbENdcjTI6WNRzjUkihMZn644xWgtCrH6Iegf4zA7Xk27XS-HqsI552fRITY43e3PJ3BU8RLa.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/z0lVl9unT2-WLqdvypjjB82X7JSsf7oLoBIz683-ithOqmkQLWukPuMZgLEMMrg23B0uMp7ATsex2MVb8XO80rWPJ_L2dfoi-vXbjcMl85ZFhGIq02jNRk8X4_xW1dDF.png) 
    - Smalltalk 
        - Abstraction via **private **instance variables and **public **methods.
        - Everything is an object; even a class. All operations are then messages to objects. Dynamically typed. 
        - Most implementations of Smalltalk were based around IDE environments - with prompts to click places to add classes/methods.
        - Explain what the following Smalltalk code is doing and how
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LeZWdbrsHSZ9aze4DCkuTHKKN9Mmpmc2jq-Jd3Uf2FT1L0i8__RHe-_WzYvjt-jDz0TJF6-aUOQ62wuQ_fqj2jOI8r0Et1QVArg8VRH1IawsDV-FPnnl4flYbU9x5uhb.png)―This extends Integer with the method myfact! First we check if the integer we're dealing with is 0 - this produces a boolean. 
We then send a test if that boolean is true or false, ^ means return.
If the boolean is false, we first generate the integer (self - 1) then we pass myfact to it.
Passing myfact to (self - 1) will produce the result of $(\text{self} -1)!$ which we then multiply by self.
    - Reflection, live coding and IDEs 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R4VOh4BxHL0LWlTNkRqomOZchR4m7BDGPYnVI19PiQqCf9EZNZbLfPyAltnwbTXAL_UndKPGivuzqJyLyxvzpLWDh5PeWlQn-IeZ7QGgLWtJwgM0hPy8ydtTlyCDqf64.png) 
    - 
- **Lecture 3 **(Types)
    - Types in Programming 
        - A type is a collection of entities that share some common property.
        - Three main uses of types
            - Naming and organizing concepts
            - Making sure bit sequences in memory are interpreted properly
            - Providing information to the compiler about data manipulated by the program. (e.g. integer addition vs floating point addition)
        - Can be used for many kinds of optimization
    - Type system 
        - A set of rules for associating a type with phrases in the language
        - What is a strongly vs weakly typed language?―Strongly typed languages have a strong type checker, that is if the type checker allows a piece of code then that code will evaluate with no type errors.
A language is weak if it isn't strong.
 __To have a strong type checker, the language will need certain things  - like explicit typing etc.__  
    - Type safety 
        - A language is **type safe **if―no program is allowed to violate it's type distinctions.
We can violate them in C & C++ with type casts and pointer arithmetic.
You cannot in Java, LISP, Smalltalk... 
    - Type Checking 
        - Used to prevent some or all type errors, ensuring that operations in the program are applied properly.
        - Can be done statically or dynamically. 
        - What is expressiveness in a type checker?―- e.g. amongst safe languages, how many strings are accepted. 
One strong type system is the one that rejects all programs.
    - Static vs Dynamic type checking 
        - How are dynamic types achieved? Pros/cons?―The compiler adds tag fields to data representations, which can be checked at runtime.
Lower compile time, slower and more memory used. 
Can find errors at runtime that static would miss.
        - How are static types achieved? Pros/cons?―Compiler checks the program text for potential type errors and rejects code which does not conform.
Faster code and finds errors earlier BUT may restrict programming style.
    - Java Downcasts 
        - Consider the following code: ```java
class A { ... };
class B extends A { ... };
// Which of the following are allowed?
a = b;
a = (A) b;
b = a;
b = (B) a;
// Each line executes independently.
```―```java
// You can think that in assignments, we want to keep the left hand arguments type the same.

a=b; // This is allowed - its an upcast, cast b to an A and then assign
a = (A) b; // Allowed. Explicit upcast

 b = a; // Not Allowed! Non-explicit downcast.
 
 b = (B) a; // Allowed - but needs to be type checked. Explicit downcast
``` 
    - Type equality 
        - Want to know when two types are the same.
        - What are  __structural __ equality and  __nominal __ equality? ↓ 
            - Structural equality means we could look inside the types and find the same structure of bits and subtypes. 
            - Nominal equality means they have the same name.
            - ```java
type x = int * bool;
type y = int * bool;

// Structurally equal but not nominally so.
```
        - What are **transparent **and **opaque **type declarations, and what do they imply for type equality? ↓ 
            - **Transparent **type declarations are when alternative names are given to already existing types. A system using this would require structural type checking. 
            - **Opaque **type declarations means when a type is added, it differs from any other type. Implies nominal type checking will suffice.
        - Examples 
            - In C type equality is structural for typedef, but nominal for unions & structs.
            - ML works similarly to C/C++, structural equality except for datatype names which is nominal.
            - Type equality was left ambiguous in Pascal.
            - Modula-2 had the following rules, two types are compatible if:
                - They are the same name
                - They are s and t, and s=t is a type declaration
                - One is a subrange of the other
                - They are both subranges of the same basic type
    - Type compatibility and subtyping 
        - Explain the difference between type compatibility vs type equality―Type equality is symmetric, whereas in type compatibility we are interested in a one way relation. E.g. can we pass this variable to a function, or can this type be cast to this other type. 
Do we want an age type to be assigned to a weight type etc. Int to age makes some sense (to perform calculations) but age to int is more sticky.
    - Polymorphism 
        - Parametric polymorphism - a function may be applied to any arguments whose type matches a type expression involving **type variables**. 
E.G. (an e.g thats needed but  the lecturer didn't provide) append  [a] $\times$ [a] ⇒ [a]
Where **a is the type variable**. 
        - Subtype polymorphism - a function expecting a given class can be applied to a subclass instead.
        - Ad-hoc polymorphism or overloading - Two or more implementations of a function with different types are **referred to by the same name**. 
E.g. add(Real x, Real y), add(Int x, Int y)
    - Type inference 
        - Process of determining the types of phrases based on the constructs that appear in them.
        - Describe the idea of Type inference in ML―Give every expression a new type variable, and then emit constraints $\alpha \approx \beta$ whenever two types have to be equal. 
We then unify these constraints.
E.g. with inference rules: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cghUV3AFlGOJeG6oMb1_HQcmRKea9SmbgQ3nyGyt_xX0IesvB5s-V38nfbPCABcByFQKO1H6qFWRZ75Ta8nSLc06QDXmfllhiExtMRdD74Vw7qZfcWIqbNBrAjGCj_Vo.png) 
    - let-polymorphism 
        - The 'obvious' way to type-check ```kotlin
let val x = e in e' end
// Is to treat that as:
(fn x => e') (e)
``` This has issues, e.g.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ea4bJSJt1p8X2YjDkzrJeYDOqwiMWxsVtvHs0urhiflM6Itbq5Tz61c46VB7fAe21vVZOSzbT3lWykb_AL0GWtrEzDwHy2dLrGi4x5SK-lDDBjPef0YOLUGQwE64XWrE.png) 
        - Milner invented a more generous way to type let-expressions, using $\forall$. 
    - Surprises/issues in ML 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QixtG7r9PccH80MpgAWiWipI6m9ZXiP0tMEbScOq9o0yWfqm12eGSl1YF59dKUXAp8h_pLETdNJX4yLof0Preai05rllTaQ0pPFilGRhVVw6Hh9qMixafOKCrke5-Oag.png) 
        - This is a problem, because the type of x changes from a list to an int list. While this will fail type-checking, we need to be careful of things changing behind our backs.
    - Polymorphic Exceptions 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YPvMWprgg__EQ_7dcsHHFqVKbwl_zUXxLuK_jpQwK5MVujBXHe67qY0rbT3MQpasQxogfiNXvqdvyz0tmzIm6mI0p8yYUHG7npxpvyDCQCdiaZ_6iZYB0zZPyNc-ZdKy.png) 
    - Interaction of subtyping and generics - variance. 
        - Given String is a subtype of Object: 
            - String[] be a subtype of Object[]?
            - Should ArrayList<String> be a subtype of ArrayList<Object>?
        - Given a generic G, we say it is {{covariant }}if G<String> is a subtype of G<Object>. {{Contravariant }}if G<Object> is a subtype of G<String>
And {{invariant }}if neither hold.
    - Java arrays are covarient 
        - So String[] is a subtype of Object[].
        - How does Java handle this subtyping issue? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j6p3uqnvDrh0qA2BAHmh4Rl7PQZexr_wBWUdHsC7swT8hj-WKQyRJBJryARkPp6fQ7hjAa0JV5V-OKbN3BZ5yf86jiTYF7x2qdBdJjmZDvDW1sjbA_smRbgqYgxuHe0r.png)―All writes to a Java array are type checked to ensure it's a subtype of the **array they are stored in**. In this case a String array. 
There are no problems with reads.
This means you pay a price every time you write - this was changed for Java generics.
    - Java generics are invariant 
        - For Generics, what would fail to type check here:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VQnn-BBhaf96LTNCVWOZq7-eZgrfHIxp3va12S1euKTybogITCM1ycXhrqezKG5bI4xt45H-d0_qh8XuL4_E_U_8NVigGF1VYhT8yQb8-uHnkudOadqneTuzT9SLUt6Z.png)―o=s would fail to type check, everything else would work fine. 
This would fail because o is a subtype of s, so s would need to be downcast.
        - So, generics are safer than arrays. But covariance and contravariance can be useful.
    - Java variance specifications 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RPIcnJ7o3WyMC29z9f6qZvkHbKljADSHk8tj5T8_3ZxHMbBRaqL0QhdAPKNHl6XJO3WipTWKCK5HBAfEC_OVWx7rDdth-7I8tBK_jiBGwa2-n5tKQ8SQj0rMPBmO1x6A.png) 
        - What is the trade off of using ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W_IT6wm02cJ-PEUZDsDi-xFaOQNJBoa9jUVcbZI7VbSrtJWntLVK61yqRsK-XoiiprTRT8EQ5Ok11aqysj-n1i6UsBZVoh9z6fZgR2Idz7DKDSS0N9J_wJzGGyQqoCe9.png)―This makes o covariant, however we cannot write to elements of o. We can only write to s. 
    - 
- **Lecture 4 **(Scripting)
    - Scripting Languages 
        - Scripting languages are generally created to automate human tasks, a script is then just a program written for a scripting language. 
        - The definition is usage-dependent - ML was originally the scripting language for creating proof trees. Similarly Lisp is the scripting language for Emacs.
        - A scripting language means essentially "language with a REPL" or a "language which can run interactively".
They are generally {{dynamically }}typed or use {{type inference.}} 
        - Some static languages are also used for scripting, with type inference and lightweight top-level phrase syntax.
    - Executing code in browsers 
        - Java applets were―a system where Java code was compiled to JVM bytecode and then run in a browser sandbox. This was a security mess and unloved by Apple & Microsoft as they want to keep their apps behind a store.
        - Alternatively, embed Javascript source code and JIT compile it for execution. Then talk to the browser using the DOM model.
    - Javascript 
        - Originally called Mocha. Designed and implemented in 10 days. 
        - Dynamically typed, prototype-based object system.
        - Has both OOP and functional language features (including higher-order functions)
        - Implemented within browsers. So has callback style approach for use in browsers.
        - Language inspirations
            - Java for syntax
            - Scheme for lexical closures
            - Self for prototypes instead of classes
        - Why did Javascript avoid classes? ↓ 
            - Much time spent defining classes, before even thinking about objects. 
            - In flexible design style (agile or spiral) you may want to change the design of a class as you go. This can have problems, as classes who inherit from you will then change too (the  __fragile base class__  problem).
    - Prototypes instead of classes 
        - Describe prototypes in JavaScript―When a constructor function is defined, it acquires a prototype property initially an empty object. When a constructor is called, created objects inherit from the prototype - we look in the object first and then in the prototype - then in the prototypes prototype and so on up the chain until we encounter null.
You can add properties to the prototype object, or replace it with a different object.
        - What is duck typing, and why do we need it in Javascript―If we don't have classes, we can't check the name of our class in Javascript. E.g. we can't test if (x instanceof Duck)...
Instead we check if x quacks like a duck, walks like a duck etc.
We take a structural view of the prototype and decide if a prototype has a certain number of duck methods - then it is a duck.
    - The JavaScript DOM model 
        - JavaScript needs to be tightly connected with web pages, how is this done using the DOM model? ↓ 
            - The browser converts the HTML into a tree of objects representing the HTML page structures. This is made available as the JavaScript variable  __document__ . 
            - Executing JS code reads and modifies  __document __ which the browser then renders on screen. 
    - WebAssembly 
        - JavaScript is the only language universally supported by browsers. So various compilers have been developed to compile from many languages to JavaScript. 
        - But JavaScript is a terrible compiler target language. Instead use WebAssembly a machine-agnostic safety-checked assembly language JIT'd in the browser.
    - Gradual type systems 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FxpogsRGADiOOolbtugV1Sgtyz4WmTSSpFwtCHvFiyYrgQhAHo2UH3uHMBTWbTE70RdjRR3P1DmkosAdDH5ll_GPOtDaRK7GuRF-EFZ6UrEbnxuNy2ozcsYmJpJi9cRb.png) 
        - Statically type languages are better for large programs, why?―Cross-module static checks and documentation provided by types.
        - What are gradual types?―A language in which small programs can be written without types, but the IDE encourages you to add types faster than software rust overtakes your system. I.e. PHP to Hack at Facebook.
Some variables are given types and checked at runtime. And some aren't, so their correctness is dynamically checked at runtime.
        - 
- **Lecture 5 **(Modules)
    - Need for modules 
        - Why do we need modules? ↓ 
            - We want structure in large scale architecture. 
            - We also want to control name visibility, excessive visibility increases the attack surface for malevolent use.
    - SML 
        - Consists of two sub-languages:
            - The Core language for programming in the small.
            - The Modules language for programming in the large, by grouping related Core definitions of types and variables into self-contained units.
        - What is an abstract data type?―A type equipped with a set of operations only applicable to that type. It's implementation can be changed without affecting the rest of the program.
    - Structures 
        - What are Structures and Signatures?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZegvmLiSqEKTLBSayzTVRWh2d71xyq2h91xR-HfHMntpnO47iZjQe5ybNtmD9hHhCo1QFeZ5lMuYq5TjEjEfmDTmbkkM0bE8DrT0hU8FtciH3Kl-Sii_knJ5kyLnUojV.png) 
        - We can encapsulate a sequence of CORE type and value definitions into a structure. We enclose the definitions between the keywords `struct...end.` 
    - Signatures 
        - A signature consists of a sequence of component specifications, enclosed between `sig...end`.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iqGCwLnMlQU8j7-anw9KuYayQ_RyuI9OxmX32g-E51ovhB5V8-HBaIgHCiPxBbgEL5qtiIMBrkW8FXwkb6f6y4YZGE_2tBkejVNHKdGgDEM0Pafvj-tpg9GLKMPGvslQ.png) 
        - What are opaque signatures?―Signatures that give more freedom of the implementation of the structure:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8TSoTI-au2SIgogwZO-3_B_vFuCPbW5J4QeTzHLPEnDIic43YzTZL58Wse_oGoePo5sYi7WQ_L0CYWYX_J68zd-53MKODDDEKmZasMCI2j4LXnBXXyt3PnhNMjRjiTqu.png) 
    - Naming structures and signatures 
        - We can bind names to structures and signatures using:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/oRP7oIR_wDoLOTzAWPsBcdxCjcgo4P9tpmyzdM8NEmfqRsbf94RoeCfmE9gMidougAwY_c056snznQWXtPn-tcj-nH04EiBrqgy3ju3qBesbiSDVedoHgUTS875sCEcr.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R629rgFM01lg4u-oLtGU-mZdxsYT_j7GSg6wPPX_hCwJLopMIBaJy3ybzAAAn88ZZr0pnQX9SuhsDG8HYrzd2SPjIBnXh-TJZXt1NuBDNHwlS1ZnNfNtE7bbNQaCQNUI.png)
Why is split not exported in MyStack?―It acts as a private method that is part of the implementation. 
    - Signature matching 
        - When does a structure satisfy a signature?―When it implements **at least **the components of the signature. Can have private state/methods. 
A lot like subtyping.
        - Describe signature constraints―Take an already existing structure, and create it using a new signature which constrains the defined values. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EgyC3CuAR1XDSoQ4wp2AJC2B2-Jp2M9ZUY4oK2uXI_l1ulZ9aoEujZNrEIBUQ1G5nas23VXADqq4wN4sVDJoyRub0z1wj286S8XQbbj18tsKza9Br5S9Th4uRCjORGXV.png) 
    - Signature Constraints
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G9odY2Z0wrknPNqTPdfH-Zf09nCYPFxv7TYZNEaSywyWpGmng5u0orU30mLI2dccywnjW0CARG4ff9h0T3xAXZ7z8seOjxgaiecy-t8SDlm-u3SnqvqBGaPRUrROcYZa.png) 
        - What are opaque signature constraints and why might we use them?―These hide the identity of types. We might want to hide that our natural number is based of int, as otherwise someone could store a negative integer in our datatype (a.succ(-3))
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a3mWUWvi76k-M2xayUz6HWHB7wYFW2a5UODvtt0p4SqnJpwLbnh0Dj_JP2mFrnNFEy2r9BLwiM0BLovIZbPCneevLr8DiE9CtWzHBScJ1zffGgWftXEySLCx3CeUCKS8.png)
So AbsNat.nat ≠ int. Even though it uses int 
    - Nested Structures and signature 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/X2ekHF7PqPGe8dFi6zYyJItcn7Ph26o_foV3s-6YWfPqFnyqs6V5zoNdz_0u_BFoqWLSidpRJFFZjO7g56iwUdR8ZdlpsqZofsXIDJ0sN34_oWK87JPJ8j8syVEfF_Y2.png) 
    - Modules in other languages
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PqZH4ZI_DTqYs3zjI_eykyI_4sWp76yqHsh-LarvyiKWNO5L-RVPt4z0OaNOa5guZZwfc-xWrx8X5SnhWpSeEvPiBpE1FrFSyT8-KioXIBAsR4GevhqmBvHs01iEq4A2.png) 
    - 
- **Lecture 6 **(Concurrency)
    - Painful facts of parallel life 
        - Single core clock speeds stagnated for last 10 years. More transistors, but no more speed.
        - Inter-processor communication is FAR more expensive than computation.
        - Compiler **can't **just take my code and parallelise it!
    - Painful facts of timings 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3PbZIo0g1zJeny5V0iYAg-o7z5ktKcrJLJU8HX0OM0uD1bNXc5wdMBvDbQdKrzHoV44ex1Oh-PFDhr9hEs2ilWxJ0p4MoWfoqmBqDuBuZD5zsXsiuTeobaqjnhln1t5j.png)
CPUs have sped up much faster than memory. 
        - With multi-core:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YQ3RZRAcdtlem_z_NVImEH1H2ugHckHIxefOdOBCbP7jSxnNeHF3cYrWnWs6TwIVPkU-3U433rSeufAsHuxjPlBlIoZYV1HoVBr4hkZqe74LsTvGjzRpnFZw_4Zwywqx.png)
Why could communication take up to 400 cycles?―If CPU 0 writes to cache 0, and CPU 1 reads the value - CACHE 0 needs to flush the value to memory, and CACHE 1 needs to then read that from memory. This takes 400 cycles. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bewosUDp2xBdZhWTtblrrO1Q5MDocEd2qvb9rBUywqv2SFYxMJKRdDB0wW3ktPaJt3bMdiHFCwK29kszr0Zv-vp-AY18qrBceSkFatMf2NyB02V9suHyvOJ3z9LWx-PV.png) 
    - What  __programming abstractions__ ? 
        - We've got more and more processors available with each device. From on cloud to on chip.
        - What are good programming abstractions for a system like this? 
        - Memory is local to the processor units, but message passing between units is much slower.
    - What hardware architecture tells us 
        - Communication latency is far higher than instruction execution time (2-6 orders of magnitude depending on if the core is on/off the chip).
What does this tell you about the number of instructions you should send?―Have to send at least $10^2$ instructions and realistically more like $10^4$ for it to be worth it. 
Long-running independent computations fit the hardware best.
        - "Shared memory" is an illusion. Emulated by message passing in the cache-coherency protocol.
        - Often best to think as CPUs as distributed systems. 
    - Communication abstractions for programming 
        - "Head in the sand" - What communication? 
        - "Principled head in the sand" - leave this to someone else
        - Just use TCP/IP
        - Shared memory, message passing, RMI/RPC?
        - Communication is expensive, expose it to programmer (No lies about shared memory).
    - Concurrent, Parallel, Distributed 
        - Parallel for computation and concurrency for what you have in your language.
        - Concurrent behaviour can happen on single-core CPU, but true concurrency different from interleaving concurrency.
    - SIMD, MIMD 
        - What are SIMD and MIMD―Single instruction multiple Data = GPU.
Multiple instruction multiple data = multi-core CPU.
        - Most parallel systems MIMD
        - GPUs are SIMD, so Programming languages for GPUs differ.
    - Oldest idea: Threads 
        - What's wrong with Threads? 
            - Give some problems with threads >  ↓ 
                - Need explicit synchronisation  ⇒ means they're error prone.
                - Because they're implemented as library calls, the compiler cannot work out where they start and end.
                - pthreads are OS-level threads ⇒ Means we need a context switch which is very slow.
                - Number of threads generally hard-coded into your program. 
        - Cilk Language 
            - What is Cilk?―Cilk is a superset of C that adds concurrency with threads:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CwXc9qkvj9JkRxBSE4YFWruC9Pr0H_lVcGassLNkEDLDY1J38X-kjfdlQHhGOK_Zn_kiNnLCcoEDIT-ob2srF0NihSocx94CgnoTOdBiQaH9ts1Oo8_u9zPvf_I832xD.png)
Note that there is Compiler management of threads.
            - What is OpenMP?―Again a superset of C, where you can indicate to the compiler what to parallelize and where:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p8dNLLP_xB1bAkghZEMd0slaJu7xf7Am4_-RB7OidPg6KYC-ouwN9wMf4UxOdCy3IHwQEO1JOzyAQVgc7QCPN44RrhaCITvmFhy0ns0K-aRGwUS8J0JSrEO30K7Bg5JU.png)
Note, assumes shared memory. 
        - How do you implement threads in Java?―Either extend Thread or implement Runnable:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fM3gwMC0EL7Utr2Ft1BYX4VUPwZnMAGpJz1cg6FW5RYwr0OlOI0PqqIxKHZGP85bN34cqbk9x6GseCh5hIh4UCBDkxr7iydxq4yprzGltHWnZEHheNj3EHz3WghtbwEL.png) 
    - Clusters and cloud Computing 
        - Cilk and OpenMP centre around shared address space, here we need **message passing.**
        - Software support for message passing: MPI 
            - What does MPI stand for and what is it ↓ 
                - Message passing interface
                - It's the standard for communication among processes on a distributed memory system. 
                - Emphasis on the expensive nature of message passing.
                - Does a **sweep of computation** and then a **sweep of message** **passing** 
        - Erlang
            - What is Erlang? ↓ 
                - Language with nothing shared, based on the actor model (Asynchronous message passing).
                - If tasks reach a problem, they just commit suicide and hope someone will fix things up. 
        - Cloud Computing 
            - Can mean doing one computers work on a server (e.g. Google Docs), or massively parallel combinations of computing  
            - MapReduce invoked in a search engine, where a search term matched against many computers (Map) and then combined (in logarithmic time) using Reduce.
            - Why is functional style preferred in parallel cloud computing? ↓ 
                - Functional style (idempotency) useful for error resilience. Can easily restart computation if an error occurs (cosmic rays, etc.)
                - Here idempotency means, we can restart the computation with the same arguments and will get the right result. (e.g. no permanent state change due to error).
                - Additionally, every tuple and argument list **can be evaluated in parallel!** 
But need to find big units of work to make up for communication time. 
    - Embarrassingly Parallel 
        - Programs with many separate sub-units of work - where they don't interact and the data is large.
    - Garbage Collection
        - How do we do Garbage collection over multiple cores?  ↓ 
            - We could manage data structures so they don't move from one processor to another. (not always possible)
            - Parallel GC - stop the world and do the garbage collection in parallel
            - Concurrent GC - do GC while the program is running (Hard!).
            - Incremental GC - track imported/exported pointers.
    - How have languages adapted to parallel hardware?
        - The hardware change of adding new cores was **huge! **But programming language support is fragmentary. 
        - Concurrency and mutable data structures seems too hard for programmers to use together in large programs.
        - So languages have evolved to use more Function programming ideas.
        - Describe the difference between internal and external iteration ↓ 
            - External iteration is where the looping mechanism (the for) is outside of the body. E.g:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XhX8NT8XbrVP2nH-XmvepNDle3CUESPUyzlxrcrbaKG0lMna0KCjKwgYAQZzgvtgxn3wZ1W8BtskWhEpJS2RwEUky_OHyrWzDFwHZ2cew6K_xUp4RAl51RvUGLuvEbsG.png) 
You need to do the parallelization yourself, e.g. converting to:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pKs52Cqz7ES0RypFDYxe9i58btc9IhXNJFwadEapzb4NjPgqGsEtpfSWK-vlYEn0u-PfQy0TCOC_-Efu_lTWHV3ZtnFPRy879VxiyiXVwDidM21kPPBe2siIGdSKin5q.png) 
Which takes **ages.** We don't want to do this. 
            - Internal iteration means the iterator is built into the library, and the body of the loop is done on top of that:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GY-WSHnwDiVlczM2JjeTXG76bP3kNGLfcTtkCC-xpd7f7yzrMCcawRdFoEf648jc9vKfh90W8cGJ8CIEoecsvXOc8q47rO_LifksL55bf4r86zPM3tsCY3ZUHxMG3vM7.png)
The library can then optimize the iteration based on the number of threads available. 
        - Java Collections vs Streams 
            - How do Java Collections differ from streams?  ↓ 
                - Collections use traditional for loops - internally using mutable state. 
                - Streams have lazy allocation, items need to be in memory all at once.
A stream pipeline traverses the stream only once.
.parallel() authorises arbitrary order of calls to the stream pipeline! Good for parallelism.
            - 
- **Lecture 7 **(Scala)
    - Scala 
        - Describe Smalltalk's main features  ↓ 
            - Minimal expression-oriented language (cut everything to a minimum).
            - Smalltalk-style "everything is an object". 
            - Unifies OO and functional language techniques.
            - Rich polymorphic static type system, without NULL.
            - Can write code procedurally or declaratively.
        - In Scala Array selection is written in {{functional notation}}. Type declarations can often be {{avoided}}, with var used instead. Higher order functions exist, using ⇒. 
    - Parameter passing
        - Scala uses {{call-by-value}} by default, but it switches to {{call-by-name}} evaluation if we put ⇒ before the type. 
        - How does this while loop work? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x1V_cxWm8wCRg6adNkARK2gBwGJOW-JgREP6wG6rZDYYIAZcRg3oriOyimXD1rZYC9j36uHW7DlaWtjjLg-zpDCstRZjE6ZCejgudshuQudaM1h71Qr3U-5JpadEUe19.png)―Works because of call by name, cond get's re-evaluated and comm does to - where comm would be the body of the while loop. 
    - How lambdas are implemented 
        - What would ```java
 static int test(Function<Integer, Integer> f) {
 	return f.apply(1)
 }
 
 k = 10;
 System.out.println(test( x => x+k));
 k = 20;
 System.out.println(test( x => x+k));
``` Output and why?―It would output 11 and 21, because when a lambda is created it binds the local variables it doesn't pass them. In Java this is how lambda's work.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZhgssnL6HDTonWt8LxnjkiNj2ujIEmZwm4CZuRadDwYODg_fgzte8ZIWFpEImhWlfWVUsUVF-6j1y_ClURiKF70IcD6encUDk43Sx9FtgNLQDOJzz1FSejAlIr9RXpDi.png) 
        - Describe named classes for use with lambda functions―You define different classes, which take and store a free variable, then implement apply which uses that variable for computation.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BR2PeQ2PsqkGDcpmkxOtfNfdlRafSMgUdQtvghRbqgXBi719Jaof_8JabYL21NOAk8kIcOyy1UDwK9kT5q9LnQbnY6b_WkBKuKH6Cu7IW5MCRqc39rdSLB265h2v9Afa.png) 
    - Function types 
        - What type is this function in Scala? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4rM2zsZ4zlDi36-C9PiXmk4RyOft6Gvs5o9j6pcxS2lUv9m1Ssl-dsILvQ8smkpvdRf-SqqJw4IAOEFxoZlP2JGmVkrvCn_gz-w-FFVM8gt99r_skY1K4gxSsDdtqM8Y.png)―Int argument, Array[Int] argument and a Bool output.
In general `functionK[a1, ..., aK, a0]` 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8KtVcynUhJ5UbQbRddJgLGBxw3P3QTmaMp-LyWSFOIMJ22fSmyw9AvLy8W1MY9uICZHK6RBWlsNF07T_vMCJIT14i3aqR6L6JJK9fqm-2y6qMS9cw3ccflzaYn4078El.png) 
    - Data structures in functional and OO style 
        - How would you define a tree datatype in functional (use Ocaml) vs OO style?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uSY2EB5j5yT0Xf71h6JFTtNZto95GuN8OwD12FFqpGH2C5iSfzBnhjUqfqiAOx4fGY6Rd7TL02toOak15LZnXuuki_x0A2Tmj-pqvgfKRkEdA7yD9ciOYJ7XI0Yd8XzO.png)
Note that these are the same at the machine code level.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6wJurPE0hxKO3xJeLoiktGjjgpWG8r7KmE37t7SuMWKKZUm6kiofFC156GuEOFNxR-81ICDlVYr8OTK1YK_OyqnjX4MWst3U-EKzFg-DPMiQxAzUQSwwI8uaP6q_T9Pr.png)
Is it easy or hard to add new forms of data to this scheme, and is it easy or hard to add new functions on the schemes.
Additionally, describe how this changes for a functional version of this. ↓ 
            - This trade-off is known as the expression problem 
            - It's easy to add new forms of data, as the types don't interfere with one another: ```java
class Prod(e1:Expr; e2:Expr) extends Expr {
	def eval: Int = e1.eval() * e2.eval()
}
```
            - It's **hard **to add new functions to every type - as we'd have to add them to the abstract class and then implement them in every subclass. 
            - In ML we would have the opposite. 
We would have some ```java
 datatype Expr = Int of int | Sum of Expr * Expr | Prod of Expr * Expr;
 
 let eval x = 
 	match x with 
 	| Int y => y
 	| Sum a,b => eval a + eval b
 	| Prod a,b => eval a * eval b;;  
``` So every time we add a new datatype **we need to update EVERY case match. 
**But new operations on the existing data is easy. 
        - How does Scala handle the **Expression problem**?―Scala allows the user to implement OOP class inheritance and function implementation - **while **also allowing the ML pattern matching. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_Eezr-yPKzpBdMebfyw3-MWjMSXXUOE_T4PyuKC03Vo974ya-2o_hG7y0jM5B589_nA3wmNvzrXsbJD4aNBur0HgmzTgzpnjEEfNuBmNuqRkMfD6-zBesJZ8VJRsnc67.png)

So you can choose which way you'd like to jump in the tradeoff. Easy to add new operations or easy to add new datatypes.
    - Generics and polymorphism in Scala 
        - How does Scala handle the question
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8bkgjVIrudRNd3q_vk2nlPNvRD5-u5nQkTbArc0YRCX_HRBbpAZ_W0WMwOMu9QKAdPGyuv-Uf-DEg5V0_cSISK0izm3JbZmbG1QgubwB7nTEUnI8WP5ofcaRSeJMUL_G.png) ↓ 
            - By default, generic types are non-varient. E.g. an Object array will **only **allow Objects specifically.  
            - But Scala allows for covariant subtyping by prefixing a type parameter with a '+'.
            - Prefix with a '-' for contravariant arrays.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/k1Zm5OU1_wVCIbN27U8pA0gmbEY9nk_icJ59JcgJxd8kwJNJs-OwBxc5M9UDiiNlFjYh9dB-IvW9SXrNfROFBzUJSjQS4lNNWWv5PFC7wKPl9X6Lzgz3vVKRVY4R00TP.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/USoTd7xmfTu9pG_6o-O6-pUhP860sAR4hr1eWFvP2IhSXgcoZrchkeSPJYxIga8qwISFHv6S6-c5RegHEFOHPjByLWj9AT7Lf4JDlbeyCG9e_dNMRONcMj1Fl8SAVb6h.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EyXRcuCaKw-OmzTL4yj-1_xlcvw_qEEwPMLOkN9s6KI5HrGhTllAp0VScxOXH5DOInrkChEnP7DynwHu35W9acGXl0_UuXiIq0FvHKih4cC6AU0qrXcLmRxHKR2gLQky.png) 
    - Value types 
        - Describe a value type―A type representing a pure value. They can be compared, copied and their subfields examined but **their subfields cannot be altered**.  
Note that this differs from reference types (Integer vs int in Java). For example for reference types one new Integer(1) is differentiable from another new Integer(1) as every objects has identity.
        - Value types useful as more and more functional APIs are used. 
        - In what two ways can you model a value type in Java?  ↓ 
            - Use final to stop modification
            - Use a deep copy to snapshot values on operations
        - These are both fragile during program enhancement
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OYHQTjwbnwG67-KVmJ491SGRBvDwOKF2_40V1_rQKr0MPuvjc8wJVbYB_boIJ7-T23w49WN3VXqQodAz6S1VczTmd2VAJSvd-agkNDDx0gQITdYWmsEEhrfbg_oBUp9m.png) 
    - Value types and inefficient representation 
        - Why are value types inefficient in Java?―To store 100 complex values, we need to store 100 pointers (800 bytes) to 100 complex types (2400 bytes).
All we want to do is tore 200 double values (only 1600 bytes).
Costs java in memory use and cache effects.  
    - Aliasing and mutability 
        - Aliasing and mutability together can form subtle bugs (concurrency leads to insane bugs). 
        - We would rather use mutability as we like, but use deep copies. OR use aliasing or make data structures immutable.
    - 
- **Lecture 8 **(MONADS and other random shit)
    - I/O in functional languages 
        - What's wrong with having side-effecting I/O work left to right as normal in Ocaml? Whats the problem for Lazy languages? ↓ 
            - e+e might not give the same result as let x = e in x+x. This isn't how functional languages should work
            - Lazy languages only do the IO fetch when they need it. But this means the order of the side effects would vary depending on how the function was implemented! 
    - Giving different types to pure and impure functions 
        - What are pure and impure functions?―A pure function has no side effects, an impure function has side effects.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NEmpaRwSbIZuWekB0T9fw1UwcL8lno48L0Y-OozYHxg0G3jMVJQ1UrGRaybX8BB2n_DUbqoxiX64ziA2n82OitT3-dAzbRmDiaVuSB3zAP_nHyZwcCZmQ15XlD-WouqX.png) 
        - How do we represent give different types for pure and impure functions?―We give impure functions the type $$A \rightarrow B M$$ 
E.g. it goes to B with a monad, which stores the side effect. This is saying it returns a monad of type B.
    - Composing I/O functions 
        - How do we compose I/O with monads? (hint sequence and return)  ↓ 
            - We need a sequence operator  `>>= `(called **bind**). It takes some $a' M$ and a function $a' \rightarrow b'M$ and does:   $a'M \rightarrow (a' \rightarrow b'M) \rightarrow b'M$.
            - E.g. pluck out $a'$ (the output of some function), then get some pure function which output $b' M$ given $a'$ as output. 
            - Finally, output a $b'M$ (the $b'$ is different) which is the result of the function if the initial side of $a'$ were concatenated with the side effects of $b'$. 
            - We need a **return **operator. We can convert a pure value as a side effect free computation: $$\text{return}: a' \rightarrow a' \ M$$ 
        - Describe bind and return in monads, what do they do?  ↓ 
            - Bind takes one argument, a function f and **outputs** a function g.
            - $f$ takes an argument, and augments it with some extra data. E.g. ```java
def new_sin(x): return [sin(x), "we called sin"]
// type: Number ⇒ (Number, String)  
```
            - $g$ takes a (Number, String) pair and outputs a (Number, String) - so It pulls out sin(x) and operates on that and then combines the result of the output.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HRvv9xUJX56WbopM6yUF34T2pVCLYbFPn-JoiCIr10SEpDD02yoryy1e2WTakYo3A4lirOwCjEDpfPMrzU3bmvI-Y-4YPfp0SFbrc5Ly9Bk1rL485Od6-V3F-652MbRJ.png)
This allows you to compose new_sin(x)'s which have this side effect of logging. 
            - Return just converts a value to a base monad which you can start logging with: ```java
 def return(value):
 	[value, '']
```
    - Monad Laws 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sMhG4jK0y8pNX706cxwWo7smwsA4AFosvDb86cdKAV2G9_eyKrJwC2yobwKOJYC0ND4fLYU1qt1SRtaOlN1PlTwtNw_WOKAuoK5DlpG9s3FHftvu9XDUb_cV8dY_AX1U.png) 
    - Using the IO monad 
        - How do we read an integer, add one to it and print the result using monads?―```java
 rdint >>= (fn x => wrint(x + 1));
 
 // This has type unit IO
```
        - To do this twice we need: ```java
 let val doit = rdint >>= (fn x => wrint(x + 1)) in
 	doit >>= (fn () => doit);
```
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JTvVPtxenf7AhqcIURMLv7jfu4nJUmuMDcaPeH4AFxKWUlsiyASWc-1wZZv7XCj32q0hltNMKZwZL7aHgoDtlReJ3HTKqTJKweYMr86vNGazMkN4JupXW791F3BgXhHC.png) 
    - Generalised Algebraic Data Types (GADT) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iAHYPdI1-Jy3oVnn1ayYBKJUeaEutG6srUYs54in1HDRM8V0oU5zoAmrzokjW86zwI-t2E5FRtJmnk8Qj1WU79XTEYqubEgOPyrjXS1lNO7uc6oWqcTOBNppSArGpyhV.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b3cZAuydQ1Ynbutxqi25genuUUak14TO9VgejDVUBzDQSkPBdwNQN0yLxnRuWfzJdUYY8q4UjSh5PIq5Lo5VCgaozU4R29EZJdVvBg0CvmxVNZZ9EuRWjfJIGOGwzRjY.png) 
        - We can type check when values appearing in datatypes work correctly. We can ensure add and equality are used correctly.
        - We can write eval where the type of the result depends on the **value **of it's type 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S5UxtOZkHEvDs5sJiXmhHDRPFm6f7BB6qzgCv-PydsunjyU8wdJ0wdASO-mjGg_2juwh-roXkGrBviVXLyRI1FGfBh7gGZu_h8tydi4mQioyfLReTnVivcGG433My2V2.png) 
        - GADTs can type more things flexibly than in the standard ML type checking system.
    - Reified continuations 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9GqoVc8Fe_yZVAEVUoQph44mtrnJQkiPo98LUpzja2sG-GbKD0IkQnXbNDz8N7U3BJUpmHTcqPNO97XZ9XkSNYemg9MN1V2zrhxKr-sX-9s35mjwZN7Q_K_Tpn2ouqbI.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kqQ7Krzefk5dfNR-bDIxnCkpNPxz-ppmEmd5SFU3k6q_XemCvDlpHDhJvUF1ARSydLtLkbq2Zl4qbIWWMXz_kD4eXCwEdlVspWSGQpoTreuGGyK7ShR8J_FFHFxAYi0g.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KUfD-S3VPJwMAQk_Y-ga4cFYr65LxayD-zBoufdR_kd1LU3lV_eIq5vzc5P9VlL2wuS3EnBVLie4iqdP3PY2HbPPE63VuLCPSbnjOtly_EgHapApqOyKJob_g9LJhfOj.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZiszufrylJEAsZbGk888x-1vRXLka63aBr6VFLISnaXhLZEGLxtH1LHVz0WIynwVzO9IyeDtvR-x47cy16vEzmQGCY3I6czZ-eKovPa6gpihGO5WAe44TFaN8xdXTbRa.png) 
    - Dependant Types 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TX4OVXDt685PuAAmAkwZEgQJDXpNTnsA2cE0Ir5w0fqAr-qm38bppVOK93uNALeW5E4sv2eld-vBImOOh5ILGaK_TFlmL7QiJlR-yetWHAjzyivZ9exr5SDLoJPxU92w.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RBaCqJXkoxDvwpclGOVIj_wfzk2l_TADK4LMC6NrhLicJF8pD8SDlyaQscyLEdWg4h-7joBwwguWIv45lI9qEVDcRmHNI9AOjDBlU_PnNIwG1Ny6lODXjeUReK0LTxA4.png) 
- 
- **Supervision 1**
    - Tim Questions 
        1. Abstract machines are an idealised machines which execute the programming language directly, for example the JVM. 
        2. Main Concepts of OOP - Inheritance, Subtyping, Abstraction.
Inheritance: Code reuse by inheriting some or all of a parent class.
Subtyping: Subtypes can be used in place of their supertype.
Abstraction: Callers don't have to know the implementation of a class/method.
        3. Subclassing means you inherit some or all of the attributes of a parent, you cannot necessarily use the subclass in space of the parent. Simpler code reuse.
        4. Strong typing - this means that the type checker for the language is strong. A strong type checker is one which will never fail to catch a type-incorrect string in the language. 
Note that certain things might be needed for this to be possible, such as explicitly giving variable types.
        5. If we statically type our language, that is we specify the types of all variables at compile time then a strong type checker should be easier to come by (might be a requirement...). But you can have a static and dynamically typed language which does not have a strong type checker (the checker could be buggy). 
    - [2007 Paper 6 Question 7](../y2007p6q7.md)    
        - c.) What is  __aliasing __ in the context of programming languages? Explain the contexts in which it arises and provide examples of the phenomenon.  
Aliasing is when two variables reference the same physical location, possibly without the knowledge of the parameter using the variables.
This occurs in pass-by-reference languages, where the formal parameter is an alias to the actual parameter. Allowing changing the actual parameter, without having to mess around with a pointer to the actual parameter (or accidentally changing the pointer to point elsewhere).
C++ uses pass by reference, so we could have the following strangeness: ```cpp
int f(int &x, int &y) {
    x = 1;
    y = 2;
    if (x == 2)
        // Even though we haven't explicitely changed x this will print
        std::cout << "!!"; 
    return 0;
}

int t = 3;
f(t, t)
``` Where when changing y, x changes behind our backs - if we don't ensure x & y point to different locations this can lead to problems. 
It can also occur when a parameter to a function is a reference to a global variable used by that function:```kotlin
int some_global;

int g(int &x) {
    x = 1;
    if (some_global == 1)
        std::cout << "!!"; 
        // Even though we haven't explicitely changed some_global this will print
    return 0;
}

g(some_global);
``` 
        - d.) 
First we do a upcast, which is legal, e.g. we cast REF(b) to REF(A). x is now treated as a REF(A).
Then we attempt to set x equal to a REF(A), which the static type system should also allow - as REF(A)'s can clearly be set to other REF(A)'s.
However, at run time when we try and set x to a - the memory layout of x might differ causing a runtime error, or alternatively if the equality is simple the relevant memory locations (which will be the same between the two classes) could be overwritten.
    - [2012 Paper 3 Question 6](../y2012p3q6.md)   
        - a.)
Fortran's abstract machine does not have recursion or stack - variables are allocated statically, and deallocated at the end of the program.
Lisp has a heap and garbage collection, however static locations were used to store variables. With dynamic allocation for lists. As there was still no stack.
In C, Java, Algol-60 and ML static and dynamic allocation are both possible. With static allocation for globals and const items - and dynamic heap & stack allocation. Static varaibles are deallocated at the end of the program. Stack allocated items are deallocated at the end of a block. 
Java, ML and algol-60 use garbage collection for heap allocated objects. While C leaves the programmer to handle the heap.
        - b.) Fortran, Lisp, Algol-60, Pascal, C, ML and Java.  
            - i.)
They all provide static scoping. I.e. can reference the variable named in the current scope. Except for LISP.
            - ii.)   
They all provide static type checking. Except for LISP which is dynamically type checked
            - iii.)
Lisp, ML and Java are all type safe.
Fortran doesn't type check common blocks used between programs, as each program was compiled separately - there was no dynamic type checking so a addition function in one subprogram could be called with strings from different subprogram.
C void pointers are not type safe and are only dynamically type checked. Consider a void program that swaps two pointers, that will not be disallowed statically even though it could be used going from int ⇒ char:```cpp
void* add(void* x, void* y) {
    x = y;
    y = x;
}
add(some_string, some_int);
```
Algol-60:
The type of a procedure parameter to a procedure does not include the types of parameters. So an argument procedure could be called on the wrong types. 
Pascal is almost safe, variant records were not statically checked to see if the tag matched the data. Which could cause errors.
        - c.)
The ML method is better, as the parameter cannot be statically type checked in Algol - leading to errors and programmer confusion.
        - d.) 
Non-variant arrays do not allow writes. So while the compile time is lower as less type casting checks need to be done, and run-time error's are lesser you can't do writes.
Covarient arrays have a higher compile time, but run time errors can occur when you try and do something like: ```java
 Array<String>[10] X;
 Array<Object>[10] Y = X;
 Y[1] = 1; // runtime error
```
    - [2013 Paper 3 Question 6](../y2013p3q6.md)   
        - a.)
            - i.) Algol-60 has no stack allocation (as it has no stack) while Pascal does.
Algol and Pascal both have static type checkers.
        - b.)
Pass by value means the actual parameter is evaluated (the real parameter) and copied to a new location, which the formal parameter then references.
By reference, the formal parameter acts as an alias to the actual parameter.
By value/result - like pass by value. But at the end of the method, the formal parameter is copied back into the actual parameter.
By name - similar to pass by value, but the argument is evaluated lazily. In Algol-60 the parameters are replaced in the function by the actual parameter.
        - c.)  fn f => fn g => fn x => f( g( f x ) )  
( a' ⇒ b') ⇒ (b' ⇒ a') ⇒ a' ⇒ b'
This is inferred by giving every expression a new type variable and then emit constraints α ≈ β whenever two types have to be equal. These constraints can then be solved with Prolog-style unification.
    - [2015 Paper 3 Question 5](../y2015p3q5.md)
        - 5A)
Static type checking came from Fortran, and is still mainstream today.
Stacks allowing for recursive functions with static scoping came from Algol.
Algol-60 introduced arrays with dynamic bounds, where you could change the size of an array.
        - b.)
Index checking for arrays came from Pascal later, ensuring you weren't accessing memory outside of an array.
Dynamic type checking came later.
Object oriented programming, introducing objects, polymorphism etc.
        - c.) 
            - i.)
Java ```java
 public class Variant {
 	private String tag;
 	private Integer int_data;
 	private String string_data;
 	
 	Variant (Integer input_int) {self.tag = "int"; ...}
 	Variant (String input_string) {self.tag = "string"; ...}	
 	
 	public get_data() {
 		Object to_return;
 		if (tag ==...) {...}
 		return to_return;
 	}
 }
```
ML:```java
 type Car = 
 	  Truck of int
 	| Fire_engine of float;;
```ML handles the tagging automatically - e.g. We'll know a type is a Truck.

Pascal:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/o2OGn5c1qAswhIh_7mMJ3bcNsXSn8jFJzY2bxBD-qZxTw4Tk6zwUXYjuUVnVhPUTEgf3pXC7Upn1L00mC6BsJxvbn1Pg1JLXljVisP2fNy46vUnp6QWsIx4fMlgCVXgW.png) 
^^Copied from lecture, would love to go through - don't know what's going on in places.^^ 
        - ii.) 
For the java implementation we return an object, so if they then try and do an operation associated with the wrong type - a runtime type error would occur. Additionally, we aren't checking if the tag and the state match up - which could lead to further runtime errors.

        - d.)
Statically typed languages can be type safe, while dynamically typed languages cannot.
Fortran and C for statically typed languages.
Pascal and JavaScript for dynamically typed languages.
        - e.) 
Type-safe languages will catch all errors at compile time, while type-unsafe languages will not.
Java is type-safe, while Fortran is not.
        - f.) 
...
- **Supervision 2**
    - Malachy's work:
    - Tim Questions 
        1. **What is duck typing, what benefits does it provide and why?**  
Duck typing is a method to specify the equality of two structures when we don't have classes, that is if they have the same states and methods as each other - this means they do not necessarily have to have the same names. We can decide that only certain methods are needed as well, for example a list structure might just need get() and set() but also implement pop() etc.
        2. **What is the motivation behind gradual typing?**
For a large codebase of a language which is not statically typed (e.g. JavaScript) we may want to slowly update it with static typing (e.g. TypeScript) but not convert the whole codebase all at once. This provides the type safety to new parts of the language while not making the old pieces of code useless.
        3. **When do ML structures match a signature and what is a signature constraint?** 
dsads
A signature constraint is a method of hiding the underlying implementation of a structure, you don't see that your stack object is using an int stack under the hood. This can be helpful if you want to disallow/disincentivise certain behaviours on your type, e.g. you don't want people to store negative numbers in your natural number type (which uses integer in the definition).
        4. **What is a scripting language?**  
A scripting language is a language designed around smaller programs to automate human actions. It's designed to make programs quick to write and fast to interact with, this means they are usually not compiled and are instead interpreted as this leads to a faster write-execute loop (for the programmer).
        5. **How does JavaScript execute within a browser and interact with a web page?**  
The DOM model means the entire HTML of the page is stored in the document as a tree model, this can be accessed and altered in JavaScript and the browser updates these changes on the page in real time.
        6. **How does a GADT enable users to represent data structures more precisely than ML can?** 
If we have a type who's constructors have multiple different return types and multiple argument types, we can't know which of those types we have in our hand at any point. So it would be dangerous to write ```java
 Add(e1, e2) = (eval e1) + (eval e2)
``` If eval can also evaluate booleans, this won't type check as + takes two ints. Additionally, what if e1 or e2 are booleans?
GADT's allow you to explicitly indicate the input and output to your type constructors
    - 
    - [2016 Paper 3 Question 5](../y2016p3q5.md)  
    - **Part A**  
        - Monads are a method of adding new operations to state without causing side effects, instead we carry our side effects with us as we compute.  
The fundamental operations are bind (with type a'M -> (a' -> b'M) -> b'M,
and return (with type a' -> a'M)
    - Part B 
        - readint : unit -> int IO
writeint : int -> unit IO
    - Part C 
        - i.) ```java
readint() >>= (y => writeint(y+1)) => (() => y);
```type: unit -> IO int
        - ii.) ```java
 let run2diff x =
 	((x >>= (y => add1(y))) >>= (z => add1(z) - z));
``` Is the question asking for the difference between add1(y) add1(add(y)) or the difference between add1(add1(y)) and x. I assumed the latter.
I don't think my answers right anyway, the add1(z) - z seems wrong. But otherwise how do I carry my version of add1(z) through to use when I have add1(add1(z))?
    - [2014 Paper 3 Question 6](../y2014p3q6.md)  
    - Part B 
        - Thread based parallel programming is not clean, especially in a language with mutable objects. Conceptualizing how threads will interact with a mutable data structure in-between is very hard for programmers and can lead to errors.
In Java, to use threads you must implement runnable in the Thread class.
However, using Streams much cleaner thread-based parallel programming can be handled by the Streams library - without breaking a for loop down to pieces.
Writing code in a functional language does not make the problem embarrassingly parallel (this is a feature of the problem), while functional languages afford you the possibility of breaking your problem into smaller functions (subproblems) which can be computed independently (because there are no side-effects) - if the underlying problem cannot be broken down into large enough pieces that the cost of IPC is not assuaged then you'll get no speedup.
This also doesn't incorporate languages for distributed systems like Erlang.
    - Part D 
        - Z.z = A.z will work and will result in true, the type of A.z is int which is the same as t.  
        - Z.z = B.z will work and result in true, the type of A.z and B.z is int. And the t's are the same, even though the structure is opaque.
        - Z.z = C.z will not work, the structure is opaque and the underlying types are different. C.z doesn't have a type while Z.z does.
        - 
    - [2011 Paper 3 Question 6](../y2011p3q6.md)   
    - Part D 
        - Parameter passing in Scala can be done using call-by-name or call-by-value - calling-by-value is used when the symbol '⇒' is used before the variable type. This means the value is evaluated every time it's needed - this is how whileLoop works, the condition is evaluated each time as is the body of the while loop (comm). 
In qsort, the = > is overloaded to also be used in lambda functions within the body.
Call-by-name can cause confusion, so it's given as an option for more programming style freedom. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hP_vmIDlQLDakWc91a0s4byAgFHwHQgQGrGz8qMVsla7M9BR2VP5sYwTUudUAwWi4X72-MXwHvfpJ5p0dC0Rl8AK34fvaPZ9uXzdvSYVneUAbxtJ_2yHlqOe_ljs742U.png) 
    - [2010 Paper 3 Question 5](../y2010p3q5.md)  
    - Part E 
        - Case classes allows you to use ML pattern matching (a functional language feature) with normal imperative logic on top. We can define classes like the following: ```java
abstract class Expr
case class Number(n : int) extends Expr
case class Sum(e1 : Expr, e2 : Expr) extends Expr

// Which can then be pattern matched like:
def eval(e:Expr): Int = 
	e match{
		case Number(x) => ...
		case Sum(e1, e2) =>  ...
		...
	}
```This means you can choose how to approach the Expression problem, whether using a case matching or a normal inheritance system. This freedom to program using multiple disciplines can be very helpful.
Case classes and case objects implicitly come with implementations of methods toString, equals, and hashCode. 
Case classes implicitly come with nullary accessor methods which retrieve the constructor arguments. 
    - [2008 Paper 6 Question 7](../y2008p6q7.md)   
    - Part C 
        - Explain how function types are encoded in the programming language Scala, exemplifying your answer.  
        - The function type is encoded as functionN[v1,v2,...,vN,v0] where v1-vN are the argument types and v0 is the output type of the function and functionN is the type of a function with N arguments. E.g.:```java
 // Function to add an integer to every value in a list
 // This will have type function3[Int, Array[Int], Int]
 def add_this(to_add : Int, added_to : Array[Int]) : Int {
 	...
 }
``` E.g. an ML function v1*v2*...*vn -> v0 would be equivalent to [v1,v2,...,vn,v0].
    - 
- 
