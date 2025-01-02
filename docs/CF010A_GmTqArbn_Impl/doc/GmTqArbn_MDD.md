---
layout: default
title: GmTqArbn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmTqArbn**

**Feb 9, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Jayakrishnan T,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                  |                        |             |            |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                  | **Author**             | **Version** | **Date**   |
| Initial Version                                                  | Sankardu Varadapureddi | 1           | 5-Oct-2015 |
| Updated graphical representation to match anomaly EA4#2143 fixes | Nick Saxton            | 2           | 1-Feb-2016 |
| Updated graphical representation                                 | Nick Saxton            | 3           | 6-Apr-2016 |
| Updates as per latest FDD version                                | Jayakrishnan T         | 4           | 9-Feb-2017 |

**  
**

<u>Table of Contents</u>1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 GmTqArbn High-Level Description 6

3 Design details of software module 7

Graphical representation of GmTqArbn 7

3.1 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: GmTqArbnInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Module Outputs 9

5.1.2 Per: GmTqArbnPer1 9

5.1.2.1 Design Rationale 9

5.1.2.2 Store Module Inputs to Local copies 9

5.1.2.3 (Processing of function)……… 9

5.1.2.4 Store Local copy of outputs into Module Outputs 9

5.2 Server Runables 9

5.3 Interrupt Functions 9

5.4 Module Internal (Local) Functions 9

5.4.1 Local Function \#1 9

5.4.1.1 Description 10

5.4.2 Local Function \#2 10

5.4.2.1 Description 10

5.4.3 Local Function \#3 10

5.4.3.1 Description 10

5.5 GLOBAL Function/Macro Definitions 10

6 Known Limitations with Design 11

7 UNIT TEST CONSIDERATION 12

Appendix A Abbreviations and Acronyms 13

Appendix B Glossary 14

Appendix C References 15

# Introduction

## Purpose

## Scope

# GmTqArbn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of GmTqArbn

## 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF010A_GmTqArbn_Impl/doc/mediax/media/image2.png"
style="width:4.40625in;height:4.625in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Refer .m file

# Software Component Implementation

## Sub-Module Functions

## Init: GmTqArbnInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: GmTqArbnPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                |         |       |      |     |
|-------------|------------------------|-------------|-----------|--|-----------|
| **Function Name**    | PosnServoSmotRamp              | Type    | Min   |      | Max |
| **Arguments Passed** | PosSrvoCmd_HwNwtMtr_T_f32      | float32 | -8.8  | 8.8  |     |
|                      | PosSrvoSmoothEnable_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | HwTq_HwNwtMtr_T_f32            | float32 | -10   | 10   |     |
|                      | \*APAOvrlCmd_MotNwtMtr_T_f32   | float32 | -8.8  | 8.8  |     |
|                      | \*ScaleFactor_Uls_T_f32        | float32 | 0     | 1    |     |
| **Return Value**     | none                           |         |       |      |     |

## Description

'PosnServo_Smoothed_Ramp' functional block implementation.

## Local Function \#2

|                      |                               |         |      |      |     |
|--------------|-----------------------|-------------|------------|--|-----------|
| **Function Name**    | RampVal                       | Type    | Min  |      | Max |
| **Arguments Passed** | DesLKATqCmd_HwNwtMtr_T_f32    | float32 | -3   | 3    |     |
|                      | VehSpd_Kph_T_f32              | float32 | 0    | 511  |     |
|                      | OutpTqOvrlCmd_MotNwtMtr_T_f32 | float32 | 0.0F | 8.8F |     |
| **Return Value**     | LKAInterTqCmd_HwNwtMtr_T_f32  | float32 | -3   | 3    |     |

## Description

'Ramp to Value' functional block implementation.

## Local Function \#3

|                      |                           |                |       |      |     |
|--------------|---------------------|---------------|-----------|--|-----------|
| **Function Name**    | ESCLogic                  | Type           | Min   |      | Max |
| **Arguments Passed** | EscCmd_HwNwtMtr_T_f32     | float32        | -10   | 10   |     |
|                      | EscSt_Cnt_T_enum          | GmTqArbnEscSt1 | 0     | 4    |     |
|                      | \*ESCTqCmd_HwNwtMtr_T_f32 | float32        | -3    | 3    |     |
|                      | \*EscLimdActv_Cnt_T_logl  | boolean        | FALSE | TRUE |     |
| **Return Value**     | ESCActv_Cnt_T_logl        | boolean        | FALSE | TRUE |     |

## Description

'ESC Logic' functional block implementation.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

*None*

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
| 5           | FDD : CF010A\_ GmTqArbn_Design                                                                                                                                        | See Synergy sub project version |

{% endraw %}