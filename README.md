# Lab 01 – Products, Architecture & Roles

To kickstart the course, you will explore two things:
>
> 1) How real software products are structured;
> 2) What kind of engineers build and operate them.
>

## Quick Start

1. **Setup**: Fork repo → Clone locally → Open in VS Code
2. **For each task**: Issue → Branch → Commits → PR → Review → Merge
3. **Start with**: [Task 1: Pick a product](#1-pick-a-product-and-study-its-architecture)

### Time estimates

| Section | Time |
|---------|------|
| [Setup](#lab-setup) | ~30 min |
| [Task 1](#1-pick-a-product-and-study-its-architecture) | ~30–40 min |
| [Task 2](#2-tech-roles-involved-in-the-selected-product) | ~20–30 min |
| [Task 3](#3-my-tech-skills-and-the-market-roadmapsh-and-job-postings) | ~30–40 min |
| **Total** | **~2–2.5 hours** |

---

## Table of contents

**Overview**

- [Learning Outcomes](#learning-outcomes)
- [Tasks overview](#tasks-overview)
- [Repo structure](#repo-structure)

**Before you start**

- [Lab setup](#lab-setup)
- [Submission checklist](#submission-checklist)
- [Procedure for each task](#procedure-for-each-task)
- [PR reviews](#pr-reviews)

**Tasks**

- [Required tasks](#required-tasks)
  - [1. Pick a product and study its architecture](#1-pick-a-product-and-study-its-architecture) ⬅️ Start here
  - [2. Tech roles involved in the selected product](#2-tech-roles-involved-in-the-selected-product)
  - [3. My tech skills and the market](#3-my-tech-skills-and-the-market-roadmapsh-and-job-postings)
- [Optional tasks](#optional-tasks)
- [Homework](#homework)

## Learning Outcomes

By the end of this lab you should be able to:

- Use GitHub to structure your work and collaborate with peers (issues, branches, pull requests, and reviews).
- Explain the basic architecture of a real-world digital product in terms of components, data flow, deployment, and tech roles.
- Reflect on your career in tech, examine your current skillset, and plan for the future.

## Tasks overview

To complete this lab, you will need to:

- Set up your `GitHub` account and this lab's repo.
- Pick an existing digital product.
- Sketch its architecture: components, data flow, deployment.
- Map components to tech roles and skills using real job postings and `roadmap.sh`.
- Practice using GitHub issues, branches and pull requests (PRs) to organize your work in a repository (repo) and get feedback from peers.

This and all other lab assignments will simulate real-life engineering practices:

- Follow processes;
- Communicate via issues/PRs;
- Keep the work reviewable;
- Write acceptance criteria;
- Write clear commit messages.

## Repo structure

- [`.github/ISSUE_TEMPLATE/01-task.yml`](./.github/ISSUE_TEMPLATE/01-task.yml) - an issue form for a task.
- [`.github/pull_request_template.md`](./.github/pull_request_template.md) - a template for PRs.
- [`./docs/diagrams`](./docs/diagrams) - diagrams of the product's architecture.
- [`./.vscode/settings.json`](./.vscode/settings.json) - `VS Code` settings.
- [`./.vscode/extensions.json`](./.vscode/extensions.json) - recommended `VS Code` extensions.
- [`./Appendix.md`](./Appendix.md) - Additional info.

---

## Lab setup

### Set up a fork

1. Create a `GitHub` account.
2. Fork this repo to your `GitHub` account and make it public.
3. Continue your work in the forked repo.
4. In the repo -> `Settings` -> `General` -> `Features`, enable `Issues`.
5. <details> <summary> (Optional) Create a label for tasks (click to expand).</summary>

   In the repo -> `Issues` -> `Labels`, create a new label:
   1. Click `New label`.
   2. Name: `task`.
   3. Click `Create label`.

   </details>

6. <details> <summary>(Optional) Protect your <code>main</code> branch (click to expand).</summary>

   In the repo -> `Settings` -> `Code and automation` -> `Add branch ruleset`:
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
  
  </details>

### Add a classmate as a collaborator

1. In the repo `Settings` -> `Collaborators` -> `Add people`, add a classmate as a collaborator.
2. Make sure your collaborator have accepted the invitation sent to their email.

### Set up your local tools

1. (If needed) On your computer, configure [`git`](https://git-scm.com/):

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your@email"
    ```

2. <details> <summary> (Optional) Learn more about <code>Git</code> (click to expand).</summary>

   - [How Git Works: Explained in 4 Minutes](https://www.youtube.com/watch?v=e9lnsKot_SQ)
   - [Git MERGE vs REBASE: Everything You Need to Know](https://www.youtube.com/watch?v=0chZFIZLR_0)

   </details>

3. Install [`VS Code`](https://code.visualstudio.com/). This is our code editor of choice that we'll use in this course.

4. <details> <summary> Skim <code>VS Code</code> docs (click to open). </summary>

    - [`Basic Layout`](https://code.visualstudio.com/docs/getstarted/userinterface#_basic-layout) - Basic UI elements in `VS Code`.
    - `Activity Bar`, `Status Bar` (see [`Basic Layout`](https://code.visualstudio.com/docs/getstarted/userinterface#_basic-layout)) - Menus of extensions;
    - `Command Palette` ([docs 1](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette), [docs 2](https://code.visualstudio.com/docs/getstarted/getting-started#_access-commands-with-the-command-palette)) - How to use editor commands;

      To run a command, open `Command Palette`, type the command, select an appropriate command, press `Enter`.
    - [`Terminal`](https://code.visualstudio.com/docs/terminal/getting-started) - How to run terminal commands inside `VS Code`;
    - [`Source Control`](https://code.visualstudio.com/docs/sourcecontrol/overview) - How to use `Git` via `VS Code` UI;
    - [`Extension Marketplace`](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace) - How to install extensions;
    - [`Custom Layout`](https://code.visualstudio.com/docs/configure/custom-layout) - E.g., move the `Primary Side Bar` to the right so that it doesn't move your code whenever it opens;
    - [Keyboard shortcuts](https://code.visualstudio.com/docs/configure/keybindings#_keyboard-shortcuts-reference).
  
   </details>

5. Enable:
    - [`files.autoSave`](https://code.visualstudio.com/docs/editing/codebasics#_save-auto-save) - to not lose your work if VS Code closes;
    - [`editor.formatOnSave`](https://code.visualstudio.com/docs/editing/codebasics#_formatting) - to keep your code formatted;
    - Force saving and hence formatting by clicking `Ctrl + S` (or `Cmd + S` on `macOS`).

### Open the repository on your machine

1. On your computer, create a directory `software-engineering-toolkit`.
2. In that directory, clone the lab repo.

    ```bash
    git clone https://github.com/<your-username>/lab-01-market-product-and-git
    ```

3. Open the repo in `VS Code`.

    ```bash
    cd software-engineering-toolkit
    code lab-01-market-product-and-git
    ```

### Set up `VS Code` extensions

1. Install the recommended `VS Code` extensions (listed in [`./.vscode/extensions.json`](./.vscode/extensions.json)) when `VS Code` suggests to install them.
2. Sign in to accounts.
    In the `Activity Bar`:
    1. Click `Accounts`
    2. Click `Sign in with GitHub ...`
    3. Repeat for the remaining extensions if there any.

3. <details><summary> (Optional) Check <code>GitLens</code> (click to expand).</summary>

    In the `Status Bar`:

    1. Click `Visualize commits on the Commit Graph`.
    2. Make sure you can see the commit graph.

    In the `Activity Bar`:

    1. Click `Source Control`.
    2. Click `GitLens` in the opened `Primary Side Bar` to open the `GitLens` panel.
    3. In the `GitLens` panel, click `Remotes`.
    4. Make sure `origin` points to your repo URL.
    5. In the `GitLens` panel, click `Commits`.
    6. Make sure you can see commits on the current branch.

    Learn more about [`GitLens` features](https://help.gitkraken.com/gitlens/gitlens-features/).
  
   </details>

4. <details><summary> (Optional) Set up a free <a href="https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-patterns/coding-agents.html">coding agent</a> to help you with the lab (click to expand).</summary>

    You may use any coding agent with any model. `OpenRouter` provides [free models](https://openrouter.ai/collections/free-models).

    Here's how to use `Copilot Chat` with free [`Qwen3 Coder`](https://github.com/QwenLM/Qwen3-Coder):

    1. Create an account at <https://chat.qwen.ai>.
    2. [Install](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_browse-for-extensions) the `github.copilot-chat` and `denizhandaklr.vscode-qwen-copilot` extensions.
    3. Open [`Command Palette`](https://code.visualstudio.com/docs/getstarted/getting-started#_access-commands-with-the-command-palette), type `Qwen Copilot: Authenticate`, press `Enter`.
    4. Complete the authentication procedure.
    5. Open `Command Palette`, run `Chat: Manage Language Models`.
    6. Double click `Qwen 3 Coder Plus` to make the model visible.
    7. In `Command Palette`, run `Chat: Open Chat`.
    8. In the `Chat`, click `Auto` (`Pick Model`) and then click `Qwen 3 Coder Plus`.

  </details>

### Skim the lab description

1. Skim this `README.md` file once so you know what’s coming.

---

## Submission checklist

By the end of the lab:

- Make sure that each task that you have completed has a corresponding issue linked to a PR.
- Close the issues for which all related activities are done.
- Show your progress to the TA as your proceed with the lab. TA will share a link to the table to mark the status of your tasks.

---

## Procedure for each task

> [!NOTE]
> This procedure is based on the [`GitHub flow`](https://docs.github.com/en/get-started/using-github/github-flow).

```text
┌───────┐    ┌────────┐    ┌─────────┐    ┌────┐    ┌────────┐    ┌───────┐
│ Issue │ →  │ Branch │ →  │ Commits │ →  │ PR │ →  │ Review │ →  │ Merge │
└───────┘    └────────┘    └─────────┘    └────┘    └────────┘    └───────┘
```

1. [Create](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue) a `GitHub` issue in your forked repo using the `Lab Task` [issue form](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository#creating-issue-forms).
2. Create a new branch for the issue via [`GitHub`](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-a-branch-for-an-issue) or via `git checkout -b <branch-name>`.
3. <details><summary> Make <a href="https://smartprogramming.in/tutorials/git-and-github/git-commit">commits</a> to that branch to complete the task (click to expand).</summary>

     - Commit messages must follow the [`Conventional Commits`](https://www.conventionalcommits.org/en/v1.0.0/) format.
     - Commit to the branch using one of these approaches:
       1. Using `VS Code` (see [docs](https://code.visualstudio.com/docs/sourcecontrol/staging-commits)): `Activity Bar` -> `Source Control` -> Click a file -> Select lines in the editor -> Right mouse click the selected lines -> Click `Stage Selected Ranges` -> Write a commit message -> Click `Commit`.
       2. Using a terminal (adds all changes in these files to the staging area):

          ```console
          git add <file 1> <file 2> ... <file n>
          git commit -m "<message>"
          ```

   </details>

4. Push the branch to your forked repo:

    ```console
    git push -u origin <branch-name>
    ```

5. Create a PR to the `main` branch via [`GitHub`](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) ([tutorial](https://www.geeksforgeeks.org/git/creating-a-pull-request-on-any-public-repository-from-github-using-vs-code/)) or via the [`GitHub Pull Requests` extension](https://code.visualstudio.com/docs/sourcecontrol/github#_pull-requests).
6. Write an appropriate PR description following the PR template.
7. [Link the PR](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) to the issue, e.g. `Closes #<issue number>`.
8. [Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review#requesting-reviews-from-collaborators-and-organization-members) a review of the PR from the collaborator.
9. Get the collaborator comments and address them, e.g., make fixes or ask to clarify the comment.
10. Get the collaborator to approve the PR.
11. Merge the PR to the `main` branch.
12. Close the issue.
13. Delete the branch.

## PR reviews

As a PR reviewer, you must:

- Review the assigned PR.
- Leave at least 2 meaningful comments highlighting [particular lines](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request#adding-comments-to-a-pull-request). It's enough to select line(s), write a comment and click `Comment`.
- Click `Submit review` if you clicked `Start a review` before.
- Approve the PR if you're satisfied with the PR.

As a PR author, you must:

- Reply to comments in a meaningful way, e.g., write “Fixed in d0d5aeb” (`d0d5aeb` being the id of commit where you addressed the comment), ask to clarify the comment, or explain why you disagree.
- Make necessary changes based on the review.

---

## Required tasks

> [!TIP]
> **Start here** after completing the [lab setup](#lab-setup).

You work **independently** on the tasks below in your forked repo.

Follow the [procedure for each task](#procedure-for-each-task).

### 1. Pick a product and study its architecture

⏱️ **~30–40 min**

> [!WARNING]
> System architecture diagrams are a part of the architecture documentation and not the [system architecture](https://github.com/inno-se/the-guide?tab=readme-ov-file#architecture).

1. [ ] Create an issue `[Task] Product & architecture description`.
2. [ ] Learn how to [embed images](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images) into your `Markdown` files.
3. [ ] Pick one product from this list:

    - Yandex Go
    - Telegram
    - Wildberries.ru

    Alternatively, choose another full-stack product with at least a million users. In that case, you'll have to [visualize the architecture](./Appendix.md#visualize-the-architecture) on your own.

   > [!NOTE]
   > The provided architecture diagrams are based on educated guesses since the products in the list are mostly closed-source.
   > All diagrams were generated via Gemini 3 Pro (free web version) and edited by the course instructors.

4. [ ] Find the directory with the product's architecture diagrams in two formats:
    - `PlantUML` code in `./docs/diagrams/src/<product-name>`.
    - Rendered architecture diagrams in `./docs/diagrams/out/<product-name>`.

    If you chose another project, provide component, deployment, sequence diagrams in two formats in corresponding directories.

5. [ ] Create `./docs/architecture.md` and add the following contents:
    1. [ ] In the `## Product choice` section:
        - [ ] Provide:
          - [ ] The product's name;
          - [ ] A link to the product's website.
          - [ ] A short description of the product (1–2 sentences).
    2. [ ] In the `## Main components` section:
        > [!NOTE]
        > According to the [`C4 model`](https://c4model.com/abstractions/component), a *component* is a grouping of related functionality encapsulated behind a well-defined interface.
        - [ ] Add the product's `Component Diagram.svg`.
        - [ ] Provide a link to the `PlantUML` code for that [component diagram](./Appendix.md#component-diagram).
        - [ ] Select at least 5 main components of the product from the component diagram.
        - [ ] For each selected component, explain in 1–2 sentences what it does.
    3. [ ] In the `## Data flow` section:
        - [ ] Embed the product's `Sequence Diagram.svg`.
        - [ ] Provide a link to the `PlantUML` code for that [sequence diagram](./Appendix.md#sequence-diagram).
        - [ ] Describe what happens when a typical user action occurs (e.g. a user orders a taxi or sends a message).
        - [ ] Mention which components talk to each other and what kind of data they exchange.
    4. [ ] In the `## Deployment` section:
        - [ ] Embed the product's `Deployment Diagram.svg`.
        - [ ] Provide a link to the `PlantUML` code for that [deployment diagram](./Appendix.md#deployment-diagram).
        - [ ] Briefly describe where the components are deployed.
    5. [ ] In the `## Assumptions and Open Questions` section:
        - [ ] List at least two assumptions you made while describing the architecture.
        - [ ] List at least two questions you couldn't answer from public information.

        Examples:
        - Yandex Go: *"I assumed the rider app talks directly to the driver app, but there's probably a server in between."*
        - Telegram: *"I'm not sure if media files are stored on the same servers as text messages."*
        - Wildberries: *"I don't know if payments are processed by Wildberries or by an external payment service."*

---

### 2. Tech roles involved in the selected product

⏱️ **~20–30 min**

1. [ ] Create an issue `[Task] Roles and skills mapping`.
2. [ ] In `./docs/roles-and-skills.md`:

     - [ ] In the `## Components and roles` section:
        - [ ] For each selected component from `architecture.md`, list IT roles that are likely involved in the development and maintenance of that component.
        - [ ] Use a nested list. Example:

          ```markdown  
          - Mobile app
            - Mobile engineer (iOS/Android)
            - QA
            - ...
          - Payment service
            - Back-end engineer
            - DevOps
            - QA
          - ...
          ```

     - [ ] In the `## Roles and responsibilities` section:
        - [ ] Select any five roles.
        - [ ] Consult an LLM or search engine to find out what are the typical responsibilities of these roles (what do people holding these role do?).
        - [ ] For each selected role, briefly describe the responsibilities.
     - [ ] In the `## Common skills across roles` section:
       - [ ] Based on your intuition and some research, list **tech skills that are required for these responsibilities**.

### 3. My tech skills and the market: roadmap.sh and job postings

⏱️ **~30–40 min**

1. [ ] Choose *one* role that seems most interesting to you now.
2. [ ] Go to [`roadmap.sh`](https://roadmap.sh/) and sign up.
3. [ ] Find the roadmap relevant for the role you chose.
4. [ ] In that roadmap, mark the items you already have at least some knowledge in.
5. [ ] In `./docs/roles-and-skills.md`, in the `## My chosen role` section, write:

    ```markdown
    ### Role
    
    <name>
    
    ### Skills I already have
    <!-- from roadmap.sh -->
    - ...
    
    ### Skills I clearly lack
    <!-- 4-5 skills from roadmap.sh that seemed important to have -->
    - ...
    ```

6. [ ] Find **5-7 job postings** for this role on [`HH.ru`](https://hh.ru) or a similar job site.
7. [ ] For each posting, write:
    - Role title.
    - Link to the posting.
    - 3–5 key skills/requirements they mention.
8. [ ] In `./docs/roles-and-skills.md`, in the `## Job market snapshot` section, write:

    ```markdown
    ### Skills that appear in several postings
    <!-- 3-10 skills -->
    - ...
    
    ### Skills specific to a single posting
    <!-- 2-5 skills -->
    - ...

    ```

9. [ ] In `./docs/roles-and-skills.md`, in the `## Personal reflection.` section write 5–10 sentences reflecting on the following questions:
    > [!IMPORTANT]
    > Write this section **without** an LLM.
    > This is your opportunity to think and arrive at useful conclusions.
    - [ ] Which role did I choose and why?
    - [ ] How my skillset compares to the market demands?
    - [ ] Which one or two key skills for this role would I like to develop this semester and why?
    - [ ] What did I learn in this lab?
    - [ ] If you used an AI tool to work on this lab:
      - [ ] What did the tool do well?
      - [ ] What did it do bad?

---

## Optional tasks

> [!NOTE]
> Pick **one** optional task below. Still follow the [procedure for each task](#procedure-for-each-task).

### 1. Merge conflicts & resolution

1. [ ] Create the issue `[Task] Deep dive: Merge conflicts`.
2. [ ] Complete a short learning resource on conflicts:
    - [Learn Git Branching](https://learngitbranching.js.org/) (focus on merge/rebase and conflicts).
3. [ ] Coordinate with your collaborator:
    - [ ] Both of you create PRs that edit the **same lines** in the same file (e.g., the same paragraph in `README.md`).
    - [ ] Merge one PR first.
4. [ ] In the second PR, resolve the conflict (locally or on `GitHub`) and push the fix.
5. [ ] In the PR description, add a short `Conflict resolution note`:
    - [ ] What conflicted (1–2 sentences).
    - [ ] How you resolved it (1–2 sentences).
6. [ ] Merge the PR.

### 2. Add a CI check (`GitHub Actions`)

1. [ ] Create the issue `[Task] Deep dive: Add CI`.
2. [ ] Read [Quickstart for `GitHub Actions`](https://docs.github.com/en/actions/get-started/quickstart).
3. [ ] Add a `GitHub Actions` workflow that runs `markdownlint` on every PR (use `.markdownlint.jsonc`).
4. [ ] Open a PR for the workflow and make sure the checks pass.

### 3. Tag and release notes (shipping mindset)

1. [ ] Create the issue `[Task] Deep dive: Tag and release`.
2. [ ] Read [Managing releases in a repository](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).
3. [ ] Read [Semantic Versioning 2.0.0](https://semver.org/).
4. [ ] Create a tag `v0.1.0` for the current state of your lab repo.
5. [ ] Create a release for `v0.1.0` with notes:
    - [ ] What you built (links to your key docs/PRs).
    - [ ] What you learned (3–5 bullets).
    - [ ] What you would do next (2–3 bullets).

### 4. Skill development strategy (from job market → deep learning → planning)

1. [ ] Create the issue `[Task] Skill development strategy`.
2. [ ] Choose one skill that you decided to improve this semester in [Task 3](#3-my-tech-skills-and-the-market-roadmapsh-and-job-postings).
3. [ ] Create `./docs/skill-development-strategy.md` with:
    - [ ] `## About the skill` (3–5 sentences):
      - [ ] What is this skill?
    - [ ] `## Planning` (5–10 sentences):
      - [ ] Plan to develop this skill during the semester.
      - [ ] Include specific resources, timeline, and milestones.
    - [ ] `## Tracking` (5-10 sentences):
      - [ ] How will I measure my progress in developing the skill?

## Homework

- [ ] Read this [tutorial](https://hackmd.io/@aabounegm/SWP-git) to learn about `Git`, `Github`, and `Git` workflows.
- [ ] Practice on [Learn Git Branching](https://learngitbranching.js.org/) (focus on merge/rebase and conflicts).
- [ ] Read about [`GitHub flow`](https://docs.github.com/en/get-started/using-github/github-flow).
