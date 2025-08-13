# Bash Cheatsheet

`pwd`: prints the working directory (i.e. the directory you are in).

`cd /`: *takes* you to the **root directory**.

`cd path_dir` : *takes* you from your *current directory* (the directory you are in) to the `path_dir` directory. Consider:
    The **relative path** of a directory/file specifies a **location starting from the *current* location**.  
    The **absolute path** of a directory/file specifies a **location from the *root directory* of the file system** (from `/`).

`cd`: *takes* you to your **home directory**.

`cd ..` : *takes* you to the **parent directory** of the *current directory*.

`cd -` : *takes* you to the previous directory you were in. 

`ls`: lists the contents of the working directory (the directory you are in).

`ls -lSh` : (with a lower case “L” and an upper case "S") lists the same as `ls -l` but with all files and directories sorted by size with the size in human readable format (KB, MB, etc.).

`mkdir name_dir` : make (create) directory called `name_dir`. 

`touch my_file` : creates an empty file in the *current* directory (replace `my_file` with the name of the file you want to create).

`cat my_file.txt` : prints the contents of the `my_file.txt` file to the screen of the terminal (replace `my_file.txt` with the name of the file you want to see). 

`mv file1 dir1` : when first argument is a *file* and second argument is a *directory*, `mv` moves the *file* to that *directory*. You can provide the name of the file (if the file is in the *current* directory) or the path of the file (if the file is in another folder.

`mv file1 file2` : when both arguments are *files*, `mv` renames the first file to the second file (here you should replace `file1` by the name of the file you want to rename, and `file2` by the new name you want to give it). Both `file1` and `file2` can also be given as paths. 

`cp file1 file2` : copies the file given as a first argument to the file given as the second argument (here you should replace `file1` by the name of the file you want to make a copy of, and `file2` by name of the file you want to be the copy of `file1`). Both files can also be given as paths to the respective files.

For copying a directory and all its contents you can use the recursive flag `-r`, e.g. to back up a directory. For example: `cp –r thesis thesis_backup`.

`rm file1` : deletes a file (replace `file1` by the file you want to delete). **Be aware this command deletes the file FOR-E-VER. So be careful!**

`rm –r dir1` : deletes a directory (replace `dir1` by the directory you want to delete). As above: **be careful!**

The asterisks `*` is a wildcard that **matches zero or more characters**. 
    
The `?` is a different wildcard that **matches exactly one character**. For example: let's say *you are* in a given directory, and inside that directory you have 3 files called `data.txt`, `data1.txt` and `data10.txt`. Then `data?.txt` would refer only to `data1.txt`. While `data*.txt` would refer to `data.txt`, `data1.txt` and `data10.txt`.

`find <name_directory> -type f -name "<filename>"`: searches for a file called `<filename>` inside the directory `<name_directory>` (and all its sub-directories).  

`find . -type d`: searches for directories (`-type d`) inside the current directory (`.`) and lists them to the terminal.

`grep "<string>" <filename>`: searches for a string `<string>` in the file called `<filename>`and prints the results to the terminal.

`grep -r "<string>" <name_directory>`: searches for a string `<string>` in all files of the directory `<name_directory>`and prints the results to the terminal.

`unzip <name_zip>`: un-compresses the zip file called `<name_zip>` to the current directory.

`df -h`: prints disk usage to the terminal.

`du -sh`: prints size of the current directory.

`wget <url>`: downloads files from a url.

`echo`: prints the string `<string>` to the terminal.

`export` : sets environment variables.

`history`: prints the history of commands.


## Requires extra installation

`zip -r <name_zip> <name_directory>`: compresses the contents of the directory `<name_directory>` into a zip file called `<name_zip>`.

`tree <name_directory>`: prints the directory tree structure of the directory `<name_directory>` to the terminal (nice layout for the `README.md` of your repo!).

`rsync`:  transfers and syncs files from different locations.