# Two-cucumbersfloating

Repository prepared for development with a classic GitFlow branching model.

## Permanent branches

- `main`: production-ready code only
- `develop`: integration branch for active development

## Supporting branches

- `feature/<name>`: created from `develop`, merged back into `develop`
- `release/<semver>`: created from `develop`, merged into `main`, then back-merged from `main` into `develop`
- `hotfix/<name>`: created from `main`, merged into `main`, then back-merged from `main` into `develop`

## Working cycle

1. Create a `feature/*` branch from `develop`
2. Open a pull request from `feature/*` into `develop`
3. Cut `release/<semver>` from `develop` when the next release is ready
4. Merge `release/*` into `main`, create a tag, and publish a GitHub Release
5. Open a back-merge pull request from `main` into `develop`

## Documentation

- Branching and merge rules: [docs/GITFLOW.md](docs/GITFLOW.md)
- GitHub settings and required protections: [docs/GITHUB_SETUP.md](docs/GITHUB_SETUP.md)
- Release preparation checklist: [docs/RELEASE_CHECKLIST.md](docs/RELEASE_CHECKLIST.md)
- Release history: [CHANGELOG.md](CHANGELOG.md)
