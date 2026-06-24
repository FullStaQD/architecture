# Context and Scope {#section-context-and-scope}

Quantum software systems can be any system that involves tasks solved on quantum
computers.
As this reference architecture remains highly general, we characterise typical
properties of the context of such systems rather than one specific context.

## Business Context {#_business_context}

<figure markdown="span">
  ![](./images/Business-Context.excalidraw.png)
</figure>

* The **Quantum Software System** is at the heart of the above diagram.
  Its [internal structure](./05_building_block_view.md),
  [behaviour](./06_runtime_view.md) and [deployment](./07_deployment_view.md)
  are characterised in the respective sections.
* Most quantum software systems control physical **Quantum Hardware** (although
  some can use simulators too).
  The protocols for controlling quantum hardware are highly vendor-specific but
  the corresponding drivers and/or firmware are part of the quantum software
  system (see [physical layer](./05_building_block_view.md#physical-layer)).
  Quantum hardware is made available by hardware vendors (either on-premise or
  through cloud access).
* **External IT Systems** such as business applications can call quantum
  software systems, for example with specific computation tasks.
  The use of quantum algorithms, problem transformations and circuit
  formulations is part of application-specific components which are part of the
  quantum software system
  (see [application layer](./05_building_block_view.md)).
  While the concrete protocol used for the external system to call quantum
  software systems is highly application-specific, the aforementioned
  application-specific component can implement such protocols.
  <!--
    TODO: link workflow tooling at a means to alleviate this issue.
    TODO: consider making HPC systems an explicit external system in the
          diagram.
  -->
* **Quantum developers** build and compose the internal components of quantum
  software systems.
  Quantum developers include quantum and classical software engineers and
  architects but also quantum theorists like quantum algorithm experts or
  quantum information theory experts.

## Technical Context {#_technical_context}

**\<Diagram or Table\>**

**\<optionally: Explanation of technical interfaces\>**

**\<Mapping Input/Output to Channels\>**
