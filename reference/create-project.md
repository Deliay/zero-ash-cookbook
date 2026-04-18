# Create Project

Project creation follows this workflow:
Business Modeling -> Tech Stack Selection -> Create Project Structure -> Development Standards -> Initialize Projects -> Service Orchestration

## Project Service Modeling

Before starting, if the user hasn't briefly introduced the core domain or main business of the project, break the Agent loop and directly ask the user to explain the project's core domain or main business.

## Tech Stack Selection

Based on the user's core domain information, use `ask` or `question` tools to dynamically interact with the user and inquire about tech stack selection. Provide mainstream technology options. If a language is explicitly specified in the prompt, default options are the most commonly used tech stacks for that language.

Ask about tech stacks category by category: frontend, backend, persistence, cache, and other components.

## Project Structure

Before initialization, check if a git repository exists for the initialized project. If not, execute:

```bash
git init
git branch -m main
```

Create project structure directories based on the user's tech stack selection.
REFERENCE: [[project-structure.md]]

## Development Standards

After project initialization, generate unified standards for the relevant tech stacks in the `docs/engineering/` directory, and reference these standards in each project's `AGENTS.md`.

Example reference relationships:
```
docs/engineering/common-rules.md
docs/engineering/frontend-rules.md
docs/engineering/backend-rules.md
```

`common-rules.md` contains: development processes (such as TDD, contract-based development, loading product documents before development, coverage requirements, review requirements, etc.), branch standards, commit standards, etc. Expand detailed content based on the specific tech stack (this section only contains common standards).

`frontend-rules.md` contains: unified frontend standards, initialization instructions, project selection, project structure, component naming, state management selection, bundlers, testing frameworks, contract generators (codegen) in contracts, etc. Unless specially specified, use the selections in this file. Expand detailed content according to the specific tech stack selection.

`backend-rules.md` contains: unified backend standards, initialization instructions, project selection, project structure, testing frameworks, contract generators (codegen) in contracts, etc. Unless specially specified, use the selections in this file. Expand detailed content according to the specific tech stack selection.

## Initialize Each Project

Initialize projects in their respective directories according to the tech stack selection.

Prioritize using the official CLI/scaffolding provided by the tech stack. If unavailable, use the LLM to generate the project.

Note: Be aware if the official scaffolding creates subdirectories. If it does, use the command to create directly in the current directory.
For example:

```bash
# cwd: apps/my-front-end-app

# WRONG! Folder structure becomes apps/my-front-end-app/my-front-end-app
npx create-react-app --template typescript my-front-end-app

# CORRECT, folder structure remains apps/my-front-end-app
npx create-react-app --template typescript .
```

Then install dependencies that were indicated in the prior selection process.

During initialization, do not write any business logic code. Only set up the project structure, dependencies, and basic configuration files.

After initialization, generate a brief tech stack description for the project in its `AGENTS.md`.

Content includes:
```
# <Project Name, e.g., my-front-end-app>
## Tech Stack Description
## Project Module Diagram
## Development Process
## Related Standards Reference
```

After each individual project is initialized, make one commit.

## Service Orchestration

After all projects are initialized, proceed with Service Orchestration in the `infra/` directory.

Project orchestration is performed using `aspire` and its `skill`. REFERENCE: [[dev/infra-orchestrator.md]]

The orchestration phase sets up middleware infrastructure dependencies and configures service-to-service communication, but does not involve business logic implementation.
