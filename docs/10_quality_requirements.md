# Quality Requirements {#section-quality-scenarios}
As breifly mentioned in the 'Introduction and Goals' section, there are quality goals, we want to achieve in the FullStaQD reference architecture. 
In this section, we want to describe these goals in more detail and want to present some scenarios, in which they are needed.

## Quality Requirements Overview {#_quality_requirements_overview}
We sort the quality requirements after the arc42 design (https://quality.arc42.org/qualities/). Afterwards, we present the scenarios that can appear in the reference architecture, and we define which quality goal needs to be fulfilled in each scenario.

### Efficient

| Quality Goal  | Description | Scenario ID |
| ------------- | ------------- |  ------------- | 
| Coherence    | The reference architecture is logically or aesthetically ordered or integrated.  | SC1 |
| Cohesion  | The modules of the architecture belong and work together as intended. | |
| Compliance  | The architecture should obey the rules of state of the art standards.  | |
| Conciseness | The architectures content needs to be clearly but briefly described.  | SC1 |
| Effectiveness  | The architecture is able to produce the desired result/output. | |
| Efficiency  | The architecture capable of producing desired results with little or no waste (as of time or materials). | SC6  |
| Latency | The time delay of some changes in the refrence architecture should be minimal.  |  |
| Performance | The architecture should perform its functions efficiently in the use of of resources and withing a specified time and throughput parameters.  | SC6 |
| Profitability  | The reference architecture needs to be profitable in an industrial sense.  | |
| Resource utilization | The reference architecture doesnt use more than the specified amount of resources to perform its function under specified conditions.  | SC6 |
| Simplicity  | The reference architecture needs to be easy to read, understand, and correctly modify.  | SC1 |
| Sustainability  | The reference architecture has to meet the needs of the present without compromising the ability of future generations to meet their own needs. It emphasizes the long-term viability, resilience, and adaptability of the system, considering environmental, economic, and social factors  | SC2, SC3, SC8 |

### Flexible

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Adaptability  | Capability of a product to be effectively and efficiently adapted for or transferred to different hardware, software or other operational or usage environments | SC2, SC3, SC4 |
| Agility  | A system can rapidly be changed (as opposed to flexibility, which means that a system can easily be changed.)  | SC2, SC3, SC4|
| Changeability  |  the system can rapidly be changed. | SC2, SC3, SC5, SC8 |
| Co-existence  | Capability of a product to perform its required functions efficiently while sharing a common environment and resources with other products, without detrimental impact on any other product (with other stacks) | SC8 |
| Composability  | Composability is a system design principle that deals with the inter-relationships of components. A highly composable system provides components that can be selected and assembled in various combinations to satisfy specific user requirements.    |  |
| Configurability | Configurability refers to the ability of a system, software application, or hardware device to be easily customized and adapted to suit various requirements, preferences, and environments. A configurable system allows users or administrators to modify its settings, features, or behavior without the need for extensive code changes or hardware modifications. Configurability empowers users to tailor the system to their specific needs, making it more versatile and adaptable. | SC2, SC3, SC4, SC8 |
| Elasticity  | In distributed system and system resource, elasticity is defined as “the degree to which a system is able to adapt to workload changes by provisioning and de-provisioning resources in an autonomic manner, such that at each point in time the available resources match the current demand as closely as possible” | SC6 |
| Evolvability  | The ability of a system to adapt to changes in its environment, requirements, and implementation technologies in a cost-effective way.  | SC2, SC3, SC5, SC8 |
| Extensibility  | Ability to add new features or functions to a system.  | SC2, SC3, SC4  |
| Flexibility  | Applies to several stages in the life of a system or product, for example: at development or compile time, installation or deployment time, during testing at runtime  | |
| Independence  | Functional independence is achieved by developing functions that perform only one kind of task and do not excessively interact with other modules. Independence is important because it makes implementation more accessible and faster. The independent modules are easier to maintain, test, and reduce error propagation and can be reused in other programs as well. Thus, functional independence is a good design feature which ensures software quality.  | |
| Integrability  | Integrability is the ease with which a software component or system can be integrated with other components or systems.  | SC2, SC3, SC4, SC8|
| Interchangeability | Interchangeability is the ability to substitute one component, part, or element with another of the same type without requiring modifications to the system or loss of functionality. | SC3 |
| Internationalization  | Developing information so that it is suitable for an international audience  | |
| Modifiability | Capability of a system to be effectively and efficiently modified without introducing defects or degrading existing product quality | |
| Reusability  | Capability of a product to be used as assets in more than one system, or in building other assets.  | |
| Scalability  | Scalability is the property of a system to handle a growing amount of work by adding resources to the system. | SC8 |
| Versatility  | able to change easily or to be used for different purposes  | SC5 |


### Maintainable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Analysability  | Capability of a product to be effectively and efficiently assessed regarding the impact of an intended change to one or more of its parts, to diagnose it for deficiencies or causes of failures, or to identify parts to be modified.  | |
| Debuggability  | Debuggability focuses on shortening time-to-diagnosis and reducing the effort to pinpoint root causes. It is closely related to but distinct from:  Observability: raw signals (logs, metrics, traces) vs. using those signals effectively to debug. Testability: how easily a system can be tested vs. how easily failures can be diagnosed. Analysability: impact/change assessment; debuggability emphasizes incident and defect diagnosis| |
| Maintainability  | Maintainability is concerned with modifications after the software baseline is established. The goal of a maintenance activity is to correct defects, adapt to changing environments, or im- prove a system’s future maintainability or other quality attributes. The description of a particular maintenance activity is in the eye of the beholder: A particular change (or type of change) can be labeled differently, depending on the maintainer’s intention. We measure maintainability as the amount of work required to modify, test, and maintain our software base in response to changes in environmental elements. This measure may depend on who is perform- ing the maintenance task and that individual’s level of skill or knowledge. | |
| Modularity  | Capability of a product to limit changes to one component from affecting other components. (Backend)  | SC3 |
| Updateability  | Updateability refers to the capability of a software system to efficiently receive, install, and integrate updates, patches, security fixes, and minor enhancements while maintaining system integrity and minimizing service disruption. | SC5 |
| Testability  | Capability of a product to enable an objective and feasible test to be designed and performed to determine whether a requirement is met. | |
| Verifiability  | The capability of a product or system to be proven correct and complete, allowing for the checking of the correctness of statements or claims, and the replication or confirmation of results by independent means.  | |

### Operable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Auditability  | … what the product has to do (usually retain records) to permit the required audit checks.  | |
| Autonomy | The ability of a system or component to operate independently, without requiring continuous control or intervention from external entities.  | |
| Backward compatibility  | Backward compatibility is a property of an operating system, product, or technology that allows for interoperability with an older legacy system, or with input designed for such a system, especially in telecommunications and computing.  | |
| Compatibility  | Capability of a product to exchange information with other products, and/or to perform its required functions while sharing the same common environments and resources.  | SC4 |
| Deployability  | Deployability refers to a property of software indicating that it may be deployed, that is, allocated to an environment for execution—within a predictable and acceptable amount of time and effort. Moreover, if the new deployment is not meeting its specifications, it may be rolled back, again within a predictable and acceptable amount of time and effort.  | SC6 |
| Ease of Use | Ease of use is a basic concept that describes how easily users can use a product. Design teams define specific metrics per project—e.g., “Users must be able to tap Find within 3 seconds of accessing the interface.” —and aim to optimize ease of use while offering maximum functionality and respecting business limitations. | SC1 |
| Governability  | Governability is the degree to which an organization can direct and control a system through policies that are defined, communicated, monitored, and enforced.  | SC5 |
| Interaction capability  | capability of a product to be interacted with by specified users to exchange information between a user and a system via the user interface to complete the intended task  | |
| Interoperability  | Work (together) with other products or systems.  | SC2, SC3, SC4, SC8 |
| Learnability  | Capability of a product to have specified users learn to use specified product functions within a specified amount of time. | SC1 |
| Legal Requirements  | Legal Requirement means any federal, state, local, municipal, foreign or other law, statute, constitution, principle of common law, resolution, ordinance, code, edict, decree, rule, regulation, ruling or requirement issued, enacted, adopted, promulgated, implemented or otherwise put into effect by or under the authority of any Governmental Body.  | |
| Redundancy  | The goal (required quality) can be twofold: free of redudancy (or repetition), avoid duplication have (controlled) redundancy or repetition, e.g. with redundant hardware or certain parts of systems to avoid downtime due to failures (e.g. due to hardware defects or component/service overload or similar).  | |
| Understandability  | Understandability is the concept that a system should be presented so that (somebody) can easily comprehend it. The more understandable a system is, the easier it will be for engineers to change it in a predictable and safe manner.  | SC1 |
| Usability | Capability of a product to be used by specified users to exchange information between a user and an interactive system via the user interface to complete the intended task.  | |


### Reliable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |
| Availability  | Capability of a product to be accessible and operational when required for use.  | |
| Certifiability  | The degree to which a system can be certified to meet specific regulatory, safety, or quality standards through demonstration of compliance evidence.  | |
| Clarity | The quality of being coherent and intelligible.  | SC1 |
| Correctness | Provide accurate results when used by intended users for intended functions. | |
| Credibility  | Credibility comprises the objective and subjective components of the believability of a source or message.  | |
| Data Integrity  | Data integrity refers to the maintenance and assurance of accuracy, consistency, and reliability of data over its entire life cycle. It ensures that data remains unaltered and consistent from creation to deletion, maintaining its original state unless specifically modified through authorized processes. | SC7 |
| Durability | The ability of a software system to remain useful and meet user needs over a long period, particularly in the face of changing business requirements and technological advancements.  | SC2, SC3, SC4, SC5, SC8 |
| Fault isolation  | An method that enables to identify which component or parameter of the system is responsible for a fault or the symptoms of the faulty behavior.  | |
| Fault tolerance  | Capability of a product to operate as intended despite the presence of hardware or software faults. | |
| Functional completeness | Provide a set of functions that covers all the specified tasks and intended users’ objectives.  | |
| Functional suitability  | Provide functions that meet stated and implied needs of intended users when it is used under specified conditions. | |
| Functionality  | Functionality is the ability of the system to do the work for which it was intended. | |
| Reliability | Capability of a product to perform specified functions under specified conditions for a specified period of time without interruptions and failures. | |
| Stability  |  When adding new features, existing parts can remain largely unchanged.  | SC2 SC3, SC4, SC8  |
| Suitability  | Provide functions that meet stated and implied needs of intended users when it is used under specified conditions.  | |
| Timeliness | The degree to which data is up-to-date and available when needed for decision-making or processing. | |
| Transparency  | the quality of being easy to see through.  | |


### Secure

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- |  ------------- |
| Confidentiality  | Capability of a product to ensure that data are accessible only to those authorized to have access.  | SC7 |
| Privacy | Broadly speaking, privacy is the right to be let alone, or freedom from interference or intrusion. Information privacy is the right to have some control over how your personal information is collected and used.  | SC7 |


### Usable

| Quality Goal  | Description |  Scenario ID |
| ------------- | ------------- | ------------- |  
| Accessibility  | Capability of a product or system to be usable by people with the widest range of characteristics and capabilities to achieve a specified goal in a specified context of use.  | SC1 |
| Attractiveness  | Attractiveness summarizes properties that make software appealing to users and stakeholders. Attractive software typically exhibits: User-friendly and intuitive design: The software is easy to navigate and use, minimizing learning curves and maximizing efficiency.  Robust functionality and regular updates: The software offers powerful features and is continuously improved to meet evolving user needs. Optimized performance with minimal errors: The software runs smoothly, with quick load times and few errors, enhancing user productivity. Compatibility with various systems: The software works well across different platforms and hardware configurations.  | |
| Communicability  | Communicability in software systems refers to the clarity and effectiveness with which the system conveys its functions and usability to the user. This includes the design of the user interface, the presentation of information, and the system’s ability to guide and assist users in accomplishing their tasks.  | SC1 |
| Consistency  | Eventual consistency is a weaker consistency model: after an update, reads may temporarily return stale values, but if no new updates occur, all replicas will eventually converge to the last written value. It is commonly used to improve availability and latency in distributed systems.  | |
| Discoverability  | The ease with which users can find new or unknown features, content, and functionalities within a product or system without prior knowledge of their existence.  | SC1 |
| Inclusivity  | Capability of a product to be utilised by people of various backgrounds  | SC1 |
| Intuitiveness  | The degree to which a system’s interface, behavior, and information organization align with users’ existing mental models and expectations, enabling immediate understanding and effective use without prior learning or training. | SC1 |
| Readability  | The fact of being easy to read, or the degree to which something is easy to read.  | SC1 |
| Self-descriptiveness  | Capability of a product to present appropriate information, where needed by the user, to make its capabilities and use immediately obvious to the user without excessive interactions with a product or other resources.  | SC1 |



## Quality Scenarios {#_quality_scenarios}
Scenario ID | Scenario  | Description | 
|-------------| ------------- | ------------- | 
| SC1 | Getting Introduced to the Architecture  | A new user (idepedently of his background) wants to learn about the architecture and use it.  |
| SC2 | New Programming Language  | A new programming language for quantum computing is getting introducted and is not represented in the reference architecture. |
| SC3 | New Hardware Provider  | A new hardware is introduced, which should be integrated into the reference architecture |
| SC4 | Integration of HPC  | A Stakeholder wants to use a programm, which needs a HPC and a quantum processor.  |
| SC5 | Errors in the Architecture  | A Stakeholder finds an undefined space or error in the reference architecture  |
| SC6 | Cost Estimation of Quantum Program  | A Stakeholder pays a certain amount of money per time period for his program and needs information how long his program runs.  |
| SC7 | Running a job   | When a job is run in architecture, the job content must be protected from outside interference to prevent research from being accessed.|
| SC8 | A new architecture is introduced  | A new architecture/stack for the quantum eco system is introduced, which may or may not be similar to our reference architecture.  |
