# Aliases & Handy Config

## Creating aliases

```sh
git config --global alias.st "status -sb"
git config --global alias.co switch
git config --global alias.br "branch -vv"
git config --global alias.cm "commit -m"
git config --global alias.amend "commit --amend --no-edit"
git config --global alias.unstage "restore --staged"
git config --global alias.last "log -1 HEAD --stat"
git config --global alias.pushf "push --force-with-lease"
```

Then `git st`, `git co main`, `git amend` and so on.

## Aliases in ~/.gitconfig

Editing the file directly is often easier (`git config --global --edit`):

```ini
[alias]
    st    = status -sb
    lg    = log --graph --date=short --pretty=format:'%C(yellow)%h%Creset %C(cyan)%ad%Creset %s %C(green)(%an)%Creset%C(auto)%d'
    undo  = reset --soft HEAD~1
    wip   = !git add -A && git commit -m 'WIP'
    gone  = !git fetch -p && git branch -vv | grep ': gone]' | awk '{print $1}'
    aliases = config --get-regexp ^alias\\.
```

Aliases starting with `!` run as shell commands.

## Show the current branch in your prompt

**PowerShell** with [posh-git](https://github.com/dahlbyk/posh-git):

```powershell
Install-Module posh-git -Scope CurrentUser
Add-PoshGitToProfile
```

**Bash** (Git for Windows shows this by default):

```sh
source /usr/share/git/completion/git-prompt.sh
PS1='\w$(__git_ps1 " (%s)")\$ '
```

## Better diffs

```sh
git config --global diff.algorithm histogram
git config --global diff.colorMoved zebra
```

## Sign commits with SSH

```sh
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
```
