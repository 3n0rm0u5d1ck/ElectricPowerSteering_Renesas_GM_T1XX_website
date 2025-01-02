---
layout: default
title: EotProtnFwl_Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**SF027A_EotProtnFwl**

**VERSION: 1.0**

**DATE: 01-Feb-2016**

**Prepared By:**

**Sarika Natu,**

**KPIT Technologies,**

**India**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|                 |             |             |             |
|-----------------|-------------|-------------|-------------|
| **Description** | **Author**  | **Version** | **Date**    |
| Initial version | Sarika Natu | 1.0         | 01-Feb-2016 |

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
7](#__RefHeading___Toc442192160)

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

[7.3 NvM Blocks 10](#nvm-blocks)

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

|             |                                                                                                                                                               |                                  |
|--------|-----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                                                                                                                                                     | **Version**                      |
| 1           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                     |
| 2           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 2.0                              |
| 3           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                              |
| 4           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2                |
| 5           | SF027_EotProtnFwl_Design                                                                                                                                      | Refer Synergy subproject version |

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

**None**

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

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                             |             |
|----------------------|-----------------------------|-------------|
| **Init**             | **Scheduling Requirements** | **Trigger** |
| **EotProtnFwlInit1** | None                        | RTE (Init)  |

|                     |                             |             |
|---------------------|-----------------------------|-------------|
| **Runnable**        | **Scheduling Requirements** | **Trigger** |
| **EotProtnFwlPer1** | None                        | RTE(2ms)    |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                                |              |           |
|--------------------------------|--------------|-----------|
| **Memory Section**             | **Contents** | **Notes** |
| **EotProtnFwl_START_SEC_CODE** |              |           |
| **EotProtnFwl_STOP_SEC_CODE**  |              |           |

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

None

## Optimization Settings

None

# Appendix

None

{% endraw %}