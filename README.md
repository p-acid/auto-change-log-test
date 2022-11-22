# Auto Change Log Testing

> `standard-version` is excluded

## `standard-version`

### Install

```sh
yarn add -D standard-version
```

### Release

```sh
# initial release
yarn standard-version --first-release

# release command
yarn standard-version # 0.0.1(patch)
yarn standard-version --release-as minor # 0.1.0 (minor)
yarn standard-version --release-as major # 1.0.0 (major)
yarn standard-version --release-as [version-to-release]
```

### How to make CHANGELOG

1. Make commit aligned with [Conventional Commits](https://www.conventionalcommits.org/ko/v1.0.0/#%ea%b0%9c%ec%9a%94).
2. Enter the release command according to the version.
3. Create CHANGELOG with version update according to the type of commit.

### Notice

- If you don't use the types in ".versionrc", it will be not written in CHANGELOG
- If you use "Squash or Rebase and Merge" in Github, you must name the PR aligned with Conventional Commits
- If you use interactive rebase in cli, you must name the title of rebased commit aligned with Conventional Commits

## `release-please`

### About

Auto Release service by Github Actions

### Setting

```yml
# .github/workflow/release-please.yml

name: release-please
on:
  push:
    branches:
      - main
      - develop
jobs:
  release-please:
    runs-on: ubuntu-latest
    steps:
      - uses: google-github-actions/release-please-action@v3
        with:
          release-type: node # Multiple release types are supported
          default-branch: main
          changelog-types: '[{"type": "chore","section": "Others","hidden": false},{"type": "revert","section": "Reverts","hidden": false},{"type": "feat","section": "Features","hidden": false},{"type": "fix","section": "Bug Fixes","hidden": false},{"type": "improvement","section": "Feature Improvements","hidden": false},{"type": "docs","section": "Docs","hidden": false},{"type": "style","section": "Styling","hidden": false},{"type": "refactor","section": "Code Refactoring","hidden": false},{"type": "perf","section": "Performance Improvements","hidden": false},{"type": "test","section": "Tests","hidden": false},{"type": "build","section": "Build System","hidden": false},{"type": "ci","section": "CI","hidden": false}]'
```

### Set specific version in commit

```sh
git commit --allow-empty -m "<type>: <message>" -m "Release-As: <specific-version>"
```
