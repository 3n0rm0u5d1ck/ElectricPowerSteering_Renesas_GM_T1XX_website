---
layout: default
title: FlsMem Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**FlsMem**

**Aug 25 , 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                                                               |                |             |          |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                                                               | **Author**     | **Version** | **Date** |
| Initial Version                                                                                               | Lucas Wendling | 1.0         | 10/06/15 |
| Updated with changes for DTS configuration for Flash CRC check                                                | Avinash James  | 2.0         | 03/18/16 |
| Updates for DTS Transfer Clear                                                                                | Avinash James  | 3.0         | 3/29/16  |
| Updated for removing the flash ECC single bit error handling and disabling the DTS channels after calculation | Avinash James  | 4.0         | 3/31/16  |
| Trusted function call for the DTS clean up updates                                                            | Avinash James  | 5.0         | 04/18/16 |
| Function name changes and added CodFlsSngBitEcc handler for single bit code flash ecc                         | Avinash James  | 6.0         | 08/25/16 |

**  
**

<u>Table of Contents</u>[1 Introduction
[5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 FlsMem & High-Level Description
[6](#flsmem-high-level-description)](#flsmem-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of FlsMem
[7](#graphical-representation-of-flsmem)](#graphical-representation-of-flsmem)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Variable Data Dictionary
[9](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[9](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[9](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[6.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[6.1.1 Init: FlsMemInit1 [10](#init-flsmeminit1)](#init-flsmeminit1)

[6.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[6.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[6.1.2 Init: FlsMemInit2 [10](#init-flsmeminit2)](#init-flsmeminit2)

[6.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[6.1.2.2 Module Outputs [10](#module-outputs-1)](#module-outputs-1)

[6.1.3 Per: FlsMemPer2 [10](#per-flsmemper2)](#per-flsmemper2)

[6.1.3.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[6.1.3.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[6.1.3.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[6.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[6.2 Server Runnables
[11](#server-runnables---codflssngbitecc)](#server-runnables---codflssngbitecc)

[6.3 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[6.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[6.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[6.4.1.1 Design Rationale
[11](#design-rationale-4)](#design-rationale-4)

[6.4.1.2 Processing [11](#processing)](#processing)

[6.5 GLOBAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6.5.1 DTSInit [11](#dtsinin)](#dtsinin)

[6.5.1.1 Design Rationale
[11](#design-rationale-5)](#design-rationale-5)

[6.5.1.2 Processing [14](#processing-1)](#processing-1)

[6.5.2 DTSClnUp [14](#dtsclnup)](#dtsclnup)

[6.5.2.1 Design Rationale
[14](#design-rationale-6)](#design-rationale-6)

[6.5.2.2 Processing [14](#processing-2)](#processing-2)

[7 Known Limitations with Design
[15](#known-limitations-with-design)](#known-limitations-with-design)

[8 UNIT TEST CONSIDERATION
[16](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[17](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [18](#glossary)](#glossary)

[Appendix C References [19](#references)](#references)

# Introduction

## Purpose

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# FlsMem & High-Level Description

*See FDD*

# Design details of software module

## Graphical representation of FlsMem

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM102A_FlsMem_Impl/doc/mediax/media/image1.png"
style="width:2.80764in;height:2.02569in" />

## Data Flow Diagram

### Component level DFD

*See FDD*

### Function level DFD

*See FDD*

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                | Resolution | Units      | Value             |
|------------------------------|------------|------------|-------------------|
| **CPU1PEID_CNT_U32**         | **1**      | **uint32** | **0x01U**         |
| **CODFLSTOCRCSPID_CNT_U32**  | **1**      | **uint32** | **0x02U**         |
| **CRCTOLCLRAMSPID_CNT_U32**  | **1**      | **uint32** | **0x00U**         |
| **USRMODDIS_CNT_U32**        | **1**      | **uint32** | **0x00U**         |
| **FLSBLKLEN_CNT_U32**        | **1**      | **uint32** | **0x0003FFFCU**   |
| **DTSDATALEN_CNT_U32**       | **1**      | **uint32** | **4U**            |
| **CRCCHKMAXALLWDTI_CNT_U32** | **1**      | **uint32** | **2000**          |
| **MAXNROFDTSCH_CNT_U32**     | **1**      | **uint32** | **32**            |
| **DUMMYREADADDR1_CNT_U32**   | **1**      | **uint32** | **(0xFFFFFE1FU)** |
| **DUMMYREADADDR2_CNT_U32**   | **1**      | **uint32** | **(0xFFFFFE2FU)** |
| **DUMMYREADADDR3_CNT_U32**   | **1**      | **uint32** | **(0xFFFFFE4FU)** |
| **DUMMYREADADDR4_CNT_U32**   | **1**      | **uint32** | **(0xFFFFFE8FU)** |

# Variable Data Dictionary

## User defined typedef definition/declaration 

*\<This section documents any user types uniquely used for the
module.\>*

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
<td>FlsCrcCfgBlkRec</td>
<td>CrcFlsBlkStrtAdr</td>
<td>uint32</td>
<td>0</td>
<td>0xFFFFFFFFH</td>
</tr>
<tr class="even">
<td></td>
<td>CrcFlsBlkLen</td>
<td>uint32</td>
<td>0</td>
<td>0xFFFFFFFFH</td>
</tr>
<tr class="odd">
<td></td>
<td>PreCalcnCrcFlsAdr</td>
<td>uint32*</td>
<td>0</td>
<td>0xFFFFFFFFH</td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 40%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Enum Name</th>
<th>Element Name</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;(Name given for the user defined typdef of type
struct/union)</p>
<p>(Variable name qualified in refer[2])&gt;</p></td>
<td>&lt;(Variable name qualified Refer[2])&gt;</td>
<td>&lt;Define the value &gt;</td>
</tr>
</tbody>
</table>

# Software Component Implementation

## Sub-Module Functions

## Init: FlsMemInit1

## Design Rationale

*Empty function for purposes of memory mapping*

## Module Outputs

*None*

## Init: FlsMemInit2

## Design Rationale

*The FlsMemInit2 function is a non RTE function which shall be called to
set up the DTS configuration for the Flash CRC check. The DTS channel
configuration has to be applied only when the system is waking up from a
Power On Reset or after a flash programming reset. In such a scenario a
Hardware CRC unit is allocated by function call to the CRC module and
once a hardware assignment is successful, the DTS channels are
configured for chaining for the entire definition of the flash blocks
(Boot, App, Cal1, Cal2 etc.). Record the time when the DTS transfer is
initiated so that a check on a timeout can be made in the periodic
function where a maximum timeout of 200 ms is checked for*

*This function shall be called in the startup sequence. Hence it is a
non RTE function*

*See FDD for more.*

## Module Outputs

*None*

*None*

## Per: FlsMemPer2

## Design Rationale

*See FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnables - CodFlsSngBitEcc

## Design Rationale

*See FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     |                   |                               |                               |                               |

## Design Rationale

## Processing

## GLOBAL Function/Macro Definitions

## DtsInin

|                      |                |        |     |            |
|----------------------|----------------|--------|-----|------------|
| **Function Name**    | DTSInit        | Type   | Min | Max        |
| **Arguments Passed** | CrcHwIdxInReg  | uint32 | 0   | 0xFFFFFFFF |
|                      | CrcHwIdxOutReg | uint32 | 0   | 0xFFFFFFFF |
| **Return Value**     | None           |        |     |            |

## Design Rationale

Trusted function that performs all register initialization from the
CM102A_FlsMem_DTSPeripheralCfg.xlsx spreadsheet in the FDD. The
DTSMstrCfg channel master registers can be written only in supervisor
mode. After the Channel master register for a given channel has been
written, the selected Processor Element can write to that channel’s
registers. However, for simplicity, all DTS register initialization and
chaining is being done in one trusted function.

The chaining is done in the following manner

1.  Consider the first flash region to have the CRC calculated

2.  Calculate the number of DTS chains required for the length of the
    CRC region. Each DTS channel can address up to a maximum of 0x3FFFC
    bytes of data (0xFFFF maximum transfer count multiplied by 4 bytes
    of data in each transfer).

Hence number of channel is equal to Region length/0x3FFFC + {1} if
(Region length % 0x3FFFC is non zero)

1.  Clear the DTS Transfer flag to make sure no pending requests are
    present for all the used channels

2.  Configure the DTS channels starting from 0 using the configuration
    defined as per CM102A_FlsMem_DTSPeripheralCfg.xlsx for the above
    calculated number of chains

3.  Configure the next DTS channel to transfer the CRC result from CRC
    HW output register to Per Instance Memory

4.  Configure the next DTS channel to transfer zero value to the CRC HW
    output register to clear the output register to continue with next
    flash region operation

5.  Repeat Step 1 thru 5 for all the flash regions(Boot, App, Cal1, Cal2
    etc) The definition of the flash region is in the generated file
    CDD_FlsMem_Cfg.c which takes inputs defined in the Vector
    configurator Tool

6.  Disable chaining on the last channel

7.  Enable the Interrupt on the second last channel

8.  Clear the interrupt status register which shall be monitored in the
    periodic

9.  Start the DTS transfer

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM102A_FlsMem_Impl/doc/mediax/media/image2.emf)

## Processing

## DtsClnUp

|                      |          |      |     |     |
|----------------------|----------|------|-----|-----|
| **Function Name**    | DTSClnUp | Type | Min | Max |
| **Arguments Passed** | None     |      |     |     |
|                      |          |      |     |     |
| **Return Value**     | None     |      |     |     |

## Design Rationale

***None***

## Processing

*None*

# Known Limitations with Design

We have made use of a static constant global variable (**static const
uint32 CrcClrData_M = 0U**) for the purpose of clearing the CRC hardware

Also the result array (**HwCrcCalcdRes_C\[8\]**) has been also declared
as a global array for the purpose of DTS write access in the
MotCtrlMgr_MemMap memory map section

In the CodFlsSngBitEcc function in FDD the reads are done to the same
variable. In the implementation we have used 4 different variables for
the purpose that compiler wont optimize those reads. Any optimization
settings change in the compiler would need a reevaluation of the use of
volatile temporary variables

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0               |

{% endraw %}