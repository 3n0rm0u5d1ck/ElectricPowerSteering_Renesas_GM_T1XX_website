---
layout: default
title: PwrSply_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**PwrSply**

**April 04, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                               |             |             |               |
|-------------------------------|-------------|-------------|---------------|
| **Description**               | **Author**  | **Version** | **Date**      |
| Initial Version               | Rijvi Ahmed | 1.0         | 15-Sep-2015   |
| Updated per design rev. 1.4.0 | Rijvi Ahmed | 2.0         | 04-April-2016 |

**<u>Table of Contents</u>**

[1 Introduction 4](#introduction)

[2 PwrSply & High-Level Description 5](#pwrsply-high-level-description)

[3 Design details of software module
6](#design-details-of-software-module)

[3.1 Graphical representation of PwrSply
6](#graphical-representation-of-pwrsply)

[3.2 Data Flow Diagram 6](#data-flow-diagram)

[3.2.1 Component level DFD 6](#component-level-dfd)

[3.2.2 Function level DFD 6](#function-level-dfd)

[4 Constant Data Dictionary 7](#constant-data-dictionary)

[4.1 Program (fixed) Constants 7](#program-fixed-constants)

[4.1.1 Embedded Constants 7](#embedded-constants)

[5 Software Component Implementation
8](#software-component-implementation)

[5.1 Sub-Module Functions 8](#sub-module-functions)

[5.1.1 Init: PwrSplyInit1 8](#init-pwrsplyinit1)

[5.1.1.1 Design Rationale 8](#__RefHeading___Toc447646292)

[5.1.1.2 (Processing of function)……… 8](#__RefHeading___Toc447646293)

[5.1.2 Per: PwrSplyPer1 8](#per-pwrsplyper1)

[5.1.2.1 Design Rationale 8](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 8](#processing-of-function-1)

[5.1.2.4 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runnable 8](#server-runnable)

[5.3 Interrupt Functions 8](#interrupt-functions)

[5.4 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
9](#global-functionmacro-definitions)

[6 Known Limitations with Design 10](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 11](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 12](#abbreviations-and-acronyms)

[Appendix B Glossary 13](#glossary)

[Appendix C References 15](#references)

# Introduction

None

# PwrSply & High-Level Description

*None*

# Design details of software module

*\<The Data Flow Diagrams should be created in the absence of this
representation with the FDD.\>*

## Graphical representation of PwrSply

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES008A_PwrSply_Impl/doc/mediax/media/image1.png"
style="width:3.05in;height:2.41667in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                           |            |       |       |
|-------------------------------------------|------------|-------|-------|
| Constant Name                             | Resolution | Units | Value |
| Refer to the DataDictionary of the design |            |       |       |

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

## Init: PwrSplyInit1

## Design Rationale

*None*

## (Processing of function)………

*Refer to FDD.*

###  [section]

## Per: PwrSplyPer1 

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD.*

## (Processing of function)………

*Refer to FDD.*

## Store Local copy of outputs into Module Outputs

*Refer to FDD.*

## Server Runnable 

*None*

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2                 |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                               |
| 5           | FDD – ES008A PwrSply                                                                                                                                          | See Synergy subproject version    |
| 6           | **CM600A_CSIG0CfgAndUse_Design**                                                                                                                              | See the latest version in Synergy |

{% endraw %}