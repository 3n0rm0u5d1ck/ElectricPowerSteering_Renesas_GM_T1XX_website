---
layout: default
title: MotCurrRegCfg_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotCurrRegCfg**

**VERSION: 4.0**

**DATE: 11-Nov-2016**

**Prepared By:**

**Software Group**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                               |            |             |             |
|------|------------------------------------|-----------|---------|------------|
| **Sl. No.** | **Description**               | **Author** | **Version** | **Date**    |
| 1           | Initial Version               | Selva      | 1.0         | 02-JUN-2015 |
| 2           | Updated per design rev. 1.3.0 | Rijvi      | 2.0         | 12-Mar-2016 |
| 3           | Updated per design rev. 1.4.0 | Krishna    | 3.0         | 29-Apr-2016 |
| 4           | Updated per design rev. 2.1.0 | JK         | 4.0         | 11-Nov-2016 |
|             |                               |            |             |             |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MotCurrRegCfg & High-Level Description
7](#motcurrregcfg-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of MotCurrRegCfg
8](#graphical-representation-of-motcurrregcfg)

[4.2 Data Flow Diagram 8](#data-flow-diagram)

[4.2.1 Module level DFD 8](#module-level-dfd)

[4.2.2 Sub-Module level DFD 8](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 8](#component-flow-diagram)

[5 Variable Data Dictionary 9](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
9](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
9](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 10](#constant-data-dictionary)

[6.1 Program(fixed) Constants 10](#programfixed-constants)

[6.1.1 Embedded Constants 10](#embedded-constants)

[6.1.1.1 Local 10](#local)

[6.1.1.2 Global 10](#global)

[6.1.2 Module specific Lookup Tables Constants
10](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 11](#software-module-implementation)

[7.1 Sub-Module Functions 11](#sub-module-functions)

[7.2 Initialization Functions 11](#initialization-functions)

[7.2.1 Per: MotCurrRegCfgINIT1 11](#per-motcurrregcfginit1)

[7.2.1.1 Design Rationale 11](#design-rationale)

[7.2.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.2.1.3 (Processing of function)……… 11](#processing-of-function)

[7.2.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: MotCurrRegCfgper1 11](#per-motcurrregcfgper1)

[7.3.1.1 Design Rationale 11](#design-rationale-1)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies-1)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function-1)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs-1)

[7.4 Non PERIODIC FUNCTIONS 11](#non-periodic-functions)

[7.5 Interrupt Functions 11](#__RefHeading___Toc467249995)

[7.6 Serial Communication Functions 12](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.8 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.9 TRANSIENT FUNCTIONS 12](#transient-functions)

[8 Unit Test Considerations 13](#unit-test-considerations)

[9 Known Limitations With Design 14](#known-limitations-with-design)

[10 UNIT TEST CONSIDERATION 15](#__RefHeading___Toc467250002)

[11 Appendix 16](#appendix)

# Abbrevations And Acronyms

|              |                                         |
|--------------|-----------------------------------------|
| Abbreviation | Description                             |
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                   |                                |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                             | Version                        |
| \<1\>   | \<MDD Guidelines\>                | Process 04.02.01               |
| \<2\>   | \<Software Naming Conventions\>   | Process 04.02.01               |
| \<3\>   | \<Coding standards\>              | Process 04.02.01               |
| \<4\>   | FDD - SF104A_MotCurrRegCfg_Design | See Synergy Subproject version |
|         | \<Add if more available\>         |                                |

# MotCurrRegCfg & High-Level Description

# Design details of software module

## Graphical representation of MotCurrRegCfg

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF104A_MotCurrRegCfg_Impl/doc/mediax/media/image2.png"
style="width:4.9375in;height:5.97917in" />

## Data Flow Diagram

## Module level DFD

## Sub-Module level DFD

## COMPONENT FLOW DIAGRAM

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
<td>N/A</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |                                          |                       |
|--------------------------------|-----------------------------|------------|
| Enum Name | Element Name                             | Value                 |
| N/A       | \<(Variable name qualified Refer\[2\])\> | \<Define the value \> |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                              |            |       |       |
|------------------------------|------------|-------|-------|
| Constant Name                | Resolution | Units | Value |
| Refer constants from .m file |            |       |       |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                              |
|------------------------------|
| Constant Name                |
| Refer constants from .m file |
|                              |
|                              |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| Refer .m file |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*NONE*

## Initialization Functions

## Per: MotCurrRegCfgINIT1

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## PERIODIC FUNCTIONS 

## Per: MotCurrRegCfgper1

## Design Rationale

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

None

# Unit Test Considerations

None

# Known Limitations With Design

# UNIT TEST CONSIDERATION 

The range of the application data type used for the calibration
MotCurrRegCfgMotClsdLoopBwDaxY and MotCurrRegCfgMotNatFrqQaxY are not
updated per the DataDict.m file changes. We moved away using the
application data type, hence it has no impact.

# Appendix

*None*

{% endraw %}