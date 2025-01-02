---
layout: default
title: RamMem_Integration Manual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**RamMem**

**VERSION:** **2**

**DATE:** **08/20/16**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                 |                    |             |          |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                 | **Author**         | **Version** | **Date** |
| 1           | Initial version                 | Selva Sengottaiyan | 1.0         | 04/11/16 |
| 2           | Uodated to design version 3.0.1 | Avinash James      | 2.0         | 08/23/16 |
|             |                                 |                    |             |          |
|             |                                 |                    |             |          |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 8](#configuration-requirements)

[4.1 Build Time Config 8](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
8](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
8](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#__RefHeading___Toc447790833)

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

|                  |                 |
|------------------|-----------------|
| **Abbreviation** | **Description** |
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

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

**RamMemLclRamSngBitEcc** – – Callout function for Non-Rte Server
Interface , Call back functions for MCU ECM Error Source RAM Memory
single bit ECC.

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
|             |           |     |

## Configuration Files to be provided by Integration Project

N/A

## Da Vinci Parameter Configuration Changes

<table style="width:100%;">
<colgroup>
<col style="width: 50%" />
<col style="width: 39%" />
<col style="width: 10%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>/Renesas/EcucDefs_Mcu/Mcu/McuModuleConfiguration</p>
<p>/McuEcmErrorSourcesCfg/McuEcmErrorSource34</p></td>
<td>Call back function name is “RamMemLclRamSngBitEcc”. Refer the CM104A
Integration manual for the configuration of the error source. (Type of
the error, classification of the error eg FENMI or EI information)
.</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## DaVinci Interrupt Configuration Changes

|              |           |
|--------------|-----------|
| **ISR Name** | **Notes** |
|              |           |
|              |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
|              |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

Yes

# Runnable Scheduling 

API usage and scheduling of BSW components expected to be captured at a
project architectural level and is beyond the scope of this document.
Third party documentation can be referenced as needed.

|             |                             |                    |
|-------------|-----------------------------|--------------------|
| **Init**    | **Scheduling Requirements** | **Trigger**        |
| RamMemInit1 | RTE initializaton           | RTE initialization |
|             |                             |                    |
|             |                             |                    |

|            |                             |             |
|------------|-----------------------------|-------------|
|            | **Scheduling Requirements** | **Trigger** |
| RamMemPer1 |                             | 2ms         |

**.**

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

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

## NvM Blocks

# Compiler Settings

##  Preprocessor MACRO

## Optimization Settings

# Appendix

*None*

{% endraw %}