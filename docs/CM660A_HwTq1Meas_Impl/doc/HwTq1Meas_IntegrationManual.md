---
layout: default
title: HwTq1Meas_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**HwTq1Meas**

**VERSION: 3.0**

**DATE:** **21-Dec-2015**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                           |             |             |             |
|-----|------------------------------------|------------|---------|-----------|
| **Sl. No.** | **Description**                           | **Author**  | **Version** | **Date**    |
| 1           | Initial version                           | Rijvi Ahmed | 1.0         | 11-Aug-2015 |
| 2           | Updated for CM660A_HwTq1Meas_Design_1.4.0 | Selva       | 2.0         | 14-Oct-2015 |
| 3           | Updated for CM660A_HwTq1Meas_Design_1.6.0 | Selva       | 3.0         | 21-Dec-2015 |

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
7](#davinci-interrupt-configuration-changes)

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

|                  |                            |
|------------------|----------------------------|
| **Abbreviation** | **Description**            |
| DFD              | Design functional diagram  |
| MDD              | Module design Document     |
| FDD              | Functional Design Document |
|                  |                            |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | FDD – CM660A HwTq1Meas      | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Software Coding Standards   | Process 04.02.00               |

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

CDD_HwTq1Meas_Cfg.h

*Note: Temporarily this file can be copied from the contract folder.
Later revision will have the Davinci configuration parameter to generate
the file.*

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

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                    |                             |                |
|--------------------|-----------------------------|----------------|
| **Init**           | **Scheduling Requirements** | **Trigger**    |
| **HwTq1MeasInit1** | **None**                    | **RTE (Init)** |

|                                     |                             |                  |
|----------------------------|------------------------------|---------------|
| **Runnable**                        | **Scheduling Requirements** | **Trigger**      |
| **HwTq1MeasPer1**                   | **None**                    | **RTE (2 ms)**   |
| **HwTq1MeasPer2**                   | **None**                    | **RTE (100 ms)** |
| **HwTq1MeasHwTq1AutTrim_Oper**      | **None**                    | **On event**     |
| **HwTq1MeasHwTq1ClrTrim_Oper**      | **None**                    | **On event**     |
| **HwTq1MeasHwTq1ReadTrim_Oper**     | **None**                    | **On event**     |
| **HwTq1MeasHwTq1TrimPrfmdSts_Oper** | **None**                    | **On event**     |
| **HwTq1MeasHwTq1WrTrim_Oper**       | **None**                    | **On event**     |
| **HwTq1MeasTrigStrt_Oper**          | **None**                    | **On event**     |

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

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*Port Configuration SENT1SPCO output:*

*Port (that’s needs to be configured as SENT1SPCO) should be initialized
as input DIO with level high.*

*The client call IoHwAb_SetFctPrphlHwTq1_Oper will reset the pin to
output Alterante mode for SENT1SPCO.*

{% endraw %}