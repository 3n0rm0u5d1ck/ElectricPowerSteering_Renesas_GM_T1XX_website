---
layout: default
title: HiLoadStallLimr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HiLoadStallLimr**

**August 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Kanth Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                    |              |             |
|-----------------|--------------------|--------------|-------------|
| **Description** | **Author**         | **Version**  | **Date**    |
| Initial Version | Krishna Kanth Anne | EA4 01.00.01 | 19-Aug-2015 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[2 HiLoadStallLimr & High-Level Description
[6](#hiloadstalllimr-high-level-description)](#hiloadstalllimr-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HiLoadStallLimr
[7](#graphical-representation-of-hiloadstalllimr)](#graphical-representation-of-hiloadstalllimr)

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

[5.1.1 Init: HiLoadStallLimrInit1
[9](#init-hiloadstalllimrinit1)](#init-hiloadstalllimrinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: HiLoadStallLimrPer1
[9](#per-hiloadstalllimrper1)](#per-hiloadstalllimrper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[*5.2* Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#global-function-1)](#global-function-1)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

MDD for HiLoadStallLimr

# HiLoadStallLimr & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of HiLoadStallLimr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF017A_HiLoadStallLimr_Impl/doc/mediax/media/image1.png"
style="width:4.26111in;height:5.27847in" />

## Data Flow Diagram

Please refer FDD.

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
| Please refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

None

## Init: HiLoadStallLimrInit1

## Design Rationale

## Module Outputs

None

###  [section]

## Per: HiLoadStallLimrPer1

## Design Rationale

None

## Store Module Inputs to Local copies

Please refer FDD

## (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |      |      |     |     |
|----------------------|------|------|-----|-----|
| **Function Name**    | None | Type | Min | Max |
| **Arguments Passed** | None | NA   | NA  | NA  |
|                      | None | NA   | NA  | NA  |
| **Return Value**     | NA   | NA   | NA  | NA  |

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |      |      |     |     |
|----------------------|------|------|-----|-----|
| **Function Name**    | NA   | Type | Min | Max |
| **Arguments Passed** | None |      |     |     |
|                      | NA   |      |     |     |
| **Return Value**     | NA   |      |     |     |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                             |
| 5           | FDD : SF017A_HiLoadStallLimr_Design                                                                                                                                   | See Synergy sub project version |

{% endraw %}