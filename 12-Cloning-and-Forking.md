# Cloning and Forking

This section goes into two important concepts when using Github (the same applies with e.g. Gitlab): *cloning* and *forking*. In very simple words:   

- **Cloning** refers to "downloading" a Github repository to your local device, including its commit history and related metadata. You mainly use *cloning* when you want to re-use the code of that Github repository.   
- **Forking** refers to "having a copy" of a Github repository in your Github account, *synced* with the original repo. So you can keep the "copy" updated with the original repo's latest commits. You mainly use *forking* when you want to collaborate with the original repo.

## Cloning

Let's say you are in `/c/Users/your_user_name/Documents/`, and the Github repository you want to clone in there is called **Project_X**. Once you are in the landing page of the **Project_X**  Github repository, click on the **Code** green button > **Local** tab > **SSH**. Copy the url to clipboard. This is the url address you will give to the `git clone` command: 

```
cd /c/Users/your_user_name/Documents/
git clone ssh_-_key
```

The `ssh_key` will be of the form `git@github.com:<Github_namespace>/Project_X.git`. The **Project_X** repository will be cloned to `/c/Users/your_user_name/Documents/Project_X/`. 

### Keep in mind

- You will be able to see the history of commits (e.g. with `git log --oneline`) up to the point you cloned it. You will not have the commits there may be after that point in time.   
- You can clone any public Github repository.  
- You can clone only private Github repositories to which you have been invited to participate as a **Member**.  
- When cloning a repository with `git clone`, Git defines as **origin** the repository with the `ssh_key` you provided, but you will not be able to **push** changes unless you have the permission to do so.  
 