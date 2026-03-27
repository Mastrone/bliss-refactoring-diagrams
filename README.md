# BLISS Software Architecture & Refactoring 🔭

*Read this in other languages: [Italiano](README.it.md)*

[![C++](https://img.shields.io/badge/C++-Modern-blue.svg)](https://isocpp.org/)
[![CUDA](https://img.shields.io/badge/CUDA-Enabled-green.svg)](https://developer.nvidia.com/cuda-zone)
[![UML](https://img.shields.io/badge/UML-clang--uml-orange.svg)](https://github.com/bkryza/clang-uml)

This repository contains the high-resolution architectural and sequence diagrams referenced in the thesis: **"[Refactoring of the BLISS software for Technosignatures search]"**.

The diagrams document the software engineering and refactoring process applied to the **BLISS** (Breakthrough Listen Interesting Signal Search) pipeline, a high-performance, GPU-accelerated SETI search software. All diagrams were generated using the `clang-uml` static analysis tool.

## Repository Structure

The repository is organized into three main categories, structured to provide an objective and direct comparison between the pre-refactoring and post-refactoring code states.

### 1. [Architectural Diagrams](./architecture_diagrams)
High-level package diagrams illustrating the software topology. 
* They highlight the elimination of cyclic dependencies originally present between the `core` and `file_types` modules, demonstrating the achievement of a unidirectional architecture.

### 2. [Class Diagrams](./class_diagrams)
Detailed UML diagrams focusing on the core mathematical and domain components.
* They illustrate the resolution of "God Classes" and the reduction of constructor complexity through the implementation of the *Parameter Object Pattern*.
* They demonstrate the decoupling of the logic engine from physical I/O libraries (e.g., HDF5) through the introduction of abstract interfaces, such as `IScanDataSource`.

### 3. [Sequence Diagrams](./sequence_diagrams)
Mapping of the dynamic execution flow related to the main command `bliss_find_hits`.
* The documentation includes the complete execution flow for both versions of the software.
* To ensure better readability, the dynamic flow analysis has been fragmented into four macro-phases (Initialization, Device Configuration, Mathematical Computation, Output Serialization). This subdivision allows for detailed isolation and analysis of the runtime optimizations introduced, such as the adoption of *Lazy Evaluation* and the drastic reduction of blocking disk calls.

## External References

* Original BLISS software repository: [n-west/bliss](https://github.com/n-west/bliss)
* Refactored code forked from the official UCBerkeley repository [Mastrone/bliss](https://github.com/Mastrone/bliss)
* Information on the SETI project and Breakthrough Listen: [Berkeley SETI Research Center](https://seti.berkeley.edu/)
