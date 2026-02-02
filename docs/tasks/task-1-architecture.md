# Task 1: Pick a Product and Study Its Architecture

**Time:** ~25-30 min

**Purpose:** Understand how a real software product is structured by examining its components, data flow, and deployment.

> [!IMPORTANT]
> You and your partner must pick **different products**. This way, during reviews, you'll learn about each other's products.

## Context

Imagine you're considering joining one of these product teams. Before you decide, you want to understand what the product does and how it's built.

## Available Products

Choose one:

- **Yandex Go** - Ride-hailing and delivery service
- **Telegram** - Messaging platform
- **Wildberries** - E-commerce marketplace

Or choose another full-stack product with at least a million users (you'll need to create the diagrams yourself - see [Appendix](../../Appendix.md#visualize-the-architecture)).

> [!NOTE]
> The provided architecture diagrams are educated guesses since these products are closed-source. They were generated with AI and edited by instructors.

## Steps

### 1. Create an Issue

Title: `[Task 1] Product & architecture description`

### 2. Find the Diagrams

Locate your product's diagrams:
- **PlantUML source:** `./docs/diagrams/src/<product-name>/`
- **Rendered SVGs:** `./docs/diagrams/out/<product-name>/`

### 3. Create `docs/architecture.md`

Create the file and add the following sections:

#### `## Product Choice`

- Product name
- Link to the product's website
- Short description (1-2 sentences)

#### `## Main Components`

> A *component* is a grouping of related functionality behind a well-defined interface ([C4 model](https://c4model.com/abstractions/component)).

1. Embed the Component Diagram:
   ```markdown
   ![Component Diagram](./diagrams/out/<product>/component-diagram/Component%20Diagram.svg)
   ```
2. Link to the PlantUML source.
3. Select at least **5 main components** from the diagram.
4. For each component, explain what it does (1-2 sentences).

#### `## Data Flow`

1. Embed the Sequence Diagram.
2. Link to the PlantUML source.
3. Describe what happens when a user performs a typical action:
   - Yandex Go: User orders a taxi
   - Telegram: User sends a message
   - Wildberries: User places an order
4. Explain which components communicate and what data they exchange.

#### `## Deployment`

1. Embed the Deployment Diagram.
2. Link to the PlantUML source.
3. Briefly describe where components are deployed (cloud, mobile devices, etc.).

#### `## Assumptions and Open Questions`

List at least:
- **2 assumptions** you made while describing the architecture
- **2 questions** you couldn't answer from public information

Examples:
- *"I assumed the rider app communicates with the driver app through a server, not directly."*
- *"I don't know if media files are stored on the same servers as text messages."*
- *"Unclear whether payments are processed internally or by an external provider."*

### 4. Complete the Git Workflow

1. Commit your changes.
2. Push and create a PR.
3. Request review from your partner.
4. Address feedback and merge.

---

## Acceptance Criteria

- [ ] Issue created
- [ ] `docs/architecture.md` created with all required sections
- [ ] Component, Sequence, and Deployment diagrams embedded
- [ ] At least 5 components described
- [ ] Data flow explained for a user action
- [ ] At least 2 assumptions and 2 open questions listed
- [ ] PR reviewed and merged

## Reviewer Checklist

As a reviewer, verify:

- [ ] Product name, link, and description are present
- [ ] Component diagram is embedded and visible
- [ ] At least 5 components are described (1-2 sentences each)
- [ ] Sequence diagram is embedded
- [ ] Data flow description mentions which components interact
- [ ] Deployment diagram is embedded
- [ ] At least 2 assumptions and 2 open questions listed

**Since you're reviewing a different product than yours:**
- Ask questions if something is unclear - this is valuable feedback!
- Comment on something interesting you learned about this product.

---

**Done!** Proceed to [Task 2: Roles](./task-2-roles.md).
