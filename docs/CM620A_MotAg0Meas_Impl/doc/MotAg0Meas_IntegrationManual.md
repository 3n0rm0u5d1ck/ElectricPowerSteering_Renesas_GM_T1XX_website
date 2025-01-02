---
layout: default
title: MotAg0Meas_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**MotAg0Meas**

**Integration Manual**

**VERSION: 2.0**

**DATE:** **04_Oct-2015**

**Revision History**

|             |                           |             |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**           | **Author**  | **Version** | **Date**    |
| 1           | Initial version           | Rijvi Ahmed | 1.0         | 09-Jun-2015 |
| 2           | Updated for FDD rev 3.0.0 | Rijvi Ahmed | 2.0         | 04-Oct-2015 |

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
7](#__RefHeading___Toc421811099)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 10](#memory-map-requirements)

[7.1 Mapping 10](#mapping)

[7.2 Usage 10](#usage)

[7.3 Non RTE NvM Blocks 10](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 10](#rte-nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                            |
|------------------|----------------------------|
| **Abbreviation** | **Description**            |
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                               |                                   |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                         | Version                           |
| \<1\>   | MDD Guidelines                | Software Process Release 04.02.00 |
| \<2\>   | Software Naming Conventions   | Software Process Release 04.02.00 |
| \<3\>   | Design and Coding Standards   | Software Process Release 04.02.00 |
| \<4\>   | FDD: CM620A_MotAg0Meas_Design | See Synergy subproject version    |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

> See FDD – CM620A_MotAg0Meas_DataDict.m file

# Configuration REQUIREMeNTS

## Build Time Config

|               |                                                      |     |
|---------------|------------------------------------------------------|-----|
| **Modules**   | **Notes**                                            |     |
| **FLTINJENA** | Set to STD_ON if want to turn on the fault injection |     |

## Configuration Files to be provided by Integration Project

CDD_MotAg0Meas_Cfg.h

## Da Vinci Parameter Configuration Changes

|                                             |           |         |
|---------------------------------------------|-----------|---------|
| **Parameter**                               | **Notes** | **SWC** |
| **\<Configurator Changes for parameters\>** |           |         |

## DaVinci Interrupt Configuration Changes

|                                             |            |                         |           |
|-------------|--------|---------------------------|-------------------------|
| **ISR Name**                                | **VIM \#** | **Priority Dependency** | **Notes** |
| **\<Configurator Changes for Interrupts\>** |            |                         |           |

## Manual Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 47%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Constant</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><p><em>Note: Temporarily</em> CDD_MotAg0Meas_Cfg.h</p>
<p><em>file can be copied from the contract folder. Later revision will
have the Davinci configuration parameter to generate the
file.</em></p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

See FDD – CM620A_MotAg0Meas_DataDict.m file

## Required Global Data Outputs

See FDD – CM620A_MotAg0Meas_DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                     |                             |             |
|---------------------|-----------------------------|-------------|
| **Init**            | **Scheduling Requirements** | **Trigger** |
| **MotAg0MeasInit1** |                             | RTE/ Init   |

|                                       |                             |                        |
|------------------------------|-----------------------------|-------------|
| **Runnable**                          | **Scheduling Requirements** | **Trigger**            |
| **MotAg0MeasPer1**                    | None                        | Motor control runnable |
| **MotAg0MeasPer2**                    | None                        | RTE/2 ms               |
| **MotAg0MeasMotAg0CoeffTblRead_Oper** | None                        | On event               |
| **MotAg0MeasMotAg0CoeffTblWr_Oper**   | None                        | On event               |
|                                       |                             |                        |
|                                       |                             |                        |
|                                       |                             |                        |
|                                       |                             |                        |
|                                       |                             |                        |

# Memory Map REQUIREMENTS

## Mapping

|                                           |                         |           |
|---------------------------------|-------------------|--------------------|
| **Memory Section**                        | **Contents**            | **Notes** |
| **CDD_MotAg0Meas_MotCtrl_START_SEC_CODE** | Motor Control runnables |           |
|                                           |                         |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **None**       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

|                    |
|--------------------|
| **Block Name**     |
| **MotAg0CoeffTbl** |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

# Appendix

*\<This section is for appendix\>*

{% endraw %}