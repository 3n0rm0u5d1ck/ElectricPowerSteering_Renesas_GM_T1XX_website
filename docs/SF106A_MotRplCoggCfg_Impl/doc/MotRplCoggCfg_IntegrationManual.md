---
layout: default
title: MotRplCoggCfg_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**MotRplCoggCfg**

**VERSION: 1**

**DATE: 09-Feb-2016**

**Prepared By:**

**Selva Sengottaiyan**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                 |             |             |
|-------------|-----------------|-----------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**      | **Version** | **Date**    |
| 1           | Initial version | S. Sengottaiyan | 1.0         | 09-Feb-2016 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Dependencies 7](#dependencies-1)

[4.1 SWCs 7](#swcs-1)

[4.2 Global Functions(Non RTE) to be provided to Integration Project
7](#global-functionsnon-rte-to-be-provided-to-integration-project-1)

[5 Configuration REQUIREMeNTS 8](#configuration-requirements)

[5.1 Build Time Config 8](#build-time-config)

[5.2 Configuration Files to be provided by Integration Project
8](#configuration-files-to-be-provided-by-integration-project)

[5.3 Da Vinci Parameter Configuration Changes
8](#da-vinci-parameter-configuration-changes)

[5.4 DaVinci Interrupt Configuration Changes
8](#__RefHeading___Toc442638987)

[5.5 Manual Configuration Changes 8](#manual-configuration-changes)

[6 Integration DATAFLOW REQUIREMENTS
9](#integration-dataflow-requirements)

[6.1 Required Global Data Inputs 9](#required-global-data-inputs)

[6.2 Required Global Data Outputs 9](#required-global-data-outputs)

[6.3 Specific Include Path present 9](#specific-include-path-present)

[7 Runnable Scheduling 10](#runnable-scheduling)

[8 Memory Map REQUIREMENTS 11](#memory-map-requirements)

[8.1 Mapping 11](#mapping)

[8.2 Usage 11](#usage)

[8.3 RTE NvM Blocks 11](#rte-nvm-blocks)

[9 Compiler Settings 12](#compiler-settings)

[9.1 Preprocessor MACRO 12](#preprocessor-macro)

[9.2 Optimization Settings 12](#optimization-settings)

[10 Appendix 13](#appendix)

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

|             |                                |                                |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                      | **Version**                    |
| 1           | FDD – SF106_MotRplCoggCfg_Impl | See Synergy subproject version |
| 2           | Software Naming Conventions    | Process 04.02.01               |
| 3           | Software Coding Standards      | Process 04.02.01               |
|             |                                |                                |
|             |                                |                                |

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

> None

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

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
| **None**      |           |         |

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

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer .m file

## Required Global Data Outputs

Refer .m file

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                        |                             |             |
|------------------------|-----------------------------|-------------|
| **Init**               | **Scheduling Requirements** | **Trigger** |
| **MotRplCoggCfgInit1** | None                        | Rte         |

|                           |                             |      |                           |             |
|------------------|------|--------------------------|--------|---------------|
| **Runnable**              | **Scheduling Requirements** |      |                           | **Trigger** |
| **MotRplCoggCfgPer1**     |                             | None | RTE(2ms)                  |             |
| **SetMotRplCoggPrm_Oper** |                             | None | On server invocation call |             |
| **GetMotRplCoggPrm_Oper** |                             | None | On server invocation call |             |
|                           |                             |      |                           |             |
|                           |                             |      |                           |             |
|                           |                             |      |                           |             |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
|                    |              |           |
|                    |              |           |
|                    |              |           |
|                    |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| MotRplCoggPrm  |

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

None

# 

{% endraw %}