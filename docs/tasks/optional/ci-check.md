# Optional: Add a CI Check (GitHub Actions)

**Time:** ~30-40 min

**Purpose:** Learn how to set up automated checks that run on every PR.

## What's CI?

**Continuous Integration (CI)** automatically runs checks (tests, linting, etc.) whenever you push code. This catches problems early, before they're merged into `main`.

## Steps

### 1. Create an Issue

Title: `[Optional] Deep dive: Add CI`

### 2. Learn About GitHub Actions

Read the [GitHub Actions Quickstart](https://docs.github.com/en/actions/get-started/quickstart).

Key concepts:
- **Workflow:** An automated process defined in a YAML file
- **Job:** A set of steps that run on the same runner
- **Step:** An individual task (run a command, use an action)
- **Trigger:** What starts the workflow (push, PR, schedule)

### 3. Create a Workflow

Create `.github/workflows/lint.yml`:

```yaml
name: Lint Markdown

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run markdownlint
        uses: DavidAnson/markdownlint-cli2-action@v19
        with:
          globs: '**/*.md'
          config: '.markdownlint.jsonc'
```

### 4. Test the Workflow

1. Commit the workflow file.
2. Push and create a PR.
3. Watch the `Actions` tab - the workflow should run.
4. If there are markdown lint errors, fix them.

### 5. Make Sure Checks Pass

Your PR should show a green checkmark when all checks pass.

If you have lint errors:
1. Read the error messages in the Actions log
2. Fix the issues in your markdown files
3. Commit and push - the checks will re-run

---

## Acceptance Criteria

- [ ] Workflow file created at `.github/workflows/lint.yml`
- [ ] Workflow runs on PRs to main
- [ ] Markdownlint check passes
- [ ] PR shows green checkmark

## Reviewer Checklist

- [ ] Workflow file exists and has correct syntax
- [ ] Workflow triggered and ran successfully
- [ ] Check passed (or errors were fixed)

---

## Going Further

Try adding more checks:
- Spell checking with [cspell](https://github.com/streetsidesoftware/cspell-action)
- Link checking with [lychee](https://github.com/lycheeverse/lychee-action)
- Custom scripts for your project

---

Return to the [main README](../../../README.md).
