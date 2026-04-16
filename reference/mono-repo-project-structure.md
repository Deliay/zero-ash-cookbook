# Monorepo Project Structure

For multi-service projects, the recommended structure is as follows:

```
server/           - Backend projects
apps/             - Frontend projects
packages/         - Shared/common projects
docs/             - Related documentation
docs/product      - Product documents
docs/product/draft    - Product documents pending review
docs/product/reviewed - Product documents in implementation or not yet implemented
docs/product/shipping - Product documents in development
docs/product/released - Product documents that have been merged and accepted
docs/engineering  - Development standards
docs/engineering/proposals/ - Technical development documents
contracts/        - Development contract files (e.g., openapi-spec, graphql-schema)
tests/            - Integration tests, API tests, E2E test projects
```

Example (for illustration only):
```
server/domainA-api
server/domainB-api
server/product-bff
server/product-gateway

apps/domainA-web
apps/domainB-web
apps/domainA-android
apps/domainA-flutter
apps/domainB-react-native

packages/common-package-A
packages/common-package-B

docs/product/draft/20260415-some-domain-feature.md
docs/product/shipping/20260415-another-domain-feature.md
docs/product/released/20260415-one-another-domain-feature.md

contracts/changes/pending/20260415-changes-for-some-domain-feature.md
contracts/changes/applied/
contracts/domainA.graphql
contracts/domainB-openapi.yaml

tests/domainA-api-test
tests/domainA-web-e2e
```

## Project Naming

Project names must have a strong association with their business or functionality. Examples:

```bash
# BAD! Cannot tell what the project is for
server/zeus

# Good! Can directly understand the project's purpose
server/api

# Good! Both reflects the personalized project name and directly indicates the project's purpose
server/zeus-api
```