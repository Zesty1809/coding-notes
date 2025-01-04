Working dates: 3/01 4/01
# Compilers
- What is a compiler?
	- Computers understand only one language and that language consists of sets of instructions made of ones and zeros. The computer language is known as machine language.
	- Because a computer can only understand machine language and humans wish to write in high level languages high level languages have to be re-written (translated) into machine language at some point. This is done by special programs called compilers, interpreters, or assemblers.
- C++ is designed to be a compiled language, meaning that it is generally translated into machine language that can be understood by the system, making the generated program highly efficient. 

# Console programs
- Console programs are programs that use text to communicate with the user and the environment, such as printing text to the screen or reading input from the keyboard.

# Structure of a program
- Typically the first program beginners write is a program called "Hello World", which simply prints "Hello World" to your computer screen.

```cpp
// my first program in C++
#include <iostream>

int main()
{
	std::cout << "Hello World!";
}
```
The output is:

```terminal
Hello World!
```

Let's examine this program line by line:
- Line 1: // my first program in C++
	- Two slash signs indicate that the rest of the line is a comment inserted by the programmer but which has no effect on the behavior of the program. Programmers use them to include short explanations or observations concerning the code or program.
- Line 2: \#include \<iostream\>
	- Lines beginning with a hash sign (#) are directives read and interpreted by what is known as the `preprocessor`. They are special lines interpreted before the compilation of the program itself begins. In this case, the directive \#include \<iostream\>, instructs the preprocessor to include a section of standard C++ code, known as `header iostream`, that allows to perform standard input and output operations, such as writing the output of this program (Hello World) to the screen.
- Line 3: A blank line
	- Blank lines have no effect on a program. They simply improve readability of the code.
- Line 4: int main() 
	- This line initiates the declaration of a function. Essentially, a function is a group of code statements which are given a name: in this case, this gives the name "main" to the group of code statements that follow. 
	- The function named `main` is a special function in all C++ programs; it is the function called when the program is run. The execution of all C++ programs begins with the `main` function, regardless of where the function is actually located within the code.
- Line 5 and 7: { and }
	- The open brace ({) at line 5 indicates the beginning of `main's` function definition, and the closing brace (}) at line 7, indicates its end., Everything between these braces is the function's body that defines what happens when `main` is called. All functions use braces to indicate the beginning and end of their definitions.
- Line 6: std::cout << "Hello World!";
	- This line is a C++ statement. A statement is an expression that can actually produce some effect. It is the meat of a program, specifying its actual behavior. Statements are executed in the same order that they appear within a function's body.
	- This statement has three parts: First, std::cout, which identifies the **st**andard **c**haracter **out**put device (usually, this is the computer screen). Second, the insertion operator (<<), indicates that what follows is inserted into `std::cout`. Finally, a sentence within quotes ("Hello world!"), is the content inserted into the standard output.
	- Notice that the statement ends with a semicolon (;). This character marks the end of the statement, just as the period ends a sentence in English. All C++ statements must end with a semicolon character. One of the most common syntax errors in C++ is forgetting to end a statement with a semicolon.

The program has been structured in different lines and properly indented, in order to make it easier to understand for the humans reading it. But C__ does not have strict rules on indentation or on how to split instructions in different lines. For example, instead of
```cpp
int main()
{
	std::cout << "Hello World!";
}
```
We could have written:
```cpp
int main() { std::cout << "Hello World!"; }
```
- In C++, the separation between statements is specified with an ending semicolon (;), with the separation into lines not mattering at all for this purpose. The division of code into different lines serves only to make it more legible and schematic for the humans that may read it, but has no effect on the actual behavior of the program.

Now let's add additional statement to the program:
```cpp
// my second program
#include <iostream>

int main()
{
	std::cout << "Hello World! ";
	std::cout << "I'm a C++ programmer";
}
```
```terminal
Hello World! I'm a C++ programmer
```

# Comments
- Comments do not affect the operation of the program; however they provide an important document directly within the source code what the program does and how it operates.
- C++ supports two ways of commenting code:
```cpp
// line comment
/* block comment */
```
- The first  of them is known as **line comment**, discards everything from where the pair of slash signs (`//`) are found up to the end of that same line. The second one, known as **block comment**, discards everything between the /* characters and the first appearance of the */ characters, with the possibility of including multiple lines.

Let's add comments to our second program:
```cpp
/* my second program in C++
   with comments */
   
#include <iostream>

int main()
	{
	std::cout << "Hello World! ";        // prints Hello World!
	std::cout << "I'm a C++ programmer"; // prints I'm a C++ programmer
}
```

# Using namespace std
- If you have seen C++ code before, you may have seen `cout` being used instead of `std::cout`. Both name the same object: the first one uses its **unqualified name**(*cout*), while the second qualifies it directly within the **namespace** *std*(as std::cout).
- *cout* is part of the standard library, and all the elements in the standard C++ library are declared within what is called a **namespace**: the namespace *std*.
- In order to refer to the elements in the *std* namespace a program shall either qualify each and every use of elements of the library (as we have done by prefixing *cout* with *std::*), or introduce visibility of its components. The most typical way to introduce visibility of these components is by means of **using declarations**:
```cpp
using namespace std;
```
- The above declaration allows all elements in the *std* namespace to be accessed in an **unqualified** manner (without the *std::* prefix).

With this in mind, the last example can be rewritten to make unqualified uses of *cout* as:
```cpp
// my second program in C++
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello World! ";
	cout << "I'm a C++ programmer";
}
```
- Both ways of accessing the elements of the *std* namespace (explicit qualification and **using** declarations) are valid in C++ and produce the exact same behavior. For simplicity, and to improve readability, we will use the latter approach of with **using** declarations, although note that **explicit qualification** is the only way to guarantee that name collisions never happen.

# Variables and types
- *Variable* can be defined as a portion of memory to store a value.
- Each variable needs a name that identifies it and distinguishes it from the others.

# Identifiers
- A valid *identifier* is a sequence of one or more letters, digits, or underscore characters (_). Spaces, punctuation marks and symbols cannot be part of an identifier. In addition, identifiers shall always begin with a letter. They can also begin with an underline character (_), but such identifiers are -on most cases- considered reserved for compiler-specific keywords or external identifiers, as well as identifiers containing two successive underscore characters anywhere. In no case can they begin with a digit.
- C++ uses a number of keywords to identify operations and data descriptions, therefore, identifiers created by a programmer cannot match these keywords. The standard reserved keywords that cannot be used for programmer created identifiers are:
- `alignas, alignof, and, and_eq, asm, auto, bitand, bitor, bool, break, case, catch, char, char16_t, char32_t, class, compl, const, constexpr, const_cast, continue, decltype, default, delete, do, double, dynamic_cast, else, enum, explicit, export, extern, false, float, for, friend, goto, if, inline, int, long, mutable, namespace, new, noexcept, not, not_eq, nullptr, operator, or, or_eq, private, protected, public, register, reinterpret_cast, return, short, signed, sizeof, static, static_assert, static_cast, struct, switch, template, this, thread_local, throw, true, try, typedef, typeid, typename, union, unsigned, using, virtual, void, volatile, wchar_t, while, xor, xor_eq`
Note: The C++ language is a "case-sensitive" language. That means that an identifier written in capital letters is not equivalent to another one with the same name but written in small letters. 

# Fundamental data types
 - Fundamental data types are basic types implemented directly by the language that represent the basic storage units supported natively by most systems. They can mainly be classified into:
 - **Character types:** They can represent a single character, such as 'A' or '$'. The most basic type is char, which is a one-byte character. Other types are also provided for wider characters.
 - **Numerical integer types:** They can store a whole number value, such as 7 or 1024. They exist in a variety of sizes, and can either be **signed** or **unsigned**, depending on whether they support negative values or not.
 - **Floating-point types:** They can represent real values, such as 3.14 or 0.01, with different levels of precision, depending on which of the three floating-point types is used.
 - **Boolean type:** The boolean type, known in C++ as bool, can only represent one of two states, `true` or `false`.
![[Pasted image 20250104223535.png]]
- The names of certain integer types can be abbreviated without their *signed* and *int* components - only the part not in italics is required to identify the type, the part in italics is optional. i.e., *signed* short *int* can be abbreviated as `signed short`, `short int`, or simply `short`; they all identify the same fundamental type.
![[Pasted image 20250104225822.png]]
- A 16-bit unsigned integer would be able to represent 65536 distinct values in the range 0 to 65535, while its signed counterpart would be able to represent, on most cases, values between -32768 and 32767.
- The properties of fundamental types in a particular system and compiler implementation can be obtained by using the **numeric_limits** classes (see standard header \<limits\>). If for some reason, types of specific sizes are needed, the library defines certain fixed-size type aliases in header \<cstdint\>.
- The types such as characters, integers, floating-point, and boolean are collectively known as arithmetic types. But two additional fundamental types exist: `void`, which identifies the lack of type; and the type `nullptr`, which is a special type of pointer.

# Declaration of variables
- C++ is a strongly-typed language, and requires every variable to be declared with its type before its first use. This informs the compiler the size to reserve in memory for the variable and how to interpret its value. The syntax to declare new variable in C++ is straightforward: we simply write the type followed by the variable name (i.e., its identifier). for example:
```cpp
int a;
float mynumber;
```
- The first one declares a variable of type int with the identifier a. The second one declares a variable of type float with the identifier mynumber. Once declared, the variables a and mynumber can be used within the rest of the scope of the program.
- If declaring more than one variable of the same type, they can all be declared in a single statement by separating their identifiers with commas. For example:
```cpp
int a, b, c;
```
- This declares three variables (a, b, and c), all of them of type int, and has exactly the same meaning as:
```cpp
int a;
int b;
int c;
```
- To see what variable declaration looks like in action let's create a sample program:
```cpp
// Operating with variables
#include <iostream>
using namespace std;

  

int main(){

// declaring variables
	int a, b;
	int result;

	// process

	a = 5;
	b = 2;
	a = a + 1;
	result = a - b;

	// print out the result
	cout << result << endl;

	return 0;
}
```


































