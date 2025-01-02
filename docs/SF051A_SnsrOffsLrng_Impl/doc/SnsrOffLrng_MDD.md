---
layout: default
title: SnsrOffLrng_MDD
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Sensor Offset Learning**

**Dec 7, 2016**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|             |                                           |                    |             |
|--------|----------------------------------|------------------|-------------|
| **Version** | **Description**                           | **Author**         | **Date**    |
| 1           | Initial Version                           | Selva Sengottaiyan | 07-Feb-2016 |
| 2           | Updated as per FDD v 1.2.0                | Krishna Anne       | 07-Mar-2016 |
| 3           | Updated graphical representation          | Nick Saxton        | 17-Aug-2016 |
| 4           | Updated design limitations for FDD v1.5.0 | Shruthi Raghavan   | 7-Dec-2016  |

**  
**

<u>Table of Contents</u>[1 Introduction
[6](#introduction)](#introduction)

[2 SnsrOffsLrng & High-Level Description
[7](#snsroffslrng-high-level-description)](#snsroffslrng-high-level-description)

[3 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of SnsrOffsLrng
[9](#graphical-representation-of-snsroffslrng)](#graphical-representation-of-snsroffslrng)

[4 Constant Data Dictionary
[11](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[11](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants
[11](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[12](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[12](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: SnsrOffsLrngInit1
[12](#init-snsroffslrnginit1)](#init-snsroffslrnginit1)

[5.1.1.1 Design Rationale [12](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [12](#module-outputs)](#module-outputs)

[5.1.2 Per: SnsrOffsLrngPer1
[12](#per-snsroffslrngper1)](#per-snsroffslrngper1)

[5.1.2.1 Design Rationale
[12](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[12](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[12](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[12](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.1 Per: SnsrOffsLrngPer2
[12](#per-snsroffslrngper2)](#per-snsroffslrngper2)

[5.1.1.1 Design Rationale
[12](#design-rationale-2)](#design-rationale-2)

[5.1.1.2 Store Module Inputs to Local copies
[12](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.1.3 (Processing of function)………
[12](#processing-of-function-1)](#processing-of-function-1)

[5.1.1.4 Store Local copy of outputs into Module Outputs
[12](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables [13](#server-runables)](#server-runables)

[5.2.1 SnsrOffsLrng_RstHwTq
[13](#snsroffslrng_rsthwtq)](#snsroffslrng_rsthwtq)

[5.2.1.1 Design Rationale
[13](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies-2)](#store-module-inputs-to-local-copies-2)

[5.2.1.3 (Processing of function)………
[13](#processing-of-function-2)](#processing-of-function-2)

[5.2.1.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs-2)](#store-local-copy-of-outputs-into-module-outputs-2)

[5.2.2 SnsrOffsLrng_RstYawAndAg
[13](#snsroffslrng_rstyawandag)](#snsroffslrng_rstyawandag)

[5.2.2.1 Design Rationale
[13](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies-3)](#store-module-inputs-to-local-copies-3)

[5.2.2.3 (Processing of function)………
[13](#processing-of-function-3)](#processing-of-function-3)

[5.2.2.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs-3)](#store-local-copy-of-outputs-into-module-outputs-3)

[5.2.3 SnsrOffsLrng_SetHwAgOffs
[13](#snsroffslrng_sethwagoffs)](#snsroffslrng_sethwagoffs)

[5.2.3.1 Design Rationale
[13](#design-rationale-5)](#design-rationale-5)

[5.2.3.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies-4)](#store-module-inputs-to-local-copies-4)

[5.2.3.3 (Processing of function)………
[13](#processing-of-function-4)](#processing-of-function-4)

[5.2.3.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs-4)](#store-local-copy-of-outputs-into-module-outputs-4)

[5.2.4 SnsrOffsLrng_GetHwAgOffs
[14](#snsroffslrng_gethwagoffs)](#snsroffslrng_gethwagoffs)

[5.2.4.1 Design Rationale
[14](#design-rationale-6)](#design-rationale-6)

[5.2.4.2 Store Module Inputs to Local copies
[14](#store-module-inputs-to-local-copies-5)](#store-module-inputs-to-local-copies-5)

[5.2.4.3 (Processing of function)………
[14](#processing-of-function-5)](#processing-of-function-5)

[5.2.4.4 Store Local copy of outputs into Module Outputs
[14](#store-local-copy-of-outputs-into-module-outputs-5)](#store-local-copy-of-outputs-into-module-outputs-5)

[5.2.5 SnsrOffsLrng_SetHwTqOffs
[14](#snsroffslrng_sethwtqoffs)](#snsroffslrng_sethwtqoffs)

[5.2.5.1 Design Rationale
[14](#design-rationale-7)](#design-rationale-7)

[5.2.5.2 Store Module Inputs to Local copies
[14](#store-module-inputs-to-local-copies-6)](#store-module-inputs-to-local-copies-6)

[5.2.5.3 (Processing of function)………
[14](#processing-of-function-6)](#processing-of-function-6)

[5.2.5.4 Store Local copy of outputs into Module Outputs
[14](#store-local-copy-of-outputs-into-module-outputs-6)](#store-local-copy-of-outputs-into-module-outputs-6)

[5.2.6 SnsrOffsLrng_GetHwTqOffs
[14](#snsroffslrng_gethwtqoffs)](#snsroffslrng_gethwtqoffs)

[5.2.6.1 Design Rationale
[14](#design-rationale-8)](#design-rationale-8)

[5.2.6.2 Store Module Inputs to Local copies
[14](#store-module-inputs-to-local-copies-7)](#store-module-inputs-to-local-copies-7)

[5.2.6.3 (Processing of function)………
[14](#processing-of-function-7)](#processing-of-function-7)

[5.2.6.4 Store Local copy of outputs into Module Outputs
[14](#store-local-copy-of-outputs-into-module-outputs-7)](#store-local-copy-of-outputs-into-module-outputs-7)

[5.2.7 SnsrOffsLrng_SetYawRateOffs
[15](#snsroffslrng_setyawrateoffs)](#snsroffslrng_setyawrateoffs)

[5.2.7.1 Design Rationale
[15](#design-rationale-9)](#design-rationale-9)

[5.2.7.2 Store Module Inputs to Local copies
[15](#store-module-inputs-to-local-copies-8)](#store-module-inputs-to-local-copies-8)

[5.2.7.3 (Processing of function)………
[15](#processing-of-function-8)](#processing-of-function-8)

[5.2.7.4 Store Local copy of outputs into Module Outputs
[15](#store-local-copy-of-outputs-into-module-outputs-8)](#store-local-copy-of-outputs-into-module-outputs-8)

[5.2.8 SnsrOffsLrng_GetYawRateOffs
[15](#snsroffslrng_getyawrateoffs)](#snsroffslrng_getyawrateoffs)

[5.2.8.1 Design Rationale
[15](#design-rationale-10)](#design-rationale-10)

[5.2.8.2 Store Module Inputs to Local copies
[15](#store-module-inputs-to-local-copies-9)](#store-module-inputs-to-local-copies-9)

[5.2.8.3 (Processing of function)………
[15](#processing-of-function-9)](#processing-of-function-9)

[5.2.8.4 Store Local copy of outputs into Module Outputs
[15](#store-local-copy-of-outputs-into-module-outputs-9)](#store-local-copy-of-outputs-into-module-outputs-9)

[5.3 Module Internal (Local) Functions
[15](#module-internal-local-functions)](#module-internal-local-functions)

[5.3.1 Module Internal (Local) Functions
[15](#_Toc445196931)](#_Toc445196931)

[6 Known Limitations with Design
[19](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[20](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[21](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [22](#glossary)](#glossary)

[Appendix C References [23](#references)](#references)

# Introduction

Refer the Design Subproject.

# SnsrOffsLrng & High-Level Description

Refer the Design Subproject.

# Design details of software module

## Graphical representation of SnsrOffsLrng

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF051A_SnsrOffsLrng_Impl/doc/mediax/media/image1.PNG"
style="width:4.76108in;height:8.92833in" />

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                        | Resolution             | Units        | Value |
|---------------------------------|---------------|-----------|-------------|
| HWTQOFFSHILIM_HWNWTMTR_F32           | Single precision float | HwNwtMtr     | 4     |
| HWTQOFFSLOLIM_HWNWTMTR_F32           | Single precision float | HwNwtMtr     | -4    |
| VEHYAWRATEOFFSHILIM_VEHDEGPERSEC_F32 | Single precision float | VehDegPerSec | 20    |
| VEHYAWRATEOFFSLOLIM_VEHDEGPERSEC_F32 | Single precision float | VehDegPerSec | -20   |
| HWAGOFFSHILIM_HWDEG_F32              | Single precision float | HwDeg        | -30   |
| HWAGOFFSLOLIM_HWDEG_F32              | Single precision float | HwDeg        | -30   |
| MTRXSIZE_CNT_U08                     | 1                      | Cnt          | 3     |

# Software Component Implementation

## Sub-Module Functions

### Init: SnsrOffsLrngInit1

## Design Rationale

*Refer the Design.*

## Module Outputs

*Refer the Design.*

###  [section]

### Per: SnsrOffsLrngPer1

## Design Rationale

*Refer the Design.*

## Store Module Inputs to Local copies

*Refer the Design.*

##  (Processing of function)………

*Refer the Design.*

## Store Local copy of outputs into Module Outputs

*Refer the Design.*

### Per: SnsrOffsLrngPer2

## Design Rationale

*Refer the Design.*

## Store Module Inputs to Local copies

*Refer the Design.*

##  (Processing of function)………

*Refer the Design.*

## Store Local copy of outputs into Module Outputs

*Refer the Design.*

## Server Runables 

### SnsrOffsLrng_RstHwTq

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_RstYawAndAg

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_SetHwAgOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_GetHwAgOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_SetHwTqOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_GetHwTqOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_SetYawRateOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

### SnsrOffsLrng_GetYawRateOffs

## Design Rationale

> *Refer the Design.*

## Store Module Inputs to Local copies

> *Refer the Design.*

##  (Processing of function)………

> *Refer the Design.*

## Store Local copy of outputs into Module Outputs

> *Refer the Design.*

## Module Internal (Local) Functions

### Module Internal (Local) Functions

##### Calculate **LearnHwAg**

|                      |                               |         |       |      |          |
|----------------|-----------------------------|----------|-------|------|------|
| **Function Name**    | LearnHwAg                     | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | HwAgLrngLrngCdnVld_Cnt_T_logl | Boolean | FALSE | TRUE |          |
|                      | HwAgLrngEna_Cnt_T_logl        | Boolean | FALSE | TRUE |          |
|                      | SysTqFild_HwNm_T_f32          | float32 | -8.8  | 8.8  |          |
|                      | HandwheelPosition_HwDeg_T_f32 | float32 | -1440 | 1440 |          |
| **Return Value**     | None                          |         |       |      |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **SOaCHierarchyManager**

|                      |                          |         |       |      |          |
|----------------|-----------------------------|----------|-------|------|------|
| **Function Name**    | SOaCHierarchyManager     | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | \*EnableYOC_Cnt_T_logl   | Boolean | FALSE | TRUE |          |
|                      | \*HwAgLrngEna_Cnt_T_logl | Boolean | FALSE | TRUE |          |
|                      | \*HwAgLrngRst_Cnt_T_logl | Boolean | FALSE | TRUE |          |
| **Return Value**     |                          |         |       |      |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **Perform_TqInpDetn**

|                      |                   |      |     |     |          |
|----------------------|-------------------|------|-----|-----|----------|
| **Function Name**    | Perform_TqInpDetn | Type | Min | Max | UTP Tol. |
| **Arguments Passed** | None              |      |     |     |          |
|                      |                   |      |     |     |          |
| **Return Value**     |                   |      |     |     |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **EnableLearning**

|                      |                        |         |       |      |          |
|----------------|-----------------------------|----------|-------|------|------|
| **Function Name**    | **EnableLearning**     | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** |                        |         |       |      |          |
|                      |                        |         |       |      |          |
| **Return Value**     | HwTqLrngEna_Cnt_T_logl | Boolean | FALSE | TRUE |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate CalculateKVector

<table style="width:100%;">
<colgroup>
<col style="width: 23%" />
<col style="width: 43%" />
<col style="width: 12%" />
<col style="width: 6%" />
<col style="width: 6%" />
<col style="width: 6%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Function Name</strong></td>
<td><h5 id="calculatekvector"
class="unnumbered">CalculateKVector</h5></td>
<td>Type</td>
<td>Min</td>
<td>Max</td>
<td>UTP Tol.</td>
</tr>
<tr class="even">
<td><strong>Arguments Passed</strong></td>
<td>TqMdlXAry_HwRadpS_T_f32[3]</td>
<td>float32</td>
<td>-42</td>
<td>42</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>KVect_Uls_T_f32[3]</td>
<td>float32</td>
<td>-42</td>
<td>42</td>
<td></td>
</tr>
<tr class="even">
<td><strong>Return Value</strong></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **EnablePreProcessing**

|                      |                          |         |       |       |          |
|----------------|-----------------------------|----------|-------|------|------|
| **Function Name**    | **EnablePreProcessing**  | Type    | Min   | Max   | UTP Tol. |
| **Arguments Passed** | HwTqPreproc_dB_T_f32     | float32 | -100  | 30    |          |
|                      | SampleCntrLim_Cnt_T_u16  | Uint16  | 1     | 65535 |          |
|                      | TqInpPrsntVld_Cnt_T_logl | Boolean | FALSE | TRUE  |          |
|                      | TqInpPrsnt_Cnt_T_logl    | Boolean | FALSE | TRUE  |          |
| **Return Value**     |                          |         |       |       |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **UpdateCovarianceMatrix**

|                      |                              |         |     |     |          |
|-----------------|------------------------------|----------|------|------|------|
| **Function Name**    | UpdateCovarianceMatrix       | Type    | Min | Max | UTP Tol. |
| **Arguments Passed** | TqMdlXAry_HwRadpS_T_f32\[3\] | float32 | -42 | 42  |          |
|                      | KVect_Uls_T_f32\[3\]         | float32 | -42 | 42  |          |
| **Return Value**     |                              |         |     |     |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

TblSize_Cnt_T_u16 is size of the single dimension of
TqMdlAryKVect_Uls_T_f32.

##### Calculate **UpdateHwTqOffs**

|                      |                                   |         |       |      |          |
|----------------|-----------------------------|----------|-------|------|------|
| **Function Name**    | **UpdateHwTqOffs**                | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | HwTqEstimnVld_Cnt_T_logl          | boolean | FALSE | TRUE |          |
|                      | HwTqDriftEstimnOnCentr_HwNm_T_f32 | float32 | -10   | 10   |          |
| **Return Value**     | None                              |         |       |      |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

##### Calculate **UpdateSampleCnt**

|                      |                       |         |       |      |          |
|----------------------|-----------------------|---------|-------|------|----------|
| **Function Name**    | **UpdateSampleCnt**   | Type    | Min   | Max  | UTP Tol. |
| **Arguments Passed** | HwAgMeasd_HwDeg_T_f32 | float32 | -1440 | 1440 |          |
|                      |                       |         |       |      |          |
| **Return Value**     | None                  |         |       |      |          |

#### Description

No flowchart added. For Unit test FDD should provide the information
needed regarding function processing

# Known Limitations with Design

The display variable dSnsrOffsLrngSysTqFild and PIM SysTqCdngFil
structure have wrong ranges defined in the datadict.m file. The actual
range according to developer is \[-366, 366\]. However, since the given
range is larger and includes the correct range and because these
variables are not affecting the downstream operations in a way that will
fail the PIL, this is not changed in the interest of time (changing this
would mean rerunning the robustness test and there wasn’t enough time
for that before release).

The name of the NVM structure type SnsrLrndOffsRec2 is changed without
any change to the name or datatype of the corresponding elements. The
only difference between SnsrLrndOffsRec1 and SnsrLrndOffsRec2 is the
ranges of the elements within the structure.

Since this is not the agreed process for EA4, the implementation
deviates from FDD and uses the original structure in order to avoid a
change to StdDef to only add a redundant datatype. For the next FDD
revision we need to make a decision on whether to go back to
SnsrLrndOffsRec1 in the FDD or change the StdDef and add
SnsrLrndOffsRec2 type in it. Either way, once the new tool is officially
rolled out for use, such deviations of type will be caught in the
Polyspace as an error (necessitating manual fixes to work around such
issues).

# UNIT TEST CONSIDERATION

The display variable dSnsrOffsLrngSysTqFild and PIM SysTqCdngFil
structure have wrong ranges defined in the datadict.m file. The actual
range according to developer is \[-366, 366\]. However, since the given
range is larger and includes the correct range and because these
variables are not affecting the downstream operations in a way that will
fail the PIL, this is not changed in the interest of time (changing this
would mean rerunning the robustness test and there wasn’t enough time
for that before release).

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                                   |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2                             |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                                  |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                                           |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                                           |
| 5           | SF051A_SnsrOffsLrng_Design                                                                                                                                            | See the synergy sub-project version included. |

{% endraw %}