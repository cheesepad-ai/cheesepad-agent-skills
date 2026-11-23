# Contributing

Fixes and new skills are welcome. Open an issue first for anything bigger than a wording fix.

## Change a skill

1. Fork the repository and branch from `main`: `git checkout -b fix/<short-name>`.
2. Edit the skill under `skills/<name>/`. Keep `SKILL.md` short and move task detail into
   `references/`.
3. Bump `metadata.version` in its `SKILL.md`: patch for wording, minor for a new action, major for
   a change in how the agent must behave.
4. Add a line to [CHANGELOG.md](CHANGELOG.md).
5. Install it from your checkout and try it with an agent:
   `npx skills add ./ --skill <name>`.
6. Open a pull request to `main` and fill in the template.

## Add a skill

Create `skills/<name>/SKILL.md`. The folder name must equal the `name` in its frontmatter:

```markdown
---
name: <name>
description: When to use the skill, in the words a user would say.
license: MIT
metadata:
  author: cheesepad
  version: '1.0.0'
---

# <Skill title>

Instructions for the agent.
```

Then add it to the table in [README.md](README.md).

## Rules for every skill

- Transactions: the agent shows the wallet's preview and waits for the user's yes on every step.
- Contract addresses come from the CheesePad API or docs. Change one only with a link that shows
  the new address.
- No API keys, private keys or seed phrases in any file.
- No investment advice.
