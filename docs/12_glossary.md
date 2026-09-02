# Glossary {#section-glossary}

## Quantum Kernel {#quantum-kernel}
A quantum kernel is a program to be executed on a quantum computer.
The term highlights that the kernel program is part of a bigger program which is
executed across heterogeneous hardware (meaning there might be CPUs, GPUs, QPUs
or other types of processors involved).

See also:
* [GPU Kernels in the CUDA Programming Language](https://docs.nvidia.com/cuda/cuda-programming-guide/01-introduction/programming-model.html#heterogeneous-systems)

## Quantum Error Correction {#quantum-error-correction}
Quantum Error Correction (QEC) uses redundancy to detect and correct errors occuring throughout quantum computation. A logical qubit is encoded across multiple physical qubits, allowing errors to be detected through measurements of error syndromes and subsequently corrected while preserving the encoded quantum information. QEC therefore introduces a substantial resource overhead, but is the fundamental approach towards fault-tolerant quantum computation.

For further background on the fundamentals of QEC, see [Nielsen and Chuang](https://doi.org/10.1017/CBO9780511976667) as well as [Terhal](https://doi.org/10.1103/RevModPhys.87.307). For a recent experimental development, see [here](https://doi.org/10.1038/s41586-024-08449-y).

## Quantum Error Suppression {#quantum-error-suppression}
Quantum Error Suppression (QES) aims to reduce errors at or close to their physical source by exploiting prior knowledge about unwanted hardware effects and noise. Instead of correcting errors after they have occurred, suppression techniques modify the hardware control to prevent, or reduce their impact, for example through techniques such as dynamical decoupling. QES can therefore improve the reliability of quantum operations with comparatively low resource overhead, but it cannot eliminate errors entirely: its effectiveness is limited by the type of noise and available control resources, and residual errors can accumulate over time.

[Ezzel et al.](https://doi.org/10.1103/PhysRevApplied.20.064027) provide a survey of different dynamical decoupling approaches and their performance. For the underlying principles, see [Viola et al.](https://doi.org/10.1103/PhysRevLett.82.2417)

## Quantum Error Mitigation {#quantum-error-mitigation}
Quantum Error Mitigation (QEM) reduces the effect of noise on computational results. It typically combines multiple noisy circuit executions with classical post-processing to estimate expectation values that are closer to their ideal, noise-free values. Common techniques include Zero Noise Extrapolation (ZNE) and Probabilistic Error Cancellation (PEC); however, these methods can incur substantial or even exponential sampling overhead.

[Li and Benjamin](https://doi.org/10.1103/PhysRevX.7.021050) as well as [Temme et al.](https://doi.org/10.1103/PhysRevLett.119.180509) discuss foundational approaches to QEM. For a recent development, see [here](https://doi.org/10.1038/s41567-023-02042-2).

See also:
* [IBM Quantum Blog](https://www.ibm.com/quantum/blog/quantum-error-suppression-mitigation-correction) for an accessible overview of QEC, QES and QEM.
* [IBM Tutorial](https://quantum.cloud.ibm.com/learning/en/courses/foundations-of-quantum-error-correction) for practical foundations of QEC