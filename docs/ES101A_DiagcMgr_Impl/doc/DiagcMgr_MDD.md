---
layout: default
title: DiagcMgr_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Diagnostic Manager**

**VERSION:** **7.0**

**DATE:** **02-DEC-2016**

**Prepared By:**

**Spandana Balani**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                     |            |             |             |
|------|---------------------------------|-----------|----------|-------------|
| **Sl. No.** | **Description**                                     | **Author** | **Version** | **Date**    |
| 1           | Initial Version                                     | SB         | 1.0         | 23-Apr-2015 |
| 2           | Added to Design Limitations section                 | KMC        | 2.0         | 03-Jun-2015 |
| 3           | ES101A_DiagcMgr_Design version 2 implementation     | SB         | 3.0         | 11-Mar-2016 |
| 4           | ES101A_DiagcMgr_Design version 3 implementation     | SB         | 4.0         | 19-Apr-2016 |
| 5           | ES101A_DiagcMgr_Design version 4 implementation     | SB         | 5.0         | 22-Jun-2016 |
| 6           | Added DETs to “SetNtcStsCore_Oper” server runnables | SB         | 6.0         | 26-Sep-2016 |
| 7           | Updated to fix anomalies EA4#8118 and EA4#8115      | SB         | 7.0         | 02-Dec-2016 |

Table of Contents

[1 Abbrevations And Acronyms 6](#abbrevations-and-acronyms)

[2 References 7](#references)

[3 DiagcMgr & High-Level Description
8](#diagcmgr-high-level-description)

[4 Design details of software module
9](#design-details-of-software-module)

[4.1 Graphical representation of Diagcmgr
9](#graphical-representation-of-diagcmgr)

[4.2 Data Flow Diagram 9](#data-flow-diagram)

[4.2.1 Module level DFD 9](#module-level-dfd)

[4.2.2 Sub-Module level DFD 9](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 10](#component-flow-diagram)

[5 Variable Data Dictionary 11](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
11](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
11](#__RefHeading___Toc454959206)

[6 Constant Data Dictionary 12](#constant-data-dictionary)

[6.1 Program(fixed) Constants 12](#programfixed-constants)

[6.1.1 Embedded Constants 12](#embedded-constants)

[6.1.1.1 Local 12](#local)

[6.1.1.2 Global 12](#global)

[6.1.2 Module specific Lookup Tables Constants
12](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 13](#software-module-implementation)

[7.1 Sub-Module Functions 13](#sub-module-functions)

[7.1.1 Initialization Functions 13](#initialization-functions)

[7.1.2 PERIODIC FUNCTIONS 13](#periodic-functions)

[7.1.2.1 Per: diagcmgrPer1 13](#per-diagcmgrper1)

[7.1.2.1.1 Design Rationale 13](#design-rationale)

[7.1.2.1.2 Store Module Inputs to Local copies
13](#store-module-inputs-to-local-copies)

[7.1.2.1.3 (Processing of function)……… 13](#processing-of-function)

[7.1.2.1.4 Store Local copy of outputs into Module Outputs
13](#store-local-copy-of-outputs-into-module-outputs)

[7.1.2.2 Per: diagcmgrPer2 13](#per-diagcmgrper2)

[7.1.2.2.1 Design Rationale 14](#design-rationale-1)

[7.1.2.2.2 Store Module Inputs to Local copies
15](#store-module-inputs-to-local-copies-1)

[7.1.2.2.3 (Processing of function)……… 15](#processing-of-function-1)

[7.1.2.2.4 Store Local copy of outputs into Module Outputs
15](#store-local-copy-of-outputs-into-module-outputs-1)

[7.1.3 Interrupt Functions 15](#interrupt-functions)

[7.1.4 Server Runnable Functions 16](#server-runnable-functions)

[7.1.4.1 ClrAllDiagc_Oper 16](#clralldiagc_oper)

[7.1.4.2 ClrSnpshtData_Oper 16](#clrsnpshtdata_oper)

[7.1.4.3 DiagcMgrIninCore_Oper 16](#diagcmgrinincore_oper)

[7.1.4.4 DiagcMgrPwrDwN 17](#diagcmgrpwrdwn)

[7.1.4.4.1 Design Rationale 18](#design-rationale-3)

[7.1.4.5 UpdDtcEnaCdn 18](#upddtcenacdn)

[7.1.4.5.1 Design Rationale 18](#design-rationale-4)

[7.1.4.6 GetNtcActvCORE_Oper 19](#getntcactvcore_oper)

[7.1.4.7 GetNtcQlfrStsCORE_Oper 19](#getntcqlfrstscore_oper)

[7.1.4.8 GetNtcStsCORE_Oper 19](#getntcstscore_oper)

[7.1.4.9 ReadNtcFltAry_Oper 19](#readntcfltary_oper)

[7.1.4.9.1 Design Rationale 19](#design-rationale-5)

[7.1.4.10 ReadNtcInfoAndDebCntr_Oper 19](#readntcinfoanddebcntr_oper)

[7.1.4.10.1 Design Rationale 19](#design-rationale-6)

[7.1.4.11 ReadSnpshtData_Oper 19](#readsnpshtdata_oper)

[7.1.4.12 SetNtcStsCORE_Oper 19](#setntcstscore_oper)

[7.1.4.13 RestoreNtcFltAryDft 19](#restorentcfltarydft)

[7.1.4.14 RestoreSnpshtAryDft 20](#restoresnpshtarydft)

[7.1.5 Local Function/Macro Definitions
20](#local-functionmacro-definitions)

[7.1.5.1 Local Function \#1 20](#local-function-1)

[7.1.5.2 Description 20](#description)

[7.1.5.3 Local Function \#2 20](#local-function-2)

[7.1.5.4 Description 20](#description-1)

[7.1.6 GLObAL Function/Macro Definitions
20](#global-functionmacro-definitions)

[7.1.6.1 GLObAL Function \#1 20](#global-function-1)

[7.1.6.1.1 Description 21](#description-2)

[7.1.6.2 GLObAL Function \#2 21](#global-function-2)

[7.1.6.2.1 Description 21](#description-3)

[7.1.6.3 GLObAL Function \#3 21](#global-function-3)

[7.1.6.3.1 Description 21](#description-4)

[7.1.6.4 GLObAL Function \#4 21](#global-function-4)

[7.1.6.5 Description 21](#description-5)

[7.1.6.6 GLObAL Function \#5 21](#global-function-5)

[7.1.6.7 Description 22](#description-6)

[7.1.6.8 GLObAL Function \#6 22](#global-function-6)

[7.1.6.9 Description 22](#description-7)

[7.1.6.10 GLObAL Function \#7 22](#global-function-7)

[7.1.6.11 Description 22](#description-8)

[7.1.6.12 GLObAL Function \#8 22](#global-function-8)

[7.1.6.13 Description 22](#description-9)

[7.1.7 TRANSIENT FUNCTIONS 22](#transient-functions)

[8 Known Limitations With Design 23](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 24](#unit-test-consideration)

[10 Appendix 25](#appendix)

# Abbrevations And Acronyms

|              |                                         |
|--------------|-----------------------------------------|
| Abbreviation | Description                             |
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                 |                                |
|---------|---------------------------------|--------------------------------|
| Sr. No. | Title                           | Version                        |
| \<1\>   | \<MDD Guidelines\>              | Process 04.02.01               |
| \<2\>   | \<Software Naming Conventions\> | Process 04.02.01               |
| \<3\>   | \<Coding standards\>            | Process 04.02.01               |
| \<4\>   | FDD – ES101A Diagnostic Manager | See Synergy Subproject version |
|         | \<Add if more available\>       |                                |

# DiagcMgr & High-Level Description

# Design details of software module

## Graphical representation of Diagcmgr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image1.png"
style="width:3.23333in;height:5.46667in" />

## Data Flow Diagram

## Module level DFD

*N/A*

## Sub-Module level DFD

*N/A*

## COMPONENT FLOW DIAGRAM

*N/A*

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
<td>NtcMapRec1</td>
<td>ApplIdx</td>
<td>Uint8</td>
<td>0</td>
<td>10</td>
</tr>
<tr class="odd">
<td></td>
<td>NtcInfoIdx</td>
<td>uint8</td>
<td>0</td>
<td>255</td>
</tr>
<tr class="even">
<td>NtcInfoRec4</td>
<td>NtcStInfo</td>
<td>Uint8</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Sts</td>
<td>Uint8</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>AgiCntr</td>
<td>Uint8</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Ary1D_NtcInfoRec4</td>
<td></td>
<td>NtcInfoRec4[]<sup>1</sup></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Ary1D_NtcInfoRec4_DiagcMgrProxyApplX<sup>3</sup></td>
<td></td>
<td>NtcInfoRec4[]<sup>1</sup></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Ary1D_s16_DiagcMgrProxyApplX<sup>3</sup></td>
<td></td>
<td>Sint16[]<sup>2</sup></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

1 – Array of NtcInfoRec4

2 – Array of sint16

3 – One for each Application configured with NTCs

For example – Application 6 and 10 have NTCs then -
Ary1D_NtcInfoRec4_DiagcMgrProxyAppl6,
Ary1D_NtcInfoRec4_DiagcMgrProxyAppl10, Ary1D_s16_DiagcMgrProxyAppl6,
Ary1D_s16_DiagcMgrProxyAppl10 would exist with configured sizes.
<span id="__RefHeading___Toc454959206" class="anchor"></span>Variable
definition for enumerated types

|                     |              |       |
|---------------------|--------------|-------|
| Enum Name           | Element Name | Value |
| See DataDict.m file |              |       |

## Global Variable definition

|                         |                |     |     |
|-------------------------|----------------|-----|-----|
| Name                    | Type           |     |     |
| SnpshtDataAry_M\[8\]^1^ | SnpshtDataRec1 |     |     |

|                |                             |        |             |               |
|-----------------|--------------------------|---------|----------|------------|
| Name           | Element                     | Type   | Min         | Max           |
| SnpshtDataRec1 | RegInBRAMDAT1_Cnt_T_u32     | uint32 | 0           | 4294967295    |
|                | HwTq_Cnt_T_s5p10            | sint16 | -10         | 10            |
|                | MotTqCmdMrfScad_Cnt_T_s5p10 | sint16 | -8.8        | 8.8           |
|                | IgnCntr_Cnt_T_u32           | uint32 | 0           | 4294967295    |
|                | BrdgVltg_Cnt_T_u6p10        | uint16 | 6           | 26.5          |
|                | EcuTFild_Cnt_T_s8p7         | sint16 | -50         | 150           |
|                | NtcNr_Cnt_T_u16             | NtcNr1 | NTCNR_0X001 | NTCNR_0X1FF   |
|                | NtcStInfo_Cnt_T_u08         | uint8  | 0           | 255           |
|                | SysSt_Cnt_T_enum            | SysSt1 | SYSST_DI    | SYSST_WRMININ |
|                | VehSpd_Cnt_T_u9p7           | Uint16 | 0           | 511           |

Notes:

1- This variable is mapped to MemMap –
“GlobalShared_START_SEC_VAR_NOINIT_UNSPECIFIED”

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                                 |            |        |                 |
|---------------------------------|------------|--------|-----------------|
| Constant Name                   | Resolution | Units  | Value           |
| See DataDict.m file             |            |        |                 |
| IMDTSHTDWNFLT_CNT_U32           | 1          | Counts | 13              |
| CTRLDSHTDWNFLT_CNT_U32          | 1          | Counts | 14              |
| INFOONLYFLT_CNT_U32             | 1          | Counts | 15              |
| TOTNROFDTC_CNT_U08^4^           | 1          | Counts | Configured      |
| PimSnpshtDataAry_SnpshtDataRec1 |            |        | SnpshtDataAry_M |

4 - Number of DTCs for that program.

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                     |
|---------------------|
| Constant Name       |
| See DataDict.m file |
|                     |
|                     |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                        |                        |                                                                                    |                         |
|------------------------------|----------------|--------------|--------------|
| Constant Name                          | Resolution             | Value                                                                              | Software Segment        |
| DiagcMgrNtcMap_Cnt_rec\[512\]          | NtcMapRec1             | Configured                                                                         | DiagcMgr_START_SEC_CODE |
| NtcNrAryApplX_Cnt_u16\[Configured\]^5^ | 1                      | Configured                                                                         | DiagcMgr_START_SEC_CODE |
| DtcEnaMask\[Configured\]^6^            | 1                      | Configured                                                                         | DiagcMgr_START_SEC_CODE |
| DemDtcEveIdMap\[Configured\]^6^        | 1                      | Configured                                                                         | DiagcMgr_START_SEC_CODE |
| FltRespRampTbl_Uls_f32\[13\]           | Single Precision Float | {0.1F,0.125F,0.1428F,0.1667F,0.2F,0.25F,0.333F,0.5F,1.0F,2.0F,3.333F,10.0F,500.0F} | DiagcMgr_START_SEC_CODE |

5 - One for each Application configured with NTCs.

6 - Variable Length (TOTNROFDTC_CNT_U08 + 1) for each build/program
depending on the Number of DTCs

for that program.

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: diagcmgrPer1

This function exists in “DiagcMgr.c” file.

## Design Rationale

“Rte_Call_GetDiagcDataApplX_Oper” for each application(X) is called
based on conditional compile using constants generated in
DiagcMgr_Cfg_private.h

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: diagcmgrPer2

This function exists in “DiagcMgr.c” file.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image2.wmf)

## Design Rationale

“Rte_Call_GetDiagcDataApplX_Oper” for each application(X) is called
based on conditional compile using constants generated in
DiagcMgr_Cfg_private.h

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

## Server Runnable Functions

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## ClrAllDiagc_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## ClrSnpshtData_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## Design Rationale

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_SnpshtDataAry” is used
instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so that
the Integrator doesn’t have to configure the DiagcMgr to know about the
Nvm block Ids.

## DiagcMgrIninCore_Oper

See DataDict.m file and modelThis function exists in “DiagcMgr.c” file.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image3.wmf)

## DiagcMgrPwrDwN

See DataDict.m file and model

This function exists in “DiagcMgrNonRte.c” file.

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg_private.h.

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_DiagcMgrNtcFltAry” is
used instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so
that the Integrator doesn’t have to configure the DiagcMgr to know about
the Nvm block Ids.

## UpdDtcEnaCdn

See DataDict.m file and model

This function exists in “DiagcMgrNonRte.c” file.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image4.wmf)

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg_private.h.

## GetNtcActvCORE_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## GetNtcQlfrStsCORE_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## GetNtcStsCORE_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## ReadNtcFltAry_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## Design Rationale

“GetNtcInfoApplX_Oper” for each application(X) is called based on
conditional compile using constants generated in DiagcMgr_Cfg_private.h

## ReadNtcInfoAndDebCntr_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## Design Rationale

“GetNtcDebCntrApplX” and “GetNtcInfoApplX_Oper” for each application(X)
is called based on conditional compile using constants generated in
DiagcMgr_Cfg_private.h

## ReadSnpshtData_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

## SetNtcStsCORE_Oper

See DataDict.m file and model

This function exists in “DiagcMgr.c” file.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES101A_DiagcMgr_Impl/doc/mediax/media/image5.wmf)

## RestoreNtcFltAryDft

See DataDict.m file and model

This function exists in “DiagcMgrNonRte.c” file.

## RestoreSnpshtAryDft

See DataDict.m file and model

This function exists in “DiagcMgrNonRte.c” file.

## Local Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## Local Function \#1

|                      |                       |               |     |       |
|----------------------|-----------------------|---------------|-----|-------|
| **Function Name**    | ProcRampResp          | Type          | Min | Max   |
| **Arguments Passed** | NtcNr_Cnt_T_u16       | uint16        | 0   | 511   |
|                      | DiagcData_T_rec       | DiagcDataRec1 | 0   | 65535 |
|                      | ProxySetNtcData_T_rec | DiagcDataRec1 | 0   | 65535 |
| **Return Value**     | N/A                   |               |     |       |

## Description

Refer ‘ProcessRampResponse and DiagcSts’ block in Simulink model

This function exists in “DiagcMgr.c” file.

## Local Function \#2

|                      |                             |        |             |               |
|-------------|-----------------------------|----------|----------|-----------|
| **Function Name**    | UpdSnpshtData               | Type   | Min         | Max           |
| **Arguments Passed** | RegInBRAMDAT1_Cnt_T_u32     | uint32 | 0           | 4294967295    |
|                      | HwTq_Cnt_T_s5p10            | sint16 | -10         | 10            |
|                      | MotTqCmdMrfScad_Cnt_T_s5p10 | sint16 | -8.8        | 8.8           |
|                      | IgnCntr_Cnt_T_u32           | uint32 | 0           | 4294967295    |
|                      | BrdgVltg_Cnt_T_u6p10        | uint16 | 6           | 26.5          |
|                      | EcuTFild_Cnt_T_s8p7         | sint16 | -50         | 150           |
|                      | NtcNr_Cnt_T_u16             | NtcNr1 | NTCNR_0X001 | NTCNR_0X1FF   |
|                      | NtcStInfo_Cnt_T_u08         | uint8  | 0           | 255           |
|                      | SysSt_Cnt_T_enum            | SysSt1 | SYSST_DI    | SYSST_WRMININ |
|                      | VehSpd_Cnt_T_u9p7           | Uint16 | 0           | 511           |
| **Return Value**     | N/A                         |        |             |               |

## Description

Refer ‘UpdSnpshtData’ block in Simulink model

This function exists in “DiagcMgr.c” file

## Design Rationale

“NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_SnpshtDataAry” is used
instead of BlockID Number in “NvMProxy_SetRamBlockStatus” call so that
the Integrator doesn’t have to configure the DiagcMgr to know about the
Nvm block Ids.

## GLObAL Function/Macro Definitions

:All the global functions described below are declared in
DiagcMgr_private.h and are intended to be used only by DiagcMgr and the
DiagcMgrProxyApplX components.These functions exist in
“DiagcMgr_private.c” file.

## GLObAL Function \#1

|                      |                    |        |     |            |
|----------------------|--------------------|--------|-----|------------|
| **Function Name**    | ProcessDiagSts     | Type   | Min | Max        |
| **Arguments Passed** | FltRsp_Cnt_T_u32   | uint32 | 0   | 4294967295 |
|                      | DiagStsX_Cnt_T_u16 | uint16 | 0   | 65535      |
| **Return Value**     | N/A                |        |     |            |

## Description

Refer to “ES101A_DiagcMgr/DiagcMgr/SetNtcStsCore/NtcNr is
Valid/Diagnostics Not Inhibited/NtcEnabled/NTCSTS_PREFAILD/Update
NtcInfoSts, DebCntr and Process RampRate/DebCntr =
MAXDEBCNTRVAL_CNT_S16/ProcessRampResponse and
DiagcSts/ControlledShutdown Fault/ProcessDiagcSts” Simulink path in the
FDD.

## GLObAL Function \#2

|                      |                      |               |     |       |
|----------------------|----------------------|---------------|-----|-------|
| **Function Name**    | ProcProxyRampResp    | Type          | Min | Max   |
| **Arguments Passed** | NtcNr_Cnt_T_u16      | uint16        | 0   | 511   |
|                      | ProxyDiagcData_T_rec | DiagcDataRec1 | 0   | 65535 |
| **Return Value**     | N/A                  |               |     |       |

## Description

Refer ‘ProcessRampResponse and DiagcSts’ block in Simulink path ”
ES101A_DiagcMgrProxyX/DiagcMgrProxyApplX/DiagcMgrProxyApplXPer1/Update
the DiagcSts/For Number of NTCs/Update DiagcSts and Ramp Response/Update
Latest Values/ProcessRampResponse”

## GLObAL Function \#3

|                      |                     |        |     |     |
|----------------------|---------------------|--------|-----|-----|
| **Function Name**    | DiagcMgrSetBits_u16 | Type   | Min | Max |
| **Arguments Passed** | Data                | uint16 | 0   | 511 |
|                      | BitMask             | Uint16 | 0   | 511 |
| **Return Value**     | Data                | Uint16 | 0   | 511 |

## Description

This function will set bits based on the passed BitMask for a uint16
datatype.

## GLObAL Function \#4

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrSetBits_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will set bits based on the passed BitMask for a uint8
datatype

## GLObAL Function \#5

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrClrBits_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will clear bits based on the passed BitMask for a uint8
datatype

## GLObAL Function \#6

|                      |                     |       |     |     |
|----------------------|---------------------|-------|-----|-----|
| **Function Name**    | DiagcMgrReadBit_u08 | Type  | Min | Max |
| **Arguments Passed** | Data                | Uint8 | 0   | 255 |
|                      | BitMask             | Uint8 | 0   | 255 |
| **Return Value**     | Data                | Uint8 | 0   | 255 |

## Description

This function will return TRUE if any bits are set based on the passed
BitMask for a uint8 datatype

## GLObAL Function \#7

|                      |                     |        |     |     |
|----------------------|---------------------|--------|-----|-----|
| **Function Name**    | DiagcMgrReadBit_u16 | Type   | Min | Max |
| **Arguments Passed** | Data                | uint16 | 0   | 511 |
|                      | BitMask             | Uint16 | 0   | 511 |
| **Return Value**     | Data                | Uint16 | 0   | 511 |

## Description

This function will return TRUE if any bits are set based on the passed
BitMask for a uint16 datatype

## GLObAL Function \#8

|                      |                     |        |     |       |
|----------------------|---------------------|--------|-----|-------|
| **Function Name**    | DiagcMgrReadBit_u32 | Type   | Min | Max   |
| **Arguments Passed** | Data                | uint16 | 0   | 511   |
|                      | BitMask             | Uint16 | 0   | 65535 |
| **Return Value**     | Data                | Uint16 | 0   |       |

## Description

This function will return TRUE if any bits are set based on the passed
BitMask for a uint32 datatype

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

1.  Per the FDD author, safety critical data is protected in an
    exclusive area but there is a possibility of corruption of non
    critical data.

2.  Refer to Design Rationale section on the top level of DiagcMgr
    Simulink model.

# UNIT TEST CONSIDERATION

1.  Config files in the contract folder are for a test project with
    sample configurations using Application 6 and Application 10.
    Therefore with this configuration, the following files cannot be
    tested – DiagcMgrProxyAppl0, DiagcMgrProxyAppl1, DiagcMgrProxyAppl2,
    DiagcMgrProxyAppl3, DiagcMgrProxyAppl4, DiagcMgrProxyAppl5,
    DiagcMgrProxyAppl7, DiagcMgrProxyAppl8, DiagcMgrProxyAppl9.

# Appendix

*None*

{% endraw %}