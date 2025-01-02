---
layout: default
title: Swp_IntegrationManual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Swp**

**VERSION: 2.0**

**DATE:** **01-Feb-2016**

**Prepared By:**

**Krishna Kanth Anne,**

**Software Engineering,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                          |                    |             |           |
|-----------|---------------------|-----------------|----------|---------------|
| **Sl. No.** | **Description**          | **Author**         | **Version** | **Date**  |
| 1           | Initial version          | Krishna Kanth Anne | 1.0         | 20-Oct-15 |
| 2           | Fix for anomaly EA4#2461 | Krishna Kanth Anne | 2.0         | 01-Feb-16 |

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

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | MDD Guidelines              | Process 04.02.00               |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Coding standards            | Process 04.02.00               |
| 4           | FDD : DF002A_Swp_Design     | See Synergy Subproject version |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   |                      |

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |                                                                                                            |     |
|---------------------------|--------------------------------------|--------|
| **Modules** | **Notes**                                                                                                  |     |
| **Swp**     | Set to STD_ON for Sweep software build, set to STD_OFF for normal build. Constant resides in “Swp.h” file. |     |

## Configuration Files to be provided by Integration Project

> None

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
| **NA**        |           |         |

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **NA**       |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **NA**       |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Please refer DataDict.m file

## Required Global Data Outputs

> Please refer DataDict.m file

## Specific Include Path present

Swp.h file shall have to be included.

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Init**     | **Scheduling Requirements** | **Trigger** |
| **SwpInit1** |                             | RTE_Init    |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
| **SwpPer1**  | None                        | RTE(2ms)    |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
| **SwpPer2**  | None                        | RTE(2ms)    |

# Memory Map REQUIREMENTS

## Mapping

|                        |                        |                                                                                                                                                                                     |
|--------------------------------|--------------------|---------------------|
| **Memory Section**     | **Contents**           | **Notes**                                                                                                                                                                           |
| **Swp_START_SEC_CODE** | Swp code and variables | **This code section statement will contain variables that need mapping to GlobalShared memory during** **Sweep** **builds (these variables are present when** **SWPENA == STD_ON)** |
|                        |                        |                                                                                                                                                                                     |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

None.

# Compiler Settings

##  Preprocessor MACRO

> None

## Optimization Settings

> None

# Appendix

> None

{% endraw %}