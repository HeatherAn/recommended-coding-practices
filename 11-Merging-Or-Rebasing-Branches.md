# Merging Or Rebasing Branches

When working with branches there are two ways to integrate changes from one branch onto another branch: using `git merge` or `git rebase`.  

## Merging

### Working on a branch without modifying the *main* 

Let us say you only have the *local main* branch, and you want to work on a feature in a `feature_1` branch (e.g. `1` refers to an identifier of a specific feature). Then at `HEAD` from the *local main* branch you create a `feature_1` branch typing:

```
git switch -c feature_1      
```

If you work on the `feature_1` branch without making any changes in the *local main* branch, then once you have tested and finalized the feature in `feature_1` you have to go back to the *local main* and merge `feature_1`:

```
git checkout main
git merge feature_1
```

Since you did not modify the *main* while working on `feature_1`, this merge will happen without any conflicts. 

Once the merge has happened you will see the changes applied in `feature_1` sort-of "copy-pasted" at the tip of the *local main* branch. Now you can decide whether to keep the `feature_1` or delete it. If you want to delete it, you can do so by typing:

```
git branch -d feature_1
```
