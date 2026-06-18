---
name: switch-prod-create-branch 
description: Switch to the production (prod) branch and create a new branch with a given name. Use when asked to switch to prod and create a branch, checkout prod and make a new branch, or any variant of switching to the production branch before branching off. compatibility. Designed for GitHub Copilot in VS Code. Requires git to be installed and a remote named origin to exist. allowed-tools. Bash.If the user has not provided a branch name, ask for one before running any commands.
---

Run this command, replacing `<branch-name> with the name provided by the user:

```bash
git fetch origin && git checkout prod && git pull origin prod && git checkout -b `<branch-name>`
```

Gotchas
If prod does not exist locally yet, git checkout prod will fail. Fall back to:
```bash
git checkout --track origin/prod
```

If the working tree has uncommitted changes, git checkout prod will fail. Tell the user to stash or commit their changes first:
```bash
git stash
```

If `<branch-name>` already exists locally, git checkout -b will fail. Ask the user if they want to switch to it instead (git checkout `<branch-name>`) or pick a different name.
