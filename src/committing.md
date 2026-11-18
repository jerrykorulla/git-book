# Staging & Committing

## Check what changed

```sh
git status          # full status
git status -sb      # short format with branch info
```

## Stage changes

```sh
git add <file>        # stage a file
git add .             # stage everything under the current directory
git add -A            # stage all changes, including deletions, repo-wide
git add -p            # interactively choose hunks to stage
git add -u            # stage modified and deleted tracked files only
```

During `git add -p`: `y` stage hunk, `n` skip, `s` split into smaller hunks,
`e` edit manually, `q` quit.

## Unstage changes

```sh
git restore --staged <file>    # remove from the index, keep your edits
git restore --staged .         # unstage everything
```

## Commit

```sh
git commit -m "Short summary"
git commit                        # opens your editor for a longer message
git commit -am "Message"          # stage tracked files and commit
git commit --amend                # change the last commit (message and/or content)
git commit --amend --no-edit      # add staged changes to the last commit
git commit --fixup <commit>       # make a fixup commit to squash in later
git commit --allow-empty -m "Trigger CI"
```

> **Tip:** Only amend commits you haven't pushed yet, or be ready to
> force-push (see [Force-pushing safely](remotes.md#force-pushing-safely)).

## Writing good commit messages

```text
Short summary in the imperative, ~50 chars

Optional body wrapped at ~72 chars explaining *why* the change was
made, not just what changed.

Refs: #123
```

## Removing and moving files

```sh
git rm <file>              # delete and stage the deletion
git rm --cached <file>     # stop tracking, keep the file on disk
git mv <old> <new>         # rename or move
```
