# Code Documentation

Documentation is as important as the coding itself. In this section we will refer only to the **embedded documentation** of code. Do not confuse the **embedded documentation** with the **supporting documentation**. The first one refers to the explanatory notes that are written in the code itself (such as one-line comments, or the text in help functions), while the latter refers to documentation about the entire *project* (e.g., the `README.md` of a repository). We have talked already about **supporting documentation** in the [Project Structure](https://github.com/HeatherAn/recommended-coding-practices/blob/main/09-Project-Structure.md) section and we will come back to it at a later point when discussing code archiving and publishing practices.

We can distinguish two types of **embedded documentation**: documentation for **developers** and documentation for **users**.  

## For developers: comments

Comments are meant to describe the code to other developers (including your future-self). Thus, you can use comments for planning following steps, tagging what needs to be revisited, describing complex workflows, etc. Comments can be written in the line itself next to the code, or can be written as a one or more lines before a given instruction(s) (**one-line** or **block** comments, respectively). In Python comments are written after a `#` symbol, while in C comments are written after a `//` or enclosed between `/*` and `*/` (using white spaces between the symbols and the text; see the [Prioritize Readability](https://github.com/HeatherAn/recommended-coding-practices/blob/main/12-Prioritize-Readability.md) section). 

When writing comments -regardless of the language- keep in mind the following:  

- **Avoid providing redundant information**. Remember comments are for developers and, if you follow the previous recommendations to enhance the readability of the code, developers should understand already how the instructions work.

- Comments in the code should be **short**. For example, Python [PEP 8](https://www.python.org/dev/peps/pep-0008/) convention establishes comments should have a maximum length of 72 characters. Thus, it is more recommended to use comments before an instruction than next to the instruction.

- If your comment is going to require more than one line, you can use multiple lines. But in general: try to keep it short! Avoid over-using comments. If you think you need to provide more information, perhaps it is time to segment further the code (split the instructions) or perhaps it can be information that should be in the **supporting documentation** rather than in the code itself.

## For users: object documentation

Object documentation is meant to describe the use and functionality of an object to the users of the code. An object could be a function or a class or a module, etc. In Python this type of **embedded documentation** refers to the famous **docstrings**. In C/C++ they are commonly referred to as **comments** (e.g., **function comments**).

Object documentation is more extensive information about what the object does, what other objects it calls, what it takes as input, and what it returns as output (if applicable of course, since it depends on the object). In Python the information is enclosed between `"""` symbols. And it is extremely important! For example: when you define a function in Python, the docstring you add after the line of the `def` is what users will read when looking for the `help()` on that function. For example, let's say you just started working on a function which you defined as:

```
    def sum_numbers(value1, value2):
        """Returns the sum of two values"""
        return value1 + value2
```

The text written in between `"""` symbols is the docstring. You can see (and modify) this docstring by looking at the `__doc__` property of `sum_numbers` (i.e., `sum_numbers.__doc__`). When users do `help(sum_numbers)` to know what the function does, the docstring is what will be printed.

Docstring should be written following a specific convention (the Python styling convention on docstrings is the [PEP 257](https://www.python.org/dev/peps/pep-0257/)) and there are also templates on their format (check out the Docstring section of [this link](https://realpython.com/documenting-python-code/) for more information on formats and documentation tools like [Sphinx](https://www.sphinx-doc.org/en/master/) and [Epydoc](http://epydoc.sourceforge.net/epydoc.html)).

In C text is enclosed between `/*` and `*/` symbols or after a `//` for each line. Unlike Python, the documentation of a function is asked before the function is defined:

```
    // Returns the sum of two double numbers
    double add(double a, double b);
```

The documentation in C and C++ is not as *callable* as Python docstrings. Check more in [Doxygen](https://www.doxygen.nl/manual/docblocks.html) which is a tool that can generate html documentation pages from comments in a program. See more about C++ documentation guidelines in the [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html#Comments).


If you code in another programming language, you can use what is mentioned here to have as reference to what to look for, when looking at documentation conventions.


________________________

[Previous : 14 - Code Errors](https://github.com/HeatherAn/recommended-coding-practices/blob/main/14-Code-Errors.md)  
[Next : 16 - Coding Check Tools](https://github.com/HeatherAn/recommended-coding-practices/blob/main/16-Coding-Check-Tools.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)