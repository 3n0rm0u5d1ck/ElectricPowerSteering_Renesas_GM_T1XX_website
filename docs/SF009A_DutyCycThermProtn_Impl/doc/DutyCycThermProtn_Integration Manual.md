---
layout: default
title: DutyCycThermProtn_Integration Manual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**SF009A_DutyCycThermProtn**

**VERSION: 1.0**

**DATE: 02-Oct-2015**

**Prepared By:**

**Sarika Natu,**

**KPIT Technologies,**

**India**

**Revision History**

|                 |             |             |             |
|-----------------|-------------|-------------|-------------|
| **Description** | **Author**  | **Version** | **Date**    |
| Initial version | Sarika Natu | 1.0         | 02-Oct-2015 |

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
|                  |                           |
|                  |                           |
|                  |                           |

# References

|             |                                       |                                   |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                             | **Version**                       |
| 1           | MDD Guidelines                        | Software Process Release 04.02.00 |
| 2           | Software Naming Conventions           | Software Process Release 04.02.00 |
| 3           | Design and Coding standards           | Software Process Release 04.02.00 |
| 4           | FDD – SF009A_DutyCycThermProtn_Design | See Synergy sub project version   |

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

Refer DataDict.m file in the FDD

## Required Global Data Outputs

Refer DataDict.m file in the FDD

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                            |                             |             |
|----------------------------|-----------------------------|-------------|
| **Init**                   | **Scheduling Requirements** | **Trigger** |
| **DutyCycThermProtnInit1** | None                        | RTE(Init)   |

|                           |                             |             |
|---------------------------|-----------------------------|-------------|
| **Runnable**              | **Scheduling Requirements** | **Trigger** |
| **DutyCycThermProtnPer1** | None                        | RTE(100ms)  |

# Memory Map REQUIREMENTS

## Mapping

|                                      |              |           |
|--------------------------------------|--------------|-----------|
| **Memory Section**                   | **Contents** | **Notes** |
| **DutyCycThermProtn_START_SEC_CODE** |              |           |
|                                      |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

None

{% endraw %}