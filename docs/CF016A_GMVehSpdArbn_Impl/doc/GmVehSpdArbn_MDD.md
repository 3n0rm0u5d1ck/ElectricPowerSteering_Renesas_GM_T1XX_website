---
layout: default
title: GmVehSpdArbn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmVehSpdArbn**

**March 15, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                                                                  |            |             |             |
|------------------|----------------|----------|----------------------------|
| **Description**                                                                                                  | **Author** | **Version** | **Date**    |
| Initial Version                                                                                                  | N. Saxton  | 1.0         | 03-Sep-2015 |
| Updated graphical representation                                                                                 | N. Saxton  | 2.0         | 12-Nov-2015 |
| Added Init function to sub-module functions and Updated graphical representation for addition of timer functions | N. Saxton  | 3.0         | 15-Mar-2016 |

**<u>Table of Contents</u>**

[1 GmVehSpdArbn High-Level Description
[5](#gmvehspdarbn-high-level-description)](#gmvehspdarbn-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of GmVehSpdArbn
[6](#graphical-representation-of-gmvehspdarbn)](#graphical-representation-of-gmvehspdarbn)

[2.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[4.1.1 Per: GmVehSpdArbnPer1
[8](#per-gmvehspdarbnper1)](#per-gmvehspdarbnper1)

[4.1.1.1 Design Rationale [8](#design-rationale)](#design-rationale)

[4.1.1.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.1.3 (Processing of function)………
[8](#processing-of-function)](#processing-of-function)

[4.1.1.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.1.2 Init: GmVehSpdArbnInit1
[8](#init-gmvehspdarbninit1)](#init-gmvehspdarbninit1)

[4.1.2.1 Design Rationale [8](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[8](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[4.1.2.3 (Processing of function)………
[8](#_Toc445817951)](#_Toc445817951)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[8](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[4.2 Server Runables [8](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[8](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [8](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[4.4.1.2 Processing [9](#processing)](#processing)

[4.4.2 Local Function \#2 [9](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale [9](#design-rationale-3)](#design-rationale-3)

[4.4.2.2 Processing [9](#processing-1)](#processing-1)

[4.4.3 Local Function \#3 [9](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale [9](#design-rationale-4)](#design-rationale-4)

[4.4.3.2 Processing [9](#processing-2)](#processing-2)

[4.4.4 Local Function \#4 [9](#local-function-4)](#local-function-4)

[4.4.4.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[4.4.4.2 Processing [10](#processing-3)](#processing-3)

[4.4.5 Local Function \#5 [10](#local-function-5)](#local-function-5)

[4.4.5.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[4.4.5.2 Processing [10](#processing-4)](#processing-4)

[4.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# GmVehSpdArbn High-Level Description

*This GM specific function determines how EPS shall calculate Secure
Vehicle Speed, Non-Secure Vehicle Speed, and how to arbitrate between
those signals in addition to a serial communication supplied vehicle
speed signal.*

# Design details of software module

## Graphical representation of GmVehSpdArbn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF016A_GMVehSpdArbn_Impl/doc/mediax/media/image2.PNG"
style="width:4.61842in;height:4.6278in" />

## Data Flow Diagram

Simulink model being created for component in near future

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Refer DataDict.m file.

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

## Per: GmVehSpdArbnPer1

## Design Rationale

Simulink model being created for component in near future

## Store Module Inputs to Local copies

##  (Processing of function)………

## Store Local copy of outputs into Module Outputs

## Init: GmVehSpdArbnInit1

## Design Rationale

Simulink model being created for component in near future

## Store Module Inputs to Local copies

##  (Processing of function)………

## Store Local copy of outputs into Module Outputs

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                       |         |       |      |
|----------------------|-----------------------|---------|-------|------|
| **Function Name**    | DetVld                | Type    | Min   | Max  |
| **Arguments Passed** | VldSig1_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | VldSig2_Cnt_T_logl    | Boolean | FALSE | TRUE |
|                      | StuckSig1_Cnt_T_logl  | Boolean | FALSE | TRUE |
|                      | StuckSig2_Cnt_T_logl  | Boolean | FALSE | TRUE |
| **Return Value**     | OverallVld_Cnt_T_logl | Boolean | FALSE | TRUE |

## Design Rationale

Created to reduce static path count and avoid repeated code.

## Processing

This function checks to see if at least one of the input valid signals
is FALSE (invalid) or input stuck signals is TRUE (stuck) , returning an
overall validity (OverallVld) of FALSE (invalid) if so, and TRUE (valid)
otherwise.

## Local Function \#2

|                      |                         |         |       |      |
|----------------------|-------------------------|---------|-------|------|
| **Function Name**    | DetInvld                | Type    | Min   | Max  |
| **Arguments Passed** | VldSig1_Cnt_T_logl      | Boolean | FALSE | TRUE |
|                      | VldSig2_Cnt_T_logl      | Boolean | FALSE | TRUE |
|                      | VldSig3_Cnt_T_logl      | Boolean | FALSE | TRUE |
|                      | VldSig4_Cnt_T_logl      | Boolean | FALSE | TRUE |
| **Return Value**     | OverallInvld_Cnt_T_logl | Boolean | FALSE | TRUE |

## Design Rationale

Created to reduce static path count and avoid repeated code.

## Processing

This function checks to see if all of the input signals (VldSig1 – 4)
are FALSE (invalid), returning an overall invalidity (OverallInvld) of
TRUE (invalid) if so, and FALSE (valid) otherwise.

## Local Function \#3

|                      |                    |         |       |        |
|----------------------|--------------------|---------|-------|--------|
| **Function Name**    | UpdtAvg            | Type    | Min   | Max    |
| **Arguments Passed** | VldSig_Cnt_T_logl  | Boolean | FALSE | TRUE   |
|                      | VelSig_Kph_T_f32   | Float32 | 0.0   | 511.0  |
|                      | \*AvgSum_Kph_T_f32 | Float32 | 0.0   | 2044.0 |
|                      | \*AvgCnt_Cnt_T_f32 | Float32 | 0.0   | 4.0    |

## Design Rationale

Created to reduce static path count and avoid repeated code

\* AvgSum and AvgCnt are outputs of this function

## Processing

This function adds the velocity signal input (VelSig) to the average sum
(AvgSum) and increments the average count (AvgCnt) if the input signal
is valid (VldSig).

## Local Function \#4

|                      |                    |         |       |       |
|----------------------|--------------------|---------|-------|-------|
| **Function Name**    | CondMax            | Type    | Min   | Max   |
| **Arguments Passed** | VldSig_Cnt_T_logl  | Boolean | FALSE | TRUE  |
|                      | VelSig1_Kph_T_f32  | Float32 | 0.0   | 511.0 |
|                      | VelSig2_Kph_T_f32  | Float32 | 0.0   | 511.0 |
|                      | \*MaxVel_Kph_T_f32 | Float32 | 0.0   | 511.0 |

## Design Rationale

Created to reduce static path count and avoid repeated code.

\* MaxVel_Kph_T_f32 is an output of this function

## Processing

This function sets max velocity (MaxVel) to the maximum of the previous
value of max velocity, velocity signal 1 (VelSig1), and velocity signal
2 (VelSig2) given that the valid signal condition (VldSig) is TRUE
(valid).

## Local Function \#5

|                      |                    |         |       |       |
|----------------------|--------------------|---------|-------|-------|
| **Function Name**    | CondMin            | Type    | Min   | Max   |
| **Arguments Passed** | VldSig_Cnt_T_logl  | Boolean | FALSE | TRUE  |
|                      | VelSig1_Kph_T_f32  | Float32 | 0.0   | 511.0 |
|                      | VelSig2_Kph_T_f32  | Float32 | 0.0   | 511.0 |
|                      | \*MinVel_Kph_T_f32 | Float32 | 0.0   | 511.0 |

## Design Rationale

Created to reduce static path count and avoid repeated code.

\* MinVel_Kph_T_f32 is an output of this function

## Processing

This function sets minimum velocity (MinVel) to the minimum of the
previous value of minimum velocity, velocity signal 1 (VelSig1), and
velocity signal 2 (VelSig2), given that VldSig is TRUE.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

Simulink model being created for component in near future

# UNIT TEST CONSIDERATION

Simulink model being created for component in near future

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
| 5           | CF016A_GmVehSpdArbn_Design                                                                                                                                              | See Synergy subproject version |

{% endraw %}