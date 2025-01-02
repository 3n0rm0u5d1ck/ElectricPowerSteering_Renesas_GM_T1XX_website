---
layout: default
title: HwAg1Meas_IntegrationManual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**HwAg1Meas**

**VERSION:** **4.0**

**DATE: 21-Jun-2015**

**Prepared By:**

**TATA ELXSI**

**CHENNAI**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                        |                    |             |              |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**        | **Author**         | **Version** | **Date**     |
| 1           | Initial version        | Selva Sengottaiyan | 1.0         | 21-July-2015 |
| 2           | Updated to FDD v 1.2.0 | Selva Sengottaiyan | 2.0         | 11-Sep-2015  |
| 3           | Updated to FDD v1.4.0  | Selva Sengottaiyan | 3.0         | 22-Dec-2015  |
| 4           | Updated to FDD v1.8.0  | TATA               | 4.0         | 21-Jun-2015  |

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
7](#__RefHeading___Toc425325791)

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

[7.4 RTE NvM Blocks 10](#rte-nvm-blocks)

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

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| v           | FDD – CM670A_HwAg1Meas_Design        | See Synergy sub project version |
| 2           | Software Naming Conventions          | Process 4.01.00                 |
| 3           | Software Design and Coding Standards | Process 4.01.00                 |
|             |                                      |                                 |
|             |                                      |                                 |

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

**HwAg1Meas_Cfg.h**

## Da Vinci Parameter Configuration Changes

|                       |                                                  |         |
|-----------------------------|----------------------------------|----------|
| **Parameter**         | **Notes**                                        | **SWC** |
| **Refer the . mfile** | CM10 provides program specific NTC configuration |         |

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

Refer DataDict.m file file in the FDD

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                    |                             |             |
|--------------------|-----------------------------|-------------|
| **Init**           | **Scheduling Requirements** | **Trigger** |
| **HwAg1MeasInit1** | None                        | RTE (Init)  |

|                                     |                             |                   |
|---------------------------|--------------------------------|-------------|
| **Runnable**                        | **Scheduling Requirements** | **Trigger**       |
| **HwAg1MeasPer1**                   | None                        | RTE (2 ms)        |
| **HwAg1MeasPer2**                   | None                        | RTE (2 ms)        |
| **HwAg1MeasPer3**                   | None                        | RTE (2 ms)        |
| **HwAg1MeasPer4**                   | None                        | RTE (2ms)         |
| **HwAg1MeasPer5**                   | None                        | RTE (100ms)       |
|                                     |                             |                   |
| **HwAg1MeasHwAg1AutTrim_Oper**      | None                        | Server invocation |
| **HwAg1MeasHwAg1ClrTrim_Oper**      | None                        | Server invocation |
| **HwAg1MeasHwAg1ReadTrim_Oper**     | None                        | Server invocation |
| **HwAg1MeasHwAg1ReadTrim_Oper**     | None                        | Server invocation |
| **HwAg1MeasHwAg1TrimPrfmdSts_Oper** | None                        | Server invocation |
| **HwAg1MeasHwAg1WrTrim_Oper**       | None                        | Server invocation |

**.**

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

## NvM Blocks

## RTE NvM Blocks

|                |
|----------------|
| **Block Name** |
| **HwAg1Offs**  |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

**None**.

## Optimization Settings

**None**.

# Appendix

## SENT2SPCO port out should be configured to be high level on port configurations refer CM10 for SPCO port configuration (SENT2SPCO shall be port level high). port configuration SENT2SPCO output:port (that’s needs to be configured as SENT2SPCO) should be initialized as input dio with level high.the client call Iohwab_Setfctprphlhwag1_oper will reset the pin to output alterante mode for SENT2SPCO

## Design Recommandation :

## - Port Config RSENT2 IO pin shall setup default input.

## - Schedule execution of tasks as per below order at the end of 2ms task

##  1. "HwAg1MeasPer2" 

##  2. "HwAg1MeasPer3" 

##  3. "HwAg1MeasPer4"

##  4. "HwAg1MeasPer1" 

## - Schedule "HwAg1MeasPer4" & "HwAg1MeasPer1" shall at least 110us apart. 

{% endraw %}