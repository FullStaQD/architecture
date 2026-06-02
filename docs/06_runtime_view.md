# Runtime View {#section-runtime-view}

- An architecture must work for its use cases
    - Scenarios can be used to test architectural decisions
    - Representative scenario selection is crucial

- Carbonelli et al. study three industrial use cases
    - Quantum cloud services for optimisation problems
    - Quantum simulation for material science, chemistry and physics
    - Embedded quantum computing for non-functional properties

### Application Layer 
- Contains all pre-processing and quantum programming steps
- Using high-level QPLs as interface to system layer is possible
    - However, this abstraction was not necessary in the scenarios considered
    - Ability to construct specific (but hardware-independent) circuits still required
    - High-level QPLs can help typing response data from system layer

### System Layer   
- Mostly contains automated transpilation steps
- Targeting specific hardware architecture via device data retrieval
- Integration and purpose of runtimes still unclear (HPC? Batching?)

### Physical Layer  
- Exchangeable hardware requires hardware-independent interface
    - Pulse sequences insufficient for neutral atom devices (missing shuttling)
    - Future architectures might not use pulses at all
- Unclear whether physical layer handles batching or single circuit executions

### General Observations  
- Quantum Error {Correction, Mitigation, Suppression} present in every layer
    - E.g. Zero Noise Extrapolation in application layer, Probabilistic Error Cancellation in system layer, energy correction in physical layer
- In hybrid systems, the quantum stack only contains the quantum part
    - But: hybrid algorithms are a common pattern in QC and need to be specifiable

## Quantum Cloud Services {#_runtime_scenario_1}
Quantum Cloud Services for optimisation problems

Hybrider Algorithmus gut

TODO: SZENARIO 1 und 2 tauschen 


- Solving NP-hard combinatorial optimisation problems
- Input: Max-Cut instance
- Output: Solution or approximation to the Max-Cut instance

- Use cases:
    - Flight-gate assignment in airports
    - Electronic Design Automation
    - Trajectory optimization in air traffic
    - Paint-shop scheduling
    - Planning problems in highly individualised mass production


## Quantum simulation for material science, chemistry and physics {#_runtime_scenario_2}

-  Input: molecule or atom specification
-  Output: ground state energy, excited states, dipole moments, …
-  Used in: material science, battery design, catalyst research, …


DFT und Hartree-Fock


## Embedded QPU {#_runtime_scenario_3}
Embedded quantum computing for non-functional properties

