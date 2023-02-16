- Go
    - **Concepts** 
        - Most of this comes from this video &[](https://youtu.be/YS4e4q9oBaU) 
        - Variable Declaration 
            - Variable declarations happen with the type on the {{**right**}}. Because that's how you read the code. 
            - When are the following three types of variable declaration/initialization useful?```go
a := 25

var b int
b = 100 

var c int = 400
```↓ ↓ 
                - a is useful when the compiler has enough information to discern what the type of a will be (in this case an int) for quick declaration and initialization
                - b is useful when we want to declare a variable of a type, but aren't ready to use it yet. Remember in go variables **have to be used **so if you don't declare it, on your head be it (you'll get a compile time error). 
                - c is useful when we want to declare a variable of a type, but the compiler may not be able to discern it's type. E.G. var c float64 = 400 .
            - You can group declarations (v useful at the package level) by wrapping with a var ```go
var (
	x int = 10
	y string = "abc"
)
``` 
            - What will the result of this code be and why?```go
var int i = 100

func main() {
	
	var int i = 50 
	fmt.Println(i)
}
```→50 will be outputted. Because the block scope takes precedent over the package scope 
            - To convert types in go, we explicitely use those types as functions. E.g.: ```go
var x float3 = 42.5
var y int = int(x)

// y is 42 
``` 
            - What does the following do and why? ```go
var x int = 42
var stringified string = string(42)

fmt.Println( stringified )
```→This will output the UTF-8 encoding of 42, which is *
            - Are redeclaring or shadowing allowed in go? ↓ 
                - Redeclaring is not allowed! You cannot declare a variable twice in the same scope
                - Shadowing is allowed, you may declare the same variable multiple times in various scopes
            - Uppercase variables and functions get exported globally, lower case variables and functions don't.
            - 
        - Primitives
            - Go contains booleans. ` var x bool = true; var y bool = false` 
            - What is stored in an uninitialized value?→The zero value always. 
            - For integers, go has , 16, 32 and 64 bit signed integers  - and 8, 16 and 32 bit unsigned integers.```go
var a int16
var b int32
var c int64 

var d uint8 // Note this is the same as var d byte
var e uint16 
var f uint32  
``` 
            - What is the result of this? ```go
a := 10
b := 3

fmt.Println(a / b)
```→Get this in your head, THE RESULT IS 3. Go will not change the type of a variable without your explicit consent - it will not return a new type without your explicit consent. 
            - Go allows exponential notation - e.g. ```go
n := 13.7e3 // = 13700
``` 
            - What will the result of this be and why? ```go
s := "this is a string"
fmt.Printf("%v, %T", s[2], s[2]) // NOTE THAT WE ARE SELECTING THE 3RD ELEMENT
```→This will result in 105 uint8. Strings are stored as an array of bytes representing UTF8 characters, we select the 3rd byte which holds 105 representing the UTF8 mapping of the character 'i'
            - What are the two problems with this? ```go
var s string = "abc" + "de"
s[2] = "a"
```↓ ↓ 
                - Strings are arrays of bytes, so you can't put a string in a string.
                - Strings are immutable, you cannot change them - you could do this if you wanted to change a string: ```go
a := "abc" + "def"
fmt.Println(a)

x := []byte(a)
x[1] = 97

fmt.Println(x) // [97 97 99 100 101 102]
fmt.Println(string(x))  // aacdef
``` 
            - What are runes?→Runes are type aliases for int32 - they are used for representing UTF32 characters. 
        - Constants
            - Constants start with the const keyword 
            - What will happen here and why? ```go
const x int = sin(1.57)
```→This will result in a compiler error, because the value of the constant **cannot **be decided at compile time. Only at runtime can we know the value of this particular constant.
Constants must be compile time decidable. So ` const x int = 12 * 500` is allowed
            - What happens here and why? ```go
const a = 42
var b float = 27.0 

fmt.Println(a + b)
```→This will output 69. While you would think a would be assumed to be an int by the compiler, so a+b shouldn't work (as they're different types). 
HOWEVER, what actually happens is that any place a crops up, it's replaced by the literal value 42 - e.g. the last line becomes ` 42 + b`. 
(Note that literal values will be set to the type that makes the most sense. In this case 42 is assumed to be a float) 

This means, that constants can mean different types in different places (if you don't set the type) - so we could later say ` c := 1; a+c` and that would evaluate to the integer 43.
            - Enumerated constants are constant blocks set to the special value **iota **```go
const (
	a = iota
	b = iota
	c = iota // note you can skip all iota's past the first
			 // if you like and the compiler will infer them
)

fmt.Println(a,b,c) // 0 1 2 
```
These are constants that are known to have unique increasing values - acting like an Enumerator 

            - Using enumerated constants, why might someone do this ```go
const (
	_ = iota
	electron
	proton
)
```→Consider a test like the following: ```go
var subatomicParticle int
fmt.Printf(subatomicParticle == electron) // false
```
If we didn't have the 0 value of the enumerated constant set to the (read only) underscore - then uninitialized variables might accidentally equal a value. 
            - What does this do? ```go
const (
	_  = iota
	KB = 1 << (iota* 10)
	MB
	GB
)
```→This generates conversion numbers that can be used to go from bytes to KB, MB and GB. This is because the right side of the equals is duplicated across every value in the const - and the iota value is incremented.
        - Arrays and Slices ↓ 
            - How do you initialize an array with or without initial values?→```go
test_array := [5]int{1,2,3,4,5}
// or 
test_array := [..]int{1,2,3,4,5} 
``` 
            - How do you get the length of an array?→` len(test_array)` 
            - How do you create and initialize a 2D array?→```go
test_array := [3][3]int{{1, 2, 3}, {1, 2, 3}, {4, 5, 6}}// or
test_array := [3][3]int{ [3]int{1,2,3}, [3]int{1,2,3}, [3]int{4,5,6} } 
``` 
            - What will happen in this code and why? ```go
a := [3]int{1,2,3}
b := a 
b[1] = 100
fmt.Println(a, b)
```→This will output: [1 2 3] [1 100 3]. This is because arrays are values, they don't point to an underlying structure. These get copied over when we reassign arrays. We could change this by doing ` b := &a` 
            - Give two ways to initialize a slice→```go
a := []int{1,2,3}

a := make([]int, 3, 100) // Create a slice of length 3 and capacity 100
// or
a := make([]int, 3) // Create a slice of length 3 and capacity 3 
``` 
            - How do I append 2,3,4,5 to the following ` a := []int`?→```go
a = append(a, 2,3,4,5) // Results in [2,3,4]

// Not fixed in stone, but will likely have a capacity of 4
``` 
            - How do I get all the values from a slice except for the 3rd, and convert those values into a slice of it's own?→```go
a := []int {1,2,3,4,5}

result := append(a[:2], a[3:]...)
 
``` 
            - What does the ... operator do after a slice or an array? ↓ 
                - After the slice it behaves like the * in python and decomposes it into its constituent elements, e.g.: ```go
a = append(a, []int{1,2,3}...)
// or
x := []int{1,2,3}
a = append(a, x...)

// Both of these are useful for concatenating slices together  
``` 
                - After an array, it doesn't work!
        - Maps↓ ↓ 
            - Describe how you would form a map from from odd digits to the next even digit→```go
result := map[int]int{
	1: 2,
	3: 4,
	5: 6,
	7: 8,
}
``` 
            - What's wrong with this code? ```go
x := map[[]int]string
```→You cannot map from slices - you can however map from arrays, so ` x := map[[3]int]string` would work.
            - How can you create a map without populating it?→```go
myMap := make(map[string]int)
``` 
            - Adding items and getting items out of maps has the same syntax as Python.
            - How do you remove items from a map?→```go
myMap := map[string]int {
	"a" : 1,
	"b" : 2
}
delete(myMap, "a")
// Now myMap only has {"b" : 2} 
``` 
            - What does this do and why is it necessary? ```go
a, b := myMap["a"] 
```→If myMap does not contain the key "a", then 0 will be stored in a. However, false will be stored in b. b acts as an 'ok' - checking that the key was present. 
        - Structs ↓ 
            - Describe how I would create a Doctor Who struct, containing a name, the number of the doctor and a list of companion names→```go
type DoctorWho struct {
	name string
	number int
	companions []string
}
``` 
            - Describe how I would **initialize **a Doctor Who struct, containing a name, the number of the doctor and a list of companion names. Then how would I fetch out a field?→```go
doctor := DoctorWho{
				name: "...",
				number: 5000,
				companions: []string { "a", "b" }
}

// NOTE: we must tell go the type of the companions that we're creating and passing 

doctor.name
doctor.number
doctor.companions 
``` 
            - What is an anonymous struct and how do you create one?→An anonymous struct is an unnamed struct that will be short lived ```go
s := struct{name string}{name : "Tim"}
// Note that the first brackets describe what's in the struct and the second brackets initialize the struct 
``` 
            - What happens if we copy a struct and then alter it and why?→The original struct will not be changed, this is because structs are values (first-class-citizens) so we can alter them in our hand.
            - What does Go do instead of inheritance, give an example with a bird that is an animal→Go has embedding, we embed one struct within another and the initial struct now has all the properties of the embedded one. ```go
type Animal struct {
	Name string
}


type Bird struct {
	Animal // This is where we embed
	canFly bool
}

// As a result we can do the following
b := Bird{name: "Penguin", canFly: false}
fmt.Println(b.name) // results in "Penguin"

``` 
            - Explain the difference between inheritance and embedding ↓ 
                - Embedding is a form of syntactic sugar that maps the attributes over to the enclosing struct
                - A Bird type (with an Animal embedded inside) **CANNOT **be used for a function that takes type Animal! 
                - Embedding is a  __has a __ relationship, e.g. a bird has animal type characteristics. It is **not **an  __is a __ relationship. 
            - What are tags in structs and when are they used?→Tags indicate requirements for fields of a struct for example: ```go
type Car struct {
	numWheels int `required min: 3 max: 4`
	colour string `required`
	make string
}
// Here we've indicated that numWheels and colour are required - and the numWheels can only be 3 or 4
``` 
To access tags we need to use the reflect module.
They are useful when writing validation code that checks features of certain structs - **go does not handle this on it's own!**
        - If and switch ↓ 
            - How can I get a value out of a map, check if it's ok and use it in one if block?→Go provides a handy syntax for this: ```go
if val, ok := someMap[5]; ok {
	fmt.Println(val)
}
// We first get the value out - then check if it's ok, then we can use that value in the if block to our heart's content 
``` 
            - Does Go use short circuiting?→Yes - it will evaluate or's (||) until it finds a true value - and and's (&&) until it finds a false one. 
            - Note that Go contains **else if**! 
            - Give a switch statement that prints odd if the digit passed is odd, even if it's even and prints "something else" otherwise→```go
switch number {
	case 1,3,5,7,9: {
		fmt.Println("odd")
	}
	case 0,2,4,6,8: {
		fmt.Println("even")
	}
	default: {
		fmt.Println("Something else")
	}
}
// Note that test cases CANNOT overlap 
``` 
            - What are tagless switch statements and what are they useful for?→```go
i := 10
switch {
	case i < 5: {
		...
	}
	case i >7: {
		...
	}
	default: {...}
} 
// Note that test cases CAN overlap 
``` 
            - How do you get the type of a variable in go?→```go
i.(type)
``` 
        - Looping
            - 
            - How can you create and increment to variables at once in a for loop? ```go
for i, j := 0,0; i<5; i,j=i+1, j+1 {
	fmt.Println(i,j)
}

``` 
            - How do you create the most basic for loop?→/```go
for i := 0; i < 5; i++ {...}
// (create i ); (set bounds for i); (increment i);

//Alternatively, you can do:
i := 2
for ; i<5; i++ {...} 
``` 
            - You can create infinite loops if we don't include the incrementor ```go
for i:=0; i<5; {...}
// or 
i := 0;
for i < 5 {
	i++
} 
``` 
            - You can use breaks and continues in for loops like python.
            - What is the equivalent to enumerate in Go?→```go
s := []int{1,2,3};
// Can also be used for maps and strings
for k, v := range s {
	fmt.Println(k,v)
} 
``` 
        - Defer, Panic and Recover
            - What does defer do?→```go
func main() {
	fmt.PrintLn("Start")
	defer fmt.PrintLn("Middle")
	fmt.Println("End")
}
// -> Start End Middle
Defer waits to execute the code until the enclosing function exits. 
``` 
            - What will happen here?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4RHrZ3rZ2NWcTI8zz5sDluJ-dnwMtS3RgTbZ7t2J5m4xQYKO74cMtZA4bqJyN4UZwj1tIUXUvPE8BbNXZvwIdYGWq6ID3ynVgP2AuY-EgANMhCLFa9RwYzuQ23pEg6c7.png)→This will execute in last in first out - meaning the output will be "end middle start". Useful for closing resources after a function ends so we don't forget. i.e.:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BPiUQ-itv9QYpW9llNump4OVygJttOfjUTkhxlKeWBC4PszKRk1s45r9xoTd6Oqu82PiGsDafhBmPLu41gHOjYof8gltXsjbIw5X3zCSZmApGdwsbsusns0yiPZHjgVs.png)
            - What will this do and why?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9m8vsHj1pYPzevOdMy4cBV1t2NgaDAMLVS8qogqQjZA9p4cang2WY77qrru0ezW24rCRFylAU-VmnXdIiGl78EEF4cUcnSFNM7-UGD7_WKayEJW06WtS894hWiWBrJWL.png)→This will output "start" - we eagerly evaluate a and store it.
            - What does defer take?→A function **call**. 
            - Panic
            - Exceptions are replaced by Panic in go. Certain things throw exceptions (start panicking) and certain things don't - e.g. not being able to open a resource is not unusual, and so it only returns an error and doesn't panic.
            - How do you throw an exception in go?→panic("The message") 
            - What would happen here? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ulyQTkxNT7GadkzugcvnEZBWmrePghe8fZrPIJHcq20do07ygUiJYhIpVcGxVM_UCwf3kwomQJM56PuWkbj7YDHa7PX6ezU8nDISGoxaVQUMk-txWdLh-YvE79Kat9mL.png)→First start will be printed, then the defer get's queued up then finally we panic. The panic causes us to exit the function so the defer get's executed. Only after the defer is executed does the panic output come:
"start" "this was deferred" "something bad happened"
            - What does recover do?→It checks if we're currently panicking, if we're not then it returns the nil value otherwise it returns the error. It's **only useful in defer functions**. E.g.:
```go
defer func() {
	if err := recover(); err != nil {
		fmt.Println("Error:", err)
	}
}()
``` 
        - Pointers
            - How do I create a pointer to a given var a int = 42? How do I then get the value out of our new pointer?→```go
var b *int = &a
value := *b 
``` 
            - What happens here ```go
a := 5
var b *int = &a
*b = 10

// What are a and b storing
```→They both now store 10. 
            - Go {{does not allow}} pointer arithmetic!
            - What is the uninitialized initial value for a pointer?→An uninitialized pointer gives nil! We need to check for these if we're using pointers. 
            - Describe what's happening here line by line
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6OgVYzp91VLP2WPY_pOg9-Zuc3iKBH9W-PnAybeQjtsDkYM6JkI32bPxE16XWacw2CXwR0r-q1lEhZNdfo4FCLpK1c7M6sNCZ0FlOLhkqj3Or3TCmy3ZmElHd2pwYJD2.png)↓ ↓ 
                1. First we declare a pointer of type myStruct
                2. Then we initialize a myStruct using new, new creates a zeroed out version of myStruct.
                3. We then fetch out the foo field, normally you would assume we'd have to do (*ms).foo - but the compiler gives some support
                4. Finally we print out ms.foo
            - What happens here and why
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Bxjpg5wU0XhO39XKPhGF7B1g6mdfB_lJEY-666f-cHMDPPgW7P_WDDoF_fqkdw0EZMPOzwRQNM9h2k6EK-WDMlaW-LjcnUpTS0xqsgZRZDZywJU5cHOCQGHP3DLI_VUU.png)→This will print out 42 42. This is because a slice is a pointer to the first value of an underlaying array. So when we copy the slice, both the original and the copy point to the underlying fact of the matter.
**Note: Maps do the same thing **maps also point to an underlying datastructure which will do the same as avobe. 
        - Functions
            - Will this work? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NCq25eBSkx-sh0Bt74Bu6dxd2cdztTOMZfKInnfjRbG9x1l7ZuWUPOrslvufjji_SlcO2iNKWI38NqTGpMQS_RjFyN93YeFL6AyIVfoiqwZvFx0DG1JOgQ_oYfwHx95i.png)→Yes, in a comma delaminated list the last type is taken for all items in the list. 
            - What does this do
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HU5TiuuzEYI_H887tnyu3IkRpZSoDuxz7LW6zDNpPjhFD1TGFsTA78bB9Qwglf8Y8qKq_saCt_wUfuhFxkfBV26UhRguwsGC7NYWr8UbhlBV9IDLhynQsEl_D2x2XtDu.png)→values ...int takes any number of input and puts them into a slice. You can only have one variadic parameter and it needs to be the last one.
            - Can you return the address of a local variable from a function?→Yes! The variable is first created in the execution stack but is moved to the heap when it's returned. 
            - What is the syntactic sugar doing here in the return type? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PuMTsBxH6O3ykRIu68H8BT56g0WSsu5xd-Ukiv_CP001uClyjIPKuZpwXX9bulA1S5Kgh7LATOu_lbRRtkF4MUUTKz7WSSDGRETLn4ZjpUWNST5FW7tvZz8R3JUIgc4n.png)→This states we're going to return a variable result of type int. This creates the variable for us, then when we return we don't have to put the name of the variable we're returning.
            - What is the idiomatic way to deal with an error that occurs here when dividing by zero:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_zOmXWJx8ZeGjDLpgyn64h7LKH8xbBLKMxAs3xJflk8lyZ0PUa3_Fwyzk7Cvwzk4qkhH6Nbu4W0LuBjzuPK-5mgciYY9bFmVr97YfLC9JppRPWM_YwRjT5AFr1OO7V2Q.png)→Give a second return value storing an error, make it nil if no error occurred. Multiple valued returns works a bit like python.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VjbSxrgMePb2u3tha9uZ5Cmnkkirqt1Ovgp4r3DQreQA6-HmllQBINOctrKZpTPGQISBJr4bRUKz33trgIX1JQNWtnOql0PBabMRhJINXtk_ZiKNwoDvKV_zaaMOv4Pd.png) 
            - Why would you pass i like this, why not let the function use the value in the scope naturally? ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P5PH16B5CgQ16ReO4Dlrsn0CD8fTUkDnZc64nqyWuq2L6NMEYN3oOFNo_Kayhf4aM--wJ6ubL1Lwhw4cPFvkZDZiXQ5oTOafdovsd99QAYR2tRfyUvokdD5IW2qnAyUb.png)→For asynchronous code, not passing it can get messy as it runs at different times to the incrementor. Passing it ensures correctness.
            - How do you declare functions as variables? How do you define them? ↓ 
                - You declare them with the input and return types to your function. E.g.:```go
var divide func(float64, float64) (float64)
// Note they are defined without argument names 
``` 
                - You can then define them with an anonymous function: ```go
divide = func(x float64, y float64) {
	return x / y
} 
``` 
            - What is going on here?  What is this useful for?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TgKi9KVfqwyl0mQsXJL8bRQIjiNKfMQqeGjC54j4sAd4imgw8bssWk83KdAxJGt4gv1FN0dtosGG8HMW9RTQrt8VZ7TAcPwBkqoenNMRQg5LIEQW04DQ4-fl_NNT8W50.png)↓ ↓ 
                - First we create a greeter struct which holds two strings. Then we define a **method **this is given a **context **e.g. the struct it will work on. It's name is greet and it prints out the given greeters greeting and name. 
This method is now bound to the struct 
                - This is useful as it allows us to easily apply methods to structures - e.g.:
```go
g := greeter {
		greeting: "Hello",
		name: "dsadas"
}
g.greet() // Outputs Hello dsadas 
```
Whenever we call g.greet - the greet function is passed a **copy of the struct **as g which it can then use. 
            - How can we edit the type passed as the context to a method→![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vUcIQowavvDwo6wZwK3TDcU4bD3nI9yTF8foCX-mwMItgW3cO3dKov7d9m-YtdK7qGMv7r9rpYRUjGPhGfXzNEA9qY-v5n5a9Bt4XW0IuZjwlG9f5c-AeiWAynx03WX-.png)
Pass a pointer instead!
You still only have to call g.greet() on your structure it works fine.
        - Interfaces and Type Conversion
            - What is going on here? Is this polymorphic behaviour?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S0UyOiZm5_1k13ak_CVNwTQ5TEUSYE9xv3Iw4D2V69F9JfD0Nv5il5sWMRzfcpbUNCAMh3ZUWe8PrMhGpCMcj5urd8xGJBQdDsVWo-p9lPgkzeMn5D7t5msekUjMQbeQ.png)↓ ↓ 
                - First we define an interface, this is a type not a struct - so it encodes behaviour not state! This interface, Writer, has a single function that takes an array of bytes and returns an int and an error. 
                - Then we define a ConsoleWriter struct and give it a method called Write which prints to the console.
                - Finally, in main(), we define our **Writer **to be of type **ConsoleWriter **- Writer doesn't know what it's writing **to **you have to tell it that with your implementation. So this is Polymorphic behaviour as more Writers are added. 
                - Write can be used because it has the same name and types as in the interface.
            - How do you compose interfaces together?→```go
type Writer interface {
	Write([]byte) (int, error)
}
type Closer interface {
	Close() error
}

type WriterCloser interface {
	Writer
	Closer
} 

// So now writercloser must implement all the methods in Writer and Closer. 
``` 
            - How do we do type conversions for types that implement interfaces? How do we make this safe? ↓ 
                - We can type convert using the following syntax  ```go
x := Reader()
x.read(10)
y := x.(*NewReader)
// Now y holds the NewReader type (assuming NewReader implements all of the methods of Reader) 
``` 
                - We can type convert safely using: ```go
y, ok := x.(*NewReader)
// Now if this fails, we won't panic
// Instead we check if ok is true - otherwise it will be the 0 initialized value of NewReader

if ok {...}
else {...}

``` 
            - What is the empty interface and what is it useful for? ↓ 
                - The empty interface is just that, some interface with no methods attached ```go
type SomeInterface interface {}
``` 
                - This is useful because any type can be cast to an empty interface as it has no methods to implement - even an integer can be cast to it. This is useful if we don't know the type we're passed, and we want to perform some logic to decide what it is later and while that happens we put it there.
You then go through, do the casts and find which one works to decide what type of object you're holding.
            - How do you make a type switch?→```go
switch x.(type) {
	case int:
		...
	case string:
		...
	default:
		...
}
``` 
            - What might be the difference between these two: ```go
var wc WriterCloser = myWriterCloser{}
// VS
var wc WriterClose = &myWriterCloser{}
``` ↓ 
                - When you implement an interface, if you pass the value of the interface - only the methods that operate on the **value of the type **are revealed to the receiving interface. I.e. the methods that can't alter the state of the method.

                - However, when you pass a pointer to an interface type - **all methods are included**, those that operate on the value of the type **and **those that operate on a pointer to the type. 
            - Best Practices:
                - Build many small interfaces and compose them if you need a larger one.
                - Single method interfaces are very powerful - e.g. io.Writer, io.Reader, interface{}
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TyM8lo3JPTGZsadBnSVj8T6zyaZ4VvI_KP4__QNh_drkfL0wYi4haDuE-SgnWKByEkZYNmZn7HlJ_G8J73KMwgwd_-05-5170Jc1kacIEA0kLeleqmg4Zr0X_WhWqjpf.png) 
                - Design functions and methods to receive interfaces whenever possible.
        - Goroutines
            - When you call "go someFunc()" this tells go to spin off a **green thread **and run the function on there. In normal languages this would create an OS thread with an individual function call stack.

            - Instead of creating these large heavy overhead threads, go creates an abstraction of a thread which is then managed by a scheduler - the scheduler maps these goroutines to the heavy OS threads and we don't need to create a new one each time.
            - What bad thing can happen here and why? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PhXWQ_MS3KoBD8XkjM3hfXEvn4kltSgycPTIVG31hC4WRad--8MTOKMFPIf_OWafyfJKcjhmHMcTpHqMcVZgGaBrfOtj7W_NB0ICifHqy57uFIOd4PUZnWaI7eKdKqda.png)→This will usually result in printing out "Goodbye" - this is because the Go scheduler keeps running main() until it hits the Sleep, at which point the value of msg will change. This is a race condition.
We can fix this by passing msg into the unnamed function.
            - What are wait groups, how do you implement them?↓ ↓ 
                - Wait groups are just a method for waiting on a group of threads to finish before continuing. E.g. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pdvFoa6FNYg41jDLCLKn80tn-hqHPZTrXfANesU1hG6eW5b21iCrtVzyuxnJDX3UAexneXzCoL9wFUFblPVBr-C1K2Vh6l32bY3rIEmX9ANaVIX3GFuDAalXK40lKZzA.png)
            - What are Mutexes? What is a RWMutex? ↓ 
                - A mutex is a way of protecting parts of code, so only one routine can perform certain actions at once.
```go
var mutex = sync.Mutex{}

mutex.Lock()
...
mutex.Unlock() 
```
                - A read write lock means any number of threads can read a value, but only if no ones writing to it. If someone is writing to it then they have to wait for all the readers to clear out.
            - Best Practices 
                - Don't create goroutines in libraries - let consumers control that concurrency (unless you're using channels)
                - Check for race conditions at compile time. This can be done using a -race flag. E.g. ` go run -race your_file.go.`  This will try and find race conditions.
        - Channels
            - How do you make channels?→```go
ch := make(chan int)
// Change int to whatever type you plan to send 
``` 
            - How do you send data into a channel or get it out?→```go
ch := make(chan int)
// Now slap data in:
ch <- 20
// Now get it out:
i := <- ch 
``` 
**NOTE: By default only one thing can be in the channel at once**. Adding to a channel with an item in it will block! 
            - How do you ensure a go routine only writes to or receives from a channel?→```go
ch := make(chan int)

go func(ch <-chan int) {
	// This function can only take values out of the channel
}(ch)

go func(ch chan<- int) {
	// This function can only put values into the channel
}(ch) 
``` 
            - How do you add a buffer to a channel?→```go
ch := make(chan int, 50)
// The channel now has a buffer 50 wwide 
``` 
This is useful if input data is sent in bursts.
            - What will go wrong if we do the following and how do we fix it: ```go
ch := make(chan int)
go func() {
	for i := range ch {
		fmt.Println(i)
	}
}

go func() {
	ch <- 10
	ch <- 20
} 
``` ↓ 
                - The range (yes that is the correct syntax for channels) continually checks for values in a channel **forever**. So when we've put 10 and 20 in it will continue to wait and will deadlock. 
                - To solve this, we close our channel once we're finished writing to it:
```go
go func() {
	ch <- 10
	ch <- 20
	close(ch)
}
// You cannot send on a closed channel! 
``` 
            - How do you check if a range is open before taking from it?→```go
// Standard go, ok gets true if open and something else if it's closed
if val, ok := <-ch; ok {
	...
}
``` 
            - What would this channel be useful for? ```go
ch := make(chan struct{})
```→This channel detects messages - i.e. when an empty struct (which takes no memory) is sent into the channel it detects it. You can then use this as a message passing system to receive shutdown messages for a goroutine or other such messages. 
            - What's happening here?
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/egX60Gn72QMzbXf4c0A6mYBUED7P-IqJwdbwypvlxM-CH5NwhAxTloMepbE0PwfCmu6XmBQpRJwUU2ZSHARCEy2aTZML6kgw50FamcPBhSEUCKbxWxsmjKcOjrqKKCG1.png)→The select statement listens for inputs to any of it's channels. In this case when the log channel get's an entry it prints that out - and when the done channel gets some input it breaks and closes the logger.
    - **Videos** 
        - ** The Go Programming Language and Environment** 
            - &[](https://www.youtube.com/watch?v=YXV7sa4oM4I) 
            - Built to allow for concurrency, scaling technology, scaling dependencies (telling if a dependency is necessary).
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QvTkYVo6A0U2h2XiiOyoGkWjBOcJMnRNVdz60WjbrVBLIpWl-QEyBsgfGvPkUKtAa4S18dvvg5caRhjslr56pgGstledAkOnYDfvez14erYY2kBstcjksWcS5t5nrdoG.png) 
            - Fundamental idea of interfaces - fprintf should work on an IOStream, a network card etc - it just needs to know if it can write to it.
            - Go has no parametric polymorphism
            - Go Routines (green threads)
                - Never have go routines block other go routines on one thread - if one requests a blocking operation, move that routine or others off that thread.
                - Rate limited:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kZ8wfIkkFs-mxu6T-G0suAc4WVfVrKQjmC0hxauIgDA_YAfaGnum9kV45mmQOOJ3OdIWRu-2Su04zEqn4-uQ67UGUP5gjF9NkV1xG2pyPW5_2M8Rhy_5cjdH4JpRjv-d.png) 
            - Safety
                - Go is garbage collected. 
                - Runtime race detection exists.
                - No pointer arithmetic
            - 
    - **Articles/Papers** 
        - The Go Programming Language and Environment   
        - 
        - 
    - 
- Proposal
    - TODO:
        - 
        - Introduction
            - Describe what makes these aims challenging  
            - Describe what makes the project useful
            - NOTE: Bus data does **not **come through MQTT - CDBB in the building does 
            - Explain what acronyms mean
            - Mention **Smart **and **Timely** 
        - Success criterion
            - Add extensions
            - Add MQTT-SN to the extensions
        - Deliverables
            - Deliverables vs Measurables - Add a deliverables section (current success criteria look like deliverables) measure success against currently deployed MQTT, mention Go profiling and Python profiling. PAHO MQTT in python
        - Evaluation metrics
            - Test on varying use cases, some messages end up as JSON
            - MQTT Box?
            - Testing power is v complicated, can't just look at DRAM - all this deep sleep junk going on
            - Diagram of lab setup
        - Timetable and milestones
            - Milestones are a combination of evaluations and deliverables
        - Resource declaration
            - Explain you will prototype components on whatever dev setup you have (big that up, mention github, usb backups) but run the testing on the 'lab' platform.  
    - 
    -   
    - Completed Sections:
        - Introduction
        - Starting Point
        - Success criterion
        - Deliverables
        - Evaluation metrics 
        - Timetable and milestones 
        - Resource declaration 
    - 
    - 
    - 
    - 
    - Check out Kafka
    - Build a Mosquitto Pub & Sub thing
- Research
    - Mosquitto
        - Got mosquitto running with
            - ```
mosquitto_sub -t 'test/topic' -v
```  
            - ```python
mosquitto_pub -t 'test/topic' -m 'hello world' 
``` 
    - Kafka
        - Kafka also does publish subscribe by splitting messages into topics, but that's the only similarity with MQTT. It's usually used for event streaming,  big data proliferation and storage of huge amounts of messages.
        - This differs from MQTT which is for smaller data from many smaller devices with spotty connections in real time.
        - You can connect Kafka to MQTT at the edges for smaller data proliferation. Can be done through MQTT bridges, bridge from MQTT broker to Kafka broker which then proliferates to clients. Alternatively, connect to Kafka via MQTT proxy **without **an MQTT broker. 
    - MQTT Docs 
        - Client does the following:
            - Opens the Network Connection to the Server publishes Application Messages that other Clients might be interested in. 
            - Subscribes to request Application Messages that it is interested in receiving. 
            - Unsubscribes to remove a request for Application Messages. 
            - Closes the Network Connection to the Server.  
        - Server does the following:
            - Accepts Network Connections from Clients. 
            - Accepts Application Messages published by Clients.  
            - Processes Subscribe and Unsubscribe requests from Clients. 
            - Forwards Application Messages that match Client Subscriptions. 
            - Closes the Network Connection from the Client.   
        - A Subscription ‒ Comprises a topic filter and a maximum QoS. A subscription is per session (a message stream between  __a __ client and  __a __ broker), obviously you can have many subscriptions in a session. 
        - MQTT Control Packets - there are 15 bloody different types.
    - QUIC
        - Long and short headers
            - Long header:
            - Long Header Packet {
  Header Form (1) = 1,
  Version-Specific Bits (7),
  Version (32),
  Destination Connection ID Length (8),
  Destination Connection ID (0..2040),
  Source Connection ID Length (8),
  Source Connection ID (0..2040),
  Version-Specific Data (..),
}
            - Short header
            - Short Header Packet {
  Header Form (1) = 0,
  Version-Specific Bits (7),
  Destination Connection ID (..),
  Version-Specific Data (..),
}
            - Need to decide destination connection ID somehow 
            - Address without qualification IP version, IP address, and UDP port number
        - Streams
            - Streams can be bi or uni-directional. An arbitrary number can run concurrently.
They are encoded by a 62 bit stream ID. The two **LEAST SIGNIFICANT **bits represent client/server initiated and uni/bi directional.
            - A stream ID must **not **be reused. 
            - **Server initiated streams must be an odd number - clients must be even numbered.** We will only handle bidirectional. Must be ordered.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WV4A1Ad_5RJpdi2C2O4SLlmI2Wz36Gz9-_b1AO1pKiP4-TuKCqeQj0B7oW43_m-ZRL4AotKMeXjaxzpGOvVqrEUO3cQVgDk-tn2uNditFA_EWvNt7Z7UrbtKx1aKNDoa.png) 
            - States for part of stream that [**sends **](https://remnote-user-data.s3.amazonaws.com/8OAJFD0OpGdhKq0EYHe3glZ7XH_v3r3aeeHtoN6Sc6EI7YWNh3bNgIKEaBN_vjybihsKERvZHB-JAlrSPfBqHhEU24h0VKk3mZk_g6kuZ8tIABKyJhRCk7fZxyER_pHK.png)data. We starting a ready state once the receiving part is created.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8OAJFD0OpGdhKq0EYHe3glZ7XH_v3r3aeeHtoN6Sc6EI7YWNh3bNgIKEaBN_vjybihsKERvZHB-JAlrSPfBqHhEU24h0VKk3mZk_g6kuZ8tIABKyJhRCk7fZxyER_pHK.png) 
            - States for receiving part of data:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sZDJUJfrSbwMjIGQ52E3y_MAw7Vf61phze9KCFJ5XKLM9oUv0rSiFVZvz9VD31wMlqDjJS9Vv9vuiOuD5-5y7RIMbqB06KLAWNoS2EeKAbXK9PUV7f2BTobZ-qWjVeAs.png)
        - Data flow control
            - Receiver advertises the limit of total bytes it is prepared to receive on a given stream or for the entire connection. These are set in the initial handshake or through specific Frames.
        - Connections
            - Shared state between client & server. Establish shared secret - negotiate the application protocol.
            - Connection established by client sending initial packet containing a connection identifier - also contains security handshake. Server sends back its own initial packet - has the server CID and the second handshake message. Subsequent handshake packets are protected with the key from the initial messages.
        - 
    - 
    - Ssh into tfc-app9.cl.cam.ac.uk -l mro31 ‒ NOTE I CHANGED THE PASSWD
    - Mention the ssh code in the report. 
    - Safety port 22 open to the internet but 31122 only open to the server itself.
    - ssh -p 31122 pi@localhost..
    - pw is mqttpi1 or 2 ...
    - intel box address: ssh -p 31022 mro31@localhost - password is same as you know what
    - 
    - touch a file when it runs the stuff! Which the crontab
    - 
    - 
    - In every pi:
        - WRONG - look in toRun in repo
        - Edit crontab so that every 15 minutes we try and rectreate our ssh connection
        - Edit autostart in ~/.config/lxsession/LXDE-pi/autostart and create the following file called openConnection.desktop:

        - [Desktop Entry]
Type=Application
Name=bootCommands
Exec=/home/pi/Desktop/bootCommands.sh 
    - 
    - remember to put the hostnames on the pi
    - Need to give the pi's fixed IP's
    - Normal crontab start the ssh connection every 15 mins
    - Sudo crontab restart 
    - Pi's could be establishing a rssh connection to the server itself - using the IP as the host address
    - ping 192.168.1.X 20-29
    - 
    - 192.168.1.154
    - 192.168.1.154
    - 
    - Installing go on the pi's
        - mkdir ~/src && cd ~/src
wget https://dl.google.com/go/go1.19.5.linux-armv6l.tar.gz
sudo tar -C /usr/local -xzf go1.19.5.linux-armv6l.tar.gz
rm go1.19.5.linux-armv6l.tar.gz 
        - 
        - Add these to ~/.profile:
```
PATH=$PATH:/usr/local/go/bin
GOPATH=$HOME/go
```
        - 
        - Then run ```
source ~/.profile
``` 
- 
- 
- 
