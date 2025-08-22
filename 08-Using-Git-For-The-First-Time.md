# Using Git For The First Time

## Create a repository in Github

First make sure you have created repository in Github called **Project_Y**. This will be your *remote* (online) repository. 

To create a repository in Github, click on **+** button at the top panel > **New repository**:
   - In **General** specify **Project Y** as the repository name.  
   - In **Configuration** set the visibility to **Private**.  
   - Do not add anything in the repository and just click on the **Create repository** green button.  

## Generate an SSH key pair

Next step is to set up an SSH key pair so that your device can push the history of changes to the remote repository in Github. For this open Git-Bash and from anywhere type:

```
ssh-keygen -t ed25519 -C "your_email"
```

This will ask you where you want to store the public/private SSH key pair. Just press **Enter** to select the defaut suggested location (`/c/Users/your_username/.ssh/id_ed25519`). Two files will be created: `id_ed25519` and `id_ed25519.pub`. The first one has the private part of the key pair. **Do not share this with anyone!** The second file (`id_ed25519.pub`) has the public part of the key pair.

Go to your Github account > top right corner > click on your username > select **Settings** > select **SSH and GPG keys** > click on the **New SSH key** green button. Add a title such as your device's nickname or identifier. In **Key** copy the contents of the `id_ed25519.pub` file. Then click the **Add SSH key** green button.  

## Define the Github repository as the remote

Once you are in the landing page of your **Project_Y** repository, click on the **Code** green button > **Local** tab > **SSH**. Copy the url to clipboard. This is the url address you will give to your *local* Git repository, in order to **Project_Y** as the *remote* repository of your *local* repository. It will be of the form `git@github.com:<your_Github_username>/Project_Y.git`.

In your device, open the **terminal** (for Windows users: remember to use **Git Bash**) and go to the directory where you had initialized Git already: `~/Documents/Project_Z` (see [Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Setting-Up-Git.md) section).

To add the Github **Project_Y** as the *remote* use:

```
git remote add origin git@github.com:<your_Github_username>/Project_Y.git
```
This tells Git which is the *remote* repository that will be referred to as **origin**, and that will be "linked" to the *local* repository at `~/Documents/Project_Z`. 

**Keep in mind**: here we have used different names for the *local* and *remote* repositories for training purposes. In general, and especially when starting to use Git and Github, use the same name for both.

__________________________

### Parenthesis

- If you want to make sure you have the right **origin**, you can check the defined remotes by typing `git remote –v`.  

- Keep in mind **origin** is the alias with which your "local Git" refers to the *remote* Github repository for that *local* repository. In principle, you can change this alias, but you are advised not to (especially when learning how to use Git). During this Wiki we will stick to the **origin** and **main** aliases only.  

__________________________

## Start working locally on the files

Now you can start working on the files of your *local* **main** branch (which is the only branch you have so far), *pulling*/*pushing* from/to the *remote* repository.  

**Recommendation:** do the version control of one file at a time, and one (relevant) change at a time.

When you work on files inside the directory where Git has been initialized, you have to tell Git *"hey, keep track of what I am doing to this file"* and *"hey, record the changes made to this file and add this metadata to those changes"*. The first thing is calling **adding** files to Git, and the second thing is making a **commit** of the changes made to the file.  
 
Let’s say you started working on `file1` (e.g., a Python `.py` script) doing all changes in your device (in your *local* Git repository at `~/Documents/Project_Z`). Use:

```
git add file1
``` 
This will tell Git to basically "follow" the changes made to this file and put it in the so-called **staging area**.   

Let’s say you created a function on `file1`. This change is worth saving as a whole, so that you can always go back to it if needed. In order to *save* it, you have to **commit** it. To do this, type:

```
git commit -m “text_commit1”
```
Where you need to replace `“text_commit1”` with a short description of the change made to the file. For example: `git commit –m “Added sum function”`. This will tell Git to **record such a change** with that **descriptive metadata**.   

If you only type `git commit`, the editor you set by default (when installing/configuring Git) will open so that you can write the **descriptive metadata** `“text_commit1”` in it. But always try to keep `“text_commit1”` as short as possible. See the following [blog](https://chris.beams.io/posts/git-commit/) where you can find principles on how to write Git commit messages. Try to set up conventions on how to write them right from the start. It will pay off in the long-term!

### Difference between adding and committing

*Adding* and *committing* might be a bit confusing at first. Think of them as if you were preparing the clothes for a trip. You first put the clothes on your bed to have an overview of what you will be taking to the trip. In this case, the act of *putting the clothes on the bed* would be `git add`; and the *bed* itself would the so-called `staging area`. 

Once you have *finally decided what to take* for your trip, you *put the clothes on the suitcase*. In this case, *putting the clothes on the suitcase* would be like doing a `git commit`.

### More Git commands  

While working on a file, between **adding** and **committing**, you might also find useful the following commands:   

`git status` : this will show you the *tracked* and *untracked* files. The “untracked” file(s) message means that there is(are) file(s) in the directory that Git is **not officially keeping track of**.  

- If you want Git to *officially* track them, then you should **add** the files using `git add file_name`.   

- If you do not want Git to *officially* track them, you can tell Git to ignore them. You can do this by using `git ignore`. To do this:   

   - create a `.gitignore` file (it is a hidden file) in the top directory of the project, where Git has been initialized. You can create it by typing: `touch .gitignore`   

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
      
   - If you want to see what files or directories are being ignored by Git, use `git status --ignored`  
      
   - If you want Git to ignore all files with a given extension **except one file**, you can use the `!` symbol. For example: let's say you tell Git to ignore all files with `csv` extension except for `register_total.csv`. Then `.gitignore` file should look like this:
   
   ```
   *.csv  
   !register_total.csv
   ```  
      
   Every time you change the `.gitignore` file, do not forget to *add* it and *commit* it.
   
   - A bit of advice on **what kind of files** should be ignored:  
      - log files     
      - files with (API) keys/credentials  
      - files with sensitive information (especially if the project is shared with others)  
      - system files like `Desktop.ini` in Windows, `.DS_Store` on macOS, etc.   
   In [gitignore.io](https://www.toptal.com/developers/gitignore) you can find other type of files that are recommended to be ignored by Git depending on your operating system, IDE or programming language.  
   
   - You can also include comments in `.gitignore` files, in case you want to provide more documentation about the files that are being ignored. The lines (in the `.gitignore` file)  starting with `#` symbol, are considered as *comments*.  
   
   - If for some reason you would like Git to track a file that has already been ignored (i.e., included in the `.gitignore` file), then delete it from the `.gitignore` file, and *add* the file to the **staging area** by using the `f` flag, forcing Git to consider it:  
   
   ```
   git add -f file
   ```  
   Where `file` would be the file that was in `.gitignore` and that you *now* want Git to track.  
   
   - If you want Git to ignore a file that has already been tracked, use `git rm --cached file` (replace `file` by the name of the file) and then *commit* this change. Similarly, if you want Git to ignore an entire directory, use `git rm -r --cached dir` (replace `dir` with the name of the directory) and then commit this change.   

`git diff` : shows the changes you have done *locally* (compared to the last version that was **committed**) but you have **not added** to the *staging area*.

`git diff --staged` : shows the changes you have done *locally* (compared to the last version that was **committed**) and that you have **added** to the *staging area*.

`git log` : shows the project’s history. It will show the *unique identifier* (aka the *hash*) of each **commit** related to that repository (the very large string next to "commit"), the *author* (who made each `commit`), the *date* (when each `commit` was made) and the *metadata* of the commit (the message defining what the change is about). Use the `q` to exit the view of the log.  

`git log -N` : shows the last `N` commits.  

`git log --oneline` : shows a summarized version of `git log`. You can also add the `-N` option to see only the latest one-line logs.  

### Rule of thumb: when to *add* and when to *commit*?

Every time you make **small changes** to a file, use `git add file1` (where `file1` is the name of the file you have been working in). 

Every time you **finalize an important task**, do a **commit**. Remember **commits** have **descriptive metadata** attached to them (the log messages, who made the commit and when). Hence, try to commit significant changes and use **descriptive metadata** that will allow your future self (and that of your colleagues) to understand in a few words what change you did in that **commit**.    

### How to refer to a given commit?

You can refer to a given **commit** by its *unique identifier* (*hash*) or in terms of the `HEAD` variable. `HEAD` is actually a pointer that refers to the *most recent commit of the current branch*. Thus, if you want to refer to the commit before the current one, you can use: `HEAD~1`. If you want to refer to two commits before the current one, then you can use `HEAD~2`, and so on. 

Do you want to see more about how to refer to commits without writing the *hash* but using `HEAD` instead? It can get a bit confusing! But our dear friend [Stack Overflow](https://stackoverflow.com/) has quite a few discussions on it like [this one](https://stackoverflow.com/questions/2221658/whats-the-difference-between-head-and-head-in-git). 

### How can I undo an *adding* or a *commit*?
 
The following diagram shows the commands to undo the *adding* and the *committing*.  

![undo_diagram](uploads/undo_diagram.png)

Keep in mind:  

- `git restore <file>` : when used without any options, it discards the changes made to the file called `<file>`.   
   - When the `--staged` option is used, it un-stages the changes (but changes are not discarded).   

- `git rm --cached <file>` :  it un-stages the changes made to the file `<file>` when the file has been staged for the first time.   

- `git reset <commit_id>` : un-does a commit:   
   - `git reset --soft <commit_id>` : un-does the commit `<commit_id>` but keeps the changes to the file staged.   
   - `git reset --mixed <commit_id>` : un-does the commit `<commit_id>` and un-stages the changes (but changes are not discarded).   
   - `git reset --hard <commit_id>` : un-does the commit `<commit_id>`, un-stages the changes and discards the changes.  

**Recommendation**: especially when starting to use Git, always do a `git status` after every Git command and read its output. It will always tell you what command instructions you can use to undo the latest Git command used. 

## Push to the remote

Start editing your files, *adding* them to the staging area, and *committing* the relevant changes so that you have them in the history of the repository. After making a commit, **push** the commit done in your *local main* branch to the remote *main* branch so that they are synced: 


```
git push origin main
```

In fact, with `git push` you can "send" the changes done in any *local* branch to any *remote* branch (see more in [Using Git With Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/10-Using-Git-With-Branches.md) section).  

If you happen to make commits to the *remote main* directly via Github's user interface (or if you are collaborating with others and they push their local changes to the *remote main*, then you will need to **pull** those changes first, before making any changes *locally*. This you do with:  

```
git pull origin main
```

## When should I *push/pull* to/from the *remote*?

It depends:  

- If you are working by yourself, then every time you **take a break** or **by the end of your working day**, **push all commits** to the respective *online* Github repository.    

- If you are collaborating with others on the same *remote* repository, you need to **push** (and **pull**) more often.   

**As a rule of thumb**:   

- **pull** before starting to work *locally*;   

- **push** after every *local* commit.    


________________________

[Previous : 07 - Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Setting-Up-Git.md)  
[Next : 09 - Using Git for the Nth Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/09-Using-Git-For-The-Nth-Time.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)