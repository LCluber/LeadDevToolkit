## Husky

Prevents bad git commit, git push with git hooks.

## Commitizen

Launch commitizen CLI to commit your work. It will guide you to write good conventional commits.

```bash
$ npm run commit
```

## Conventional commits

[official website](https://conventionalcommits.org).

A specification for adding human and machine readable meaning to commit messages :

- Automatic CHANGELOGs.
- Automatic semantic version bump (based on the types of commits landed).
- Communicate the nature of changes to teammates, the public, and other stakeholders.
- Trigger build and publish processes.
- Make it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

The message is structured as follows:

```
<type>([optional scope]): <description>

[optional body]

[optional footer]
```

The commit contains the following structural elements, to communicate intent to the consumers of your library:

### Types

Type must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- **test**: Adding missing tests or correcting existing tests


### example

```
feat(lang): added polish language
```
