# Contributing

## Branching model

This repository uses GitFlow:

- branch from `develop` for all regular work
- merge completed features back into `develop`
- cut `release/*` branches from `develop`
- merge release branches into `main`, then back-merge `main` into `develop`
- cut `hotfix/*` branches from `main`
- merge hotfix branches into `main`, then back-merge `main` into `develop`
- do not commit directly to `main` or `develop`

## Branch naming

- `feature/<short-description>`
- `release/<semver>`
- `hotfix/<short-description>`

## Commit guidance

- keep commits focused
- use clear commit messages
- avoid mixing refactors, fixes, and features in one commit
- prefer conventional prefixes such as `feat:`, `fix:`, `docs:`, `chore:`

## Pull requests

- target `develop` for features
- target `main` for releases and hotfixes
- open a separate back-merge PR from `main` into `develop` after every release or hotfix
- describe scope, risks, and validation steps
- update `CHANGELOG.md` in release and hotfix PRs when user-visible behavior changes
