# Practice the `Git workflow`

**Time:** ~15 min

**Purpose:** Practice the [`Git workflow`](../git-workflow.md) before working on the main tasks.

**Context:** This task is an opportunity to practice the full cycle (Issue → Branch → Commits → PR → Review → Merge).

## Steps

### 1. Create an issue

Title: `[Task] Add my name to contributors`

### 2. Create a branch

On the issue page, click `Create a branch` in the right sidebar.

Alternatively, use the terminal:

```bash
git checkout -b add-contributor
```

### 3. Add your name

> [!NOTE]
> Replace `<your-username>` with your `GitHub` username without `@`.

1. Open [`CONTRIBUTORS.md`](../../../CONTRIBUTORS.md).
2. Add your GitHub username below the comment:

    ```markdown
    <!--
    ...
    -->
    - @<your-username>
    ```

3. Save the file.

### 4. Commit and push

```bash
git add CONTRIBUTORS.md
git commit -m "docs: add <your-username> to contributors"
git push -u origin add-contributor
```

### 5. Create a Pull Request (PR)

1. Go to your fork on `GitHub`.
2. If you see the `Compare & pull request` button, click it.
3. Otherwise:
   1. Click `main`.
   2. In the `Find or create a branch...`, start typing the branch name (`add-contributor`).
   3. Click the branch name in the list.
   4. Click `Contribute`.
   5. Click `Open pull request`.
4. Write the PR title (`Add @<your-username> to contributors`).
5. Write the PR description.
6. Click `Create pull request`.

### 6. Get review and merge

1. Request a review from your partner.
2. Once your partner has approved the PR, click `Merge pull request`.
3. Delete the branch when prompted.

## Acceptance criteria

- [x] Issue created
- [x] Username added to `CONTRIBUTORS.md`
- [x] Commit message follows `type: description` format
- [x] PR created and linked to issue
- [x] Partner reviewed and approved
- [x] PR merged
