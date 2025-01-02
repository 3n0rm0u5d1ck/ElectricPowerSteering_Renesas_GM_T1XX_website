---
layout: default
title: EcmOutpAndDiagc Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**EcmOutpAndDiagc**

**Feb 5, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                              |                |             |          |
|------------------------|---------------------|--------------|--------------|
| **Description**                                              | **Author**     | **Version** | **Date** |
| Initial Version                                              | Lucas Wendling | 1           | 10/06/15 |
| Updated with startup tests for EI and Pseudo Error Injection | Avinash James  | 2           | 02/05/15 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 EcmOutpAndDiagc & High-Level Description
[6](#ecmoutpanddiagc-high-level-description)](#ecmoutpanddiagc-high-level-description)

[*3* Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of EcmOutpAndDiagc
[7](#graphical-representation-of-ecmoutpanddiagc)](#graphical-representation-of-ecmoutpanddiagc)

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

[5.1.1 Init: EcmOutpAndDiagcInit1
[9](#init-ecmoutpanddiagcinit1)](#init-ecmoutpanddiagcinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Init: EcmOutpAndDiagcInit2
[9](#init-ecmoutpanddiagcinit2)](#init-ecmoutpanddiagcinit2)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [9](#module-outputs-1)](#module-outputs-1)

[*5.1.3* *Init: EcmOutpAndDiagcInit3*
[9](#init-ecmoutpanddiagcinit3)](#init-ecmoutpanddiagcinit3)

[*5.1.3.1* *Design Rationale*
[9](#design-rationale-2)](#design-rationale-2)

[*5.1.3.2* *Module Outputs* [9](#module-outputs-2)](#module-outputs-2)

[*5.1.4* *Init: EcmOutpAndDiagcInit4*
[9](#init-ecmoutpanddiagcinit4)](#init-ecmoutpanddiagcinit4)

[*5.1.4.1* *Design Rationale*
[9](#design-rationale-3)](#design-rationale-3)

[*5.1.4.2* *Module Outputs* [9](#module-outputs-3)](#module-outputs-3)

[5.1.5 Per: EcmOutpAndDiagc_Per
[9](#per-ecmoutpanddiagc_per)](#per-ecmoutpanddiagc_per)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.2.1 CtrlErrOut_Oper [10](#ctrlerrout_oper)](#ctrlerrout_oper)

[5.2.1.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.2.1.2 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[5.5.1.2 Processing [10](#processing-1)](#processing-1)

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

# EcmOutpAndDiagc & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of EcmOutpAndDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Impl/doc/mediax/media/image1.png"
style="width:2.28333in;height:2.125in" />

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

## Init: EcmOutpAndDiagcInit1

## Design Rationale

*Temporary variables were created to read register values into in order
to avoid MISRA violations that appear when volatile values are used in
conditional statements.*

## Module Outputs

*See FDD*

## Init: EcmOutpAndDiagcInit2

## Design Rationale

*Empty function for purposes of memory mapping*

## Module Outputs

*None*

## *Init: EcmOutpAndDiagcInit3*

## *Design Rationale*

*Non-RTE initialization function for EI Start up Test*

## *Module Outputs*

*None*

## *Init: EcmOutpAndDiagcInit4*

## *Design Rationale*

*Non-RTE initialization function for Pseudo Error Injection Start up
Test*

## *Module Outputs*

*None*

## Per: EcmOutpAndDiagc_Per

None

## Server Runables 

## CtrlErrOut_Oper

## Design Rationale

*None*

##  (Processing of function)………

*Refer to FDD*

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

| **Abbreviation or Acronym** | **Description**     |
|-----------------------------|---------------------|
| EI                          | Exception Interrupt |
|                             |                     |

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