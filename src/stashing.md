# Stashing

Set work-in-progress aside without committing it.

## Save

```sh
git stash                          # stash tracked changes
git stash push -m "wip: login"     # with a message
git stash -u                       # include untracked files
git stash -a                       # include untracked and ignored files
git stash push <file>              # stash specific files only
git stash --staged                 # stash only what is staged
git stash --keep-index             # stash, but leave staged changes in place
```

## List and inspect

```sh
git stash list
git stash show stash@{0}           # summary
git stash show -p stash@{1}        # full diff
```

## Restore

```sh
git stash pop                      # apply the latest stash and drop it
git stash apply                    # apply, but keep it in the list
git stash apply stash@{2}          # a specific stash
git stash branch <branch>          # new branch from a stash (avoids conflicts)
```

## Delete

```sh
git stash drop stash@{0}
git stash clear                    # delete all stashes
```

> On PowerShell, quote stash refs: `git stash show -p 'stash@{1}'`.
