---
layout: default
title: HwAgTrakgServo_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgTrakgServo**

**Dec 18, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Kannappa Chidambaram (Tata Elxsi),**

**Trivandrum, INDIA.**

**  
<u>Change History</u>**

|                 |            |              |             |
|-----------------|------------|--------------|-------------|
| Initial Version | Kannappa C | EA4 01.00.01 | 18-Dec-2015 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#_Toc438214153)](#_Toc438214153)

[2 HwAgTrakgServo & High-Level Description
[6](#hwagtrakgservo-high-level-description)](#hwagtrakgservo-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwAgTrakgServo
[7](#graphical-representation-of-hwagtrakgservo)](#graphical-representation-of-hwagtrakgservo)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [8](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[9](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: HwAgTrakgServoInit1
[10](#init-hwagtrakgservoinit1)](#init-hwagtrakgservoinit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Per: HwAgTrakgServoPer1
[10](#per-hwagtrakgservoper1)](#per-hwagtrakgservoper1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [10](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#_Toc438214176)](#_Toc438214176)

[5.4.1.1 Design Rationale [11](#_Toc438214177)](#_Toc438214177)

[5.4.1.2 Processing [11](#_Toc438214178)](#_Toc438214178)

[5.4.2 Local Function \#2 [11](#_Toc438214179)](#_Toc438214179)

[5.4.2.1 Design Rationale [11](#_Toc438214180)](#_Toc438214180)

[5.4.2.2 Processing [11](#_Toc438214181)](#_Toc438214181)

[5.4.3 Local Function \#3 [11](#_Toc438214182)](#_Toc438214182)

[5.4.3.1 Design Rationale [11](#_Toc438214183)](#_Toc438214183)

[5.4.3.2 Processing [11](#_Toc438214184)](#_Toc438214184)

[5.4.4 Local Function \#4 [11](#_Toc438214185)](#_Toc438214185)

[5.4.4.1 Design Rationale [12](#_Toc438214186)](#_Toc438214186)

[5.4.4.2 Processing [12](#_Toc438214187)](#_Toc438214187)

[5.5 GLOBAL Function/Macro Definitions
[12](#local-function-1)](#local-function-1)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# Introduction

## Purpose

MDD for Handwheel Angle Tracking Servo.

# HwAgTrakgServo & High-Level Description

Please refer FDD

# Design details of software module

## Graphical representation of HwAgTrakgServo

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF020A_HwAgTrakgServo_Impl/doc/mediax/media/image1.png"
style="width:3.14583in;height:5.96875in" />

## Data Flow Diagram

Please refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                     | Resolution | Units | Value   |
|-----------------------------------|------------|-------|---------|
| SECTOMILLISEC_ULS_F32             | Float32    | Uls   | 1000.0F |
| Please refer .m file for the rest | NA         | NA    | NA      |

# Software Component Implementation

## Sub-Module Functions

## Init: HwAgTrakgServoInit1

## Design Rationale

None

## Module Outputs

None

###  [section]

## Per: HwAgTrakgServoPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                               |         |          |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | FilterDesiredAngle            | Type    | Min      | Max     |
| **Arguments Passed** | VehSpd_Kph_T_u8p8             | u8p8    | 0U       | 511U    |
|                      | HwAgTrakgServoEna_Uls_T_logl  | boolean | FALSE    | TRUE    |
|                      | HwAgTrakgServoCmd_HwDeg_T_f32 | float32 | -1440.0F | 1440.0F |
|                      | HwAg_HwDeg_T_f32              | float32 | -1440.0F | 1440.0F |
|                      | RampComplete_Cnt_T_logl       | boolean | FALSE    | TRUE    |
| **Return Value**     | HWATrgtFilt_HwDeg_T_f32       | float32 | -1440.0F | 1440.0F |

## Design Rationale

> NA

## Processing

> Please refer FilterDesiredAngle block of the FDD.
>
> (Path :
> SF020A_HwAgTrakgServo/HwAgTrakgServo/HwAgTrakgServoPer1/FilterDesiredAngle)

## GLOBAL Function/Macro Definitions

None.

# Known Limitations with Design

> None.

# UNIT TEST CONSIDERATION

None.

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                             |
| 5           | FDD: SF020A_HwAgTrakgServo_Design                                                                                                                                     | See Synergy sub project version |

{% endraw %}