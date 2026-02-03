# Add a CI check

1. Create the issue `[Task] Add a CI check`.
2. Read [Quickstart for `GitHub Actions`](https://docs.github.com/en/actions/get-started/quickstart).
3. Enable [`GitHub Actions`](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository) for your fork.
4. In `.github/workflows/ci.yml`, write a `GitHub Actions` workflow that runs on PRs and on push.
5. Add the `check` job that runs these checks:
   1. Check `Markdown` files using a linter - [`DavidAnson/markdownlint-cli2-action`](https://github.com/DavidAnson/markdownlint-cli2-action).
   2. Check links in `Markdown` files - [`tcort/github-action-markdown-link-check`](https://github.com/tcort/github-action-markdown-link-check#how-to-use).
6. Commit changes and publish the branch.
7. Open a PR to `main` and make sure the workflow passes without warnings.
8. Provide a link to the PR in the issue description.
9. Close the PR. Don't merge it.
10. Close the issue.
