---
layout: default
title: TEstimn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TEstimn**

**Sep 17, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                        |             |             |
|-----------------|------------------------|-------------|-------------|
| **Description** | **Author**             | **Version** | **Date**    |
| Initial Version | Sankardu Varadapureddi | 1           | 17-Sep-2015 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 TEstimn High-Level Description
[5](#testimn-high-level-description)](#testimn-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of TEstimn
[6](#graphical-representation-of-testimn)](#graphical-representation-of-testimn)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

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

[5.1.1 Init: TEstimnInit1 [9](#init-testimninit1)](#init-testimninit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: TEstimnPer1 [9](#per-testimnper1)](#per-testimnper1)

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
[9](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# Introduction

## Purpose

## Scope

# TEstimn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of TEstimn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF006A_TEstimn_Impl/doc/mediax/media/image1.png"
style="width:3.40833in;height:6.925in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

#### Local Constants

# Software Component Implementation

## Sub-Module Functions

## Init: TEstimnInit1

## Design Rationale

*Refer FDD for the functionality.*

## Module Outputs

*Refer FDD*

## Per: TEstimnPer1

## Design Rationale

In ‘AssistMechanismLeadLagFilterRe-Initialization’ block, blocks
‘AssistMechanismInitEnable’ and ‘AssistMechanismInitDisable’ have
similar logic except for some calculations related to inputs. So the
differences are implemented in ‘if-else’ statement and common logic is
implemented after ‘if-else’ statements in the SW.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

*None*

# UNIT TEST CONSIDERATION

Due to the lead/lag filter implementation in this module, absolute
ranges are difficult to determine without pre-defined knowledge on the
combination of coefficient values (A1, B0, B1). For unit test purposes,
below four sets of lead/lag filter coefficient calibrations
(TEstimnXXLLFilCoeffA1, TEstimnXXLLFilCoeffB0 and TEstimnXXLLFilCoeffB1)
should be tested using the combinations of coefficient values in the
table below, as well as the default values of the filter coefficient
calibrations as given in the data dictionary. The ranges given
throughout this module were taken as the worst case results of the
entire given filter coefficient sets.

| Fz  | 0.0045      | 0.0045        | 0.00003    | 0.00003     |
|-----|-------------|---------------|------------|-------------|
| Fp  | 0.0045      | 0.00003       | 0.0045     | 0.00003     |
|     |             |               |            |             |
| B0  | 1           | 0.0066760330  | 149.78955  | 1           |
| B1  | -0.99717656 | -0.0066571836 | -149.78673 | -0.99998115 |
| A1  | 0.99717656  | 0.99998115    | 0.99717656 | 0.99998115  |

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
| 5           | FDD : SF006A\_ TEstimn_Design                                                                                                                                         | See Synergy sub project version |

{% endraw %}