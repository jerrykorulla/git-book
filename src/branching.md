# Branching & Merging

## Listing branches

```sh
git branch                 # local branches
git branch -a              # local + remote-tracking branches
git branch -vv             # with upstream and last commit
git branch --merged        # branches already merged into the current one
git branch --no-merged     # branches not merged yet
```

## Creating and switching

```sh
git switch <branch>              # switch to an existing branch
git switch -c <branch>           # create and switch
git switch -c <branch> <commit>  # create from a specific commit or branch
git switch -                     # back to the previous branch
git switch --detach <commit>     # look at an old commit (detached HEAD)
```

> The older equivalents are `git checkout <branch>` and
> `git checkout -b <branch>`.

## Renaming and deleting

```sh
git branch -m <new-name>               # rename the current branch
git branch -m <old> <new>              # rename another branch
git branch -d <branch>                 # delete (only if merged)
git branch -D <branch>                 # force delete
git push origin --delete <branch>      # delete on the remote
```

## Merging

```sh
git merge <branch>             # merge a branch into the current one
git merge --ff-only <branch>   # only fast-forward, fail otherwise
git merge --no-ff <branch>     # always create a merge commit
git merge --squash <branch>    # stage all changes as one, then git commit
git merge --abort              # bail out of a conflicted merge
```

## Resolving conflicts

1. Run `git status` to see the conflicted files.
2. Edit each file and remove the conflict markers:

   ```text
   <<<<<<< HEAD
   your version
   ||||||| base
   original version
   =======
   their version
   >>>>>>> feature
   ```

3. Mark each file as resolved and continue:

   ```sh
   git add <file>
   git merge --continue
   ```

Take one side for a whole file:

```sh
git checkout --ours <file>     # keep the current branch's version
git checkout --theirs <file>   # keep the incoming branch's version
```

Let git remember how you resolved a conflict and reuse the resolution:

```sh
git config --global rerere.enabled true
```
