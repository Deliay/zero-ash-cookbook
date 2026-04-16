# Development Workflow

Strictly follow contract-based development, such as `openapi-spec`, `graphql-schema` placed in `contract/`.

## Read Product Document

Before each development, specify a product document. By default, use the `ask` or `question` tool to list the most recent documents from the `docs/product/reviewed` directory for the user to select or input `<product document>`.

## Development Flow

Create requirement branch -> Write technical proposal -> Update Contract -> Create development branch -> Write implementation [1] -> Orchestrate services -> Cover API tests -> Cover E2E tests.

[1] The implementation writing part involves parallel subagent calls.

Create a `todo` for this workflow.

### Load Standards

Before writing code, if context hasn't loaded the `AGENTS.md` in the corresponding directory, load it.

For example: modifying `backend/src/x/y/z/a.ts`, load `backend/AGENTS.md`.

Each time writing code, load `docs/engineering/common-rules.md`.

### Create Requirement Branch

After specifying the product document to develop, create a development branch `<feat-branch>` on the remote. The branch name is `feat/<slug>`, where `<slug>` is extracted from the product document content.

### Write Technical Proposal

USE FOR: write proposals, update proposals
REFERENCE: [[dev/dev-proposal-template.md]]

### Update Contract

USE FOR: write contract, update contract
REFERENCE: [[dev/update-contract.md]]

### Write Implementation

USE FOR: implements, write code, implement
REFERENCE: [[dev/write-implementation.md]]

### Orchestrate Services

USE FOR: service orchestration, update infra, infrastructure, aspire, run services, start services, docker, compose
REFERENCE: [[dev/infra-orchestrator.md]]

## Write Integrated API Tests

USE FOR: integrate test for api service, api test
REFERENCE: [[dev/integrate-test-api.md]]

## Write Integrated E2E Tests

USE FOR: integrate test for frontend
REFERENCE: [[dev/integrate-test-e2e.md]]