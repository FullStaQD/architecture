# Quality Requirements {#section-quality-scenarios}
Quality Requirements are a key component in designing an architecture. They describe non-functional properties of a system and must be addressed at an architectural level, as changes for addressing quality requirements can become difficult or expensive afterwards.

This section describes typical quality requirements that are relevant to quantum software systems in general. Although many of these quality requirements have been addressed in the design of the reference architecture, they still need to be taken into account during implementation. Specific implementations may have additional quality requirements, which are not covered. To show the usability of the quality requirements, we also describe and assign example scenarios. As a guideline for this section, we use the [arc42 quality model](https://quality.arc42.org/qualities/).


## Quality Requirement for the instantiation of the reference architecture

### Adaptability  ([SC2,SC4](#example-scenarios-and-their-expectation))
Quantum software systems should be adaptable to different quantum computing hardware.
### Evolvability  ([SC4](#example-scenarios-and-their-expectation))
Due to the fast evolving field of quantum computing, the architecture needs to adapt to changes in its environment, requirements, and implementation technologies in a cost-effective way. These changes could involve new software, algorithms, or hardware technology. 
### Extensibility  ([SC2](#example-scenarios-and-their-expectation))
We want to be able to extend quantum software systems with new compilation passes, problem transformations and applications. 
### Fault tolerance ([SC3](#example-scenarios-and-their-expectation))
Quantum software systems must be resilient to noise on hardware, i.e. quantum programs should produce their intended result even in the presence of noise.
### Integrability  ([SC2](#example-scenarios-and-their-expectation))
The architecture allows software components or systems to be easily integrated into the existing IT infrastructure of stakeholders. It is important to ensure that stakeholders are motivated to use the architecture.
### Latency ([SC3](#example-scenarios-and-their-expectation))
The data transmission latency between components e.G. between quantum device and QEC decoder must be minimised.
### Maintainability  ([SC2,SC4](#example-scenarios-and-their-expectation))
The architecture needs must allow modifications with ease after the baseline is established.
### Modularity  ([SC4](#example-scenarios-and-their-expectation))
The reference architecture needs to limit changes to one component from affecting other components, e.g. exchanging quantum hardware should not affect the application layer.
### Interchangeability ([SC2](#example-scenarios-and-their-expectation))
The reference architecture should be interchangeable, which allows it to substitute one component, part, or element with another of the same type without requiring modifications to the system or loss of functionality. This including different SDKs, compilers and hardware backends.
### Resource utilization ([SC1](#example-scenarios-and-their-expectation))
The quantum compiler should optimise quantum programs in order to minimise the number of required qubits and gates. An inefficient quantum program can lead to high costs for the user.
### Scalability ([SC2](#example-scenarios-and-their-expectation))
Because of the rapidly evolving field of quantum technology, the reference architecture should be scalable in terms of job size, kernel amount, ...
### Testability 
The architecture needs to be capable to enable an objective and feasible test to be designed and performed to determine whether a requirement is met.


## Example Scenarios and their Expectation

### Cost Estimation (SC1)
A stakeholder who received a cost estimate for the execution of their program only has to pay the estimated amount.

### Switching Hardware Vendor (SC2)
A stakeholder should be able to change its hardware vendors without facing high costs.

### Performance should be guaranteed (SC3)
The time and quality of performance when executing a program should be as expected.

### Software Update (SC4)
The maintenance time must be low when the software used for the quantum programme is updated.




