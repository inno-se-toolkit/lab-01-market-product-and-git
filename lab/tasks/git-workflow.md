# `Git workflow` for tasks

> [!NOTE]
> This procedure is based on the [`GitHub flow`](https://docs.github.com/en/get-started/using-github/github-flow).

```text
┌───────┐    ┌────────┐    ┌─────────┐    ┌────┐    ┌────────┐    ┌───────┐
│ Issue │ →  │ Branch │ →  │ Commits │ →  │ PR │ →  │ Review │ →  │ Merge │
└───────┘    └────────┘    └─────────┘    └────┘    └────────┘    └───────┘
```

Here's this workflow in the context of repos:

![Git workflow](../images/git-workflow.drawio.svg)

hello my name Danila

Outline:

- [Create an issue](#create-an-issue)
- [Create a branch](#create-a-branch)
  - [Create using `GitHub`](#create-using-github)
  - [Create using the `Terminal`](#create-using-the-terminal)
  - [Create using `GitLens`](#create-using-gitlens)
- [Make commits](#make-commits)
  - [Commit message format](#commit-message-format)
  - [Commit using the `Terminal`](#commit-using-the-terminal)
  - [Commit using `Source Control`](#commit-using-source-control)
  - [Commit using `Source Control` (specific changes)](#commit-using-source-control-specific-changes)
- [Publish the branch](#publish-the-branch)
  - [Publish using the `Terminal`](#publish-using-the-terminal)
  - [Publish using `GitLens`](#publish-using-gitlens)
- [Push more commits](#push-more-commits)
  - [Push using the `Terminal`](#push-using-the-terminal)
  - [Push using `GitLens`](#push-using-gitlens)
- [Create a PR](#create-a-pr)
  - [Open the PR editor using `GitHub`](#open-the-pr-editor-using-github)
    - [Open the PR editor using a button](#open-the-pr-editor-using-a-button)
    - [Open the PR editor using `Pull requests`](#open-the-pr-editor-using-pull-requests)
    - [Open the PR editor using the branch list](#open-the-pr-editor-using-the-branch-list)
  - [Finish creating a PR](#finish-creating-a-pr)
- [Get a PR review](#get-a-pr-review)
  - [PR review rules](#pr-review-rules)
    - [As a PR reviewer](#as-a-pr-reviewer)
    - [As a PR author](#as-a-pr-author)
- [Merge the PR](#merge-the-pr)
- [Clean up](#clean-up)
- [Pull changes](#pull-changes)
  - [Pull using the `Terminal`](#pull-using-the-terminal)
  - [Pull using `GitLens`](#pull-using-gitlens)

## Create an issue

[Create](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue) a `GitHub` issue in your forked repo using the `Lab Task` [issue form](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository#creating-issue-forms) (defined in [`.github/ISSUE_TEMPLATE/01-task.yml`](../../.github/ISSUE_TEMPLATE/01-task.yml)).

## Create a branch

Create a new branch for the issue using one of these ways:

### Create using `GitHub`

1. [Create a branch](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-a-branch-for-an-issue).
1. Copy the command.
1. [Open the `Terminal`](../appendix/vs-code.md#open-the-terminal).
1. Paste the command to the `Terminal`.
1. Press `Enter` to run the command.

### Create using the `Terminal`

1. [Open the `Terminal`](../appendix/vs-code.md#open-the-terminal).
2. [Run](../appendix/vs-code.md#run-a-command-using-the-terminal):

    ```console
    git checkout -b <branch-name>
    ```

> [!IMPORTANT]
> Replace `<branch-name>` with an actual branch name in all subsequent commands.

### Create using `GitLens`

1. [Open the `Command Palette`](../appendix/vs-code.md#open-the-command-palette).
2. Run `GitLens: Git Create Branch...`.
3. Select `main` as the base branch (e.g., using `UpArrow` and `DownArrow` on your keyboard).
4. Press `Enter` to confirm.
5. Write `<branch-name>` to provide the new branch name.
6. Press `Enter` to confirm.
7. `Select Create & Switch to Branch` (e.g., using `UpArrow` and `DownArrow` on your keyboard).
8. Press `Enter` to confirm.

## Make commits

Make commits to that branch to complete the task.

### Commit message format

Format: `type: short description`

Common types:

- `docs:` — documentation changes (most common in this lab)
- `feat:` — new functionality
- `fix:` — bug fixes

### Commit using the `Terminal`

1. Open the [`Terminal`](../appendix/vs-code.md#open-the-terminal).
2. Run:

   ```console
   git add <file>
   # example: git add README.md
   # example (spaces): git add 'path/some image.svg'
   
   git commit -m '<type>: <short description>'
   # example: git commit -m 'docs: add architecture diagram'
   ```

### Commit using `Source Control`

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Go to `Changes`.
3. Hover over a file name.
4. Click `+` to stage the file.
5. Type commit message, e.g., `docs: add architecture diagram`.
6. Click `Commit`.

### Commit using `Source Control` (specific changes)

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Go to `Changes`.
3. Click a file to open it.
4. Select changed lines in the editor (red-green).
5. Right mouse click the selected lines.
6. Click `Stage Selected Ranges`.
7. Go to `Changes`.
8. Write a commit message.
9. Click `Commit`.

## Publish the branch

### Publish using the `Terminal`

1. [Open the `Terminal`](../appendix/vs-code.md#open-the-terminal).
1. Run:

   ```console
   git push -u origin <branch-name>
   ```

### Publish using `GitLens`

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Click `GITLENS` to open the `GitLens` panel.
3. Click the `Commits` icon.
4. Click the `Publish Branch` icon to the right of `Publish <branch-name> to GitHub`.
5. Press `Enter` to confirm.

## Push more commits

### Push using the `Terminal`

1. [Open the `Terminal`](../appendix/vs-code.md#open-the-terminal).
2. Run:

   ```console
   git push
   ```

### Push using `GitLens`

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Click `GITLENS`.
3. Click the `Commits` icon.
4. Click the `Push` icon to the right of `COMMITS`.

## Create a PR

Create a PR to the `main` branch via [`GitHub`](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request#creating-the-pull-request) or via the [`GitHub Pull Requests` extension](https://code.visualstudio.com/docs/sourcecontrol/github#_creating-pull-requests).

### Open the PR editor using `GitHub`

Open the PR editor using one of the following methods.

#### Open the PR editor using a button

Go to your fork on `GitHub`.

If you see the `Compare & pull request` button, click it.

#### Open the PR editor using `Pull requests`

1. Go to your fork on `GitHub`.
1. Click `Pull requests`.
1. Click `New pull request`.
1. Click `base repository: <your-username>/lab-01-market-product-and-git`.
1. Click `<your-username>/lab-01-market-product-and-git` to select the base repo.
1. The PR will be created in your repo with `main` as the base branch.
1. Click `compare: main` to choose a branch to compare with the base.
1. Click `<branch-name>`.
1. Click `Create pull request`.

#### Open the PR editor using the branch list

1. Go to your fork on `GitHub`.
2. Click `main` under the `forked from ...` text.
3. Click `<branch-name>`.
4. Click `Contribute`.
5. Click `Open pull request`.

### Finish creating a PR

1. Write the PR title (`Add @<your-username> to contributors`).
2. Write the PR description.
3. [Link the PR](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) to the issue, e.g. `Closes #<issue number>`.
4. Check the boxes.
5. Click `Create pull request`.

## Get a PR review

[Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review#requesting-reviews-from-collaborators-and-organization-members) a review of the PR from the collaborator (see [PR review rules](#pr-review-rules)).

Get the collaborator's comments and address them, e.g., make fixes or ask to clarify the comment.

Get the collaborator to approve the PR.

### PR review rules

#### As a PR reviewer

1. Check the task's **Acceptance criteria**.
2. Leave at least one [comment](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request#adding-comments-to-a-pull-request) — point out problems or confirm that items look good.
3. [Approve](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request#submitting-your-review) the PR when all relevant acceptance criteria are met.

#### As a PR author

- Address reviewer comments (fix issues or explain your reasoning).
- Reply to comments, e.g., "Fixed in d0d5aeb".

## Merge the PR

Click `Merge pull request`.

## Clean up

Close the issue.

Delete the PR branch.

## Pull changes

### Pull using the `Terminal`

1. [Open the `Terminal`](../appendix/vs-code.md#open-the-terminal).
1. Switch to `main`:

   ```console
   git switch main
   ```

1. Pull changes:

   ```console
   git pull
   ```

### Pull using `GitLens`

Switch to `main`:

1. Go to the [`Status Bar`](../appendix/vs-code.md#status-bar).
2. Click the `<branch-name>`.
3. Click `main`.

Synchronize changes:

1. Go to the [`Status Bar`](../appendix/vs-code.md#status-bar).
2. Click the `Synchronize Changes` icon to the right of `<branch-name>`.
