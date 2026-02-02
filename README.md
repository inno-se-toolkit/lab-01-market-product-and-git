# Lab 01 – Products, Architecture & Roles

Imagine you're choosing which product team to join. In this lab, you'll explore a real software product, understand how it's built, and discover what roles are needed to develop it. By the end, you'll have a clearer picture of where you stand as a tech specialist and what skills to develop.

## Lab Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              LAB 01 FLOW                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Setup ──► Task 0 ──► Task 1 ──► Task 2 ──► Task 3 ──► Optional ──► Done  │
│   (solo)   (git       (product   (roles)    (skills)   (bonus)             │
│             intro)     arch)                                                │
│                              ▲                                              │
│                              │                                              │
│                     Partner reviews throughout                              │
│                     (you review different products)                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Time Estimates

| Task | Time | Description |
|------|------|-------------|
| [Setup](./docs/setup.md) | ~20 min | Fork, clone, VS Code, find a partner |
| [Task 0](./docs/tasks/task-0-git-intro.md) | ~15 min | Learn the git workflow (add your name) |
| [Task 1](./docs/tasks/task-1-architecture.md) | ~25-30 min | Analyze your product's architecture |
| [Task 2](./docs/tasks/task-2-roles.md) | ~20-25 min | Map components to tech roles |
| [Task 3](./docs/tasks/task-3-skills.md) | ~30-40 min | Assess your skills vs. market demands |
| **Total** | **~2 hours** | |

## How This Lab Works

### Pair Work

You'll work with a partner, but each of you picks a **different product** to analyze. This means:
- You become the expert on your product
- Your partner becomes the expert on theirs
- During PR reviews, you learn about each other's products
- Questions like "I don't understand this component" are valuable feedback

### The Git Workflow

Every task follows the same cycle:

```
Issue → Branch → Commits → PR → Review → Merge
```

If you're new to git, [read the workflow guide](./docs/git-workflow.md) before starting.

---

## Getting Started

### 1. Complete Setup

Follow the [setup guide](./docs/setup.md) to:
- Fork and clone the repo
- Find a partner (you must pick **different products**)
- Set up VS Code

### 2. Start with Task 0

[Task 0](./docs/tasks/task-0-git-intro.md) is a guided exercise to learn the git workflow. Complete it before moving on.

---

## Required Tasks

| Task | What You'll Create | Reviewer Focus |
|------|-------------------|----------------|
| [Task 0: Git Intro](./docs/tasks/task-0-git-intro.md) | Add your name to `CONTRIBUTORS.md` | PR format, commit message |
| [Task 1: Architecture](./docs/tasks/task-1-architecture.md) | `docs/architecture.md` with diagrams | Component descriptions, data flow |
| [Task 2: Roles](./docs/tasks/task-2-roles.md) | `docs/roles-and-skills.md` | Role assignments, responsibilities |
| [Task 3: Skills](./docs/tasks/task-3-skills.md) | Skills self-assessment | Genuine reflection, realistic goals |

## Optional Tasks

| Task | What You'll Learn |
|------|------------------|
| [Merge Conflicts](./docs/tasks/optional/conflict-resolution.md) | Handle git conflicts with your partner |
| [CI Check](./docs/tasks/optional/ci-check.md) | Set up GitHub Actions for automated linting |
| [Tag & Release](./docs/tasks/optional/tag-release.md) | Create a release with retrospective notes |
| [Skill Development](./docs/tasks/optional/skill-development.md) | Build a concrete semester learning plan |

---

## Submission Checklist

By the end of the lab:

- [ ] All required tasks have merged PRs
- [ ] Each PR was reviewed by your partner
- [ ] Issues are closed
- [ ] Show progress to TA (they'll share a link to mark your status)

---

## Learning Outcomes

By completing this lab, you'll be able to:

- Use GitHub to structure work and collaborate (issues, branches, PRs, reviews)
- Explain the architecture of a real product (components, data flow, deployment)
- Map system components to tech roles and skills
- Assess your skills against market demands and plan development

---

## Repo Structure

```
.
├── README.md                    # This file
├── CONTRIBUTORS.md              # Add your name here in Task 0
├── Appendix.md                  # Additional technical info
├── docs/
│   ├── setup.md                 # Setup instructions
│   ├── git-workflow.md          # Git workflow explained
│   ├── team-agreement.md        # For conflict resolution task
│   ├── tasks/
│   │   ├── task-0-git-intro.md
│   │   ├── task-1-architecture.md
│   │   ├── task-2-roles.md
│   │   ├── task-3-skills.md
│   │   └── optional/
│   │       ├── conflict-resolution.md
│   │       ├── ci-check.md
│   │       ├── tag-release.md
│   │       └── skill-development.md
│   └── diagrams/
│       ├── src/                 # PlantUML source files
│       └── out/                 # Rendered SVG diagrams
└── .github/
    ├── ISSUE_TEMPLATE/
    └── pull_request_template.md
```

---

## Homework

Practice git on your own time:

- [ ] Read this [git tutorial](https://hackmd.io/@aabounegm/SWP-git) for concepts and workflows
- [ ] Practice on [Learn Git Branching](https://learngitbranching.js.org/) (focus on merge/rebase)
- [ ] Read about [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
