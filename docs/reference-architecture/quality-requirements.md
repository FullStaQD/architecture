# Quality Requirements {#section-quality-scenarios}
As briefly mentioned in the [Introduction and Goals section](./introduction-and-goals.md), there are quality requirements, we want to achieve in the FullStaQD reference architecture. 
In this section, we want to describe these requirements in more detail and want to present some scenarios, in which they are needed. While there are many more quality requirements in concrete systems, we only discuss requirements that are often relevant in general quantum software systems. 

## Quality Requirements Overview {#_quality_requirements_overview}
We sort the quality requirements after the [arc42 quality model](https://quality.arc42.org/qualities/). Afterwards, we present some of the scenarios that can appear in the instantiation of the reference architecture, and we define which quality goal needs to be fulfilled in each scenario.

## Quality Requirement for the instantiation of the reference architecture

| Quality Requirement  | Description | Scenario ID |
| ------------- | ------------- |  ------------- | 
| Analysability  | The architecture must be able to detect causes of failure using testing, etc.  | [SC3](#_quality_scenarios) |
| Auditability  | The architecture must fullfil certain checks to be realized  | |
| Certifiability  | The architecture has to meet specific regulatory,  or quality standards through demonstration of compliance evidence.  | [SC6](#_quality_scenarios) |
| Cohesion  | The modules of the architecture belong and work together as intended. | [SC3](#_quality_scenarios) |
| Conciseness | The architectures content needs to be clearly but briefly described.  | [SC1](#_quality_scenarios) |
| Confidentiality  | The architecture should not give access to data to entities which are unauthorized to have access.  | [SC5](#_quality_scenarios) |
| Data Integrity  | The architecture must ensure that the used data remains unaltered and consistent from creation to deletion, maintaining its original state unless specifically modified through authorized processes. | [SC5](#_quality_scenarios) |
| Efficiency  | The architecture is capable of producing desired results with little or no waste (as of time or materials). | [SC4](#_quality_scenarios)  |
| Fault isolation  | The architecture needs methods that enables to identify which component or parameter of the system is responsible for a fault or the symptoms of the faulty behavior.  | [SC3](#_quality_scenarios) |
| Fault tolerance  | The architecture should be capable to operate as intended despite the presence of hardware or software faults. | |
| Independence  | The architectures components should only perform on task and do not excessively interact with other components. | [SC6](#_quality_scenarios) |
| Maintainability  | The architecture needs must allow modifications with ease after the baseline is established. | [SC2](#_quality_scenarios)  |






## Quality Scenarios {#_quality_scenarios}
Scenario ID | Scenario  | Description | 
|-------------| ------------- | ------------- | 
| SC1 | Getting Introduced to the Architecture  | A new user (independently of his background) can understand the architecture with ease and use it  |
| SC2 | Integration of HPC  | The possibility that a Stakeholder wants to use a program, which needs a HPC and a quantum processor.  |
| SC3 | Errors in the Architecture  | A Stakeholder finds an undefined space or error in the reference architecture and can report it.  |
| SC4 | Cost Estimation of Quantum Program  | A Stakeholder pays a certain amount of money per time period for his program and gets information how long his program runs.  |
| SC5 | Running a job   | When a job is run in architecture, the job content must be protected from outside interference to prevent research from being accessed.|
| SC6 | Change Module | After the instantiation a component needs to be changed|
