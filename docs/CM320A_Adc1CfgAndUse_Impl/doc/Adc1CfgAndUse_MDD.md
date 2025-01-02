---
layout: default
title: Adc1CfgAndUse_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**ForAdc1 Configuration and use**

**VERSION:** **3.0**

**DATE: 09-Jun-2016**

**Prepared By:**

**Avinash James**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                              |               |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**                              | **Author**    | **Version** | **Date**    |
| 1           | Initial Version                              | Selva         | 1.0         | 4- May-2015 |
| 2           | Updated per design rev 2.0.0                 | Rijvi         | 2.0         | 9-Feb-2016  |
| 3           | Added Periodic 2 and removed server runnable | Avinash James | 3.0         | 9-Jun-2016  |
|             |                                              |               |             |             |
|             |                                              |               |             |             |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 High-Level Description 7](#high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation 8](#graphical-representation)

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

[7.1.1 Initialization Functions 11](#initialization-functions)

[7.1.1.1 INIT: Adc1CfgAndUseINIT1 11](#init-adc1cfganduseinit1)

[7.1.1.2 Design Rationale 11](#design-rationale)

[7.1.2 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.1.2.1 Per: Adc1CfgAndUsePer1 11](#per-adc1cfganduseper1)

[7.1.2.2 Design Rationale 11](#design-rationale-1)

[7.1.2.3 Per: Adc1CfgAndUsePer2 11](#__RefHeading___Toc453258777)

[7.1.2.4 Design Rationale 11](#__RefHeading___Toc453258778)

[7.2 Interrupt Functions 11](#interrupt-functions)

[7.3 Server RUNNABLE Functions 12](#server-runnable-functions)

[7.3.1.1 Per: Adc1CfgAndUseAdc1EnaCnvn_Oper
12](#per-adc1cfganduseadc1enacnvn_oper)

[7.3.1.2 Design Rationale 12](#design-rationale-3)

[7.4 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[7.5 GLObAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[7.5.1 GLObAL Function \#1 12](#global-function-1)

[7.5.1.1 Description 12](#description)

[7.6 TRANSIENT FUNCTIONS 12](#transient-functions)

[8 Known Limitations With Design 13](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[10 Appendix 15](#appendix)

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

|         |                             |                                 |
|---------|-----------------------------|---------------------------------|
| Sr. No. | Title                       | Version                         |
| 1       | MDD Guidelines              | Process 04.02.01                |
| 2       | Software Naming Conventions | Process 04.02.01                |
| 3       | Coding standards            | Process 04.02.01                |
| 4       | FDD – CM320A Adc1CfgAndUse  | See synergy sub project version |
|         | \<Add if more available\>   |                                 |

# High-Level Description

None

# Design details of software module

## Graphical representation 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM320A_Adc1CfgAndUse_Impl/doc/mediax/media/image2.png"
style="width:2.70833in;height:1.6in" />

## Data Flow Diagram

## Module level DFD

*N/A*

## Sub-Module level DFD

*N/A*

## COMPONENT FLOW DIAGRAM

*N/A*

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

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
| N/A       |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                             |            |       |       |
|-----------------------------|------------|-------|-------|
| Constant Name               | Resolution | Units | Value |
| Refer . mfile in the design |            |       |       |
|                             |            |       |       |
|                             |            |       |       |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                             |
|-----------------------------|
| Constant Name               |
| Refer . mfile in the design |
|                             |
|                             |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                            |                                |                                |                                |
|------------------------------|----------------|--------------|--------------|
| Constant Name                              | Resolution                     | Value                          | Software Segment               |
| \<Refer Constant name qualified in \[2\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## INIT: Adc1CfgAndUseINIT1

## Design Rationale

Refer the FDD

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: Adc1CfgAndUsePer1

## Design Rationale

> Refer the FDD

## Per: Adc1CfgAndUsePer2

## Design Rationale

> Refer the FDD

## Interrupt Functions

> None

## Server RUNNABLE Functions

## Per: Adc1CfgAndUseAdc1EnaCnvn_Oper

## Design Rationale

> Refer the FDD

## 

## 

## 

## Local Function/Macro Definitions

None

## 

## GLObAL Function/Macro Definitions

## GLObAL Function \#1

|                      |                   |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used) | Type                          | Min                           | Max                           |
| **Arguments Passed** | None              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |                   |                               |                               |                               |
| **Return Value**     | N/A               |                               |                               |                               |

## Description

N/A

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

1.  None

# UNIT TEST CONSIDERATION

*None*

# Appendix

*None*

{% endraw %}