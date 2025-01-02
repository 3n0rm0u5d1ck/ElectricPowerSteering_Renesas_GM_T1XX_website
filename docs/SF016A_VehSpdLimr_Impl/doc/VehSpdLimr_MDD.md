---
layout: default
title: VehSpdLimr_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**VehSpdLimr**

**August 10, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sarika Natu** **,**

**KPIT Technologies,**

**India  
<u>Change History</u>**

|                 |                                |             |             |
|-----------------|--------------------------------|-------------|-------------|
| **Description** | **Author**                     | **Version** | **Date**    |
| Initial Version | Sarika Natu(KPIT Technologies) | 1.0         | 10-Aug-2015 |

**  
**

**<u>Table of Contents</u>**

[1 VehSpdLimr High-Level Description
[4](#vehspdlimr-high-level-description)](#vehspdlimr-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of VehSpdLimr
[5](#graphical-representation-of-vehspdlimr)](#graphical-representation-of-vehspdlimr)

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

[4.1.1 Init: VehSpdLimr_Init
[7](#initcomponent-name_initn)](#initcomponent-name_initn)

[4.1.1.1 Design Rationale [7](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [7](#module-outputs)](#module-outputs)

[4.1.2 Per: VehSpdLimr_Per1
[7](#per-vehspdlimrper1)](#per-vehspdlimrper1)

[4.1.2.1 Design Rationale [7](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[7](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [7](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[7](#interrupt-functions)](#interrupt-functions)

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

# VehSpdLimr High-Level Description

The Vehicle Speed Limiting Function determines a limited assist torque
command value as a function of vehicle speed and handwheel position to
manage mechanical fatigue near end-of-travel positions.

# Design details of software module

## Graphical representation of VehSpdLimr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF016A_VehSpdLimr_Impl/doc/mediax/media/image1.png"
style="width:2.79792in;height:3.52153in"
alt="cid:image001.png@01D0D38B.56DD1A30" />

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

NA

# Software Component Implementation

## Sub-Module Functions

## Init\<Component Name\>\_Init\<n\>

## Design Rationale

None

## Module Outputs

None

## Per: VehSpdLimrPer1

## Design Rationale

FDD model contains a block named VehSpdLimrPer1

## Store Module Inputs to Local copies

*See FDD*

## (Processing of function)………

*See FDD*

## Store Local copy of outputs into Module Outputs

*See FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

Referring to anomaly EA4#1276, following are the discrepancies found:

1) Min/max values of HwAgEotCw, HwAgEotCcw, VehSpdLimrPosMaxOffs1, and
VehSpdLimrPosMaxOffs2 need to be set to more realistic values; With the current ranges, there is a
possiblity of converting negative numbers to unsigned data types.  Note these ranges need to
be coordinated with SF011A and SF018A. 

2) Table VehSpdLimrMaxAssiY monotony needs to be identified as "Decreasing" ­­ the implementation
assumes that VehSpdLimrMaxAssiY\[0\] is the maximum value of the table.

3) The concatenate block that creates the Y table for the linear interpolation block has the two inputs
reversed ­­ the first input to the concatenation should be the max value of the VehSpdLimrMaxAssiY
table, and the second input to the concatenation should be the output of the 1­D Lookup block.

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

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                      | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                            |
| 5           | SF016A_VehSpdLimr_Design                                                                                                                                                | See Synergy subproject version |
|             |                                                                                                                                                                         |                                |

{% endraw %}