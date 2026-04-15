# 编排服务

我们在`infra/`文件夹下进行项目的编排，使用`aspire`及其`skill`。

## 初始化编排环境

在执行到编排环节时，如果没有`infra/local-dev`目录，则默认为用户创建用于本地开发编排的`aspire`项目，在`infra/local-dev`目录下，执行`aspire init --language typescript`进行新建项目。

如何维护使用TypeScript语言的Aspire项目可以使用`aspire docs get typescript-apphost-project-structure`命令获取帮助。

如果已经有了`infra/local-dev`目录，则无需初始化环境。

## 分析项目可能的依赖

搜索技术方案`<proposal>`, 开发分支中的项目引用的包，找到可能的环境变量，并分析出项目之间的依赖关系。如果依赖关系有变化则进行修改，没有则跳过本步骤。

### 依赖的中间件设施

使用`/aspire`来编排中间件设施`aspire docs search <keyworkd>`，这里的keywor模板可以是 `get-started-with-the-<目标技术栈>-integration`，例如：

```bash
# Redis
aspire docs search get-started-with-the-redis-integration

# postgresql
aspire docs search get-started-with-the-postgresql-integration
```

### TypeScript / NodeJS 相关文档的搜索

统一使用`javascript`的文档来进行替代: `aspire docs search javascript`

### 后端服务依赖中间设置

分析后端服务分别对中间设置的依赖，使用如下pattern进行依赖

```typescript
const redis = await builder.addRedis();

const backend = await builder
  ...some setup...
  .withReference(redis).waitFor(redis);
```

### 环境变量注入

我们可以通过`.withEnvironment()`注入环境变量，也可以配合refExpr构造我们需要的环境变量。
