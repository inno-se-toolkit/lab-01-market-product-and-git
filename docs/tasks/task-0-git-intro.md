# Task 0: Git Workflow Practice

**Time:** ~15 min

**Purpose:** Learn the git workflow on a simple task before tackling the main assignments.

> [!TIP]
> If you're new to git, read [docs/git-workflow.md](../git-workflow.md) first.

## What You'll Do

Add your name to the contributors list. This gives you practice with the full workflow:
Issue → Branch → Commit → PR → Review → Merge

## Steps

### 1. Create an Issue

1. Go to your repo on GitHub → `Issues` → `New issue`.
2. Use the `Lab Task` template.
3. Title: `[Task 0] Add my name to contributors`
4. Description: "Add my name to CONTRIBUTORS.md"
5. Submit the issue.

### 2. Create a Branch

On the issue page, click `Create a branch` in the right sidebar.

Or use the terminal:
```bash
git checkout -b add-contributor-<your-name>
```

### 3. Make Changes

1. Open `CONTRIBUTORS.md` in VS Code.
2. Add your name below the comment:

    ```markdown
    # Contributors

    Students who completed this lab:

    <!-- Add your name below in Task 0 -->
    - Your Name (@your-github-username)
    ```

3. Save the file.

### 4. Commit and Push

**Using VS Code:**
1. Go to `Source Control` in the Activity Bar.
2. Stage `CONTRIBUTORS.md` by clicking `+`.
3. Write commit message: `feat: add my name to contributors`
4. Click `Commit`.
5. Click `Sync Changes` or use terminal: `git push -u origin <branch-name>`

**Using terminal:**
```bash
git add CONTRIBUTORS.md
git commit -m "feat: add my name to contributors"
git push -u origin <branch-name>
```

### 5. Create a Pull Request

1. Go to your repo on GitHub.
2. Click `Compare & pull request`.
3. Title: `Add [Your Name] to contributors`
4. Description:
    ```
    Closes #<issue-number>

    Added my name to the contributors list.
    ```
5. Click `Create pull request`.

### 6. Request Review

1. In the PR, add your partner as a reviewer.
2. Wait for their review.

### 7. Merge

Once approved:
1. Click `Merge pull request`.
2. Delete the branch when prompted.

---

## Acceptance Criteria

- [ ] Issue created with correct title
- [ ] Branch created from the issue
- [ ] Name added to `CONTRIBUTORS.md`
- [ ] Commit message follows Conventional Commits format
- [ ] PR created and linked to issue
- [ ] Partner reviewed and approved

## Reviewer Checklist

As a reviewer, verify:

- [ ] The contributor's name is added to `CONTRIBUTORS.md`
- [ ] The commit message follows `feat: ...` format
- [ ] The PR description links to the issue

If everything looks good, approve the PR.

---

**Done!** Proceed to [Task 1: Architecture](./task-1-architecture.md).
