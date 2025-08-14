



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
