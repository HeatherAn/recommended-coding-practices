# Cloning and Forking

This section goes into two important concepts when using Github (the same applies with e.g. Gitlab): *cloning* and *forking*. In very simple words:   

- **Cloning** refers to "downloading" a Github repository to your local device, including its commit history and related metadata. You mainly use *cloning* when you want to re-use the code of that Github repository.   
- **Forking** refers to "having a copy" of a Github repository in your Github account, *synced* with the original repo. So you can keep the "copy" updated with the original repo's latest commits. You mainly use *forking* when you want to collaborate with the original repo.

## Cloning

Let's say you are in `/c/Users/your_user_name/Documents/`, and the Github repository you want to clone in there is called **Project_X**. Once you are in the landing page of the **Project_X**  Github repository, click on the **Code** green button > **Local** tab > **SSH**. Copy the url to clipboard. This is the url address you will give to the `git clone` command: 

```
cd /c/Users/your_user_name/Documents/
git clone ssh_key
```

The `ssh_key` will be of the form `git@github.com:<your_Github_user_name>/Project_X.git`. The **Project_X** repository will be cloned to `/c/Users/your_user_name/Documents/Project_X/`. 

### Keep in mind

- You will be able to see the history of commits (e.g. with `git log --oneline`) up to the point you cloned it. You will not have the commits there may be after that point in time.   
- You can clone any public Github repository.  
- You can clone only private Github repositories to which you have been invited to participate as a **Member**.  
- When cloning a repository with `git clone`, Git defines as **origin** the repository with the `ssh_key` you provided, but you will not be able to **push** changes to that *remote* unless you have the permission to do so.  

## Forking 

Whenever you would like to contribute to an existing Github repository, usually authors will ask you to **create an issue first**; then **fork** their repo; work on whatever you want to contribute; and do a **pull request**. The authors can then review your contribution and see whether they want to integrate it into their repo or not. This is usually the process in which you would use the **forks**. In this section we will exemplify how to use forks within this scenario. But of course, **always check first the contribution guidelines of the repository**. 

### Create an issue first

The first thing to do is to create an issue to explain the authors of the Github repo what you want to work on to contribute to their project. For this, go to the Github repository you are interested in contributing to > go to **Issues** in the top menu of the repository > click on the green **New issue** button. Specify there a title and a description of what you would like to do. 

Keep in mind some repos may ask you to follow a given numbering for the issue title, or a title naming convention, etc. Some repositories may also have issue templates asking for more specifications on what you want to do.  

### Fork the repository

In order to fork the repository go to the Github repository's landing page and click on the **Fork** button in the top right part of the page. This will take you to a **Create a new fork** page. As mentioned in there, a **fork** is a copy of a repository that can be easily synced to stay updated with its latest commits, allowing you to experiment with it without affecting the original repository.  

Create the fork in e.g. your namespace (so that its url will start with: `https://github.com/<your_Github_user_name>`). Regarding the **Repository name**, just go for the suggested name Github displays. Click on the green **Create fork** button and the fork will be created. 

### Work on your contribution

The recommended practice is always to first **clone** the fork repo to your local device, create a branch and work within that branch. 

So first go to the fork repo that is in `https://github.com/<your_Github_user_name>/<name_repository>`, where `<name_repository>` is the name you specified in **Repository name** when creating the for (which is usually the same name as the original repository). Click on the green **Code** button and copy the ssh url to clipboard. Then in your local device in e.g. `/c/Users/your_user_name/Documents/` clone it:

```
cd /c/Users/your_user_name/Documents/
git clone ssh_key
cd name_project
```

Where `ssh_key` is the url copied to clipboard (of the form `git@github.com:<your_Github_username>/<name_project>.git`), and `name_project` is the name of the directory that is created (same name as the Github repo you created the fork of).  

Now inside the cloned repo, inspect the history first, its branches, ensure the **origin** is well-defined, and create a branch e.g. called `feature_X` starting from the *local main* at the latest commit:  

```
git status
git log --oneline
git branch --all
git remote -v
git switch -c feature_X
# start working on the files adding and committing to feature_X
```

Work within `feature_X` adding the files and committing the relevant changes made to them. While doing so, always make sure your *local main* is up to date with whatever changes have been made in the original repo. For this go to your fork repo in Github (`https://github.com/<your_Github_user_name>/<name_repository>.git`). Whenever new commits have been made in the original repo, Github will let you know with a message saying `This branch is N commits behind ...`, where `N` is the number of new commits in the original repo that are not in your fork. In order to keep your fork updated just click on the `Sync fork` button, and **pull** again to your *local* fork repo (in `/c/Users/your_user_name/Documents/name_project/`). You may then need to e.g. do a `git rebase main` in `feature_X` to get those latest updates in your working branch `feature_X`.

Once you have tested and finished your contribution, **push** those changes to your fork repo (the **origin** will be `git@github.com:<your_Github_username>/<name_project>.git`). You will not push to the original repo. You will push to the fork you created in your namespace:

```
git push origin feature_X
```

Keep in mind the *local main* of your (local) fork repo remains intact.

### Do a pull request

Go to your fork repo in Github (`https://github.com/<your_Github_user_name>/<name_repository>.git`) and you will see that Github suggests already to make a **Pull request**. Click on that button and mention in the description that it closes the issue you opened (give an identifier or the title of the issue). Follow the original repo's contribution guidelines to specify who has to review the pull request, or go for the default settings in case the original authors do not specify that information.  

If your pull request is accepted, you will get a notification. It could also be the case the authors/reviewers would like to discuss extra aspects with you via the issue chat. 

______________________

[Previous : 11 - Merging Or Rebasing Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/11-Merging-Or-Rebasing-Branches.md)  
[Next : 13 - Git Cheatsheet](https://github.com/HeatherAn/recommended-coding-practices/blob/main/13-Git-Cheatsheet.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)