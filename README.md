# ZeroAsh Development Skill

A comprehensive skill for AI agents to manage projects, write code, create documentation, and implement products using contract-first development methodology.

## Overview

This skill provides structured workflows for:
- **Project Creation**: From business modeling to tech stack selection to project initialization
- **Document Writing**: Following Zettelkasten methodology with Mermaid diagrams
- **Development**: Contract-first TDD development with clear workflows
- **Product Management**: Create and manage product documents

## Directory Structure

```
├── SKILL.md              # Main skill entry point
└── reference/
    ├── create-project.md        # Project creation workflow
    ├── document-standards.md    # Documentation standards
    ├── development-standards.md # Development workflow
    ├── git.md                   # Git conventions
    ├── mono-repo-project-structure.md
    ├── product-document-standards.md
    ├── project-structure.md
    ├── dev/
    │   ├── dev-proposal-template.md
    │   ├── infra-orchestrator.md
    │   ├── update-contract.md
    │   ├── write-implementation.md
    │   └── write-proposal.md
    └── prd/
        ├── create-prd.md
        ├── edit-prd.md
        ├── product-document-template.md
        └── reviewed-prd.md
```

## Quick Start

### Create a New Project

```
USE FOR: Create Project.
DO NOT USE FOR: The exists project.
REFERENCE: reference/create-project.md
```

### Write Documents

```
USE FOR: write any documents, Update documents.
DO NOT USE FOR: write code, code implementions.
REFERENCE: reference/document-standards.md
```

### Write Product Documents

```
USE FOR: write product documents, write product solution.
REFERENCE: reference/product-document-standards.md
```

### Development

```
USE FOR: write code, implement product, write tech proposal, write tech solution, write implement plan, write tech document.
DO NOT USE FOR: write product documents, write product solution.
REFERENCE: reference/development-standards.md
```

## Development Workflow

```
Create Feature Branch → Write Proposal → Update Contract → Create Dev Branch → Implement → Orchestrate → API Test → E2E Test
```

### Key Principles

1. **Contract-First Development**: All contracts (OpenAPI specs, GraphQL schemas) go in `contract/` directory
2. **Worktree-Based Development**: Each task works on a dedicated git worktree
3. **Subagent Parallelization**: Implementation tasks run in parallel via subagents
4. **Zettelkasten Documentation**: Atomic notes with Wiki-style links `[[filename]]`
5. **Mermaid Diagrams**: All diagrams use Mermaid syntax (no external images)

## Document Standards

- All documents require YAML front matter with `description` and `type` (Fleeting | Literature | Permanent)
- File naming: `{ID}-{title}.md` (e.g., `01-AIMP-PRD.md`)
- Max ~7 bidirectional links per document
- All graphics must use Mermaid syntax

## Git Conventions

- **Branch Naming**: `<type>/<slug>` (e.g., `feat/add-user-auth`, `prd/new-feature`)
- **Worktree Location**: `.worktree/<branch-name>`
- **Commit per Unit Task**: Small, focused commits
- **PR Cleanup**: Delete branches after merge (except target branch)

## Tech Stack

The skill supports:
- Frontend: React, Vue, Flutter, React Native, etc.
- Backend: Node.js, Python, Go, etc.
- Databases: PostgreSQL, MongoDB, Redis, etc.
- Orchestration: Aspire for local development
