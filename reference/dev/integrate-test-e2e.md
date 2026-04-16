# Integrated E2E Testing

Search through technical proposals (`<proposal>`) and files in the `contract/` directory to identify all frontend or app projects. Any project with a frontend tech stack and UI code should be covered by e2e tests.

## Branch Management

Use [[git.md]] for branch management. Each integrated E2E test is performed in a new `worktree` created from `<dev-branch>`, with `<type>` set to `e2e`. All development work happens in this new `worktree`.

## Project Path

Tests are uniformly placed under the `tests/e2e/` directory. For browser-based web applications, use the Playwright framework. For other applications, use the e2e testing framework appropriate for that tech stack.

If the project hasn't been created yet, display a selection using the `ask` or `question` tool for the user to choose from.

## Directory Structure

Assuming we have two frontend web projects: `apps/web-a` and `apps/web-b`, the E2E integration test structure would be:
(This structure is illustrative for Node.js frameworks; adjust based on actual tech stack.)

```
tests/e2e/src/web-a/    # Tests for web-a
tests/e2e/src/web-b/    # Tests for web-b
tests/e2e/src/tools/    # Temporary scripts for investigation
tests/e2e/package.json  
```

## Writing E2E Tests

Use the `@general` subagent for writing, with work directory set to the `worktree`. Requirements: load relevant contracts from the `contract/` directory, `proposal` content, and `<product document>`. Cover all possible page scenarios and product acceptance criteria. **Do NOT** write test cases by referencing implementations in `servers/`, as this leads to "shooting arrows at a target you've already drawn."

After writing E2E tests, submit a `pull request` for user review. The `pull request` description should include the test case list. Once review passes, run the E2E tests.

## Running E2E Tests

Use the `@general` subagent to execute tests: use `aspire` (SKILL: aspire and [[infra-orchestrator.md]]) to bring up all services and run tests based on the `tests/e2e` tech stack.

Target backend endpoints can be obtained via `aspire describe <service-slug>`, e.g., `aspire describe web-a` to get the endpoint. It is recommended to inject the endpoint into the test project via environment variables.

## Fixing Issues Found During Testing

If test cases fail or throw errors, use the `@general` subagent to delegate the fix: have it load `docs/engineering` and the corresponding project's `AGENTS.md`, then pass the failing API and `aspire` context to the subagent for fixing. Fix directly in the current test `worktree`.

If E2E tests fail, you may simultaneously schedule multiple subagents for fixes. Once all subagents complete their fixes, verification will be run again.

## Successful Run

If all test cases pass, update the `pull request` with the test cases added/modified this round and any issues discovered and their fixes. Then merge the `pull request` into `<dev-branch>`.