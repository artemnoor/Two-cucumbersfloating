# Two-cucumbersfloating

Repository prepared for development with a GitFlow-based branching model.

## Branches

- `main`: production-ready code only
- `develop`: integration branch for active development
- `feature/<name>`: work on a single task or feature
- `release/<version>`: release preparation and stabilization
- `hotfix/<name>`: urgent fixes for production

## Workflow

Detailed process is described in [docs/GITFLOW.md](docs/GITFLOW.md).

## First steps

1. Create a feature branch from `develop`
2. Develop and commit in small increments
3. Open a pull request into `develop`
4. Use `release/*` and `hotfix/*` only when needed

## GitHub setup

GitHub branch settings and protection rules are described in [docs/GITHUB_SETUP.md](docs/GITHUB_SETUP.md).
