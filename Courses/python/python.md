---
layout: page
title: Python
permalink: /Courses/Python/
---
# Python Tutorial

## Variables
- Variables are used to store pieces of data with a specific names
- Unlike other programming languages, there is no need to specify the data type of the variable during declaration.
- An example of a variable in python is

```python
 var = 5
```

## Booleans
- A boolean is a data type which stores the value of True and False.
- It is like a light switch which can either be on(True) or off(False).
- When assigning a value to a boolean variable, the value(True or False) must be capitalized.
- An example of a boolean is

```python
a = True
b = False
```

## Whitespace
- In python, the whitespace is the editor which is used to structure code.
- It is always good to properly indent your code with a tab or 4 spaces. The contents in methods and loops should be indented to improve code readability

## Comments
- Comments make your code easier to read and follow.
- Comments also make it easy to collaborate with other on your code.
- The use of the pound sign(#) is used for single line comments in python.
- An example of a single line comment is

```python
 # This is a comment
```

- The use of a set of three quotation marks(""") is used for a multiline comments
- An example of a multiline comment is

```python
"""
This is a
multiline comment.
"""
```

## Math
- Examples of basic mathematics operators in python are

```python
addition = 72 + 23
subtraction = 108 - 204
multiplication = 108 * 2
division = 108 / 9
```

- Exponents are expressed in python through the use of two asterisks between the base and the power
- An example of an exponent is

```python
exponent= 2 ** 3  #2^3 = 8
# The value of the exponent variable is 8
```

- The modulo operator returns the remainder(or modulus) of two numbers from division
- An example of the modulo operator is

```python
remainder = 3 % 2  #The remainder of 3/2 is 1
# The value of remainder variable is 1
```

## Strings
- A string is a data type which is used to store letters, numbers, and/or symbols
- An example of a string is

```python
name = "John"
age = "20"
string = "This is a string"
```

- Some characters may cause some problems when declaring strings. Escaping characters creates a break in the string for python to interpret the problematic character as a string
- An example of the use of a escaping character is

```python
#Problem code
string = 'There's a snake in my boot!'

#Fixed code
string = "There\'s a snake in my boot!"
```

- Each character in a string is assigned a number. which is called the index. Hence a string can be thought of as an array of characters
- An example of how the characters a broken up in a string is

```
+---+---+---+---+---+---+
| P | Y | T | H | O | N |
+---+---+---+---+---+---+
  0   1   2   3   4   5

To access the 'T' in the word we can run the code below:

t = "PYTHON"[2]
# This access the character at index 2 in array/string "PYTHON", which is the character 'T'
```

- String methods let you perform specific operations on strings
- Examples of string methods are

```python
len("String") # Gets the length of the input string

"String".lower() # Removes all the capitalization in the input string and makes it all lower case

"String".upper() # Capitalizes all the characters in the input string

str(2) # Turns any non-string character into a string
```

- Certain methods are used without a dot, such as len("String") or str(2), and other methods are used with a dot, such as "String".lower() and "String".upper(). This is because methods that use dot notation only work with strings. the upper() method only works with strings, however len() and str() methods can work with other data types.

### Printing Strings
- Printing strings and variables are identical. Putting the word "print" in your code will print the value to your console.
- An example of printing is

```python
print "Hello world"
print hello
```

### String concatenation
- The "+" operator between strings will <i>add</i> them together, or concatenating/combining them together
- An example of concatenation is

```python
string = "Hello" + "world" + "!"
```

### Explicit String Conversion
- Sometimes we need to concatenate a string with something that is not a string. To do this, we must convert the non-string data to a string using the str() method.
- An example of explicit string conversion is

```python
print "I have " + str(2) + " apples!"
# The above line prints "I have 2 apples!"
```

### String formatting
- When trying to print a variable in a string, there is an easier way than concatenating the strings together.
- The '%' operator after a string is used to combine a string with variables. Replacing the '%' operator with '%s' will allow combining and string with string variables
- Examples of the use of the '%s' operator is

```python
name = "John"
print "A name is %s" % (name)
```

## Date and Time

- Python can keep track of when something happens through the use of datetime.
- The code below can enable use to use the datetime feature of Python by importing datetime

```python
from datetime import datetime
```

- We can use the function ``` datetime.now()``` to retrieve the current date and time
- An example of printing the current date and time is

```python
from datetime import datetime
print datetime.now()
```

- To retrieve certain parts of date, we can use the methods below

```python
from datetime import datetime
now = datetime.now()

current_year = now.year
current_month = now.month
current_day = now.day
current_hour = now.hour
current_minute = now.minute
current_second = now.second
```

### Printing the date in a specific format

- We can print the date in a specific format by using the '%s' operator for formatting strings
- An example of a formatted date

```python
from datetime import datetime
now = datetime.now()

print '%s/%s/%s' % (now.month, now.day, now.year)
# The statement prints: month/day/year
```

## Conditionals & Flow Control

### Comparators

| Symbol | Meaning  |
| :------------- | :------------- |
|      ==        | equal to       |
|      !=        | not equal      |
|      <         | less than      |
|      <=       | less than or equal |
|      >         | greater than      |
|      >=        | greater than or equal |

### Boolean operators

<u> AND OPERATIONS </u>

| Argument A | Argument B | Solution |
| :------------- | :------------- | :------------- |
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

<u> OR OPERATIONS </u>

| Argument A | Argument B | Solution |
| :------------- | :------------- | :------------- |
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

<u> NOT OPERATIONS </u>

| Argument A | Solution |
| :------------- | :------------- |
| True | False|
| False | True |

### Conditional Statement Syntax
