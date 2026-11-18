# Git Book

A personal quick reference for the git commands I reach for most often.

Each chapter groups related commands with a short description and a
copy-paste-ready example. Use the **search** button (or press `S`) to jump to
a command quickly, or go straight to the [Cheat Sheet](cheatsheet.md) for a
one-page summary.

## Conventions

| Placeholder  | Meaning                                        |
|--------------|------------------------------------------------|
| `<branch>`   | A branch name, e.g. `feature/login`            |
| `<remote>`   | A remote name, usually `origin`                |
| `<commit>`   | A commit SHA, branch, tag or ref like `HEAD~2` |
| `<file>`     | A path to a file (or a pathspec like `src/`)   |

## Mental model

```text
working tree --git add--> staging area --git commit--> local repo ------git push----> remote
                                                       local repo <--git fetch/pull-- remote
```

- **Working tree**: the files you are editing.
- **Index / staging area**: what will go into the next commit.
- **Local repository**: your commits, branches and tags (`.git/`).
- **Remote**: a shared copy, e.g. on GitHub.

## Referring to commits

| Ref            | Meaning                                       |
|----------------|-----------------------------------------------|
| `HEAD`         | The commit you have checked out               |
| `HEAD~1`, `HEAD~3` | 1 or 3 commits before `HEAD` (first parent) |
| `HEAD^2`       | The second parent of a merge commit           |
| `main@{1}`     | Where `main` pointed one move ago (reflog)    |
| `@{u}`         | The upstream of the current branch            |
| `a1b2c3d`      | A (short) commit SHA                          |

## Working on this book

The book is built with [mdBook](https://rust-lang.github.io/mdBook/). To
preview it locally:

```sh
mdbook serve --open
```

Pushing to `main` rebuilds and publishes the site via GitHub Actions.
