# Cross-cutting Concepts

In this section, we describe concepts whose implementation concerns many
[building blocks](./05_building_block_view.md) across the stack.

## Fault Tolerance
Noise is deemed on of the most severe limitations of today's quantum computing
devices[^preskill-nisq].
Many methods in Quantum Error Correction, Quantum Error Mitigation and Quantum
Error Suppression have been developed to reduce noise with different techniques.
Experts suggest that several methods will likely be combined to achieve optimal
performance. <!-- TODO cite interview study or other source -->
These methods vary greatly in the mathematical concepts behind them as well as
the environments they can be used.

Within the FullStaQD reference architecture, we identify three typical places
for implementing fault tolerance measures:

1. **Firmware-bundled:**
   Some hardware vendors suggest that they want to bundle highly optimised and
   highly device-specific error correction and supression techniques within
   their device firmware (see
   [Physical Layer](./05_building_block_view.md#_white_box_phys_layer)).
   Such measures would effectively be hidden in the device such that higher
   layers could treat the quantum device's logical qubits as physical qubits
   with an improved error rate.
2. **Compilation:**
   Researchers often frame Quantum Error Correction as a compilation step that
   maps logical operations to their physical, fault-tolerant implementations.
   Such an approach could be implemented as a compilation pass within the
   [System Layer](./05_building_block_view.md#_white_box_sys_layer)'s Compiler.
   As the Compiler can access figures of merit from its compilation target,
   QEC compilation passes can implement their mapping while respecting the
   physical device's topology and fidelities.
   <p>
   Similarly, some Quantum Error Suppression and Quantum Error Mitigation
   techniques could be injected into the program through a compilation pass.
   </p>
3. **Application-specific:**
   Some Quantum Error Mitigation and Quantum Error Correction techniques are
   highly application-specific and could be implemented along with the Use Case
   implementation in the.
   Common primitives and utilities for implementing these techniques can also be
   part of Quantum SDKs and related libaries
   (see [Application Layer](./05_building_block_view.md#_white_box_app_layer)).

[^preskill-nisq]: Preskill, J. [Quantum Computing in the NISQ era and beyond](https://quantum-journal.org/papers/q-2018-08-06-79/). Quantum 2, 79 (2018).

## Monitoring {#monitoring}
Large-scale deployments of quantum software systems will require extensive
monitoring to allow operators to ensure smooth operation of these systems.
Such monitoring will be most useful when it captures montoring data (such as
logs and metrics) across all components that run live during the execution of
quantum software workloads, and when individual datapoints can be traced to
the corresponding workloads.

Monitoring will require a separate data collection building block that all
layers can access.
For the extraction of logs and metrics, two common patterns are to be expected:

* Data-producing components can implement routines that directly send metrics
  and logs to the data collection component.
  This would make such components depend on the data collection interface, which
  is only likely for tighly integrated systems or when a common data collection
  interface emerges.
* Lightweight wrapper components can extract logs and metrics from individual
  data-producing components.
  This approach introduces some overhead but decouples the data collection
  component from the rest of the stack.
<!-- TODO: cite common pattern for data extraction from classical monitoring software -->

Besides data collection, there will need to be an interface that allows
operators to access monitoring data.
Such a component could be a standalone tool, or it could be bundled with
integration tooling in the
[Application Layer](./05_building_block_view.md#_white_box_app_layer) or the
data collection component itself. 

## Authentication and Metering
In cloud and HPC environments where multiple users can submit workloads, access
to resources needs to be controlled through an authentication mechanism and
resource usage must be recorded to enable billing or budgeting.

!!! warning "Work in Progress"

    This cross-cutting concept and its influence on the reference architecture
    is currently being investigated as part of the FullStaQD project.
    More detailed guidance on how to implement Authentication and Metering in
    Quantum Software Systems will follow in a future release of this
    documentation.

## Design and Development Support Tooling {#design-and-development-support-tooling}
Some quantum software tools are not directly part of the implementation of
quantum software stacks but instead aim to support their design and development
process.
A key characteristic of these tools is that they are not fully automated but
instead support a developer's implementation decisions.
Furthermore, many of these tools go across the boundaries of individual layers
to enable a holistic treatment of the quantum software stack.

Typical examples for Design and Development Support Tooling include:

- Low-code tools for assembling quantum applications (e.g. the
  [ProvideQ Toolbox](https://provideq.kit.edu)'s visual problem decomposition
  tools,
  [Kipu Quantum Workflows](https://docs.hub.kipu-quantum.com/services/workflow/air-traffic-tutorial)
  based on [CAMUNDA](https://docs.camunda.io), or the
  [QuaST Decision Tree](https://www.quast-decisiontree.com/tree))
- Agentic AI Tools supporting the the choice of components and algorithms, or
  supporting the implementation of business use cases with quantum algorithms
  (e.g. Kipu Quantum's [Paqari AI Agent](https://kipu-quantum.com/paqari))
- Integrated Development Environments (IDEs) (e.g. the
  [IBM Quantum Composer](https://quantum.cloud.ibm.com/composer) for editing
  OpenQASM and Qiskit programs)
- Visualisation tools for inspecting the results of quantum computations,
  intermediary results or [monitoring data](#monitoring)
- Testing, benchmarking and verification tools

??? question "Aren't compilers development tools too?"

    Compilers are traditionally considered development tools, used to compile
    programs once for a few common compilation targets (e.g. standard OS's, x86
    and ARM instruction sets) and then not needed for the execution anymore.
    In quantum computing, they take up a slightly different role as compilation
    targets are much more nuanced since more different hardware modalities are
    available.
    Furthermore, some researchers <!-- TODO cite interview study once available -->
    suggest that compilation should also adapt the compiled program to the
    current state of the hardware, informed by drift and fidelity metrics.
    Therefore, compilers cannot be separated from the application, as it is the
    case for the design and development tools discussed in this section.

    Another reason for the different treatment of compilers lies in their degree
    of automation.
    Compilers should be able to run without further user input whereas our
    Design and Development Support Tooling merely supports the developer.

??? info "Rationale"

    The rationale behind making Design and Development Support Tooling a
    cross-cutting concern is explained in the
    [architectural decisions](./architecture-decisions.md#2-separate-devtools)
    section.
