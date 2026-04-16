# 编排服务

我们在`infra/`文件夹下进行项目的编排，使用`aspire`及其`skill`。

## 初始化编排环境

在执行到编排环节时，编排服务需要使用[[git.md]]的能力，基于`<dev-branch>`创建`worktree`，`<type>`为`infra`。如果没有`infra/local-dev`目录，则默认为用户创建用于本地开发编排的`aspire`项目，在`infra/local-dev`目录下，执行`aspire init --language typescript`进行新建项目。

如何维护使用TypeScript语言的Aspire项目可以使用`aspire docs get typescript-apphost-project-structure`命令获取帮助。

如果已经有了`infra/local-dev`目录，则无需初始化环境。

## 分析项目可能的依赖

搜索技术方案`<proposal>`, 开发分支中的项目引用的包，找到可能的环境变量，并分析出项目之间的依赖关系。如果依赖关系有变化则进行修改，没有则跳过本步骤。

## 完成编排

在编排完成后，提`pull request`要求用户review，直到用户显式说明review通过，或者pull request状态已经是merge了，再进行下一个步骤。

## 依赖的中间件设施

使用`SKILL: aspire`来编排中间件设施，可以通过cli搜索对应的文档`aspire docs search <keyworkd>`，这里的keywor模板可以是 `get-started-with-the-<目标技术栈>-integration`，例如：

```bash
# Redis
aspire docs search get-started-with-the-redis-integration

# postgresql
aspire docs search get-started-with-the-postgresql-integration
```

## TypeScript / NodeJS 相关文档的搜索

统一使用`javascript`的文档来进行替代: `aspire docs search javascript`

## 编排技巧

#### 服务依赖设置

分析后端服务分别对中间设置的依赖，使用如下pattern进行依赖，`withReference`是将对应资源的`parameter resource`注入到目标服务中，`waitFor`则是标记这个服务需要等到目标服务成功启动，health check完成后再进行启动。

```typescript
const redis = await builder.addRedis();

const backend = await builder
  ...some setup...
  .withReference(redis).waitFor(redis);
```

#### 环境变量注入

我们可以通过`.withEnvironment()`注入环境变量，可以从其他的resource中获取对应的endpoint，示例如下：

```typescript
const mongo = await builder.addMongoDB();

const backend = await builder.addJavaScriptApp()
  .withEnvironment("MY_CUSTOM_BACKEND", await mongodb.uriExpression.get());

const frontend = await build.addJavaScriptApp()
  .withEnvironment("API_URI", await api.getEndpoint('http'))
```

#### 开放外部端口

使用`.withHttpEndpoint`开放一个外部端口，使用这个方法会增加名为`http`的endpoint，用于外部访问，比如我们的前端服务，后端服务都需要一个外部端口来进行访问。下面是一个示例：

```typescript
const api = await builder.addJavaScriptApp()
  .withHttpEndpoint({ env: 'PORT' }); // 使用 env将端口号注入到环境变量

const frontend = await build.addJavaScriptApp()
  .withReference(backend)
  .withEnvironment("API_URI", await api.getEndpoint('http'))
```
