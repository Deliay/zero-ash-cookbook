# ZeroAsh Cookbook

模块化 AI Agent 技能库，为 AI 驱动的软件开发提供结构化工作流和最佳实践。

## 核心技能

| 技能 | 用途 |
|------|------|
| [z-product](./z-product/) | 产品文档创建与生命周期管理 (PRD 工作流) |
| [z-project](./z-project/) | 项目创建与管理 (monorepo 支持、技术栈选择) |
| [z-coding](./z-coding/) | 契约式开发工作流 (提案、契约、实现) |
| [z-git](./z-git/) | Git 工作流管理 |
| [z-document](./z-document/) | 文档规范 (Zettelkasten 方法、Mermaid 图表) |
| [z-aspire-orchestrator](./z-aspire-orchestrator/) | 使用 Microsoft Aspire 进行服务编排 |
| [z-test](./z-test/) | API 测试和 E2E 测试工作流 |
| [z-debugging](./z-debugging/) | 调试方法论与故障排除 |

## 开发理念

遵循**契约式开发**流程：

1. 阅读产品文档
2. 创建功能分支
3. 编写技术提案
4. 定义 API 契约 (OpenAPI, GraphQL)
5. 通过 subagent 并行实现代码
6. 编排服务 (Aspire / docker-compose)
7. 覆盖 API 测试 & E2E 测试

## 技术栈

- **编排**: Microsoft Aspire, Docker/Podman
- **测试**: Playwright (E2E)
- **合约**: TypeScript, OpenAPI, GraphQL
- **文档**: Mermaid 图表, Zettelkasten 方法

## 使用方式

各技能模块包含 `SKILL.md` 文件，供 AI agent 在对话中加载使用。

## 目录结构

```
zero-ash-cookbook/
├── z-product/              # 产品生命周期
├── z-project/              # 项目管理
├── z-coding/               # 开发工作流
├── z-git/                  # Git 工作流
├── z-document/             # 文档规范
├── z-aspire-orchestrator/  # 服务编排
├── z-test/                 # 测试工作流
└── z-debugging/            # 调试
```
