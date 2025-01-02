---
layout: default
title: HwAgCorrln_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgCorrln**

**Dec 15, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Selva Sengottaiyan**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                         |                        |             |              |
|------------------------|---------------------|--------------|--------------|
| **Description**         | **Author**             | **Version** | **Date**     |
| Initial Version         | Sankardu Varadapureddi | 1.0         | 28-July-2015 |
| Anomoly 3047,1982 fixed | Selva Sengottaiyan     | 2.0         | 15-Dec-15    |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 HwAgCorrln High-Level Description
[5](#hwagcorrln-high-level-description)](#hwagcorrln-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of ‘HwAgCorrln’
[6](#_Toc425843677)](#_Toc425843677)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[5.1.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.2 Interrupt Service Routines
[8](#interrupt-service-routines)](#interrupt-service-routines)

[5.1.3 Server Runnable Functions
[8](#server-runnable-functions)](#server-runnable-functions)

[5.1.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[5.1.5 Transition Functions
[8](#transition-functions)](#transition-functions)

[6 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# Introduction

## Purpose

## Scope

# HwAgCorrln High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of ‘HwAgCorrln’

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES239A_HwAgCorrln_Impl/doc/mediax/media/image2.png"
style="width:2.85833in;height:3.6in" />

## Data Flow Diagram

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

#### Local Constants

| Constant Name       | Resolution | Units  | Value |
|---------------------|------------|--------|-------|
| AANDBUSABLE_CNT_U08 | 1          | uint08 | 3     |
| ONLYBUSABLE_CNT_U08 | 1          | uint08 | 2     |
| ONLYAUSABLE_CNT_U08 | 1          | uint08 | 1     |
| NONEUSABLE_CNT_U08  | 1          | uint08 | 0     |
| BOTHVALID_CNT_U08   | 1          | uint08 | 2     |
| ONEISVALID_CNT_U08  | 1          | uint08 | 1     |
| NONEVALID_CNT_U08   | 1          | uint08 | 0     |

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

None

#### Periodic sub-module {\_Per()}

HwAgCorrlnPer1 (Refer FDD for details)

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

#### Local Function \#1

|                      |                      |          |               |               |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | HwAgSigAvlChk        | Type     | Min           |               | Max |
| **Arguments Passed** | SigRollg_Cnt_T_u08   | uint8    | 0             | 255           |     |
|                      | SigQlfr_Cnt_T_enum   | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |     |
|                      | \*LstRollg_Cnt_T_u08 | uint8    | 0             | 255           |     |
|                      | \*LstStall_Cnt_T_u08 | uint8    | 0             | 255           |     |
| **Return Value**     | SigAvl_Cnt_T_lgc     | boolean  | FALSE         | TRUE          |     |

##### **Description**

‘HwAgAAvlChk’ and ‘HwAgBAvlChk’ blocks in FDD have same functionality.
This routine is implemented for that logic.

### Transition Functions

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD - ES239A_HwAgCorrln_Design                                                                                                                                        | See Synergy sub project version |

{% endraw %}