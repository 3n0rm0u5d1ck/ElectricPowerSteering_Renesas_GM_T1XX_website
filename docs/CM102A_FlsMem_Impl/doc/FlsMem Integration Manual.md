---
layout: default
title: FlsMem Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**FlsMem**

**VERSION:** **5**

**DATE:** **08/26/16**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                             |                |             |            |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                                             | **Author**     | **Version** | **Date**   |
| 1           | Initial version                                                             | Lucas Wendling | 1           | 10/07/15   |
| 2           | Updated with changes for DTS configuration for Flash CRC check              | Avinash James  | 2           | 03/18/16   |
| 3           | Removed FlsMemCodFlsSngBit handling                                         | Avinash James  | 3           | 03/31/16   |
| 4           | Added Trusted function for DTS clean up                                     | Avinash James  | 4           | 04/18/16   |
| 5           | Added Single bit ECC error handler and name correction for trusted funcions | Avinash James  | 5           | 08/26/2016 |

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
7](#__RefHeading___Toc459966917)

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
| CCT              | Common Checksum Tool       |
|                  |                            |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | FDD – CM102A FlsMem         | See Synergy subproject version |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Software Coding Standards   | Process 04.02.00               |
|             |                             |                                |
|             |                             |                                |

# Dependencies

## SWCs

|                            |                                                    |
|-----------------------|-------------------------------------------------|
| **Module**                 | **Required Feature**                               |
| **AR202A MicroCtrlrSuprt** | NxtrMcuSuprtLib functions and register definitions |
| **CM800A SyncCrc**         | CRC HW Module Configuration and Allocation         |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

DtsInin - To be defined as a trusted function as the DTS Channel master
registers need to be configured in the supervisor mode.

DtsClnUp - To be defined as a trusted function as the DTS registers are
being re-configured in the supervisor mode to avoid access protection
violation

CodFlsSngBitEcc – Single bit code flash ECC error handler call back
function provided to the MCAL driver

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

CDD_FlsMem_Cfg.c

CDD_FlsMem_Cfg_private.h

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 44%" />
<col style="width: 24%" />
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
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/ StartAddress</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region(for eg:- Boot, App, Cal1) has a start address where
the code resides on the flash</p></td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/Length</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a length defined for the region</p></td>
<td>FlsMem</td>
</tr>
<tr class="odd">
<td>/Nexteer/FlsMem/FlashCRCRegnConfig/PredefinedCrcAddress</td>
<td><p>Configured with “FlashCRCRegnConfig”</p>
<p>Each Flash region has a PredefinedCrcAddress defined for the region
which is used by the CCT tool for storing the checksum on the flash and
serves as the reference location to retrieve the pre calculated CRC and
do a comparison with calculated CRC</p></td>
<td>FlsMem</td>
</tr>
<tr class="even">
<td><p>/Renesas/EcucDefs_Mcu/Mcu/McuModuleConfiguration</p>
<p>/McuEcmErrorSourcesCfg/McuEcmErrorSource36</p></td>
<td>Call back function name is “CodFlsSngBitEcc”. Refer the CM104A
Integration manual for the configuration of the error source. (Type of
the error, classification of the error eg FENMI or EI information)
.</td>
<td></td>
</tr>
</tbody>
</table>

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|              |            |                         |           |

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

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                 |                                            |                                   |
|-------------------|---------------------------------------|---------------|
| **Init**        | **Scheduling Requirements**                | **Trigger**                       |
| **FlsMemInit1** | None                                       | Once At Init (RTE)                |
| **FlsMemInit2** | Non-RTE Init, Called in Startup Sequence\* | Function call in Startup Sequence |

|                |                             |             |
|----------------|-----------------------------|-------------|
| **Runnable**   | **Scheduling Requirements** | **Trigger** |
|                |                             |             |
|                |                             |             |
| **FlsMemPer2** | None                        | 100ms(RTE)  |

\*“FlsMemInit2” shall schedule after OS Start – Refer CM100A Start up
sequence.

PEG shall be configured before “FlsMemInit2”.

CrcHw Init shall be scheduled before “FlsMemInit2”.

# Memory Map REQUIREMENTS

## Mapping

|                               |              |           |
|-------------------------------|--------------|-----------|
| **Memory Section**            | **Contents** | **Notes** |
| **CDD_FlsMem_START_SEC_CODE** |              |           |
|                               |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*The current implementation of the Flash Config Blocks in the
configurator accepts values for all the parameters. Future
implementation shall be targeted with parameters being able to also
accept linker symbols*

{% endraw %}