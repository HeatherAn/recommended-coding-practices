# Version Control With Git

**Git** is a sort-of back-end machinery that performs version control of files in local and remote repositories. Services like **Github** and **Gitlab** are web services that host remote Git repositories.

## How does version control work?

Version control systems start with a base version of a file and then **record all changes** made to it with useful metadata (e.g., information about those changes). This helps you to keep track and understand all the **history of changes** made to each tracked file. A version control system not only allows you to *see* those changes, but it also allows you to **retrieve different versions** of each file (e.g., in case you need to recover a previous version of a file). In that sense, Git allows you to keep track of all changes made to a file as a-sort of "hidden information". So that instead of seeing a visible (most likely long) list of files in your working directory (e.g., `file_v1.dat`, `file_v2_final.dat` ... `file_v10_final_FINAL.dat`), you have a single **hidden directory** (the hidden `.git/` directory) where all that information is stored and it is easily retrievable. 

Aside keeping track of file changes (each record of these changes is called a **commit**), a version control system also allows you to merge the changes made by different people or made by yourself in different line of developments (different **branches**).  

___________________

**To keep in mind**: in Gitlab, a repository is also referred to as a **project**.
___________________

![fig_phd-mess](figures/fig_phd-mess.gif)

[“Piled Higher and Deeper”](http://phdcomics.com/comics/archive.php?comicid=1531) by Jorge Cham, [http://www.phdcomics.com](http://www.phdcomics.com)

Version control can become a bit complicated -especially when working in collaboration with others- so **we will start from the basics!**

## Where are you now?

You are now in **Github**. In order for you to follow the material presented in this repository, we will assume you are working within a **new repository** in your Github account. But the same instructions apply when using Gitlab for the remote repository.  


## *Local* versus *Remote* repository

When doing version control with Git and using Github, you will be working *locally* on your code files in your device (in directories of your laptop/workstation). And you will have this *local* (Git) repository "synchronized" with a *remote* repository in your Github account.

To do version control with Git on your *local* files (and "synchronize" it with the *remote*), you will need to **install Git** in your device (your laptop/workstation) and initialize Git in the directory of your project.  

If you work alone, in principle you do not *need* to have a *remote* repository at all. Using Git *locally* on your device can suffice to keep track of changes. However, a good practice when working with code -and especially in research- is to also have a *remote* repository so that (not mentioned according to relevance):  

- you can easily **collaborate** with others and **publish/archive** the code once it is finalized (or once a version of it is finalized); and,  

- the code is not only lying in a single device (which increases the chances of being lost and especially *forgotten*).  

In other words, keeping things online (i.e., in Github) allows others to access those projects, re-use them and contribute to them, making your work more impactful!


## First things first: let's install Git  

* [Installing Git on Windows](https://github.com/HeatherAn/installations-instructions/blob/main/Install-Git-on-Windows.md)
* [Installing Git on Linux](https://github.com/HeatherAn/installations-instructions/blob/main/Install-Git-on-Linux.md)
* [Installing Git on MacOS](https://github.com/HeatherAn/installations-instructions/blob/main/Install-Git-on-MacOS.md)


________________________

[Previous : 05 - Bash Cheatsheet](https://github.com/HeatherAn/recommended-coding-practices/blob/main/05-Bash-Cheatsheet.md)  
[Next : 07 - Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Setting-Up-Git.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)