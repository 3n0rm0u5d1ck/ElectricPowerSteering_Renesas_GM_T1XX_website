---
layout: default
title: CM800A_SycnCrc_MDD
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**SyncCrc**

**January 11, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Kevin Smith,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                     |            |             |           |                 |
|--------------------|------------------|------------|------------|------------|
| **Description**                     | **Author** | **Version** | **Date**  | **Approved By** |
| Initial Version                     | K. Smith   | 1           | 07-Oct-15 |                 |
| Updates to meet the Rev1 of the FDD | K. Smith   | 2           | 11-Jan-16 |                 |

**<u>  
</u>**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 SyncCrc & High-Level Description
[6](#synccrc-high-level-description)](#synccrc-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of SyncCrc
[7](#graphical-representation-of-synccrc)](#graphical-representation-of-synccrc)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[4.2 Variable Data Dictionary
[8](#variable-data-dictionary)](#variable-data-dictionary)

[4.2.1 User Defined Typedef Definition/Declaration
[8](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[4.2.2 User Defined Enumerated Types
[9](#user-defined-enumerated-types)](#user-defined-enumerated-types)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: SyncCrcInit0 [10](#init-synccrcinit0)](#init-synccrcinit0)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Processing [10](#processing)](#processing)

[5.1.1.3 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Init: SyncCrcInit1 [10](#init-synccrcinit1)](#init-synccrcinit1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Processing [10](#processing-1)](#processing-1)

[5.1.2.3 Module Outputs [10](#module-outputs-1)](#module-outputs-1)

[5.2 Server Runnables [11](#server-runnables)](#server-runnables)

[5.2.1 ResvCrcHwUnit [11](#resvcrchwunit)](#resvcrchwunit)

[5.2.1.1 Design Rationale
[11](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[11](#processing-of-function)](#processing-of-function)

[5.2.1.3 Module Outputs [13](#module-outputs-2)](#module-outputs-2)

[5.2.2 CRC API Server Runnables
[14](#crc-api-server-runnables)](#crc-api-server-runnables)

[5.2.2.1 API Design Rationale
[14](#api-design-rationale)](#api-design-rationale)

[5.2.2.2 API Processing [14](#api-processing)](#api-processing)

[5.3 Interrupt Functions
[17](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[17](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 RelsCrcHwUnit [17](#relscrchwunit)](#relscrchwunit)

[5.4.1.1 Design Rationale
[17](#design-rationale-3)](#design-rationale-3)

[5.4.1.2 Processing [17](#processing-2)](#processing-2)

[5.4.2 NONTRUSTED_NtWrapS_SyncCrc_RelsCrcHwUnit
[17](#nontrusted_ntwraps_synccrc_relscrchwunit)](#nontrusted_ntwraps_synccrc_relscrchwunit)

[5.4.2.1 Design Rationale
[17](#design-rationale-4)](#design-rationale-4)

[5.4.2.2 Processing [18](#processing-3)](#processing-3)

[5.4.3 GetAvlCrcHwUnit [18](#getavlcrchwunit)](#getavlcrchwunit)

[5.4.3.1 Design Rationale
[18](#design-rationale-5)](#design-rationale-5)

[5.4.3.2 Processing [18](#processing-4)](#processing-4)

[5.4.4 NONTRUSTED_NtWrapS_SyncCrc_GetAvlCrcHwUnit
[19](#nontrusted_ntwraps_synccrc_getavlcrchwunit)](#nontrusted_ntwraps_synccrc_getavlcrchwunit)

[5.4.4.1 Design Rationale
[19](#design-rationale-6)](#design-rationale-6)

[5.4.4.2 Processing [19](#processing-5)](#processing-5)

[5.4.5 CrcRegCfg [19](#crcregcfg)](#crcregcfg)

[5.4.5.1 Design Rationale
[19](#design-rationale-7)](#design-rationale-7)

[5.4.5.2 Processing [19](#processing-6)](#processing-6)

[5.5 GLOBAL Function/Macro Definitions
[21](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[22](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[23](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[24](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [25](#glossary)](#glossary)

[Appendix C References [26](#references)](#references)

# Introduction

## Purpose

This MDD aids in documenting the implementation of CM800A for the
synchronous CRC API with the EA4 hardware CRC units.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# SyncCrc & High-Level Description

Provides an API interface for other BSW and application level software
components to calculate a synchronous CRC calculation using the EA4
hardware peripherals.

# Design details of software module

## Graphical representation of SyncCrc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image1.jpg"
style="width:2.67164in;height:2.63602in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Values between the brackets \[\] are the ranges that the configurable
constants could be defined as for a given integration. These values are
generated by Configurator before the software build.

| Constant Name             | Resolution | Units | Value                    |
|---------------------------|------------|-------|--------------------------|
| CRCININVAL8BIT_CNT_U08    | Uint8      | Cnt   | 0xFF                     |
| CRCININVAL16BIT_CNT_U16   | Uint16     | Cnt   | 0xFFFF                   |
| CRCININVAL32BIT_CNT_U32   | Uint32     | Cnt   | 0xFFFFFFFF               |
| CRCERRVAL_CNT_U08         | Uint8      | Cnt   | 0                        |
| CRCHWRESVCFGRNG_CNT_U08   | Uint8      | Cnt   | 7                        |
| INVLDTASKID_CNT_U16       | Uint16     | Cnt   | 0xFFFF                   |
| NROFCRCHWUNIT_CNT_U08     | Uint8      | Cnt   | 4                        |
| NROFACTVCRCHWUNIT_CNT_U08 | Uint8      | Cnt   | \[0 – 4\]\*              |
| ARWRPRENAD_CNT_U08        | Uint8      | Cnt   | \[STD_OFF – STD_ON\]\*\* |
| CRCOSREF_CNT_U08          | Uint8      | Cnt   | \[0-255\]\*\*\*          |

\* Based on the value of “Available CRC Hardware Units” as defined in
Configurator.  
\*\* Based on the value of “Autosar Wrapper Enable” as defined in
Configurator.  
\*\*\*Based on the value of “Crc Os Application Reference” as defined in
Configurator.

## Variable Data Dictionary

The following type definitions are found in the private header of this
component.

### User Defined Typedef Definition/Declaration

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NtCrcIdRec</td>
<td>CrcHwIdx</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>NtResvCallRec</td>
<td>ResvCall</td>
<td>Boolean</td>
<td>FALSE</td>
<td>TRUE</td>
</tr>
</tbody>
</table>

### User Defined Enumerated Types 

| Enum Name        | Element Name          | Value |
|------------------|-----------------------|-------|
| CrcDataAcsWidth1 | CRCDATAACSWIDTH_32BIT | 0     |
|                  | CRCDATAACSWIDTH_16BIT | 1     |
|                  | CRCDATAACSWIDTH_8BIT  | 2     |
| CrcAlg1          | CRCALG_32BITETH       | 0     |
|                  | CRCALG_16BIT          | 1     |
|                  | CRCALG_8BIT           | 2     |
|                  | CRCALG_8BITH2F        | 3     |

# Software Component Implementation

## Sub-Module Functions

## Init: SyncCrcInit0

## Design Rationale

This function initializes the PIM with the proper status for the CRC
hardware units for use by the application components. This function is
defined in the CDD_SyncCrcNonRte.c file as it shall be called prior to
the RTE Init functions.

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image2.emf)

## Module Outputs

None

## Init: SyncCrcInit1

## Design Rationale

Stub function for mapping the server runnable functions within a memory
region.

## Processing

None

## Module Outputs

None

## Server Runnables 

## ResvCrcHwUnit

## Design Rationale

This function allows the caller to reserve a single CRC hardware unit
until it is released. This will allow features such as the DMA to
perform a CRC calculation over a large portion of data and does not need
to permanently reserve a CRC hardware unit. This function can be called
from within or outside a task. This server runnables must be defined
with “can be invoked concurrently” enabled in Developer.

##  (Processing of function)………

##### Top Level Logic

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image3.emf)

##### Reserve CRC

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image4.emf)

##### Release CRC

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image5.emf)

## Module Outputs

None

## CRC API Server Runnables

## API Design Rationale

The following flow chart is applicable to all CRC API functions in this
document. However, the highlighted green squares vary by the API. These
differences will be pointed out in each sub-function section. All API
client calls must be called from within a task. These server runnables
must be defined with “can be invoked concurrently” enabled in Developer.

##  API Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image6.emf)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image7.emf)

##### Calc8BitCrc_Oper

DCRA\[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH_8BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_8BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL8BIT_CNT_U16;

##### Calc8BitCrc0X2F_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH_8BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_8BITH2F;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL8BIT_CNT_U16;

##### Calc16BitCrc_u08_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_16BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL16BIT_CNT_U16;

##### Calc16BitCrc_u16_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH_16BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_16BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL16BIT_CNT_U16;

##### Calc32BitCrc_u08_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_32BITETH;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL32BIT_CNT_U16;

##### Calc32BitCrc_u16_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH_16BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_32BITETH;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL32BIT_CNT_U16;

##### Calc32BitCrc_u32_Oper

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.ISZ = CRCDATAACSWIDTH_32BIT;

DCRA \[CrcHwIdx_Cnt_T_u08\].CTL.BIT.POL = CRCALG_32BITETH;

DCRA \[CrcHwIdx_Cnt_T_u08\].COUT = CRCININVAL32BIT_CNT_U16;

## Interrupt Functions

None

## Module Internal (Local) Functions

## RelsCrcHwUnit

|                      |                    |       |     |     |
|----------------------|--------------------|-------|-----|-----|
| **Function Name**    | RelsCrcHwUnit      | Type  | Min | Max |
| **Arguments Passed** | CrcHwIdx_Cnt_T_u08 | Uint8 | 0   | 3   |
| **Return Value**     | N/A                |       |     |     |

## Design Rationale

To minimize time in Exclusive areas, the Enter and Exit calls were
placed within this function. All API server runnables that use this
function are defined in Developer to have access to the exclusive area.

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image8.emf)

## NONTRUSTED_NtWrapS_SyncCrc_RelsCrcHwUnit

|                      |                                          |        |     |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | NONTRUSTED_NtWrapS_SyncCrc_RelsCrcHwUnit | Type   | Min | Max     |
| **Arguments Passed** | FunctionIndex                            | Uint16 | 0   | 65535   |
|                      | FunctionParams                           | Void\* | 0   | 2\^32-1 |
| **Return Value**     | N/A                                      |        |     |         |

## Design Rationale

Function is required to prevent MPU violations when the API modifies the
per-instance-memory used by all API functions.

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image9.emf)

## GetAvlCrcHwUnit

|                      |                 |      |     |     |
|----------------------|-----------------|------|-----|-----|
| **Function Name**    | GetAvlCrcHwUnit | Type | Min | Max |
| **Arguments Passed** | N/A             |      |     |     |
| **Return Value**     | N/A             |      |     |     |

## Design Rationale

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image10.emf)

## NONTRUSTED_NtWrapS_SyncCrc_GetAvlCrcHwUnit

|                      |                                            |        |     |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | NONTRUSTED_NtWrapS_SyncCrc_GetAvlCrcHwUnit | Type   | Min | Max     |
| **Arguments Passed** | FunctionIndex                              | Uint16 | 0   | 65535   |
|                      | FunctionParams                             | Void\* | 0   | 2\^32-1 |
| **Return Value**     | N/A                                        |        |     |         |

## Design Rationale

Function is required to prevent MPU violations when the API modifies the
per-instance-memory used by all API functions.

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image11.emf)

## CrcRegCfg

|                      |              |               |     |            |
|----------------------|--------------|---------------|-----|------------|
| **Function Name**    | CrcRegCfg    | Type          | Min | Max        |
| **Arguments Passed** | CrcHwIdx_Arg | Uint8         | 0   | 255        |
|                      | CrcCfg_Arg   | CrcHwResvCfg1 | 0   | 6          |
|                      | StrtVal_Arg  | Uint32        | 0   | 4294967295 |
| **Return Value**     | N/A          |               |     |            |

## Design Rationale

Function created to reduce the complexity of the ResvCrcHwUnit_Oper
function.

## Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Impl/doc/mediax/media/image12.emf)

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

1.  API client calls, except ResvCrcHwUnit, must be called from within a
    task.

2.  To meet design and coding standards, ‘For’ loops called out by the
    FDD were implemented with ‘While’ loops to break out of the loops
    without using the ‘break’ keyword.

# UNIT TEST CONSIDERATION

The constants NROFACTVCRCHWUNIT_CNT_U08, ARWRPRENAD_CNT_U08, and
CRCOSREF_CNT_U08 shall be tested to their full range as defined in the
constant section.

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}