# Conventional Commits using Git Hooks

The [Conventional Commits](https://www.conventionalcommits.org/) specification is a lightweight convention on top of commit messages.
It provides an easy set of rules for creating an explicit commit history, which makes it easier to write automated tools on top of.

## Why Conventional Commits

Conventional Commits offer some advantages, such as:

- Automatically generating CHANGELOGs.
- Automatically determining a semantic version bump (based on the types of commits landed).
- Communicating the nature of changes to teammates, the public, and other stakeholders.
- Triggering build and publish processes.
- Making it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

## Commit Messages Convention

This convention dovetails with [SemVer](https://semver.org/), by describing the features, fixes, and breaking changes made in commit messages.
In order to have a consistent git history every commit must follow a specific template.

Here's the template:

```bash
<type>(<ITEM ID>?): <subject>

[optional body]

[optional footer(s)]
```

### Type

Must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: Gradle, Maven)
- **ci**: Changes to our CI configuration files and scripts (example scopes: Jenkins, Travis, Circle, SauceLabs)
- **chore**: Changes to the build process or auxiliary tools and libraries such as documentation generation
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **revert**: A commit that reverts a previous one
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc.)
- **test**: Adding missing tests or correcting existing tests

### ITEM ID

The related **issue** or **user story** or even **defect**.

- For **user stories**, you shoud use `US-` as prefix. Example: `feat(US-4321): ...`
- For **no related issues** or **defects** you should leave it blank. Example: `feat: ...`

### Subject

The subject contains a succinct description of the change.

## Configuring the Git Hook

[Git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) are scripts that run automatically every time a particular event occurs in a Git repository.
They let you customize Git's internal behavior and trigger customizable actions at key points in the development life cycle.

Git hooks reside in the `.git/hooks` directory of every Git repository.
[Git Hook Plugin](https://github.com/STAR-ZERO/gradle-githook) automatically create git hook script file when you run any Gradle task.

```groovy
githook {
    hooks {
        'commit-msg' {
            task = 'commitlint'
        }
    }
}
```

Common use cases for Git hooks include encouraging a commit policy, altering the project environment depending on the state of the repository, and implementing continuous integration workflows.

## Reference Documentation

For further reference, please consider the following articles:

- [Official Gradle documentation](https://docs.gradle.org)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Hooks Tutorial](https://www.atlassian.com/git/tutorials/git-hooks)
