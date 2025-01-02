---
layout: default
title: DampgPahFwl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**DampgPahFwl**

**February 9, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Akhil Krishna N D (Tata Elxsi),**

**Trivandrum, INDIA**

**<u>Change</u>** History

|                 |                   |             |             |
|-----------------|-------------------|-------------|-------------|
| **Description** | **Author**        | **Version** | **Date**    |
| Initial Version | Akhil Krishna N D | 1.0         | 09-Feb-2016 |

**<u>Table of Contents</u>**

[1 Introduction 5](#introduction)

[1.1 Purpose 5](#purpose)

[2 DampgPahFwl & High-Level Description
6](#dampgpahfwl-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of DampgPahFwl
7](#graphical-representation-of-dampgpahfwl)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: DampgPahFwlInit1 9](#init-dampgpahfwlinit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.2 Per: DampgPahFwlPer1 9](#per-dampgpahfwlper1)

[5.2.1.1 Design Rationale 9](#design-rationale-1)

[5.2.1.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.2.1.3 (Processing of function)……… 9](#processing-of-function)

[5.2.1.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.3 Server Runables 9](#server-runables)

[5.4 Interrupt Functions 9](#interrupt-functions)

[5.5 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.5.1 Local Function \#1 9](#local-function-1)

[5.5.1.1 Design Rationale 9](#design-rationale-2)

[5.5.1.2 Processing 10](#processing)

[5.5.2 Local Function \#2 10](#local-function-2)

[5.5.2.1 Design Rationale 10](#design-rationale-3)

[5.5.2.2 Processing 10](#processing-1)

[5.5.3 Local Function \#3 10](#local-function-3)

[5.5.3.1 Design Rationale 10](#design-rationale-4)

[5.5.3.2 Processing 10](#processing-2)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 15](#references)

# Introduction

## Purpose

# DampgPahFwl & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of DampgPahFwl

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF035A_DampgPahFwl_Impl/doc/mediax/media/image1.png"
style="width:3.55208in;height:6.01181in" />

## Data Flow Diagram

Please refer FDD

### Component level DFD

Please refer FDD

### Function level DFD

Please refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                   |            |       |       |
|-----------------------------------|------------|-------|-------|
| Constant Name                     | Resolution | Units | Value |
| NODEBSTEP_CNT_U16                 | 1          | Cnt   | 65535 |
| Please refer .m file for the rest |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: DampgPahFwlInit1

## Design Rationale

None

## Module Outputs

None

## Per: DampgPahFwlPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

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

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | DebncDmpCmdOverBound           | Type    | Min   | Max  |
| **Arguments Passed** | DampgCmdFWOverBound_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | DampgCmdFailSts_Cnt_T_logl     | boolean | FALSE | TRUE |

## Design Rationale

None

## Processing

Please refer Debounce Damp Cmd Overboundary block in FDD

## Local Function \#2

|                      |                                 |         |       |      |
|--------------|-------------------------------|-----------|---------|---------|
| **Function Name**    | DebncVBICOverBound              | Type    | Min   | Max  |
| **Arguments Passed** | InertiaCmpFwlOverBnd_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | VBICCmdFailSts_Cnt_T_logl       | boolean | FALSE | TRUE |

## Design Rationale

None

## Processing

Please refer ‘Debounce VBIC Overboundary’ block in FDD

## Local Function \#3

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | SetFaults                  | Type    | Min   | Max  |
| **Arguments Passed** | DampgFwlReached_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | VBICFwlReached_Cnt_T_logl  | boolean | FALSE | TRUE |
| **Return Value**     | None                       | NA      | NA    | NA   |

## Design Rationale

None

## Processing

Please refer ‘Set_Faults’ block in FDD

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

None.

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                             |
| 5           | FDD: SF035A_DampgPahFwl_Design                                                                                                                                | See Synergy sub project version |

{% endraw %}