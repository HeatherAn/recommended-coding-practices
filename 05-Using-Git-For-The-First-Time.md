# Using Git For The First Time

First make sure you have created repository in Github called **Project_Y**. This will be your *remote* (online) repository.

In Github go to the **Project_Y** repository > **Code** green button > **Local** tab > **HTTPS**. Copy the https key. This is the http address you will give to your *local* Git repository, in order to "link" the *local* with the *remote* repository.

In your device, open the **terminal** (for Windows users: remember to use **Git Bash**) and go to the directory where you want to **clone the online repository**. Do this by using the `cd` command.

Let's say you want to clone the repository in `/c/Users/your_user_name/Documents/`. Then in that directory type:

`git clone https-key dir1` : here **https-key** is the http address of the Github (*remote*) repository, and **dir1** is the local directory where you want to "dump" its contents.
   For example: let's say *you are* in `/c/Users/your_user_name/Documents/`, and the Github repository you want to clone in there is called **Project_Y**. Then to clone the *remote* repository you must type: `git clone https-key .` (where `https-key` is the one you copied from the **Project_Y** Github repository). Here we are using the single dot `.` to tell Git to clone the *remote* repository to the *current* directory (instead of the dot, you could also use for example the **absolute path** `/c/Users/your_user_name/Documents/`). Then the *online* repository will be cloned to `/c/Users/your_user_name/Documents/Project_Y/`.

______________________
### Parenthesis

- When cloning a repository with `git clone`, Git defines as **origin** the repository with the **https_key** you provided. 

- If you want to use a different name for the *local* repository (different from the name of the *remote* repository), then you can do the following:

   * `mkdir dir1` : to create the directory (replace `dir1` by the path of the directory where you want to work in). This directory will be the one where you will *clone* the online repository.

   * `cd dir1` : to go into the directory `dir1`.  

   * `git init` : to initialize a Git repository in `dir1` (a hidden `.git/` directory will be created, which you can see by typing `ls -a`). This will be the so-called *local* **master** branch.  

   * `git branch -M main`: to rename the *local* **master** branch as **main** (see previous [section](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Setting-Up-Git.md#change-master-to-main-in-github-for-now)).

   * `git remote add origin https_key` : this is to tell Git which is the **origin** (*remote*) repository that should be "linked" to the *local* repository created within `dir1`. Replace `https_key` by the corresponding key of the Github online repository.

   * `git pull origin main` : this will "copy" the contents of the (*remote*) **origin** repository to the directory where the (*local*) **main** has been defined.

__________________________
### Parenthesis

- If you want to make sure you have the right **origin**, you can check the **current origin** by typing `git remote –v`. If the **origin** is not the right one, then you can change it with `git remote add origin https_key` as above.

- Keep in mind **origin** is the alias with which your device refers to the *remote* Github repository. In principle you can change this alias, but you are advised not to (especially when learning how to use Git). During this Wiki we will stick to the **origin** and **main** aliases only. 
__________________________

# Start working locally on the files

After **initializing** or **cloning** a repository, you can start working on the files of your *local* **main** branch (which is the only branch you have so far), *pulling*/*pushing* from/to the *remote* repository. 

When you work on files inside the directory where Git has been initialized, you have to tell Git *"hey, keep track of what I am doing to this file"* and *"hey, record the changes made to this file and add this metadata to those changes"*. The first thing is calling **adding** files to Git, and the second thing is making a **commit** of the changes made to the file. 
 
Let’s say you started working on `file1` (e.g., a Python `.py` script) doing all changes in your device (in your *local* Git repository at `~/Documents/Project_Y`). Use:

`git add file1` : this will tell Git to basically "follow" the changes made to this file and put it in the so-called **staging area**. 

Let’s say you created a function on `file1`. Then you have to **commit** such change (so that there is a record that a function has been added to the file). To do this type:

`git commit -m “text_commit1”` : this will tell Git to **record such a change** with the **descriptive metadata** `“text_commit1”`. Replace `“text_commit1”` with a short description of the change made to the file. For example: `git commit –m “Added sum function”`. If you only type `git commit`, the editor you set by default (when installing Git) will open so that you can write the **descriptive metadata** `“text_commit1”`. But always try to keep `“text_commit1”` as short as possible. See the following [blog](https://chris.beams.io/posts/git-commit/) where you can find principles on how to write Git commit messages. Try to set up conventions on how to write them right from the start. It will pay off in the long-term!

## Difference between adding and committing

*Adding* and *committing* might be a bit confusing at first. Think as if you were preparing the clothes you will take for a trip. You first put the clothes on your bed to have an overview of what you will be taking to the trip. In this case, the act of *putting the clothes on the bed* would be `git add`; while the *bed* itself would the so-called `staging area`. 

Once you have *finally decided what to take* on your trip, you *put the clothes on the suitcase*. In this case, *putting the clothes on the suitcase* would be like doing a `git commit`.

___________________________________


While working on a file, and between **adding** and **committing**, you might also find useful the following commands:

`git add --all` : to add all changes made to all files to the **staging area**. For example: 
   - you modify `file1` and `file2`, all within the same *(local)* repository. 
   - Then you do `git add --all` and then `git commit –m “Fixed typos in file1 and file2”`
   - Then you do `git push origin main`. You will then see the changes in the Github *(remote)* repository linked to this *(local)* **main** branch.

`git status` : this will show you the *tracked* and *untracked* files. The “untracked” file(s) message means that there is(are) file(s) in the directory that Git is **not officially keeping track of**.  
   - If you want Git to *officially* track them, then you should **add** the files using `git add file_name`.  
   - If you do not want Git to *officially* track them, you can tell Git to ignore them. You can do this by using `git ignore`. To do this:   
      - create a file in the directory of the project (where Git has been initialized). Call this file: `.gitignore` (it is a hidden file). You can create it via the terminal by typing: `touch .gitignore`    
      - Add in that file the name of each file and/or directory you want Git to ignore. For example, if you want Git to ignore all files with `csv` extension that can be found in the *current* directory, and all files inside a sub-directory called `data`. Then the file `.gitignore` would look like this:
      
      ```
      *.csv  
      data/
      ```  
      - *Add* and *commit* the file `.gitignore` by typing in your terminal:  
      ```
      git add .gitignore
      git commit -m "Ignore all csv files and data sub-folder"
      ```   

`git diff` : shows the changes you have done *locally* (compared to the last version that was **committed**) but you have **not added** to the *staging area*.

`git diff --staged` : shows the changes you have done *locally* (compared to the last version that was **committed**) and that you have **added** to the *staging area*.

## Rule of thumb: when to *add* and when to *commit*?

Every time you make **small changes** to a file, use `git add file1` (where `file1` is the name of the file you have been working in). 

Every time you **finalize an important task**, do a **commit**. Remember **commits** have **descriptive metadata** attached to them. Hence, try to commit significant changes and use **descriptive metadata** that will allow your future self (and that of your colleagues) to understand in a few words what change you did in that **commit**. 

## What about *pushing* to the *remote*?

It depends. If you are working by yourself then every time you **take a break** or **by the end of your working day**, **push all commits** to the respective *online* Gtihub repository (this will "sync" the *online remote* repository with your *local* repository). But if you are collaborating with others on a repository, it may be better to **push** more often. 

### How to push?

Type the following in the **terminal** (in the directory where the *local* repository is):

`git push origin main` : to **push** the changes made *locally* to the *remote* Github repository. Once you have done this, you should be able to see the changes you made *locally* in the remote Github repository. Try it out!


________________________

[Previous : 04 - Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Setting-Up-Git.md)  
[Next : 06 - Using Git for the Nth Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/06-Using-Git-For-The-Nth-Time.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)