# Integrated API Testing

Search through technical proposals (`<proposal>`) and files in the `contract/` directory to identify all possible APIs across services, whether they are openapi-spec, GraphQL, or WebSocket. Any remote RPC interface should be covered by unit tests.

## Branch Management

Use [[git.md]] for branch management. Each integrated API test is performed in a new `worktree` created from `<dev-branch>`, with `<type>` set to `test`. All development work happens in this new `worktree`.

## Project Path

Tests are uniformly placed under the `tests/api/` directory. The tech stack should match the testing framework used by most backend services (find relevant documentation in the `docs/engineering` directory).

If the project hasn't been created yet, display a selection using the `ask` or `question` tool for the user to choose from.

Once created, document it in `tests/api/AGENTS.md`.

## Directory Structure

Assuming we have two backend API projects: `servers/api-a` and `servers/api-b`, the API integration test structure would be:
(This structure is illustrative for Node.js frameworks; adjust based on actual tech stack.)

```
tests/api/src/api-a
tests/api/src/api-b
tests/api/package.json
```

## Writing API Tests

Use the `@general` subagent to write tests in the `worktree`. Requirements: load relevant contracts from the `contract/` directory and `proposal` content, covering all possible cases. **Do NOT** write test cases by referencing implementations in `servers/`, as this leads to "shooting arrows at a target you've already drawn."

After writing API tests, submit a `pull request` for user review. The `pull request` description should include the test case list. Once review passes, run the API tests.

## Running API Tests

Use the `@general` subagent to run tests: use `aspire` (SKILL: aspire and [[infra-orchestrator.md]]) to bring up all services and run tests based on the `tests/api` tech stack.

Target backend endpoints can be obtained via `aspire describe <service-slug>`, e.g., `aspire describe api-a` to get the endpoint. It is recommended to inject the endpoint into the test project via environment variables.

## Fixing Issues Found During Testing

If test cases fail or throw errors, use the `@general` subagent to delegate the fix: have it load `docs/engineering` and the corresponding project's `AGENTS.md`, then pass the failing API and `aspire` context to the subagent for fixing. Fix directly in the current test `worktree`.

If multiple project API tests fail, you may simultaneously schedule multiple subagents for fixes. Once all subagents complete their fixes, verification will be run again for these APIs.

## Successful Run

If all test cases pass, update the `pull request` with the test cases added/modified this round and any issues discovered and their fixes. Then merge the `pull request` into `<dev-branch>`.