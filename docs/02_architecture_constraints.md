# Architecture Constraints {#section-architecture-constraints}

This section covers architecture constraints, that is limitations to the design
of quantum software systems and this reference architecture which haven't been
covered as
[functional requirements](./01_introduction_and_goals.md#_requirements_overview)
or [quality goals](./10_quality_requirements.md).
Many of these constraints are set out in the funding goals of the 
[FullStaQD project][fullstaqd]
which funded this reference architecture to strengthen the quantum software
ecosystem through modularisation, compatibility and reuse.

## Open Source
The [FullStaQD project][fullstaqd] seeks to be community-driven and target a
wide adoption within the quantum software community through an open source
model.
This goal is characterised with the following constraints:

* The FullStaQD Reference Architecture must be open source.
  This means that the architecture documentation must be openly available,
  that the project accepts feedback and contributions from the community and
  that the community can participate in its governance.
* An open source reference implementation must be available.

## Commercial Use
The [FullStaQD project][fullstaqd] aims to facilitate the commercialisation of
quantum computing, which yields the following constraint:

* The architecture must allow for proprietary software to be used.
  Reference implementations must allow commercial use and proprietary
  extensions, e.g. through well-defined interfaces or permissive licensing.

## Release Cycle
As one of [FullStaQD][fullstaqd]'s core goals is to provide stable interfaces
but also to keep up with the state of the art, the release cycle is constrained
as follows: 

* A first draft of the Reference Architecture should be released around the
  end of June 2026 to gather feedback from project partners ahead of the first
  full version.
* The first version of the Reference Architecture must be released by the end
  of September 2026 in order to be used by partners within the FullStaQD
  project.
* Further changes to the Reference Architecture should be released
  infrequently but at a fixed cycle.

[fullstaqd]: https://www.digital.iao.fraunhofer.de/en/competences/quantum-computing/FullStaQD.html
