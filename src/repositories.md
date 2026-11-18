# Creating & Cloning Repositories

## Start a new repository

```sh
git init                    # in the current directory
git init my-project         # in a new directory
```

Then connect it to a remote and push:

```sh
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

With the GitHub CLI you can create the remote and push in one step:

```sh
gh repo create <repo> --public --source=. --push
```

## Clone an existing repository

```sh
git clone https://github.com/<user>/<repo>.git
git clone <url> my-folder                # into a specific folder
git clone --branch <branch> <url>        # check out a specific branch
git clone --depth 1 <url>                # shallow clone (latest commit only)
git clone --filter=blob:none <url>       # partial clone (fetch file contents on demand)
git clone --recurse-submodules <url>     # include submodules
```

## Ignoring files

Create a `.gitignore` at the repository root:

```gitignore
# build output
dist/
*.log
.env
```

```sh
git check-ignore -v <file>       # which rule ignores this file?
git rm --cached <file>           # stop tracking a file that is now ignored
```

For ignore rules that apply only on your machine, use `.git/info/exclude` or a
global ignore file:

```sh
git config --global core.excludesFile ~/.gitignore_global
```

## Submodules

```sh
git submodule add <url> <path>             # add a submodule
git submodule update --init --recursive    # fetch submodules after cloning
git submodule update --remote              # move submodules to their latest commit
```
