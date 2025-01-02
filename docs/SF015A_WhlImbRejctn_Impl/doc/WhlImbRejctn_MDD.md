---
layout: default
title: WhlImbRejctn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**WhlImbRejctn**

**Version: 9**

**Jan 26, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matt Leser,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                             |                        |                          |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                             | **Author**             | **Version**              | **Date**    |
| Initial Version                                             | Sankardu Varadapureddi | 1                        | 4-Mar-2016  |
| Updated for FDD ver 1.2.0                                   | Sankardu Varadapureddi | 2                        | 21-Mar-2016 |
| Updated for FDD ver 1.6.0                                   | Matt Leser             | 3 (Version 4 in Synergy) | 21-Sep-2016 |
| Updated version number to match Synergy Database            | Matt Leser             | 6                        | 28-Sep-2016 |
| Updated for FDD ver 1.7.0                                   | Matt Leser             | 7                        | 13-Oct-2016 |
| Updated to fix Anomaly EA4#8205                             | Matt Leser             | 8                        | 2-Dec-2016  |
| Updated for FDD ver 1.9.0, Fixed Anomaies EA4#8955/EA4#9065 | Matt Leser             | 9                        | 26-Jan-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 WhlImbRejctn High-Level Description
[6](#whlimbrejctn-high-level-description)](#whlimbrejctn-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of WhlImbRejctn
[7](#graphical-representation-of-whlimbrejctn)](#graphical-representation-of-whlimbrejctn)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [8](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[9](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: WhlImbRejctnInit1
[10](#init-whlimbrejctninit1)](#init-whlimbrejctninit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Per: WhlImbRejctnPer1
[10](#per-whlimbrejctnper1)](#per-whlimbrejctnper1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: WhlImbRejctnPer2
[10](#per-whlimbrejctnper2)](#per-whlimbrejctnper2)

[5.1.3.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[5.4.1.1 Description [11](#description)](#description)

[5.4.2 Local Function \#2 [11](#local-function-2)](#local-function-2)

[5.4.2.1 Description [11](#description-1)](#description-1)

[5.4.3 Local Function \#3 [12](#local-function-3)](#local-function-3)

[5.4.3.1 Description [12](#description-2)](#description-2)

[5.4.4 Local Function \#4 [12](#local-function-4)](#local-function-4)

[5.4.4.1 Description [12](#description-3)](#description-3)

[5.4.5 Local Function \#5 [12](#local-function-5)](#local-function-5)

[5.4.5.1 Description [12](#description-4)](#description-4)

[5.4.6 Local Function \#6 [13](#local-function-6)](#local-function-6)

[5.4.6.1 Description [13](#description-5)](#description-5)

[5.4.7 Local Function \#7 [13](#local-function-7)](#local-function-7)

[5.4.7.1 Description [13](#description-6)](#description-6)

[5.4.8 Local Function \#8 [13](#local-function-8)](#local-function-8)

[5.4.8.1 Description [14](#description-7)](#description-7)

[5.4.9 Local Function \#9 [14](#local-function-9)](#local-function-9)

[5.4.9.1 Description [14](#description-8)](#description-8)

[5.4.10 Local Function \#10
[14](#local-function-10)](#local-function-10)

[5.4.10.1 Description [14](#description-9)](#description-9)

[5.4.11 Local Function \#11
[14](#local-function-11)](#local-function-11)

[5.4.11.1 Description [14](#description-10)](#description-10)

[5.4.12 Local Function \#12
[14](#local-function-12)](#local-function-12)

[5.4.12.1 Description [15](#description-11)](#description-11)

[5.4.13 Local Function \#13
[15](#local-function-13)](#local-function-13)

[5.4.13.1 Description [15](#description-12)](#description-12)

[5.5 GLOBAL Function/Macro Definitions
[15](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[16](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[17](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[18](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [19](#glossary)](#glossary)

[Appendix C References [20](#references)](#references)

# Introduction

## Purpose

## Scope

# WhlImbRejctn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of WhlImbRejctn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF015A_WhlImbRejctn_Impl/doc/mediax/media/image1.png"
style="width:2.75799in;height:5.11077in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

| Constant Name            | Resolution | Units | Value |
|--------------------------|------------|-------|-------|
| MAXMGNMASK_CNT_U08       | 1          | Cnt   | 1     |
| QUALMASK_CNT_U08         | 1          | Cnt   | 2     |
| DCTRENDMASK_CNT_U08      | 1          | Cnt   | 4     |
| FREQDIAGCMASK_CNT_U08    | 1          | Cnt   | 8     |
| WHLSPDCORRLNMASK_CNT_U08 | 1          | Cnt   | 16    |
| MINSTOMILLISEC_ULS_F32   | 1          | Cnt   | 60000 |

For other constants, refer .m file.

#### Local Constants

# Software Component Implementation

## Sub-Module Functions

## Init: WhlImbRejctnInit1

## Design Rationale

Refer FDD

## Module Outputs

Refer FDD

## Per: WhlImbRejctnPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Per: WhlImbRejctnPer2

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                            |         |       |            |     |
|-----------|--------------------------------|----------|----------|--|---------|
| **Function Name**    | UGRFilOutp                 | Type    | Min   |            | Max |
| **Arguments Passed** | Y_Hz_T_f32                 | float32 | -8.8  | 376.991118 |     |
|                      | FreqEst_Hz_T_f32           | float32 | 0.005 | 60         |     |
|                      | PoleMag_Uls_T_f32          | float32 | 0     | 1          |     |
|                      | \* Ugr1_MotRadPerSec_T_f32 | float32 | 0     | 256        |     |
|                      | \* Ugr2_MotRadPerSec_T_f32 | float32 | 0     | 256        |     |
| **Return Value**     | YFild_Hz_T_f32             | float32 | 0     | 127        |     |

## Description

‘UGR’ filter implementation. ‘Ugr1_MotRadPerSec_T_f32’ and
‘Ugr2_MotRadPerSec_T_f32’ corresponds to PIMs used in internal
calculations.

## Local Function \#2

|                      |                                |         |          |               |     |
|-----------|-------------------------------|---------|----------|--|------------|
| **Function Name**    | DtrmnEnadAmnt                  | Type    | Min      |               | Max |
| **Arguments Passed** | FreqEstAvg_Hz_T_f32            | float32 | 0.005    | 60            |     |
|                      | WhlSpdLFilt_MotRadPerSec_T_f32 | float32 | -100     | 100           |     |
|                      | WhlSpdRFilt_MotRadPerSec_T_f32 | float32 | -100     | 100           |     |
|                      | VehSpd_Kph_T_f32               | float32 | 0        | 511           |     |
|                      | VehSpdVld_Cnt_T_logl           | boolean | FALSE    | TRUE          |     |
|                      | WhlImbRejctnCustEna_Cnt_T_logl | boolean | FALSE    | TRUE          |     |
|                      | WhlImbRejctnDi_Cnt_T_logl      | boolean | FALSE    | TRUE          |     |
|                      | SysSt_Cnt_T_enum               | SysSt1  | SYSST_DI | SYSST_WRMININ |     |
|                      | \*Enable_Uls_T_f32             | float32 | 0        | 1             |     |
| **Return Value**     | WhlImbRejctnActv_Cnt_T_logl    | boolean | FALSE    | TRUE          |     |

## Description

"Determine Enabled Amt" block implementation. In determination of
‘DistbnMagEnadPrev’, ‘ScaleL’ and ‘ScaleR’ values, some if-else loops
were combined in software for optimization.

\*Enable_Uls_T_f32 is an output of this function.

## Local Function \#3

|                      |                     |         |          |               |     |
|-----------|------------------------------|---------|----------|--|------------|
| **Function Name**    | EnaRamp             | Type    | Min      |               | Max |
| **Arguments Passed** | EnableFac_Uls_T_f32 | float32 | 0        | 1             |     |
|                      | SysSt_Cnt_T_enum    | SysSt1  | SYSST_DI | SYSST_WRMININ |     |
| **Return Value**     | RampEna_Uls_T_f32   | float32 | 0        | 1             |     |

## Description

"Enable Ramp" block implementation.

## Local Function \#4

|                      |                            |           |       |     |     |
|-----------|--------------------------------|----------|----------|--|---------|
| **Function Name**    | DistMag                    | Type      | Min   |     | Max |
| **Arguments Passed** | WhlSpd_MotRadPerSec_T_f32  | float32   | -100  | 100 |     |
|                      | Freq_Hz_T_f32              | float32   | 0.005 | 60  |     |
|                      | \* PeakPrev_Uls_T_f32      | float32   | 0     | 127 |     |
|                      | \* CurrMag_Uls_T_f32       | float32   | 0     | 127 |     |
|                      | \*LpFilOut_Cnt_T_FilLpRec1 | FilLpRec1 |       |     |     |
| **Return Value**     | DistMag_Uls_T_f32          | float32   | 0     | 127 |     |

## Description

"DistMagL/DistMagR" block implementation. ‘PeakPrev_Uls_T_f32’ is a PIM
used in the internal implementation.

‘LePeakPrev’ is output of this function.

## Local Function \#5

|                      |                                 |         |       |     |     |
|-----------|--------------------------------|----------|----------|--|---------|
| **Function Name**    | ActvRejctnCmd                   | Type    | Min   |     | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32             | float32 | -10   | 10  |     |
|                      | Enable_Uls_T_f32                | float32 | 0     | 1   |     |
|                      | FreqEst_Hz_T_f32                | float32 | 0.005 | 60  |     |
|                      |                                 |         |       |     |     |
| **Return Value**     | WhlImbRejctnCmd_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8 |     |

## Description

"Active Rejection Command " block implementation.
“WhlImbRejctnAmp_MtrNm_T_f32” is the output of this function.

PIMs ‘StordValLe’ and ‘StordValRi’ directly used in the software for
signals ‘FiltWhlSpdLScld’ and ‘FiltWhlSpdRScld’ in the FDD.

## Local Function \#6

|                      |                     |         |             |             |     |
|-----------|--------------------------------|----------|----------|--|----------|
| **Function Name**    | AdjSigFil           | Type    | Min         |             | Max |
| **Arguments Passed** | In1_MotNwtMtr_T_f32 | float32 | -127        | 127         |     |
|                      | Zm_Uls_T_f32        | float32 | 0.244742    | 1.0         |     |
|                      | Pk_Uls_T_f32        | float32 | 0.244742    | 1.0         |     |
|                      | B0_Uls_T_f32        | float32 | 0.249683    | 4.005074    |     |
|                      | MagAtFreq_Uls_T_f32 | float32 | 0.414213562 | 2.414213562 |     |
|                      | \* Coeff1_Uls_T_f32 | float32 | 0           | 127         |     |
|                      | \* Coeff1_Uls_T_f32 | float32 | 0           | 127         |     |
| **Return Value**     | Out_MotNwtMtr_T_f32 | float32 | -127        | 127         |     |

## Description

"Filter1 / Filter2 " block implementation.

## Local Function \#7

|                      |           |      |     |     |     |
|----------------------|-----------|------|-----|-----|-----|
| **Function Name**    | SetNTCBlk | Type | Min |     | Max |
| **Arguments Passed** |           |      |     |     |     |
|                      |           |      |     |     |     |
| **Return Value**     | None      |      |     |     |     |

## Description

'Set NTC Block' implementation.

## Local Function \#8

|                      |                        |         |       |      |     |
|----------------------|------------------------|---------|-------|------|-----|
| **Function Name**    | MaxMagDiag             | Type    | Min   |      | Max |
| **Arguments Passed** | CmdAmp_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8  |     |
| **Return Value**     | FltStat_Cnt_T_lgc      | boolean | FALSE | TRUE |     |

## Description

"MaxMagDiag" block implementation.

## Local Function \#9

|                      |                        |         |       |      |     |
|----------------------|------------------------|---------|-------|------|-----|
| **Function Name**    | DcTrendDiag            | Type    | Min   |      | Max |
| **Arguments Passed** | WIRCmd_MtrNwtMtr_T_f32 | float32 | -8.8  | 8.8  |     |
| **Return Value**     | FltStat_Cnt_T_lgc      | boolean | FALSE | TRUE |     |

## Description

" DcTrendDiag" block implementation.

## Local Function \#10

|                      |                        |         |       |      |     |
|----------------------|------------------------|---------|-------|------|-----|
| **Function Name**    | FrequencyDiag          | Type    | Min   |      | Max |
| **Arguments Passed** | WIRCmd_MtrNwtMtr_T_f32 | float32 | -8.8  | 8.8  |     |
|                      | FreqEst_Hz_T_f32       | float32 | 0.005 | 60   |     |
|                      | Enable_Uls_T_f32       | float32 | 0     | 1    |     |
|                      | CmdAmp_MotNwtMtr_T_f32 | float32 | -8.8  | 8.8  |     |
| **Return Value**     | FltStat_Cnt_T_lgc      | boolean | FALSE | TRUE |     |

## Description

' FrequencyDiag ' block implementation.

## Local Function \#11

|                      |                   |         |       |      |     |
|----------------------|-------------------|---------|-------|------|-----|
| **Function Name**    | WhlSpdCorrDiag    | Type    | Min   |      | Max |
| **Arguments Passed** | WhlRiFrq_Hz_T_f32 | float32 | 0.01  | 60   |     |
|                      | WhlLeFrq_Hz_T_f32 | float32 | 0.01  | 60   |     |
| **Return Value**     | FltStat_Cnt_T_lgc | boolean | FALSE | TRUE |     |

## Description

" WhlSpdCorrDiag" block implementation.

## Local Function \#12

|                      |                          |         |            |            |     |
|-----------|-----------------------------|---------|------------|--|-----------|
| **Function Name**    | ElpdTi                   | Type    | Min        |            | Max |
| **Arguments Passed** | FltStsTrue_Cnt_T_lgc     | boolean | FALSE      | TRUE       |     |
|                      | PrevFltStsTrue_Cnt_T_lgc | boolean | FALSE      | TRUE       |     |
|                      | RefTi_Sec_T_u32          | uint32  | Full range | Full range |     |
| **Return Value**     | ElpdTi_MilliSec_T_f32    | float32 | Full range | Full range |     |

## Description

"Elapsed Timer" block implementation.

FltStsTrue_Cnt_T_lgc - Fault condition current status

PrevFltStsTrue_Cnt_T_lgc - Fault condition previous status (PIM)

RefTi_Sec_T_u32 - Reference Timer (PIM)

## Local Function \#13

|                      |                      |                       |                               |                               |     |
|----------|--------------------------|---------------|-----------|--|----------|
| **Function Name**    | FltRcvry             | Type                  | Min                           |                               | Max |
| **Arguments Passed** | ElpdTi_Sec_T_f32     | float32               | Full range                    | Full range                    |     |
|                      | FltRecDly_Mins_T_f32 | float32               | 0                             | 255                           |     |
|                      | \* FltRec_Uls_T_str  | PassFailCntrDiagcRec1 | Structure members –full range | Structure members –full range |     |
|                      | FltRst_Uls_T_lgc     | boolean               | FALSE                         | TRUE                          |     |
| **Return Value**     | None                 |                       |                               |                               |     |

## Description

"Flt Recovery" block implementation. Elapsed time is passed as argument

## Local Function \#14

|                      |                          |         |       |                 |     |
|----------|-----------------------------|---------|------------|--|-------------|
| **Function Name**    | ChkCompPersc             | Type    | Min   |                 | Max |
| **Arguments Passed** | ActiveBand1Inp_Cnt_T_u32 | uint32  | 0     | 4.294967294e+09 |     |
|                      | ActiveBand2Inp_Cnt_T_u32 | uint32  | 0     | 4.294967294e+09 |     |
|                      | ActiveBand3Inp_Cnt_T_u32 | uint32  | 0     | 4.294967294e+09 |     |
| **Return Value**     | Flt_Cnt_T_lgc            | boolean | FALSE | TRUE            |     |

## Description

“CheckCompPersistence” block implementation.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

1\. The Inter runnable variable 'IniCmpFlt' is written in Init1 and read
in Per1. The DD dictionary has a discrepancy where it mentions written
in Per2 and read in Per1. The implementation/code has already been
updated to the current read write combination. The design needs to be
updated for the same. Refer to CR EA4#7979.

2\. Constant DURATIONDISABLE_CNT_U16 value needs to be changed to a
value less than max of the data type.  Implementation is using 18500 to
match the EA3 component based on agreement with FDD Owner. Refer to CR
EA4#7979

3\. The Inter runnable Variable ‘MaxMgnFlt’ is written in Per2 and Read
in Per1. The DataDict.m has a discrepancy where it mentions written in
Init1 and read in Per1. The implementation/code has already been updated
to the current read write combination. The design needs to be updated
for the same. Refer to CR EA4#7979.

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : SF015A_WhlImbRejctn_Design                                                                                                                                      | See Synergy sub project version |

{% endraw %}