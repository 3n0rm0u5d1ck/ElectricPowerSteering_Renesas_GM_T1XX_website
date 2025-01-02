---
layout: default
title: ES006A_NvM_Integration_Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**ES006A NvM**

**VERSION: 3**

**DATE: 28-Sep-2016**

**Prepared By:**

**Kevin Smith**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                  |            |             |           |                 |
|--------|------------------------|------------|--------|----------|------------|
| **Sl. No.** | **Description**                  | **Author** | **Version** | **Date**  | **Approved By** |
| 1           | Initial version                  | K. Smith   | 1.0         | 28-Jan-16 | \-              |
| 2           | Updates for fast ignition cycles | O. Tosh    | 2           | 27-Jun-16 | \-              |
| 3           | Updates for Naming Convections   | K. Smith   | 3           | 28-Sep-16 | \-              |

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
7](#__RefHeading___Toc437335986)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[4.6 Exclusive Area Changes 7](#exclusive-area-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 10](#memory-map-requirements)

[7.1 Mapping 10](#mapping)

[7.2 Usage 10](#usage)

[7.3 NvM Blocks 10](#nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |
|                  |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | MDD Guidelines              | Process 04.02.00               |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Coding standards            | Process 04.02.00               |
| 4           | ES006A_NvM_Design           | See Synergy subproject version |

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

NvMProxy_Init0()

NvMProxy_MainFunction()

NvMProxy_ClsChkWr_Oper()

NvMProxy_MultiBlkCallBack()

NvM Proxy API Functions

NvMProxy_EraseNvBlock()

NvMProxy_GetDataIndex()

NvMProxy_GetErrorStatus()

NvMProxy_InvalidateNvBlock()

NvMProxy_ReadBlock()

NvMProxy_RestoreBlockDefaults()

NvMProxy_SetBlockProtection()

NvMProxy_SetDataIndex()

NvMProxy_SetRamBlockStatus()

NvMProxy_WriteBlock()

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

1.  CDD_NvM_Cfg_private.h

2.  CDD_NvMProxy_Cfg.h

3.  CDD_NvMProxy_Cfg.c

4.  CDD_NvMProxy_Cbk.h

5.  CDD_NvMProxy_Cbk.c

6.  CDD_NvMProxyDftDataGroup.h

7.  NvMProxy_swc_arxml (service component to be imported into Developer)

## Da Vinci Parameter Configuration Changes

|                                                                        |                                                                                                                                                                                                     |          |
|----------------------|---------------------------------------|------------|
| **Parameter**                                                          | **Notes**                                                                                                                                                                                           | **SWC**  |
| /Nexteer/EcucDefs_SyncCrc/NvMProxy/NvMProxyCommon/NvMOsApplicationRef  | This shall point to the application that the NvM component is integrated. Typically this is an ASIL D application.                                                                                  | NvMProxy |
| /Nexteer/EcucDefs_SyncCrc/NvMProxy/NvMProxyCommon/NvmProxyIncludes     | Additional includes for callback functions if required.                                                                                                                                             | NvMProxy |
| //Nexteer/EcucDefs_NvMProxy/NvMProxy/NvMProxyBlkSet/NvMBlkRef          | Reference to the NvM block that NvMProxy will check                                                                                                                                                 | NvMProxy |
| /Nexteer/EcucDefs_NvMProxy/NvMProxy/NvMProxyBlkSet/NvMBlkFlt           | This shall be set to the NTC that a failed NvMProxy check is required to set (NTC 6,7,8 or A)                                                                                                       | NvMProxy |
| /Nexteer/EcucDefs_NvMProxy/NvMProxy/NvMProxyBlkSet/NvMProxyApplCallCbk | If a NvM block requires a callback function, this field shall be populated with the function name. The function prototype can be included by a header file defined in the NvMProxyIncludes section. | NvMProxy |
| /ActiveEcuC/NvM/NvMCommon/NvMMultiBlockCallback                        | Shall be set to NvMProxy_MultiBlkCallBack.                                                                                                                                                          | NvM      |

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **None**     |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **None**     |           |         |

## Exclusive Area Changes

|          |           |         |
|----------|-----------|---------|
| **Name** | **Notes** | **SWC** |
| **None** |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                                                           |              |
|-------------------|---------------------------------------|---------------|
| **Init**             | **Scheduling Requirements**                               | **Trigger**  |
| **NvMProxyInit1**    | Shall be called after DiagcMgr has been initazlied        | RTE Init     |
| **NvMProxyCrcInit0** | Shall be scheduled outside of the RTE after NvM_ReadAll() | Non-RTE Init |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
| **None**     | None                        | N/A         |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

To ensure proper handling for quick ignition cycles, the integration
team must call NvMProxy_MultiBlkCallBack manually prior to calling
NvM_WriteAll(). Ideally this should be placed within the same BswM call
as the NvM_WriteAll().

The call should implemented similary as shown below:

NvMProxy_MultiBlkCallBack(NVM_WRITE_ALL, NVM_REQ_PENDING);

NvM_WriteAll()

This will record all the NvM block status into the PIM. Once the
WriteAll has completed or has been canceled by the NvM_CancelWriteAll()
or NvM_KillWriteAll(), the NvM shall call the callback function and
restore the RAM statuses back to their values prior to the
NvM_WriteAll() call.

{% endraw %}