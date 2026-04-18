# 编写实现

读取 `<产品文档>`，`contract/`目录下的结构和对应的`proposal`文档。

对于前端项目：加载`docs/engineering/frontend-rules.md`
对于后端项目：加载`docs/engineering/backend-rules.md`

按照项目结构，单个`<子项目>`使用`@general` subagent，委托进行关于`proposals`文件的这个`<子项目>`部分的开发。提示词如下：
```
需要使用[[git.md]]的能力，基于`<dev-branch>`创建`worktree`，`<type>`为`<servers>`或者`<apps>`
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

实现完成后，两个worktree分别提一个pull request，让用户进行review。等待用户review通过，执行后续步骤。

#### Explore固定知识库

如果需要使用`Explore`这个subagent进行项目理解时，将这个subagent的输出创建或更新到对应项目的`AGENTS.md`。
