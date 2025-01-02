---
layout: default
title: MotAg2Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotAg2Meas**

**Apr 22, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                         |                        |             |             |
|------------------------------|------------------|------------|-------------|
| **Description**                                                         | **Author**             | **Version** | **Date**    |
| Initial Version                                                         | Sankardu Varadapureddi | 1           | 28-Aug-2015 |
| Updates of FDD v 1.5.0 and 1.6.0                                        | Krishna Anne           | 2           | 16-Mar-2016 |
| Updates of FDD v 1.7.0                                                  | Krishna Anne           | 3           | 14-Apr-2016 |
| Fixed issue found w.r.t MotPosTestOk_Cnt_T_lgc during manual inspection | Krishna Anne           | 4           | 14-Apr-2016 |

**  
**

<u>Table of Contents</u>[1 Introduction
[5](#introduction)](#introduction)

[1.1.1.1 Purpose [5](#purpose)](#purpose)

[1.1.1.2 Scope [5](#scope)](#scope)

[2 MotAg2Meas High-Level Description
[6](#motag2meas-high-level-description)](#motag2meas-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1.1.1 Graphical representation of MotAg2Meas
[7](#graphical-representation-of-motag2meas)](#graphical-representation-of-motag2meas)

[3.1.1.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.1.2 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.1.3 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1.1.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.2 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1.1.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1.2 Init: MotAg2MeasInit1
[9](#init-motag2measinit1)](#init-motag2measinit1)

[5.1.1.3 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.4 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.1.5 Per: MotAg2MeasPer1
[9](#per-motag2measper1)](#per-motag2measper1)

[5.1.1.6 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.1.7 [9](#section)](#section)

[5.1.1.8 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.1.9 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.1.10 Server Runables [9](#server-runables)](#server-runables)

[5.1.1.11 MotAg2MeasEolPrmRead_Oper
[9](#motag2measeolprmread_oper)](#motag2measeolprmread_oper)

[5.1.1.12 Design Rationale
[9](#design-rationale-2)](#design-rationale-2)

[5.1.1.13 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.1.14 (Processing of function)………
[9](#processing-of-function-1)](#processing-of-function-1)

[5.1.1.15 MotAg2MeasEolPrmWr_Oper
[10](#motag2measeolprmwr_oper)](#motag2measeolprmwr_oper)

[5.1.1.16 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.1.1.17 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.1.18 (Processing of function)………
[10](#processing-of-function-2)](#processing-of-function-2)

[5.1.1.19 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.1.1.20 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.1.1.21 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

## Scope

# MotAg2Meas High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of MotAg2Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES241A_MotAg2Meas_Impl/doc/mediax/media/image1.png"
style="width:3.08819in;height:3.67986in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants [local-constants]

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
| SINCOSMINERR_CNT_U08 | 1          | Cnt   | 0x01  |
| SINCOSMAXERR_CNT_U08 | 1          | Cnt   | 0x02  |
| ROLLCNTMAX_CNT_U08   | 1          | Cnt   | 255   |
| MOTAG2VLTGSQDMIN     | 1          | Volt  | 0.0F  |
| MOTAG2VLTGSQDMAX     | 1          | Volt  | 25.0F |

# Software Component Implementation

## Sub-Module Functions

## Init: MotAg2MeasInit1

## Design Rationale

*Refer FDD for the functionality.*

## Module Outputs

*Refer FDD*

## Per: MotAg2MeasPer1

## Design Rationale

Refer FDD for the functionality.

In the path
*ES241A_MotAg2Meas/MotAg2Meas/MotAg2MeasPer1/AnalogMsbDiagnostics* of
the FDD model, the 4 input OR block would be redundantly doing the same
functionality as done in the TestFail block of respective if action
sub-system.

## 

Store Module Inputs to Local copies

Refer FDD

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## MotAg2MeasEolPrmRead_Oper

## Design Rationale

None

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## MotAg2MeasEolPrmWr_Oper

## Design Rationale

None

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Interrupt Functions

*None*

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.00                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : ES241A\_ MotAg2Meas_Design                                                                                                                                      | See Synergy sub project version |

{% endraw %}