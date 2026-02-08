# Choose a product and study its architecture

**Time:** ~30-40 min

**Purpose:** Understand how a real software product may be structured by examining its components, data flow, and deployment.

**Context:** Imagine you have joined one of these product teams. On your first days, you need to understand what the product does and how it is structured.

- [Steps](#steps)
  - [1. Create an issue](#1-create-an-issue)
  - [2. Choose a product](#2-choose-a-product)
  - [3. Find the diagrams](#3-find-the-diagrams)
  - [4. Create `docs/architecture.md`](#4-create-docsarchitecturemd)
    - [`## Product Choice`](#-product-choice)
    - [`## Main components`](#-main-components)
    - [`## Data flow`](#-data-flow)
    - [`## Deployment`](#-deployment)
    - [`## Assumptions`](#-assumptions)
    - [`## Open questions`](#-open-questions)
- [Acceptance criteria](#acceptance-criteria)

## Steps

### 1. Create an issue

Title: `[Task] Product & architecture description`

### 2. Choose a product

> [!IMPORTANT]
> You and your partner must pick **different products**. This way, during PR reviews, you'll learn about each other's products.

Available products:

- Yandex Go
- Telegram
- Wildberries.ru

Alternatively, choose another full-stack product with at least a million users. In that case, you'll have to [visualize the architecture](../../appendix/visualize-architecture.md) on your own.

### 3. Find the diagrams

> [!IMPORTANT]
> System architecture diagrams represent the system architecture but they are not the [system architecture](https://github.com/inno-se/the-guide?tab=readme-ov-file#architecture).
>
> The provided architecture diagrams are based on educated guesses since the products in the list are mostly closed-source.
> All diagrams were generated via Gemini 3 Pro (free web version) and edited by the course instructors.

1. Find the directory with the product's architecture diagrams in two formats:
    - `PlantUML` code is in [`docs/diagrams/src/<product-name>`](../../../docs/diagrams/src/).
    - Rendered architecture diagrams are in [`docs/diagrams/out/<product-name>`](../../../docs/diagrams/out/).

2. If you chose another project, provide component, deployment, sequence diagrams in two formats in corresponding directories.

### 4. Create `docs/architecture.md`

Create the file and add the following sections:

#### `## Product Choice`

Provide:

- Product name;
- Link to the product's website;
- Short description of the product (1-2 sentences).

#### `## Main components`

> [!NOTE]
>
> According to the [`C4 model`](https://c4model.com/abstractions/component), a *component* is a grouping of related functionality encapsulated behind a well-defined interface.

> [!IMPORTANT]
> Use paths relative to the `docs/architecture.md` file when embedding images and providing links.
>
> Quick intro:
>
> - `.` - the current directory.
> - `..` - parent directory.
> - `./file` - file in the current directory.
> - `../file` - file in the parent directory.

> [!TIP]
> Use auto-completion for paths.
>
> 1. [Open `docs/architecture.md`](../../appendix/vs-code.md#open-a-file).
> 2. Write `![Telegram Component Diagram]()`.
> 3. Inside parentheses `()`, start typing `./`.
> 4. Use suggestions to continue the path.

> [!IMPORTANT]
>
> Replace space in the path with `%20` (see [URL encoding](https://en.wikipedia.org/wiki/Percent-encoding)).

1. Embed the product's `Component Diagram.svg`.

   Example (path provided relative to this file): `![Telegram Component Diagram](../../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)`

   <details><summary>Embedded image example (click to open)</summary>

   ![Telegram Component Diagram](../../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

   </details>

2. Provide a link to the `PlantUML` code for that [component diagram](../../appendix/architectural-views.md#component-diagram).
  
   Example: [Telegram Component Diagram Code](../../../docs/diagrams/src/telegram/component-diagram.puml)

3. Select at least 5 components of the product from the component diagram.

4. For each selected component, explain in 1-2 sentences what it does (as you think).

#### `## Data flow`

1. Embed the product's `Sequence Diagram.svg`.
2. Provide a link to the `PlantUML` code for that [sequence diagram](../../appendix/architectural-views.md#sequence-diagram).
3. Choose a group of actions (a box in the diagram, `group` or `Flow` in the `PlantUML` code).
4. Describe what happens in that group of steps.
5. Mention which components talk to each other and what data they exchange.

#### `## Deployment`

1. Embed the product's `Deployment Diagram.svg`.
2. Provide a link to the `PlantUML` code for that [deployment diagram](../../appendix/architectural-views.md#deployment-diagram).
3. Briefly describe where the components are deployed.

#### `## Assumptions`

List two or more assumptions you made while describing the architecture. Examples:

- Yandex Go: *"I assume the pricing service handles surge pricing calculations based on demand and supply in real-time."*
- Telegram: *"I assume the cloud storage system implements deduplication to optimize storage costs for shared media files."*
- Wildberries: *"I assume the Logistics & Routing service integrates with multiple delivery partners to optimize shipping costs and delivery times"*

#### `## Open questions`

List two or more questions that you couldn't answer based on the openly available information. Examples:

- Yandex Go: *"How does the actual load balancing mechanism work between the microservices in production?"*
- Telegram: *"How does the data flow look like in secret chats?"*
- Wildberries: *"What specific caching strategies are used to handle high traffic during sales events?"*

## Acceptance criteria

- [ ] Issue created
- [ ] `docs/architecture.md` created with all required sections
- [ ] Product name, link, and description are present
- [ ] Component diagram is visible
- [ ] At least 5 components are described (1-2 sentences each)
- [ ] Sequence diagram is visible
- [ ] Data flow description explains which components interact and what data they exchange during a user action
- [ ] Deployment diagram is visible
- [ ] Deployment is briefly described
- [ ] At least 2 assumptions and 2 open questions listed
- [ ] Partner reviewed and approved
- [ ] PR merged
