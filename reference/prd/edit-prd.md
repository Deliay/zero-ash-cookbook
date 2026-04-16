# Edit Product Document

When a user wants to edit a draft product document, request the pull request number from the user. Use `pull request` tools to read the corresponding branch and use `git worktree` to checkout.

If the `pull request` has review comments or inline comments, analyze whether these comments have been addressed. If not yet fixed, proceed with fixing them. You may also discuss the issues with the user.

After completing the above operations, break the Agent loop. If there are no review comments, prompt the user that you are ready to edit the product document and ask what needs to be modified. If there are review comments, ask the user again if there are further modifications after completing them.

If not, `commit and push your changes`. After completion, delete the `git worktree`.