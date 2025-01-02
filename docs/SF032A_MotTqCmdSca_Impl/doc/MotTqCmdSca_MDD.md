---
layout: default
title: MotTqCmdSca_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotTqCmdSca**

**Prepared For:**

**,**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
<u>Change History</u>**

|     |     |     |     |
|-----|-----|-----|-----|
|     |     |     |     |
|     |     |     |     |

|             |                            |                          |             |            |
|---------|------------------|------------------|-----------|-----------------|
| **Sl. No.** | **Description**            | **Author**               | **Version** | **Date**   |
| 1           | Initial version            | Kannappa Chidambaram P R | 1.0         | 01/21/2016 |
| 2           | Updated as per FDD v 1.2.0 | Krishna Anne             | 2.0         | 03/14/2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#_Toc441164420)](#_Toc441164420)

[2 MotTqCmdSca & High-Level Description
[6](#mottqcmdsca-high-level-description)](#mottqcmdsca-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of MotTqCmdSca
[7](#graphical-representation-of-mottqcmdsca)](#graphical-representation-of-mottqcmdsca)

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

[5.1.1 Init: MotTqCmdScaInit1
[9](#init-mottqcmdscainit1)](#init-mottqcmdscainit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#_Toc421011516)](#_Toc421011516)

[5.1.2 Per: MotTqCmdScaPer1
[9](#per-mottqcmdscaper1)](#per-mottqcmdscaper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#_Toc421011520)](#_Toc421011520)

[5.1.2.3 (Processing of function)………
[9](#_Toc421011521)](#_Toc421011521)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 SetMotTqCmdSca [9](#setmottqcmdsca)](#setmottqcmdsca)

[5.2.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[9](#processing-of-function-1)](#processing-of-function-1)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

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

# MotTqCmdSca & High-Level Description

Please refer FDD

# Design details of software module

## Graphical representation of MotTqCmdSca

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF032A_MotTqCmdSca_Impl/doc/mediax/media/image2.png"
style="width:4.14792in;height:3.72222in" />

## Data Flow Diagram

Please Refer FDD

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

## Init: MotTqCmdScaInit1

## Design Rationale

<span id="_Toc421011516" class="anchor"></span>Please refer FDD

## Module Outputs

Please refer FDD

###  [section]

## Per: MotTqCmdScaPer1

## Design Rationale

<span id="_Toc421011520" class="anchor"></span>Please refer FDD

## Store Module Inputs to Local copies

<span id="_Toc421011521" class="anchor"></span>Please refer FDD

##  (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

## SetMotTqCmdSca

## Design Rationale

Please refer FDD

##  (Processing of function)………

Please refer FDD

## Server Runables 

## GetMotTqCmdSca

## Design Rationale

Please refer FDD

##  (Processing of function)………

Please refer FDD

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process 4.02.00                 |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process 4.02.00                 |
| 5           | FDD: SF032A_MotTqCmdSca_Design                                                                                                                                        | See Synergy sub project version |

{% endraw %}