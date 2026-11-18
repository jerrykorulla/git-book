# Rebasing

Rebasing replays your commits on top of another base, giving a linear history.

> **Golden rule:** don't rebase commits that other people have already based
> work on. Rebasing your own feature branch is fine.

## Update a feature branch with main

```sh
git fetch origin
git rebase origin/main
```

## Handling conflicts during a rebase

```sh
# fix the files, then
git add <file>
git rebase --continue

git rebase --skip     # drop the commit that conflicts
git rebase --abort    # go back to where you started
```

## Interactive rebase

Rewrite, reorder, squash or drop the last N commits:

```sh
git rebase -i HEAD~5
git rebase -i main          # everything since the branch left main
```

In the editor, change the word in front of each commit:

| Command  | Short | Effect                                      |
|----------|-------|---------------------------------------------|
| `pick`   | `p`   | keep the commit                             |
| `reword` | `r`   | keep, but edit the message                  |
| `edit`   | `e`   | stop so you can amend it                    |
| `squash` | `s`   | combine with the previous commit, merge messages |
| `fixup`  | `f`   | combine with the previous commit, drop this message |
| `drop`   | `d`   | remove the commit                           |

Lines can also be reordered to reorder the commits.

## Autosquash fixups

```sh
git commit --fixup <commit>
git rebase -i --autosquash main
```

Make it the default with `git config --global rebase.autoSquash true`.

## Move a branch onto a different base

```sh
# Take the commits on feature that aren't on old-base, replay them onto new-base
git rebase --onto <new-base> <old-base> feature
```

## Keep merge commits

```sh
git rebase --rebase-merges main
```

## Rebase vs merge

| Use rebase when...                         | Use merge when...                        |
|--------------------------------------------|------------------------------------------|
| Cleaning up your own unpushed commits      | Integrating a shared branch              |
| Updating a feature branch with `main`      | You want to keep the true history        |
| You want a linear history                  | The branch has been pushed and shared    |
