---
layout: default
title: CM800A_SyncCrc_Integration_Manual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**CM800A SyncCrc**

**VERSION: 2.0**

**DATE: 11-Jan-2016**

**Prepared By:**

**Kevin Smith**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                                     |            |             |           |                 |
|----|---------------|---------------|-------|----------------|----------------|
| **Sl. No.** | **Description**                                                                     | **Author** | **Version** | **Date**  | **Approved By** |
| 1           | Initial version                                                                     | K. Smith   | 1.0         | 05-Oct-15 | \-              |
| 2           | Added exclusive area details and updates for version 1.0.0 of the component design. | K. Smith   | 2.0         | 11-Jan-16 | \-              |

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
7](#__RefHeading___Toc437335986)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[4.6 Exclusive Area Changes 7](#exclusive-area-changes)

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

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | MDD Guidelines              | Process 04.02.00               |
| 2           | Software Naming Conventions | Process 04.02.00               |
| 3           | Coding standards            | Process 04.02.00               |
| 4           | CM800A_SyncCrc_Design       | See Synergy subproject version |

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

SyncCrcInit0\*

Calc16BitCrc_u16_Oper

Calc16BitCrc_u08_Oper

Calc32BitCrc_u16_Oper

Calc32BitCrc_u32_Oper

Calc32BitCrc_u08_Oper

Calc8BitCrc0X2F_Oper

Calc8BitCrc_Oper

ResvCrcHwUnit_Oper\*

The following functions are available if the Autosar Wrapper is enabled

Crc_CalculateCRC8

Crc_CalculateCRC8H2F

Crc_CalculateCRC16

Crc_CalculateCRC32

\*All functions except marked must be called from within a task.

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

1.  CDD_SyncCrc_Cfg_private.h

## Da Vinci Parameter Configuration Changes

|                                                                           |                                                                                                                                                                                                                                                                                                                                                                          |         |
|----------------------|---------------------------------------|------------|
| **Parameter**                                                             | **Notes**                                                                                                                                                                                                                                                                                                                                                                | **SWC** |
| /Nexteer/EcucDefs_SyncCrc/SyncCrc/SyncCrcCommon/AutosarWrapperEnable      | Enables the AUTOSAR API Wrapper functions. This should only be enabled if the Crc BSW is not to be used in a project                                                                                                                                                                                                                                                     | SyncCrc |
| /Nexteer/EcucDefs_SyncCrc/SyncCrc/SyncCrcCommon/AvailableCRCHardwareUnits | Defines the number of CRC hardware units the application can use. Four (4) shall be used as a default value unless there is a specific need to reserve one or more units for other software components. For example, if this was set to 3, the indexes 0-2 would be available to components and index 3 would be reserved. This feature is disabled and hard coded to 4. | SyncCrc |
| /Nexteer/EcucDefs_SyncCrc/SyncCrc/SyncCrcCommon/CrcOsApplicationReference | Value shall be the application in which the SyncCrc is integrated. Due to the nature of CRC usage, an ASIL D application should be selected unless the program is directed otherwise.                                                                                                                                                                                    | SyncCrc |

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

## Exclusive Area Changes

|                          |                                                                                                                                                                                                                                                                                                                                   |         |
|-----------------------------|----------------------------------|----------|
| **Name**                 | **Notes**                                                                                                                                                                                                                                                                                                                         | **SWC** |
| **SyncCrcExclusiveArea** | The exclusive area defined in this component is used by all API functions. The area is used to prevent interruption when searching for an available CRC hardware unit. Presently MtrCtrl function design should not be performing CRC calculations. As a result, the area shall be configured to block all OS related interrupts. | SyncCrc |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                      |                                                                                 |              |
|-------------------|---------------------------------------|---------------|
| **Init**             | **Scheduling Requirements**                                                     | **Trigger**  |
| **CDD_SyncCrcInit1** |                                                                                 | RTE Init     |
| **CDD_SyncCrcInit0** | Shall be scheduled outside of the RTE before any components use the SyncCrc API | Non-RTE Init |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
| **None**     | None                        | N/A         |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |

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

*\<This section is for appendix\>*

{% endraw %}