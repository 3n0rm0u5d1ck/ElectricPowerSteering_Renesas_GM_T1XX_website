---
layout: default
title: HwAgSnsrls_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HwAgSnsrls**

**VERSION: 4.0**

**DATE: 17-Nov-2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI**

**CHENNAI, INDIA**

**  
**

**<u>Change History</u>**

|                                                        |                 |             |             |
|----------------------------------------|-----------|---------|-------------|
| **Description**                                        | **Author**      | **Version** | **Date**    |
| Initial Version                                        | TATA            | 1.0         | 29-Jun-2016 |
| Implemented design 1.2.0, 1.3.0 and fixed anomaly 6881 | Hari Mattupalli | 2.0         | 22-Sep-2016 |
| Implemented design 1.4.0 and fixed anomaly 7844        | Hari Mattupalli | 3.0         | 21-Oct-2016 |
| Updated per design rev. 1.6.0                          | TATA            | 4.0         | 17-Nov-2016 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[2 HwAgSnsrls & High-Level Description
[6](#hwagsnsrls-high-level-description)](#hwagsnsrls-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwAgSnsrls
[7](#graphical-representation-of-hwagsnsrls)](#graphical-representation-of-hwagsnsrls)

[3.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[8](#component-level-dfd)](#component-level-dfd)

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

[5.1.1 Init: HwAgSnsrlsInit1
[10](#init-hwagsnsrlsinit1)](#init-hwagsnsrlsinit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Per: HwAgSnsrlsPer1
[10](#per-hwagsnsrlsper1)](#per-hwagsnsrlsper1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runnables [10](#server-runnables)](#server-runnables)

[5.2.1 FSnsrlsHwCentr [10](#fsnsrlshwcentr)](#fsnsrlshwcentr)

[5.2.1.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[5.2.1.2 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.2.2 RstSnsrlsHwCentr [11](#rstsnsrlshwcentr)](#rstsnsrlshwcentr)

[5.2.2.1 Design Rationale
[11](#design-rationale-3)](#design-rationale-3)

[5.2.2.2 (Processing of function)………
[11](#processing-of-function-2)](#processing-of-function-2)

[5.3 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[11](#design-rationale-4)](#design-rationale-4)

[5.4.1.2 Processing [11](#processing)](#processing)

[5.4.2 Local Function \#2 [12](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[12](#design-rationale-5)](#design-rationale-5)

[5.4.2.2 Processing [12](#processing-1)](#processing-1)

[5.4.3 Local Function \#3 [12](#local-function-3)](#local-function-3)

[5.4.3.1 Design Rationale
[12](#design-rationale-6)](#design-rationale-6)

[5.4.3.2 Processing [13](#processing-2)](#processing-2)

[5.4.4 Local Function \#4 [13](#local-function-4)](#local-function-4)

[5.4.4.1 Design Rationale
[13](#design-rationale-7)](#design-rationale-7)

[5.4.4.2 Processing [13](#processing-3)](#processing-3)

[6 Known Limitations with Design
[14](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[15](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[16](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [17](#glossary)](#glossary)

[Appendix C References [18](#references)](#references)

# Introduction

## Purpose

MDD for Handwheel Angle Sensorless.

# HwAgSnsrls & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of HwAgSnsrls

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF042A_HwAgSnsrls_Impl/doc/mediax/media/image1.jpeg"
style="width:4.22917in;height:5.42708in" alt="E:\Doc\SF042A.JPG" />

## Data Flow Diagram

### Component level DFD

Please refer FDD.

### Function level DFD

Please refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                        | Units | Value |
|--------------------------------------|-------|-------|
| Please refer Data Dictionary .m file | NA    | NA    |

# Software Component Implementation

## Sub-Module Functions

## Init: HwAgSnsrlsInit1

## Design Rationale

None

## Module Outputs

None

###  [section]

## Per: HwAgSnsrlsPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runnables 

##  FSnsrlsHwCentr

## Design Rationale

None

##  (Processing of function)………

Please see FSnsrlsHwCentr block in FDD

##  RstSnsrlsHwCentr

## Design Rationale

None

##  (Processing of function)………

Please see RstSnsrlsHwCentr block in FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                          |         |          |         |
|----------------------|--------------------------|---------|----------|---------|
| **Function Name**    | WhlSpdAutocentr          | Type    | Min      | Max     |
| **Arguments Passed** | WhlFrqVld_Cnt_T_lgc      | boolean | FALSE    | TRUE    |
|                      | WhlLeFrq_Hz_T_f32        | float32 | 0.01F    | 60.0F   |
|                      | WhlRiFrq_Hz_T_f32        | float32 | 0.01F    | 60.0F   |
|                      | VehSpd_Kph_T_f32         | float32 | 0.0F     | 511.0F  |
|                      | RelHwAg_HwDeg_T_f32      | float32 | -1440.0F | 1440.0F |
|                      | \*WhlSpdHwConf_Uls_T_f32 | float32 | 0.0F     | 1.0F    |
| **Return Value**     | None                     |         |          |         |

## Design Rationale

None.

## Processing

Refer to the “WhlSpdAutocentr” block of the Simulink model of the
design.

## Local Function \#2

|                      |                               |         |          |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | VehDynAutoCentr               | Type    | Min      | Max     |
| **Arguments Passed** | MotTqCmdCrf_MotNwtMtr_T_f32   | float32 | -8.8     | 8.8     |
|                      | HwTq_HwNwtMtr_T_f32           | float32 | -10.0F   | 10.0F   |
|                      | VehYawRate_VehDegPerSec_T_f32 | float32 | -120.0F  | 120.0F  |
|                      | VehSpd_Kph_T_f32              | float32 | 0.0F     | 511.0F  |
|                      | MotVelCrf_MotRadPerSec_T_f32  | float32 | -1350.0F | 1350.0F |
|                      | VehSpdVld_Cnt_T_logl          | Boolean | FALSE    | TRUE    |
|                      | RelHwAg_HwDeg_T_f32           | float32 | -1440.0F | 1440.0F |
|                      | \*VehDynHwConf_Uls_T_f32      | float32 | 0.0F     | 1.0F    |
| **Return Value**     | None                          |         |          |         |

##  [section-1]

## Design Rationale

None.

## Processing

Refer to the “VehDynAutoCentr” block of the Simulink model of the
design.

## Local Function \#3

|                      |                               |         |          |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | PinionTqCalcandLpFilOneEna    | Type    | Min      | Max     |
| **Arguments Passed** | MotTqCmdCrf_MotNwtMtr_T_f32   | float32 | -8.8     | 8.8     |
|                      | HwTq_HwNwtMtr_T_f32           | float32 | -10.0F   | 10.0F   |
|                      | VehYawRate_VehDegPerSec_T_f32 | float32 | -120.0F  | 120.0F  |
|                      | VehSpd_Kph_T_f32              | float32 | 0.0F     | 511.0F  |
|                      | MotVelCrf_MotRadPerSec_T_f32  | float32 | -1350.0F | 1350.0F |
|                      | VehSpdVld_Cnt_T_logl          | boolean | FALSE    | TRUE    |
|                      | RelHwAg_HwDeg_T_f32           | float32 | -1440.0F | 1440.0F |
| **Return Value**     | FilOneEna_MilliSec_T_lgc      | boolean | FALSE    | TRUE    |

## Design Rationale

None.

## Processing

Refer to the “PinionTqCalc” and “LpFilOneEna” blocks of the Simulink
model of the design.

## Local Function \#4

|                      |                        |         |          |         |
|----------------------|------------------------|---------|----------|---------|
| **Function Name**    | ArbtrtnSmthng          | Type    | Min      | Max     |
| **Arguments Passed** | FCentrHwConf_Uls_T_f32 | float32 | 0.0F     | 1.0F    |
|                      | VehDynHwConf_Uls_T_f32 | float32 | 0.0F     | 1.0F    |
|                      | WhlSpdHwConf_Uls_T_f32 | float32 | 0.0F     | 1.0F    |
|                      | RelHwAg_HwDeg_T_f32    | float32 | -1440.0F | 1440.0F |
|                      | \*LrndHwConf_Uls_T_f32 | float32 | 0.0F     | 1.0F    |
| **Return Value**     | None                   |         |          |         |

## Design Rationale

None.

## Processing

Please refer to the “Arbitration” and “Smoothing” blocks of the Simulink
model of the design.

# Known Limitations with Design

None.

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

| **Ref. \#** | **Title**                                                                                                                                                           | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                  | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                       | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 1.0                             |
| 4           | [Software Coding Standards.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.1                             |
| 5           | FDD : SF042A_HwAgSnsrls_Design                                                                                                                                      | See Synergy Sub-project version |

{% endraw %}