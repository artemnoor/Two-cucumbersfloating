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
- should contain one focused unit of work

Example:

```bash
git switch develop
git pull
git switch -c feature/add-auth
```

### `release/*`

- created from `develop`
- used for final testing, changelog updates, and version bumps
- merged into `main`
- after the release PR is merged, open a back-merge PR from `main` into `develop`
- branch name should follow `release/<semver>`, for example `release/0.2.0`

Example:

```bash
git switch develop
git pull
git switch -c release/0.1.0
```

### `hotfix/*`

- created from `main`
- used for urgent fixes after a production release
- merged into `main`
- after the hotfix PR is merged, open a back-merge PR from `main` into `develop`

Example:

```bash
git switch main
git pull
git switch -c hotfix/fix-login
```

## Recommended merge rules

- features: `feature/* -> develop`
- releases: `release/* -> main`, then `main -> develop`
- hotfixes: `hotfix/* -> main`, then `main -> develop`

## Suggested protection rules on GitHub

- protect `main`
- protect `develop`
- require pull requests before merging
- block direct pushes to protected branches
- require at least one review before merge
- require review from code owners
- require status checks to pass before merging
- include administrators if you want the rule to apply to everyone

## Daily development flow

```bash
git switch develop
git pull origin develop
git switch -c feature/add-auth

# work, commit, push
git push -u origin feature/add-auth

# open PR: feature/add-auth -> develop
```

## Release flow

```bash
git switch develop
git pull origin develop
git switch -c release/0.2.0

# update changelog, version, release notes
git push -u origin release/0.2.0

# open PR: release/0.2.0 -> main
# after merge: create tag v0.2.0 and GitHub Release
# then open PR: main -> develop
```

## Hotfix flow

```bash
git switch main
git pull origin main
git switch -c hotfix/fix-login

# fix, commit, push
git push -u origin hotfix/fix-login

# open PR: hotfix/fix-login -> main
# after merge: create patch tag and GitHub Release
# then open PR: main -> develop
```

## Suggested first release path

```bash
git switch develop
git switch -c feature/initial-setup
git commit --allow-empty -m "chore: project bootstrap"
git switch develop
git merge --no-ff feature/initial-setup
git switch -c release/0.1.0
git push -u origin release/0.1.0
git switch main
git merge --no-ff release/0.1.0
git tag v0.1.0
git push origin v0.1.0
# open PR: main -> develop
```
