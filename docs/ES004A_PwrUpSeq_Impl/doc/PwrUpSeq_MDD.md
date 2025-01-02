---
layout: default
title: PwrUpSeq_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Power Up Sequence**

**VERSION:** **4.0**

**DATE:** **04-JAN-2017**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                           |                        |             |              |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**           | **Author**             | **Version** | **Date**     |
| 1           | Initial Version           | Rijvi Ahmed            | 1.0         | 11-Apr-2015  |
| 2           | Updated for FDD ver 1.2.0 | Sankardu Varadapureddi | 2.0         | 13-Jan-2016  |
| 3           | Updated for FDD ver 1.4.0 | Rijvi Ahmed            | 3.0         | 15-July-2016 |
| 4           | Updated for FDD ver 1.5.0 | Avinash James          | 4.0         | 04-Jan-2017  |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MDD pwrupseq & High-Level Description
7](#mdd-pwrupseq-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of pwrupseq
8](#graphical-representation-of-pwrupseq)

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

[7.2.1 PwrUpSeqInit1 11](#pwrupseqinit1)

[7.2.1.1 Design Rationale 11](#design-rationale)

[7.2.1.2 Module Outputs 11](#module-outputs)

[7.3 PERIODIC FUNCTIONS 11](#__RefHeading___Toc471305925)

[7.3.1 Per: PwrUpSeqPer1 11](#__RefHeading___Toc471305926)

[7.3.1.1 Design Rationale 11](#design-rationale-1)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.4 Server Runables 11](#__RefHeading___Toc471305931)

[7.4.1 PwrTurnOffCtrl_Oper 11](#__RefHeading___Toc471305932)

[7.4.1.1 Design Rationale 11](#__RefHeading___Toc471305933)

[7.4.1.2 (Processing of function)……… 11](#__RefHeading___Toc471305934)

[7.5 Interrupt Functions 12](#interrupt-functions)

[7.6 Serial Communication Functions 13](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
13](#local-functionmacro-definitions)

[7.7.1 Local Function \#1 13](#__RefHeading___Toc471305938)

[7.7.1.1 Description 13](#description)

[7.8 GLObAL Function/Macro Definitions
13](#global-functionmacro-definitions)

[7.8.1 GLObAL Function \#1 13](#__RefHeading___Toc471305941)

[7.8.1.1 Description 13](#description-1)

[7.9 TRANSIENT FUNCTIONS 13](#transient-functions)

[8 Known Limitations With Design 14](#known-limitations-with-design)

[9 UNIT TEST CONSIDERATION 15](#unit-test-consideration)

[1 Appendix 16](#appendix)

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
| 3       | Software Coding Standards   | Process 04.02.01                |
| 4       | FDD – ES004A PwrUpSeq       | See synergy sub project version |

# MDD pwrupseq & High-Level Description

> None

# Design details of software module

## Graphical representation of pwrupseq

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES004A_PwrUpSeq_Impl/doc/mediax/media/image1.png"
style="width:3.99167in;height:2.9in" />

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

<table style="width:100%;">
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
</tbody>
</table>

## Variable definition for enumerated types

|           |              |       |
|-----------|--------------|-------|
| Enum Name | Element Name | Value |
|           |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|                 |            |       |       |
|-----------------|------------|-------|-------|
| Constant Name   | Resolution | Units | Value |
| PINSTHI_CNT_U08 | 1          | CNT   | 1U    |
| Refer .m file   |            |       |       |

## Global

|               |
|---------------|
| Constant Name |
|               |

## Module specific Lookup Tables Constants

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| N/A           |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*None*

## Initialization Functions

## PwrUpSeqInit1

## Design Rationale

*Refer FDD*

## Module Outputs

None

## PERIODIC FUNCTIONS 

1.  <span id="__RefHeading___Toc471305926" class="anchor"></span>Per:
    PwrUpSeqPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## 

## 

## Server Runables 

## PwrTurnOffCtrl_Oper

## Design Rationale

*None*

##  (Processing of function)………

*Refer to FDD*

## 

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

1.  <span id="__RefHeading___Toc471305938" class="anchor"></span>Local
    Function \#1

|                      |      |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | None | Type                          | Min                           | Max                           |
| **Arguments Passed** | None | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |      |                               |                               |                               |
| **Return Value**     | None |                               |                               |                               |

## Description

N/A

## GLObAL Function/Macro Definitions

1.  <span id="__RefHeading___Toc471305941" class="anchor"></span>GLObAL
    Function \#1

|                      |      |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | None | Type                          | Min                           | Max                           |
| **Arguments Passed** | None | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      |      |                               |                               |                               |
| **Return Value**     | None |                               |                               |                               |

## Description

N/A

## TRANSIENT FUNCTIONS 

*None*

# Known Limitations With Design

# UNIT TEST CONSIDERATION

> Roll over of the PIM Rte_Pim_PwrTurnOffCtrlPrev() is intentional

# Appendix

*None*

{% endraw %}