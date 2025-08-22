# Bash Cheatsheet

**Relative path** of a directory/file : the location of the directory/file starting from the *current* directory.    

**Absolute path** of a directory/file : the location of the directory/file starting from the *root* directory of the file system.   

Wildcard `*` : match zero or more characters.  
    
Wildcard `?` : match exactly one character.  

`pwd` : print the *current* directory (i.e. the directory you are in).  

`cd` : change directory to the *home* directory.    

`cd /` : change directory to the *root* directory.  
    
`cd ..` : change directory to the *parent* directory of the *current* directory.   

`cd -` : change directory to the previous directory you were in.   

`cd dir1` : change directory from your *current* directory to the `dir1` directory.  

`ls` : list the contents of the *current* directory.   

`ls -a` : list all the files and directories including hidden ones.  

`ls -lSh` : list all files and directories of the *current* directory, sorted by size with the size in human readable format (KB, MB, etc.).    

`df -h` : print disk usage to the terminal.  

`du -sh` : print size of the *current* directory.  

`mkdir dir1` : make (create) directory called `dir1` (`dir1` can also include the path).   

`touch file1` : create an empty file in the *current* directory called `file1` (`file1` can also include the path).  

`cat file1` : print the contents of the (text) file called `file1` to the screen of the terminal (`file1` can also include the path).   

`mv file1 dir1` : when first argument is a *file* and second argument is a *directory*, `mv` moves the *file* to that *directory*. You can provide the name of the file (if the file is in the *current* directory) or the path of the file (if the file is in another directory).  

`mv file1 file2` : when both arguments are *files*, `mv` renames the first file to the second file. Both `file1` and `file2` can also include the respective paths.   

`cp file1 file2` : copy the file given as a first argument (`file1`) to the file given as the second argument (`file2`). Both `file1` and `file2` can also include the respective paths.   

`cp -r dir1 dir2` : copy the contents of the directory given as a first argument (`dir1`) to the directory given as the second argument (`dir2`).  

`rm file1` : delete the file called `file1`. **Be aware this command deletes the file FOR-E-VER. So be careful!**

`rm –r dir1` : delete the directory called `dir1`. **Be aware this command deletes the directory FOR-E-VER. So be careful!**

`find dir1 -type f -name "file1"` : search for a file (`-type f`) called `file1` inside the directory `dir1` (and all its sub-directories). When using `-iname` instead of `-name`, the match is case insensitive.  

`find . -type d` : search for directories (`-type d`) inside the current directory (`.`) and list them to the terminal.    

`grep "str1" file1` : search for a string `str1` in the file called `file1` and print the results to the terminal.    

`grep -r "str1" dir1` : search for a string `str1` in all files of the directory `dir1` and print the results to the terminal.   

`unzip zip1` : un-compress the zip file called `zip1` to the current directory.   

`echo str1` : print the string `str1` to the terminal.  

`export var1` : set the `var1` environment variable.  

`history` : print the history of commands stored in memory for the current Shell session.  


## Require extra installation

The following commands require extra installation in Windows. In order to install them: 

- Download the executables first (e.g. `rsync.exe`) from [https://repo.msys2.org/msys/x86_64/](https://repo.msys2.org/msys/x86_64/).   

- If more DLL files are required, download the OpenSSL package (`libopenssl`) from [https://repo.msys2.org/msys/x86_64/](https://repo.msys2.org/msys/x86_64/) and copy the required DLLs into the same folder as the executables.   

`zip -r zip1 dir1` : compress the contents of the directory `dir1` into a zip file called `zip1`.   

`tree dir1` : print the directory tree structure of the directory `dir1` to the terminal (nice layout for the `README.md` of your repo!).  

`rsync -av dir1 dir2` :  transfer and sync files from the location `dir1` to location `dir2`. Both locations can be local or over a network.  

`wget url1` : download the files from the provided url `url1`.   

________________________

Want to check some of the commands in more details? Go to [Typing Bash Commands](https://github.com/HeatherAn/recommended-coding-practices/blob/main/02-Typing-Bash-Commands.md) section.

________________________

[Previous : 04 - Aliases](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Aliases.md)  
[Next     : 06 - Version control with Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/06-Version-Control-With-Git.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)