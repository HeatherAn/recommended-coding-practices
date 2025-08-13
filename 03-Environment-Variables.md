# Environment Variables

*Environment variables* are variables whose values are related to a given environment. By typing the following in the terminal:

```
    env
```

the terminal will show you all *environment variables* you have defined in your session as a user. You will see quite likely a long list of variables which have different values.

In general you can define *environment variables* at **system** and **user** levels. Changing the value of an *environment variable* at **system** level will define it for all users in the device. While changing the value of an *environment variable* at **user** level, defines it only for that specific user.

You can also create new *environment variables* (such as a [PYTHONPATH](https://bic-berkeley.github.io/psych-214-fall-2016/using_pythonpath.html)), whose values are made available to all programs upon launch.

The typical *environment variable* you will have to deal with at some point in your coding life is the **PATH**. 


# PATH

When you type a *command* in the terminal, you are basically telling the Shell to *run an executable* file. The Shell will recognize default executable files that it finds in the so-called **PATH**. The **PATH** *environment variable* is a colon-delimited list of directories that the Shell will consider to search for executable files.

When typing `env` you will be able to see the **PATH**. The visualization might be a bit confusing among the list of all other *environment variables*. Thus if you only want to see the **PATH**, you can use the `echo` command to print it to the screen of the terminal:

```
    echo $PATH
```

You can see the directories the **PATH** is pointing to. As you have noticed we used a `$` when referring to the **PATH** variable. The `$` sign is indeed the prefix that you have to use when referring to a given *environment variable*.

**Important to keep in mind:** If you have two executable files sharing the same name but located in different directories, the Shell will run the file that is in the directory that comes first in the **PATH**.


## Adding directories to the PATH

There are situations where you may want to add other directories to the **PATH**. For example, you may want to have a dedicated directory for your Bash scripts and be able to run them from anywhere in your device. In order to do this, you just need to add the directory where you have the scripts, to the **PATH**. You can do this by using commands via the terminal, or by modifying directly the files where the environment variables are defined.

Let’s say you have a directory called `bin` located in your home directory in which you keep your Bash scripts. To add the directory to your **PATH** type :

```
    export PATH="$HOME/bin:$PATH"
```

The `export` command will *export* the modified variable to the Shell process environments. Keep in mind that using that syntax in your terminal will only temporarily change the **PATH** (i.e., it will only be valid in the *current* Shell session; once you close the terminal, the change will not be valid anymore). To make the change permanent, you need to add the export instruction in a file that the Shell executes every time it starts. For Bash, this is the `.bashrc` file found in your home directory. Thus, you need to modify the `~/.bashrc` file. You can do this by opening the file with your preferred editor and then adding the following line `export PATH="$HOME/bin:$PATH"` at the end of it. Or you can do it with `echo` command (see the [Typing Bash Commands section](https://gitlab.tudelft.nl/ascm/start-here/-/wikis/Typing-Bash-Commands#the-echo-command)):

```
    echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
    cat ~/.bashrc
```

Be aware you have to use **`>>`** to concatenate the string at the end of the current version of the `~/.bashrc` file.

After adding the `export` instruction, we have to integrate such a change by using the `source` command:

```
    source ~/.bashrc
```

Then Bash will know the **PATH** has been modified to a new value.

__________________________________________

### Parenthesis:

- In general use `export variable_name=value` syntax to set any *environment variable* (replace `variable_name`) to a given *value* (replace `value`).
- In Linux/macOS systems instead of using a `.bashrc` file, you may see a `.bash_profile` or `.profile` in your home directory. These are also user-level files where you can set up *environment variables* (e.g., change the **PATH**).
 
__________________________________________

### Defining the **PATH** at **system** level

Before we saw how to define the **PATH** at **user** level. You can also checkout the **PATH** and modify it at **system** level.


In **Windows** distributions:  

- Go to **Edit the system environment variables** in the main menu (Control Panel). The system will ask you for your admin username and password. If you are using a TU Delft laptop the password is the one corresponding to the username `.\localadmin`. A **System Properties** windows will pop-up.  
- Click on the **Environment Variables...** button. 
- Under **System variables** find the row that says "Path", select it and click **Edit**. This will open an **Edit environment variable** window. 
- Click "New" and type the new path you want to add. Be aware you have to write it with `\`. After writing it, click **OK**. 
- Recommendation: restart the system to ensure the new **PATH** is taken into account. 


In **Linux/macOS** distributions:

- When you start a new session, system-level *environment variables* are read from the **global** Shell-specific configuration files. These files are usually in the `/etc` folder (e.g., `/etc/profile`). Use any of these files to add a directory to the **PATH** by using the `export instruction`.

___________________________

