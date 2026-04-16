# Git Operation Standards

## Prohibition on Change Base

Rebase / squash operations are **prohibited**. Only merge operations are allowed.

## Branch Reuse Prohibited

Before explicitly marking the current session topic as complete, if the working area is not in a clean state, prompt that the working area is dirty. For example, if the user has developed feature A but hasn't committed, and still has changes for feature A, but now needs to develop feature B, you should break the Agent loop and indicate the working area is dirty.

## Work on Worktrees

After confirming the current work topic and before performing any `write` or `edit` operations, proactively use `git fetch` and `git worktree` to create a new worktree based on the latest main branch. If a target branch is explicitly specified, use that; otherwise, use the repository's default branch (e.g., main/master).

The `worktree` directory is in the `.worktree` folder at the project root. For example, a branch named `prd/add-new-feature-this-is-name` would have its checkout directory at `.worktree/prd/add-new-feature-this-is-name`.

After making some changes, you will commit in the worktree. Changes should be committed as atomic units of work when possible.

After completing work, destroy the corresponding worktree. In the example above, the directory to be removed would be `.worktree/prd/add-new-feature-this-is-name`.

## Branch Naming Convention

Branch name format: `<type>/<slug>`

Where `<type>` can be:
- prd: Product document branch
- feat: Feature development branch
- Other externally specified types

`<slug>` is the branch slug determined from context.

## Pull Request Standards

After merging a pull request, delete both remote and local branches. Note: **Do NOT** delete the target branch.