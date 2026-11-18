# Cheat Sheet

## Daily workflow

```sh
git switch main && git pull              # start from an up-to-date main
git switch -c feature/my-change          # new branch
# ...edit...
git status -sb
git add -p                               # review and stage
git commit -m "Describe the change"
git fetch && git rebase origin/main      # stay current
git push -u origin HEAD                  # publish the branch
gh pr create --fill                      # open a pull request
```

## Everyday commands

| Task                         | Command                                 |
|------------------------------|-----------------------------------------|
| Status                       | `git status -sb`                        |
| Stage all                    | `git add -A`                            |
| Stage interactively          | `git add -p`                            |
| Commit                       | `git commit -m "msg"`                   |
| Amend last commit            | `git commit --amend --no-edit`          |
| Graph log                    | `git log --oneline --graph --all`       |
| Staged diff                  | `git diff --staged`                     |
| New branch                   | `git switch -c <branch>`                |
| Previous branch              | `git switch -`                          |
| Delete branch                | `git branch -d <branch>`                |
| Merge                        | `git merge <branch>`                    |
| Rebase on main               | `git rebase origin/main`                |
| Squash last N commits        | `git rebase -i HEAD~N`                  |
| Fetch and prune              | `git fetch --prune`                     |
| Pull with rebase             | `git pull --rebase`                     |
| First push                   | `git push -u origin <branch>`           |
| Safe force-push              | `git push --force-with-lease`           |
| Stash (incl. untracked)      | `git stash -u`                          |
| Restore stash                | `git stash pop`                         |

## Undo

| Task                                  | Command                         |
|---------------------------------------|---------------------------------|
| Discard file edits                    | `git restore <file>`            |
| Unstage file                          | `git restore --staged <file>`   |
| Undo last commit, keep changes        | `git reset --soft HEAD~1`       |
| Throw away last commit                | `git reset --hard HEAD~1`       |
| Undo a pushed commit                  | `git revert <commit>`           |
| Match the remote exactly              | `git reset --hard origin/main`  |
| Remove untracked files                | `git clean -fd`                 |
| Undo a bad reset or rebase            | `git reset --hard ORIG_HEAD`    |
| Find lost commits                     | `git reflog`                    |

## Tags

| Task                 | Command                                 |
|----------------------|-----------------------------------------|
| Annotated tag        | `git tag -a v1.0.0 -m "msg"`            |
| Push tags            | `git push --follow-tags`                |
| Delete remote tag    | `git push origin --delete v1.0.0`       |
| Latest tag           | `git describe --tags --abbrev=0`        |
