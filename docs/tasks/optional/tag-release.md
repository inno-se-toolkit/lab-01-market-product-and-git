# Optional: Tag and Release Notes

**Time:** ~25-30 min

**Purpose:** Learn how software teams mark milestones and communicate what's been accomplished.

## What Are Tags and Releases?

- **Tag:** A named reference to a specific commit (like a bookmark)
- **Release:** A GitHub feature that packages a tag with release notes

Professional teams use releases to:
- Mark stable versions of their software
- Communicate changes to users
- Provide downloadable artifacts

## Steps

### 1. Create an Issue

Title: `[Optional] Deep dive: Tag and release`

### 2. Learn the Concepts

Read:
- [Managing releases in a repository](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
- [Semantic Versioning 2.0.0](https://semver.org/)

**Semantic Versioning** uses `MAJOR.MINOR.PATCH`:
- `MAJOR`: Breaking changes
- `MINOR`: New features (backwards compatible)
- `PATCH`: Bug fixes

For this lab, use `v0.1.0` (initial development version).

### 3. Gather Your Metrics

Before creating the release, collect data about your work:

```markdown
## Lab Statistics

- **PRs merged:** <count>
- **Commits made:** <count>
- **Issues closed:** <count>
- **Time spent:** <estimate in hours>
- **Files created:** <count>
```

Use `git log --oneline` and GitHub's insights to find these numbers.

### 4. Create a Tag

**Option A: Via GitHub (when creating release)**
GitHub can create the tag automatically when you create a release.

**Option B: Via terminal**
```bash
git tag -a v0.1.0 -m "Lab 01 complete"
git push origin v0.1.0
```

### 5. Create a Release

1. Go to your repo → `Releases` → `Create a new release`
2. Tag: `v0.1.0` (create new or select existing)
3. Title: `v0.1.0 - Lab 01 Complete`
4. Write release notes (see template below)
5. Click `Publish release`

### 6. Release Notes Template

```markdown
## Summary

Completed Lab 01: Products, Architecture & Roles.

## What Was Built

- [x] Analyzed [Product Name] architecture
- [x] Mapped components to tech roles
- [x] Assessed personal skills against market demands
- [x] Practiced GitHub flow (issues, PRs, reviews)

## Key Documents

- [Architecture Analysis](./docs/architecture.md)
- [Roles and Skills](./docs/roles-and-skills.md)

## Lab Statistics

- PRs merged: X
- Commits made: X
- Issues closed: X
- Estimated time spent: X hours

## What I Learned

1. <something about the product/architecture>
2. <something about tech roles>
3. <something about git/GitHub workflow>
4. <something about your own skills>
5. <something unexpected>

## What Was Challenging

1. <a challenge you faced>
2. <another challenge>

## What I Would Do Differently

1. <if you did this lab again, what would you change?>
2. <another improvement>

## Next Steps

- [ ] <skill you want to develop>
- [ ] <another goal>
```

---

## Acceptance Criteria

- [ ] Tag `v0.1.0` created
- [ ] Release published with meaningful notes
- [ ] Release includes actual metrics (not placeholders)
- [ ] "What I Learned" section has 5 genuine items
- [ ] "What I Would Do Differently" reflects real experience

## Reviewer Checklist

- [ ] Release exists with tag `v0.1.0`
- [ ] Statistics are filled in with real numbers
- [ ] Learnings are specific, not generic
- [ ] Reflections sound genuine (not AI-generated)

---

## Why This Matters

Writing release notes forces you to:
- Reflect on what you accomplished
- Articulate what you learned
- Think about improvements

This is a valuable skill for professional software development.

---

Return to the [main README](../../../README.md).
