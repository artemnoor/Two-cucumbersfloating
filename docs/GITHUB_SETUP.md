# GitHub Setup For GitFlow

This repository uses `main` and `develop` as the permanent branches.

## Recommended default branch

Set `develop` as the default branch if you want all day-to-day work and feature pull requests to start there.

## Branch protection rules

### Protect `main`

Recommended options:

- require a pull request before merging
- require at least 1 approval
- dismiss stale approvals when new commits are pushed
- require conversation resolution before merging
- require review from code owners
- require status checks to pass before merging
- select the `GitFlow Guard` workflow as a required check
- select the `Repository Quality Gates` workflow as a required check
- block direct pushes to `main`
- block force pushes
- block deletions
- include administrators if you want the rule to apply to everyone

Expected PR direction:

- `release/* -> main`
- `hotfix/* -> main`

### Protect `develop`

Recommended options:

- require a pull request before merging
- require at least 1 approval
- require conversation resolution before merging
- require review from code owners
- require status checks to pass before merging
- select the `GitFlow Guard` workflow as a required check
- select the `Repository Quality Gates` workflow as a required check
- block direct pushes to `develop`
- block force pushes
- block deletions

Expected PR direction:

- `feature/* -> develop`
- `main -> develop`

## GitHub UI path

As of March 20, 2026, GitHub documents branch setup through repository `Settings`, then `Branches`, where you can change the default branch and create branch protection rules. Source: [GitHub Docs](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch) and [GitHub Docs](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

## Suggested merge policy

- allow squash merge for `feature/*`
- allow merge commits for `release/*` and `hotfix/*`
- allow auto-delete of head branches after merge
- avoid direct commits into `main` and `develop`
- avoid rebase merge for release and hotfix branches so branch history stays explicit

## Suggested first working cycle

```bash
git switch develop
git pull
git switch -c feature/add-login
# work here
git push -u origin feature/add-login
# open PR: feature/add-login -> develop
```

## Release cycle

```bash
git switch develop
git pull
git switch -c release/0.1.0
git push -u origin release/0.1.0
# open PR: release/0.1.0 -> main
# after merge: create tag v0.1.0 and GitHub Release
# after merge, open PR: main -> develop
```

## Repository settings to review once

- enable `Issues` only if you plan to track work in GitHub
- keep `Pull Requests` and `Actions` enabled
- enable automatic branch deletion after merge
- restrict who can push to `main` and `develop` if the repository becomes collaborative
