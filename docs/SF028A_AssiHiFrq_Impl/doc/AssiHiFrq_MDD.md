---
layout: default
title: AssiHiFrq_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**AssiHiFrq**

**February 9, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**<u>Change History</u>**

|                                |                  |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                | **Author**       | **Version** | **Date**    |
| Initial Version                | Kathleen Creager | 01.00.00    | 04-Aug-2015 |
| Updated per design vers. 1.1.0 | Matthew Leser    | 2.0         | 09-Feb-2017 |

**<u>Table of Contents</u>**

[1 AssiHiFrq High-Level Description
[4](#assihifrq-high-level-description)](#assihifrq-high-level-description)

[2 Design details of software module
[5](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of AssiHiFrq
[5](#graphical-representation-of-assihifrq)](#graphical-representation-of-assihifrq)

[2.2 Data Flow Diagram [5](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[5](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [5](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[6](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[6](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [6](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[7](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[7](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: AssiHiFrqInit1
[7](#init-assihifrqinit1)](#init-assihifrqinit1)

[4.1.1.1 Design Rationale [7](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [7](#module-outputs)](#module-outputs)

[4.1.2 Per: AssiHiFrqPer1 [7](#per-assihifrqper1)](#per-assihifrqper1)

[4.1.2.1 Design Rationale [7](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[7](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[7](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[7](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [7](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.5 GLOBAL Function/Macro Definitions
[8](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# AssiHiFrq High-Level Description

Implements the SF028A_AssiHiFrq_Design FDD. This function provides a
means of compensating for system

inertia and road feedback. It is tunable over both vehicle speed and
handwheel torque to obtain the desired

level of disturbance rejection under various operating conditions. It
passes handwheel torque through a high-pass

filter and multiplies the resulting signal by a tunable gain factor. The
output is known as high-frequency assist

and is simply added to the usual assist calculated elsewhere

# Design details of software module

## Graphical representation of AssiHiFrq

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF028A_AssiHiFrq_Impl/doc/mediax/media/image2.png"
style="width:3.60842in;height:2.44509in" />

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution                     | Units                          | Value                          |
|---------------------------------|---------------|-----------|-------------|
| None          | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> | \<Refer MDD guidelines \[1\]\> |

# Software Component Implementation

## Sub-Module Functions

## Init: AssiHiFrqInit1

## Design Rationale

Init function is present in DataDict.m file but not shown in FDD model,
and no initialization logic is needed. This is implemented as an empty
function.

## Module Outputs

None

###  [section]

## Per: AssiHiFrqPer1

## Design Rationale

FDD model does not contain a block named AssiHiFrqPer1; this function
implements the AssiHiFrq block.

BilnrIntrpnWithRound_u16_u16MplXu16MplY function from NxtrIntrpn library
used to implement the 2-D Lookup tables in the
SF028A_AssiHiFrq/AssiHiFrq/AssiHiFrq/Determine Gain model block.

Blnd_f32 function from NxtrMath library used to implement the part of
the model that computes GainVal_MtrNmpHwNm from the outputs of the three
bilinear interpolation functions in the
SF028A_AssiHiFrq/AssiHiFrq/AssiHiFrq/Determine Gain model block.

FilHpUpdGain and FilHpUpdOutp_f32 functions from the NxtrFil library
used to implement HP-CF Filter block in the
SF028A_AssiHiFrq/AssiHiFrq/AssiHiFrq model block.

A note in the model mentions that the frequency lookup table for the
high pass filter cutoff frequency could be converted to the filter gain
values at initialization. This was not done because the DataDict.m file
did not contain the necessary IRV for the converted table, and the
FilHpUpdGain library function expects frequency in Hz; if this
throughput improvement (converting the frequency table once in
initialization) is made in the future, a new version of FilHpUpdGain
will be needed.

LnrIntrpn_u16_u16VariXu16VariY function from NxtrIntrpn library used to
implement the “freq lookup” block in the
SF028A_AssiHiFrq/AssiHiFrq/AssiHiFrq model block.

## Store Module Inputs to Local copies

See FDD

## (Processing of function)………

See FDD, and design rationale noted above.

## Store Local copy of outputs into Module Outputs

See FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description** |
|-----------------------------|-----------------|
|                             |                 |
|                             |                 |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                      | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                   |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                            |
| 5           | SF028A_AssiHiFrq_Design                                                                                                                                                 | See Synergy subproject version |

{% endraw %}