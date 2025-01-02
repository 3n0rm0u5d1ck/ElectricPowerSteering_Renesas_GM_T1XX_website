---
layout: default
title: ClkCfgAndMon Integration Manual 
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**ClkCfgAndMon**

**VERSION: 1.0**

**DATE: 03-04-2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |               |             |             |
|-------------|-----------------|---------------|-------------|-------------|
| **Sl. No.** | **Description** | **Author**    | **Version** | **Date**    |
| 1           | Initial version | Avinash James | 1.0         | 04-Mar-2016 |

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
8](#__RefHeading___Toc444864778)

[4.5 Manual Configuration Changes 8](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
9](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 9](#required-global-data-inputs)

[5.2 Required Global Data Outputs 9](#required-global-data-outputs)

[5.3 Specific Include Path present 9](#specific-include-path-present)

[6 Runnable Scheduling 10](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 11](#memory-map-requirements)

[7.1 Mapping 11](#mapping)

[7.2 Usage 11](#usage)

[7.3 NvM Blocks 11](#nvm-blocks)

[8 Compiler Settings 12](#compiler-settings)

[8.1 Preprocessor MACRO 12](#preprocessor-macro)

[8.2 Optimization Settings 12](#optimization-settings)

[9 Appendix 13](#appendix)

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

|             |                             |             |
|-------------|-----------------------------|-------------|
| **Sr. No.** | **Title**                   | **Version** |
| 1           | FDD CM109A_ClkCfgAndMon.doc | 1.0         |
|             |                             |             |
|             |                             |             |
|             |                             |             |
|             |                             |             |

# Dependencies

## SWCs

|     |     |
|-----|-----|
|     |     |
|     |     |

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

None

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 47%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm0MonitoringClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm0Operation</td>
<td>Set TRUE</td>
<td>Mcu</td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm0SamplingClockAccuracy</td>
<td>Set to 10</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm1MonitoringClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm1Operation</td>
<td>Set TRUE</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm1SamplingClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm2MonitoringClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm2Operation</td>
<td>Set TRUE</td>
<td>Mcu</td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm2SamplingClockAccuracy</td>
<td>Set to 10</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm3MonitoringClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
<tr class="even">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm3Operation</td>
<td>Set TRUE</td>
<td>Mcu</td>
</tr>
<tr class="odd">
<td>/Renesas/EcucDefs_Mcu/Mcu/<br />
McuGeneralConfiguration/<br />
McuClm3SamplingClockAccuracy</td>
<td>Set to 1</td>
<td>Mcu</td>
</tr>
</tbody>
</table>

## DaVinci Interrupt Configuration Changes

|                                             |            |                         |           |
|-------------|--------|---------------------------|-------------------------|
| **ISR Name**                                | **VIM \#** | **Priority Dependency** | **Notes** |
| **\<Configurator Changes for Interrupts\>** |            |                         |           |

## Manual Configuration Changes

|                                          |           |         |
|------------------------------------------|-----------|---------|
| **Constant**                             | **Notes** | **SWC** |
| **\<Additional configuration changes\>** |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

> None

## Required Global Data Outputs

> None

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|          |                             |             |
|----------|-----------------------------|-------------|
| **Init** | **Scheduling Requirements** | **Trigger** |
|          |                             |             |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
|              |                             |             |

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
|                    |              |           |
|                    |              |           |

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

\<Define all the preprocessor Macros needed and conditions when
needed\>.

## Optimization Settings

\<Define Optimization levels that are needed and conditions when
needed\>.

# Appendix

*\<This section is for appendix\>*

{% endraw %}