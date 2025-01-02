---
layout: default
title: McuCoreCfgAndDiagc Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**McuCoreCfgAndDiagc**

**Oct 6, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                |             |          |
|-----------------|----------------|-------------|----------|
| **Description** | **Author**     | **Version** | **Date** |
| Initial Version | Lucas Wendling | 1           | 10/06/15 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 \<Component Name\> & High-Level Description
[6](#mcucorecfganddiagc-high-level-description)](#mcucorecfganddiagc-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of \<Component Name\>
[7](#graphical-representation-of-mcucorecfganddiagc)](#graphical-representation-of-mcucorecfganddiagc)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: \<Component Name\>\_Init\<n\>
[9](#init-mcucorecfganddiagcinit1)](#init-mcucorecfganddiagcinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: \<Component Name\>\_Per\<n\>
[9](#per-mcucorecfganddiagc_pern)](#per-mcucorecfganddiagc_pern)

[5.1.2.1 Design Rationale [9](#_Toc431918167)](#_Toc431918167)

[5.1.2.2 Store Module Inputs to Local copies
[9](#_Toc431918168)](#_Toc431918168)

[5.1.2.3 (Processing of function)………
[9](#_Toc431918169)](#_Toc431918169)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#_Toc431918170)](#_Toc431918170)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 \<Server Runable Name\> [9](#_Toc431918172)](#_Toc431918172)

[5.2.1.1 Design Rationale [9](#_Toc431918173)](#_Toc431918173)

[5.2.1.2 (Processing of function)………
[10](#_Toc431918174)](#_Toc431918174)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.3.1 Interrupt Function Name [10](#_Toc431918176)](#_Toc431918176)

[5.3.1.1 Design Rationale [10](#_Toc431918177)](#_Toc431918177)

[5.3.1.2 (Processing of the ISR function)…..
[10](#_Toc431918178)](#_Toc431918178)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[11](#design-rationale-4)](#design-rationale-4)

[5.5.1.2 processing [11](#processing-1)](#processing-1)

[6 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# McuCoreCfgAndDiagc & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of McuCoreCfgAndDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Impl/doc/mediax/media/image1.png"
style="width:1.98333in;height:2.125in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: McuCoreCfgAndDiagcInit1

## Design Rationale

*Temporary variables were created to read register values into in order
to avoid MISRA violations that appear when volatile values are used in
conditional statements.*

## Module Outputs

*Refer to FDD*

## Init: McuCoreCfgAndDiagcInit2

## Design Rationale

*Temporary variables were created to read register values into in order
to avoid MISRA violations that appear when volatile values are used in
conditional statements.*

## Module Outputs

*Refer to FDD*

## Init: McuCoreCfgAndDiagcInit3

## Design Rationale

*Empty function for purposes of memory mapping*

## Module Outputs

*None*

## Per: McuCoreCfgAndDiagc_Per\<n\>

*None*

## Server Runables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     |                   |                               |                               |                               |

## Design Rationale

## Processing

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     |                   |                               |                               |                               |

## Design Rationale

## Processing

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |
|                             |                 |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0               |

{% endraw %}