# Aliases

We mentioned in [Typing Bash commands](https://github.com/HeatherAn/recommended-coding-practices/blob/main/02-Typing-Bash-Commands.md) section that you can also open applications directly from the terminal with a single command. 

By default, in Windows systems, you can use the `start` command to open a file with the default Windows application for it. In macOS and Linux systems you can use the `open` command to open a file with the default applications, or `open -a` to open with an application of choice. 

There are however some applications that you do need to setup the command Bash can use to run them. For this you have to create an **alias** in the Bash profile file `.bashrc` (or `.bash_profile`) that is in your home directory. 

## Example

For example, let us say you want to be able to open the **Microsoft Excel** application via the terminal with a single command named 'excel'. If you just go ahead and type 'excel' you will get the message `bash: excel: command not found`. For Bash to recognize it as a command, you have to define it. 

    - First you need to find where the Excel executable is (`EXCEL.exe`). For this you can use the `find` command (see also [Typing Bash commands](https://github.com/HeatherAn/recommended-coding-practices/blob/main/02-Typing-Bash-Commands.md)):  

    ```
    find /c/ -type f -iname "excel.exe" 2>/dev/null
    ```
    The `-iname` option is to do a case-insensitive match to the name of the file.   
    The `2>/dev/null` option is to skip the permission errors (`permission denied`) since the `/c/` drive has protected directories and we are using Bash with normal (non-admin) user privileges.  

    - The `find` command will print to the terminal the location where the `EXCEL.exe` file is. Let us say the executable is in `/c/Program Files/Microsoft Office/root/Office16/`. Now you need to edit your `~/.bashrc` file to define the alias:  
    ```
    alias excel='"/c/Program Files/Microsoft Office/root/Office16/EXCEL.exe"'
    ```
    - Close the `~/.bashrc` file, and reload it with `source` command:
    ```
    source ~/.bashrc
    ```

Now you can use the 'excel' command to open the application (e.g., `excel file.xlsx`).

________________________

[Previous : 03 - Environment variables](https://github.com/HeatherAn/recommended-coding-practices/blob/main/03-Environment-Variables.md)  
[Next     : 05 - Bash Cheatsheet](https://github.com/HeatherAn/recommended-coding-practices/blob/main/05-Bash-Cheatsheet.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)