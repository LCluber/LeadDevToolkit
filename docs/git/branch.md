---
layout: default
title: Branching
parent: Git
nav_order: 1
---

# Workflow

## Branches

- **master**: For production releases.
- **develop**: For next release development.
- Available branch prefixes for developers : 
    - **feature**: For new feature to develop.
    - **release**: When release cycle is over. Features ready to ship are kept here. Freeing develop branch for next cycle.
    - **bugfix**: For new bug to fix.
    - **hotfix**: For production bug to fix ASAP on master branch.
    - **refactor**: To improve or update code and structure.
    - **doc**: To improve or update developer documentation.
    - **test**: To add or update unit tests or E2E tests.
    - **build**: To improve the workflow of the project.

## Feature branch

From : **develop**

Each new feature should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a feature is complete and tested, it gets merged back into develop. Features never interact directly with master.

When a feature is way behind develop because of a long development process, merge develop into the feature branch to stay tuned.

### example

```bash
git checkout develop
git checkout -b feature/csv-export
```

## Release branch

From : **develop**

Once develop has acquired enough features for a release or a predetermined release date is approaching, you fork a release branch off of develop.

Creating this branch starts the next release cycle, so no new features can be added after this point, only bug fixes, documentation generation, and other release-oriented tasks should go in this branch.

Once it's ready to ship, the release branch gets merged into master and tagged with a version number. In addition, it should be merged back into develop, which may have progressed since the release was initiated.

Using a dedicated branch to prepare releases makes it possible for one team to polish the current release while another team continues working on features for the next release. It also creates well-defined phases of development.

### example

```bash
git checkout develop
git checkout -b release/0.1.0
```

## Bugfix branch

From : **develop**

Each new bug should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a bugfux is complete and tested, it gets merged back into develop. Bugfixes never interact directly with master.

### example

```bash
git checkout develop
git checkout -b bugfix/#456/export-button-color
```

## Hotfix branch

From : **master**

Used to quickly patch production releases.

This is the only branch that should fork directly off of master. As soon as the fix is complete, it should be merged into both master and develop (or the current release branch), and master should be tagged with an updated version number.

Having a dedicated line of development for bug fixes lets your team address issues without interrupting the rest of the workflow or waiting for the next release cycle.

### example

```bash
git checkout master
git checkout -b hotfix/#344/wrong-email-regex
```

## Refactor branch

From : **develop**

Useful technical debt reduction, ESlint/SonarQube fix, 

Each refactor should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When refactor is complete and tested, it gets merged back into develop. Tests never interact directly with master.

### example

```bash
git checkout develop
git checkout -b refactor/export-csv-class
```

## Doc branch

From : **develop**

Each documentation update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

Doc branch is only for developer documentation in order to improve collabortation in the team.
User documentation update has to be developed in a feature branch. 

When documentation is complete, it gets merged back into develop. Documentations never interact directly with master.

### example

```bash
git checkout develop
git checkout -b doc/husky-pre-commit
```

## Test branch

From : **develop**

Each test update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When test is complete, it gets merged back into develop. Tests never interact directly with master.

### example

```bash
git checkout develop
git checkout -b test/csv-export
```

## Build branch

From : **develop**

Each build update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When build is complete and tested, it gets merged back into develop. Builds never interact directly with master.

### example

```bash
git checkout develop
git checkout -b build/gitbranchvalidator
```

## Summary

The overall flow is as follow :

- A develop branch is created from master.
- A release branch is created from develop.
- Feature, Doc, Test and Build branches are created from develop.
- When a feature is complete it is merged into the develop branch.
- When the release branch is done it is merged into develop then master on release date.
- If an issue in master is detected a hotfix branch is created from master.
- Once the hotfix is complete it is merged to both develop and master.

![Gitflow chart][gitflowchart]

[gitflowchart]: ../../assets/git/gitflow.png "Gitflow chart"

## Automation

- [Husky](https://github.com/typicode/husky) : 
Prevents bad git commit, git push with git hooks. It will stop you if your commit message is not valid.
- [GitBranchValidator](https://github.com/LCluber/GitBranchValidator) : 
Automaticaly check the validity of a branch name before commit.
