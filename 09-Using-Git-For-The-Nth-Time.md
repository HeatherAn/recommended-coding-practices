# Using Git For The Nth Time  

Once you come back to work on the files (e.g., the next day or after a break), you **do not** need to initialize the *local* repository again. In rough words: Git will be automatically activated in your device. You just need to go to the directory where the Git repository has been initialized, and start **pulling**, **adding**, **committing** and **pushing**. 

## General workflow

The overall workflow when working by yourself on a code project should be the following:

- Open the Git Bash terminal.  
- Go to the directory where the *local* Git repo has been previously initialized (using the `cd` command). Remember that, so far, you only have a single branch: the *local* **main** branch.  
- Ensure the *remote* **origin** is the correct one by doing `git remote –v`.  
- **Pull** the *remote* changes (i.e., done to the *online* Github repository) to your *local* repository, in order to update your *local* repo with whichever change done *online*. Do this by typing: `git pull origin main` to pull the changes from the *remote main* branch to the *local main* branch.  Remember that your *remote* repository is recognized by your *local* Git as the **origin** and that, so far, your **origin** has a single (also called) **main** branch (recognized by your system as the **origin/main** branch).  
- Start working *locally* on the files again: work on one file at a time (*adding* and making commits concerning a single file).  
    * **Add** the file you are modifying using `git add` and the respective file name.  
    * After every relevant change, **commit** it using `git commit -m "commit_message"` where `"commit_message"` is a short message describing what the change is about. Git then stores the change permanently in the hidden directory `.git/`  
    * After committing, **push** the commit to the *remote main* branch doing `git push origin main`. 
    * Repeat the **adding** and **committing** how many times necessary. See [this diagram](https://github.com/HeatherAn/recommended-coding-practices/blob/main/figures/fig_git-undo.jpg) in case you need to un-stage changes and/or un-do commits.    

If you are developing the code in collaboration with others, you will need to *pull* and *push* more often and pay attention to which branches you have to commit to. See more in [Using Git With Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/10-Using-Git-With-Branches.md) section. 


## Other useful commands 

`git remote rm origin` : to delete the **origin** previously defined by `git remote add origin ssh_url`. After deleting the **origin**, you can check that the former **origin** has been removed by doing `git remote –v`. You can define the new **remote** by using: `git remote add origin ssh_url` (with the corresponding `ssh_url` obtained from the Github; see [Using Git For The First Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/08-Using-Git-For-The-First-Time.md#define-the-github-repository-as-the-remote) section). 

_____________________________

### Important to keep in mind: Git is smart!

You can move within repositories in your *local* work laptop/station and in each one (if you initialized them accordingly and set the respective **origin** correctly) Git will identify *which* is the respective **origin**. For example, let us say you have:   

- Directory `dir1` (in your work laptop/station) where Git has been *initialized* and the **origin** has been defined as `remote1` (that refers to **Remote1** repository in the Github).  
- Directory `dir2` (in your work laptop/station) where Git has been *initialized* and the **origin** has been defined as `remote2` (that refers to  **Remote2** repository in the Github).  
- You go to `dir1` and do `git remote -v`, you will see that it recognizes the **origin** as `remote1`.  
- If you then go to `dir2` and do `git remote -v`, you will see that it recognizes the **origin** as `remote2`.   
_____________________________

`git diff id_commit1 id_commit2` : where `id_commit1` and `id_commit2` would be the **unique identifiers** of the commits (that can be seen with `git log`). This will show the difference between the two versions of the file (when `id_commit1` was committed and `id_commit2` was committed).  

- The `diff` command is a very powerful one. For all information about `git diff` do: `git diff --help` (it opens the help page in a browser).    
- Check out [this video](https://youtu.be/Wk-IK2uJt28) where the presenter talks about `git diff` and configuring the `diff.tool` global Git configuration variable to visualize the difference between two version using the `vimdiff` tool (by using the `difftool` command). A few remarks about the video:
    * The presenter in this case is working in a Linux system (that is why he uses `man` as a help command) and he is using `vim` as his default editor (see about global Git configuration in [Setting up Git](https://github.com/HeatherAn/recommended-coding-practices/blob/main/07-Setting-Up-Git.md) section).  
    * The presenter often talks about the **index**. If you go to the `./git` directory, you will see an `index` file which gets constantly updated. In very rough terms, the **index** helps Git "know" what is being **tracked** and what is **not being tracked but has been changed** in a Git repository. That is how Git can give you messages letting you know whenever you have made changes to a file that you have not added nor committed yet.  
    * Keep in mind software like **VSCode** have also ways to visualize the `git diff` output, highlighting the differences between versions.  

`git checkout commit_id file1` : to recover the version of the file (`file1`) recorded with the commit `commit_id`. If you use this by mistake, you can recover the current version of the file by doing: `git checkout HEAD file1` (replacing `file1` by the name of the file you want to recover).

_________________________ 

### Important to keep in mind: watch out with checkout! 

**Never** do `git checkout HEAD` **WITHOUT SPECIFYING THE FILE**, because Git will restore all files to whichever last version that was committed (losing all changes you have recently made!).

_________________________


#### Interested in more?

See a Git cheatsheet [here](https://github.com/HeatherAn/recommended-coding-practices/blob/main/13-Git-Cheatsheet.md)

________________________

[Previous : 08 - Using Git For The First Time](https://github.com/HeatherAn/recommended-coding-practices/blob/main/08-Using-Git-For-The-First-Time.md)  
[Next     : 10 - Using Git with Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/10-Using-Git-With-Branches.md)

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)