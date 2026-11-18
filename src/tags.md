# Tags & Releases

## Create tags

```sh
git tag v1.0.0                            # lightweight tag on HEAD
git tag -a v1.0.0 -m "Release 1.0.0"      # annotated tag (recommended)
git tag -a v1.0.0 <commit> -m "..."       # tag an older commit
git tag -s v1.0.0 -m "..."                # signed tag
```

## List and inspect

```sh
git tag                     # list tags
git tag -l "v1.*"           # filter
git tag --sort=-v:refname   # newest version first
git show v1.0.0
git describe --tags --abbrev=0   # latest tag reachable from HEAD
```

## Push tags

```sh
git push origin v1.0.0      # push one tag
git push --tags             # push all tags
git push --follow-tags      # push commits plus their annotated tags
```

## Delete tags

```sh
git tag -d v1.0.0                   # local
git push origin --delete v1.0.0     # remote
```

## Check out a tag

```sh
git switch --detach v1.0.0            # look around
git switch -c hotfix/1.0.1 v1.0.0     # start a branch from it
```

## GitHub releases

```sh
gh release create v1.0.0 --generate-notes
gh release create v1.0.0 ./dist/*.zip --title "v1.0.0" --notes "..."
gh release list
```

## Changes since the last release

```sh
git log $(git describe --tags --abbrev=0)..HEAD --oneline
```
