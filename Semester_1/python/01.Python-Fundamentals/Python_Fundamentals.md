# Python Fundamentals

## 1. What is Python?

Python is a **high-level, general-purpose programming language**.

Python was created by **Guido van Rossum** and first released in
**1991**.

Python is designed to make code easy to read and write. Its syntax is
close to normal English compared with many other programming languages.

### Where is Python used?

Python is used in many areas:

-   Web development
-   Backend development
-   Data analysis
-   Data science
-   Artificial intelligence and machine learning
-   Automation and scripting
-   Testing
-   Cybersecurity
-   Scientific computing
-   Desktop applications
-   DevOps and cloud automation

### Important characteristics of Python

  -----------------------------------------------------------------------
  Feature                   |         Meaning
  ----------------------------------- -----------------------------------
  High-level                :        You can write programs without
                                      dealing directly with hardware
                                      details.

  Interpreted               :         Python code is executed by the
                                      Python runtime.

  Dynamically typed         :         You do not normally declare a
                                      variable's type explicitly.

  General-purpose           :         Python can be used for many
                                      different types of applications.

  Object-oriented           :          Python supports classes and
                                      objects.

  Easy to read              :          Python syntax is designed to be
                                      simple and readable.

  Cross-platform            :          Python programs can run on Windows,
                                      macOS, Linux, and other systems.

  Open source               :          Python is freely available and has
                                      a large community.
  -----------------------------------------------------------------------

> **Note:** Python's execution model is more accurately described as
> compiling source code to bytecode and then executing that bytecode on
> the Python virtual machine. Calling Python simply "interpreted" is
> common for beginners, but it is an oversimplification.

------------------------------------------------------------------------

## 2. Why Python is Popular

Python is one of the most widely used programming languages because it
combines simple syntax with a huge ecosystem.

### 1. Easy syntax

Python uses fewer symbols and less boilerplate than many languages.

``` python
print("Hello, World!")
```

A beginner can understand this quickly.

### 2. Large library ecosystem

Python has a huge collection of built-in modules and third-party
packages.

Examples:

-   `math` --- mathematical operations
-   `datetime` --- dates and times
-   `os` --- operating-system operations
-   `requests` --- HTTP requests
-   `pandas` --- data analysis
-   `numpy` --- numerical computing
-   `django` --- web development
-   `flask` --- web development
-   `fastapi` --- API development
-   `tensorflow` --- machine learning
-   `pytorch` --- machine learning

### 3. Large community

Python has a large developer community.

This means:

-   Many tutorials are available.
-   Many problems already have solutions online.
-   Many open-source packages are available.
-   Companies can find Python developers more easily.

### 4. Used in many industries

Python is not limited to one field.

For example:

``` text
Web Development       -> Django, Flask, FastAPI
Data Science          -> NumPy, Pandas
Machine Learning      -> PyTorch, TensorFlow
Automation             -> Python scripts
Testing                -> pytest
DevOps                 -> Automation and infrastructure scripts
```

### 5. Good for beginners

Python lets beginners focus more on programming logic instead of
complicated syntax.

### Interview Tip

**Question:** Why is Python popular?

**Good answer:**

> Python is popular because it has simple and readable syntax, a large
> ecosystem of libraries and frameworks, strong community support,
> cross-platform support, and applications in areas such as web
> development, automation, data science, AI, and machine learning.

Do not say only:

> "Python is popular because it is easy."

That answer is incomplete.

------------------------------------------------------------------------

## 3. Writing and Running a Python Program

A Python program can be written in a file with the `.py` extension.

Example:

``` python
print("Hello, World!")
```

Save the file as:

``` text
hello.py
```

### Understanding the code

``` python
print("Hello, World!")
```

-   `print` is a built-in Python function.
-   `"Hello, World!"` is a string.
-   `print()` displays the value on the screen.

### Comment

``` python
# This is a comment - ignored by the interpreter
print("Hello, World!")
```

A comment starts with `#`.

Python does not execute the comment as a Python statement.

Comments are used to explain code.

Example:

``` python
# Store student's age
age = 20
```

### Running the Program

Open the terminal in the folder containing `hello.py`.

Run:

``` bash
python hello.py
```

On some systems, especially where multiple Python versions are
installed, you may use:

``` bash
python3 hello.py
```

### Example

File:

``` text
hello.py
```

Code:

``` python
# This is a comment - ignored by the interpreter

print("Hello, World!")
```

Terminal:

``` bash
python hello.py
```

Output:

``` text
Hello, World!
```

### Interview Tip

**Question:** What is the purpose of `#` in Python?

**Answer:**

`#` starts a single-line comment. The comment is not executed as Python
code and is mainly used to explain the program.

------------------------------------------------------------------------

## 4. Statement in Python

A **statement** is an instruction that Python can execute.

Example:

``` python
x = 10
```

This is an assignment statement.

Another example:

``` python
print("Hello")
```

This is a function-call statement.

A Python program can contain many statements:

``` python
name = "Rahul"
age = 20

print(name)
print(age)
```

Each instruction performs some action.

### Statements and Line Breaks

Normally, each line contains one statement:

``` python
x = 10
y = 20
print(x + y)
```

Python uses indentation to define blocks of code.

Example:

``` python
if age >= 18:
    print("Adult")
```

The indented line belongs to the `if` block.

### Semicolons

Python allows multiple statements on one line using `;`:

``` python
x = 10; y = 20
```

But this is generally discouraged because separate lines are easier to
read.

Prefer:

``` python
x = 10
y = 20
```

------------------------------------------------------------------------

# 5. Variables

A **variable** is a name that refers to a value/object.

Example:

``` python
name = "Amit"
age = 21
salary = 50000
```

Here:

-   `name` refers to the string `"Amit"`
-   `age` refers to the integer `21`
-   `salary` refers to the integer `50000`

Python does not require you to declare the variable type first.

Example:

``` python
age = 21
```

You do not write:

``` text
int age = 21
```

as you commonly would in languages such as Java or C++.

### Variable Naming Rules

  -----------------------------------------------------------------------
  Rule                    Valid Example           Invalid Example
  ----------------------- ----------------------- -----------------------
  Must start with a       `_value`, `name1`       `1value`
  letter or underscore                            

  May contain letters,    `student_name`          `student-name`
  digits, underscores                             

  Case-sensitive          `Age` and `age` are     ---
                          different               

  Cannot be a Python      `total`, `count`        `for`, `class`, `if`
  keyword                                         

  No spaces allowed       `first_name`            `first name`
  -----------------------------------------------------------------------

### Rule 1: Must Start with a Letter or Underscore

Valid:

``` python
name = "Amit"
_value = 10
student1 = "Rahul"
```

Invalid:

``` python
1student = "Rahul"
```

A variable cannot start with a digit.

### Rule 2: Can Contain Letters, Digits, and Underscores

Valid:

``` python
student_name = "Amit"
student1 = "Amit"
total_marks = 500
```

Invalid:

``` python
student-name = "Amit"
```

`-` is treated as the subtraction operator, not as part of a variable
name.

### Rule 3: Python is Case-Sensitive

These are different variables:

``` python
age = 20
Age = 30
```

Therefore:

``` python
print(age)
print(Age)
```

produces:

``` text
20
30
```

### Rule 4: Cannot Use Python Keywords

Python has reserved words called **keywords**.

Examples:

``` text
if
else
for
while
class
def
return
import
try
except
True
False
None
```

You cannot use these as normal variable names.

Invalid:

``` python
class = 10
```

Valid:

``` python
class_name = "Python"
```

### Rule 5: No Spaces

Invalid:

``` python
student name = "Amit"
```

Valid:

``` python
student_name = "Amit"
```

### Recommended Naming Style

Python recommends **snake_case** for normal variable and function names.

Example:

``` python
student_name = "Amit"
total_marks = 450
first_name = "Rahul"
employee_salary = 50000
```

Avoid:

``` python
studentName = "Amit"
```

when following standard Python style.

`studentName` is valid Python, but `student_name` follows the usual PEP
8 convention.

------------------------------------------------------------------------

## Important --- Interview Tip

### What is PEP 8?

**PEP 8** is Python's official style guide.

PEP stands for **Python Enhancement Proposal**.

PEP 8 defines conventions for writing readable Python code, including:

-   Naming
-   Indentation
-   Spaces
-   Line length
-   Imports
-   Blank lines
-   Code layout

Example:

``` python
student_name = "Amit"
total_marks = 450
```

is preferred over:

``` python
studentName = "Amit"
totalMarks = 450
```

when following normal Python naming conventions.

### Interview Answer

> PEP 8 is the style guide for Python code. It provides conventions for
> naming, indentation, spacing, imports, and code layout so that Python
> code remains consistent and readable.

------------------------------------------------------------------------

# 6. Assigning Values

The `=` operator is used for assignment.

``` python
x = 10
```

This means the object/value `10` is assigned to the name `x`.

## Single Assignment

``` python
x = 10
name = "Amit"
age = 21
```

Each variable gets one value.

## Multiple Assignment --- Same Value

You can assign the same value to multiple variables:

``` python
a = b = c = 100

print(a)
print(b)
print(c)
```

Output:

``` text
100
100
100
```

All three names refer to the same integer object.

## Multiple Assignment --- Different Values

Python allows multiple assignment in one line:

``` python
x, y, z = 5, 10, 15

print(x, y, z)
```

Output:

``` text
5 10 15
```

This is called **multiple assignment** or **iterable unpacking**
depending on the situation.

### Swapping Variables

Python can swap values without a temporary variable:

``` python
x = 10
y = 20

x, y = y, x

print(x)
print(y)
```

Output:

``` text
20
10
```

This is a useful Python feature.

------------------------------------------------------------------------

# 7. Variables as References

This is an important Python concept.

In Python, a variable is better understood as a **name/reference to an
object**, rather than a box that permanently stores a value.

Example:

``` python
x = 10
```

Conceptually:

``` text
x ───────> 10
```

The name `x` refers to the integer object `10`.

Now:

``` python
x = 20
```

The name `x` is made to refer to another object:

``` text
x ───────> 20
```

### Example with Two Variables

``` python
x = 10
y = x
```

Conceptually:

``` text
x ───────> 10
y ───────> 10
```

Both names refer to the same integer object.

### Important Interview Point

Python variables do not have a fixed type.

The **object has a type**.

Example:

``` python
x = 10
print(type(x))

x = "Hello"
print(type(x))
```

Output:

``` text
<class 'int'>
<class 'str'>
```

The name `x` first refers to an integer object and later refers to a
string object.

This is one reason Python is called **dynamically typed**.

------------------------------------------------------------------------

# 8. Data Types in Python

A data type tells us what kind of object/value we are working with.

Common Python data types include:

  Data Type    Example              Description
  ------------ -------------------- -------------------------------
  `int`        `10`                 Integer numbers |
  `float`      `10.5`               Decimal numbers |
  `complex`    `2 + 3j`             Complex numbers  |
  `str`        `"Hello"`            Text |
  `bool`       `True`               Boolean value |
  `list`       `[1, 2, 3]`          Ordered, mutable collection |
  `tuple`      `(1, 2, 3)`          Ordered, immutable collection |
  `set`        `{1, 2, 3}`          Collection of unique values |
  `dict`       `{"name": "Amit"}`   Key-value collection | 
  `NoneType`   `None`               Represents absence of a value |

For this beginner topic, focus first on:

``` text
int
float
complex
str
bool
None
```

Then learn collection types in later topics.

------------------------------------------------------------------------

## 8.1 `int`

`int` represents whole numbers.

``` python
age = 21
count = 100
temperature = -5
```

Examples:

``` python
print(type(21))
print(type(-5))
```

Output:

``` text
<class 'int'>
<class 'int'>
```

------------------------------------------------------------------------

## 8.2 `float`

`float` represents decimal numbers.

``` python
price = 99.50
height = 5.8
temperature = -2.5
```

Example:

``` python
print(type(99.50))
```

Output:

``` text
<class 'float'>
```

------------------------------------------------------------------------

## 8.3 `str`

`str` represents text.

``` python
name = "Amit"
city = 'Pune'
```

Both single and double quotes can be used:

``` python
name = "Amit"
city = 'Pune'
```

A string can contain spaces:

``` python
message = "Hello Python"
```

------------------------------------------------------------------------

## 8.4 `bool`

Boolean values represent logical states.

Python has two Boolean values:

``` python
True
False
```

Example:

``` python
is_logged_in = True
is_admin = False
```

Important:

``` python
True
False
```

must begin with capital letters.

------------------------------------------------------------------------

## 8.5 `complex`

Python supports complex numbers.

Example:

``` python
z = 2 + 3j
```

Here:

-   `2` is the real part.
-   `3` is the imaginary part.
-   `j` represents the imaginary unit in Python.

Check the type:

``` python
print(type(z))
```

Output:

``` text
<class 'complex'>
```

------------------------------------------------------------------------

## 8.6 `None`

`None` represents the absence of a value.

Example:

``` python
result = None
```

Check its type:

``` python
print(type(result))
```

Output:

``` text
<class 'NoneType'>
```

`None` is not the same as:

``` text
0
""
False
```

It means there is no value/object assigned in that situation.

------------------------------------------------------------------------

# 9. Checking a Variable's Type

Python provides the built-in `type()` function.

Syntax:

``` python
type(value)
```

Example:

``` python
age = 21

print(type(age))
```

Output:

``` text
<class 'int'>
```

More examples:

``` python
name = "Amit"
price = 99.5
is_active = True
number = 2 + 3j
data = None

print(type(name))
print(type(price))
print(type(is_active))
print(type(number))
print(type(data))
```

Output:

``` text
<class 'str'>
<class 'float'>
<class 'bool'>
<class 'complex'>
<class 'NoneType'>
```

### Interview Tip

**Question:** How do you check the type of a variable in Python?

**Answer:**

Use the built-in `type()` function.

``` python
x = 10
print(type(x))
```

------------------------------------------------------------------------

# 10. Type Casting

**Type casting** means converting a value from one data type to another
compatible type.

Common functions:

``` python
int()
float()
str()
bool()
complex()
```

## String to Integer

``` python
age = "21"

age = int(age)

print(age)
print(type(age))
```

Output:

``` text
21
<class 'int'>
```

## Integer to Float

``` python
x = 10

y = float(x)

print(y)
print(type(y))
```

Output:

``` text
10.0
<class 'float'>
```

## Integer to String

``` python
age = 21

text = str(age)

print(text)
print(type(text))
```

Output:

``` text
21
<class 'str'>
```

## Float to Integer

``` python
price = 99.99

x = int(price)

print(x)
```

Output:

``` text
99
```

The fractional part is removed. It is not rounded.

For example:

``` python
print(int(9.99))
```

Output:

``` text
9
```

## String to Float

``` python
price = "99.50"

price = float(price)

print(price)
```

Output:

``` text
99.5
```

## Boolean Conversion

Python can convert values to Boolean.

``` python
print(bool(1))
print(bool(0))
print(bool("Hello"))
print(bool(""))
```

Output:

``` text
True
False
True
False
```

Empty values are commonly considered **falsy**, while many
non-empty/non-zero values are **truthy**.

### Important Casting Error

This works:

``` python
x = int("100")
```

This does not work:

``` python
x = int("hello")
```

It raises a `ValueError` because `"hello"` cannot be converted to an
integer.

### Interview Tip

**Question:** What happens when you do `int("10")`?

**Answer:**

Python converts the string `"10"` into the integer `10`.

``` python
x = int("10")
print(type(x))
```

Output:

``` text
<class 'int'>
```

------------------------------------------------------------------------

# 11. Basic Input and Output

Programs often need to:

1.  Take data from the user.
2.  Process the data.
3.  Display the result.

This is commonly called:

``` text
Input -> Processing -> Output
```

Example:

``` text
User enters age
       ↓
Python processes age
       ↓
Python displays result
```

------------------------------------------------------------------------

## 11.1 Output with `print()`

The `print()` function displays information.

``` python
print("Hello")
print(100)
print(10 + 20)
```

Output:

``` text
Hello
100
30
```

### Printing Multiple Values

``` python
name = "Amit"
age = 21

print(name, age)
```

Output:

``` text
Amit 21
```

Python separates multiple arguments with a space by default.

### `sep`

You can change the separator:

``` python
print("2026", "08", "15", sep="-")
```

Output:

``` text
2026-08-15
```

### `end`

By default, `print()` moves to a new line after printing.

You can change this using `end`:

``` python
print("Hello", end=" ")
print("World")
```

Output:

``` text
Hello World
```

------------------------------------------------------------------------

# 12. Formatted Output with f-strings

An **f-string** is a convenient way to insert variables and expressions
into strings.

Put `f` before the string:

``` python
name = "Amit"
age = 21

print(f"My name is {name} and I am {age} years old.")
```

Output:

``` text
My name is Amit and I am 21 years old.
```

### Expressions Inside f-strings

``` python
a = 10
b = 20

print(f"Sum = {a + b}")
```

Output:

``` text
Sum = 30
```

### Example

``` python
product = "Laptop"
price = 50000

print(f"The price of {product} is ₹{price}.")
```

### Why Use f-strings?

Without f-string:

``` python
print("My age is", age)
```

With f-string:

``` python
print(f"My age is {age}")
```

f-strings are usually clearer when building formatted messages.

### Interview Tip

**Question:** What is an f-string?

**Answer:**

An f-string is a formatted string literal that allows us to insert
variables and expressions directly inside a string using `{}`.

Example:

``` python
name = "Amit"
print(f"Hello {name}")
```

------------------------------------------------------------------------

# 13. Input with `input()`

The `input()` function takes input from the user.

Example:

``` python
name = input("Enter your name: ")

print(f"Hello {name}")
```

If the user enters:

``` text
Amit
```

Output:

``` text
Hello Amit
```

## Important: `input()` Returns a String

This is a very important interview concept.

Consider:

``` python
age = input("Enter your age: ")

print(type(age))
```

Even if the user enters:

``` text
21
```

the type is:

``` text
<class 'str'>
```

So if you need a number, convert it.

``` python
age = int(input("Enter your age: "))

print(age)
print(type(age))
```

Now the type is:

``` text
<class 'int'>
```

### Taking a Float

``` python
price = float(input("Enter price: "))

print(price)
```

### Input Example

``` python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print(f"Name: {name}")
print(f"Age: {age}")
```

### Common Beginner Mistake

Wrong:

``` python
age = input("Enter age: ")

print(age + 5)
```

This produces a `TypeError` because `age` is a string.

Correct:

``` python
age = int(input("Enter age: "))

print(age + 5)
```

------------------------------------------------------------------------

# 14. Arithmetic Operators

Arithmetic operators are used to perform mathematical calculations.

  Operator   Name             Example     Result
  ---------- ---------------- ----------- ------------
  `+`        Addition         `10 + 3`    `13`
  `-`        Subtraction      `10 - 3`    `7`
  `*`        Multiplication   `10 * 3`    `30`
  `/`        Division         `10 / 3`    `3.333...`
  `//`       Floor Division   `10 // 3`   `3`
  `%`        Modulus          `10 % 3`    `1`
  `**`       Exponentiation   `10 ** 3`   `1000`

------------------------------------------------------------------------

## 14.1 Addition `+`

``` python
a = 10
b = 5

print(a + b)
```

Output:

``` text
15
```

------------------------------------------------------------------------

## 14.2 Subtraction `-`

``` python
print(10 - 5)
```

Output:

``` text
5
```

------------------------------------------------------------------------

## 14.3 Multiplication `*`

``` python
print(10 * 5)
```

Output:

``` text
50
```

------------------------------------------------------------------------

## 14.4 Division `/`

``` python
print(10 / 3)
```

Output is approximately:

``` text
3.3333333333333335
```

The `/` operator produces a floating-point result.

Even:

``` python
print(10 / 2)
```

produces:

``` text
5.0
```

------------------------------------------------------------------------

## 14.5 Floor Division `//`

Floor division removes the fractional part by taking the floor of the
mathematical result.

``` python
print(10 // 3)
```

Output:

``` text
3
```

Important with negative numbers:

``` python
print(-10 // 3)
```

Output:

``` text
-4
```

Why?

The mathematical result is approximately `-3.333`, and floor means
moving toward negative infinity.

------------------------------------------------------------------------

## 14.6 Modulus `%`

The modulus operator returns the remainder.

``` python
print(10 % 3)
```

Output:

``` text
1
```

Because:

``` text
10 = 3 × 3 + 1
```

### Common Use: Even/Odd

``` python
number = 10

print(number % 2)
```

Output:

``` text
0
```

If:

``` python
number % 2 == 0
```

the number is even.

Example:

``` python
number = 7

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

------------------------------------------------------------------------

## 14.7 Exponentiation `**`

Used for powers.

``` python
print(2 ** 3)
```

Output:

``` text
8
```

Because:

``` text
2 × 2 × 2 = 8
```

Another example:

``` python
print(5 ** 2)
```

Output:

``` text
25
```

------------------------------------------------------------------------

# 15. Arithmetic Operations

We can combine variables and arithmetic operators.

``` python
a = 20
b = 10

addition = a + b
subtraction = a - b
multiplication = a * b
division = a / b
floor_division = a // b
remainder = a % b
power = a ** 2

print(addition)
print(subtraction)
print(multiplication)
print(division)
print(floor_division)
print(remainder)
print(power)
```

### Operator Precedence

Python follows mathematical operator precedence.

Example:

``` python
result = 10 + 5 * 2
print(result)
```

Output:

``` text
20
```

Multiplication happens before addition.

Use parentheses when you want to make the order explicit:

``` python
result = (10 + 5) * 2

print(result)
```

Output:

``` text
30
```

### Basic Precedence Order

A useful beginner-level order is:

``` text
()
**
*, /, //, %
+, -
```

Example:

``` python
result = 10 + 2 * 3
```

First:

``` text
2 * 3 = 6
```

Then:

``` text
10 + 6 = 16
```

So:

``` python
print(result)
```

Output:

``` text
16
```

------------------------------------------------------------------------

# 16. Common String Operations

Strings are sequences of characters.

Example:

``` python
text = "Python"
```

Python provides many useful operations for strings.

------------------------------------------------------------------------

## 16.1 String Concatenation

The `+` operator can join strings.

``` python
first_name = "Amit"
last_name = "Patil"

full_name = first_name + " " + last_name

print(full_name)
```

Output:

``` text
Amit Patil
```

Both operands should be strings.

This causes an error:

``` python
age = 21

print("Age: " + age)
```

Correct:

``` python
print("Age: " + str(age))
```

Or preferably:

``` python
print(f"Age: {age}")
```

------------------------------------------------------------------------

## 16.2 String Repetition

The `*` operator can repeat a string.

``` python
print("Hi " * 3)
```

Output:

``` text
Hi Hi Hi
```

------------------------------------------------------------------------

## 16.3 Finding String Length

Use `len()`:

``` python
text = "Python"

print(len(text))
```

Output:

``` text
6
```

------------------------------------------------------------------------

## 16.4 Changing Case

``` python
text = "Python Programming"

print(text.upper())
print(text.lower())
```

Output:

``` text
PYTHON PROGRAMMING
python programming
```

Other useful methods:

``` python
text.capitalize()
text.title()
text.swapcase()
```

------------------------------------------------------------------------

## 16.5 Removing Extra Spaces

``` python
text = "  Python  "

print(text.strip())
```

Output:

``` text
Python
```

Related methods:

``` python
text.lstrip()
text.rstrip()
```

------------------------------------------------------------------------

## 16.6 Replacing Text

``` python
text = "I like Java"

new_text = text.replace("Java", "Python")

print(new_text)
```

Output:

``` text
I like Python
```

------------------------------------------------------------------------

## 16.7 Checking Whether Text Exists

Use the `in` operator:

``` python
text = "Python Programming"

print("Python" in text)
print("Java" in text)
```

Output:

``` text
True
False
```

------------------------------------------------------------------------

## 16.8 String Comparison

Strings can be compared:

``` python
a = "apple"
b = "banana"

print(a == b)
print(a != b)
```

Output:

``` text
False
True
```

String comparisons are case-sensitive:

``` python
print("Python" == "python")
```

Output:

``` text
False
```

------------------------------------------------------------------------

# 17. Practice Exercises

Try these exercises without looking at the solution first.

## Exercise 1 --- Hello Student

Write a program that prints:

``` text
Hello, Python!
I am learning Python.
```

------------------------------------------------------------------------

## Exercise 2 --- Student Details

Create variables for:

-   Student name
-   Age
-   City
-   Course

Print all details using an f-string.

Expected style:

``` text
Name: Amit
Age: 21
City: Pune
Course: Python
```

------------------------------------------------------------------------

## Exercise 3 --- Basic Arithmetic

Create two variables:

``` python
a = 20
b = 6
```

Print:

-   Addition
-   Subtraction
-   Multiplication
-   Division
-   Floor division
-   Remainder
-   Power

------------------------------------------------------------------------

## Exercise 4 --- User Input

Take the user's:

-   Name
-   Age

Then print:

``` text
Hello Amit, you are 21 years old.
```

Remember that `input()` returns a string.

------------------------------------------------------------------------

## Exercise 5 --- Rectangle

Take length and width from the user.

Calculate:

``` text
Area = length × width
Perimeter = 2 × (length + width)
```

Print both results using f-strings.

------------------------------------------------------------------------

## Exercise 6 --- Simple Calculator

Take two numbers from the user and print:

``` text
Addition
Subtraction
Multiplication
Division
```

Use `float()` so that the user can enter decimal numbers.

------------------------------------------------------------------------

## Exercise 7 --- Even or Odd

Take an integer from the user.

Use `%` to determine whether the number is:

``` text
Even
```

or:

``` text
Odd
```

------------------------------------------------------------------------

## Exercise 8 --- String Operations

Take a string from the user and print:

-   Length
-   Uppercase
-   Lowercase
-   First character
-   Last character
-   Whether `"python"` exists in the string

Try this with:

``` text
I am learning Python
```

Remember that string matching is case-sensitive.

------------------------------------------------------------------------

## Exercise 9 --- Type Practice

Create variables containing:

``` python
10
10.5
"10"
True
2 + 3j
None
```

Print the type of every variable using `type()`.

------------------------------------------------------------------------

## Exercise 10 --- Type Casting

Start with:

``` python
number = "100"
```

Convert it to:

``` text
int
float
```

Then print the values and their types.

------------------------------------------------------------------------

## Exercise 11 --- Swap Two Variables

Create:

``` python
a = 10
b = 20
```

Swap their values without using a third variable.

Expected result:

``` text
a = 20
b = 10
```

------------------------------------------------------------------------

## Exercise 12 --- Bill Calculator

Take:

-   Item name
-   Item price
-   Quantity

Calculate:

``` text
Total = price × quantity
```

Print:

``` text
Item: Laptop
Price: 50000
Quantity: 2
Total: 100000
```

Use an f-string.

------------------------------------------------------------------------

# 18. Mini Assignment

## Student Information and Marks Calculator

Create a Python program that asks the user for:

``` text
Student name
Student age
Math marks
Science marks
English marks
```

The program should calculate:

``` text
Total marks
Average marks
```

Then display all information in a readable format.

### Requirements

1.  Use variables.
2.  Use `input()`.
3.  Use appropriate type casting.
4.  Use arithmetic operators.
5.  Use f-strings.
6.  Use `type()` at least once while testing your program.
7.  Use meaningful variable names.
8.  Follow `snake_case`.
9.  Add at least two useful comments.
10. Do not use unnecessary semicolons.

### Expected Output Style

``` text
Enter student name: Amit
Enter age: 21
Enter Math marks: 80
Enter Science marks: 75
Enter English marks: 90

----- Student Report -----
Name: Amit
Age: 21
Math: 80
Science: 75
English: 90
Total: 245
Average: 81.67
```

------------------------------------------------------------------------

# 19. Interview Questions

Use these questions to test yourself.

### Beginner Questions

1.  What is Python?
2.  Who created Python?
3.  When was Python first released?
4.  Why is Python popular?
5.  What is a Python interpreter/runtime?
6.  What is a `.py` file?
7.  How do you run a Python file from the terminal?
8.  What is a statement in Python?
9.  What is a variable?
10. What are the rules for naming variables?
11. Is Python case-sensitive?
12. What is PEP 8?
13. What is snake_case?
14. Can a variable name start with a number?
15. Can a variable name contain a hyphen?
16. What is multiple assignment?
17. What is dynamic typing?
18. How are Python variables related to objects?
19. How do you check the type of a variable?
20. What is type casting?
21. What does `input()` return?
22. What is the difference between `int()` and `float()`?
23. What is an f-string?
24. What is the difference between `/` and `//`?
25. What does `%` do?
26. What does `**` do?
27. How do you concatenate two strings?
28. How do you find the length of a string?
29. What is `None`?
30. What are the basic built-in Python data types?

### Interview Tip

Do not only memorize definitions.

For each question, be able to give:

``` text
Definition
+
Example
+
Practical use
```

For example:

**Question:** What is dynamic typing?

Weak answer:

> Python is dynamically typed.

Better answer:

> Python is dynamically typed, which means we do not have to declare a
> variable's type explicitly. A name can refer to objects of different
> types during program execution.

Example:

``` python
x = 10
print(type(x))

x = "Hello"
print(type(x))
```

------------------------------------------------------------------------

# 20. Quick Summary

## Python

-   Python is a high-level, general-purpose programming language.
-   It was created by Guido van Rossum.
-   Python is known for readable syntax and a large ecosystem.

## Program Execution

Create a file:

``` text
hello.py
```

Write:

``` python
print("Hello, World!")
```

Run:

``` bash
python hello.py
```

## Comments

Use `#`:

``` python
# This is a comment
```

## Statements

A statement is an instruction that Python executes.

``` python
x = 10
print(x)
```

## Variables

``` python
name = "Amit"
age = 21
```

Use meaningful names and prefer `snake_case`.

## Assignment

Single:

``` python
x = 10
```

Same value:

``` python
a = b = c = 100
```

Different values:

``` python
x, y, z = 5, 10, 15
```

## Variables as References

A variable/name refers to an object.

``` python
x = 10
x = "Hello"
```

The name can refer to objects of different types.

## Data Types

Important beginner types:

``` text
int
float
complex
str
bool
NoneType
```

## Type Checking

``` python
type(x)
```

## Type Casting

``` python
int()
float()
str()
bool()
complex()
```

## Input

``` python
name = input("Enter name: ")
```

Remember:

``` python
input()
```

returns a string.

## Output

``` python
print("Hello")
```

## f-strings

``` python
name = "Amit"

print(f"Hello {name}")
```

## Arithmetic Operators

``` text
+     Addition
-     Subtraction
*     Multiplication
/     Division
//    Floor division
%     Remainder
**    Power
```

## String Operations

Common operations:

``` python
"Hello" + " World"
"Hi " * 3
len("Python")
"python".upper()
"PYTHON".lower()
" Python ".strip()
"Java".replace("Java", "Python")
"Python" in "I love Python"
```

------------------------------------------------------------------------

# Final Checklist

Before moving to the next Python topic, make sure you can:

-   [ ] Explain what Python is.
-   [ ] Explain why Python is popular.
-   [ ] Create a `.py` file.
-   [ ] Write and run a Python program.
-   [ ] Explain comments.
-   [ ] Explain what a statement is.
-   [ ] Create and use variables.
-   [ ] Explain Python variable naming rules.
-   [ ] Use `snake_case`.
-   [ ] Explain PEP 8.
-   [ ] Perform single assignment.
-   [ ] Perform multiple assignment.
-   [ ] Swap two variables.
-   [ ] Explain variables as references.
-   [ ] Identify common Python data types.
-   [ ] Use `type()`.
-   [ ] Perform type casting.
-   [ ] Use `print()`.
-   [ ] Use f-strings.
-   [ ] Take input using `input()`.
-   [ ] Remember that `input()` returns a string.
-   [ ] Use arithmetic operators.
-   [ ] Explain `/`, `//`, and `%`.
-   [ ] Perform common string operations.
-   [ ] Complete the practice exercises.
-   [ ] Complete the mini assignment.
-   [ ] Answer the basic interview questions with examples.
