# CI/CD (Continuous Integration / Continuous Deployment)

CI/CD automates the process of building, testing, and deploying code changes.

## Concepts

### Continuous Integration (CI)

- Developers merge code frequently to main branch
- Automated builds and tests run on each commit
- Catches integration issues early

### Continuous Deployment (CD)

- Automatically deploy passing builds to production
- Or **Continuous Delivery**: deploy to staging, manual production release

## Typical Pipeline Stages

```
Code Commit → Build → Test → Security Scan → Deploy Staging → Deploy Production
```

## GitHub Actions Example

```yaml
# .github/workflows/ci.yml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm ci

      - name: Run linter
        run: npm run lint

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build
```

## Best Practices

- Run tests on every commit/PR
- Keep builds fast (under 10 minutes)
- Use caching for dependencies
- Implement branch protection rules
- Use environment variables for secrets
- Deploy to staging before production
- Implement rollback strategies
- Monitor deployments with alerts
