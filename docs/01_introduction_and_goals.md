# Introduction and Goals {#section-introduction-and-goals}
The FullStaQD reference architecture is the first step towards a full stack, which ensures compatability and interoperability of various components in the quantum ecosystem. We want to develop a reference architexture with uniform standardised interfaces, which is consistent, modular and open. This reference architecture would reinforce the german quantum computing ecosystem by demonstrating the technical feasibility of quantum applications in the german industry, while also covering a wide quantum computing landscape.

The reference architecture is divided into three layers and cross-layer concerns. 

| Module  | Description | 
| ------------- | ------------- | 
| Application Layer | Contains all components on a high-level programming language or algorithmic level  |
| System Layer  | Contains all components to adjust high-level program to the specific hardware and to integrate HPCs |
| Physical Layer  | Contains all components on a physical layer, which indirectly/directly communicated with the quantum backend  |
| Cross-Layer Concerns  | Contains all components like Testing, Benchmarking, Simulations, Tools, Visualization, ...  |

![](./images/Reference-Architecture-Introduction.png)


## Requirements Overview {#_requirements_overview}
To establish a solid foundation for the reference architecture and ensure alignment across all stakeholders, we are now defining the key requirements that will guide its design and implementation.

| Requirement  | Description | 
| ------------- | ------------- | 
| Open Source  | The reference architecture and most of its building blocks in the layers are open source |
| Communication | The reference architecture allows changes through communication with the community  |
| Modular  | Systems or whole Layers can be integrated and are exchangeable into the reference architecture using specific interfaces  |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |


## Quality Goals {#_quality_goals}
To maintain a state of the art reference architecture in the quantum ecosystem, we list a few of our most important quality goals for this architecture.

| Quality Goal  | Description | 
| ------------- | ------------- | 
| Operability  | The reference architecture can be understood, learned, used and is attractive to users from academia and industry  |
| Compatibility  | Systems can be integrated into the reference architecture using specific interfaces  |
| Maintainability  | The reference architecture can be modified, corrected, adapted or improved due to changes in the environment or requirements  |
| Functional Suitability  | The reference architecture provides functions that meet the needs.  |
| Realiability  | The reference architecture can maintain a high level of performance when used under specific conditions  |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

## Stakeholders {#_stakeholders}
The FullStaQD reference architecture is designed for research at the university, as well as for practical use of the industry. Current stakeholders that identify themselves and their expectations of the architecture are listed below.


### Academia
| Name  | Role | Contact | Expectation |
| ------------- | ------------- | ------------- | ------------- |
| Karlsruhe Institut of Technology  | Reference Architecture / Application Layer / Cross-Layer Concerns | fullstaqd@lists.kit.edu  | Create an reference architecture which is viable for academia and industry. Expecting strong and future-oriented interfaces between the layers  |
| Forschungszentrum Informatik (FZI)  | Reference Architecture / Application Layer  | denninger@fzi.de  | ....  |
| Technical University of Munich (TUM)  | System Layer  | martin.w.j.schulz@tum.de  | Content Cell  |
| Munich Quantum Software Company (MQSC) | System Layer  | robert@munichquantum.software  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |


### Industry

| Name  | Role | Contact | Expectation |
| ------------- | ------------- | ------------- | ------------- |
| ParityQC  | System Layer  | r.stahn@parityqc.com  | Content Cell  |
| DB Systel GmbH  | Application Layer / Use Cases  | manfred.rieck@deutschebahn.com  | Content Cell  |
| eleQtron | Physical Layer  | pawel.nalezyty@eleqtron.com  | Content Cell  |
| Kipu Quantum  | Cross-Layer Concerns  | david.niehaus@kipu-quantum.com  | Content Cell  |
| Bundesdruckerei (BDR)  | Use Cases  | mohammad.yeghanehAbkenar@bdr.de  | Content Cell  |
| Fraunhofer IAO | Application Layer  | philipp.kunst@iao.fraunhofer.de  | Content Cell  |
| Fraunhofer FOKUS  | Application Layer  | sebastian.bock@fokus.fraunhofer.de | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |
| Content Cell  | Content Cell  | Content Cell  | Content Cell  |

