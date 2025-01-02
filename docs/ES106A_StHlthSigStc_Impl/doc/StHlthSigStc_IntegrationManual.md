---
layout: default
title: StHlthSigStc_IntegrationManual
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**State of Health Signal Statistics**

**VERSION: 5.0**

**DATE: 12-Dec-2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Revision History**

|             |                                                  |                      |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                  | **Author**           | **Version** | **Date**    |
| 1           | Initial version                                  | Akilan Rathakrishnan | 1.0         | 15-Feb-2016 |
| 2           | EA4#4910 fix                                     | Akilan Rathakrishnan | 2.0         | 28-Mar-2016 |
| 3           | EA4#5553 update                                  | Akilan Rathakrishnan | 3.0         | 02-May-2016 |
| 4           | EA4#7307                                         | Akilan Rathakrishnan | 4.0         | 27-Sep-2016 |
| 5           | EA4#7836 – added note for regenerating cfg files | Akilan Rathakrishnan | 5.0         | 12-Dec-2016 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes 8](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
9](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 9](#required-global-data-inputs)

[5.2 Required Global Data Outputs 9](#required-global-data-outputs)

[5.3 Specific Include Path present 9](#specific-include-path-present)

[6 Runnable Scheduling 10](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 11](#memory-map-requirements)

[7.1 Mapping 11](#mapping)

[7.2 Usage 11](#usage)

[7.3 Non RTE NvM Blocks 11](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 11](#rte-nvm-blocks)

[8 Compiler Settings 12](#compiler-settings)

[8.1 Preprocessor MACRO 12](#preprocessor-macro)

[8.2 Optimization Settings 12](#optimization-settings)

[9 Appendix 13](#appendix)

# Abbrevations And Acronyms

|                  |                                         |
|------------------|-----------------------------------------|
| **Abbreviation** | **Description**                         |
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                            |                                  |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                                  | **Version**                      |
| \<1\>       | \<FDD - \<FDD ES106A_StHlthSigStc_Design\> | Refer Synergy subproject version |
|             |                                            |                                  |
|             |                                            |                                  |
|             |                                            |                                  |
|             |                                            |                                  |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

See section 6. Please note the server runnables listed can be used as
needed in the integration project and can be called via the RTE or
outside of the RTE as required

|                                                   |                |                                                                                                                   |
|------------------------------------|--------------------|----------------|
| **Non-Trusted Function**                          | **Parameters** | **Notes**                                                                                                         |
| **NONTRUSTED_NtWrapS_StHlthSigStc_UpdNvmPim**     |                | This function shall be defined as a non-trusted function call to the application that StHlthSigStc is integrated. |
| **NONTRUSTED_NtWrapS_StHlthSigStc_ClrDataSample** |                | This function shall be defined as a non-trusted function call to the application that StHlthSigStc is integrated. |
| **NONTRUSTED_NtWrapS_StHlthSigStc_UpdDataSample** |                | This function shall be defined as a non-trusted function call to the application that StHlthSigStc is integrated. |

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

StHlthSigStc_Cfg.c

StHlthSigStc_Cfg.h

Note 1: Include “StHlthSigStc_Cfg.h” in the “Rte_UserTypes.h” file since
user defined typedefs are generated in this file.

Note 2: Configuration files “*StHlthSigStc_Cfg.c” and
“StHlthSigStc_Cfg.h”*

shall be regenerated whenever there is a change in text template files
*StHlthSigStc_Cfg.c.tt and StHlthSigStc_Cfg.h.tt.*

## Da Vinci Parameter Configuration Changes

Following configurations shall be made in DaVinci configurator for the
component.

There are three containers that need to be instantiated for this
components configuration.

1.  StHlthSigStcApplicationConfigs : OS application in which this
    component is scheduled to run shall be configured in this container.

|                          |                                       |
|--------------------------|---------------------------------------|
| **Parameter Name**       | **Parameter Value**                   |
| OS Application Reference | Application in which ES106A scheduled |

1.  StHlthSigStcCrConfigLists: List of CRC constants that are need to be
    checked for NvM validation shall be configured in this container.
    Each CRC constant shall have one entry.

> Below table indicates list of CRC values currently considered.

|                            |                             |
|----------------------------|-----------------------------|
| **Parameter Name**         | **Parameter Value**         |
| StHlthSigStcCrcStartSymbol | Application CRC symbol name |

1.  StHlthSigStcSignalLists: This list shall have one entry for every
    monitored signal.

> Following set of information shall be configured for every signal:

1.  Singal Name: Signal name of the State of Health signal (mentioned in
    the below table).

2.  Task Id: Task id of the task in which the periodic(s) from the FDD,
    mentioned against respective signal in the below table, is
    scheduled.

3.  Loop time: Loop time of the task with 1 micro second resolution.

|                         |                          |
|-------------------------|--------------------------|
| **Signal Name**         | **FDD**                  |
| CtrlrTStHlth            | ES210A_EcuTMeas          |
| OutpAssiStHlth          | ES259A_BattVltgCorrln    |
| DigTqSnsrAStHlth        | ES229A_HwTqCorrln        |
| DigTqSnsrBStHlth        | ES229A_HwTqCorrln        |
| DigTqIdptSigStHlth      | ES229A_HwTqCorrln        |
| DutyCycStHlth           | SF009A_DutyCycThermProtn |
| EotImpctStHlth          | SF011A_EotLrng           |
| MotPosStHlth            | ES241A_MotAg2Meas        |
| AbsltMotPosABDifStHlth  | ES249A_MotAgCorrln       |
| AbsltMotPosACDifStHlth  | ES249A_MotAgCorrln       |
| AbsltMotPosBCDifStHlth  | ES249A_MotAgCorrln       |
| CurrMotSumABCStHlth     | ES209A_CurrMeasCorrln    |
| CurrMotSumDEFStHlth     | ES209A_CurrMeasCorrln    |
| PhaAStHlth              | ES320A_MotDrvDiagc       |
| PhaBStHlth              | ES320A_MotDrvDiagc       |
| PhaCStHlth              | ES320A_MotDrvDiagc       |
| PhaDStHlth              | ES320A_MotDrvDiagc       |
| PhaEStHlth              | ES320A_MotDrvDiagc       |
| PhaEStHlth              | ES320A_MotDrvDiagc       |
| RamEccSngBitCorrnStHlth | CM103A_RamMem            |
| FricEstimnStHlth        | SF007A_SysFricLrng       |
| WhlImbMaxCmpStHlth      | SF015A_WhlImbRejctn      |

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **N/A**      |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                       |                             |             |
|-----------------------|-----------------------------|-------------|
| **Init**              | **Scheduling Requirements** | **Trigger** |
| **StHlthSigStcInit1** | Invoked by RTE during Init  | RTE         |

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 39%" />
<col style="width: 9%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Runnable</strong></td>
<td><strong>Scheduling Requirements</strong></td>
<td><strong>Trigger</strong></td>
</tr>
<tr class="even">
<td><strong>ClrSigStcHlthData_Oper</strong></td>
<td>Server Runnable</td>
<td>Client Call</td>
</tr>
<tr class="odd">
<td><strong>GetSigStcHlthData_Oper</strong></td>
<td>Server Runnable</td>
<td>Client Call</td>
</tr>
<tr class="even">
<td><strong>StHlthStcPwrDwn_Oper</strong></td>
<td>Server Runnable</td>
<td>Client Call</td>
</tr>
<tr class="odd">
<td><strong>UpdStHlthStcData_Oper</strong></td>
<td>Server Runnable</td>
<td>Client Call</td>
</tr>
<tr class="even">
<td><strong>NONTRUSTED_NtWrapS_StHlthSigStc_ClrDataSample</strong></td>
<td><p>Non-Tusted function definition</p>
<p>(Index: NtWrapS_StHlthSigStc_ClrDataSample)</p></td>
<td>On Event</td>
</tr>
<tr class="odd">
<td><strong>NONTRUSTED_NtWrapS_StHlthSigStc_UpdNvmPim</strong></td>
<td><p>Non-Tusted function definition</p>
<p>(Index: NtWrapS_StHlthSigStc_UpdNvmPim)</p></td>
<td>On Event</td>
</tr>
<tr class="even">
<td><strong>NONTRUSTED_NtWrapS_StHlthSigStc_UpdDataSample</strong></td>
<td><p>Non-Tusted function definition</p>
<p>(Index: NtWrapS_StHlthSigStc_UpdDataSample)</p></td>
<td>On Event</td>
</tr>
</tbody>
</table>

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

|                       |
|-----------------------|
| **Block Name**        |
| **SigStcHistDataAry** |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*\<This section is for appendix\>*

{% endraw %}