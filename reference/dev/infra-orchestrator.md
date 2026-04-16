# Service Orchestration

Project orchestration is performed in the `infra/` directory using `aspire` and its `skill`.

## Initialize Aspire Skill

If aspire is not installed in the user's environment, prompt the user to download and install from the [aspire official website](https://aspire.dev/) and abort the Agent workflow. If the user explicitly states that aspire is not needed for orchestration, skip the orchestration process.

If aspire is installed, proceed with operations using knowledge from [[ref/aspire-skill.md]].

## Initialize Orchestration Environment

When reaching the orchestration stage, services need to use [[git.md]] capabilities to create a `worktree` based on `<dev-branch>`, with `<type>` set to `infra`. If no `infra/local-dev` directory exists, create an `aspire` project for local development orchestration in the `infra/local-dev` directory by default.

If `local-dev` aspire project doesn't exist yet, create it by running `aspire init --language typescript`.

For guidance on maintaining a TypeScript Aspire project, use the command `aspire docs get typescript-apphost-project-structure`.

If `infra/local-dev` directory already exists, no environment initialization is needed.

## Analyze Project Dependencies

Search technical proposals (`<proposal>`) and packages referenced in development branch projects to find possible environment variables and analyze dependencies between projects. Modify if there are changes in dependencies; otherwise, skip this step.

## Complete Orchestration

After orchestration is complete, run `npm run aspire:build` and `npm run aspire:lint` in the `local-dev` folder to verify the changes are correct.

Use `aspire stop` + `aspire restore` + `aspire start` + `aspire describe` to start aspire and verify all services started successfully.

Then submit a `pull request` for user review. Proceed to the next step only after the user explicitly approves the review or the pull request status is already merged.

## Middleware Infrastructure Dependencies

Use `SKILL: aspire` to orchestrate middleware infrastructure. Search for corresponding documentation via CLI: `aspire docs search <keyword>`. The keyword template can be `get-started-with-the-<target-tech-stack>-integration`, for example:

```bash
# Redis
aspire docs search get-started-with-the-redis-integration

# PostgreSQL
aspire docs search get-started-with-the-postgresql-integration
```

## TypeScript / NodeJS Documentation Search

Use the `javascript` documentation as a substitute: `aspire docs search javascript`

## Orchestration Tips

### Specify Service Image Tag

Use `.withImageTag(tag: string)` to override Docker Resource tags.

### JavaScript App Integration

Use the `addJavaScriptApp` API. The third parameter is an object like `{ runScriptName: "" }`. If you want to execute the `dev` script, for example:

```typescript
.addJavaScriptApp('service-name', 'project_relative_path', { runScriptName: 'dev' });
```

### Service Dependency Setup

Analyze backend service dependencies on middleware and use the following pattern for dependencies. `withReference` injects the target resource's `parameter resource` into the target service, while `waitFor` marks that this service needs to wait for the target service to start successfully with health check completed before starting.

```typescript
const redis = await builder.addRedis();

const backend = await builder
  ...some setup...
  .withReference(redis).waitFor(redis);
```

### Environment Variable Injection

We can inject environment variables via `.withEnvironment()`. You can get the corresponding endpoint from other resources. Note that `api.getEndpoint` requires await. Example:

```typescript
const mongo = await builder.addMongoDB();

const backend = await builder.addJavaScriptApp()
  .withEnvironment("MY_CUSTOM_BACKEND", await mongodb.uriExpression.get());

const frontend = await build.addJavaScriptApp()
  .withEnvironment("API_URI", await api.getEndpoint('http'))
```

### Expose External Ports

Use `.withHttpEndpoint` to expose an external port. This method adds an endpoint named `http` for external access. Both frontend and backend services need an external port for access. Example:

```typescript
const api = await builder.addJavaScriptApp()
  .withHttpEndpoint({ env: 'PORT' }); // Use env to inject port number into environment variable

const frontend = await build.addJavaScriptApp()
  .withReference(backend)
  .withEnvironment("API_URI", await api.getEndpoint('http'))
```

### Lint Cannot Find tsconfig.json

Create a tsconfig.json that references aspire's apphost tsconfig:

```json
{
  "extends": ["tsconfig.apphost.json"]
}
```