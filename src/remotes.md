# Remotes: Fetch, Pull & Push

## Managing remotes

```sh
git remote -v                          # list remotes with URLs
git remote add <remote> <url>          # add a remote
git remote rename <old> <new>
git remote remove <remote>
git remote set-url origin <new-url>    # change a remote's URL
git remote show origin                 # details and tracked branches
```

### Working with a fork

```sh
git remote add upstream https://github.com/<owner>/<repo>.git
git fetch upstream
git rebase upstream/main
```

## Fetch

Download new commits without touching your working tree.

```sh
git fetch                  # from the default remote
git fetch --all            # from all remotes
git fetch --prune          # also remove branches deleted on the remote
```

## Pull

`git pull` is `git fetch` followed by a merge (or rebase) into the current
branch.

```sh
git pull
git pull --rebase          # rebase local commits on top of the remote
git pull --ff-only         # only fast-forward, fail if branches diverged
git pull origin main       # pull a specific branch
```

## Push

```sh
git push                            # push current branch to its upstream
git push -u origin <branch>         # first push: set the upstream
git push origin <local>:<remote>    # push to a branch with a different name
git push --tags                     # push all tags
git push origin --delete <branch>   # delete a remote branch
```

## Force-pushing safely

After a rebase or amend you need to force-push. Prefer `--force-with-lease`,
which refuses to overwrite commits on the remote that you haven't seen:

```sh
git push --force-with-lease
```

## Tracking branches

```sh
git branch -u origin/<branch>           # set upstream for the current branch
git branch -vv                          # show upstreams and ahead/behind
git switch <branch>                     # auto-creates tracking branch from origin/<branch>
git status -sb                          # quick ahead/behind summary
```

## Clean up stale branches

```sh
git fetch --prune
git branch -vv | grep ': gone]'         # local branches whose remote is gone
```
