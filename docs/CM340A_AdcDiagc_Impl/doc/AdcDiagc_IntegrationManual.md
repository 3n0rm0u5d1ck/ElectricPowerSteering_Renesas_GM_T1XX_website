---
layout: default
title: AdcDiagc_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**AdcDiagc**

**VERSION:** **4.0**

**DATE:** **Aug** **25, 2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                               |               |             |             |
|-----|------------------------------|----------------|----------|-------------|
| **Sl. No.** | **Description**               | **Author**    | **Version** | **Date**    |
| 1           | Initial version               | Rijvi Ahmed   | 1.0         | 02-Feb-2016 |
| 2           | Updated per design rev. 1.1.0 | Rijvi Ahmed   | 2.0         | 23-Mar-2016 |
| 3           | Updated per design rev. 1.6.0 | Avinash James | 3.0         | 18-Jul-2016 |
| 4           | Updated per design rev. 1.7.0 | Avinash James | 4.0         | 25-Aug-2016 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#__RefHeading___Toc442273288)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
7](#__RefHeading___Toc442273292)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#__RefHeading___Toc442273298)

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

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | FDD – CM340A-AdcDiagc_Design         | See Synergy sub project version |
| 2           | Software Naming Conventions          | Process 04.02.01                |
| 3           | Software Design and Coding Standards | Process 04.02.01                |
|             |                                      |                                 |
|             |                                      |                                 |

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

1.  <span id="__RefHeading___Toc442273288"
    class="anchor"></span>Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

No

## Da Vinci Parameter Configuration Changes

|                                     |           |         |
|-------------------------------------|-----------|---------|
| **Parameter**                       | **Notes** | **SWC** |
| **Refer the .m file in the design** |           |         |

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

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

None <span id="__RefHeading___Toc442273298"
class="anchor"></span>Runnable Scheduling

This section specifies the required runnable scheduling.

|                   |                             |             |
|-------------------|-----------------------------|-------------|
| **Init**          | **Scheduling Requirements** | **Trigger** |
| **AdcDiagcInit1** | None                        | RTE/Init    |

|                  |                             |             |
|------------------|-----------------------------|-------------|
| **Runnable**     | **Scheduling Requirements** | **Trigger** |
| **AdcDiagcPer1** | None                        | RTE/2ms     |
|                  |                             |             |

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

None.

## Optimization Settings

None.

# Appendix

*None.*

{% endraw %}