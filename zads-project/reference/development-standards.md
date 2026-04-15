# Development Standards

你需要严格按照契约式来进行开发，例如 `openapi-spec`, `graphql-schema` 放置在 `contract/` 中。

## 阅读产品文档

每次开发前需要指定一个产品文档，默认可以用`ask`或者`question`工具从目录`docs/product/reviewed`列出日期最新的几个文档，让用户选择或输入`<产品文档>`。

## 开发流程

创建需求分支 -> 编写技术方案 -> 更新Contract -> 创建开发分支 -> 编写实现[1] -> 编排服务 -> 覆盖API测试 -> 覆盖e2e测试。

[1] 编写实现部分是并行进行subagent调用。

为这套流程创建`todo`。

### 加载规范

在写代码之前，如果上下文没有加载对应目录下的AGENTS.md，则进行加载。

例如：修改 `backend/src/x/y/z/a.ts`，加载 `backend/AGENTS.md`

每次进行代码编写，需要加载`docs/engineering/common-rules.md`

### 创建需求分支

在指定了需要开发的产品文档后，在远端创建开发分支`<feat-branch>`，分支名是`feat/<slug>`，其中`<slug>`产品文档内容的提炼。

### 编写技术方案

读取 `<产品文档>`,  `docs/engineering/frontend-rules.md`, `docs/engineering/backend-rules.md`和 `contract/`目录下的结构。

模板参考[[dev/dev-proposal-template.md]]。

使用[[git.md]]规范，分支前缀的`<type>`使用`proposal`，分支基于`<feat-branch>`，编写完成后写入`proposals`文件，路径为`docs/engineering/proposals/<年月日>-proposal-<功能>.md`，并提pull request，合并的目标分支是`<feat-branch>`，完成后中断agent循环，让用户review这个pull request。

如果有修改意见则让提取pull request中的review comment和inline review comment，进行修改，如果用户显式告知review通过则操作合并这个pull request到`<feat-branch>`。

### 更新Contract

读取 `<产品文档>`,  `docs/engineering/frontend-rules.md`, `docs/engineering/backend-rules.md`和 `contract/`目录下的结构。

使用[[git.md]]规范，分支前缀的`<type>`使用`contract`，分支基于`<feat-branch>`（可在`proposal`中找到这个branch），在上生成对应的 contract schema。并提交，如果有`pull request`的工具，则提起`pull request`让用户审批。此时中断Agent循环，让用户输入是否审批完成。

如果用户显示告知review通过，则操作这个`pull request`合并到`<feat-branch>`

### 并行

### 编写实现

读取 `<产品文档>`，`contract/`目录下的结构和对应的`proposal`文档。

对于前端项目：加载`docs/engineering/frontend-rules.md`
对于后端项目：加载`docs/engineering/backend-rules.md`

按照项目结构，单个`<子项目>`使用`@general` subagent，委托进行关于`proposals`文件的这个`<子项目>`部分的开发。提示词如下：
```
读取 `<产品文档>`，`contract/`目录下的结构和<proposal>文档，在`<子项目>`中实现这个需求，并覆盖单元测试直到通过。
```

更新`todo`，为每一项子项目新增`todo`，并在subagent执行完成后完成这个`todo`，待办项有

- `<子项目>`代码实现
- `<子项目>`单元测试覆盖
- `<子项目>`执行单元测试
- `<子项目>`更新AGENTS.md   - 按照本次的修改内容，更新AGENTS.md的内容。

举例说明，假设有如下项目结构
```
servers/api   - 使用@general 委托开发`proposals`关于 server/api的变动
apps/web      - 使用@general 委托开发`proposals`关于 apps/web的变动   
```

#### Explore固定知识库

如果需要使用`Explore`这个subagent进行项目理解时，将这个subagent的输出创建或更新到对应项目的`AGENTS.md`。
