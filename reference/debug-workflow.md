# 调试

## 诊断原则

1. 不要看代码猜测
2. 用e2e test/api test复现出实际问题

## 调试工作流

使用`todo`工具新建如下`todo`

问题核实 -> 环境准备 -> 复现问题 -> 修复问题

## 问题核实

在上下文不全的情况下，或者用户只抛出了一部分问题，则需要主动和用户沟通上下文信息。使用`ask`或者`question`工具。

在用户显式的说没有其他补充时，进入到下一个环节。

## 环境准备

delegate `@general` subagent to prepare environment

使用[[git.md]]进行分支管理，每次进行调查根据当前分支创建新的`worktree`，`<type>`为`issues`，`<slug>`为上面核实问题的简写。在这个新的`worktree`进行后续操作

在这个`worktree`使用[[dev/ref/aspire.md]] aspire来启动服务，准备完成后进入到下一个步骤

## 复现问题

按照和用户沟通的信息，使用e2e或者api测试尝试复现问题，包括但不限于可以截图查看浏览器状态等手段。

## 修复问题

delegate `@general` subagent to fix the issues

修复在`worktree`进行，修复完成后，提`pull request`让用户进行review。
修复时，需要编写e2e test或api test放置之后再出现类似的问题。
