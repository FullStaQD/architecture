# Runtime View {#section-runtime-view}
The runtime view documents the concrete behaviour and interaction of the building blocks. Based on [Carbonelli et al.'s work](https://link.springer.com/content/pdf/10.1007/978-3-031-64136-7_12.pdf), we demonstrate how typical quantum use cases are represented in the architecture. The demonstration shows one scenario in detail for each use case, starting at the user input, continuing through the execution, and concluding with the return value to the user.
We document these steps through an activity diagram, in which each architecture layer is divided by a swim lane.  We focus on the steps and interfaces during the execution process rather than describing the building blocks in detail.

!!! note "Architecture Note Scenarios"

        - An architecture must work for its use cases
            - Scenarios can be used to test architectural decisions
            - Representative scenario selection is crucial



## Quantum simulation for material science, chemistry and physics {#_runtime_scenario_1}

This scenario describes the how quatum computing can be used for material science, chemistry and physics. 

It has the following specifications:

-  Input: molecule specification
-  Output: ground state energy
-  Used in: material science, battery design, catalyst research, …


  ![](./images/RuntimeView-scenario1.png)

### Application Layer - Downwards

1. Simulation App:
    - The Simulation App is the entry point for this scenario.
    - It takes the molecule specification and passes it down to the Hartree-Fock algorithm

2. Hartree-Fock:
    - The Hartree-Fock algorithm is the first transformation step to get from the molecule input to a quantum ready representation
    - Its input is the molecular geometry in our scenario
    - The output are the electron integrals.

4. Hamiltonian Formulator:
    - The Hamiltonian formulation maps the electron integrals into a fermonic Hamiltonian.

6. Jordan-Wigner:
    - The Jordan-Wigner Transformation allows a qubit representation using a fermonic Hamiltonian and turns it into a spin Hamiltonian, which is equivalent to a set of qubits.
     
8. VQE (Variational Quantum Eigensolver):
    - The VQE Algorithm is a hybrid algorithm, which uses the qubit Hamiltonian to create a parameterised quantum circuit.

9. VQE Program Generator
    - With the parametrised circuit the program generator creates a program for the transpilation pipeline in the system layer.
 
### System Layer - Downwards

The [Qiskit Transpilation Pipeline](https://quantum.cloud.ibm.com/docs/en/guides/transpile) consists of 6 steps:

1. Initialization Stage
    - Using the quantum program from the Application Layer, the transpilation pipeline can start.
    - The first step of the transpilation pipeline is breaking down multi- and custom made qubit- gates into one- or two-qubit operations.
      
2. Layout Stage
    - This stage maps the input circuit's virtual qubits to the target's physical hardware qubits.
    - Ideally, the algorithm maps the qubit that interact the most next to each other. 
    - While it does not guarantee continuous connectivity or direct execution validity, finding an optimal initial layout is a important, computationally expensive step that minimizes error rates and reduces the need for subsequent routing.

3. Routing Stage
    - As described in the step before, a perfect connectivity between the qubits can not always be achieved. Therefore this stage adds additional operations to adapt to these constraints.
    - Using the circuit and hardware topology as inputs, it can create a physically compatible circuit by inserting SWAP gates to move information between previously disconnected qubits.

4. Translation Stage
    - This stage rewrites all previously chosen gates into the specific native gates supported by the target hardware's Instruction Set Architecture (ISA). 

5. Optimization Stage 
    - This stage executes low-level, hardware-aware refinements on circuits that are already compatible with the target's Instruction Set Architecture (ISA) to reduce redundancy.

6. Scheduling Stage 
    - The scheduling stage receives an ISA-compatible circuit and inserts explicit delay instructions to accurately reflect qubit idle periods, hardware timing constraints and to reduce error rate.
    - It ensures the final output remains ISA-compatible while updating start-time metadata and optionally applying walltime-sensitive transformations.

7. Circuit-Command Mapping
    - Using the ISA-compatible circuit, additional information like number of measurements demanded and a translation table, which translated the commands into backend compatible commands, this steps gives a list of operations to the device and firmware of the hardware.

### Physical Layer 

1. Superconducting Device and Firmware:
    - Using digital hardware instructions and pulse definitions, this process converts these commands into physical signals to control operations on the quantum chip. 
    - It outputs a Microwave Signal List directly to the quantum hardware, translating digital instructions into executable physical actions.
    
2. Molecule Laser:
    - The Molecule Laser uses the Microwave Signal List to execute the quantum operations on the physical hardware.
    - When all operations are done, the Molecule Laser sends a status flag to the Energy Sensor

3. Energy Sensor:
    - When the Molecule Laser updated its status, this step measures the qubit energy levels 

### System Layer - Upwards 

7. Transpilation
    - In this step, the qubit energy levels are transformed into an expectation value.
    - To do this, additional backend data is needed to interpret the measured results.

### Application Layer - Upwards 

10. COBYLA
    - COBYLA is a classical optimizer which needs an expectation value as input.
    - It compares the expectation value to the last one (if it exists) and tries to optimize the parameters of the VQE algorithm.
    - After an local optimal solution is found or the maximum of iterations is reached, the classical optimizer terminates
      
11. VQE Program Generator
    - The Program Generator updates the parameters of the COBYLA algorithm and starts the process again.
    - When the classical optimizer terminates, the Program Generator gives the optimal result towards the Error Mitigation Method.
      
12. Zero Noise Extrapolation
    - Zero Noise Extrapolation (ZNE) is a error mitigation method, which can reduce the error rate by using an expectation value and a circuit has input
    - It creates a program to measure a new expectation value with a circuit, which has still the same function but uses more gates. 
    - This process is repeated multiple times and lead towards a noise pattern, which allows to reduce the error rate by extrapolation.
    
13. Simulation App
    - The error-optimized expectation value is given towards the simulation app, which then visualize it as ground state energy for the user.


## Quantum Cloud Services {#_runtime_scenario_2}
In this scenario, we want to show how our architecture behaves and interacts using a NP-hard combinatorial optimisation problem. Since the System and Physical Layer are almost identical to the first scenario, we only document the new building blocks. 

  ![](./images/RuntimeView-scenario2.png)


- Approximating the optimal Max-Cut
- Input: Max-Cut instance
- Output: A cut consisting of a set of edges
  
- Use cases:
    - Flight-gate assignment in airports
    - Electronic Design Automation
    - Trajectory optimization in air traffic
    - Paint-shop scheduling
    - Planning problems in highly individualised mass production

### Application Layer - Downwards
1. Cloud Optimisation Application:
    - Processes the MaxCut problem instance and forwards the information to the QUBO Transformator

2. QUBO Transformator
    - Creates a QUBO, using the information of the Cloud Optimisation Application

3. Ising Transformator
    - Transforms the QUBO into an Ising Hamiltonian

4. Penalty Encoder
   - Checks if the required optimization problem needs a penalty factor and adjusts it.
     
5. QAOA
   - QAOA is a hybrid algorithm which uses tunable parameters.
   - It encodes the Ising Hamiltonian into a quantum circuit
   
6. QAOA Program Generator
    - With the parametrised circuit the program generator creates a program for the transpilation pipeline in the system layer.
 
### System Layer - Downwards
--
1. Noise Suppression
   - Noise Supression reduces the error rate by actively canceling noise using clever pulse timing or add redudancy to detect and fix errors.
   - It takes an optimized circuit and adds the above mentioned operations.
   
   
### Physical Layer - Downwards
-- 
### System Layer - Upwards
-- 
### Application Layer - Upwards
7. SPSA
   - Similar to COBYLA, SPSA is classical optimizer used for optimizing the parameters of the QAOA algorithm. 
   - It updates the parameters and sends them to the QAOA Program Generator, where the program is computed again until the optimizer terminates.
   
## Embedded QPU {#_runtime_scenario_3}
In this scenario, we demonstrate an integration of a quantum processing unit (QPU) into a hybrid safety software system with non-functional properties.

  ![](./images/RuntimeView-scenario3.png)

- Compute the probability of a collision and give it to the executive unit.
- Input: Environment data
- Output: Collision probability

### Application Layer - Downwards
1. Collision Probability App
   - Takes the environment data and forwards the lidar, camera and gps data to the Feature Vector Encoder
   
2. Feature Vector Encoder
   - Encodes a feature vector based on the ionformation of the collision probability app
   
3. Angle Encoder
   - Used the feature vector to create a quantum state, which represents the given information 

4. Quantum Kernel Method
   - The quantum kernel method creates a qiskit program, which can then be forwarded to the system layer
   
### System Layer - Downwards
1. Probabilistic Error Cancellation (PEC_1)
   - Probabilistic Error Cancellation is an error mitigation technique, which reduces the error rate by measuring how much noise each gate creates and creating "ideal", noise-free gates by a combination of the noisy gates. 
   - Run the circuit multiple times, where the gate you replace is randomly chosen.
   
### Physical Layer - Downwards
-- 
### System Layer - Upwards
2. Probabilistic Error Cancellation (PEC_2)
   - In this step, we finish the PEC from before using the combination of all measurements and creating an average.
   
### Application Layer - Upwards
5. Collision Probability App
    - Sends the result to the device/software that requested the job. 
