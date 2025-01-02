---
layout: default
title: SysStMod_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**System States and Modes**

**VERSION:** **2**

**DATE:** **05-Apr-2016**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                           |                        |             |
|--------|---------------------------------------|---------------|-----------|
| **Version** | **Description**           | **Author**             | **Date**    |
| 1           | Initial version           | Owen Tosh              | 25-Mar-2015 |
| 2           | Updated for FDD ver 1.3.0 | Sankardu Varadapureddi | 05-Apr-2016 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 SysStMod & High-Level Description
6](#sysstmod-high-level-description)

[4 Design details of software module
7](#design-details-of-software-module)

[4.1 Graphical representation of SysStMod
7](#graphical-representation-of-sysstmod)

[5 Variable Data Dictionary 8](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
8](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
8](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 9](#constant-data-dictionary)

[6.1 Program(fixed) Constants 9](#programfixed-constants)

[6.1.1 Embedded Constants 9](#embedded-constants)

[6.1.1.1 Local 9](#local)

[6.1.1.2 Global 9](#global)

[6.1.2 Module specific Lookup Tables Constants
10](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 11](#software-module-implementation)

[7.1 Sub-Module Functions 11](#sub-module-functions)

[7.2 Initialization Functions 11](#initialization-functions)

[7.2.1 Init: SysStMd_Init1 11](#init-sysstmodinit1)

[7.2.1.1 Design Rationale 11](#design-rationale)

[7.2.1.2 Module Internal 11](#module-internal)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: SysStMd_Per1 11](#per-sysstmdper1)

[7.3.1.1 Design Rationale 11](#design-rationale-1)

[7.3.1.2 Processing of Function 11](#processing-of-function)

[7.4 Interrupt Functions 11](#interrupt-functions)

[7.5 Serial Communication Functions 11](#serial-communication-functions)

[7.6 Local Function/Macro Definitions
11](#local-functionmacro-definitions)

[7.7 GLObAL Function/Macro Definitions
11](#global-functionmacro-definitions)

[8 Known Limitations With Design 12](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 13](#unit-test-consideration)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                             |                  |
|---------|-----------------------------|------------------|
| Sr. No. | Title                       | Version          |
| 1       | MDD Guidelines              | Process 03.05.00 |
| 2       | Software Naming Conventions | Process 03.05.00 |
| 3       | Software Coding Standards   | Process 03.05.00 |

# SysStMod & High-Level Description

This module manages the overall system state based on ignition, startup
test completion, and fault status. It arbitrates between the various
demands on the system state and manages the transition decisions with a
lookup table, dependent on the current state.

# Design details of software module

## Graphical representation of SysStMod

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES100A_SysStMod_Impl/doc/mediax/media/image2.png"
style="width:2.75833in;height:1.53333in" />

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                              |            |       |       |
|------------------------------|------------|-------|-------|
| Constant Name                | Resolution | Units | Value |
| SYSSTREQENBIT_CNT_U16        | 1          | Count | 0x04  |
| PWRSPLYENREQBIT_CNT_U16      | 1          | Count | 0x10  |
| SYSSTFLTOUTPREQDIBIT_CNT_U16 | 1          | Count | 0x08  |
| SYSSTREQDIBIT_CNT_U16        | 1          | Count | 0x02  |
| SYSSTWRMININCMPLBIT_CNT_U16  | 1          | Count | 0x01  |

## Global

|               |
|---------------|
| Constant Name |
| None          |

##  Module specific Lookup Tables Constants

|                               |            |       |                  |
|-------------------------------|------------|-------|------------------|
| Constant Name                 | Resolution | Value | Software Segment |
| See design M file for details |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## Init: SysStModInit1

## Design Rationale

None

## Module Internal

See design model for details.

## PERIODIC FUNCTIONS 

## Per: SysStMdPer1

## Design Rationale

The logic around building the transition vector does not match the
design model exactly for efficiency and coding standard reasons. They
are identical functionally, however.

## Processing of Function

See design model for details.

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

None

{% endraw %}