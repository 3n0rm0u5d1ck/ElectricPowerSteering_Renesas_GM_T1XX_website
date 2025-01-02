---
layout: default
title: Adc1CfgAndUse_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Adc1 Cfg And Use**

**VERSION:** **3.0**

**DATE: 09-Jun-2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                   |                    |             |             |
|-----|-------------------------------|----------------|----------|------------|
| **Sl. No.** | **Description**                                   | **Author**         | **Version** | **Date**    |
| 1           | Initial version                                   | Selva Sengottaiyan | 1.0         | 4-May-2015  |
| 2           | Updated for design rev. 2.0.0                     | Rijvi              | 2.0         | 05-Feb-2016 |
| 3           | Added Newperiodic and removed one server runnable | Avinash James      | 3.0         | 9-Jun-2016  |

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

[7.3 Non RTE NvM Blocks [10](#_Toc418747827)](#_Toc418747827)

[7.4 RTE NvM Blocks [10](#_Toc418747828)](#_Toc418747828)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**                         |
|------------------|-----------------------------------------|
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                  | **Version**                     |
|-------------|----------------------------|---------------------------------|
| 1           | FDD – CM320A Adc1CfgAndUse | See synergy sub project version |
|             |                            |                                 |
|             |                            |                                 |
|             |                            |                                 |
|             |                            |                                 |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| None        |           |     |

## Configuration Files to be provided by Integration Project

Yes

## Da Vinci Parameter Configuration Changes

| **Parameter**                    | **Notes** | **SWC** |
|----------------------------------|-----------|---------|
| Refer the . m file in the design |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **N/A**      |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**           | **Scheduling Requirements** | **Trigger** |
|--------------------|-----------------------------|-------------|
| Adc1CfgAndUseInit1 | None                        | RTE         |
|                    |                             |             |

| **Runnable**                  | **Scheduling Requirements** | **Trigger** |
|-------------------------------|-----------------------------|-------------|
| Adc1CfgAndUsePer1             | None                        | 2ms(RTE)    |
| Adc1CfgAndUsePer2             | None                        | 2ms(RTE)    |
| Adc1CfgAndUseAdc1EnaCnvn_Oper | None                        | On event    |
|                               |                             |             |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section** | **Contents** | **Notes** |
|--------------------|--------------|-----------|
| **None**           |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

##  [section]

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}