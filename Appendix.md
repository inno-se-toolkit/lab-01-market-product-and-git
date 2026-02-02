# Appendix

## Architectural views

### Component diagram

This is a *static view* of the architecture. It doesn't show how the system works, but rather what components it has and how they are connected.

We use `PlantUML` [component diagrams](https://plantuml.com/component-diagram).

"Balls" (circle) are *provided interfaces*, "sockets" (open ring) are *required interfaces* (see [explanation](https://stackoverflow.com/a/78941132), [how to draw them](https://stackoverflow.com/questions/55077828/using-required-provided-interfaces-in-component-diagrams-plantuml/57134601#57134601)).

Learn more about the component diagrams on [wiki](https://en.wikipedia.org/wiki/Component_diagram).

### Sequence diagram

This is a *dynamic view* of the architecture. It shows how the system works by showing the sequence of interactions between components.

We use `PlantUML` [sequence diagrams](https://plantuml.com/sequence-diagram).

[`Mermaid`](#visualize-the-architecture---mermaid) also [supports](https://mermaid.js.org/syntax/sequenceDiagram.html) sequence diagrams.

Learn more about the sequence diagrams on [wiki](https://en.wikipedia.org/wiki/Sequence_diagram).

### Deployment diagram

This is a *static view* of the architecture. It shows how the system is deployed, i.e., what hardware and software components are used and how they are connected.

We use `PlantUML` [deployment diagrams](https://plantuml.com/deployment-diagram).

[`Mermaid`](#visualize-the-architecture---mermaid) supports [Architecture](https://mermaid.js.org/syntax/architecture.html) diagrams and [C4](https://mermaid.js.org/syntax/c4.html#c4-deployment-diagram-c4deployment) deployment diagrams.

Some [other tools](#visualize-the-architecture---other-tools) also support deployment diagrams.

Learn more about the deployment diagrams on [wiki](https://en.wikipedia.org/wiki/Deployment_diagram).

## Visualize the architecture

> [!NOTE]
> Visualizing the architecture is not the same as designing the architecture.
>
> To design the architecture of a system, you need to consider the architectural drivers.

### Visualize the architecture - `Draw.io`

You can *prototype* diagrams in `./docs/diagrams/prototype` via the [`hediet.vscode-drawio`](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) extension ([example](./docs/diagrams/prototype/example.drawio.svg)).

However, it's not a good idea to version control images because you can't conveniently visualize their diffs and therefore can't track changes well.

Therefore, you must use the ["diagrams as code"](https://simmering.dev/blog/diagrams/) approach and eventually switch to one of the following approaches.

### Visualize the architecture - `PlantUML`

[`PlantUML`](https://plantuml.com/) supports all the diagrams we need. Therefore, we use it to visualize the architecture.

If you want to preview the `PlantUML` diagrams in `VS Code`, follow these steps:

- [ ] Install the [`jebbs.plantuml`](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) `VS Code` extension.
- [ ] Install [`Docker`](https://docs.docker.com/get-started/get-docker/).
- [ ] Run in the terminal `docker run --name plantuml-server -d -p 48080:8080 plantuml/plantuml-server:jetty` to start a `PlantUML` server.
- [ ] Open the `PlantUML` server in the browser at `http://localhost:48080` to make sure it works.
- [ ] In `VS Code`, in the `./docs/diagrams/src/` directory, open a `PlantUML` file with the `.puml` extension.
- [ ] Click the `Preview Current Diagram` icon.

    The extension should connect to the `PlantUML` server and render the diagram.

    The `48080` port is already set in [`./.vscode/settings.json`](./.vscode/settings.json).

- [ ] Write the `PlantUML` code in `./docs/diagrams/src/` and render the diagrams to `SVG` in `./docs/diagrams/out/` using the `jebbs.plantuml` extension. These directories are already set in [`./.vscode/settings.json`](./.vscode/settings.json)..
- [ ] To render diagrams to SVG, open the [`Command Palette`](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette), write `PlantUML: Export Workspace Diagrams`, and choose `svg`.
- [ ] [Embed](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) the rendered images into your `Markdown` file.

### Visualize the architecture - `Mermaid`

You can write [`Mermaid`](https://mermaid.js.org/) code in `Markdown` files in code blocks with the `mermaid` language tag (see [docs](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-mermaid-diagrams)).

### Visualize the architecture - other tools

Other tools that implement the "diagrams as code" approach are:

- [`Structurizr`](https://structurizr.com/)
- [`D2`](https://d2lang.com/)
- [`LikeC4`](https://github.com/likec4/likec4) etc.
