# Cross-cutting Concepts

In this section, we describe concepts whose implementation concerns many
[building blocks](./05_building_block_view.md) across the stack.

## Fault Tolerance
Noise is deemed on of the most severe limitations of today's quantum computing
devices[^preskill-nisq].
Many methods in Quantum Error Correction, Quantum Error Mitigation and Quantum
Error Suppression have been developed to combat noise with different techniques.
Experts suggest that several methods will likely be combined to achieve optimal
performance.
These methods vary greatly in the mathematical concepts behind them as well as
the environments they can be used.

Within the FullStaQD reference architecture, we identify three typical places
for implementing fault tolerance measures:

1. Some hardware vendors suggest that they want to bundle highly optimised and
   highly device-specific error mitigation and supression techniques within
   their device firmware in the
   [Physical Layer](./05_building_block_view.md#_white_box_phys_layer).
   Such measures would effectively be hidden in the device such that higher
   layers could treat the quantum device's logical qubits as physical qubits
   with an improved error rate.
2. Researchers often frame Quantum Error Correction as a compilation step that
   maps logical operations to their physical, fault-tolerant implementations.
   Such an approach could be implemented as a compilation pass within the
   [System Layer](./05_building_block_view.md#_white_box_sys_layer)'s Compiler.
   As the Compiler can access figures of merit from its compilation target,
   QEC compilation passes can implement their mapping while respecting the
   physical device's topology and fidelities.
3. Some Quantum Error Suppression techniques are highly application-specific and
   could be implemented along with the Use Case implementation in the
   [Application Layer](./05_building_block_view.md#_white_box_app_layer).

[^preskill-nisq]: Preskill, J. [Quantum Computing in the NISQ era and beyond](https://quantum-journal.org/papers/q-2018-08-06-79/). Quantum 2, 79 (2018).

## Monitoring
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
