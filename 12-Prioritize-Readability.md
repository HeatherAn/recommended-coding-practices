# Prioritize Readability 

Always **prioritize the readability** of the code over anything else. 

- **One-line code**. In some programming languages you can "condense" several instructions in a single line of code (e.g., Python list comprehensions). One-line code is not bad but can sometimes sacrifice readability for the sake of "saving" a few lines of code. When this happens, it might be preferable to write more lines of code. 

- **Length of instructions**. Keep instructions short in order to avoid line wrapping. For example, Python [PEP 8](https://www.python.org/dev/peps/pep-0008/) convention establishes each line of code should have less than 80 characters. This can serve as a rule-of-thumb for other programming languages as C/C++ as well. Shortening the length of the lines of code also implies you should keep the number of parameters to functions small.

- **Use white spaces and blank lines consistently**. In order to increase the readability of the code it is important to establish some rules about the writing itself, and stick to them no matter what! When it comes to the use of spaces there are three things to think of: *indentation*, the use of *white spaces* in the writing of lines of codes, and the use of *blank spaces* to separate different sections of the code.

#### Indentation

Indentation is not mandatory for most programming languages. However indentation helps to properly convey the structure of a code increasing its readability. Thus, even if it is not a requirement for the programming language you use, always try to use indentation to facilitate the visualization of the grouping of statements.  

For indentation **forget about tabs!** Always use spaces instead of tabs. Some IDEs do not "recognize" tab spaces anymore. So instead of using tabs, use **4 white spaces** for indentation. And use a new indentation level for every level of nesting in your program (a new indentation level would be if you use an `if` inside a `for` for example).  

#### White spaces

Use white spaces consistently throughout the code. The following rules are based on Python and C/C++ conventions, but you can apply them for different programming languages. If you work in a quite different language, use the following rules as a reference to what to search for when looking for a convention.

- In languages where you use parenthesis after a keyword like `while`, `for` or `if`, use a white space in between the keyword and the parenthesis. 

    For example: in C code write `for (i = 0; i < 10; i++) {` instead of `for(i = 0; i < 10; i++) {`    


- Put a space between all binary operators (e.g., `<=`, `=`, `+`) and their operands. 

    For example: use `i < 0` instead of `i<0`. One possible exception would be to emphasize precedence. For example: write `a*x + b` instead of `a * x + b`  

- Do not put spaces between an object name, the `.` separator, and a method name. For example: in Python use `int.__str__(num)` instead of `int . __str__(num)`

- Do not put spaces before a semicolon. For example: in C use `int  x = 1;` instead of `int  x = 1 ;`  

- Put a space after each comma in an argument list. For example: in Python write `print(x, y, z)` instead of `print(x , y , z)`

- Put space after each comment delimiter. For example: in C/C++ one-line comments are done after a `//`, thus use `// My comment` instead of `//My comment`

- In general do not use white spaces to align parallel code, unless it *really* enhances the readability of the code. 

For example: in Python use.  

```
    x = 1
    y = 2
    value = 3
```

instead of this:  

```
    x     = 1
    y     = 2
    value = 3
```

#### Blank lines

Use blank lines to separate your code into **logical sections**. For example: in Python write

```
    class MaterialRecord:
        def __init__(self, name, manufacturer):
            self.name = name
            self.manufacturer = manufacturer


    materialRecord = MaterialRecord("PolymerA", "LabX")

    print(materialRecord.name)
```

instead of this:

```
    class MaterialRecord:
        def __init__(self, name, manufacturer):
            self.name = name
            self.manufacturer = manufacturer
    materialRecord = MaterialRecord("PolymerA", "LabX")
    print(materialRecord.name)
```


________________________

[Previous : 11 - Keep It Simple](https://github.com/HeatherAn/recommended-coding-practices/blob/main/11-Keep-It-Simple.md)  
[Next : 13 - Naming Conventions](https://github.com/HeatherAn/recommended-coding-practices/blob/main/13-Naming-Conventions.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)