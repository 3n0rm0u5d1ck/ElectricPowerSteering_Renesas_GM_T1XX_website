---
layout: default
title: MotCtrlMgr_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotCtrlMgr**

**VERSION: 2**

**DATE:** **10/28/15**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                            |                |             |          |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**            | **Author**     | **Version** | **Date** |
| 1           | Initial Version            | Lucas Wendling | 1           | 05/29/15 |
| 2           | Updates for Signal Mapping | Lucas Wendling | 2           | 10/28/15 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 MotCtrlMgr High-Level Description
6](#motctrlmgr-high-level-description)

[4 Design details of software module
7](#design-details-of-software-module)

[4.1 Graphical representation of MotCtrlMgr
7](#graphical-representation-of-motctrlmgr)

[4.2 Data Flow Diagram 7](#data-flow-diagram)

[4.2.1 Module level DFD 7](#module-level-dfd)

[4.2.2 Sub-Module level DFD 7](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 7](#component-flow-diagram)

[5 Variable Data Dictionary 8](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
8](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
8](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 9](#constant-data-dictionary)

[6.1 Program(fixed) Constants 9](#programfixed-constants)

[*6.1.1* Embedded Constants 9](#embedded-constants)

[6.1.1.1 Local 9](#local)

[6.1.1.2 Global 9](#global)

[6.1.2 Module specific Lookup Tables Constants
9](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 10](#software-module-implementation)

[7.1 Generated file description and logic
10](#generated-file-description-and-logic)

[7.2 Initialization Functions 13](#initialization-functions)

[7.3 PERIODIC FUNCTIONS 13](#periodic-functions)

[7.3.1 Per1/Per2: 13](#per1per2)

[7.4 Non PERIODIC FUNCTIONS 13](#non-periodic-functions)

[7.5 Interrupt Functions 13](#interrupt-functions)

[7.5.1 Isr: \<ModuleName\>\_Isr\<n)\> 13](#isr)

[7.6 Serial Communication Functions 14](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
14](#local-functionmacro-definitions)

[7.8 GLObAL Function/Macro Definitions
14](#global-functionmacro-definitions)

[7.9 TRANSIENT FUNCTIONS 14](#transient-functions)

[8 Unit Test Considerations 15](#unit-test-considerations)

[9 Known Limitations With Design 16](#known-limitations-with-design)

[10 Appendix 17](#appendix)

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

|         |                             |                                |
|---------|-----------------------------|--------------------------------|
| Sr. No. | Title                       | Version                        |
| 1       | MDD Guidelines              | Process 04.00.00               |
| 2       | Software Naming Conventions | Process 04.00.00               |
| 3       | Software Coding Standards   | Process 04.00.00               |
| 4       | AR300A_MotCtrlMgr_Design    | See Synergy subproject version |

# MotCtrlMgr High-Level Description

*None*

# Design details of software module

## Graphical representation of MotCtrlMgr

*None*

## Data Flow Diagram

*None*

## Module level DFD

*None*

## Sub-Module level DFD

*None*

## COMPONENT FLOW DIAGRAM

*None*

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
<td>MotCtrlToTwoMilliSecRec1</td>
<td>Elements are project specific and generated</td>
<td>struct</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>TwoMilliSecFromMotCtrlRec1</td>
<td>Elements are project specific and generated</td>
<td>struct</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>TwoMilliSecToMotCtrlRec1</td>
<td>Elements are project specific and generated</td>
<td>struct</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>MotCtrlFromTwoMilliSecRec1</td>
<td>Elements are project specific and generated</td>
<td>struct</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>MotCtrlIntRec1</td>
<td>Elements are project specific and generated</td>
<td>struct</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|                                                 |              |       |
|-------------------------------------------------|--------------|-------|
| Enum Name                                       | Element Name | Value |
| Enumerations are project specific and generated |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
| N/A           |            |       |       |

## Global

|               |
|---------------|
| Constant Name |
| N/A           |
|               |
|               |

## Module specific Lookup Tables Constants

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| N/A           |            |       |                  |

# Software Module Implementation

## Generated file description and logic

The following sections provide details on the logic used for generating
the data and functions from the MotCtrlMgr configuration. The generator
uses text templating to generate the appropriate file content based on
the configuration details. The logic described in the following sections
are implemented in the text template files provided in this component.

1.  CDD_MotCtrlMgr_Irq.c

This file contains the definition of the interrupt service routine that
Motor Control Manager defines. This interrupt service routine primarily
contains a task list for executing runnables that are required to be
scheduled at the motor control rate or motor control x2 rate. The
following table lists the configuration parameters that are required in
generation of this file:

|                                                                                   |                                                                                                                         |
|-----------------------------|-------------------------------------------|
| **Configuration Parameter**                                                       | **File Generation Usage Notes**                                                                                         |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable               | Used to determine the runnables needed to be called in the ISR task list                                                |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable/RunnableRate  | Used to determine if runnable needs to be called every ISR loop (MotorControl) or every other ISR loop (MotorControlx2) |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/IncludeHeaders         | Used for include list required for this file for runnable prototype definitions                                         |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable/SequenceOrder | Used to help define the relative calling sequence of the runnables in the ISR task list                                 |

1.  CDD_MotCtrlMgr.c

This file contains the functions for the RTE interface. This file will
receive appropriate signals from the RTE and provide appropriate signals
to the RTE. Per1 provides updated signals to the RTE after the DMA
transfer of the data successfully completed, and Per2 recieves signals
from the RTE and then indicates to the DMA that the data is ready for
transfer.

|                                                                                          |                                                                                                                                                                               |
|-----------------------------|-------------------------------------------|
| **Configuration Parameter**                                                              | **File Generation Usage Notes**                                                                                                                                               |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal                          | Used for the name of the signals being read/written by the runnables being defined.                                                                                           |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenInMotCtrlRunnable | Used in conjuction with “/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable” to determine when a signal is needed to be managed by Per1        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable        | Used in conjuction with “/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenInMotCtrlRunnable” to determine when a signal is needed to be managed by Per1 |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable     | Used in conjuction with “/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadInMotCtrlRunnable” to determine when a signal is needed to be managed by Per2    |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadInMotCtrlRunnable    | Used in conjuction with “/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable” to determine when a signal is needed to be managed by Per2     |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Size                     | Used to determine if the signals being read/written by the runnables being defined are arrays (Impacts RTE API name).                                                         |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ImplementationDataType   | Used to determine if the signals being read/written by the runnables being defined are boolean types (Impacts RTE API name).                                                  |

1.  CDD_MotCtrlMgr_Data.c

This file contains the definition of all of the structures containing
the Motor Control ISR related signals. This includes providing initial
values for all of the signals in the structure and padding the structure
for proper structure size alignment restrictions.

|                                                                                          |                                                                                                                                                                                                        |
|-----------------------------|-------------------------------------------|
| **Configuration Parameter**                                                              | **File Generation Usage Notes**                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal                          | Used to determine signal names as part of the logic to determine if special grouping is needed for TSG3 signals                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenInMotCtrlRunnable | Used to determine which initial values are needed in which structure.                                                                                                                                  |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable        | Used to determine which initial values are needed in which structure.                                                                                                                                  |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable     | Used to determine which initial values are needed in which structure.                                                                                                                                  |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadInMotCtrlRunnable    | Used to determine which initial values are needed in which structure.                                                                                                                                  |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Size                     | Used in the structure size calculation to determine how many pad bytes are needed for alignment at the end of the structure. Used also to add the appropriate braces for arrays on structure elements. |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ImplementationDataType   | Used in the structure size calculation to determine how many pad bytes are needed for alignment at the end of the structure.                                                                           |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/InitialValue             | Used as the initializer value for a given signal in the structure                                                                                                                                      |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/IncludeHeaders                  | Used for include list required for this file for definition of any intial values that may be required                                                                                                  |

1.  CDD_MotCtrlMgr_Data.h

This file defines the structure definition of the Motor Control Data
structures containing all Motor Control ISR related signals. It also
defines any enumerations that need to be accessed by Non-RTE related
code. Prototype statements for all Motor Control Data structures are
included in this file as well as the macros defined for accessing
individual signals of the Motor Control Data structures.

|                                                                                                |                                                                                                                                                                                                                                                      |
|-----------------------------|-------------------------------------------|
| **Configuration Parameter**                                                                    | **File Generation Usage Notes**                                                                                                                                                                                                                      |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum                            | Used to define enumeration accessed by Non-RTE related code. Used for enumeration name.                                                                                                                                                              |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumImplementationDataType | Used to define enumeration accessed by Non-RTE related code. Used for enumeration datatype.                                                                                                                                                          |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumElement                | Used to define enumeration accessed by Non-RTE related code. Used for enumeration element name.                                                                                                                                                      |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumElement/Value          | Used to define enumeration accessed by Non-RTE related code. Used for enumeration element value.                                                                                                                                                     |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal                                | Used to determine signal names as part of the logic to determine if special grouping is needed for TSG3 signals. Also used as signal name for structure element definitions. Used to also determine name of signal access macros that are generated. |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenInMotCtrlRunnable       | Used to determine the structure the signal should be added to.                                                                                                                                                                                       |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable              | Used to determine the structure the signal should be added to                                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable           | Used to determine the structure the signal should be added to                                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadInMotCtrlRunnable          | Used to determine the structure the signal should be added to                                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ImplementationDataType         | Used to determine datatype of structure element. Also used as part of the structure size calculation to determine how many pad bytes are needed for alignment at the end of the structure.                                                           |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/EnumerationNameReference       | Used to determine if a given signal is an enumeration and used to determine the corresponding enumeration name                                                                                                                                       |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Size                           | Used in the structure size calculation to determine how many pad bytes are needed for alignment at the end of the structure. Used also to add the appropriate array size on signals that are arrays (having size \> 1).                              |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping                         | Used for creation of motor control signal access macros for inputs that are named differently than outputs                                                                                                                                           |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping/OutputSignalName        | Output name for signal mapping (used to define an input signal macro definition)                                                                                                                                                                     |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping/InputSignalName         | Input name(s) for signal mapping (used to define the names of the signal macros)                                                                                                                                                                     |

1.  AR300A_MotCtrlMgr_DataDict.m

This file is the generated data dictionary for MotCtrlMgr. This is
intended to be used for documentation purposes as well as to aid in
creating the AUTOSAR component description files.

|                                                                                          |                                                                                                                                                                                                                                                                  |
|-----------------------------|-------------------------------------------|
| **Configuration Parameter**                                                              | **File Generation Usage Notes**                                                                                                                                                                                                                                  |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal                          | Used to determine signal name for I/O depending on signal useage.                                                                                                                                                                                                |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ImplementationDataType   | Used to determine datatype of signal. Also used for stripping off c constant qualification (“U”, “L”, “F”) on standard datatypes that is assumed to be present in the initial value. Also used to convert boolean type initial values to “0/1” from “TRUE/FALSE” |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/EnumerationNameReference | Used to determine if a given signal is an enumeration and used to determine the corresponding enumeration name                                                                                                                                                   |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/InitialValue             | Used for the initial value of a signal                                                                                                                                                                                                                           |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Size                     | Used to determine if the signal is an array and to set the format of the initial value appropriately                                                                                                                                                             |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable        | Used to determine if signal is an output from Per1 runnable                                                                                                                                                                                                      |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable     | Used to determine if signal is an input to Per2 runnable                                                                                                                                                                                                         |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Max                      | Used for Maximum value property of signal                                                                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Min                      | Used for Minimum value property of signal                                                                                                                                                                                                                        |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Units                    | Used for units property of signal                                                                                                                                                                                                                                |

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## Per1/Per2: 

See section 7.1.2

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

## Isr: 

See section 7.1.1

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

None

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

*None*

# Unit Test Considerations

# Known Limitations With Design

1.  None

# Appendix

{% endraw %}