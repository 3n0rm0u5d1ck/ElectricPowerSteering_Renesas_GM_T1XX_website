---
layout: default
title: TqOscn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TqOscn**

**Feb 05, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Kanth Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                        |                    |             |             |
|-----------------------------|-------------------|-------------|-------------|
| **Description**                        | **Author**         | **Version** | **Date**    |
| Initial Version                        | Krishna Kanth Anne | 1.0         | 05-Feb-2016 |
| Corrected ranges in local function \#1 | Krishna Kanth Anne | 2.0         | 25-May-2016 |

**  
**

Table of Contents

1 Introduction 5

1.1 Purpose 5

2 TqOscn & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of TqOscn 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: TqOscnInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Module Outputs 9

5.1.2 None 9

5.1.3 Per: TqOscnPer1 9

5.1.3.1 Design Rationale 9

5.1.3.2 Store Module Inputs to Local copies 9

5.1.3.3 (Processing of function)……… 9

5.1.3.4 Store Local copy of outputs into Module Outputs 9

5.2 Server Runnables 9

5.3 Interrupt Functions 9

5.4 Module Internal (Local) Functions 10

5.4.1 Local Function \#1 10

5.4.2 Local Function \#2 10

5.5 GLOBAL Function/Macro Definitions 10

6 Known Limitations with Design 11

7 UNIT TEST CONSIDERATION 12

Appendix A Abbreviations and Acronyms 13

Appendix B Glossary 14

Appendix C References 15

# Introduction

## Purpose

# TqOscn & High-Level Description

Please refer FDD.

# Design details of software module

## Graphical representation of TqOscn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF043A_TqOscn_Impl/doc/mediax/media/image1.png"
style="width:4.31319in;height:5.66111in" />

## Data Flow Diagram

Please refer FDD

### Component level DFD

Please refer FDD

### Function level DFD

Please refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
| Please refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: TqOscnInit1

## Design Rationale

None

## Module Outputs

## None

## Per: TqOscnPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)………

> Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runnables 

None

## Interrupt Functions

> None

## Module Internal (Local) Functions

## Local Function \#1 

|                      |                                           |         |          |         |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | AmpRateLim                                | Type    | Min      | Max     |
| **Arguments Passed** | LimdAmp_MotNwtMtr_T_f32                   | Float32 | 0.0F     | 1.2F    |
|                      | HwOscnRisngRampRate_MotNwtMtrPerSec_T_f32 | Float32 | 0.1F     | 4400.0F |
|                      | HwOscnFallRampRate_MotNwtMtrPerSec_T_f32  | Float32 | -4400.0F | -0.1F   |
|                      | HwOscnEna_Cnt_T_logl                      | Boolean | FALSE    | TRUE    |
|                      | \*NonZeroAmpFlg_Cnt_T_logl                | Boolean | FALSE    | TRUE    |
| **Return Value**     | RateLimdAmp_MotNwtMtr_T_f32               | Float32 | 0.0F     | 1.2F    |

## Local Function \#2

|                      |                          |         |        |        |
|----------------------|--------------------------|---------|--------|--------|
| **Function Name**    | ChkFlg                   | Type    | Min    | Max    |
| **Arguments Passed** | PhaAg_MatRad_T_f32       | Float32 | 0.125F | 0.628F |
| **Return Value**     | TqOscnPhaAg_MatRad_T_f32 | Float32 | 0.0F   | 0.628F |

## GLOBAL Function/Macro Definitions

> None

# Known Limitations with Design

> None

# UNIT TEST CONSIDERATION

> None.

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
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD: SF043A\_ TqOscn_Design                                                                                                                                           | See Synergy sub project version |

{% endraw %}