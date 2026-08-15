# Team Conventions for AI Agents

> This file is read by AI agents (Cursor, Rovo Dev, etc.) at session start.
> It teaches the agent our team's standards so every agent-assisted action
> follows the same conventions a senior developer would.

---

## Project: TaskFlow Web App

A lightweight task management web app.

- **GitHub repo:** https://github.com/dugaldmorrow/task-flow
- **Jira project key:** TA (https://forgery.atlassian.net/jira/core/projects/TA/board)
- **Confluence sprint notes:** https://forgery.atlassian.net/wiki/spaces/AT/pages/1836449794/Task+Flow+Sprint+Notes+-+August

---

## Jira Conventions

### Issue Types
- **Bug** — for defects found in existing functionality
- **Story** — for new features or user-facing improvements
- **Task** — for internal/technical work with no direct user impact

### Required Fields When Creating a Bug
- **Summary:** Short, present-tense description of the broken behaviour (e.g. `Task completion button does not update count`)
- **Description:** Include: (1) what the user observes, (2) what should happen instead, (3) steps to reproduce if known
- **Issue Type:** Bug
- **Priority:** Set to `Medium` unless the bug blocks core functionality (then `High`)
- **Labels:** Add `demo` label to all issues created during demo sessions

### Jira Workflow Transitions
The project uses this workflow:

```
To Do → In Progress → In Review → Fixed → Done
```

- Move to **In Progress** when starting work on the issue (branch created)
- Move to **In Review** when a PR is raised
- Move to **Fixed** when the PR is merged
- **Always add a comment** when transitioning, explaining what happened

### Linking PRs to Jira Issues
- Include the Jira issue key in every PR title and branch name
- Add the GitHub PR URL as a comment on the Jira issue when the PR is created

---

## Git & GitHub Conventions

### Branch Naming
```
<type>/<JIRA-KEY>-<short-description>
```

**Types:**
- `bugfix/` — for bug fixes
- `feature/` — for new features  
- `chore/` — for maintenance, dependency updates, refactoring

**Examples:**
- `bugfix/TA-42-task-count-not-updating`
- `feature/TA-55-add-due-date-field`
- `chore/TA-60-upgrade-dependencies`

**Rules:**
- Use lowercase and hyphens only (no underscores, no slashes within the description)
- Keep descriptions concise — 3 to 5 words maximum
- Always branch from `main`

### Commit Messages
```
<JIRA-KEY>: <imperative verb> <what changed>
```

**Examples:**
- `TA-42: Fix task count not updating after completion`
- `TA-55: Add due date field to task creation form`

**Rules:**
- First line: 72 characters max
- Use imperative mood ("Fix", "Add", "Remove", not "Fixed", "Added", "Removed")
- Reference the Jira key at the start

### Pull Request Title
```
<JIRA-KEY>: <description matching the commit message>
```

**Example:** `TA-42: Fix task count not updating after completion`

### Pull Request Description Template
```markdown
## What
Brief description of what changed and why.

## Jira
[TA-XX](https://forgery.atlassian.net/browse/TA-XX)

## How to Test
1. Step one
2. Step two
3. Expected result
```

### Merge Strategy
- Use **squash merge** for bug fixes and small changes
- Use **merge commit** for features
- Delete the source branch after merging

---

## Agent Behaviour Rules

1. **Always create the Jira issue first** before touching any code or git operations.
2. **Transition the Jira issue to In Progress** immediately after creating the branch.
3. **Transition the Jira issue to In Review** immediately after creating the PR — add the PR URL as a Jira comment.
4. **Do not merge the PR** without explicit instruction from the developer.
5. **After merging**, always: (a) add a comment to Jira with the merge details, (b) transition to Fixed, (c) append a brief note to the [Task Flow Sprint Notes — August](https://forgery.atlassian.net/wiki/spaces/AT/pages/1836449794/Task+Flow+Sprint+Notes+-+August) page in Confluence.
6. **Never hardcode credentials or API keys** in any file — raise this as a blocker if encountered.
7. **Ask before creating issues in production Jira projects** — use the `TA` project for all demo work.
