---
layout: default
title: DmaCfgAndUse_Integration_Manual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**DmaCfgAndUse**

**VERSION:** **2.0**

**DATE:** **20-Oct-2015**

**Prepared By:**

**Kathleen Creager**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|                                                                      |                  |             |             |
|---------------------|---------------------|---------|----------------------|
| **Description**                                                      | **Author**       | **Version** | **Date**    |
| Initial version                                                      | Kathleen Creager | 1.0         | 08-Jun-2015 |
| Updated for changes for FDD version CM200A_DmaCfgAndUse_Design_1.4.0 | Kathleen Creager | 2.0         | 20-Oct-2015 |

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
7](#__RefHeading___Toc389222325)

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

[7.3 Non RTE NvM Blocks 10](#nvm-blocks)

[7.4 RTE NvM Blocks 10](#__RefHeading___Toc389222336)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

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

|             |                                 |                                                                          |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                       | **Version**                                                              |
| \<1\>       | \<MDD Guidelines\>              | Software Engineering Process 04.00.00                                    |
| \<2\>       | \<Software Naming Conventions\> | Software Engineering Process 04.00.00 and working EA4 naming conventions |
| \<3\>       | \<Coding standards\>            | Software Engineering Process 04.00.00                                    |
| \<4\>       | \<FDD \>                        | See Synergy subproject version                                           |
|             | \<Add if more available\>       |                                                                          |

# Dependencies

## SWCs

|                      |                                                                                                                                            |
|-----------------------|-------------------------------------------------|
| **Module**           | **Required Feature**                                                                                                                       |
| **MotCtrlMgr**       | Generated struct type declarations for the Motor Control loop / RTE interface data; macros for access of Motor Control loop data           |
| **GuardCfgAndDiagc** | PEG and PBG settings to allow DMA transfers; CM200A_DmaCfgAndUse_Impl_1.3.0 or newer requires CM107A_GuardCfgAndDiagc_Impl_1.0.0 or newer. |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

void DmaRegInin (void) needs to be a trusted function

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

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

|                                          |           |         |
|------------------------------------------|-----------|---------|
| **Constant**                             | **Notes** | **SWC** |
| **\<Additional configuration changes\>** |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

See DataDict.m file

## Required Global Data Outputs

See DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                       |                             |             |
|-----------------------|-----------------------------|-------------|
| **Init**              | **Scheduling Requirements** | **Trigger** |
| **DmaCfgAndUseInit1** | None                        | RTE Init    |

|                                          |                                                                                                                            |                                                       |
|----------------------------|-----------------|---------------------------|
| **Runnable**                             | **Scheduling Requirements**                                                                                                | **Trigger**                                           |
| **DmaCfgAndUsePer1**                     | Per FDD:” - Execution order of "DmaCfgAndUsePer1" shall schedule start of forward path (as soon as possible start of 2ms)” | RTE 2 ms                                              |
| **DmaWaitForMotCtrlTo2MilliSecTrf_Oper** | N/A                                                                                                                        | On invocation of DmaWaitForMotCtrlTo2MilliSecTrf.Oper |
| **DmaEna2MilliSecToMotCtrlTrf_Oper**     | N/A                                                                                                                        | On invocation of DmaEna2MilliSecToMotCtrlTrf.Oper     |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                                     |              |           |
|-------------------------------------|--------------|-----------|
| **Memory Section**                  | **Contents** | **Notes** |
| **CDD_DmaCfgAndUse_START_SEC_CODE** |              |           |
|                                     |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

None

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