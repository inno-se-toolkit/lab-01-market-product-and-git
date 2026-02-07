# Lab setup

## Find a partner

1. Find a classmate to be your partner for this lab.
2. Sit together.

## Set up a fork

1. Create a `GitHub` account.
2. [Fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#forking-a-repository) this repo (repository) to your `GitHub` account and make your fork public.
3. Continue your work in the forked repo.
4. In the repo -> `Settings` -> `General` -> `Features`, enable `Issues`.

## Add a classmate as a collaborator

In your repo `Settings` -> `Collaborators` -> `Add people`, add your partner as a collaborator.

Your partner should add you as a collaborator in their repo.

Make sure your collaborator has accepted the invitation sent to their email.

It's OK if your collaborator can't change `Settings` in your repo.

## Protect your `main` branch

Branch protection prevents accidental pushes directly to `main`.
This enforces the PR workflow and ensures all changes are reviewed.

1. Go to your fork.
2. Go to `Settings`.
3. Go to `Code and automation`.
4. Go to `Rules`.
5. Go to `Rulesets`.
6. Go to `New ruleset`.
7. Go to `Add branch ruleset`.
8. Set:

   1. `Ruleset Name`: `push`
   2. `Enforcement status`: `Active`
   3. `Target branches` -> `Add target` -> `Include default branch`
   4. Rules:
      - [x] `Restrict deletions`
      - [x] `Require a pull request before merging`:
         - `Required approvals`: `1`
         - `Require conversation resolution before merging`
         - `Allowed merge methods`: `Merge`.
      - [x] Block force pushes

## Set up `Git`

[Install `Git`](https://git-scm.com/install/).

On your computer, configure `Git`:

```bash
git config --global user.name '<your-name>'
git config --global user.email '<your-email>'
```

> [!NOTE]
> Replace `<your-name>` with a name and `<your-email>` with an email that you want to see in the commits.
>
> See [docs](https://git-scm.com/docs/git-config#Documentation/git-config.txt-username).

## Set up `VS Code`

1. Install [`VS Code`](https://code.visualstudio.com/).

   We chose this editor because it has built-in AI features and many useful [extensions](./appendix/vs-code.md#extensions).

1. (Optional) [Learn more](../lab/appendix/vs-code.md) about `VS Code`.

## Open the repository on your computer

1. On your computer, create somewhere a directory `software-engineering-toolkit`.
2. Open a terminal in that directory.
3. Clone the lab repo.

    ```bash
    git clone https://github.com/<your-username>/lab-01-market-product-and-git
    ```

> ![IMPORTANT]
> Replace `<your-username>` with your `GitHub` username.

1. Open the repo in `VS Code`.

    ```bash
    code lab-01-market-product-and-git
    ```

## Set up `VS Code` extensions

1. Install the recommended `VS Code` [extensions](./appendix/vs-code.md#extensions) (listed in [`.vscode/extensions.json`](../.vscode/extensions.json)) when `VS Code` prompts to install them.
2. Sign in to accounts.
    1. Go to the [`Activity Bar`](./appendix/vs-code.md#activity-bar).
    2. Click the icon `Accounts`.
    3. Click `Sign in with GitHub ...`.
    4. Repeat for the remaining extensions if there are any.

## Explore `VS Code` layout

Look at the [`Basic Layout`](./appendix/vs-code.md#basic-layout).

## Open `Markdown` file preview

Open `README.md` using one of these approaches:

- Approach 1:
  - [Use the `Command Palette`](./appendix/vs-code.md#open-a-file).
- Approach 2:
    1. [Open `Folders`](./appendix/vs-code.md#open-folders).
    2. Click `README.md`.

Open the [`Markdown` preview](https://code.visualstudio.com/docs/languages/markdown#_markdown-preview) using one of these approaches:

- Approach 1:
  1. Go to [`Editor Toolbar`](./appendix/vs-code.md#editor-toolbar).
  2. Click `Open Preview to the Side`.

- Approach 2:
   1. [Open the `Command Palette`](./appendix/vs-code.md#open-the-command-palette).
   2. Run `Markdown: Open Preview to the Side`.

## Change workspace settings

Look at the [workspace settings](./appendix/vs-code.md#workspace-settings) and change them as necessary.

---

## Optional enhancements to make your life easier

### Coding: Set up a coding agent

A coding agent can help you write code, explain concepts, and debug issues.

See [Coding agents](./appendix/coding-agents.md).

### Shell: Set up the prompt

Starship shows your current `Git` branch, status, and other useful info directly in your terminal prompt.

Install [`Starship`](https://github.com/starship/starship#-installation).

### `VS Code`: Check `GitLens`

GitLens shows commit history, blame annotations, and branch visualization right inside `VS Code`.

#### Look at the commit graph

1. Go to the [`Status Bar`](../lab/appendix/vs-code.md#status-bar):
1. Click the icon `Visualize commits on the Commit Graph`.
1. Make sure you can see the commit graph.

#### Inspect remotes and the current branch

1. [Open the `Source Control`](../lab/appendix/vs-code.md#open-the-source-control).
1. Click `GITLENS` in the opened [`Primary Side Bar`](../lab/appendix/vs-code.md#basic-layout).
1. Go to the `GITLENS` panel.
1. Click the icon `Remotes`.
1. Make sure `origin` points to your repo URL (hover over it an look at URLs).
1. Click the icon `Commits`.
1. Make sure you can see commits on the current branch.

#### (Optional) Learn more about `GitLens`

See [`GitLens` features](https://help.gitkraken.com/gitlens/gitlens-features/).

### Repo: Create a label for tasks

> [!TIP]
> If you create the `task` label before creating issues, your issues will have this label automatically as configured in the [issue form](../.github/ISSUE_TEMPLATE/01-task.yml).

[Labels](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/managing-labels) help you filter and organize issues.

With a `task` label, you can see in one view all lab tasks that have this label.

In the repo -> `Issues` -> `Labels`, create a new label:

1. Click `New label`.
2. Name: `task`.
3. Click `Create label`.

Then [add this label](https://github.com/orgs/community/discussions/53473#discussioncomment-5697478) to some of your task issues.

Next, in the repo -> `Issues`, filter by the label:

1. Click `Labels`.
2. In the `Filter labels` input area, write `task`.
3. Click the suggested label.
4. You'll see all issues that have this label.
