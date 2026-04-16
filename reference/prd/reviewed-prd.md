# Product Document Review Approved

If the user provides a `pull request` number, use the `git worktree` function to checkout the corresponding branch and make modifications in the worktree. If the user does not provide a `pull request` number but provides a `<document name>`, search for this `<document name>` in the `docs/product/draft` directory. If not found, prompt that no unreviewed product document was found and break the Agent execution.

If found, or checked out in the worktree, move the corresponding `<document name>` from `docs/product/draft` to `docs/product/reviewed`.