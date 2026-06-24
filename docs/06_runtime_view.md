# Runtime View {#section-runtime-view}

!!! note "Architecture Note Scenarios"

        - An architecture must work for its use cases
            - Scenarios can be used to test architectural decisions
            - Representative scenario selection is crucial


In their work, Carbonelli et al. examine three specific industrial use cases.
First, they investigate the use of quantum cloud services to solve optimization problems.
Second, they analyze the potential of quantum simulations in the fields of materials science, chemistry, and physics.
As a third aspect, the authors explore embedded quantum computing with regard to non-functional properties.
These three use-cases will be analyzed in this chapter.


## Quantum simulation for material science, chemistry and physics {#_runtime_scenario_1}

This scenario descriebes the how quatum computing can be used for material science, chemistry and physics. 

It has the following specifications:
-  Input: molecule or atom specification
-  Output: ground state energy, excited states, dipole moments, …
-  Used in: material science, battery design, catalyst research, …


<figure markdown="span">
  ![](./images/runtime-view-scenario1-Application-Layer-Downwards.drawio.pdf)
</figure>


### Application Layer (Downwards)

1. Simulation App:
    - This is the Entry Point for the scenario and this runtime. 

2. Hartree-Fock:
    - Using molecular geometry as an input, this process performs a transformation to estimate a molecule's ground-state energy and determine its molecular orbitals. 
    It outputs these orbitals, one- and two-electron integrals, and the classical ground-state energy, serving as a starting point for quantum algorithms.

3. Hamiltonian Formulator:
    - Using the one- and two-electron integrals as an input, this process formulates the system quantum-mechanically through second quantization. 
    It outputs a fermionic Hamiltonian expressed in terms of electron creation and annihilation operators, going from a classical approximation to a quantum representation.

4. Jordan-Wigner:
    - Using the fermionic Hamiltonian as input, this process translates the system into the language of quantum computing by mathematically mapping electrons onto qubits. 
    It outputs a qubit Hamiltonian, structuring the quantum system for execution on a quantum circuit.

5. VQE (Variational Quantum Eigensolver): 
    - Using a qubit Hamiltonian, a parameterized quantum circuit and a classical optimization algorithm, this hybrid process uses a quantum computer to measure energy states while a classical computer iteratively adjusts parameters to find the true ground state. 
    It outputs the calculated ground-state energy of the molecule and the optimal parameters for the circuit.

6. VQE Program Generator
    - Using the number of qubits, system properties, and a chosen strategy, this process constructs a parameterize quantum circuit to act as a trial wavefunction for the VQE algorithm and then outputs a parameterized circuit.

7. Logical Optimisation:
    - Using the unoptimized quantum circuit as input, this process optimizes the design by removing redundant operations and adapting it to the physical limitations of quantum hardware. 
    It outputs a shorter, optimized circuit with fewer gates, delivering a hardware-ready architecture.

### System Layer - Downwards

The transpilation process can be broken down in six different steps;

8. Initialization Stage
    - As the first stage in the process, it accepts a abstract circuit defined gates and performs high-level logical optimizations. 
    It breaks down complex multi-qubit operations, ultimately outputting a simplified abstract circuit that contains only one- and two-qubit operations.

9. Layout Stage
    - This stage maps the input circuit's virtual qubits to the target's physical hardware qubits, expanding the circuit to match the hardware's overall size. 
    While it does not guarantee continuous connectivity or direct execution validity, finding an optimal initial layout is a importnant, computationally expensive step that minimizes error rates and reduces the need for subsequent routing.

7. Routing Stage
    - This adapts a logical quantum circuit to fit the physical connectivity constraints of a specific quantum chip's topology. 
    Taking the original circuit and hardware coupling map as inputs, it outputs a physically compatible circuit by inserting SWAP gates to move information between previously unconnected qubits.

10. Translation Stage
    - This stage rewrites all circuit operations into the specific native gates supported by the target hardware's Instruction Set Architecture (ISA). 

11. Optimization Stage 
    - This stage executes low-level, hardware-aware refinements on circuits that are already compatible with the target's Instruction Set Architecture (ISA).

12. Scheduling Stage 
    - The scheduling stage receives an ISA-compatible circuit and inserts explicit delay instructions to accurately reflect qubit idle periods and hardware timing constraints.
    It ensures the final output remains ISA-compatible while updating start-time metadata and optionally applying walltime-sensitive transformations.

### Physical Layer 

14. Superconducting Device and Firmware:
    - Using digital hardware instructions and pulse definitions, this process converts these commands into physical signals to control operations on the quantum chip. 
    It outputs a Microwave Signal List directly to the quantum hardware, translating digital instructions into executable physical actions.
    
15. Molecule Laser:
    - Using the Microwave Signal List as input, this hardware component executes the physical quantum operations by responding to control signals and manipulating the states of the qubits. 
    It outputs a physical feedback signal to the sensor, when the operation or measurement is complete.

16. Energy Sensor:
    - Using the Status Flag from the quantum hardware as input, this readout process measures the final physical state of the qubits and translates these quantum states back into classical information. 
    It outputs classical measurement data, such as bitstrings or calculated energy values, sending it back to the classical runtime for further processing and optimization.

### System Layer - Upwards 

17. Transpilation
    - Using the Qubit energy level, it translates the energy levels to an expactation value.

### Application Layer - Upwards 

18. COBYLA
    - Using the measured expectation values it optimizes the costfunction by modeling it with linear approximations to avoid noisy quantum derivative calculations.
    It outputs updated parameters to refine the circuit in the next iteration.

19. VQE Program Generator
    - Using the number of qubits, system properties, and a chosen strategy, this process constructs a parameterize quantum circuit to act as a trial wavefunction for the VQE algorithm. 
    It then outputs a parameterized circuit for the next iteration or returns the final results. 

20. Zero Noise Extrapolation
    - It intentionally amplifying the hardware noise of a circuit across multiple scale factors and fitting a classical curve to the results to estimate the ideal state. 
    It takes a series of noisy expectation values measured at these elevated noise levels as input and outputs a single, error-mitigated value that approximates the true, noiseless computation.

21. Simulation App
    - This is the Exit Point for the scenario.


## Quantum Cloud Services {#_runtime_scenario_2}
Quantum Cloud Services for optimisation problems

<figure markdown="span">
  ![](./images/RuntimeView-scenario2.png)
</figure>


- Solving NP-hard combinatorial optimisation problems
- Input: Max-Cut instance
- Output: Solution or approximation to the Max-Cut instance

- Use cases:
    - Flight-gate assignment in airports
    - Electronic Design Automation
    - Trajectory optimization in air traffic
    - Paint-shop scheduling
    - Planning problems in highly individualised mass production


Variieren des system layer in additon to scenario 1 ...

## Embedded QPU {#_runtime_scenario_3}
Embedded quantum computing for non-functional properties

<figure markdown="span">
  ![](./images/RuntimeView-scenario3.png)
</figure>