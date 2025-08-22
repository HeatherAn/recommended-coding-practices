# Coding Check Tools

We have seen some rules that you can follow when writing code. There are tools that can also help you with this. These tools can suggest you format changes depending on the programming language you use. When using these *coding formatters* keep in mind the following:

- Some of them can be used directly **online**, while others can be used via the **command-line**. If you work with (competitive or commercially) sensitive code, then avoid the online one!

- In general (but especially if you use the online code formatters): do not put the entire code there at once! Always use these tools to check the format of **small independent pieces of code**.   

- The tools will mainly check rules like the use of white spaces, indentation, blank lines and the syntax of instructions. But they will not make recommendations about the **naming** of objects nor the **functioning** of the code itself.

- When it comes to Python, all tools will follow the **PEPs** (e.g., [PEP8](https://www.python.org/dev/peps/pep-0008/), [PEP257](https://www.python.org/dev/peps/pep-0257/)). But for other languages -where there is no single convention that is well established nor widely used- check which **convention** the tool follows.  


## Coding Formatters

For Python:

- [Black](https://pypi.org/project/black/)

- [autopep8](https://pypi.org/project/autopep8/)

- [Yet Another Python Formatter YAPF](https://github.com/google/yapf)

- [PEP8 Online](http://pep8online.com/)


For other languages:

- [Code Beautifier](https://codebeautify.org)


## Other Useful References

Python standards:

- [PEP8](https://www.python.org/dev/peps/pep-0008/) Python coding style

- [PEP257](https://www.python.org/dev/peps/pep-0257/) Python docstrings style (documentation of modules, classes, functions, and methods)


C++ standards:

- [Google C++](https://google.github.io/styleguide/cppguide.html) coding style

- [C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md) guidelines

- Other [C++ Coding Standards](https://isocpp.org/wiki/faq/coding-standards)


C standards: 

- [C Style and Coding standards](https://www.doc.ic.ac.uk/lab/cplus/cstyle.html)


MATLAB standard:

- [MATLAB Style Guideline 2.0](https://nl.mathworks.com/matlabcentral/fileexchange/46056-matlab-style-guidelines-2-0)  

- [MATLAB Style Guideline Cheatsheet](https://nl.mathworks.com/matlabcentral/fileexchange/45047-matlab-style-guidelines-cheat-sheet)  


## Using LLMs to format the Code

Nowadays you might find more useful to use AI Apps to help you with the *formatting*, *writing documentation*, *debugging*, etc. This is ok as long as you are aware that the suggested solutions come from models trained on open-source projects. This means that some of the solutions might look quite similar to the code of open-source projects. This is not necessarily troublesome, but you do have to pay attention to it. Specially if the solutions might come from open-source projects that are under not so open licenses. Then you might infring copyright for example.  

________________________

[Previous : 20 - Code Documentation](https://github.com/HeatherAn/recommended-coding-practices/blob/main/20-Code-Documentation.md)  
[Next : 22 - Publish Or Archive](https://github.com/HeatherAn/recommended-coding-practices/blob/main/22-Publish-Or-Archive.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)