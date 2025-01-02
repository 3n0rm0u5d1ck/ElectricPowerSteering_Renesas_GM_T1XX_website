---
layout: default
title: FltInj_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**FltInj**

**VERSION: 1.0**

**DATE: 08/25/15**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|                 |                |             |          |
|-----------------|----------------|-------------|----------|
| **Description** | **Author**     | **Version** | **Date** |
| Initial version | Lucas Wendling | 1.0         | 08/25/15 |

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
7](#__RefHeading___Toc428280000)

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

|             |                                          |                                |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                                | **Version**                    |
| 1           | EA4 Software Naming Conventions.doc      | 01.00.00                       |
| 2           | Software Design and Coding Standards.doc | 2.1                            |
| 3           | DF001A_FltInj_Design                     | See Synergy subproject version |
|             |                                          |                                |
|             |                                          |                                |

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

|                         |                                                                                                                         |     |
|---------------------------|--------------------------------------|--------|
| **Build Constant Name** | **Notes**                                                                                                               |     |
| **FLTINJENA**           | Set to STD_ON for fault injection software build, set to STD_OFF for normal build. Constant resides in “FltInj.h” file. |     |

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

See DataDict.m file

## Required Global Data Outputs

See DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|          |                             |             |
|----------|-----------------------------|-------------|
| **Init** | **Scheduling Requirements** | **Trigger** |
| **None** |                             |             |

|                       |                             |               |
|-----------------------|-----------------------------|---------------|
| **Runnable**          | **Scheduling Requirements** | **Trigger**   |
| **FltInjPer1**        | None                        | RTE 2ms       |
| **FltInj_f32_Oper**   | None                        | On Invocation |
| **FltInj_logl_Oper**  | None                        | On Invocation |
| **FltInj_u08_Oper**   | None                        | On Invocation |
| **FltInj_u0p16_Oper** | None                        | On Invocation |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                           |                                    |                                                                                                                                                                                      |
|--------------------------------|--------------------|---------------------|
| **Memory Section**        | **Contents**                       | **Notes**                                                                                                                                                                            |
| **FltInj_START_SEC_CODE** | Fault Injection code and variables | **This code section statement will contain variables that need mapping to GlobalShared memory during fault injection builds (these variables are present when FLTINJENA == STD_ON)** |
|                           |                                    |                                                                                                                                                                                      |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*\<This section is for appendix\>*

{% endraw %}