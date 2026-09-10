# Architecture Decisions {#section-design-decisions}
This section documents important, large scale and controversial decisions taken
in the design of the FullStaQD Reference Architecture.
This list excludes smaller-scale or less important decisions which may be
documented in the sections that they apply to.
The goal of this section is to provide the rationale behind major decisions
which will allow re-evaluating them when circumstances change. 

## 001: Use Layered Architecture
We use a three-layered architecture for the top-level decomposition of quantum
software systems.
The rationale behind this decision is documented in
[the building block view's motivation section](./building-block-view.md#motivation).

## 002: Separate Design and Development Support Tooling from the main stack {#2-separate-devtools}
In the FullStaQD Reference Architecture, we have made
[Design and Development Support Tooling][devtools]
a [cross-cutting concept](./cross-cutting-concepts.md).
This decision was driven by two main arguments:

1. Separation of concerns:
   Design and Development Support Tooling is not part of the application being
   developed, it is only used during its development[^compiler-no-devtool].
2. Not layer-specific:
   Design and Development Support Tools exist for purposes on various layers,
   and some tools even cover multiple layers.
 
Alternatively, one could have added one Design and Development Support Tooling
building block to each layer (adding redundancy and cluttering the main stack),
or one could have added a separate high-level building block next to the three
layers (which is conceptually similar to a cross-cutting concern).

[^compiler-no-devtool]:
    See [Design and Development Support Tooling][devtools] for a discussion on
    why the compiler is in the main stack nonetheless.

[devtools]: ./cross-cutting-concepts.md#design-and-development-support-tooling