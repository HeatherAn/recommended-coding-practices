# Version Control With Git

**Git** is a sort-of back-end machinery that performs version control of files. Services like **Github** and **Gitlab** make use of this Git machinery.

# How does version control work?

Version control systems start with a base version of a file and then **record all changes** made to it with useful metadata (e.g., information about those changes). This helps you to keep track and understand all the **history of changes** made to each tracked file. A version control system not only allows you to *see* those changes, but it also allows you to **retrieve different versions** of each file (e.g., in case you need to recover a previous version of a file). In that sense, Git allows you to keep track of all changes made to a file as a-sort of "hidden information". So that instead of seeing a visible (most likely long) list of files in your working directory (e.g., `file_v1.dat`, `file_v2_final.dat` ... `file_v10_final_FINAL.dat`), you have a single **hidden directory** (the hidden `.git/` directory) where all that information is stored and it is easily retrievable. 

Aside keeping track of file changes (each record of these changes is called a **commit**), a version control system also allows you to merge the changes made by different people. In this way you can follow the history of different files in different directories, all at the same time! 

The complete history of **commits** for a particular project and their metadata make up what is referred to as a **repository**. Repositories can be kept in sync across different computers, facilitating collaboration among different people. 

___________________
**To keep in mind**: in Gitlab, a repository can also be referred to as a **project**.
___________________

![phd101212s](uploads/ffe2570f8caf6fae8955deb353a0dc0c/phd101212s.gif)

[“Piled Higher and Deeper”](http://phdcomics.com/comics/archive.php?comicid=1531) by Jorge Cham, [http://www.phdcomics.com](http://www.phdcomics.com)

Version control can become a bit complicated -especially when working in collaboration with others- so **we will start from the basics!**

# Where are you now?

You are now in **Github**. In order for you to follow the material presented in this repository, we will assume you are working within a **new repository** in your Github account.

_____________________________________________________________
### Parenthesis

Depending on your work, you might also have to *clone* an existing *project* from another group/user (which we will cover in [Using Git for the First Time section](Using-Git-for-the-First-Time)).
____________________________________________________________

# Local versus Remote repository

When doing version control with Git and using a Github repository,  you will be working *locally* on your code files in your device (in directories of your work laptop/station). And you will have this *local* (Git) repository "synchronized" with the *remote* **Project Y** repository (in your Github).

To do version control with Git on your *local* files (and "synchronize" it with **Project Y**), you will need to **install Git** in your device (your work laptop/station) and initialize a (*local*) repository, that will be "linked" to **Project Y**.

If you work alone, in principle you do not *need to* have a *remote* repository at all. Using Git *locally* on your device can suffice to keep track of changes. However, a good practice when working with code -and especially in research- is to also have a *remote* repository so that (not mentioned according to relevance):

1) the code is not only lying in a single device (which increases the chances of being lost and especially *forgotten*); 

2) you can easily **collaborate** with others and **publish/archive** the code once it is finalized (or once a version of it is finalized).

In other words, keeping things online (i.e., in the *remote* **Project Y** in Github) allows others to access those projects and make your work **larger and greater**!


## First things first: let's install Git

* [Installing Git on Windows](Install-Git-on-Windows)
* [Installing Git on Linux](Install-Git-on-Linux)
* [Installing Git on MacOS](Install-Git-on-MacOS)


________________________

[Previous : 02 - Typing Bash Commands](https://github.com/HeatherAn/recommended-coding-practices/blob/main/02-Typing-Bash-Commands.md)  
[Next : 04 - Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Setting-Up-Git.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)