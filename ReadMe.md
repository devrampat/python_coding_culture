Pylint is a quality checker for Python programming language that follows the style recommended by PEP 8. 

This document provides guidelines to write clear code in Python with the main goal of improving readability and consistency of the code. Code is read much more often than is written that is why is so important to stick to conventions that will help us or other people to understand more easily the available code. 

In this article, we explain 10 rules of PEP 8 that can make your Python code easier for others to read and how we can check them with Pylint. Let’s get started! 💪

*Install Pylint*
Pylint is a third party library that is not available by default in Python. Since Pylint is not part of the Python Standard Library, we need to install it separately. This can easily be achieved by using the pip package. 

Pip is a standard package manager for Python, allowing to install and manage packages that are not included in the Python Standard Library. 
To check if pip is installed, you can execute the following command in your Windows Terminal:
pip --version

As shown above, the version 10.0.1 is already available in our system. Now, we can install pylint, running in the command prompt:

pip install pylint

*Use Pylint*

Once we have installed pylint, we can easily use it by running the command pylint with the name of the file as follows:

pylint filename.py


*Coding conventions (PEP 8)*
PEP 8 is a style guide that defines how your python code should be formatted to maximize its readability. In this post, we will only cover some key points; therefore, if you want to study the topic in greater detail, I recommend you take a look at the guide.
PEP 8 -- Style Guide for Python Code


1. Multi-line statement
In Python, we use implicit continuation line inside parethesis (()), brackets ([]),and braces ({}). Implicit means that we do not write the line continuation character (\) to indicate that we extend a statement over multiple lines.
When using implicit continuation lines, the wrapped element should be aligned vertically, or using hanging indentation. In the context of Python, hanging indentation means that the opening parenthesis of a parenthesized statement is the last non-whitespace character of the line, with subsequent lines being indented until the closing parenthesis.
Bad practice
Arguments inside the parenthesis are not aligned vertically, or using hanging indentation.

Pylint output
Pylint detects a wrong indentation.

Good practice
Arguments inside the parenthesis are aligned vertically.



2. Operators
Always surround these operators with a single space on either side:
Assignment (=)
Augmented assignment (+=, -=, etc)
Comparison operators (<, >, <=, >=, ==, !=)
Logical operators (and, or, not)
Membership operators (in, not in)
Identity operators (is, not is)
Bad practice
Operators are not surrounded by spaces.

We can easily disabled a warning in pylint adding a comment at the top of the code as shown above (#pylint: disable=C0114)
The C0114 warning indicates that a module docstring is missing. A docstring is a string that occurs as the first statement in a module, function, class, or method definition. According to PEP 257 (guide containing docstring conventions), all modules should have a docstring at the beginning, describing what the module does.
It is highly recommended to write doctrings in practice. As before, if you want to know more about how to use doctrings in Python, I recommend you take a closer look at PEP 257 guidelines.
PEP 257 -- Docstring Conventions


Good practice
Operators are surrounded with a single space on either side.

3. Whitespaces after a comma, semicolon, or colon (but not before!)
After a comma, semicolon, or colon, we have to use a whitespace. However, PEP 8 recommends to avoid them immediately before.

Bad practice
In the following code, we can observe the following bad practices:
A whitespace is missing after the comma that separates each element of the list.
A whitespace is missing after the colon (:) that separates each key-value pair in the dictionary.
A whitespace is present immediately before the comma that separates each element of the tuple.


Good practice
There are spaces after, but not before, each comma, colon, and semicolon.

4. Whitespaces inside parentheses, brackets or braces.

Bad practice
Whitespaces are used immediately inside parentheses, brackets, or braces.

Good practice
No whitespaces are used immediately inside parentheses, brackets, or braces.

5. Keyword and default arguments

Keyword arguments
An argument is a value passed to a function when calling it. Python functions accept two types of arguments: (1) positional arguments, and (2) keyword arguments. When calling a function using positional arguments, the arguments must be included in the proper order. On the contrary, the keyword arguments can be provided in an arbitrary order, since these arguments are preceded by an identifier (keyword=value). According to PEP8, we do not have to use spaces around the = sign when calling a function using keyword arguments.

Default arguments
Function arguments can have default values. In case the argument is not provided when calling a function, the argument takes its default value. As before, spaces are not used around the = sign when defining default arguments.

Bad practice
Spaces are used around the = sign when using keyword and default arguments.

Good practice
Spaces are not employed around the = sign.

6. Catching exceptions

To handle exceptions in Python, we use the try and except statements. The try clause contains the operation that can raise an exception, and the except clause includes the code that handles the exception. The try clause is executed statement by statement. However, if an exception occurs, the execution of the try statement stops, and then the except statement is executed.

Bad practice
Here, the code in the except block is executed when any kind of exception occurs during the execution of the try block. According to PEP8 guidelines, it is not recommended to use bare except clauses, since they will catch all exceptions, including SystemExit and KeyboardInterrupt exceptions, making it harder to interrupt a program with Control-C.

Good practice
We should specify which error we want to handle in the except block as follows:

Now, the program catches the TypeError exception, but not other exceptions.


7. Boolean variables
Bad practice
In if statements, it is not correct to compare boolean variables to True or False using == or is.

Good practice
We have to use the boolean variable directly in the if statement as follows:

8. Check for prefixes and suffixes

Bad practice
It is a bad practice to use string slicing to check for prefixes or suffixes.

Good practice
According to the style guide PEP8, we have to use str.startswith() and str.endswith() to check for prefixes or suffixes.


9. Imports

A module is a file consisting of Python code. If you are working on big projects, it makes sense to organize your code into multiple files, and import them into other Python files when necessary. To import a Python module, we just type the statement import followed by the name of the file. Besides importing our own modules, we can also import built-in modules available in the python standard library as well as in third-party libraries. According to PEP8 guidelines, imports are written at the top of the Python script, each one on a separated line. In addition, imports should be grouped in the following order:
Standard library imports
Third-party imports
Local scripts imports

Bad practice
Imports are not written in separated lines, and are not grouped in the correct order.

Good practice
Imports are written in separated lines, and are grouped in the correct order.

10. Lambda expressions
Lambda expressions are anonymous short-term functions with the following syntax:
lambda arguments: expression
These functions can have multiple arguments, returning the value provided by expression. We can find them not only in Python; other programming languages support lambda functions as well.
According to PEP8 guidelines, it is not recommended to assign a lambda function directly to an identifier. In this case, it is advisable to use regular functions (defined with def keyword).

Bad practice
A lambda expression is assigned directly to an identifier (multiply).

Good practice
We create the function with the def keyword.

Pylint is not perfect, but it can really help to improve the quality of your code!