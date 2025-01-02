---
layout: default
title: TSG31CfgAndUse_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**TSG31 Timer Subsystem Configuration and Use**

**Module Design Document**

**VERSION: 2.0**

**DATE:** **20-Jun-2015**

**Revision History**

|                                                                                                |            |             |             |
|--------------------------------|----------------|---------|----------------|
| **Description**                                                                                | **Author** | **Version** | **Date**    |
| Initial Version                                                                                | K. Creager | 1.0         | 28-Apr-2015 |
| Remove CnvNanoSecToHalfTmrCnt() function and add masking constant for changes in FDD ver 1.3.0 | K. Creager | 2.0         | 20-Jun-2015 |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 TSG31CfgAndUse High-Level Description
7](#tsg31cfganduse-high-level-description)

[3.1 Design details of software module
7](#design-details-of-software-module)

[3.2 Graphical representation of CDD_TSG31CfgAndUse
7](#graphical-representation-of-cdd_tsg31cfganduse)

[3.3 Data Flow Diagram 7](#data-flow-diagram)

[3.3.1 Module level DFD 8](#module-level-dfd)

[3.3.2 Sub-Module level DFD 8](#sub-module-level-dfd)

[3.4 COMPONENT FLOW DIAGRAM 8](#component-flow-diagram)

[4 Variable Data Dictionary 9](#variable-data-dictionary)

[4.1 User defined typedef definition/declaration
9](#user-defined-typedef-definitiondeclaration)

[4.2 Variable definition for enumerated types
9](#variable-definition-for-enumerated-types)

[5 Constant Data Dictionary 10](#constant-data-dictionary)

[5.1 Program(fixed) Constants 10](#programfixed-constants)

[5.1.1 Embedded Constants 10](#embedded-constants)

[5.1.1.1 Local 10](#local)

[5.1.1.2 Global 10](#global)

[5.1.2 Module specific Lookup Tables Constants
10](#module-specific-lookup-tables-constants)

[6 Software Module Implementation 11](#software-module-implementation)

[6.1 Sub-Module Functions 11](#sub-module-functions)

[6.1.1 Motor Control Periodic: TSG31CfgAndUsePer1
11](#motor-control-periodic-tsg31cfganduseper1)

[6.1.1.1 Design Rationale 11](#design-rationale)

[6.2 Initialization Functions 11](#initialization-functions)

[6.2.1 Init: TSG31CfgAndUseInit1 11](#init-tsg31cfganduseinit1)

[6.2.1.1 Design Rationale 11](#design-rationale-1)

[6.2.1.2 Module Outputs 11](#module-outputs)

[6.2.1.3 Module Internal 11](#module-internal)

[6.3 PERIODIC FUNCTIONS 11](#periodic-functions)

[6.3.1 Per: TSG31CfgAndUsePer2 11](#per-tsg31cfganduseper2)

[6.3.1.1 Design Rationale 11](#design-rationale-2)

[6.3.1.2 Store Module Inputs to Local copies
11](#store-module-inputs-to-local-copies)

[6.3.1.3 (Processing of function)……… 11](#processing-of-function)

[6.3.1.4 Store Local copy of outputs into Module Outputs
11](#store-local-copy-of-outputs-into-module-outputs)

[6.4 Interrupt Functions 12](#interrupt-functions)

[6.5 Serial Communication Functions 12](#serial-communication-functions)

[6.6 Local Function/Macro Definitions
12](#local-functionmacro-definitions)

[6.6.1 Local Function \#1 12](#local-function-1)

[6.6.1.1 Description 12](#description)

[6.6.2 Local Function \#2 12](#local-function-2)

[6.6.2.1 Description 12](#description-1)

[6.6.3 Local Function \#3 12](#local-function-3)

[6.6.3.1 Description 12](#description-2)

[6.6.4 Local Function \#4 12](#local-function-4)

[6.6.4.1 Description 13](#description-3)

[6.6.5 Local Function \#5 13](#local-function-5)

[6.6.5.1 Description 13](#description-4)

[6.6.6 Local Function \#6 13](#local-function-6)

[6.6.6.1 Description 13](#description-5)

[6.6.7 Local Function \#7 13](#local-function-7)

[6.6.7.1 Description 13](#description-6)

[6.6.7.2 Design Rationale 13](#design-rationale-3)

[6.6.8 Local Function \#8 14](#__RefHeading___Toc418069024)

[6.6.8.1 Description 14](#__RefHeading___Toc418069025)

[6.6.8.2 Design Rationale 14](#__RefHeading___Toc418069026)

[6.7 GLObAL Function/Macro Definitions
14](#global-functionmacro-definitions)

[6.8 TRANSIENT FUNCTIONS 14](#transient-functions)

[7 Known Limitations With Design 15](#known-limitations-with-design)

[8 UNIT TEST CONSIDERATION 16](#unit-test-consideration)

[9 Appendix 17](#appendix)

# Abbrevations And Acronyms

|              |                            |
|--------------|----------------------------|
| Abbreviation | Description                |
| DFD          | Design functional diagram  |
| MDD          | Module design Document     |
| FDD          | Functional Design Document |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                   |                                   |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                             | Version                           |
| \<1\>   | MDD Guidelines                    | Software Process Release 04.00.00 |
| \<2\>   | Software Naming Conventions       | Software Process Release 04.00.00 |
| \<3\>   | Design and Coding standards       | Software Process Release 04.00.00 |
| \<4\>   | FDD: CM475A_TSG31CfgAndUse_Design | See Synergy subproject version    |

# TSG31CfgAndUse High-Level Description

The CDD_TSG31CfgAndUse component is the complex driver for the TSG31
timer subsystem. The timer subsystem is used to trigger DMA transfers
and SPI transfers, and to set the GPIO pins for the three phase PWM
outputs. The component contains two .c source files, both described in
this MDD: CDD_TSG31CfgAndUse.c contains the RTE runnables;
CDD_TSG31CfgAndUse_MotCtrl.c contains the motor control runnable.

## Design details of software module

*See FDD.*

## Graphical representation of CDD_TSG31CfgAndUse

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM475A_TSG31CfgAndUse_Impl/doc/mediax/media/image1.png"
style="width:3.39167in;height:5.75in" />

## Data Flow Diagram

*See FDD.*

## Module level DFD

*See FDD.*

## Sub-Module level DFD

*See FDD.*

## COMPONENT FLOW DIAGRAM

*See FDD.*

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
<td><p>&lt;(Name given for the user defined typdef of type
struct/union)</p>
<p>(Variable name as qualified Refer[2])&gt;</p></td>
<td>&lt;(Variable name qualified Refer[2])&gt;</td>
<td>&lt;(Variable name qualified Refer[2&gt;</td>
<td>&lt;Min range allowed for the element in the Typedef &gt;</td>
<td>&lt;Max range allowed for the element in the Typedef&gt;</td>
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
<td>SysSt1</td>
<td><p>SYSST_DI</p>
<p>SYSST_OFF</p>
<p>SYSST_ENA</p>
<p>SYSST_WRMININ</p></td>
<td><p>0</p>
<p>1</p>
<p>2</p>
<p>3</p></td>
</tr>
<tr class="odd">
<td>MotCurrEolCalSt2</td>
<td><p>MCECS_OFFSCMDSTRT</p>
<p>MCECS_OFFSCMDHI</p>
<p>MCECS_OFFSCMDLO</p>
<p>MCECS_OFFSCMDZERO</p>
<p>MCECS_OFFSCMDEND</p>
<p>MCECS_GAINCMDAD</p>
<p>MCECS_GAINCMDBE</p>
<p>MCECS_GAINCMDCF</p>
<p>MCECS_CMDSAFEST</p></td>
<td><p>0</p>
<p>1</p>
<p>2</p>
<p>3</p>
<p>4</p>
<p>5</p>
<p>6</p>
<p>7</p>
<p>8</p></td>
</tr>
</tbody>
</table>

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                           |            |       |                         |
|---------------------------|------------|-------|-------------------------|
| Constant Name             | Resolution | Units | Value                   |
| ROUNDGTERM_CNT_U13P19     | P19        | Cnt   | 262144 counts = 0.5 p19 |
| PWMTMRPERDIVSSCAG_CNT_U16 | 1          | Cnt   | 19                      |
| CLRBIT0MASK_CNT_U32       | 1          | Cnt   | 0xFFFFFFFE              |
|                           |            |       |                         |
|                           |            |       |                         |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Constant Name</td>
</tr>
<tr class="even">
<td><blockquote>
<p>See FDD – CM475A_TSG31CfgAndUse_DataDict.m file</p>
</blockquote></td>
</tr>
<tr class="odd">
<td></td>
</tr>
<tr class="even">
<td></td>
</tr>
</tbody>
</table>

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|                                            |                                |                                |                                |
|------------------------------|----------------|--------------|--------------|
| Constant Name                              | Resolution                     | Value                          | Software Segment               |
| \<Refer Constant name qualified in \[2\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Module Implementation

Note: All the non RTE signals defined in m file are implemented as
global varibles managed by motor control manager. RTE can not manage
motor control runnables inputs and outputs.

## Sub-Module Functions

## Motor Control Periodic: TSG31CfgAndUsePer1

See FDD TSG31CfgAndUsePer1 model block.

## Design Rationale

The truth table in the TSG31CfgAndUsePer1 model block is just selecting
between four sets of statements based on the value of a single variable.
This was implemented as an if/else if. For run-time efficiency, since
this is a motor control runnable, the “normal operation” case was
checked first; since the normal operation and default cases are the
same, the statements in this row of the truth table action table are
repeated in the trailing else of the if/else.

## Initialization Functions

## Init: TSG31CfgAndUseInit1

## Design Rationale

All register initialization that is allowed at the register level (see
FieldNames tab of the CM475A_TSG31RegisterConfiguration.xlms spreadsheet
in the FDD) is done at the register level to save execution time as
compared to the read/modify/writes that would be needed to initialize at
the field level. Field level initialization done only where required by
the spreadsheet.

## Module Outputs

See FDD: TSG31CfgAndUseInit1 model block and the FieldNames tab of the
CM475A_TSG31RegisterConfiguration.xlms spreadsheet.

## Module Internal 

See FDD: TSG31CfgAndUseInit1 model block for Per Instance Memory
initialization.

## PERIODIC FUNCTIONS 

##  Per: TSG31CfgAndUsePer2

## Design Rationale

Each action block of the switch/case was implemented as a local
function. To minimize complexity, the “Out1” truth table output and the
switch case block were combined in the implementation with nested “if”s
which directly call the switch/case action functions

## Store Module Inputs to Local copies

See FDD: TSG31CfgAndUsePer2 model block.

## (Processing of function)………

See FDD: TSG31CfgAndUsePer2 model block.

## Store Local copy of outputs into Module Outputs

See FDD: TSG31CfgAndUsePer2 model block

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

## Local Function \#1 

|                      |                            |                  |     |     |
|------------|--------------------------|---------------|----------|----------|
| **Function Name**    | NoTranSysStIsEn            | Type             | Min | Max |
| **Arguments Passed** | MotCurrEolCalSt_Cnt_T_enum | MotCurrEolCalSt2 | 0   | 8   |
| **Return Value**     | N/A                        |                  |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/No Transition
SysState = Enable

## Local Function \#2

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | TranFromEn | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
| **Return Value**     | N/A        |      |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/Transition from
Enable

## Local Function \#3

|                      |          |      |     |     |
|----------------------|----------|------|-----|-----|
| **Function Name**    | TranToEn | Type | Min | Max |
| **Arguments Passed** | None     |      |     |     |
| **Return Value**     | N/A      |      |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/Transition to
Enable

## Local Function \#4

|                      |                  |      |     |     |
|----------------------|------------------|------|-----|-----|
| **Function Name**    | NoTranSysStNotEn | Type | Min | Max |
| **Arguments Passed** | None             |      |     |     |
| **Return Value**     | N/A              |      |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/No Transition
SysState != Enable

## Local Function \#5

|                      |                              |      |     |     |
|----------------------|------------------------------|------|-----|-----|
| **Function Name**    | MapFetCtrlSigToGpioAndSetLow | Type | Min | Max |
| **Arguments Passed** | None                         |      |     |     |
| **Return Value**     | N/A                          |      |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/Transition from
Enable/Map FET Ctrl Signals to GPIO and Set Low (also same block name in
other model layers)

## Local Function \#6

|                      |               |      |     |     |
|----------------------|---------------|------|-----|-----|
| **Function Name**    | MapPinsToGpio | Type | Min | Max |
| **Arguments Passed** | None          |      |     |     |
| **Return Value**     | N/A           |      |     |     |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse/TSG31CfgAndUse/TSG31CfgAndUsePer2/Transition from
Enable/Map FET Ctrl Signals to GPIO and Set Low/Map Pins to GPIO (also
same block name in other model layers)

## Local Function \#7

|                      |                                              |        |     |        |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CnvNanoSecToTmrCnt                           | Type   | Min | Max    |
| **Arguments Passed** | Ti_NanoSec_T_u32                             | uint32 | 0   | 100000 |
| **Return Value**     | Timer counts corresponding to the input time | uint32 | 0   | 8000   |

## Description

See FDD model block:
CM475A_TSG31CfgAndUse_ModelLibrary_Rev001/RawTime_NanoSec to
RawTimerCount_Cnt Conversion Block

## Design Rationale

Because this function is called by a motor control runnable, it is coded
as an inline function to maximize the chance that the compiler will
inline it, in order to improve runtime efficiency of the motor control
loop.

## 

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 38%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><h2 id="section-1"></h2></td>
<td><h2 id="section-2"></h2></td>
<td><h2 id="section-3"></h2></td>
<td><h2 id="section-4"></h2></td>
<td><h2 id="section-5"></h2></td>
</tr>
<tr class="even">
<td><h2 id="section-6"></h2></td>
<td><h2 id="section-7"></h2></td>
<td><h2 id="section-8"></h2></td>
<td><h2 id="section-9"></h2></td>
<td><h2 id="section-10"></h2></td>
</tr>
<tr class="odd">
<td><h2 id="section-11"></h2></td>
<td><h2 id="section-12"></h2></td>
<td><h2 id="section-13"></h2></td>
<td><h2 id="section-14"></h2></td>
<td><h2 id="section-15"></h2></td>
</tr>
</tbody>
</table>

##  [section-16]

##  [section-17]

##  [section-18]

##  [section-19]

##  [section-20]

##  [section-21]

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

None

# Known Limitations With Design

1.  Expected input ranges of the nanosecond to timer count conversion
    functions are based on FDD assumptions about the minimum PWM period
    that may ever be used, as stated in comments in the FDD model.

# UNIT TEST CONSIDERATION

*None*

# Appendix

*\<This section is for appendix\>*

{% endraw %}