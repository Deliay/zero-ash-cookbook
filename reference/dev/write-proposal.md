# 编写技术方案

读取 `<产品文档>`,  `docs/engineering/frontend-rules.md`, `docs/engineering/backend-rules.md`和 `contract/`目录下的结构。

模板参考[[dev/dev-proposal-template.md]]。

使用[[git.md]]规范，分支前缀的`<type>`使用`proposal`，分支基于`<feat-branch>`，编写完成后写入`proposals`文件，路径为`docs/engineering/proposals/<年月日>-proposal-<功能>.md`，并提pull request，合并的目标分支是`<feat-branch>`，完成后中断agent循环，让用户review这个pull request。

如果有修改意见则让提取pull request中的review comment和inline review comment，进行修改，如果用户显式告知review通过则操作合并这个pull request到`<feat-branch>`。
