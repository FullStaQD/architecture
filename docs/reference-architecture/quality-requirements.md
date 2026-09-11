# Quality Requirements {#section-quality-scenarios}
Quality Requirements are a key component in designing an architecture. They describe non-functional properties of a system and must be addressed at an architectural level, as changes can become difficult or expensive afterwards.

This section describes typical quality requirements that are relevant to quantum software systems in general. Although many of these quality requirements have been addressed in the design of the reference architecture, they still need to be taken into account during implementation. Specific implementations may have additional quality requirements, which are not covered. As a guideline for this section, we use the [arc42 quality model](https://quality.arc42.org/qualities/).


## Quality Requirement for the instantiation of the reference architecture

### Adaptability
The architecture needs to be capable to be effectively and efficiently adapted for or transferred to different hardware.
### Evolvability 
Due to the fast evolving field of quantum computing, the architecture needs to adapt to changes in its environment, requirements, and implementation technologies in a cost-effective way. These changes could involve new software, algorithms, or hardware technology. 
### Extensibility  
We want to be able to extend quantum software systems with new compilation passes, problem transformations and applications. 
### Fault tolerance 
The architecture needs to have countermeasures to reduce the error rate caused by the noisy quantum hardware, so that it can operate as intended. 
### Integrability  
The architecture allows software components or systems to be easily integrated into the existing IT infrastructure of stakeholders. It is important to ensure that stakeholders are motivated to use the architecture.
### Latency 
The data transmission latency between components e.G. between quantum device and QEC decoder must be minimised.
### Maintainability  
The architecture needs must allow modifications with ease after the baseline is established.
### Modularity  
The reference architecture needs to limit changes to one component from affecting other components, e.g. exchanging quantum hardware should not affect the application layer.
### Interchangeability
 The reference architecture should be interchangeable, which allows it to substitute one component, part, or element with another of the same type without requiring modifications to the system or loss of functionality. This including different SDKs, compilers and hardware backends.
### Resource utilization 
The quantum compiler should optimise quantum programs in order to minimise the number of required qubits and gates. An inefficient quantum program can lead to high costs for the user.
### Scalability  
Because of the rapidly evolving field of quantum technology, the reference architecture should be scalable in terms of job size, kernel amount, ...
### Testability  
The architecture needs to be capable to enable an objective and feasible test to be designed and performed to determine whether a requirement is met.




## Quality Scenarios {#_quality_scenarios}
Scenario ID | Scenario  | Description | 
|-------------| ------------- | ------------- | 
| SC1 | Cost Estimation of Quantum Program  | A Stakeholder pays a certain amount of money per time period for his program and gets information how long his program runs.  |
| SC2 | Running a job   | When a job is run in architecture, the job content must be protected from outside interference to prevent research from being accessed.|
| SC3 | Change Module | After the instantiation a component needs to be changed|
