---
layout: default
title: PwrDiscnct_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘PwrDiscnct’**

**VERSION: 1.0**

**DATE: 09-Apr-2015**

**Prepared By:**

**Sankardu Varadapureddi,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                 |                        |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description** | **Author**             | **Version** | **Date**    |
| 1           | Initial Version | Sankardu Varadapureddi | 1.0         | 09-Apr-2015 |
|             |                 |                        |             |             |
|             |                 |                        |             |             |
|             |                 |                        |             |             |
|             |                 |                        |             |             |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[4](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [5](#references)](#references)

[3 Power Disconnect High-Level Description
[6](#power-disconnect-high-level-description)](#power-disconnect-high-level-description)

[4 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation of POWER DISCONNECT
[7](#graphical-representation-of-power-disconnect)](#graphical-representation-of-power-disconnect)

[4.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[4.2.1 Module level DFD [7](#module-level-dfd)](#module-level-dfd)

[4.2.2 Sub-Module level DFD
[7](#sub-module-level-dfd)](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM
[7](#component-flow-diagram)](#component-flow-diagram)

[5 Variable Data Dictionary
[8](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[8](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[8](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[9](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [9](#local)](#local)

[6.1.1.2 Global [9](#global)](#global)

[6.1.2 Module specific Lookup Tables Constants
[9](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[7 Software Module Implementation
[10](#software-module-implementation)](#software-module-implementation)

[7.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[7.1.1 Initialization Functions
[10](#initialization-functions)](#initialization-functions)

[7.1.2 PERIODIC FUNCTIONS
[10](#periodic-functions)](#periodic-functions)

[7.1.2.1 Per: PwrDiscnct_Per1
[10](#per-pwrdiscnctper1)](#per-pwrdiscnctper1)

[7.1.2.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[7.1.2.1.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[7.1.2.1.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[7.1.2.1.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[7.1.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[7.1.4 Serial Communication Functions
[11](#serial-communication-functions)](#serial-communication-functions)

[7.1.5 Local Function/Macro Definitions
[11](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.1.6 GLObAL Function/Macro Definitions
[11](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[7.1.7 Tranisition FUNCTIONS
[11](#tranisition-functions)](#tranisition-functions)

[8 Known Limitations With Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[10 Appendix [14](#appendix)](#appendix)

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
| 4       | FDD - ES003A_PwrDiscnct_Design       | See Synergy sub project version |
|         |                                      |                                 |

# Power Disconnect High-Level Description

*This function will verify that the PowerDisconnect is not stuck closed
at init once per Ignition Cycle.*

# Design details of software module

## Graphical representation of POWER DISCONNECT

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES003A_PwrDiscnct_Impl/doc/mediax/media/image1.png"
style="width:2.55833in;height:3.84167in" />

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
| None          |            |       |       |

## Global

| Constant Name |
|---------------|
|               |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          |            |       |                  |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## Per: PwrDiscnctPer1

## Design Rationale

*Design follows implemenetation in FDD.*

## Store Module Inputs to Local copies

*Refer to FDD*

##  (Processing of function)………

*Refer to FDD (Block ‘PwrDiscnct’)*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Interrupt Functions

*None*

##  Serial Communication Functions

None

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

## Tranisition FUNCTIONS 

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

# Appendix

*None*

{% endraw %}