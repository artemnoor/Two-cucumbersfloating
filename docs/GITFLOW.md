# GitFlow Guide

## Main branches

### `main`

- contains only stable, production-ready code
- every merge into `main` should correspond to a releasable state

### `develop`

- default branch for day-to-day development
- all finished features land here first

## Supporting branches

### `feature/*`

- created from `develop`
- merged back into `develop`

Example:

```bash
git switch develop
git pull
git switch -c feature/add-auth
```

### `release/*`

- created from `develop`
- used for final testing, changelog updates, and version bumps
- merged into `main` and then back into `develop`

Example:

```bash
git switch develop
git pull
git switch -c release/0.1.0
```

### `hotfix/*`

- created from `main`
- used for urgent fixes after a production release
- merged into `main` and back into `develop`

Example:

```bash
git switch main
git pull
git switch -c hotfix/fix-login
```

## Recommended merge rules

- features: `feature/* -> develop`
- releases: `release/* -> main`, then `main/release -> develop`
- hotfixes: `hotfix/* -> main`, then `main/hotfix -> develop`

## Suggested protection rules on GitHub

- protect `main`
- protect `develop`
- require pull requests before merging
- block direct pushes to protected branches
- require at least one review before merge
- require status checks when CI is added

## Suggested first release path

```bash
git switch develop
git switch -c feature/initial-setup
git commit --allow-empty -m "chore: project bootstrap"
git switch develop
git merge --no-ff feature/initial-setup
git switch -c release/0.1.0
git switch main
git merge --no-ff release/0.1.0
git tag v0.1.0
git switch develop
git merge --no-ff release/0.1.0
```
