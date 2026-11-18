# Cherry-pick, Bisect & Friends

## Cherry-pick

Copy one or more commits onto the current branch.

```sh
git cherry-pick <commit>
git cherry-pick <a> <b> <c>          # several commits
git cherry-pick <oldest>^..<newest>  # a range (inclusive)
git cherry-pick -x <commit>          # note the original SHA in the message
git cherry-pick --no-commit <commit> # apply changes without committing

git cherry-pick --continue           # after resolving conflicts
git cherry-pick --abort
```

## Bisect: find the commit that introduced a bug

```sh
git bisect start
git bisect bad                 # current commit is broken
git bisect good v1.2.0         # this one was fine
# git checks out a commit halfway; test it, then:
git bisect good                # or: git bisect bad
# ...repeat until git names the first bad commit
git bisect reset               # return to where you started
```

Automate it with a script that exits `0` for good and non-zero for bad:

```sh
git bisect start HEAD v1.2.0
git bisect run npm test
```

## Patches

```sh
git format-patch -3                    # last 3 commits as .patch files
git format-patch main --stdout > my.patch
git apply my.patch                     # apply changes without committing
git am < my.patch                      # apply as commits (keeps author/message)
git diff > changes.diff                # quick uncommitted patch
```

## Archive

```sh
git archive --format=zip HEAD -o project.zip
git archive --format=tar.gz --prefix=project/ v1.0.0 -o project-1.0.0.tar.gz
```

## Sparse checkout (large monorepos)

```sh
git clone --filter=blob:none --sparse <url>
git sparse-checkout set src/my-service docs
git sparse-checkout disable
```

## Maintenance

```sh
git gc                    # pack and clean up the repository
git maintenance start     # schedule background maintenance
git fsck                  # check repository integrity
```
