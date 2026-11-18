# Setup & Configuration

## Identity

```sh
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Run the same commands without `--global` inside a repository to override them
for that repository only.

## Useful defaults

```sh
git config --global init.defaultBranch main     # new repos start on main
git config --global pull.rebase true            # rebase instead of merge on pull
git config --global fetch.prune true            # drop deleted remote branches on fetch
git config --global push.autoSetupRemote true   # first push sets upstream automatically
git config --global rebase.autoStash true       # stash/unstash around rebases
git config --global core.editor "code --wait"   # use VS Code for commit messages
git config --global merge.conflictstyle zdiff3  # show the base version in conflicts
```

### Line endings

```sh
git config --global core.autocrlf true    # Windows
git config --global core.autocrlf input   # macOS / Linux
```

## Viewing configuration

```sh
git config --list --show-origin   # everything, and which file it came from
git config --get user.email       # a single value
git config --global --edit        # open the global config in your editor
git config --global --unset <key> # remove a setting
```

## Config file locations

| Scope    | Flag         | File                           |
|----------|--------------|--------------------------------|
| System   | `--system`   | `<git install>/etc/gitconfig`  |
| Global   | `--global`   | `~/.gitconfig`                 |
| Local    | `--local`    | `.git/config`                  |
| Worktree | `--worktree` | `.git/config.worktree`         |

## Credentials and SSH

```sh
ssh-keygen -t ed25519 -C "you@example.com"   # create an SSH key
ssh -T git@github.com                        # test GitHub SSH access
gh auth login                                # sign in with the GitHub CLI
git config --global credential.helper manager  # Git Credential Manager (Windows)
```

## Getting help

```sh
git help <command>      # full manual page
git <command> -h        # short usage summary
```
