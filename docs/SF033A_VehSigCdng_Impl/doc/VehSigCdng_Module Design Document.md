---
layout: default
title: VehSigCdng_Module Design Document
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**VehSigCdng**

**Sep** **20, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Spandana Balani  
<u>Change History</u>**

|     |     |     |     |
|-----|-----|-----|-----|
|     |     |     |     |
|     |     |     |     |
|     |     |     |     |

|             |                        |            |             |             |
|-------------|------------------------|------------|-------------|-------------|
| **Sl. No.** | **Description**        | **Author** | **Version** | **Date**    |
| 1           | Initial Version        | SB         | 1           | 13-Jul-2015 |
| 2           | Updated for FDD v2.0.0 | NS         | 2           | 2-Jun-2016  |
| 3           | Updated for FDD v2.2.0 | SB         | 3           | 20-Sep-2016 |
|             |                        |            |             |             |

<u>Table of Contents</u>

1 Introduction 4

1.1 Purpose 4

1.2 Scope 4

2 VehSigCdng High-Level Description 5

3 Design details of software module 6

3.1 Graphical representation of VehSigCdng 6

3.2 Data Flow Diagram 8

3.2.1 Component level DFD 8

3.2.2 Function level DFD 8

4 Constant Data Dictionary 9

4.1 Program (fixed) Constants 9

4.1.1 Embedded Constants 9

5 Software Component Implementation 10

5.1.1 Sub-Module Functions 10

5.1.2 Interrupt Service Routines 10

5.1.3 Server Runnable Functions 10

5.1.4 Module Internal (Local) Functions 10

5.1.5 Transition Functions 11

6 Known Limitations with Design 13

7 UNIT TEST CONSIDERATION 14

Appendix A Abbreviations and Acronyms 15

Appendix B Glossary 16

Appendix C References 17

# Introduction

## Purpose

## Scope

# VehSigCdng High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of VehSigCdng

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF033A_VehSigCdng_Impl/doc/mediax/media/image2.PNG"
style="width:4.8861in;height:8.49077in" />

## Data Flow Diagram

### Component level DFD

Refer to FDD

### Function level DFD

Refer to FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

See .m file

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module VehSigCdngInit1()

#### Periodic sub-module VehSigCdngPer1()

Design Rationale - *Fault Injection client call is conditional compiled
based on “FLTINJENA” build constant.*

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

#### Local Function \#1

Refer to VehSpd block in the model

|                      |                            |         |       |      |
|----------------------|----------------------------|---------|-------|------|
| **Function Name**    | VehSigCdng_VehSpd          | Type    | Min   | Max  |
| **Arguments Passed** | VehSpdSerlCom_Kph_T_f32    | Float32 | 0     | 511  |
|                      | VehSpdVldSerlCom_Cnt_T_lgc | Boolean | FALSE | TRUE |
|                      | VehSpdOvrd_Kph_T_f32       | Float32 | 0     | 511  |
|                      | VehSpdOvrdVld_Cnt_T_logl   | Boolean | FALSE | TRUE |
|                      | VehSpd_Kph_T_f32           | Float32 | 0     | 511  |
|                      | VehSpdVld_Cnt_T_logl       | Boolean | FALSE | TRUE |
| **Return Value**     | N/A                        |         |       |      |

Notes: VehSpd_Kph_T_f32, VehSpdVld_Cnt_T_logl are the outputs of the
function

#### Local Function \#2

Refer to VehLgtA block in the model

|                      |                                   |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | VehSigCdng_VehLgtA                | Type    | Min   | Max  |
| **Arguments Passed** | VehLgtASerlCom_MpSecSq_T_f32      | Float32 | -180  | 180  |
|                      | VehLgtAVldSerlCom_Cnt_T_lgc       | Boolean | FALSE | TRUE |
|                      | VehLgtA_KphpS_T_f32               | Float32 | -50   | 50   |
|                      | VehLgtAVld_Cnt_T_logl             | Boolean | FALSE | TRUE |
| **Return Value**     | (if no value returned, write N/A) |         |       |      |

Notes: VehLgtA_KphpS_T_f32, VehLgtAVld_Cnt_T_logl are the outputs of the
function

#### Local Function \#3

Refer to VehLatA block in the model

|                      |                                   |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | VehSigCdng_VehLatA                | Type    | Min   | Max  |
| **Arguments Passed** | VehLatASerlCom_MpSecSq_T_f32      | Float32 | -10   | 10   |
|                      | VehLatAVldSerlCom_Cnt_T_lgc       | Boolean | FALSE | TRUE |
|                      | VehLatA_MpSecSq_T_f32             | Float32 | -10   | 10   |
|                      | VehLatAVld_Cnt_T_logl             | Boolean | FALSE | TRUE |
| **Return Value**     | (if no value returned, write N/A) |         |       |      |

Notes: VehLatA_MpSecSq_T_f32, VehLatAVld_Cnt_T_logl are the outputs of
the function

#### Local Function \#4

Refer to VehYawRate block in the model

|                      |                                   |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | VehSigCdng_VehYawRate             | Type    | Min   | Max  |
| **Arguments Passed** | VehYawRateSerlCom_DegpS_T_f32     | Float32 | -120  | 120  |
|                      | VehYawRateVldSerlCom_Cnt_T_lgc    | Boolean | FALSE | TRUE |
|                      | VehYawRate_DegpS_T_f32            | Float32 | -120  | 120  |
|                      | VehYawRateVld_Cnt_T_logl          | Boolean | FALSE | TRUE |
| **Return Value**     | (if no value returned, write N/A) |         |       |      |

Notes: VehYawRate_DegpS_T_f32, VehYawRateVld_Cnt_T_logl are the outputs
of the function

#### Local Function \#5

Refer to “Lateral Acceleration Estimation” block in the model

|                      |                                   |         |       |      |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | VehSigCdng_LatAEstmn              | Type    | Min   | Max  |
| **Arguments Passed** | VehYawRate_DegpS_T_f32            | Float32 | -120  | 120  |
|                      | VehYawRateVld_Cnt_T_lgc           | Boolean | FALSE | TRUE |
|                      | VehSpd_Kph_T_f32                  | Float32 | 0     | 511  |
|                      | VehSpdVld_Cnt_T_logl              | Boolean | FALSE | TRUE |
|                      | VehLatAEstimd_MtrPerSecSqd_T_f32  | Float32 | -10   | 10   |
|                      | VehLatAEstimdVld_Cnt_T_logl       | Boolean | FALSE | TRUE |
| **Return Value**     | (if no value returned, write N/A) |         |       |      |

Notes: VehLatAEstimd_MtrPerSecSqd_T_f32, VehLatAEstimdVld_Cnt_T_logl are
the outputs of the function

### Transition Functions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD – SF033A_VehSigCdng_Design                                                                                                                                        | See Synergy Sub project version |

{% endraw %}