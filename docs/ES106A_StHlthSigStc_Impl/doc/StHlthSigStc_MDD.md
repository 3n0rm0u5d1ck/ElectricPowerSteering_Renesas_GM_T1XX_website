---
layout: default
title: StHlthSigStc_MDD
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**State of Health Signal Statistics**

**Dec** **07, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|             |                      |                      |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**      | **Author**           | **Version** | **Date**    |
| 1           | Initial Version      | Akilan Rathakrishnan | 1.0         | 15-Feb-2016 |
| 2           | Updated for EA4#5553 | Akilan Rathakrishnan | 2.0         | 04-May-2016 |
| 3           | Updated for EA4#7307 | Akilan Rathakrishnan | 3.0         | 27-Sep-2016 |
| 4           | Updated for EA4#7836 | Akilan Rathakrishnan | 4.0         | 07-Dec-2016 |

<u>Table of Contents</u>

[**1** **StHlthSignStc High-Level Description
5**](#sthlthsignstc-high-level-description)

[2 Design details of software module
6](#design-details-of-software-module)

[Graphical representation of StHlthSigStc
6](#graphical-representation-of-sthlthsigstc)

[Data Flow Diagram 6](#data-flow-diagram)

[2.1.1 Component level DFD 6](#component-level-dfd)

[2.1.2 Function level DFD 6](#function-level-dfd)

[3 Variable Data Dictionary 7](#variable-data-dictionary)

[3.1 User defined typedef definition/declaration
7](#user-defined-typedef-definitiondeclaration)

[3.2 Variable definition for enumerated types
7](#variable-definition-for-enumerated-types)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[4.1.1.2 Global 8](#global)

[4.1.2 Module specific Lookup Tables Constants
8](#module-specific-lookup-tables-constants)

[5 Software Module Implementation 9](#software-module-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Initialization Functions: *StHlthSigStcInit1*
9](#initialization-functions-sthlthsigstcinit1)

[5.1.2 PERIODIC FUNCTIONS 9](#periodic-functions)

[5.1.3 Interrupt Functions 9](#interrupt-functions)

[5.1.4 Server Runnable Functions 9](#server-runnable-functions)

[5.1.4.1 ClrSigStcHlthData_Oper 9](#clrsigstchlthdata_oper)

[5.1.4.2 GetSigStcHlthData_Oper 9](#getsigstchlthdata_oper)

[5.1.4.3 StHlthStcPwrDwn_Oper 9](#sthlthstcpwrdwn_oper)

[5.1.4.4 UpdStHlthStcData_Oper 9](#updsthlthstcdata_oper)

[5.1.5 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.1.5.1 Local Function \#1 9](#local-function-1)

[5.1.5.1.1 Description 9](#description)

[5.1.5.2 Local Function \#2 9](#local-function-2)

[5.1.5.2.1 Description 10](#description-1)

[5.1.5.3 Local Function \#3 10](#local-function-3)

[5.1.5.3.1 Description 10](#description-2)

[5.1.5.4 Local Function \#4 10](#local-function-4)

[5.1.5.4.1 Description 10](#description-3)

[5.1.6 Transition Functions 10](#transition-functions)

[5.1.7 Global Function/Macro Definitions
10](#global-functionmacro-definitions)

[5.1.7.1 Global Function \#1 10](#global-function-1)

[5.1.7.1.1 Description 10](#description-4)

[5.1.7.2 Global Function \#2 11](#global-function-2)

[5.1.7.2.1 Description 11](#description-5)

[5.1.7.3 Global Function \#3 11](#global-function-3)

[5.1.7.3.1 Description 11](#description-6)

[6 Known Limitations with Design 12](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 13](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 14](#abbreviations-and-acronyms)

[Appendix B Glossary 15](#glossary)

[Appendix C References 16](#references)

# StHlthSignStc High-Level Description

This component shall collect State of Health data signals from other
component(s) and shall compute following statistical values for each
signal: Minimum, Maximum, Average and Life Cycle Sample counter. This
component shall provide statistical data for ignition cycle and for life
cycle for each signal upon request.

# Design details of software module

*See FDD.*

## Graphical representation of StHlthSigStc

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES106A_StHlthSigStc_Impl/doc/mediax/media/image1.png"
style="width:3.36458in;height:4.5625in" />

## Data Flow Diagram

See FDD.

### Component level DFD

See FDD.

### Function level DFD

See FDD.

# Variable Data Dictionary

## User defined typedef definition/declaration 

*\<This section documents any user types uniquely used for the
module.\>*

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 24%" />
<col style="width: 18%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td>Ary1D_u8_ StHlthSigStc1</td>
<td>Array</td>
<td>uint8</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td>Ary1D_u32_ StHlthSigStc1</td>
<td>Array</td>
<td>uint32</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="even">
<td>Ary1D_f32_ StHlthSigStc1</td>
<td>Array</td>
<td>Float32</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td>StHlthSigStcPrmRec1</td>
<td>GetStHlthDataOper</td>
<td>uint8 (*GetDataOper)(void )</td>
<td>0</td>
<td>4294967295</td>
</tr>
<tr class="even">
<td></td>
<td>SamplePerSec</td>
<td>uint16</td>
<td>0</td>
<td>65535</td>
</tr>
<tr class="odd">
<td></td>
<td>TaskRef</td>
<td>TaskType</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td></td>
<td>RamStorgOffs</td>
<td>uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="odd">
<td></td>
<td>NvmStorgOffs</td>
<td>uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>StHlthSigStcCrcAdrRec1</td>
<td>* CrcStrtAdr</td>
<td>uint32</td>
<td>0</td>
<td>4294967295</td>
</tr>
<tr class="odd">
<td>StHlthSigStcPrmRec1</td>
<td>*SigPrm</td>
<td>StHlthSigStcPrmRec1</td>
<td>0</td>
<td>4294967295</td>
</tr>
<tr class="even">
<td></td>
<td>*CrcAdr</td>
<td>StHlthSigStcCrcAdrRec1</td>
<td>0</td>
<td>4294967295</td>
</tr>
</tbody>
</table>

Ary1D_u8_StHlthSigStc1 – Typedef for Ram buffer where State of Health
Statistical data is kept for the current Ignition cycle. Size of this
array is configurable.

Ary1D_u32\_ StHlthSigStc1 – Typedef for Ignition cycle sample counter.
Size of this array is configurable.

Ary1D_f32\_ StHlthSigStc1 – typedef for Signal Average value. Size of
this array is configurable.

## Variable definition for enumerated types

|                     |              |       |
|---------------------|--------------|-------|
| Enum Name           | Element Name | Value |
| See DataDict.m file |              |       |

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                      |                        |       |                                         |
|------------------|--------------|---------------|---------------------------|
| Constant Name        | Resolution             | Units | Value                                   |
| See DataDict.m file  |                        |       |                                         |
| CRCBUFSIZE_CNT_U08   | 1                      | Cnt   | (WORDSIZE_CNT_U08\*NROFCRCAREA_CNT_U08) |
| STHLTHMAXVAL_CNT_F32 | Single precision float | Cnt   | 100.0                                   |
| STHLTHMINVAL_CNT_F32 | Single precision float | Cnt   | 0.0                                     |

**\* Also see see FDD ES106A_StHlthSigStc_DataDict.m file**

## Global

\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>

|                     |
|---------------------|
| Constant Name       |
| See DataDict.m file |
|                     |
|                     |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                        |                     |            |                    |
|----------------------------|---------------|-------------|-----------------|
| Constant Name          | Resolution          | Value      | Software Segment   |
| StHlthSigStcCfgRecInst | StHlthSigStcCfgRec1 | Configured | StHlthSigStc_CONST |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions: *StHlthSigStcInit1* 

See DataDict.m file and model. This function exists in “StHlthSigStc.c”
file.

## PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Server Runnable Functions

## ClrSigStcHlthData_Oper

See DataDict.m file and model. This function exists in “StHlthSigStc.c”
file.

## GetSigStcHlthData_Oper

See DataDict.m file and model. This function exists in “StHlthSigStc.c”
file.

## StHlthStcPwrDwn_Oper 

See DataDict.m file and model. This function exists in “StHlthSigStc.c”
file.

## UpdStHlthStcData_Oper 

See DataDict.m file and model. This function exists in “StHlthSigStc.c”
file.

## Module Internal (Local) Functions

## Local Function \#1

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | StHlthSigStc_ClrDataSample | Type    | Min   | Max  |
| **Arguments Passed** | TarSel_Uls_T_logl          | boolean | FALSE | TRUE |
| **Return Value**     | None                       | N/A     | N/A   | N/A  |

## Description

This function implements “StHlthStcPwrDwn” function in the FDD.

## Local Function \#2

|                      |                               |               |           |            |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | StHlthSigStc_GetSigStHlthData | Type          | Min       | Max        |
| **Arguments Passed** | SigId_Uls_T_enum              | StHlthMonSig3 | 0         | 21         |
|                      | TarAdr                        | uint8\*       | 0x0000000 | 0xFFFFFFFF |
| **Return Value**     | None                          | N/A           | N/A       | N/A        |

## Description

This function implements “GetSigStcHlthData” function in the FDD.

## Local Function \#3

|                      |                        |         |           |            |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | StHlthSigStc_UpdNvmPim | Type    | Min       | Max        |
| **Arguments Passed** | NvmPim_Ptr_T_u08       | uint8\* | 0x0000000 | 0xFFFFFFFF |
|                      | NvmMaxVal_Uls_T_u08    | uint8   | 0         | 100        |
|                      | NvmMinVal_Uls_T_u08    | uint8   | 0         | 100        |
|                      | NvmAvrgVal_Uls_T_u7p9  | u7p9    | 0         | 65535      |
|                      | NvmSampleCnt_Uls_T_u32 | Uint32  | 0         | Max of u32 |
| **Return Value**     | None                   | N/A     | N/A       | N/A        |

## Description

This function implements “Update Nvm” function in the FDD.

## Local Function \#4

|                      |                            |       |     |     |
|----------------------|----------------------------|-------|-----|-----|
| **Function Name**    | StHlthSigStc_UpdDataSample | Type  | Min | Max |
| **Arguments Passed** | TaskRef_Uls_T_u08          | uint8 | 0   | 255 |
| **Return Value**     | None                       | N/A   | N/A | N/A |

## Description

This function implements “Update Nvm” function in the FDD.

## Transition Functions

None.

## Global Function/Macro Definitions

## Global Function \#1

|                      |                                               |                                    |     |          |
|---------|------------------------------|----------------------|-----|--------|
| **Function Name**    | NONTRUSTED_NtWrapS_StHlthSigStc_UpdDataSample | Type                               | Min | Max      |
| **Arguments Passed** | FunctionIndex                                 | NonTrustedFunctionIndexType        | 0   | 65535    |
|                      | FunctionParams                                | NonTrustedFunctionParameterRefType | 0   | 0xFFFFFF |
| **Return Value**     | void                                          |                                    |     |          |

## Description

Implements Nontrusted function wrapper for UpdDataSample. This will be
called from UpdStHlthStcData_Oper upon client invocation.

## Global Function \#2

|                      |                                           |                                    |     |          |
|----------|-----------------------------|----------------------|------|--------|
| **Function Name**    | NONTRUSTED_NtWrapS_StHlthSigStc_UpdNvmPim | Type                               | Min | Max      |
| **Arguments Passed** | FunctionIndex                             | NonTrustedFunctionIndexType        | 0   | 65535    |
|                      | FunctionParams                            | NonTrustedFunctionParameterRefType | 0   | 0xFFFFFF |
| **Return Value**     | void                                      |                                    |     |          |

## Description

Implements Nontrusted function wrapper for UpdNvmPim. This will be
called from StHlthStcPwrDwn_Oper upon client invocation.

## Global Function \#3

|                      |                                               |                                    |     |          |
|---------|-----------------------------|----------------------|-----|--------|
| **Function Name**    | NONTRUSTED_NtWrapS_StHlthSigStc_ClrDataSample | Type                               | Min | Max      |
| **Arguments Passed** | FunctionIndex                                 | NonTrustedFunctionIndexType        | 0   | 65535    |
|                      | FunctionParams                                | NonTrustedFunctionParameterRefType | 0   | 0xFFFFFF |
| **Return Value**     | void                                          |                                    |     |          |

## Description

Implements Nontrusted function wrapper for UpdNvmPim. This will be
called from ClrSigStcHlthData_Oper upon client invocation.

# Known Limitations with Design

1.  Following constants are not used in the implementation even though
    they defined in the .m file. It is only used for the purpose of
    model simulation.

```{=html}
<!-- -->
```
1.  SHIFTFAC16_ULS_U08

2.  SHIFTFAC24_ULS_U08

3.  SHIFTFAC8_ULS_U08

```{=html}
<!-- -->
```
1.  Number of signals that can be supported for State of Health
    monitoring is limited NVM block size. Currently State of Health NVM
    block size is set to 225 bytes. With each signal occupying 8 bytes,
    1 byte for CRC, current design can support upto 28 signals.

2.  Implementation uses different name for following PIM variables that
    are defined in .m file:

    1.  SigStcPrmInst

    2.  CrcInst

# UNIT TEST CONSIDERATION

1.  Config files in the contract folder are for a test project with
    sample configurations for two monitored signals CtrlrTStHlth and
    OutpAssiStHlth.

2.  Signal related configurations are generated out of Configurator.
    Hence, none of the configuration values shall be hand-modified to
    cover legal range of underlying parameter. If complete range need to
    be supported, then make configuration, and generate the cfg files
    accordingly.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**            |
|-----------------------------|----------------------------|
| DFD                         | Design functional diagram  |
| MDD                         | Module design Document     |
| FDD                         | Functional Design Document |

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                            |
| 5           | FDD: ES106A_StHlthSigStc_Design                                                                                                                               | See Synergy subproject version |

{% endraw %}