---
layout: default
title: ES400A_TunSelnMngt_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TunSelnMngt**

**August 29, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Kevin Smith,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                         |            |             |           |                 |
|--------------------|------------------|------------|------------|------------|
| **Description**                                         | **Author** | **Version** | **Date**  | **Approved By** |
| Initial Version                                         | K. Smith   | 1           | 07-Apr-16 |                 |
| Updated program flow diagrams                           | N. Saxton  | 2           | 06-May-16 |                 |
| Updates to flow charts for anomaly EA4#6672 corrections | K. Smith   | 3           | 29-Aug-16 |                 |

**<u>  
</u>**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 TunSelnMngt & High-Level Description
[6](#tunselnmngt-high-level-description)](#tunselnmngt-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of TunSelnMngt
[7](#graphical-representation-of-tunselnmngt)](#graphical-representation-of-tunselnmngt)

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

[4.2.1.1 Static Structures [8](#static-structures)](#static-structures)

[4.2.1.2 Dynamic Structures and Enums
[9](#dynamic-structures-and-enums)](#dynamic-structures-and-enums)

[4.2.2 User Defined Enumerated Types
[10](#user-defined-enumerated-types)](#user-defined-enumerated-types)

[5 Software Component Implementation
[11](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[11](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: TunSelnMngtInit1 [11](#init-init1)](#init-init1)

[5.1.2 Per: TunSelnMngtPer1 [13](#per-per1)](#per-per1)

[5.2 Server Runnables [15](#server-runnables)](#server-runnables)

[5.2.1 CopyCalPageReq [15](#copycalpagereq)](#copycalpagereq)

[5.2.2 GetCalPageReq [16](#getcalpagereq)](#getcalpagereq)

[5.2.3 GetSegInfoReq [17](#getseginforeq)](#getseginforeq)

[5.2.4 OnlineTunRamAdrMpg
[18](#onlinetunramadrmpg)](#onlinetunramadrmpg)

[5.2.5 SetCalPageReq [19](#setcalpagereq)](#setcalpagereq)

[5.3 Interrupt Functions
[20](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[20](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 SwtCalIdx [20](#swtcalidx)](#swtcalidx)

[5.4.2 IdxChgMngt [21](#idxchgmngt)](#idxchgmngt)

[5.4.3 MemCopy32Bit [23](#memcopy32bit)](#memcopy32bit)

[5.4.4 MemCopy8Bit [24](#memcopy8bit)](#memcopy8bit)

[5.4.5 SegModAdrInfo [25](#segmodadrinfo)](#segmodadrinfo)

[5.4.6 SegModStdInfo [26](#segmodstdinfo)](#segmodstdinfo)

[5.4.7 SegModAdrMpg [27](#segmodadrmpg)](#segmodadrmpg)

[5.5 GLOBAL Function/Macro Definitions
[28](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[29](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[30](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[31](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [32](#glossary)](#glossary)

[Appendix C References [33](#references)](#references)

# Introduction

## Purpose

This MDD aids in documenting the implementation of ES400A Tuning
Selection Management.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# TunSelnMngt & High-Level Description

Tuning Selection Management (TunSelnMngt) provides the ability to change
run-time calibrations during operation. The component also provides a
RAM buffer for online calibration changes over XCP for tuning processes.

# Design details of software module

## Graphical representation of TunSelnMngt

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image1.jpg"
style="width:3.42708in;height:2.4375in" />

## Data Flow Diagram

None

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Values between the brackets \[\] are the ranges that the configurable
constants could be defined as for a given integration. These values are
generated by Configurator before the software build.

| Constant Name               | Resolution | Units | Value       |
|-----------------------------|------------|-------|-------------|
| MAXINITIDXCNT_CNT_U08       | Uint8      | Cnt   | \[0-255\]   |
| MAXRTIDXCNT_CNT_U08         | Uint8      | Cnt   | \[0-255\]   |
| MAXONLINECALCFGCNT_CNT_U08  | Uint8      | Cnt   | \[0-255\]   |
| ONLINECALGROUPS_CNT_U08     | Uint8      | Cnt   | \[0-255\]   |
| ONLINECALRAMTBL_CNT_U16     | Uint16     | Cnt   | \[0-65535\] |
| PRMPTRTBLSIZEINWORD_CNT_U16 | Uint16     | Cnt   | \[0-65535\] |

## Variable Data Dictionary

The following type definitions are found in the private header of this
component.

### User Defined Typedef Definition/Declaration

## Static Structures

The following table contains structures are static in their definition.
However, internal elements may change based on the configuration of the
project but the high level content is the same. These elements are
described at the bottom of the table.

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 22%" />
<col style="width: 20%" />
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
<td>TunSelnRamTblRec1</td>
<td>PrmRefTblPtr</td>
<td>Rte_ParameterRefTabType</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="even">
<td></td>
<td>PrmTblCrc_u32</td>
<td>Uint32</td>
<td>0</td>
<td>4294967295</td>
</tr>
<tr class="odd">
<td>TunSelnIdxTblRec1</td>
<td>SrcIdx_u16</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="even">
<td></td>
<td>DestIdx_u16</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td></td>
<td>SigIdx_u08</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>TunSelnOnlineCalIdxTblRec1</td>
<td>RamStructPtr_u08</td>
<td>UInt8*</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="odd">
<td></td>
<td>StructSize_u16</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="even">
<td></td>
<td>TblIdx_u16</td>
<td>Uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td></td>
<td>GroupIdx_u08</td>
<td>Uint8</td>
<td>0</td>
<td>255</td>
</tr>
</tbody>
</table>

Rte_ParameterRefTabType is a structure of void pointers that point to
the various calibration component structures. This type is generated by
the RTE based on the configuration of the integration.

## Dynamic Structures and Enums

The following table contains structures are dynamic in their definition.
The contents contained will vary from project to project. The intent of
this table is to document their purpose.

<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 17%" />
<col style="width: 22%" />
<col style="width: 15%" />
<col style="width: 5%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th>Entry Type</th>
<th>Typedef Name</th>
<th>Example Element(s)</th>
<th>Variable Type</th>
<th>Value</th>
<th>Comment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Enum</td>
<td>OnlineCalGroup1</td>
<td>GroupA</td>
<td>N/A</td>
<td>0</td>
<td rowspan="2">This enum contains a number representation for each
calibration group that is generated for online calibration from A=0 to
Z=26. Groups are defined by a letter suffix.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>GroupB</td>
<td>N/A</td>
<td>1</td>
</tr>
<tr class="odd">
<td>Struct</td>
<td><p>&lt;GroupName&gt;Typ</p>
<p>GroupATyp</p></td>
<td><p>&lt;Cal Region&gt;&lt;Cal Cmp Name&gt;&lt;Online Group&gt;</p>
<p>CalRegn01CmnGroupA</p></td>
<td>RTE Generated</td>
<td>N/A</td>
<td>This structure is generated based on the online groups configured.
Each group will generate a structure and contain all calibration
software components within that group.</td>
</tr>
<tr class="even">
<td>Union</td>
<td>OnlineCalTblRec1</td>
<td>Byte[&lt;RAM Size&gt;]</td>
<td>Unit8</td>
<td>N/A</td>
<td rowspan="2">This structure combines all the online calibration
groups into data type for assignment to the RAM buffer. The ‘byte’
element is used to access the entire buffer on a byte-by-byte basis and
ensure that the RAM is properly sized.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>&lt;GroupName&gt;</td>
<td>&lt;GroupName&gt;Typ</td>
<td>N/A</td>
</tr>
</tbody>
</table>

### User Defined Enumerated Types 

| Enum Name          | Element Name            | Value |
|--------------------|-------------------------|-------|
| GetSegModeSegInfo1 | GETSEGMODSEGINFO_ADR    | 0     |
|                    | GETSEGMODSEGINFO_LEN    | 1     |
| GetSegModeMpgIdx1  | GETSEGMODMPGIDX_SRCADR  | 0     |
|                    | GETSEGMODMPGIDX_DESTADR | 1     |
|                    | GETSEGMODMPGIDX_LEN     | 2     |

# Software Component Implementation

## Sub-Module Functions

### Init: Init1

#### Design Rationale

The initialization function creates two copies of the RTE generated
flash table in to RAM. A CRC is performed on each of the copies to
ensure that they match. The function also adjusts the tables to load the
appropriate initialization and run-time calibrations indexes that are
required by the application.

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image2.emf)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image3.emf)

#### Module Outputs

None

### Per: Per1

#### Design Rationale

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image4.emf)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image5.emf)

#### Module Outputs

None

## Server Runnables 

### CopyCalPageReq

#### Design Rationale

This function is called by the XCP master and queues the copy of the
calibrations contained in the selected group, or segment, into the RAM
buffer. The actual copy is performed by TunSelnMngt’s main periodic
function, but this runnable logs the current state of TunSelnMngt and
marks the copy in progress.

####  (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image6.emf)

#### Module Outputs

None

### GetCalPageReq

#### Design Rationale

This function is called by the XCP master and returns the page with the
request XCP and ECU access for a given segment.

####  (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image7.emf)

#### Module Outputs

None

### GetSegInfoReq

#### Design Rationale

This function is called by the XCP master and returns the requested
information for the provided segment.

####  (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image8.emf)

#### Module Outputs

None

### OnlineTunRamAdrMpg

#### Design Rationale

This function is called by the XCP master. During tuning, tools such as
eTool and CANape will read calibration values from their flash addresses
because that is how the A2L file is defined. However, when the
calibrations are access from RAM, the user does not always know the
exact address the calibration is located. This function calculates the
RAM address for a given calibration to the XCP function for reading and
writing.

####  (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image9.emf)

#### Module Outputs

None

### SetCalPageReq

#### Design Rationale

This function is called by the XCP master. This function will set the
status of the calibration page for a given segment.

####  (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image10.emf)

#### Module Outputs

None

## Interrupt Functions

None

## Module Internal (Local) Functions

### SwtCalIdx

|                      |           |      |     |     |
|----------------------|-----------|------|-----|-----|
| **Function Name**    | SwtCalIdx | Type | Min | Max |
| **Arguments Passed** | N/A       |      |     |     |
| **Return Value**     | N/A       |      |     |     |

#### Design Rationale

This function manages the RAM buffer access and switches the calibration
index between the two copies in RAM.

#### Processing

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image11.png"
style="width:4.44167in;height:4.15556in" />

### IdxChgMngt

|                      |                          |                     |       |            |
|--------------|------------------------------|-------------|--------|---------|
| **Function Name**    | IdxChgMngt               | Type                | Min   | Max        |
| **Arguments Passed** | SeldIdx_Cnt_T_u08        | Uint8               | 0     | 255        |
|                      | GendCalTblSize_Cnt_T_u08 | Uint8               | 0     | 255        |
|                      | GendCalTbl_T_rec         | TunSelnIdxTblRec1\* | 0     | 4294967295 |
| **Return Value**     | IdxFound_Cnt_T_logl      | Boolean             | FALSE | TRUE       |

#### Design Rationale

#### Processing

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image12.png"
style="width:4.49375in;height:5.02569in" />

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image13.emf)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image14.emf)

### MemCopy32Bit

|                      |              |        |     |            |
|----------------------|--------------|--------|-----|------------|
| **Function Name**    | MemCopy32Bit | Type   | Min | Max        |
| **Arguments Passed** | Des_Arg      | Void   | 0   | 4294967295 |
|                      | Src_Arg      | Void   | 0   | 4294967295 |
|                      | Len_Arg      | Uint16 | 0   | 65535      |
| **Return Value**     | N/A          |        |     |            |

#### Design Rationale

The 32-bit mem copy function is used to move calibration pointers from
flash to RAM. The void pointers are internally assigned to a uint32
pointer before the processing loop begins.

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image15.emf)

### MemCopy8Bit

|                      |             |        |     |            |
|----------------------|-------------|--------|-----|------------|
| **Function Name**    | MemCopy8Bit | Type   | Min | Max        |
| **Arguments Passed** | Des_Arg     | Void   | 0   | 4294967295 |
|                      | Src_Arg     | Void   | 0   | 4294967295 |
|                      | Len_Arg     | Uint16 | 0   | 65535      |
| **Return Value**     | N/A         |        |     |            |

#### Design Rationale

The 8-bit mem copy function is used to move calibration segments into
the RAM space. Since the length of the segments is not guaranteed to be
a 32-bit even address, 8-bit was selected to ensure that only the bytes
required to be moved are performed. The void pointers are internally
assigned to a uint8 pointer before the processing loop begins.

#### Processing

### SegModAdrInfo

|                      |               |                   |     |     |
|----------------------|---------------|-------------------|-----|-----|
| **Function Name**    | SegModAdrInfo | Type              | Min | Max |
| **Arguments Passed** | Seg_Arg       | UInt8             | 0   | 255 |
|                      | SegInfo_Arg   | GetSegModSegInfo1 | 0   | 1   |
|                      | Resp_Arg      | Uint8\*           | 0   | 255 |
|                      | RespLen_Arg   | Uint8\*           | 8   | 8   |
| **Return Value**     | Rtn_Cnt_T_u08 | Uint8             | 0   | 255 |

#### Design Rationale

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image16.emf)

### SegModStdInfo

|                      |                |         |     |     |
|----------------------|----------------|---------|-----|-----|
| **Function Name**    | SegModStdInfo  | Type    | Min | Max |
| **Arguments Passed** | Seg_Arg        | Uint8   | 0   | 255 |
|                      | Resp_Arg       | Uint8\* | 0   | 255 |
|                      | RespLen_Arg    | UInt8\* | 6   | 6   |
| **Return Value**     | \<Hard Coded\> | UInt8   | 1   | 1   |

#### Design Rationale

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image17.emf)

### SegModAdrMpg

|                      |                |                  |     |            |
|----------------------|----------------|------------------|-----|------------|
| **Function Name**    | SegModAdrMpg   | Type             | Min | Max        |
| **Arguments Passed** | Seg_Arg        | Uint8            | 0   | 255        |
|                      | MpgIdxInfo_Arg | GetSegModMpgIdx1 | 0   | 2          |
|                      | MpgIdx_Arg     | Uint8            | 0   | 255        |
|                      | Resp_Arg       | UInt8\*          | 0   | 4294967295 |
|                      | RespLen_Arg    | Uint8\*          | 8   | 8          |
| **Return Value**     | Rtn_Cnt_T_u08  | Uint8            | 0   | 255        |

#### Design Rationale

#### Processing

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES400A_TunSelnMngt_Impl/doc/mediax/media/image18.emf)

### TunSelnMngt_ChkXcpWrAcs

|                      |                         |         |       |            |
|----------------------|-------------------------|---------|-------|------------|
| **Function Name**    | TunSelnMngt_ChkXcpWrAcs | Type    | Min   | Max        |
| **Arguments Passed** | ReqAdr_Cnt_T_u32        | Uint32  | 0     | 4294967296 |
| **Return Value**     | Rtn_Cnt_T_logl          | Boolean | FALSE | TRUE       |

#### Design Rationale

This function is generated based on the configured access regions in
Configurator. Below is just a high level overview of the function. The
conditions in the if statements are logically OR’d together to form the
tests.

#### Processing

**  
**

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

1.  None

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}