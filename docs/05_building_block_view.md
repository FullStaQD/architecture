# Building Block View {#section-building-block-view}

## Whitebox Overall System {#_whitebox_overall_system}

<figure markdown="span">
  ![](./images/Building-Blocks-L1.excalidraw.png)
</figure>

### Motivation

Quantum software is highly complex, so we use a layered architecture to
decompose such systems into three layers: the application, system, and physical
layer.
We rectify this decision with the following three perspectives:

- **Abstraction:** Software in the application layer is implemented on a high
  level and independently from concrete quantum devices.
  The system layer compiles high-level specifications into device-specific
  instructions and software in the physical layer targets specific devices with
  low-level control.
- **Skills**: Developing software for the application layer requires abstract
  knowledge of quantum computing (e.g. the circuit model) but no understanding
  of its physical implementations is required.
  For working on the system layer, developers need to have a broad understanding
  of various quantum device architectures and
  [deployment concerns](./07_deployment_view.md).
  Detailed knowledge for concrete quantum devices is required to program and
  operate quantum backends in the physical layer.
- **Operation**: In the application layer, manual programming or specification for
  individual use cases is required.
  Compilation in the system layer is mostly automated with only high-level
  compilation settings needing to be configured.
  Execution on the physical layer is fully automated.

### Contained Building Blocks

- **Application Layer:** This layer will involve use-case-specific quantum and
  hybrid programs, written in high-level languages using algorithms, SDKs and
  libraries. 
- **System Layer:** The system layer is responsible for compiling high-level
  program specifications from the application layer to low-level,
  device-specific instructions to be executed in the physical layer, taking into
  account the quantum device architecture (e.g. superconducting vs. neutral
  atom, topology / connectivity) and possibly HPC concerns.
- **Physical Layer:** The physical layer executes the programs it receives from
  the system layers by controlling the physical quantum device.
  It is also responsible for calibrating the device and monitoring it (e.g.
  fidelities).

### Important Interfaces

!!! warning "TODO"
    
    The interfaces are still to be determined.
    The interface between the application and system layer will involve some
    form of program specification (e.g. source code, circuits or MLIR
    representations) as well as some compiler configuration (e.g. whether to use
    error correction or which quantum device to target) and result passing (e.g.
    callbacks or return values).
    The interface between the system and physical layer will be some low-level
    program specification to be run on quantum devices and co-processors, and it
    involves the reporting of final results as well as monitoring data.

<!-- ### \<Name black box 1\> {#_name_black_box_1}

*\<Purpose/Responsibility\>*

*\<Interface(s)\>*

*\<(Optional) Quality/Performance Characteristics\>*

*\<(Optional) Directory/File Location\>*

*\<(Optional) Fulfilled Requirements\>*

*\<(optional) Open Issues/Problems/Risks\>*

### \<Name black box 2\> {#_name_black_box_2}

*\<black box template\>*

### \<Name black box n\> {#_name_black_box_n}

*\<black box template\>*

### \<Name interface 1\> {#_name_interface_1}

...​

### \<Name interface m\> {#_name_interface_m} -->

## Level 2 {#_level_2}

### White Box *\<building block 1\>* {#_white_box_building_block_1}

*\<white box template\>*

### White Box *\<building block 2\>* {#_white_box_building_block_2}

*\<white box template\>*

...​

### White Box *\<building block m\>* {#_white_box_building_block_m}

*\<white box template\>*

## Level 3 {#_level_3}

### White Box \<\_building block x.1\_\> {#_white_box_building_block_x_1}

*\<white box template\>*

### White Box \<\_building block x.2\_\> {#_white_box_building_block_x_2}

*\<white box template\>*

### White Box \<\_building block y.1\_\> {#_white_box_building_block_y_1}

*\<white box template\>*
