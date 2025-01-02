---
layout: default
title: SnsrMeasStrt_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Sensor Start Measurement**

**June 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPGroup,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                                               |                    |             |             |
|-------------------------------------|----------------|---------|-----------|
| **Description**                                               | **Author**         | **Version** | **Date**    |
| Initial Version                                               | Selva Sengottaiyan | 1.0         | 12-Oct-2015 |
| CM410A SnsrMeasStrt Rev 1.1.0 - Implementation A3213 EA4#3219 | Selva Sengottaiyan | 2.0         | 22-Dec-2015 |

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1 Purpose 5](#purpose)

[2 SnsrMeasStrt & High-Level Description
6](#component-name-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of SnsrMeasStrt
7](#graphical-representation-of-snsrmeasstrt)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: SnsrMeasStrtInit1 9](#init-snsrmeasstrtinit1)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: SnsrMeasStrtPer1 9](#per-snsrmeasstrtper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runnable 9](#server-runnable)

[None 9](#none)

[5.3 Interrupt Functions 10](#interrupt-functions)

[5.3.1.3 (Processing of function)……… 10](#processing-of-function-1)

[5.4 Module Internal (Local) Functions
10](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
10](#global-functionmacro-definitions)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 16](#references)

# Introduction

## Purpose

Module design document for Sensor Measurement Start Function.

# \<Component Name\> & High-Level Description

Refer the Design.

# Design details of software module

## Graphical representation of SnsrMeasStrt

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM410A_SnsrMeasStrt_Impl/doc/mediax/media/image2.png"
style="width:1.75833in;height:1.69167in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
| Refer .m file |            |       |       |
|               |            |       |       |
|               |            |       |       |
|               |            |       |       |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

### Init: SnsrMeasStrtInit1

## Design Rationale

Magic numbers are used due to the large number of numeric values (for
peripheral register configuration), it is more readable and easier to
maintain without using embedded constants for these values. The values
are shown in code comments, and line up exactly with the definitions
given in the design module (a special spreadsheet was included in the
design for this purpose).

See CM410A_SnsrMeasStrt_PeripheralCfg.xlsx in design module.

## Module Outputs

*Refer to FDD*

###  [section]

### Per: SnsrMeasStrtPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnable 

## None [none]

## Interrupt Functions

#### SnsrMeasStrtIrq 

#### Design Rationale

*ISR calls the HwTq0, HwTq1, HwTq2, HwTq3 server runnables which inturn
trigger the Tq SENT.*

*ISR is trigger through OSTM1 timer. CM410 is designed to application
where all the torques is executed.*

##  (Processing of function)………

*None*

## Module Internal (Local) Functions

*None*

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

ISR needs to execute in the same application region of the Torque.

# UNIT TEST CONSIDERATION

Overflow for the variable **Rte_Pim_TqMsgTrigCnt** is intentional as
this is used as a rolling counter.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                            |
| 5           | FDD – CM410A SnsrMeasStrt                                                                                                                                     | See Synergy subproject version |

{% endraw %}