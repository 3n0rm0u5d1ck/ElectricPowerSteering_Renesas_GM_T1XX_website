---
layout: default
title: ChkPt Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**ChkPt**

**VERSION: 4**

**DATE: 08/17/2015**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                    |             |             |            |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                    | **Author**  | **Version** | **Date**   |
| 1           | Initial version                    | L. Wendling | 1           | 03/05/2015 |
| 2           | Updates for 1a build               | L. Wendling | 2           | 05/08/2015 |
| 3           | Added 4ms Application 10 functions | L. Wendling | 3           | 07/15/2015 |
| 4           | Added 10ms Appl10 functions        | J. Julien   | 4           | 08/17/2015 |

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

[7.3 Non RTE NvM Blocks 10](#non-rte-nvm-blocks)

[7.4 RTE NvM Blocks 10](#rte-nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                 |
|------------------|-----------------|
| **Abbreviation** | **Description** |
|                  |                 |
|                  |                 |
|                  |                 |
|                  |                 |
|                  |                 |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |           |             |
|-------------|-----------|-------------|
| **Sr. No.** | **Title** | **Version** |
|             |           |             |
|             |           |             |
|             |           |             |
|             |           |             |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

> ChkPt_10msBswAppl10Strt – This function is expected to be called at
> the start of the BSW 10ms loop to provide alive and program flow
> monitoring.
>
> ChkPt_10msBswAppl10End – This function is expected to be called at the
> end of the BSW 10ms loop to provide alive and program flow monitoring.

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
| **N/A**       |           |         |

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **N/A**      |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

N/A

## Required Global Data Outputs

N/A

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|          |                             |             |
|----------|-----------------------------|-------------|
| **Init** | **Scheduling Requirements** | **Trigger** |
|          |                             |             |
|          |                             |             |

|                             |                             |                |
|-----------------------------|-----------------------------|----------------|
| **Runnable**                | **Scheduling Requirements** | **Trigger**    |
| **ChkPt_2msAppl10Strt**     | First runnable of task      | RTE 2ms Task   |
| **ChkPt_2msAppl10End**      | Last runnable of task       | RTE 2ms Task   |
| **ChkPt_4msAppl10Strt**     | First runnable of task      | RTE 4ms Task   |
| **ChkPt_4msAppl10End**      | Last runnable of task       | RTE 4ms Task   |
| **ChkPt_10msAppl10Strt**    | First runnable of task      | RTE 10ms Task  |
| **ChkPt_10msAppl10End**     | Last runnable of task       | RTE 10ms Task  |
| **ChkPt_100msAppl10Strt**   | First runnable of task      | RTE 100ms Task |
| **ChkPt_100msAppl10End**    | Last runnable of task       | RTE 100ms Task |
| **ChkPt_10msAppl6Strt**     | First runnable of task      | RTE 10ms Task  |
| **ChkPt_10msAppl6End**      | Last runnable of task       | RTE 10ms Task  |
| **ChkPt_2msAppl6Strt**      | First runnable of task      | RTE 2ms Task   |
| **ChkPt_2msAppl6End**       | Last runnable of task       | RTE 2ms Task   |
| **ChkPt_10msBswAppl10Strt** | First runnable of task      | BSW 10ms Task  |
| **ChkPt_10msBswAppl10End**  | Last runnable of task       | BSW 10ms Task  |
|                             |                             |                |
|                             |                             |                |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                              |              |           |
|------------------------------|--------------|-----------|
| **Memory Section**           | **Contents** | **Notes** |
| **CDD_ChkPt_START_SEC_CODE** |              |           |
|                              |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

|                                           |
|-------------------------------------------|
| **Block Name**                            |
| **\<NVM block used Non RTE functions \>** |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

|                                          |
|------------------------------------------|
| **Block Name**                           |
| **\<NVM block used in RTE functions \>** |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*\<This section is for appendix\>*

{% endraw %}