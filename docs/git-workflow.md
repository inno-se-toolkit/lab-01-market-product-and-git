# Git Workflow

This document explains the workflow you'll follow for each task in this lab.

> [!NOTE]
> This workflow is based on [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow), a lightweight branching model used by many software teams.

## The Flow

```text
┌───────┐    ┌────────┐    ┌─────────┐    ┌────┐    ┌────────┐    ┌───────┐
│ Issue │ →  │ Branch │ →  │ Commits │ →  │ PR │ →  │ Review │ →  │ Merge │
└───────┘    └────────┘    └─────────┘    └────┘    └────────┘    └───────┘
```

Each task follows this cycle. Here's what each step means:

## Step-by-Step

### 1. Create an Issue

An **issue** describes what you're going to do.

1. Go to your repo on GitHub → `Issues` → `New issue`.
2. Select the `Lab Task` template.
3. Fill in the title and description.
4. Click `Submit new issue`.

**Why?** Issues create a record of planned work and enable discussion before you start.

### 2. Create a Branch

A **branch** is a separate line of development where you make changes without affecting `main`.

1. On the issue page, click `Create a branch` (in the right sidebar).
2. Or use the terminal:

    ```bash
    git checkout -b <branch-name>
    ```

    Use a descriptive name like `task-1-architecture` or `add-contributors`.

**Why?** Branches let you work on features independently and keep `main` stable.

### 3. Make Commits

A **commit** saves a snapshot of your changes with a message explaining what you did.

**Commit message format:**
```
<type>: <short description>
```

Use one of these types:
- `docs:` - documentation changes (most common in this lab)
- `feat:` - new functionality
- `fix:` - bug fixes

Examples:
- `docs: add architecture diagram`
- `docs: describe main components`
- `fix: correct typo in deployment section`

**Using VS Code:**
1. Make changes to files.
2. In the `Activity Bar`, click `Source Control`.
3. Click `+` next to changed files to stage them.
4. Write a commit message (see format above).
5. Click `Commit`.

**Using terminal:**
```bash
git add <file1> <file2>
git commit -m "docs: add product description"
```

**Why?** Good commit messages help others (and future you) understand what changed and why.

### 4. Push to Remote

**Push** uploads your local commits to GitHub.

```bash
git push -u origin <branch-name>
```

The `-u` flag sets up tracking so future pushes just need `git push`.

### 5. Create a Pull Request

A **Pull Request (PR)** proposes merging your branch into `main`.

1. Go to your repo on GitHub.
2. Click `Compare & pull request` (appears after pushing).
3. Fill in the PR description using the template:
   - Describe what you did
   - Link the issue: `Closes #<issue-number>`
4. Click `Create pull request`.

**Why?** PRs enable code review before changes reach `main`.

### 6. Request a Review

1. In the PR, click the gear icon next to `Reviewers`.
2. Select your partner.

Your partner will receive a notification to review your PR.

### 7. Address Review Comments

When your partner leaves comments:
1. Read each comment carefully.
2. Make fixes if needed, commit, and push.
3. Reply to comments explaining what you did (e.g., "Fixed in abc1234").
4. If you disagree, explain your reasoning.

### 8. Get Approval and Merge

Once your partner approves:
1. Click `Merge pull request`.
2. Click `Confirm merge`.
3. (Optional) Delete the branch when prompted.

The issue will auto-close if you used `Closes #<number>` in the PR.

---

## Common Git Commands

| Command | What it does |
|---------|--------------|
| `git status` | Show which files have changed |
| `git add <file>` | Stage a file for commit |
| `git commit -m "message"` | Create a commit |
| `git push` | Upload commits to GitHub |
| `git pull` | Download changes from GitHub |
| `git checkout -b <name>` | Create and switch to a new branch |
| `git checkout main` | Switch to the main branch |
| `git log --oneline` | View commit history |

## When Things Go Wrong

**"I committed to the wrong branch"**
```bash
# If you haven't pushed yet:
git reset HEAD~1          # Undo the commit (keeps changes)
git checkout correct-branch
git add . && git commit -m "message"
```

**"I need to undo my last commit"**
```bash
git reset --soft HEAD~1   # Keeps changes staged
# or
git reset HEAD~1          # Keeps changes unstaged
```

**"My push was rejected"**
```bash
git pull --rebase         # Get remote changes first
git push                  # Then push your changes
```

**"I have merge conflicts"**
See the [optional task on conflict resolution](./tasks/optional/conflict-resolution.md) or ask your partner/TA for help.

---

## PR Reviews: How to Be a Good Reviewer

As a reviewer, your job is to:

1. **Understand** what the PR is doing.
2. **Verify** the work meets the acceptance criteria.
3. **Ask questions** if something is unclear.
4. **Approve** when everything looks good.

### What to Look For

Each task has a **Reviewer Checklist** at the bottom. Use it.

### How to Leave Comments

1. Go to the `Files changed` tab.
2. Hover over a line, click the `+` button.
3. Write your comment and click `Add single comment` or `Start a review`.
4. When done, click `Review changes` → `Approve` (or `Request changes`).

### If the PR Looks Good

It's fine to approve! Leave a comment about something you learned or found interesting. You don't need to find problems where there aren't any.

---

Return to the [main README](../README.md) to continue with tasks.
