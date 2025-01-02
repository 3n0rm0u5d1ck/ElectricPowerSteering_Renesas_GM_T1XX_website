---
layout: default
title: GuardCfgAndDiagc Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GuardCfgAndDiagc**

**Mar 31 , 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                        |               |             |          |
|------------------------|---------------------|--------------|--------------|
| **Description**                                        | **Author**    | **Version** | **Date** |
| Initial Version                                        | Avinash James | 1.0         | 02/16/16 |
| Updates for PBG Register Lock bits and Syncm inclusion | Avinash James | 2.0         | 03/31/16 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 GuardCfgAndDiagc & High-Level Description
[6](#guardcfganddiagc-high-level-description)](#guardcfganddiagc-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of GuardCfgAndDiagc
[7](#graphical-representation-of-guardcfganddiagc)](#graphical-representation-of-guardcfganddiagc)

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

[5.1.1 Init: GuardCfgAndDiagcInit1
[9](#init-guardcfganddiagcinit1)](#init-guardcfganddiagcinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Init: GuardCfgAndDiagcInit2
[9](#init-guardcfganddiagcinit2)](#init-guardcfganddiagcinit2)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [9](#module-outputs-1)](#module-outputs-1)

[5.1.3 Init: GuardCfgAndDiagcInit3
[9](#init-guardcfganddiagcinit3)](#init-guardcfganddiagcinit3)

[5.1.3.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Module Outputs [9](#module-outputs-2)](#module-outputs-2)

[5.1.4 Per: None [9](#per-none)](#per-none)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 ConfigureFilterN [10](#configurefiltern)](#configurefiltern)

[5.4.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.4.1.2 Processing [10](#processing)](#processing)

[5.4.2 ChkForPBGErr [10](#chkforpbgerr)](#chkforpbgerr)

[5.4.2.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.4.2.2 Processing [10](#processing-1)](#processing-1)

[5.4.3 ChkForECMErr [10](#chkforecmerr)](#chkforecmerr)

[5.4.3.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.4.3.2 Processing [11](#processing-2)](#processing-2)

[5.4.4 Vrfy32BitPBGRegAcs
[11](#vrfy32bitpbgregacs)](#vrfy32bitpbgregacs)

[5.4.4.1 Design Rationale
[11](#design-rationale-6)](#design-rationale-6)

[5.4.4.2 Processing [11](#processing-3)](#processing-3)

[5.4.5 Vrfy16BitPBGRegAcs
[11](#vrfy16bitpbgregacs)](#vrfy16bitpbgregacs)

[5.4.5.1 Design Rationale
[11](#design-rationale-7)](#design-rationale-7)

[5.4.5.2 Processing [11](#processing-4)](#processing-4)

[5.4.6 Vrfy8BitPBGRegAcs [11](#vrfy8bitpbgregacs)](#vrfy8bitpbgregacs)

[5.4.6.1 Design Rationale
[11](#design-rationale-8)](#design-rationale-8)

[5.4.6.2 Processing [11](#processing-5)](#processing-5)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [12](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[12](#design-rationale-9)](#design-rationale-9)

[5.5.1.2 Processing [12](#processing-6)](#processing-6)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# Introduction

## Purpose

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# GuardCfgAndDiagc & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of GuardCfgAndDiagc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Impl/doc/mediax/media/image1.jpg"
style="width:2.40833in;height:1.475in" />

## Data Flow Diagram

### Component level DFD

*See FDD*

### Function level DFD

*See FDD*

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                    | Resolution | Units      | Value                   |
|---------------------------------|---------------|-----------|-------------|
| **PBGPROTNCMN_CNT_U32**          | **1**      | **uint32** | **0x0405FE1FU**         |
| **PBGUSRMODENA_CNT_U32**         | **1**      | **uint32** | **0x02000000U**         |
| **PBGUSRMODDI_CNT_U32**          | **1**      | **uint32** | **0x00000000U**         |
| **PBGSPID321ENA_CNT_U32**        | **1**      | **uint32** | **0x000001C0U**         |
| **PBGSPID31ENA_CNT_U32**         | **1**      | **uint32** | **0x00000140U**         |
| **PBGSPID21ENA_CNT_U32**         | **1**      | **uint32** | **0x000000C0U**         |
| **PBGSPID1ENA_CNT_U32**          | **1**      | **uint32** | **0x00000040U**         |
| **PBGSETNOREADWRACS_CNT_U32**    | **1**      | **uint32** | **0x405FE5CU**          |
| **NROF8BITREG_CNT_U08**          | **1**      | **uint8**  | **((uint8)0x09)**       |
| **NROF32BITREG_CNT_U08**         | **1**      | **uint8**  | **((uint8)0x02)**       |
| **READERRBIT_CNT_U32**           | **1**      | **uint32** | **((uint32)1U\<\<6U)**  |
| **WRERRBIT_CNT_U32**             | **1**      | **uint32** | **((uint32)1U\<\<7U)**  |
| **CFGERRBIT_CNT_U32**            | **1**      | **uint32** | **((uint32)1U\<\<8U)**  |
| **PBGERRBIT_CNT_U32**            | **1**      | **uint32** | **((uint32)1U\<\<9U)**  |
| **ECMERRBIT_CNT_U32**            | **1**      | **uint32** | **((uint32)1U\<\<10U)** |
| **REGTYPE8BIT_CNT_U32**          | **1**      | **uint32** | **((uint32)0U\<\<4U)**  |
| **REGTYPE16BIT_CNT_U32**         | **1**      | **uint32** | **((uint32)1U\<\<4U)**  |
| **REGTYPE32BIT_CNT_U32**         | **1**      | **uint32** | **((uint32)2U\<\<4U)**  |
| **PBGSTRTUPTESTNOFAILR_CNT_U32** | **1**      | **uint32** | **0x0U**                |
| **PBGPROTNLOCKENA_CNT_U32**      | **1**      | **uint32** | **0x80000000U**         |

# Software Component Implementation

## Sub-Module Functions

### Init: GuardCfgAndDiagcInit1

## Design Rationale

*Non-RTE function for Guard configuration initialization of PEG, IPG,
and PBG so that guard protection can be initialized and enabled before
the RTE is started*

## Module Outputs

*Configuration registers for PEG, IPG, and PBG*

### Init: GuardCfgAndDiagcInit2

## Design Rationale

*RTE Empty function for purposes of memory mapping*

*See FDD for more.*

## Module Outputs

*None*

### Init: GuardCfgAndDiagcInit3

## Design Rationale

*Non-RTE function for Start Up Initialization test of PBG of Group 3A*

*See FDD for more.*

## Module Outputs

*None*

## Per: None

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

### ConfigureFilterN

|                      |                      |                   |     |            |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ConfigureFilterN     | Type              | Min | Max        |
| **Arguments Passed** | PbgProtReg           | volatile uint32\* | 0   | 0xFFFFFFFF |
|                      | Val                  | uint32            | 0   | 0xFFFFFFFF |
|                      | PbgStrtUpTestFailSts | Uint32 \*         | 0   | 0xFFFFFFFF |
| **Return Value**     | None                 |                   |     |            |

## Design Rationale

This local function sets the value **Val** to the register address
**PbgProtReg** passed as the arguments and verifies the write operation
was successful. If not a diagnostic is set.

## Processing

Figure 4.5.3 from SAN ver 1.20

### ChkForPBGErr

|                      |                      |           |     |            |
|----------------------|----------------------|-----------|-----|------------|
| **Function Name**    | ChkForPBGErr         | Type      | Min | Max        |
| **Arguments Passed** | PbgStrtUpTestFailSts | Uint32 \* | 0   | 0xFFFFFFFF |
|                      |                      |           |     |            |
| **Return Value**     | None                 |           |     |            |

## Design Rationale

This local function checks PBG access violation error is captured. If
not set diagnostic, clear the error and if the error doesn’t clear set
diagnostic.

## Processing

Figure 4.5.3 from SAN ver 1.20

### ChkForECMErr

|                      |                      |           |     |            |
|----------------------|----------------------|-----------|-----|------------|
| **Function Name**    | ChkForECMErr         | Type      | Min | Max        |
| **Arguments Passed** | PbgStrtUpTestFailSts | Uint32 \* | 0   | 0xFFFFFFFF |
|                      |                      |           |     |            |
| **Return Value**     | None                 |           |     |            |

## Design Rationale

This local function checkscwhether ECM captures the error sets
diagnostic message and clears the ECM errors after the check else set
diagnostic.

## Processing

Refer FDD 4.5.3 Implementation

### Vrfy32BitPBGRegAcs

|                      |                      |           |     |            |
|----------------------|----------------------|-----------|-----|------------|
| **Function Name**    | Vrfy32BitPBGRegAcs   | Type      | Min | Max        |
| **Arguments Passed** | PbgStrtUpTestFailSts | Uint32 \* | 0   | 0xFFFFFFFF |
|                      |                      |           |     |            |
| **Return Value**     | None                 |           |     |            |

## Design Rationale

This is defined to reduce the path count and modularizes the check for
the 32 bit Access registers alone.

## Processing

### Vrfy16BitPBGRegAcs

|                      |                      |           |     |            |
|----------------------|----------------------|-----------|-----|------------|
| **Function Name**    | Vrfy16BitPBGRegAcs   | Type      | Min | Max        |
| **Arguments Passed** | PbgStrtUpTestFailSts | Uint32 \* | 0   | 0xFFFFFFFF |
|                      |                      |           |     |            |
| **Return Value**     | None                 |           |     |            |

## Design Rationale

This is defined to reduce the path count and modularizes the check for
the 16 bit Access registers alone.

## Processing

### Vrfy8BitPBGRegAcs

|                      |                      |           |     |            |
|----------------------|----------------------|-----------|-----|------------|
| **Function Name**    | Vrfy8BitPBGRegAcs    | Type      | Min | Max        |
| **Arguments Passed** | PbgStrtUpTestFailSts | Uint32 \* | 0   | 0xFFFFFFFF |
|                      |                      |           |     |            |
| **Return Value**     | None                 |           |     |            |

## Design Rationale

This is defined to reduce the path count and modularizes the check for
the 8 bit Access registers alone.

## Processing

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |     |      |     |     |
|----------------------|-----|------|-----|-----|
| **Function Name**    |     | Type | Min | Max |
| **Arguments Passed** |     |      |     |     |
|                      |     |      |     |     |
| **Return Value**     |     |      |     |     |

## Design Rationale

## Processing

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