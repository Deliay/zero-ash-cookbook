# Create Product Document

When creating a new product document, use `ask` and `question` tools to communicate product details with the user through a question-and-answer approach.

When outputting the file, use `git fetch` + `git worktree` to create a new working directory based on the main branch, named `prd/<requirement-slug>`. Place the new product document in `docs/product/draft`, commit and `push`.

If the environment has the `pull request` tool, use it to submit a pull request and display the link. Then delete this `git worktree`. After completing the above operations, request user review and provide the pull request link.