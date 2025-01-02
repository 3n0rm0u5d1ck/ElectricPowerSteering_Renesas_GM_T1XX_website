---
layout: default
title: HwAgArbn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgArbn**

**Aug 4, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Spandana Balani,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |            |             |             |
|-----------------|------------|-------------|-------------|
| **Description** | **Author** | **Version** | **Date**    |
| Initial Version | SB         | 1.0         | 04-Aug-2015 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 HwAgArbn & High-Level Description
[6](#hwagarbn-high-level-description)](#hwagarbn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwAgArbn
[7](#graphical-representation-of-hwagarbn)](#graphical-representation-of-hwagarbn)

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
[9](#init-component-name_initn)](#init-component-name_initn)

[5.1.2 Per: HwAgArbnPer1 [9](#per-hwagarbnper1)](#per-hwagarbnper1)

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

#  HwAgArbn & High-Level Description

*Refer FDD*

# Design details of software module

*Refer FDD*

## Graphical representation of HwAgArbn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES238A_HwAgArbn_Impl/doc/mediax/media/image1.png"
style="width:1.98958in;height:3.07292in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name             | Resolution | Units | Value |
|---------------------------|------------|-------|-------|
| CORRLNSTSMASKSIGA_CNT_U08 | 1          | Cnt   | 0x01  |
| CORRLNSTSMASKSIGB_CNT_U08 | 1          | Cnt   | 0x02  |

# Software Component Implementation

Refer FDD

## Sub-Module Functions

## Init: \<Component Name\>\_Init\<n\>

None

## Per: HwAgArbnPer1

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                          |          |               |               |
|--------------|------------------------------|---------|-----------|-----------|
| **Function Name**    | CorrSigAvlChkRev1        | Type     | Min           | Max           |
| **Arguments Passed** | SigRollgCnt_Cnt_T_u08    | uint8    | 0             | 255           |
|                      | SigQlfr_Cnt_T_enum       | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \* LstRollgCnt_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | \* StallCnt_Cnt_T_u08    | uint8    | 0             | 255           |
| **Return Value**     | SigAvl_Cnt_T_lgc         | boolean  | 0             | 1             |

## Design Rationale

None

## Processing

Refer FDD CorrSigAvlChkRev1 State flow Chart

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | Process 04.02.00               |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 04.02.00               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 04.02.00               |
| 5           | FDD – ES238A_HwAgArbn_Design                                                                                                                                          | See Synergy SubProject version |

{% endraw %}