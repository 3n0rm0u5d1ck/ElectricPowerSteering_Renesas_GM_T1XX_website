---
layout: default
title: SnsrOffsCorrn Module Design Document
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**SnsrOffsCorrn**

**Jan 27, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |               |             |             |
|-----------------|---------------|-------------|-------------|
| **Description** | **Author**    | **Version** | **Date**    |
| Initial Version | Avinash James | 1.0         | 27-Jan-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 SnsrOffsCorrn High-Level Description
[6](#snsroffscorrn-high-level-description)](#snsroffscorrn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of SnsrOffsCorrn
[7](#graphical-representation-of-snsroffscorrn)](#graphical-representation-of-snsroffscorrn)

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

[5.1.1 Init: SnsrOffsCorrnInit1
[9](#init-snsroffscorrninit1)](#init-snsroffscorrninit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: SnsrOffsCorrnPer1
[9](#per-snsroffscorrnper1)](#per-snsroffscorrnper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

This document defines the module level design for the Sensor Offset and
Correction Component. Major part of design has been captured in the FDD
and any design rationale that has not been identified in the FDD and has
been used to implement the component has been documented in the MDD

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

#  SnsrOffsCorrn High-Level Description

Sensor Offset and Correction (SnsrOffsCorrn) corrects the Yaw rate, Hand
wheel Position and Hand wheel Torque signals using their corresponding
offset learnt values. Each offset value is learnt by the SF051A Sensor
Offset Learning.

# Design details of software module

See FDD.

## Graphical representation of SnsrOffsCorrn 

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF052A_SnsrOffsCorrn_Impl/doc/mediax/media/image1.png)

## Data Flow Diagram

See FDD.

### Component level DFD

See FDD.

### Function level DFD

See FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                    | Resolution                      | Units        | Value    |
|---------------------------------|---------------|-----------|-------------|
| HWAGHILIM_HWDEG_F32              | Single Precision Floating Point | HwDeg        | 1440.0F  |
| HWAGLOLIM_HWDEG_F32              | Single Precision Floating Point | HwDeg        | -1440.0F |
| VEHYAWRATEHILIM_VEHDEGPERSEC_F32 | Single Precision Floating Point | VehDegPerSec | 120.0F   |
| VEHYAWRATELOLIM_VEHDEGPERSEC_F32 | Single Precision Floating Point | VehDegPerSec | -120.0F  |

# Software Component Implementation

\<The detailed design of the function is provided in the FDD. The detail
design shall only be added to the MDD when it is not provided in the FDD
or the FDD is not adequate and clarification is needed.\>

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

*\<(Note: For multiple init or per functions, insert new headers at the
“Header 3” level – subset of “Sub-Module Functions section above” and
follow the same sub-section design shown below . If none required, place
the text “None”))\>*

## Init: SnsrOffsCorrnInit1 

## Design Rationale

None – Empty Init Function

## Module Outputs

None

## Per: SnsrOffsCorrnPer1

## Design Rationale

The periodic function reads the input port values and based on the
calibration defined, applies the offset to the Yaw rate, Hand wheel
Position and Hand wheel Torque signals and writes the corrected value to
the corresponding output ports

## Store Module Inputs to Local copies

None

## (Processing of function)………

See FDD.

## Store Local copy of outputs into Module Outputs

None

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

None

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}