# Inspecting Changes & History

## Diffs

```sh
git diff                        # unstaged changes
git diff --staged               # staged changes (what will be committed)
git diff HEAD                   # all changes since the last commit
git diff <branch1>..<branch2>   # between two branches
git diff main...HEAD            # changes on this branch since it left main
git diff --stat                 # summary of files changed
git diff --name-only            # just the file names
git diff --word-diff            # word-level diff
```

## Log

```sh
git log                                 # full history
git log --oneline                       # one line per commit
git log --oneline --graph --all         # visual branch graph
git log -n 5                            # last 5 commits
git log -p <file>                       # history of a file, with patches
git log --follow <file>                 # follow a file across renames
git log --author="Name"                 # by author
git log --since="2 weeks ago"           # by date
git log --grep="fix"                    # search commit messages
git log -S "functionName"               # commits that added/removed a string
git log main..feature                   # commits on feature that aren't on main
```

### A pretty log format

```sh
git log --graph --date=short --pretty=format:"%C(yellow)%h%Creset %C(cyan)%ad%Creset %s %C(green)(%an)%Creset%C(auto)%d"
```

Save it as an alias, see [Aliases](aliases.md).

## Show a commit

```sh
git show <commit>             # message + diff
git show <commit> --stat      # message + file summary
git show <commit>:<file>      # file contents at that commit
```

## Who changed what

```sh
git blame <file>
git blame -L 10,20 <file>     # only lines 10-20
git blame -w -C <file>        # ignore whitespace, detect moved code
```

## Searching the code

```sh
git grep "TODO"               # search tracked files
git grep -n "TODO" <commit>   # search at a specific commit, with line numbers
```

## Summaries

```sh
git shortlog -sn              # commit count per author
git rev-parse HEAD            # full SHA of the current commit
git rev-parse --short HEAD    # short SHA
git describe --tags           # nearest tag + distance from it
git count-objects -vH         # repository size
```
