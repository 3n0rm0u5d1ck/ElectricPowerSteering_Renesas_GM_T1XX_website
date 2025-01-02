---
layout: default
title: Adc0CfgAndUse_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**ForAdc0 Configuration and use**

**VERSION:** **3.0**

**DATE:** **09-Jun-2016**

**Prepared By:**

**Avinash James**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                              |               |             |             |
|------|---------------------------------|------------|---------|-------------|
| **Sl. No.** | **Description**              | **Author**    | **Version** | **Date**    |
| 1           | Initial Version              | Selva         | 1.0         | 4- May-2015 |
| 2           | Updated per design rev 2.0.0 | Rijvi         | 2.0         | 5-Feb-2016  |
| 3           | Updated to design rev 2.1.0  | Avinash James | 3.0         | 09-Jun-2016 |
|             |                              |               |             |             |
|             |                              |               |             |             |

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

[7.1.1.1 INIT: ADC0CFGANDUSEInit1 11](#init-adc0cfganduseinit1)

[7.1.1.2 Design Rationale 11](#design-rationale)

[7.1.1.3 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.1.1.4 (Processing of function)……… 11](#processing-of-function)

[7.1.1.5 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.1.2 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.1.2.1 INIT: Adc0CfgAndUsePer1 11](#__RefHeading___Toc453240016)

[7.1.2.2 Design Rationale 11](#__RefHeading___Toc453240017)

[7.1.2.3 Store Module Inputs to Local copies
11](#__RefHeading___Toc453240018)

[7.1.2.4 (Processing of function)……… 11](#__RefHeading___Toc453240019)

[7.2 Interrupt Functions 11](#interrupt-functions)

[7.3 Server RUNNABLE Functions 12](#server-runnable-functions)

[7.3.1.1 Design Rationale 12](#design-rationale-2)

[7.3.1.2 (Processing of function)……… 12](#processing-of-function-2)

[7.4 Local Function/Macro Definitions 12](#__RefHeading___Toc453240024)

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
| 1       | MDD Guidelines              | Process 4.2.1                   |
| 2       | Software Naming Conventions | Process 4.2.1                   |
| 3       | Coding standards            | Process 4.2.1                   |
| 4       | FDD – CM300A Adc0CfgAndUse  | See synergy sub project version |
|         | \<Add if more available\>   |                                 |

# High-Level Description

None

# Design details of software module

## Graphical representation 

##  [section]

## <img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM300A_Adc0CfgAndUse_Impl/doc/mediax/media/image2.png"
style="width:2.03333in;height:1.16667in" /> [section-1]

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

## INIT: ADC0CFGANDUSEInit1

Refer the FDD

## Design Rationale

## Store Module Inputs to Local copies

None

##  (Processing of function)………

None

## Store Local copy of outputs into Module Outputs

None

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “ Periodic Functions” and follow the same
sub-section design shown below). If none required, place the text
“None”)\>*

> None

## INIT: Adc0CfgAndUsePer1

Refer the FDD

## Design Rationale

## Store Module Inputs to Local copies

Refer FDD

##  (Processing of function)………

Called every other motor control ISR loop

## Interrupt Functions

> None

## Server RUNNABLE Functions

None

###  

## Design Rationale

##  (Processing of function)………

1.  <span id="__RefHeading___Toc453240024" class="anchor"></span>Local
    Function/Macro Definitions

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

> None

# UNIT TEST CONSIDERATION

*None*

# Appendix

*None*

{% endraw %}