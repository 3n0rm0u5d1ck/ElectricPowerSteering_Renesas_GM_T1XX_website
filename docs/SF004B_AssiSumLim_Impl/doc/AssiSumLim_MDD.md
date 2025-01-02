---
layout: default
title: AssiSumLim_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘AssiSumLim’**

**VERSION: 1.0**

**DATE: 03-June-2015**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                        |             |              |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description** | **Author**             | **Version** | **Date**     |
| 1           | Initial Version | Sankardu Varadapureddi | 1.0         | 03-June-2015 |
|             |                 |                        |             |              |
|             |                 |                        |             |              |
|             |                 |                        |             |              |
|             |                 |                        |             |              |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[5](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [6](#references)](#references)

[3 AssiSumLim High-Level Description
[7](#assisumlim-high-level-description)](#assisumlim-high-level-description)

[4 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation of AssiSumLim
[8](#graphical-representation-of-assisumlim)](#graphical-representation-of-assisumlim)

[4.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[4.2.1 Module level DFD [8](#module-level-dfd)](#module-level-dfd)

[4.2.2 Sub-Module level DFD
[9](#sub-module-level-dfd)](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM
[9](#component-flow-diagram)](#component-flow-diagram)

[5 Variable Data Dictionary
[10](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[10](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[10](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary
[11](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[11](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants
[11](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [11](#local)](#local)

[6.1.1.2 Global [11](#global)](#global)

[6.1.2 Module specific Lookup Tables Constants
[11](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[7 Software Module Implementation
[12](#software-module-implementation)](#software-module-implementation)

[7.1 Sub-Module Functions
[12](#sub-module-functions)](#sub-module-functions)

[7.1.1 Initialization Functions
[12](#initialization-functions)](#initialization-functions)

[7.1.1.1 INIT: AssiSumLimInit1
[12](#init-assisumliminit1)](#init-assisumliminit1)

[7.1.1.1.1 Design Rationale [12](#design-rationale)](#design-rationale)

[7.1.1.1.2 Module Outputs [12](#module-outputs)](#module-outputs)

[7.1.1.1.3 Module Internal [12](#module-internal)](#module-internal)

[7.1.2 PERIODIC FUNCTIONS
[12](#periodic-functions)](#periodic-functions)

[7.1.2.1 Per: AssiSumLimPer1
[12](#per-assisumlimper1)](#per-assisumlimper1)

[7.1.2.1.1 Design Rationale
[12](#design-rationale-1)](#design-rationale-1)

[7.1.2.1.2 Store Module Inputs to Local copies
[12](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[7.1.2.1.3 (Processing of function)………
[12](#processing-of-function)](#processing-of-function)

[7.1.2.1.4 Store Local copy of outputs into Module Outputs
[12](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[7.1.3 Interrupt Functions
[12](#interrupt-functions)](#interrupt-functions)

[7.1.4 Server runnables [13](#server-runnables)](#server-runnables)

[7.1.4.1 SetManTqCmd [13](#setmantqcmd)](#setmantqcmd)

[7.1.4.1.1 Design Rationale
[13](#design-rationale-2)](#design-rationale-2)

[7.1.4.1.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[7.1.4.1.3 (Processing of function)………
[13](#processing-of-function-1)](#processing-of-function-1)

[7.1.4.1.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[7.1.5 Local Function/Macro Definitions
[13](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.1.5.1 Local Function \#1 [13](#_Toc421537785)](#_Toc421537785)

[7.1.5.1.1 Description [13](#_Toc421537786)](#_Toc421537786)

[7.1.5.2 Local Function \#2 [13](#_Toc421537787)](#_Toc421537787)

[7.1.5.2.1 Description [13](#_Toc421537788)](#_Toc421537788)

[7.1.6 GLObAL Function/Macro Definitions
[13](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[7.1.7 Tranisition FUNCTIONS
[13](#tranisition-functions)](#tranisition-functions)

[8 Known Limitations With Design
[14](#known-limitations-with-design)](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION
[15](#unit-test-consideration)](#unit-test-consideration)

[10 Appendix [16](#appendix)](#appendix)

# Abbrevations And Acronyms

| Abbreviation | Description                |
|--------------|----------------------------|
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| Sr. No. | Title                                | Version                         |
|----------|----------------------------------------------|-----------------|
| 1       | MDD Guidelines                       | Process 3.06.00                 |
| 2       | Software Naming Conventions          | Process 3.06.00                 |
| 3       | Software Design and Coding standards | Process 3.06.00                 |
| 4       | FDD - SF004B_AssiSumLim_Design       | See Synergy sub project version |
|         |                                      |                                 |

# AssiSumLim High-Level Description

# Design details of software module

## Graphical representation of AssiSumLim

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF004B_AssiSumLim_Impl/doc/mediax/media/image1.png"
style="width:2.7in;height:6.85833in" />

## Data Flow Diagram

*Refer FDD*

## Module level DFD

*Refer FDD*

## Sub-Module level DFD

*Refer FDD*

## COMPONENT FLOW DIAGRAM

*Refer FDD*

# Variable Data Dictionary

## User defined typedef definition/declaration 

*\<This section documents any user types uniquely used for the
module.\>*

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
| None      |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local 

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
|               |            |       |       |

**Note**: Refer .m file for constants definitions.

## Global

| Constant Name |
|---------------|
| None          |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*AssiSumLimInit1*

## INIT: AssiSumLimInit1

## Design Rationale

*Design follows implemenetation in FDD.*

## Module Outputs

*Refer ‘AssiSumLimInit1’ block in FDD*

## Module Internal 

None

## PERIODIC FUNCTIONS 

## Per: AssiSumLimPer1

## Design Rationale

*Design follows implementation in FDD.*

## Store Module Inputs to Local copies

*Refer to FDD*

##  (Processing of function)………

*Refer to FDD (Block ‘AssiSumLmtPer1’)*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

##  Server runnables

##  SetManTqCmd

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer ‘SetManTqCmd’ block in FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

## Tranisition FUNCTIONS 

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

None

# Appendix

*None*

{% endraw %}