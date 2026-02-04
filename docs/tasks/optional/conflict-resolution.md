# Optional: Merge Conflicts & Resolution

**Time:** ~20-30 min

**Purpose:** Learn how to handle merge conflicts - a common situation when collaborating with git.

## What's a Merge Conflict?

A merge conflict happens when two people edit the same lines in the same file, and git can't automatically merge the changes. You'll need to manually decide which changes to keep.

## Setup

This task requires coordination with your partner. You'll both edit the same file to intentionally create a conflict.

## Steps

### 1. Create an Issue

Title: `[Optional] Deep dive: Merge conflicts`

### 2. Learn About Conflicts

Complete these exercises on [Learn Git Branching](https://learngitbranching.js.org/):

1. **Main** → **Ramping Up** → **Merging in Git** (level 2)
2. **Main** → **Ramping Up** → **Rebase Introduction** (level 3)

### 3. Create a Conflict

Coordinate with your partner:

1. **Both of you** create branches from `main`:
   - You: `git checkout -b conflict-resolution-<your-name>`
   - Partner: `git checkout -b conflict-resolution-<partner-name>`

2. **Both of you** edit `docs/team-agreement.md`:
   - Open the file
   - Fill in the **same sections** with your own preferences
   - For example, both fill in "Preferred communication channel"

3. **One person** merges first:
   - Create PR, get review, merge to `main`

4. **Second person** now has a conflict:
   - Try to create PR or merge - you'll see a conflict

### 4. Resolve the Conflict

**Option A: Resolve on GitHub**
1. GitHub will show "This branch has conflicts that must be resolved"
2. Click `Resolve conflicts`
3. Edit the file to combine both versions appropriately
4. Click `Mark as resolved` → `Commit merge`

**Option B: Resolve locally**
```bash
git checkout main
git pull
git checkout your-branch
git merge main
# Git will show conflict markers in the file
# Edit the file to resolve
git add docs/team-agreement.md
git commit -m "fix: resolve merge conflict in team agreement"
git push
```

### 5. Document What Happened

In your PR description, add:

```markdown
## Conflict Resolution Note

**What conflicted:**
<1-2 sentences describing which sections conflicted>

**How I resolved it:**
<1-2 sentences explaining your resolution approach - did you keep both? combine them? choose one?>
```

### 6. Merge the PR

Once resolved and reviewed, merge your PR.

---

## Acceptance Criteria

- [ ] Completed Learn Git Branching exercises on merge/rebase
- [ ] Successfully created a merge conflict with partner
- [ ] Resolved the conflict (either on GitHub or locally)
- [ ] PR description includes conflict resolution note
- [ ] PR merged

## Reviewer Checklist

- [ ] The `team-agreement.md` file has content from both partners
- [ ] The conflict resolution note explains what happened
- [ ] The merged content makes sense (not garbled)

---

## Tips

- Conflict markers look like this:
  ```
  <<<<<<< HEAD
  Your changes
  =======
  Their changes
  >>>>>>> branch-name
  ```
- Delete the markers and keep the content you want
- Test that the file is valid after resolving

---

Return to the [main README](../../../README.md).
