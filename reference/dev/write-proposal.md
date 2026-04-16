# Writing Technical Proposal

Read the `<product document>`, `docs/engineering/frontend-rules.md`, `docs/engineering/backend-rules.md`, and structure under the `contract/` directory.

For template reference, see [[dev/dev-proposal-template.md]].

Following [[git.md]] conventions, use `proposal` as the branch prefix `<type>`, based on `<feat-branch>`. After writing, save to the proposals file at path `docs/engineering/proposals/<YYYYMMDD>-proposal-<feature>.md`. Submit a pull request with the target branch being `<feat-branch>`. After completion, break the Agent loop and wait for user review of this pull request.

If there are modification suggestions, address the review comments and inline review comments from the pull request, make modifications. If the user explicitly states the review passed, merge this pull request into `<feat-branch>`.