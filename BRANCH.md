## Husky

Prevents bad git commit, git push with git hooks.

## Branch name

- **feature**:
- **bugfix**:
- **prerelease**:
- **release**:
- **hotfix**:

## Script

```bash
LC_ALL=C

local_branch="$(git rev-parse --abbrev-ref HEAD)"

valid_branch_regex="^(feature|bugfix|library|prerelease|release|hotfix)\/[a-z0-9._-]+$ || ^dev$"

message="There is something wrong with your branch name. Branch names in this project must adhere to this contract: $valid_branch_regex. Your commit will be rejected. You should rename your branch to a valid name and try again."

if [[ ! $local_branch =~ $valid_branch_regex ]]
then
    echo "$message"
    exit 1
fi

exit 0
```

### example

```
feature/cmm-1955-send-email
bugfix/tul-12567-wrong-email-regex

```
