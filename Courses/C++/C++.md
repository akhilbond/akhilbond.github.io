---
layout: page
title: Python
permalink: /Courses/C++/
---
# <u>C++ Tutorial</u>

## Overview
- C++ is a programming language developed by Bjarne Stroustrup in 1979 at Bell Labs.

## Programming Environment Setup
- C++ can be coded on an a variety of IDE's or text editors
- Some popular IDE's and text editors are Notepad++, Sublime text, Visual Studio, Atom

## Basics

```C++
#include <iostream.h>
using namespace std;

// main method
main()
{
    cout << "Hello World!";
    return 0;
}
```

- The above code prints "Hello World!" to the screen

- C++ has several headers which contain information that is necessary for your code to run. In the above program, the header <iostream.h> is included

- The code line ``` using namespace std;``` lets the compiler know to use the standard, or std, namespace

- The next line, ``` // main method``` is a single line comment. Single line comments begin with // and end at the end of the line

- The next line, ``` int main()```, is the main function where program execution begins

- The main method cannot be called recursively, its address cannot be taken, and it cannot be predefined or overloaded

- The next line, ``` cout << "Hello World!";```, prints the message "Hello World!" to the screen

- The final line, ``` return 0;```, marks the end of the main function and returns the value 0 to the calling function

## Semicolons and blocks

- The semicolon terminates a statement. This means that each individual statement must be ended with a semicolon

- An example of the use of semicolons is

```C++
x = y;
y = y+1;
add(x,y);
```

- A block is a set of logically connected statements which are enclosed in curly braces

- An example of a block is

```C++
{
  cout << "Hello World"; // prints Hello World
  return 0;
}
```

## Comments

- A single line comment begins with // (two slashes), followed by the desired comment. The comment ends at the end of the line Below is an example

```C++
// This is a comment
```

- A multiline comment begins with "/* (slash asterisk), followed by the desired comment. This comment can take up multiple lines, and the end of the comment is marked with "\*/". Below is an example

```C++
/*
This is a
multiline comment
*/
```

## Data types

### Built-in Data Types

- The 4 built-in data types are
  - Integer data type
  - Floating Point data type
  - Void data type
  - Char data type

#### <u>Integer data type</u>

- An integer is a whole number without a decimal point. Integers can hold numbers from -32768 to 32767

#### <u>Floating point data type</u>

- A floating point is a number with a decimal point

#### <u>Void data type</u>

- Void data types have several uses. It specifies the return type of a function when the function is not returning any value. It can indicate an empty parameter list in a function when no arguments are passed. Finally, a void pointer can be assigned pointer value of any basic data type

#### <u>Char data type</u>

- A char data type is used to store character value in the identifier(variable/operand)

### Derived Data Types

- The 4 derived data types are
  - Array
  - Function
  - Pointers
  - Reference

- We will cover these data types in more details later in this tutorial

### User Defined Data Types

- The 4 user defined data types are
  - Structure
  - Union
  - Class
  - Enumerator

- We will cover these data types in more details later in this tutorial

## Type Conversion

### Automatic Type Conversion

- When an expression contains more than one data elements of different data types, the compiler coverts the smaller data type elements into larger data type elements. This is known as automatic or implicit conversion

### Typecasting

- Type casting in casting a data type to a data element, essentially converting one data type to another. An example of this is

```C++
aCharVar = static_cast<char>(an IntVar)
```

- The 4 typecast operators in C++ are
  - static_cast
  - reinterpret_cast
  - const_cast
  - dynamic_cast

## Literals/Constants

- An identifier which doesn't change it's value during the program execution is known as a constant or literal.

- The keyword "const" is added to the declaration of an identifier to make it constant

- Examples in declaring constants are

```C++
const float pi = 3.14;
const char ch = 'A';
const int rate = 50;
```

## Variable Declaration

- The syntax for general variable declaration is

```
datatype variable_name;
```

- Some examples of variable declarations are

```C++
int a;
float b;
bool c;
// bool is used to store the value true or false
char d;
```

## Arithmetic Operators

- Arithmetic operators are used for arithmetic calculations

- An example of arithmetic operators are

```C++
#include<iostream>
using namespace std;
int main(){
    int num1,num2;
    int add,subs,mul,div,mod;

    cout<<"\nEnter First Number :";
    cin>>num1;

    cout<<"\nEnter Second Number :";
    cin>>num2;

    // (+) operator
    add = num1 + num2;
    cout<<"\nAddition is : "<<add;

    // (-) operator
    subs = num1 - num2;
    cout<<"\nSubtraction is : "<<subs;

    // (\*) operator
    mul = num1 * num2;
    cout<<"\nMultiplication is : "<<mul;

    // (÷) operator
    div = num1 / num2;
    cout<<"\nDivision is : "<<div;

    // (%) operator
    mod = num2 % num1;
    cout<<"\nModulus is : "<<mod;

    return 0;
}
```

- The output of the above code is

```
Output

    Enter First Number : 10
    Enter Second Number : 2
    Addition is : 12
    Subtraction is : 8
    Multiplication is : 20
    Division is : 5
    Modulus is : 2
```

## Assignment Operator

- The assignment operator is used to assign values to variable

- An example of the assignment operator is

```C++
a = b
```

- The above code assigns the value from the right side of the operator to the left side

## Relational Operator

Symbol | Meaning
:----- | :--------------------
==     | equal to
!=     | not equal
<      | less than
<=     | less than or equal
>      | greater than
>=     | greater than or equal

## Logical Operators

<u> AND OPERATIONS (&&) </u>

Argument A | Argument B | Solution
:--------- | :--------- | :-------
True       | True       | True
True       | False      | False
False      | True       | False
False      | False      | False

<u> OR OPERATIONS (\|\|)</u>

Argument A | Argument B | Solution
:--------- | :--------- | :-------
True       | True       | True
True       | False      | True
False      | True       | True
False      | False      | False

<u> NOT OPERATIONS (!)</u>

Argument A | Solution
:--------- | :-------
True       | False
False      | True

## Increment & Decrement

- The increment operator, ++, increases the value of the operand by 1

- The decrement operator, --, decreases the value of the operand by 1

- An example of the increment and decrement operators is

```C++
int  a;
int  b;

// Increment
a = 1;

b = ++x;    // a is now 2, b is also 2
b = a++;    // a is now 3, b is 2

// Decrement
a = 3;
b = a--;    // a is now 2, b is 3
b = --a;    // a is now 1, b is also 1
```

## Bitwise operator

Symbol | Meaning
:----- | :--------------------
&      | Bitwise AND
\|      | Bitwise OR
^      | Bitwise XOR
<<     | Left Shift
>>     | Right Shift

## Conditional/Ternary Operators

- A ternary operator is an operation which takes in 3 inputs

- An example of a conditional operator is an if-else statement

- Syntax for a general conditional statement is

```
(condition) ? expression1 : expression2
```

- In the above code, if the condition is true, then expression1 is evaluated, else expression 2 is evaluated

## Comma Operator

- The comma operator has a left-to-right associativity. This means that two expressions separated are evaluated left to right.

- The comma operator is mainly used for obfuscation of code

- An example of a comma operator is

```C++
#include <iostream>
using namespace std;
int main ()
{
    int i = 1, b = 2, c= 3;

    //comma as a SEPERATOR
    i = b, c;
    //prints the value of i and then a new line
    cout<<i<<"\n";

    // bracket makes its one expression.
    // all expression in brackets will evaluate but
    // i will be assigned with right expression (left-to-right associativity)
    //comma as an  OPERATOR
    i = (b, c);
    cout<<i<<"\n";

    return 0;
}
```

- The output of the code above is
```
2
3
```

## Sizeof Operator

- The sizeof operator returns the size of the operand

## C++ Shorthand

Operator | Example      | Meaning
:------- | :----------  | :----------
+=       | a += 5       | a = a + 5
-=       | a -= 5       |  a = a - 5
\*=      | a \*= 5      |  a = a*5
/=       | a /= 5       | a = a / 5
%=       | a %= 5       | a = a % 5
&&=      | a &&= 5      | a = a && 5
