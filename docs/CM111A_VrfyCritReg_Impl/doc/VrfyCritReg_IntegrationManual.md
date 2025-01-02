---
layout: default
title: VrfyCritReg_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**VrfyCritReg**

**VERSION:** **2.0**

**DATE: 14-Apr-2016**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                       |                        |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                                       | **Author**             | **Version** | **Date**    |
| 1           | Initial version                                                       | Sankardu Varadapureddi | 1.0         | 14-Jan-2016 |
| 2           | Updated to “ Critical register” checks at init and periodic functions | Selva Sengottaiyan     | 2           | 14-Apr-2016 |

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
| 1           | FDD : CM111A_VrfyCritReg \_Design    | See Synergy sub project version |
| 2           | Software Naming Conventions          | Process 4.02.00                 |
| 3           | Software Design and Coding Standards | Process 4.02.00                 |
|             |                                      |                                 |
|             |                                      |                                 |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   |                      |

## Global Functions(Non RTE) to be provided to Integration Project

CritRegIninChk--- Needs to be trusted function because it needs to run
in supervisor mode

CritRegPerChk--- Needs to be trusted function because it needs to run in
supervisor mode

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

**CDD_VrfyCritReg_Cfg.c**

**CDD_VrfyCritReg_Cfg_private.h**

## Da Vinci Parameter Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 51%" />
<col style="width: 37%" />
<col style="width: 10%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/VrfyCritReg/VrfySysCritRegInitSignallist</strong></td>
<td><p>System Critical registers with 32 bit Access that needs to
checked at Init</p>
<p>function</p></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/VrfyCritReg/VrfySysCritRegPerSignallist</strong></td>
<td>System Critical registers with 32 bit Access that needs to checked
periodically</td>
<td></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg32bitPerSignallist</strong></td>
<td>Critical registers with 32 bit Access that needs to checked
periodically</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg32bitInitSignallist</strong></td>
<td>Critical registers with 32 bit Access that needs to checked at
Initialisation</td>
<td></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg16bitPerSignallist</strong></td>
<td>Critical registers with 16 bit Access that needs to checked
periodically</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg16bitInitSignallist</strong></td>
<td>Critical registers with 32 bit Access that needs to checked at
Initialisation</td>
<td></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg8bitPerSignallist</strong></td>
<td>Critical registers with 8 bit Access that needs to checked
periodically</td>
<td></td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/VrfyCritReg/VrfyCritReg8bitInitSignallist</strong></td>
<td>Critical registers with 32 bit Access that needs to checked at
Initialisation</td>
<td></td>
</tr>
</tbody>
</table>

Note:

Refer the CM010 RH850 Static Register Evaluation.xlsm for configuration
of critical registers

Refer the Appendix below for the steps involved in generating “Da Vinci
Configuration files needed for critical register check “ from the
Script.

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

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes.

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                             |             |
|----------------------|-----------------------------|-------------|
| **Init**             | **Scheduling Requirements** | **Trigger** |
| **VrfyCritRegInit1** | None                        | RTE (Init)  |

|                     |                             |             |
|---------------------|-----------------------------|-------------|
| **Runnable**        | **Scheduling Requirements** | **Trigger** |
| **VrfyCritRegPer1** | None                        | RTE (10ms)  |

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

None

# Compiler Settings

##  Preprocessor MACRO

**None**.

## Optimization Settings

**None**.

# Appendix

*Steps to generate CDD_VrfyCritReg_Cfg:*

1.  *Run CriticalRegisterGenerator.py* *(Script will be* *placed along
    with* *Excel RH850 Static Register Evaluation)*

2.  *The input for this Generator tool is the Excel Sheet* *RH850 Static
    Register Evaluation*

3.  *OUTPUT Generated will be* *“CDD_VrfyCritReg_Cfg.arxml* *“* *and
    rename it as “EPS_VrfyCritReg_ecuc.arxml” or corresponding .arxml
    name that matches project*

{% endraw %}