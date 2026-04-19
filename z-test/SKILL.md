---
name: z-test
description: 'USE FOR: project manage, create project, read project, development, write code, read code, write documents, update documents, api test, e2e test, implement product, debug, fix issue, troubleshooting. 项目管理，创建项目，读取项目，开发，写代码，读取代码，写文档，写测试，更新测试，实现产品逻辑，写技术方案，解决问题，修BUG'
---

# 测试

你需要为项目编写或新增新的api test和e2e test。

你的测试流程为：确定测试范围 -> 覆盖API test -> 完成API test -> 覆盖e2e test -> 完成e2e test

如果只需要e2e test则为：确定测试范围 -> 覆盖e2e test -> 完成e2e test。
如果只需要API test则为：确定测试范围 -> 覆盖API test -> 完成API test。

## 确定测试范围

如果上下文中有开发流程及其上下文，则测试范围已确定，否则中断agent让用户输入测试范围。

如果上下文已经确定上下文，则读取 `<产品文档>`，`contract/`目录下的结构和<proposal>文档，在`<子项目>`中实现这个需求，并覆盖单元测试直到通过。

## API test

REFERENCE: [[integrate-test-api.md]]

## E2E test

REFERENCE: [[integrate-test-e2e.md]]

