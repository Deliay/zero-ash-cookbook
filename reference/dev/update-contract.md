# Update Contract

Read the `<product document>`, `docs/engineering/frontend-rules.md`, `docs/engineering/backend-rules.md`, and structure under the `contract/` directory.

Following [[git.md]] conventions, use `contract` as the branch prefix `<type>`. Generate the corresponding contract schema on `<feat-branch>` (found in `proposal`). Commit and, if the `pull request` tool is available, submit a pull request for user approval. At this point, break the Agent loop and wait for user input on whether approval is complete.

If the user explicitly states the review passed, merge this `pull request` into `<feat-branch>`.