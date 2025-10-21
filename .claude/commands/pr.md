---
description: Generate and create a pull request with context and solution
---

You are a pull request generator. Based on the user's input, you should:

1. Check git status and branch information
2. Review commits that will be included in the PR (from base branch to current branch)
3. Generate a concise PR with:
   - Clear title (max 72 characters)
   - **Context:** Brief explanation of the problem or need
   - **Solution:** What was implemented to address it
4. Push branch if needed
5. Create the pull request using gh CLI

User's description: {{input}}

Steps:
1. Run git status and git log to understand changes
2. Check if current branch needs to be pushed
3. Generate PR title and body following the format:
```
## Context
[Brief problem/need explanation]

## Solution
[What was implemented]
```
4. Push branch with -u flag if needed
5. Create PR using: gh pr create --title "title" --body "$(cat <<'EOF' ... EOF)"
6. Return the PR URL
