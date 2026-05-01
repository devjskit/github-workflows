# @devjskit/github-workflows

Reusable GitHub Actions for TypeScript projects, optimized for Bun.

## Features

- Bun-only setup action for checkout, Bun install, and dependency install
- Reusable workflows for unit tests, release, auto-fix, and publish-any-commit previews
- Defaults aligned with Bun commands such as `bun run build`, `bun run test`, `bunx --bun`, and `bun publish`

## Included Workflows

- **Unit Test**: runs typecheck, lint, build, and tests across an OS matrix
- **Release**: generates a GitHub changelog and optionally publishes to npm
- **Auto Fix**: runs a fix command and commits the result through `autofix-ci`
- **Release Commit**: publishes commit builds with `pkg-pr-new`

## Usage

Reference a workflow from your project’s `.github/workflows/*.yml`:

```yaml
name: Unit Test

on:
  push:
    branches: [master, next]
  pull_request:
    branches: [master, next]

permissions: {}

jobs:
  unit-test:
    uses: devjskit/github-workflows/.github/workflows/unit-test.yml@v1
```

See [`examples/`](./examples) for complete examples.

## Action

[`setup-bun/action.yml`](./setup-bun/action.yml) sets up the Bun environment.

```yaml
- name: Setup Bun
  uses: devjskit/github-workflows/setup-bun@v1
  with:
    bun-version: latest
```

The action always uses Bun. By default it installs dependencies with `bun ci`; set `no-frozen-lockfile: true` to use `bun install`.

## 🤝 Contributing

Pull requests are welcome!  
Please open an issue before making major changes.

---

## 📄 License

MIT © 2025 DevJSKit
