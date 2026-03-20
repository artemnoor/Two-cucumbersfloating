# Contributing

## Branching model

This repository uses GitFlow:

- branch from `develop` for all regular work
- merge completed features back into `develop`
- cut `release/*` branches from `develop`
- merge release branches into both `main` and `develop`
- cut `hotfix/*` branches from `main`
- merge hotfix branches into both `main` and `develop`

## Branch naming

- `feature/<short-description>`
- `release/<semver>`
- `hotfix/<short-description>`

## Commit guidance

- keep commits focused
- use clear commit messages
- avoid mixing refactors, fixes, and features in one commit

## Pull requests

- target `develop` for features
- target `main` and back-merge to `develop` for releases and hotfixes
- describe scope, risks, and validation steps
