---
layout: default
title: HwAgVehCentrTrim_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgVehCentrTrim**

**December 6, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                 |               |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                 | **Author**    | **Version** | **Date**    |
| Initial Version                                 | Nick Saxton   | 1           | 24-Feb-2016 |
| Updated graphical representation                | Nick Saxton   | 2           | 04-Apr-2016 |
| Updated graphical representation for FDD v1.3.0 | Nick Saxton   | 3           | 15-Jun-2016 |
| Added Init function to sub-module functions     | Nick Saxton   | 4           | 12-Sep-2016 |
| Updated to fix Anomaly EA4#8204                 | Matthew Leser | 5           | 06-Dec-2016 |

**  
**

**<u>Table of Contents</u>**

[1 HwAgVehCentrTrim High-Level Description
[4](#hwagvehcentrtrim-high-level-description)](#hwagvehcentrtrim-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of HwAgVehCentrTrim
[5](#graphical-representation-of-hwagvehcentrtrim)](#graphical-representation-of-hwagvehcentrtrim)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[6](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[6](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [6](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[7](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: None
[7](#init-hwagvehcentrtriminit1)](#init-hwagvehcentrtriminit1)

[4.1.2 Per: GmStrtStopPer1
[7](#per-hwagvehcentrtrimper1)](#per-hwagvehcentrtrimper1)

[4.1.2.1 Design Rationale [7](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[4.1.2.3 (Processing of function)………
[7](#processing-of-function-1)](#processing-of-function-1)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[4.2 Server Runables [7](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[7](#clrhwagtrimval_oper)](#clrhwagtrimval_oper)

[4.4 Module Internal (Local) Functions
[7](#module-internal-local-functions)](#module-internal-local-functions)

[4.5 GLOBAL Function/Macro Definitions
[7](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[8](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[9](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[10](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [11](#glossary)](#glossary)

[Appendix C References [12](#references)](#references)

# HwAgVehCentrTrim High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of HwAgVehCentrTrim

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF053A_HwAgVehCentrTrim_Impl/doc/mediax/media/image2.png"
style="width:2.78333in;height:2.74167in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

| Constant Name      | Units | Value |
|--------------------|-------|-------|
| HALFFACTOR_ULS_F32 | ULS   | 0.5   |

Refer .m file for other constants

# Software Component Implementation

## Sub-Module Functions

## Init: HwAgVehCentrTrimInit1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: HwAgVehCentrTrimPer1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## ClrHwAgTrimVal_Oper

Refer FDD

##  GetHwAgTrimVal\_ Oper

Refer FDD

## SetHwAgTrimVal_Oper

Refer FDD

## UpdHwAgTrimVal_Oper

Refer FDD

## Interrupt Functions

*None*

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.00                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : SF053A_HwAgVehCentrTrim_Design                                                                                                                                  | See Synergy sub project version |

{% endraw %}