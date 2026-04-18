# ZeroAsh 开发技能

一个为 AI Agent 提供项目管理的综合技能，涵盖代码编写、文档撰写、产品实现，采用契约优先的开发方法论。

## 概述

本技能提供以下结构化工作流程：
- **项目创建**：从业务建模到技术栈选型再到项目初始化
- **文档编写**：遵循 Zettelkasten 方法论，使用 Mermaid 图表
- **开发流程**：契约优先的 TDD 开发，清晰的工作流程
- **产品管理**：创建和管理产品文档

## 目录结构

```
├── SKILL.md              # 技能主入口
└── reference/
    ├── create-project.md        # 项目创建流程
    ├── debug-workflow.md        # 调试工作流程
    ├── document-workflow.md     # 文档规范
    ├── development-workflow.md  # 开发工作流程
    ├── git.md                   # Git 规范
    ├── mono-repo-project-structure.md
    ├── product-document-workflow.md
    ├── project-structure.md
    ├── dev/
    │   ├── dev-proposal-template.md
    │   ├── infra-orchestrator.md
    │   ├── integrate-test-api.md    # API 集成测试
    │   ├── integrate-test-e2e.md    # E2E 集成测试
    │   ├── update-contract.md
    │   ├── write-implementation.md
    │   └── write-proposal.md
    └── prd/
        ├── create-prd.md
        ├── edit-prd.md
        ├── product-document-template.md
        └── reviewed-prd.md
```

## 快速开始

### 创建新项目

```
USE FOR: Create Project.
DO NOT USE FOR: The exists project.
REFERENCE: reference/create-project.md
```

### 编写文档

```
USE FOR: write any documents, Update documents.
DO NOT USE FOR: write code, code implementions.
REFERENCE: reference/document-workflow.md
```

### 编写产品文档

```
USE FOR: write product documents, write product solution.
REFERENCE: reference/product-document-workflow.md
```

### 开发

```
USE FOR: write code, implement product, write tech proposal, write tech solution, write implement plan, write tech document.
DO NOT USE FOR: write product documents, write product solution.
REFERENCE: reference/development-workflow.md
```

## 开发流程

```
创建需求分支 → 编写技术方案 → 更新契约 → 创建开发分支 → 编写实现 → 编排服务 → API 测试 → E2E 测试
```

### 核心原则

1. **契约优先开发**：所有契约（OpenAPI 规范、GraphQL schema）放在 `contract/` 目录
2. **基于 Worktree 开发**：每个任务在独立的 git worktree 上工作
3. **Subagent 并行化**：通过 subagent 并行执行实现任务
4. **Zettelkasten 文档**：原子化笔记，使用 `[[文件名]]` 维基链接
5. **Mermaid 图表**：所有图表必须使用 Mermaid 语法（不使用外部图片）

## 文档规范

- 所有文档需包含 YAML front matter，包含 `description` 和 `type`（Fleeting | Literature | Permanent）
- 文件命名：`{ID}-{标题}.md`（如 `01-AIMP-PRD.md`）
- 每个文档建议不超过 7 个双向链接
- 所有图形必须使用 Mermaid 语法

## Git 规范

- **分支命名**：`<type>/<slug>`（如 `feat/add-user-auth`、`prd/new-feature`）
- **Worktree 位置**：`.worktree/<分支名>`
- **按单元任务提交**：小而专注的提交
- **PR 清理**：合并后删除分支（目标分支除外）

## 技术栈支持

技能支持以下技术栈：
- 前端：React、Vue、Flutter、React Native 等
- 后端：Node.js、Python、Go 等
- 数据库：PostgreSQL、MongoDB、Redis 等
- 编排：使用 Aspire 进行本地开发
