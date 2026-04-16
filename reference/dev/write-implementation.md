# Writing Implementation

Read the `<product document>`, structure under the `contract/` directory, and corresponding `proposal` document.

For frontend projects: load `docs/engineering/frontend-rules.md`
For backend projects: load `docs/engineering/backend-rules.md`

Following the project structure, use the `@general` subagent for each `<sub-project>`, delegating development of the `<sub-project>` section in the `proposals` files. Prompt as follows:
```
Read the `<product document>`, structure under the `contract/` directory, and `<proposal>` document. Implement this requirement in `<sub-project>` and cover with unit tests until passing.
```

Update `todo`: add a todo for each sub-project, and mark the todo complete after the subagent finishes execution. Todo items include:

- `<sub-project>` code implementation
- `<sub-project>` unit test coverage
- `<sub-project>` unit test execution
- `<sub-project>` AGENTS.md update - Update AGENTS.md content based on this modification

Example: Assuming the following project structure:
```
servers/api   - Use @general to delegate development of server/api changes in proposals
apps/web      - Use @general to delegate development of apps/web changes in proposals
```

After implementation, submit a pull request from each worktree for user review. Wait for user review to pass before proceeding.

#### Explore Fixed Knowledge Base

If using the `Explore` subagent to understand the project, create or update the subagent's output to the corresponding project's `AGENTS.md`.