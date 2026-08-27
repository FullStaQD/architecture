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
todo

## Metering
todo

## Authentification
todo
