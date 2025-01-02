---
layout: default
title: WdgM Integration Manual
nav_order: 5
parent: Watchdog Manager
---
{% raw %}
**Integration Manual**

**For**

**WdgM**

**VERSION: 1**

**DATE: 01/15/16**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                |             |          |
|-------------|-----------------|----------------|-------------|----------|
| **Sl. No.** | **Description** | **Author**     | **Version** | **Date** |
| 1           | Initial version | Lucas Wendling | 1.0         | 01/15/16 |

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

[7.3 Non RTE NvM Blocks 10](#nvm-blocks)

[7.4 RTE NvM Blocks 10](#__RefHeading___Toc389222336)

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

API usage and scheduling of BSW components expected to be captured at a
project architectural level and is beyond the scope of this document.
Third party documentation can be referenced as needed.

**NxtrWdgM_Init**

NxtrWdgM_Init is a trusted function interface for WdgM_Init. This is
currently needed because an include order issue prevents the Os from
visibility to the configuration structure passed into WdgM_Init, so the
trusted function cannot be directly called. This function is only needed
in a project if the WdgM_Init function is called from a non-trusted
application task context (which is the typical scenario).

If this function is needed (based on if WdgM_Init needs to be called
from a non-trusted task context), the following needs to be done for
integration:

1.  Include NxtrWdgM.gpj as a subrproject in the integration project gpj
    file.

2.  Configure the Os with a trusted function call named “NxtrWdgM_Init”.
    This has a void return with no passed parameters (void).

3.  In the startup sequence when WdgM_Init would need to be called, the
    trusted function needs to be called “Call_NxtrWdgM_Init”

If this function is not needed (if WdgM_Init already is called from a
trusted task context), the integrator can exclude NxtrWdgM.gpj from the
integration project gpj file and WdgM_Init API can be directly called.

# Configuration REQUIREMeNTS

Configuration of BSW components expected to be captured at a project
architectural level and is beyond the scope of this document. Third
party documentation can be referenced as needed.

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
|             |           |     |

## Configuration Files to be provided by Integration Project

N/A

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
|               |           |         |

## DaVinci Interrupt Configuration Changes

|              |           |
|--------------|-----------|
| **ISR Name** | **Notes** |
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

|                   |                                                             |             |
|-------------------|---------------------------------------|---------------|
| **Init**          | **Scheduling Requirements**                                 | **Trigger** |
| **NxtrWdgM_Init** | See section 3.2 for details on if this function is required |             |

|              |                             |             |
|--------------|-----------------------------|-------------|
| **Runnable** | **Scheduling Requirements** | **Trigger** |
|              |                             |             |

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

*\<This section is for appendix\>*

{% endraw %}