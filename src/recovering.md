# Recovering Lost Work

Almost anything that was ever **committed** can be recovered.

## The reflog

The reflog records every position `HEAD` (and each branch) has pointed to,
including commits from before a reset, rebase or branch deletion.

```sh
git reflog                     # history of HEAD
git reflog show <branch>       # history of a branch
git reflog --date=relative     # with times
```

Example output:

```text
a1b2c3d HEAD@{0}: reset: moving to HEAD~2
9f8e7d6 HEAD@{1}: commit: Add login form
```

### Undo a bad reset or rebase

```sh
git reset --hard HEAD@{1}       # go back one step in the reflog
git reset --hard ORIG_HEAD      # where HEAD was before the last reset/rebase/merge
```

### Restore a deleted branch

```sh
git reflog                       # find the last commit of the branch
git switch -c <branch> <sha>
```

### Recover a single file from an old commit

```sh
git restore --source=<sha> <file>
```

## Find a lost stash or dangling commit

```sh
git fsck --lost-found                 # list dangling commits
git fsck --no-reflog | grep commit    # including dropped stashes
git show <sha>                        # inspect it
git stash apply <sha>                 # re-apply a dropped stash
```

> Reflog entries expire (by default after 90 days, or 30 for unreachable
> commits), so recover sooner rather than later.
