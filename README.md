# QVZ Linux Subsystem for Windows (QVZ-LSW)

> **An independent, low-level operating systems research project exploring how Windows binaries execute on Linux**

---

## Introduction

**QVZ Linux Subsystem for Windows (QVZ-LSW)** is a long-term, experimental systems engineering project focused on **running Windows PE (Portable Executable) binaries on Linux** by re-implementing core parts of the Windows loader and execution model from scratch.

This project exists to answer *how Windows really works at the lowest practical level*, not to provide a drop-in compatibility solution. Every component is built with the goal of understanding, not abstraction.

QVZ-LSW is intentionally minimal, explicit, and research-driven.

---

## What This Project Is — and Is Not

### This project **is**:

* A **from-scratch PE loader** targeting Linux
* A deep exploration of **Windows loader internals**
* A study of **relocations, ABI behavior, and binary startup**
* A learning-oriented systems research effort
* Designed to be **readable, inspectable, and debuggable**

### This project **is NOT**:

* ❌ A Wine fork or derivative
* ❌ A virtual machine
* ❌ A CPU or ISA emulator
* ❌ A production-ready compatibility layer
* ❌ A Microsoft-backed or Microsoft-related project

---

## Core Technical Focus

QVZ-LSW focuses on the **earliest and most critical phase of Windows execution**: the loader.

Key technical areas include:

### 1. PE (Portable Executable) Internals

* DOS header, NT headers, and optional headers
* Section table parsing and validation
* RVA vs VA resolution
* Section alignment and permissions

### 2. Image Mapping on Linux

* Mapping PE images into Linux process memory
* Handling executable, writable, and read-only sections
* Correct image base handling
* Page protections using native Linux facilities

### 3. Relocation Handling

* Base relocation blocks
* Relocation types for PE64
* Correct relocation math
* **MinGW pseudo-relocations** (a major focus area)
* Edge cases involving zero-initialized symbols

### 4. ABI and Calling Convention Research

* Windows x64 ABI vs System V ABI
* Stack alignment rules
* Register usage differences
* Entry point calling semantics

### 5. Subsystem Design

* Designing a minimal Windows-style execution environment
* Loader responsibility separation
* Early groundwork for import resolution and API bridging

---

## Current Development Focus

Active work is centered around:

* Finalizing a **correct and Windows-accurate PE64 loader**
* Fixing subtle relocation bugs that differ from documented behavior
* Studying how Windows initializes global symbols
* Reverse-validating behavior against real Windows loaders
* Incrementally stabilizing execution of simple PE programs

This phase prioritizes **correctness over speed** and **understanding over features**.

---

## Planned Work (High-Level)

The following are *research goals*, not promises:

* Import table parsing and resolution
* Minimal Windows API stubs (purely for experimentation)
* Thread Local Storage (TLS) handling
* Exception handling metadata parsing
* Improved diagnostics and loader tracing

---

## Why This Project Exists

Most compatibility layers hide complexity behind massive codebases.

QVZ-LSW deliberately does the opposite.

This project is built to:

* Demystify Windows executable startup
* Learn by re-implementation, not abstraction
* Create a reference-quality loader that can be read end-to-end
* Build deep intuition about cross-OS execution models

If you are curious *how a Windows executable becomes a running program*, this project explores exactly that.

---

## Independence & Legal Disclaimer

**QVZ Linux Subsystem for Windows is a completely independent project.**

* No affiliation with **Microsoft**
* No endorsement by Microsoft or any other company
* No use of proprietary Windows source code
* No relation to **Windows Subsystem for Linux (WSL)**

All trademarks belong to their respective owners.

This project is developed independently for **educational and research purposes only**.

---

## Philosophy

* Clarity over cleverness
* Correctness over shortcuts
* Understanding over results
* Small, inspectable code over massive frameworks

---

## License

This project is released under the **MIT License**.
