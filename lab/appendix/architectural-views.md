# Architectural views

## Component diagram

This is a *static view* of the architecture. It doesn't show how the system works, but rather what components it has and how they are connected.

We use `PlantUML` [component diagrams](https://plantuml.com/component-diagram).

"Balls" (circle) are *provided interfaces*, "sockets" (open ring) are *required interfaces* (see [explanation](https://stackoverflow.com/a/78941132), [how to draw them](https://stackoverflow.com/questions/55077828/using-required-provided-interfaces-in-component-diagrams-plantuml/57134601#57134601)).

sadasdasdadasdasdadLearn more about the component diagrams on [wiki](https://en.wikipedia.org/wiki/Component_diagram).

## Sequence diagram

This is a *dynamic view* of the architecture. It shows how the system works by showing the sequence of interactions between components.

We use `PlantUML` [sequence diagrams](https://plantuml.com/sequence-diagram).

[`Mermaid`](./visualize-architecture.md#mermaid) also [supports](https://mermaid.js.org/syntax/sequenceDiagram.html) sequence diagrams.

Learn more about the sequence diagrams on [wiki](https://en.wikipedia.org/wiki/Sequence_diagram).

## Deployment diagram

This is a *static view* of the architecture. It shows how the system is deployed, i.e., what hardware and software components are used and how they are connected.

We use `PlantUML` [deployment diagrams](https://plantuml.com/deployment-diagram).

[`Mermaid`](./visualize-architecture.md#mermaid) supports [Architecture](https://mermaid.js.org/syntax/architecture.html) diagrams and [C4](https://mermaid.js.org/syntax/c4.html#c4-deployment-diagram-c4deployment) deployment diagrams.

Some [other tools](./visualize-architecture.md#other-tools) also support deployment diagrams.

Learn more about the deployment diagrams on [wiki](https://en.wikipedia.org/wiki/Deployment_diagram).
