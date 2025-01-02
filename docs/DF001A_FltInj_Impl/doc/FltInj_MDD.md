---
layout: default
title: FltInj_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**FltInj**

**04/29/2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                            |                |             |          |
|----------------------------|----------------|-------------|----------|
| **Description**            | **Author**     | **Version** | **Date** |
| Initial Version            | Lucas Wendling | 1.0         | 08/26/15 |
| Updates are per FDD v2.1.0 | Krishna Anne   | 2.0         | 04/29/16 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#section)](#section)

[2 \<Component Name\> & High-Level Description
[6](#fltinj-high-level-description)](#fltinj-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of \<Component Name\>
[7](#graphical-representation-of-fltinj)](#graphical-representation-of-fltinj)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: \<Component Name\>\_Init\<n\> [9](#init)](#init)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: \<Component Name\>\_Per\<n\>
[9](#per-fltinjper1)](#per-fltinjper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 \<Server Runable Name\> [9](#_Toc428337900)](#_Toc428337900)

[5.2.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.3.1 Interrupt Function Name
[10](#interrupt-function-name)](#interrupt-function-name)

[5.3.1.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[5.3.1.2 (Processing of the ISR function)…..
[10](#processing-of-the-isr-function..)](#processing-of-the-isr-function..)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#section-2)](#section-2)

[5.4.1.1 Design Rationale [10](#section-3)](#section-3)

[5.4.1.2 Processing [10](#section-4)](#section-4)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#section-5)](#section-5)

[5.5.1.1 Design Rationale [11](#section-6)](#section-6)

[5.5.1.2 processing [11](#section-7)](#section-7)

[6 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

MDD for FltInj (DF001A).

## 

-   
-   
-   

# FltInj High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of FltInj

## Data Flow Diagram

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/DF001A_FltInj_Impl/doc/mediax/media/image1.png"
style="width:3.10833in;height:2.575in" />

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name           | Resolution             | Units        | Value |
|-------------------------|------------------------|--------------|-------|
| TICNVN_MICROTOMILLI_F32 | Single precision float | MicroToMilli | 0.001 |

-   For other constants, refer DataDict.m

# Software Component Implementation

## Sub-Module Functions

## Init: 

None

## Design Rationale

*N/A*

## Module Outputs

*N/A*

###  [section-1]

## Per: FltInjPer1

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## FltInj_f32_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FltInj_logl_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FltInj_u08_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FltInj_u0p16_Oper

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

*None*

## Interrupt Function Name

*N/A*

## Design Rationale

*N/A*

## (Processing of the ISR function)…..

*N/A*

## Module Internal (Local) Functions

NA

## 

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

## 

## 

## GLOBAL Function/Macro Definitions

NA

## 

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

## 

## 

# Known Limitations with Design

# UNIT TEST CONSIDERATION

1.  Unit testing should be performed for when the build constant
    FLTINJENA is set to STD_ON in order to enable core functionality of
    this module. This will have to be done by manually altering FltInj.h
    to change the value of this \#define.

2.  The SigPah_Arg signal of the FltInj_f32 server runnable has a
    special unit test consideration (MIL, SIL, PIL) that the range
    called out in the data dictionary should only be used for defining
    "input" vectors, and the range check that is normal done on the
    "output" is skipped in this special instance. (This second point is
    copied from the FDD).

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
| 4           | DF001A_FltInj_Design                                                                                                                                                    | See Synergy subproject version |

{% endraw %}