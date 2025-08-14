# Bash Cheatsheet

**Relative path** of a directory/file : the location of the directory/file starting from the *current* directory.    

**Absolute path** of a directory/file : the location of the directory/file starting from the *root* directory of the file system.   

Wildcard `*` : this wildcard matches zero or more characters.  
    
Wildcard `?` : this wildcard matches exactly one character.  

`pwd` : prints the *current* directory (i.e. the directory you are in).  

`cd` : takes you to your *home* directory.   
    `cd /` : takes you to the *root* directory.  
    `cd ..` : takes you to the *parent* directory of the *current* directory.  
    `cd -` : takes you to the previous directory you were in.   
    `cd dir1` : takes you from your *current* directory to the `dir1` directory.  

`ls` : lists the contents of the *current* directory.   
    `ls -a` : lists all the files and directories including hidden ones.  
    `ls -lSh` : lists all files and directories of the *current* directory, sorted by size with the size in human readable format (KB, MB, etc.).    

`df -h` : prints disk usage to the terminal.  

`du -sh` : prints size of the *current* directory.  

`mkdir dir1` : make (create) directory called `dir1` (`dir1` can also include the path).   

`touch file1` : creates an empty file in the *current* directory called `file1` (`file1` can also include the path).  

`cat file1` : prints the contents of the (text) file called `file1` to the screen of the terminal (`file1` can also include the path).   

`mv file1 dir1` : when first argument is a *file* and second argument is a *directory*, `mv` moves the *file* to that *directory*. You can provide the name of the file (if the file is in the *current* directory) or the path of the file (if the file is in another directory).  

`mv file1 file2` : when both arguments are *files*, `mv` renames the first file to the second file. Both `file1` and `file2` can also include the respective paths.   

`cp file1 file2` : copies the file given as a first argument (`file1`) to the file given as the second argument (`file2`). Both `file1` and `file2` can also include the respective paths.   

`cp -r dir1 dir2` : copies the contents of the directory given as a first argument (`dir1`) to the directory given as the second argument (`dir2`).  

`rm file1` : deletes the file called `file1`. **Be aware this command deletes the file FOR-E-VER. So be careful!**

`rm –r dir1` : deletes the directory called `dir1`. **Be aware this command deletes the directory FOR-E-VER. So be careful!**

`find dir1 -type f -name "file1"` : searches for a file (`-type f`) called `file1` inside the directory `dir1` (and all its sub-directories). When using `-iname` instead of `-name`, the match is case insensitive.  

`find . -type d` : searches for directories (`-type d`) inside the current directory (`.`) and lists them to the terminal.    

`grep "str1" file1` : searches for a string `str1` in the file called `file1` and prints the results to the terminal.    

`grep -r "str1" dir1` : searches for a string `str1` in all files of the directory `dir1`and prints the results to the terminal.   

`unzip zip1` : un-compresses the zip file called `zip1` to the current directory.   

`echo str1` : prints the string `str1` to the terminal.  

`export var1` : sets the `var1` environment variable.  

`history` : prints the history of commands stored in memory for the current shell session.  


## Requires extra installation

Download the executables first (e.g. `rsync.exe`) from [https://repo.msys2.org/msys/x86_64/](https://repo.msys2.org/msys/x86_64/). If more DLL files are required, download the OpenSSL package from [https://repo.msys2.org/msys/x86_64/libopenssl-3.0.8-1-x86_64.pkg.tar.zst](https://repo.msys2.org/msys/x86_64/libopenssl-3.0.8-1-x86_64.pkg.tar.zst) and copy the required DLLs into the same folder as the executables.   

`zip -r zip1 dir1` : compresses the contents of the directory `dir1` into a zip file called `zip1`.   

`tree dir1` : prints the directory tree structure of the directory `dir1` to the terminal (nice layout for the `README.md` of your repo!).  

`rsync -av dir1 dir2` :  transfers and syncs files from the location `dir1` to location `dir2`. Both locations can be local or over a network.  

`wget url1` : downloads the files from the provided url `url1`.   

________________________

[Previous : 04 - Aliases](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Aliases.md)  
[Next     : 06 - Version control with Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/06-Version-Control-With-Git.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)