# Release Checklist

Use this checklist when preparing a `release/<semver>` branch.

## Before cutting the branch

- `develop` is green and reviewed
- open feature PRs planned for the release are already merged into `develop`
- the target version number is agreed

## On `release/<semver>`

- update `CHANGELOG.md`
- update any version strings used by the project
- run local validation required by the repository
- document known risks in the release PR
- push the branch and open `release/<semver> -> main`

## After merging into `main`

- pull `main`
- create and push tag `v<semver>`
- publish a GitHub Release from the tag
- open a back-merge PR from `main` into `develop`
- delete the release branch after the back-merge is complete

## Hotfix note

For urgent production fixes, use the same checklist from `hotfix/<name>` with a patch version tag such as `v0.1.1`.
