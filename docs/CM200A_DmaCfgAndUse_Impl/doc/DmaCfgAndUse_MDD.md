---
layout: default
title: DmaCfgAndUse_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**DmaCfgAndUse**

**VERSION:** **3.0**

**DATE:** **10-Jun-2016**

**Prepared By:**

**Avinash James**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|                                                                                                      |                  |             |             |
|------------------------|------------------------|----------|--------------|
| **Description**                                                                                      | **Author**       | **Version** | **Date**    |
| Initial Version                                                                                      | Kathleen Creager | 1.0         | 08-Jun-2015 |
| Changes for FDD version CM200A_DmaCfgAndUse_Design_1.4.0                                             | Kathleen Creager | 2.0         | 20-Oct-2015 |
| Added rationale for diplay variable deviation and also changed the time out time from 100 to 400uSec | Avinash James    | 3.0         | 10-Jun-2016 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 DmaCfgAndUse High-Level Description
7](#dmacfganduse-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of DmaCfgAndUse
8](#graphical-representation-of-dmacfganduse)

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

[7.2.1 Init: DmaCfgAndUseInit1 11](#init-dmacfganduseinit1)

[7.2.1.1 Design Rationale 11](#design-rationale)

[7.2.1.2 Module Outputs 11](#module-outputs)

[7.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[7.3.1 Per: DmaCfgAndUsePer1 11](#per-dmacfganduseper1)

[7.3.1.1 Design Rationale 11](#design-rationale-1)

[7.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[7.3.1.3 (Processing of function)……… 11](#processing-of-function)

[7.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[7.4 Non PERIODIC FUNCTIONS 11](#non-periodic-functions)

[7.4.1 NONPer: DmaEna2MilliSecToMotCtrlTrf_Oper
12](#nonper-dmaena2millisectomotctrltrf_oper)

[7.4.1.1 Design Rationale 12](#design-rationale-2)

[7.4.1.2 Store Module Inputs to Local copies
12](#store-module-inputs-to-local-copies-1)

[7.4.1.3 (Processing of function)……… 12](#processing-of-function-1)

[7.4.1.4 Store Local copy of outputs into Module Outputs
12](#store-local-copy-of-outputs-into-module-outputs-1)

[7.4.2 NONPer: DmaWaitForMotCtrlTo2MilliSecTrf_Oper
12](#nonper-dmawaitformotctrlto2millisectrf_oper)

[7.4.2.1 Design Rationale 12](#design-rationale-3)

[7.4.2.2 Store Module Inputs to Local copies
12](#store-module-inputs-to-local-copies-2)

[7.4.2.3 (Processing of function)……… 12](#processing-of-function-2)

[7.4.2.4 Store Local copy of outputs into Module Outputs
12](#store-local-copy-of-outputs-into-module-outputs-2)

[7.5 Interrupt Functions 12](#interrupt-functions)

[7.6 Serial Communication Functions 13](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
13](#local-functionmacro-definitions)

[7.8 GLObAL Function/Macro Definitions
13](#global-functionmacro-definitions)

[7.8.1 GLObAL Function \#1 13](#global-function-1)

[7.8.1.1 Description 13](#description)

[7.9 TRANSIENT FUNCTIONS 13](#transient-functions)

[8 Unit Test Considerations 14](#unit-test-considerations)

[9 Known Limitations With Design 15](#known-limitations-with-design)

[10 Appendix 16](#appendix)

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

|         |                                 |                                                                          |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                           | Version                                                                  |
| \<1\>   | \<MDD Guidelines\>              | Software Engineering Process 04.00.00                                    |
| \<2\>   | \<Software Naming Conventions\> | Software Engineering Process 04.00.00 and working EA4 naming conventions |
| \<3\>   | \<Coding standards\>            | Software Engineering Process 04.00.00                                    |
| \<4\>   | \<FDD \>                        | See Synergy subproject version                                           |
|         | \<Add if more available\>       |                                                                          |

# DmaCfgAndUse High-Level Description

DMA Configuration and Usage (DmaCfgAndUse) sets up the initial DMA
configuration and defines the periodic and server runnable functionality
needed for DMA transfers of SPI, ADC, and Motor Control loop/RTE
interface data.

# Design details of software module

*See FDD.*

## Graphical representation of DmaCfgAndUse

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM200A_DmaCfgAndUse_Impl/doc/mediax/media/image1.png"
style="width:3.7in;height:2.075in" />

## Data Flow Diagram

*See FDD.*

## Module level DFD

*See FDD.*

## Sub-Module level DFD

*See FDD.*

## COMPONENT FLOW DIAGRAM

*NA*

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
<td>MotCtrlFromTwoMilliSecRec1</td>
<td>Generated in MotCtrlMgr component</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>TwoMilliSecToMotCtrlRec1</td>
<td>Generated in MotCtrlMgr component</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>MotCtrlToTwoMilliSecRec1</td>
<td>Generated in MotCtrlMgr component</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>TwoMilliSecFromMotCtrlRec1</td>
<td>Generated in MotCtrlMgr component</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 40%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Enum Name</td>
<td>Element Name</td>
<td>Value</td>
</tr>
<tr class="even">
<td><p>&lt;(Name given for the user defined typdef of type
struct/union)</p>
<p>(Variable name qualified in refer[2])&gt;</p></td>
<td>&lt;(Variable name qualified Refer[2])&gt;</td>
<td>&lt;Define the value &gt;</td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                              |            |          |       |
|------------------------------|------------|----------|-------|
| Constant Name                | Resolution | Units    | Value |
| CPU1PEID_CNT_U32             | 1          | Counts   | 1     |
| PRPHLTOLCLRAMSPID_CNT_U32    | 1          | Counts   | 3     |
| LCLRAMTOPRPHLSPID_CNT_U32    | 1          | Counts   | 2     |
| LCLRAMTOLCLRAMSPID_CNT_U32   | 1          | Counts   | 0     |
| USRMODENA_CNT_U32            | 1          | Counts   | 1     |
| USRMODDI_CNT_U32             | 1          | Counts   | 0     |
| MAXWAIT_MICROSEC_U32         | 1          | MicroSec | 400   |
| Also see FDD DataDict.m file |            |          |       |
| INIZERO_CNT_U32              | 1          | Counts   | 0     |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|                         |
|-------------------------|
| Constant Name           |
| See FDD DataDict.m file |
|                         |
|                         |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                            |                                |                                |                                |
|------------------------------|----------------|--------------|--------------|
| Constant Name                              | Resolution                     | Value                          | Software Segment               |
| \<Refer Constant name qualified in \[2\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Module Implementation

## Sub-Module Functions

*\<(Note: For multiple functions, insert new headers at the “Header 2”
level – subset of “ Sub Module Function section above” and follow the
same sub-section design shown below . If none required, place the text
“None”))\>*

## Initialization Functions

*\<(Note: For multiple init functions, insert new headers at the “Header
2” level – subset of “ Initialization Function section above” and follow
the same sub-section design shown below . If none required, place the
text “None”))\>*

## Init: DmaCfgAndUseInit1

## Design Rationale

The DMACnnCM channel master registers can be written only in supervisor
mode. After the Channel master register for a given channel has been
written, the selected Processor Element can write to that channel’s
registers in user mode. However, for simplicity, all DMA register
initialization is being done in one trusted function. Therefore, only
the Per Instance Memory initialization is done directly in the
DmaCfgAndUseInit1 function; all DMA register initialization is done in
the DmaRegInin function called by DmaCfgAndUseInit1.

## Module Outputs

*See FDD.*

## PERIODIC FUNCTIONS 

## 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “7.3 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)\>*

## Per: DmaCfgAndUsePer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See FDD.*

## Store Local copy of outputs into Module Outputs

*None*

## Non PERIODIC FUNCTIONS 

## 

## NONPer: DmaEna2MilliSecToMotCtrlTrf_Oper

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See FDD*

## Store Local copy of outputs into Module Outputs

*None*

## NONPer: DmaWaitForMotCtrlTo2MilliSecTrf_Oper

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## GLObAL Function \#1

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | DmaRegInin | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
| **Return Value**     | N/A        |      |     |     |

## Description

Trusted function that performs all register initialization from the
CM200A_DmaCfgAndUse_PeripheralCfg.xlsx spreadsheet in the FDD. The
DMACnnCM channel master registers can be written only in supervisor
mode. After the Channel master register for a given channel has been
written, the selected Processor Element can write to that channel’s
registers in user mode. However, for simplicity, all DMA register
initialization is being done in one trusted function. For timing
optimization, register level initialization is used (rather than bit
field modifications of the register fields).

## TRANSIENT FUNCTIONS 

*None*

# Unit Test Considerations

None

# Known Limitations With Design

There is a deviation from the coding standards for use of display
variables which are used only for storing values needed for test
purpose. However we have used display variable to compare with a
measured parameter and assign value to the diplay variable based on the
comparison. This deviation is okay as creating an additional per
instance memory for this purpose is redundant and hence have deviated
from the coding standards

# Appendix

*\<This section is for appendix\>*

{% endraw %}