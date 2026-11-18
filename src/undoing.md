# Undoing Changes

## Pick the right tool

| I want to...                                       | Command                              |
|----------------------------------------------------|--------------------------------------|
| Discard unstaged edits to a file                   | `git restore <file>`                 |
| Unstage a file but keep the edits                  | `git restore --staged <file>`        |
| Fix the last commit's message or content           | `git commit --amend`                 |
| Undo the last commit, keep changes staged          | `git reset --soft HEAD~1`            |
| Undo the last commit, keep changes unstaged        | `git reset HEAD~1`                   |
| Throw away the last commit and its changes         | `git reset --hard HEAD~1`            |
| Undo a commit that is already pushed               | `git revert <commit>`                |
| Delete untracked files                             | `git clean -fd`                      |

## restore: working tree and index

```sh
git restore <file>                    # discard unstaged changes
git restore .                         # discard all unstaged changes
git restore --staged <file>           # unstage
git restore --source=<commit> <file>  # get a file as it was at a commit
git restore -p <file>                 # discard selected hunks only
```

> Older equivalent: `git checkout -- <file>`.

## reset: move the branch pointer

```sh
git reset --soft <commit>    # move HEAD; keep changes staged
git reset --mixed <commit>   # move HEAD; keep changes unstaged (default)
git reset --hard <commit>    # move HEAD; DISCARD all changes
git reset --hard origin/main # make the local branch match the remote exactly
```

| Mode      | Branch moved | Index reset | Working tree reset |
|-----------|:------------:|:-----------:|:------------------:|
| `--soft`  | yes          | no          | no                 |
| `--mixed` | yes          | yes         | no                 |
| `--hard`  | yes          | yes         | **yes**            |

### Squash the last N commits into one

```sh
git reset --soft HEAD~3
git commit -m "One combined commit"
```

## revert: undo safely on shared branches

Creates a new commit that undoes an earlier one, without rewriting history.

```sh
git revert <commit>
git revert <oldest>^..<newest>   # revert a range
git revert -m 1 <merge-commit>   # revert a merge, keeping parent 1
git revert --no-commit <commit>  # stage the revert without committing
```

## clean: remove untracked files

```sh
git clean -n      # dry run: show what would be deleted
git clean -fd     # delete untracked files and directories
git clean -fdx    # also delete ignored files (e.g. build output)
git clean -i      # interactive
```

> **Warning:** `reset --hard` and `clean` destroy uncommitted work, and it
> can't be recovered with the reflog. Stash first if unsure.
