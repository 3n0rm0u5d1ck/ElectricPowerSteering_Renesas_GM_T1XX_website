---
layout: default
title: XcpIf Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**XCP Interface (XcpIf)**

**VERSION: 2.0**

**DATE: 09-Oct-2015**

**Prepared By:**

**Kevin Smith**

**ESG Software,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                               |            |             |          |                 |
|--------|-----------------------------|---------|---------|---------|----------|
| **Sl. No.** | **Description**                               | **Author** | **Version** | **Date** | **Approved By** |
| 1           | Initial version                               | K. Smith   | 1.0         | 6-Jun-15 |                 |
| 2           | Updates for intial online calibration support | K. Smith   | 2.0         | 9-Oct-15 |                 |

: ARM Cortex R4 Memory Usage

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

[4.6 OS Configuration Changes
[7](#os-configuration-changes)](#os-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
[8](#integration-dataflow-requirements)](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs
[8](#required-global-data-inputs)](#required-global-data-inputs)

[5.2 Required Global Data Outputs
[8](#required-global-data-outputs)](#required-global-data-outputs)

[5.3 Specific Include Path present
[8](#specific-include-path-present)](#specific-include-path-present)

[5.4 Other Header Changes
[8](#other-header-changes)](#other-header-changes)

[6 Runnable Scheduling [9](#runnable-scheduling)](#runnable-scheduling)

[7 Memory Map REQUIREMENTS
[10](#memory-map-requirements)](#memory-map-requirements)

[7.1 Mapping [10](#mapping)](#mapping)

[7.2 Usage [10](#usage)](#usage)

[7.3 NvM Blocks [10](#nvm-blocks)](#nvm-blocks)

[8 Compiler Settings [11](#compiler-settings)](#compiler-settings)

[8.1 Preprocessor MACRO [11](#preprocessor-macro)](#preprocessor-macro)

[8.2 Optimization Settings
[11](#optimization-settings)](#optimization-settings)

[9 Appendix [12](#appendix)](#appendix)

# Abbrevations And Acronyms

| **Abbreviation** | **Description**           |
|------------------|---------------------------|
| DFD              | Design functional diagram |
| MDD              | Module design Document    |
|                  |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                   | **Version**      |
|-------------|-----------------------------|------------------|
| 1           | MDD Guidelines              | Process 04.02.00 |
| 2           | Software Naming Conventions | Process 04.02.00 |
| 3           | Coding standards            | Process 04.02.00 |
| 4           | FDD                         | Not available    |
|             | \<Add if more available\>   |                  |

# Dependencies

## SWCs

| **Module** | **Required Feature** |
|------------|----------------------|
| **None**   |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

| **Modules** | **Notes** |     |
|-------------|-----------|-----|
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

## Da Vinci Parameter Configuration Changes

| **Parameter** | **Notes** | **SWC** |
|---------------|-----------|---------|
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **None**     |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **None**     |           |         |

## OS Configuration Changes

<table>
<colgroup>
<col style="width: 39%" />
<col style="width: 34%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Trusted Function</strong></th>
<th><strong>Parameters</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ApplXcpWrCmn</strong></td>
<td><p>MTABYTEPTR addr</p>
<p>vuint8 size</p>
<p>const BYTEPTR data</p></td>
<td>This function should be defined as trusted.</td>
</tr>
<tr class="even">
<td><strong>Rte_Call_SetCalPageReq_Oper</strong></td>
<td></td>
<td>This function shall be defined as a non-trusted function call to the
application that TunSelnMngt is integrated.</td>
</tr>
<tr class="odd">
<td><strong>Rte_Call_CopyCalPageReq_Oper</strong></td>
<td></td>
<td>This function shall be defined as a non-trusted function call to the
application that TunSelnMngt is integrated.</td>
</tr>
</tbody>
</table>

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes

## Other Header Changes

| **File**       | **Change**                            | **Reason**                                                                                                               |
|-------------|-----------------------------|-------------------------------|
| **usrostyp.h** | Add include statement for CDD_XcpIf.h | The include is needed since for the OS has the function prototypes and datatypes required for the trusted function call. |

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**          | **Scheduling Requirements** | **Trigger** |
|-------------------|-----------------------------|-------------|
| **CDD_XcpIfInit** | None                        | Rte         |

| **Runnable**  | **Scheduling Requirements** | **Trigger** |
|---------------|-----------------------------|-------------|
| **Xcp2msDaq** | 2ms                         | RTE         |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section** | **Contents** | **Notes** |
|--------------------|--------------|-----------|
| **None**           |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

The file xcp.cfg needs to have “#define
XCP_ENABLE_CALIBRATION_MEM_ACCESS_BY_APPL” added. When the XCP component
is generated in GENy, this will enable the application read/write calls.

The \#defile XCPIF_MAXCALSEG_CNT_U08 points to a generated value by the
Xcp component. Vector currently only allows one segment to be defined.
This will have to be manually changed in the xcp.cfg file by the
following:

\#undef kXcpMaxSegment

\#define kXcpMaxSegment XX

*XX is the number of tuning groups that are defined in your program.*

## Optimization Settings

None

# Appendix

*N/A*

{% endraw %}