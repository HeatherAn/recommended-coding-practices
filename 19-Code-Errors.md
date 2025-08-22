# Code Errors

**Errors are unavoidable**. They will happen, that's a fact. No matter how experienced you are (or become) in coding, you will always have to deal with errors. Whether it is because of a typo or something more complex, errors are part of life and we do not have to be afraid of them. 

**Recommendations** on how to deal with errors in the code:

1. Don't panic! It could be just a **typo**.  
2. **Read** the errors.  
3. Program ***defensively***.  

## Typos

Typos are typographical errors that we all make. Sometimes a very long error message can arise because of a very simple typo. For example: just by typing fast you can make a typo in the name of a given file, and then you will get a `File not found` type of error. So before panicking, **always check for typos!**

## Read Errors

Every language has its own way of showing errors. Some of them can be quite informative and may seem a bit dramatic. But they can actually be triggered by typos or errors that are quite straight forward to fix. Therefore, the recommendation is to **always read the error**, and **understand how errors are informed** by the language (compiler/interpreter) you are using. 

To take as a reference: in **Python**, errors are given in the form of **tracebacks**. A traceback refers to the **sequence of function calls** that led to a specific type of error. In the last line of each traceback, Python will tell you the *type of error* it found, and will give a more detailed *error message*.  

Among Python errors and so-called **Exceptions**, the more common ones are:

- Syntax Errors (e.g., forget a `:`)
- `IndentationError` (e.g., unexpected indent)
- `NameError` (e.g., variable is not defined)
- `IndexError` (e.g., trying to access items within a list or string or array that does not exist)
- `FileNotFoundError` (e.g., file is not in the specified directory)
- `UnsupportedOperation` (e.g., attempt to write to a file that was opened read-only)

Check out more on **Errors and Exceptions** in the [Software Carpentry lesson](https://swcarpentry.github.io/python-novice-inflammation/09-errors.html)!

In **C** language on the other hand, error messages are not always easy to read nor they are informative enough for you to figure out what is really happening. There may be errors that happen when compiling the code, while others may happen during the execution of the code. Some errors can even *go* silently during compilation and execution, and you will only notice them when analyzing the expected output.

Different type of errors in C are:

- **Run-time** errors (e.g., dividing by zero)
- **Syntax** errors (e.g., missing the `;` at the end of an instruction) 
- **Semantic** errors (e.g., when variables are not initialized)
- **Logical** errors (errors that are not necessarily flagged, but lead to undesired output)
- **Linker** errors (when the executable file of the program is not created; e.g., when calling the `main` function `Main`)

These errors will not be shown to you with those names. But there are ways to make the errors more visible. For example: some function calls, return a `-1` or `NULL` in case there is an error, and set the error code to `errno`. You can find various error codes defined in `<errno.h>` header file of the C Standard Library. Two useful functions to *see* the errors of `errno` are `perror()` and `strerror()` (`strerror` is defined in `string.h`). Whenever you write functions, use these to make errors more visible. See more about C errors [here](https://www.gnu.org/software/libc/manual/html_node/Error-Codes.html#index-ENOBUFS-117) and [here](https://www.gnu.org/software/libc/manual/html_node/Error-Messages.html).

If you work in other programming languages, **understand** well how errors are presented and when writing functions **make the errors more visible and descriptive**.

## Defensive Programming

When writing code assume there will be errors and prepare for it. **Defensive programming** refers to an entire philosophy which we will brutally summarize as: to write code to **detect errors before they happen**. 

### How can you start programming *defensively*? 

Use **assertions** and **test** the code. 

### Assertions

An assertion is a statement that **something must be true at a certain point** in a program. An assertion that is not satisfied, it is indicative of an error (bug) in the code. When you first start writing the code, add assertions to it as an intrinsic part of functions (and methods). 

In general assertions fall into three categories:

- **Pre-condition**: something that must be true **at the start** of a function.
- **Post-condition**: something that the function guarantees is true **when it finishes**.
- **Invariant**: something that is **always true**.

Different languages have different ways of defining assertions. For example, in Python you can use the `assert` statement to write assertions in the code. See more about `assert` [here](https://docs.python.org/3/reference/simple_stmts.html#assert) and check examples in the Software Carpentry lesson on [Defensive Programming](https://swcarpentry.github.io/python-novice-inflammation/10-defensive.html). The lesson uses Python, but principles can apply to all languages!

In C language, assertions are implemented via the `assert` macro. Check out [this link](https://ptolemy.berkeley.edu/~johnr/tutorials/assertions.html) for further information on C `assert`.


### Testing

Testing is a *must* to ensure the code *works*. There are different philosophies on how to approach testing. Here we will stick to two basic principles:

- Work **one step at a time**. Print and plot as many outputs of instructions as necessary, to see what the code is doing at each step of the way.  

- **Avoid confirmation bias**. This bias refers to subconsciously writing tests to show the code is correct. Recommendation: write tests to find errors instead. Check this [entertaining article](https://medium.com/@Ariel14/programmers-dont-get-blinded-by-the-confirmation-bias-6d8f121d77e8) to see how the author experienced this bias.  

Following these principles, when testing the code:

- Test with **simplified input data**.
- Test a **simplified case** (a case that you can solve *by hand*).
- Compare to a **well-established case** (benchmarking).
- Check **conservation laws** (invariants).
- Visualize! 

Once testing has uncovered problems, the next step is to fix them! This is what is called **debugging**. You will most likely spend >80% of the time debugging a code. Do not worry! That is normal! As mentioned before: **check for typos**, **understand** what the language/compiler/interpreter is informing you, and **read the errors**. Some errors will be easily spotted. Some will not. Some errors will refer to specific issues with the writing of the code (syntax errors, index errors, file not found type of errors, etc.), while others will point out problems related to the actual "functioning" or "processing" of the code (e.g., an algorithm does not converge because of rounding errors).  

For debugging the code:   

- Use a **divide and conquer strategy** to find bugs.
- Change **one thing at a time!**
- **Take distance!** Sometimes we cannot solve the problems in the code because we "are" *too close* to the project. Take a break or ask a colleague to take a look at the code.
- Once a solution is found, think about **turning those annoying bugs into assertions or tests**. 

# Use Git Branches!

Every test, new feature and annoying bug should have its own Git branch. Branches allow you to isolate work and experiment with the code without modifying what works already (e.g., the "official" version).  

- Create a **strategy** on how to use the different Git branches. Having a strategy is crucial regardless if you work with collaborators or not. Check [this article](https://www.toptal.com/git/git-workflows-for-pros-a-good-git-guide) where the author explains different branches strategies. 
- Use **one branch per task**.  
- **Name all branches consistently**. For example: use a naming convention of `test_X`, `feature_X` or `issue_X` for naming a given (**X**) test, feature or issue respectively. And stick to those conventions!  
- **Document** the creation and naming of branches in a supporting documentation file within the project structure (e.g., a README file within a `testing` directory).  
- Work *locally* on a particular branch. If the task was successfully performed, congratulations to yourself! Do you need to merge it with the *local* **main**? Use `git merge` command. You can then push the *local main* to the *remote* **origin/main**.

Do you need a reminder on how to use Git branches? Then check the [Using Git With Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/10-Using-Git-With-Branches.md) section as well as the [Git Cheatsheet](https://github.com/HeatherAn/recommended-coding-practices/blob/main/13-Git-Cheatsheet.md).  


________________________

[Previous : 18 - Naming Conventions](https://github.com/HeatherAn/recommended-coding-practices/blob/main/18-Naming-Conventions.md)  
[Next : 20 - Code Documentation](https://github.com/HeatherAn/recommended-coding-practices/blob/main/20-Code-Documentation.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)