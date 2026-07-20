# Quality Requirements {#section-quality-scenarios}
As briefly mentioned in the [Introduction and Goals section](./01_introduction_and_goals.md), there are quality goals, we want to achieve in the FullStaQD reference architecture. 
In this section, we want to describe these goals in more detail and want to present some scenarios, in which they are needed.

## Quality Requirements Overview {#_quality_requirements_overview}
We sort the quality requirements after the [arc42 quality model](https://quality.arc42.org/qualities/). Afterwards, we present the scenarios that can appear in the reference architecture, and we define which quality goal needs to be fulfilled in each scenario. We use "reference architecture" to define the quality goals of the concept and "architecture" for the realization of such an architecture.


## Quality Requirements for the Reference Architecture

### Efficient

| Quality Goal  | Description | Scenario ID |
| ------------- | ------------- |  ------------- | 
| Coherence    | The reference architecture is logically or aesthetically ordered or integrated.  | [SC1](#_quality_scenarios) |
| Latency | The data transmission latency between components e.G. between quantum device and QEC decoder must be minimised.  |  |
| Profitability  | The reference architecture needs to be profitable in an industrial sense.  | |
| Resource utilization | The quantum compiler should optimise quantum programs in order to minimise the number of required qubits and gates.  | [SC6](#_quality_scenarios) |
| Simplicity  | The reference architecture needs to be easy to read, understand, and correctly modify.  | [SC1](#_quality_scenarios) |
| Sustainability  | The reference architecture has to meet the needs of the present without compromising the ability of future generations to meet their own needs. It emphasizes the long-term viability, resilience, and adaptability of the system, considering environmental, economic, and social factors.  | [SC2, SC3, SC8](#_quality_scenarios) |

### Flexible

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Adaptability  | The reference architecture needs to be capable to be effectively and efficiently adapted for or transferred to different hardware. | [SC2, SC3, SC4](#_quality_scenarios) |
| Agility  | The reference architecture can be rapidly changed, if needed.  | [SC2, SC3, SC4, SC5, SC8](#_quality_scenarios)|
| Composability  | The components of the reference architecture should be exchangeable with equivalent components e.G. different hardware backends. |  |
| Configurability | The components of the reference architecture needs to be configurable to support specific needs of the user and be more adaptable. | [SC2, SC3, SC4, SC8](#_quality_scenarios) |
| Evolvability  | The reference architecture needs to adapt to changes in its environment, requirements, and implementation technologies in a cost-effective way.  | [SC2, SC3, SC5, SC8](#_quality_scenarios) |
| Extensibility  | We want to be able to extend quantum software systems with new compilation passes, problem transformations and applications.  | [SC2, SC3, SC4](#_quality_scenarios)  |
| Integrability  | The reference architecture can integrate software components or systems with ease into the existing IT infrastructure of stakeholders.  | [SC2, SC3, SC4, SC8](#_quality_scenarios)|
| Interchangeability | The reference architecture should be interchangeable, which allows it to substitute one component, part, or element with another of the same type without requiring modifications to the system or loss of functionality. | [SC3](#_quality_scenarios) |
| Internationalization  | The reference architecture should be understandable to an international audience. | |
| Scalability  | Because of the rapidly evolving field of quantum technology, the reference architecture should be scalable in terms of job size, kernel amount, .... | [SC8](#_quality_scenarios) |


### Maintainable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Modularity  | The reference architecture needs to limit changes to one component from affecting other components, e.g. exchanging quantum hardware should not affect the application layer. | [SC3](#_quality_scenarios) |
| Updateability  | The reference architecture needs to be capable to efficiently receive, install, and integrate updates, patches, security fixes, and minor enhancements while maintaining system integrity and minimizing service disruption. | [SC5](#_quality_scenarios) |

### Operable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Interoperability  | The reference architecture should be able to work with other products or systems.  | [SC2, SC3, SC4, SC8](#_quality_scenarios) |
| Understandability  | The reference architecture should be presented so that (somebody) can easily comprehend it.   | [SC1](#_quality_scenarios) |


### Reliable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Durability | The reference architecture has to remain useful and meet user needs over a long period, particularly in the face of changing business requirements and technological advancements.  | [SC2, SC3, SC4, SC5, SC8](#_quality_scenarios) |
| Functional suitability  | The reference architecture should provide functions that meet stated and implied needs of intended users when it is used under specified conditions. | |
| Stability  |  The reference architecture remains largely unchanged, when adding new features. | [SC2, SC3, SC4, SC8](#_quality_scenarios)  |

### Usable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |  
| Accessibility  | The reference architecture needs to be usable by people with the widest range of characteristics and capabilities to achieve a specified goal in a specified context of use.  | [SC1](#_quality_scenarios) |
| Discoverability  | The reference architecture needs to be well documented and presented, so that users can find easily new or unknown features, content, and functionalities within a product or system without prior knowledge of their existence.  | [SC1](#_quality_scenarios) |
| Inclusivity  | The reference architecture is intended be utilised by people of various backgrounds  | [SC1](#_quality_scenarios) |
| Intuitiveness  | The reference architectures interface, behavior, and information, enabling immediate understanding and effective use without prior learning or training. | [SC1](#_quality_scenarios) |
| Readability  | The reference architecture needs to be easy to read | [SC1](#_quality_scenarios) |
| Self-descriptiveness  | The reference architecture should be able to present appropriate information, where needed by the user, to make its capabilities and use immediately obvious to the user without excessive interactions with a product or other resources.  | [SC1](#_quality_scenarios) |





## Quality Requirement for the implementation of an Architecture

### Efficient

| Quality Goal  | Description | Scenario ID |
| ------------- | ------------- |  ------------- | 
| Cohesion  | The modules of the architecture belong and work together as intended. | |
| Compliance  | The architecture should obey the rules of state of the art standards.  | |
| Conciseness | The architectures content needs to be clearly but briefly described.  | [SC1](#_quality_scenarios) |
| Effectiveness  | The architecture is able to produce the desired result/output. | |
| Efficiency  | The architecture capable of producing desired results with little or no waste (as of time or materials). | [SC6](#_quality_scenarios)  |
| Performance | The architecture should perform its functions efficiently in the use of of resources and withing a specified time and throughput parameters.  | [SC6](#_quality_scenarios) |


### Flexible

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Elasticity  | The architecture needs to be able to adapt to workload changes, while trying to remain as close to the estimated costs as possible. | [SC6](#_quality_scenarios) |
| Independence  | The architectures components should only perform on task and do not excessively interact with other components. | |

### Maintainable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Analysability  | The architecture must be able to detect causes of failure using testing, etc.  | |
| Maintainability  | The architecture needs must allow modifications with ease after the baseline is established. | |
| Testability  | The architecture needs to be capable to enable an objective and feasible test to be designed and performed to determine whether a requirement is met.  | |
| Verifiability  | The architecture  needs to be capable to be proven correct and complete, allowing for the checking of the correctness of statements or claims, and the replication or confirmation of results by independent means.  | |

### Operable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Auditability  | The architecture must fullfil certain checks to be realized  | |


### Reliable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Availability  | The architecture should be accessible and operational when required for use.  | |
| Certifiability  | The architecture has to meet specific regulatory,  or quality standards through demonstration of compliance evidence.  | |
| Correctness | The architecture has to provide accurate results when used by intended users for intended functions. | |
| Data Integrity  | The architecture must ensure that the used data remains unaltered and consistent from creation to deletion, maintaining its original state unless specifically modified through authorized processes. | [SC7](#_quality_scenarios) |
| Fault isolation  | The architecture needs methods that enables to identify which component or parameter of the system is responsible for a fault or the symptoms of the faulty behavior.  | [SC5](#_quality_scenarios) |
| Fault tolerance  | The architecture should be capable to operate as intended despite the presence of  hardware or software faults. | |



### Secure

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- |  ------------- |
| Confidentiality  | The architecture should not give access to data to entities which are unauthorized to have access.  | [SC7](#_quality_scenarios) |
| Privacy | The architecture should only collect the necessary personal information and delete it when it is no longer needed. | [SC7](#_quality_scenarios) |



## Quality Scenarios {#_quality_scenarios}
Scenario ID | Scenario  | Description | 
|-------------| ------------- | ------------- | 
| SC1 | Getting Introduced to the Architecture  | A new user (independently of his background) can understand the architecture with ease and use it  |
| SC2 | New Programming Language  | A new programming language for quantum computing is introduced, is not represented in the reference architecture and can easily be integrated. |
| SC3 | New Hardware Provider  | A new hardware is introduced, which should be integrated with ease into the reference architecture. |
| SC4 | Integration of HPC  | The possibility that a Stakeholder wants to use a program, which needs a HPC and a quantum processor.  |
| SC5 | Errors in the Architecture  | A Stakeholder finds an undefined space or error in the reference architecture and can report it.  |
| SC6 | Cost Estimation of Quantum Program  | A Stakeholder pays a certain amount of money per time period for his program and gets information how long his program runs.  |
| SC7 | Running a job   | When a job is run in architecture, the job content must be protected from outside interference to prevent research from being accessed.|
| SC8 | A new architecture is introduced  | A new architecture/stack for the quantum eco system is introduced, which may or may not be similar to our reference architecture can be integrated.   |
