# Worktrees

Worktrees let you check out several branches at once, each in its own folder,
sharing one repository. They're handy for reviewing a PR or making a hotfix
without stashing your current work.

```sh
git worktree add ../repo-hotfix hotfix/123        # existing branch
git worktree add -b feature/x ../repo-feature-x   # new branch
git worktree add --detach ../repo-review <commit> # detached, for review

git worktree list
git worktree remove ../repo-hotfix
git worktree prune                                # clean up deleted folders
```

Notes:

- A branch can be checked out in only one worktree at a time.
- Stashes, the reflog and config are shared across worktrees.
- Each worktree has its own working tree and index, so builds don't collide.
