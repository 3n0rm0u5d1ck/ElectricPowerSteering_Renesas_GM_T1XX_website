---
layout: default
title: MotVel_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘MotVel’**

**VERSION: 2.0**

**DATE: 18-Nov-2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI**

**CHENNAI, INDIA**

**  
** **Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                               |             |             |               |
|-----|-------------------------------|----------------|----------|-----------|
| **Sl. No.** | **Description**               | **Author**  | **Version** | **Date**      |
| 1           | Initial Version               | Rijvi Ahmed | 1.0         | 12-April-2016 |
| 2           | Updated per design rev. 2.0.0 | TATA        | 2.0         | 18-Nov-2016   |
|             |                               |             |             |               |
|             |                               |             |             |               |
|             |                               |             |             |               |

**<u>  
Table of Contents</u>**

1 Abbrevations And Acronyms 5

2 References 6

3 MotVel & High-Level Description 7

4 Design details of software module 8

4.1 Graphical representation OF MotVel 8

4.2 Data Flow Diagram 8

4.2.1 Module level DFD 8

4.2.2 Sub-Module level DFD 8

4.3 COMPONENT FLOW DIAGRAM 8

5 Variable Data Dictionary 9

5.1 User defined typedef definition/declaration 9

5.2 Variable definition for enumerated types 9

6 Constant Data Dictionary 10

6.1 Program(fixed) Constants 10

6.1.1 Embedded Constants 10

6.1.1.1 Local 10

6.1.2 Module specific Lookup Tables Constants 10

7 Software Module Implementation 11

7.1 Sub-Module Functions 11

7.1.1 Initialization Functions 11

7.1.2 PERIODIC FUNCTIONS 11

7.1.2.1 INIT: MotVelPER1 11

7.1.2.1.1 Design Rationale 11

7.1.2.2 Design Rationale 11

7.1.2.3 Store Module Inputs to Local copies 11

7.1.2.4 (Processing of function)……… 11

7.1.2.5 Store Local copy of outputs into Module Outputs 11

7.1.3 PERIODIC FUNCTIONS 11

7.1.3.1 INIT: MotVelPER2 11

7.1.3.1.1 Design Rationale 11

7.1.3.2 Design Rationale 11

7.1.3.3 Store Module Inputs to Local copies 11

7.1.3.4 (Processing of function)……… 11

7.1.3.5 Store Local copy of outputs into Module Outputs 11

7.1.4 Interrupt Functions 12

Server runnables 12

7.1.4.1.1 Store Local copy of outputs into Module Outputs 12

7.1.4.2 Local Function/Macro Definitions 12

7.1.5 GLObAL Function/Macro Definitions 12

7.1.6 Tranisition FUNCTIONS 12

8 Known Limitations With Design 13

9 UNIT TEST CONSIDERATION 14

10 Appendix 15

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
| 1       | MDD Guidelines                       | Process 04.02.01                |
| 2       | Software Naming Conventions          | Process 04.02.01                |
| 3       | Software Design and Coding standards | Process 04.02.01                |
| 4       | FDD : SF40A_MotVel_Design            | See Synergy sub project version |
|         |                                      |                                 |

# MotVel & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation OF MotVel

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF040A_MotVel_Impl/doc/mediax/media/image1.png"
style="width:2.9375in;height:3.14583in" />

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
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
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

|  Enum Name | Element Name | Value |
|------------|--------------|-------|
| None       | N/A          | N/A   |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local 

| Constant Name     | Resolution | Units | Value |
|-------------------|------------|-------|-------|
| Refer the m files |            |       |       |

**6.1.1.2** **Global**

| Constant Name |
|---------------|
| N/A           |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
| None          | N/A        | N/A   | N/A              |

# Software Module Implementation

## Sub-Module Functions 

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## INIT: MotVelPER1

## 

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

##  [section-1]

## PERIODIC FUNCTIONS 

## INIT: MotVelPER2

## 

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## 

## Interrupt Functions

*None*

## Server runnables [server-runnables]

*None*

## Store Local copy of outputs into Module Outputs

*None*

## Local Function/Macro Definitions

*None*

## GLObAL Function/Macro Definitions

None

## Tranisition FUNCTIONS 

None

# Known Limitations With Design

1.  In SF040A datadictionary (Ver 2.0.0), MotAgBufIdx input signal is
    removed. But it is used in the SF040A implementation(ver
    2.0.0)’MotVelPer2’. This leads mismatch between DD and Design.

2.  MotCtrlMotAgBuf and MotCtrlMotAgTiBuf are removed in data dictionary
    but used in the model in MotVelPer1. This leads mismatch between DD
    and Design.

# UNIT TEST CONSIDERATION

None

# Appendix

*None*

{% endraw %}