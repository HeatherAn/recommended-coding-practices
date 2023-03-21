# Using Git For The Nth Time

Assuming you have a Github repository (online) and a *local* repository in your device connected to it ([Using Git for the First Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/05-Using-Git-For-The-First-Time.md)), we will now see how to work continuously doing version control.  

Once you come back to work on the files (e.g., the next day or after a break), you **do not** need to initialize the *local* repository again. In rough words: Git will be automatically activated in your device. You just need to go to the directory where the Git repository has been initialized, and start **pulling**, **adding**, **committing** and **pushing**. 

Open the **terminal** on your local work laptop/station, and go to the **main** branch of the Git repository you have already initialized. Use Bash for this with the `cd` command! You can check you are working in the **main** branch by doing:

`git branch --all` : this will list all branches of the repository. We will look into what a branch is in the next section. For now just make sure there is an asterisk next to **main** (`* main`). This means you are currently working in the **main** *local* branch of the repo.   

`git remote –v` : to see what is the current (*remote*) **origin** for that *local* repository. Use this command to make sure your *local* repository is "linked" to the correct *remote* repository. This command is particularly useful when you are moving between different *local* Git repositories, which are connected to different *remote* repositories. You always need to make sure the **origin** is properly defined.

`git fetch origin main` : to get the **remote** changes and metadata (e.g., see whether there are new *commits* in the *remote* repository made by other collaborators). This command **will not merge** the **origin** with the *local* **main** in your work laptop/station. It will only tell you if there are things to update in your *local* **main** branch. This is particularly useful when working with collaborators pushing to the same branch.  

`git pull origin main` : to **pull** the changes from the **origin** to your *local* **main**. In that way Git updates your *local* **main** branch with the changes made to the **remote** repository. Keep in mind: even if you are not collaborating with others on the same file, it is always a good practice to do `git pull origin main` before you start modifying the files *locally*.

`git status` : to show you the *tracked* and *untracked* files; what can be **added** and what can be **committed**.  

You can now work on your files *locally* *adding* and *committing*, and *pushing* all changes to the remote Github repo as explained [previously](https://github.com/HeatherAn/recommended-coding-practices/blob/main/05-Using-Git-For-The-First-Time.md).


# General workflow

The overall workflow should be the following:

- Open the Bash terminal.  
- Go to the directory where the *local* Git repo has been previously initialized (using the `cd` command). Remember that, so far, you only have a single branch: the *local* **main** branch.  
- Ensure the *remote* **origin** is the correct one by doing `git remote –v`. Make sure the https address is the one of your *remote* Github repository.  
- Do `git fetch origin master` to see if there are changes in the **origin** to update your *local* **main** branch.
- **Pull** the *remote* changes (i.e., done to the *online* Github repository) to your *local* repository, in order to update your *local* repo with whichever change that was done *online*. Do this by typing: `git pull origin master`. Remember that your *remote* repository is recognized by your *local* Git as the **origin** and that, so far, your **origin** has a single (also called) **main** branch (recognized by your system as the **origin/main** branch).  
- Start working *locally* on the files again.  
    * **Add** the files you are modifying using `git add` and the respective file name (or `git add --all` to add all files to the **staging area** at once). As a rule of thumb: **add** changes whenever you would (in non-Git world) "Save" a file.  
    * After every relevant change to a file, **commit** it (using `git commit -m "text_commit"` where `"text_commit"` is a short message describing what the change is about). Git then stores the change permanently in the hidden directory `.git/`  
    * Repeat the **adding** and **committing** how many times necessary.  
- Once you have committed all changes and you are ready to update the *online* repository with such changes (e.g., at the end of the working day or after finishing an important task): **push** the changes (using `git push origin main`), so that changes appear in the Github repo.

# Other useful commands

`git log` : shows the project’s history. It will show the *unique identifier* (aka the *hash*) of each **commit** related to that repository (the very large combination of letters and numbers next to "commit"), the *author* (who made each `commit`), the *date* (when each `commit` was made) and the *metadata* of the commit (the message defining what the change is about). Use the `q` to exit the view of the log.  

`git log -N` : shows the last `N` commits.  

`git log --oneline` : shows a summarized version of `git log`. You can also add the `-N` option to see only the latest one-line logs.  

`git remote rm origin` : to delete the **origin** previously defined by  `git remote add origin https_key`. After deleting the **origin**, you can check that the former **origin** has been removed by doing `git remote –v`. You can define the new **remote** by using: `git remote add origin https_key` (with the corresponding `https_key`).

______________________________________
### Important to keep in mind: Git is smart!

You can move within repositories in your *local* work laptop/station and in each one (if you initialized them accordingly) and set the respective **origin** correctly) Git will identify *which* is the respective **origin**. For example, let us say you have:  
- Directory `Dir1` (in your work laptop/station) where Git has been *initialized* and the **origin** has been defined as `Remote1` (that refers to **Remote1 project** in the Github).  
- Directory `Dir2` (in your work laptop/station) where Git has been *initialized* and the **origin** has been defined as `Remote2` (that refers to **Remote2 project** in the Github).
- You go to `Dir1` and make changes to the files there. If you do `git remote -v`, you will see that it recognizes the **origin** as `Remote1`. 
- You can then go to `Dir2` and make changes to the files there. If you do `git remote -v`, you will see that it recognizes the **origin** as `Remote2`. 

_______________________________________

`git diff id_commit1 id_commit2` : where `id_commit1` and `id_commit2` would be the **unique identifiers** of the commits (that can be seen with `git log`). This will show the difference between the two versions of the file (when `id_commit1` was committed and `id_commit2` was committed).

* The `diff` command is a very powerful one. For all information about `git diff` do: `git diff --help` (it opens the help page in a browser).  
* Also check out [this video](https://youtu.be/Wk-IK2uJt28) where the presenter talks about `git diff` and configuring the `diff.tool` global Git configuration variable to visualize the difference between two version using the `vimdiff` tool (by using the `difftool` command). A few remarks about the video:
    * The presenter in this case is working in a Linux system (that is why he uses `man` as a help command) and he is using `vim` as his default editor (see about global Git configuration in [Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/04-Setting-Up-Git.md)).
    * The presenter talks about the `HEAD` variable, which is a pointer to the *most recent commit of the current branch*. Keep in mind that the `HEAD^` that he uses is the same as `HEAD~1`, which indicates *the commit before the last one*. Do you want to see more about how to refer to commits without writing the unique identifier but using `HEAD` instead? It can get a bit confusing! But our dear friend [Stack Overflow](https://stackoverflow.com/) has quite a few discussions on it like [this one](https://stackoverflow.com/questions/2221658/whats-the-difference-between-head-and-head-in-git). 
    * The presenter often talks about the **index**. If you go to the `./git` directory, you will see an `index` file which gets constantly updated. In very rough terms the **index** helps Git "know" what is being **tracked** and what is **not being tracked but has been changed** in a Git repository. That is how Git can give you messages letting you know whenever you have made changes to a file that you have not added nor committed yet. 


`git checkout id_commit file1` : to recover the version of the file (`file1`) recorded with the commit `id_commit`. If you use this by mistake, you can recover the current version of the file by doing: `git checkout HEAD file1` (replacing `file1` by the name of the file you want to recover).

_________________________
### Important to keep in mind: watch out with checkout! 

**Never** do `git checkout HEAD` **WITHOUT SPECIFYING THE FILE**, because Git will restore all files to whichever last version that was committed (losing all changes you have recently made!).

_________________________


#### Interested in more?

See the Gitlab cheatsheet [here](https://about.gitlab.com/images/press/git-cheat-sheet.pdf)

In the next section we will cover **branches**, **merging** and **conflicts**.

________________________

[Previous : 05 - Using Git For The First Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/05-Using-Git-For-The-First-Time.md)  
[Next     : 07 - Using Git with Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Using-Git-With-Branches.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)