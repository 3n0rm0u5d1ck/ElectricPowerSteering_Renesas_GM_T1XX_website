---
layout: default
title: MotCurrRegVltgLimr_Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**‘MotCurrRegVltgLimr’**

**VERSION: 1.0**

**DATE: 26-May-2015**

**Prepared By:**

**Selva Sengottaiyan**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
**

**Revision History**

|             |                 |                    |             |             |
|-------------|-----------------|--------------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**         | **Version** | **Date**    |
| 1           | Initial version | Selva Sengottaiyan | 1.0         | 4-June-2015 |
|             |                 |                    |             |             |

: ARM Cortex R4 Memory Usage

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[4](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [5](#references)](#references)

[3 Dependencies [6](#dependencies)](#dependencies)

[3.1 SWCs [6](#swcs)](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
[6](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS
[7](#configuration-requirements)](#configuration-requirements)

[4.1 Build Time Config [7](#build-time-config)](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
[7](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
[7](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
[7](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[4.5 Manual Configuration Changes
[7](#manual-configuration-changes)](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
[8](#integration-dataflow-requirements)](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs
[8](#required-global-data-inputs)](#required-global-data-inputs)

[5.2 Required Global Data Outputs
[8](#required-global-data-outputs)](#required-global-data-outputs)

[5.3 Specific Include Path present
[8](#specific-include-path-present)](#specific-include-path-present)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 Usage [10](#usage)](#usage)

[7.3 Non RTE NvM Blocks [10](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks [10](#rte-nvm-blocks)](#rte-nvm-blocks)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**           |
|------------------|---------------------------|
| DFD              | Design functional diagram |
| MDD              | Module design Document    |
|                  |                           |
|                  |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                              | **Version**                     |
|----------|----------------------------------------------|-----------------|
| 1           | FDD – SF105A_MotCurrRegVltgLimr_Design | See Synergy sub project version |
| 2           | Software Naming Conventions            | Process 4.00.00                 |
| 3           | Software Design and Coding Standards   | Process 4.00.00                 |
|             |                                        |                                 |
|             |                                        |                                 |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   |                      |

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **None**     |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file in the FDD

## Required Global Data Outputs

Refer DataDict.m file file in the FDD

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**                    | **Scheduling Requirements** | **Trigger** |
|-----------------------------|-----------------------------|-------------|
| **MotCurrRegVltgLimrInit1** | None                        | Init        |

| **Runnable**               | **Scheduling Requirements** | **Trigger**          |
|-------------------|--------------------------------------|---------------|
| **MotCurrRegVltgLimrPer1** |                             | Motor Control ISR\*2 |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**         | **Contents**                                       | **Notes** |
|--------------------------------|--------------------|---------------------|
| **MotCtrl_START_SEC_CODE** | Code section for Motor Control scheduled functions |           |
|                            |                                                    |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature**                | **RAM** | **ROM** |
|----------------------------|---------|---------|
| **\<Memmap usuage info\>** |         |         |

## Non RTE NvM Blocks

| **Block Name** |
|----------------|
| **None**       |

## RTE NvM Blocks

| **Block Name** |
|----------------|
| **none**       |

# Compiler Settings

##  Preprocessor MACRO

None.

## Optimization Settings

None

# Appendix

*None*

{% endraw %}