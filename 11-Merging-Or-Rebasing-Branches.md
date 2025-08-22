# Merging Or Rebasing Branches

When working with branches there are two ways to integrate changes from one branch onto another branch: *merging* (`git merge`) or *rebasing* (`git rebase`).  

`git merge name_branch` : combines changes from the branch called `name_branch` into the *current* branch by creating a new merge commit. It preserves the complete commit history, showing all branches and merges done between branches.  

`git rebase name_branch` : it moves or re-applies commits from the branch `name_branch` on the *current* branch. Unlike *merging*, it re-writes the commit history (e.g., it changes the hashes of the commits made in the *current* branch that were not in `name_branch`).  

## Merging (without conflicts) 

Let us say you only have the *local main* branch, and you want to work on a new feature in a `feature_1` branch (e.g. `1` refers to an identifier of a specific feature). Then from the *local main* branch (at the lastest commit) you create a `feature_1` branch by typing:

```
git switch -c feature_1      
```

If you work on the `feature_1` branch **without making any changes in the *local main* branch**, then once you have tested and finalized the feature in `feature_1`, you can go back to the *local main* and merge `feature_1` into the *main* (to have the new feature in the "official version" of the code):

```
git checkout main
git merge feature_1
git log --oneline
```

Since you did not modify the *main* while working on `feature_1`, this merge will happen **without any conflicts**. 

Once the merge has happened, you will see the changes applied in `feature_1` sort-of "copy-pasted" at the tip of the *local main* branch (with the same commit hashes as in `feature_1`). Now you can decide whether to keep the `feature_1` branch or delete it. If you want to delete it, you can do so by typing:

```
git branch -d feature_1
```

## Rebasing (without conflicts) 

In order to exemplify what *rebasing* does, let us say you have to share the "official version" of the code with someone else. The "official version" of the code is in the *remote main* (in Github) "synced" to the *local main*. The "official version" does not have the new feature yet, cause you are still working on it in the *local* branch `feature_1`. Let us say that before sharing the "official version" with your collaborator, you see some typos that are easy to fix in the `README.md`. You work on those typos in the *local main* and push it to the *remote main* (with `git push origin main`). Now in your local Git repo you have the *local main* with the commit of fixing typos in the `README.md`, while you are still making commits in the `feature_1` *local* branch (that are not in the *local main*). You essentially did:   

```
git checkout main
# fix the typos in the README.md
git add README.md
git commit -m "Fix typo in README.md"
git checkout feature_1
# continue working on feature_1
```

In this case you can do a `git rebase` to apply the commits made in the *local main* in the `feature_1` branch. So that you can keep working on the new feature in `feature_1` branch with the `README.md` typos fixed. You will be essentially "applying" the fixing typos commit in the `feature_1` branch. Since the commits made in the *local main* refer to the `README.md` and you are not modifying this file in the `feature_1` branch, you will not have any conflicts:

```
# from feature_1
git rebase main
git log --oneline
```
With `git rebase` you will see that the commit made in the *local main* has been "applied" in the `feature_1` branch. When doing `git log --oneline` it looks as if you had made the changes in the `feature 1` branch all along. Be aware the commit hashes of the commits made in `feature_1` have changed: **rebase changes the hashes of commits**. 

____________________________

### Parenthesis

In the example of [**Merging (without conflicts)**](https://github.com/HeatherAn/recommended-coding-practices/blob/main/11-Merging-Or-Rebasing-Branches.md#merging-without-conflicts), doing `git rebase feature_1` instead of `git merge feature_1` results in the same history because the hashes of the commits of `feature_1` do not change, and there were no new commits in the *local main*.   
____________________________

## Merging or rebasing with conflicts

Let us say that while working on the new feature in `feature_1` you change the same file in the *local main*. This will create a **conflict** when trying to *merge* or *rebase* the branches.

**Conflicts** arise when:  
- you modify the same file in the same lines in different branches, or   
- when you delete a file in one branch but not in the other one. 

Let us exemplify a conflict with a *merge*, modifying the same file `script1.py` in the same line (line 1) in both branches (the *local main* and  `feature_1`): 

```
# edit script1.py in line 1
git add script1.py
git commit -m "Edit script1.py"
git log --oneline
git checkout feature_1
# edit script1.py in line 1
git add script1.py
git commit -m "Edit script1.py"
git checkout main
git merge feature_1
```

When doing `git merge feature_1` the following conflict message will show up in the terminal: 

```
Auto-merging script1.py
CONFLICT (content): Merge conflict in script1.py
Automatic merge failed; fix conflicts and then commit the result
```

Now you have to open the `script1.py`. You will see the conflicting lines enclosed between `<<<<<<< HEAD` and `>>>>>>> feature_1` strings,  separated by a `=======` string. Erase those strings and edit the file to save the change you want to keep:

```
# edit script1.py to solve the conflict
git add script1.py
git commit -m "Merge branch feature_1"
git log --oneline
```

The conflict is solved, and the merge is closed with a commit. You can now choose whether to keep the `feature_1` branch or delete it (with `git branch -d feature_1`).  

______________________

[Previous : 10 - Using Git With Branches](https://github.com/HeatherAn/recommended-coding-practices/blob/main/10-Using-Git-With-Branches.md)  
[Next : 12 - Cloning and Forking](https://github.com/HeatherAn/recommended-coding-practices/blob/main/12-Cloning-and-Forking.md)  

[Go back to README](https://github.com/HeatherAn/recommended-coding-practices#readme)