---
layout: default
title: LoaMgr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**LoaMgr**

**Nov 30, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**CHENNAI, INDIA** **  
<u>Change History</u>**

|                                 |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                 | **Author**             | **Version** | **Date**    |
| Initial Version                 | Sankardu Varadapureddi | 1           | 04-Aug-2015 |
| Updated to design version 2.0.0 | Sarika Natu            | 2           | 22-Jun-16   |
| Updated to design version 2.1.0 | TATA                   | 3           | 30-Nov-16   |

**  
**

<u>Table of Contents</u>1 Introduction 5

1.1 Purpose 5

2 LoaMgr High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of LoaMgr 7

3.2 Data Flow Diagram 8

3.2.1 Component level DFD 8

3.2.2 Function level DFD 8

4 Constant Data Dictionary 9

4.1 Program (fixed) Constants 9

4.1.1 Embedded Constants 9

5 Software Component Implementation 10

5.1 Sub-Module Functions 10

5.1.1 Init: LoaMgrInit1 10

5.1.1.1 Design Rationale 10

5.1.1.2 Module Outputs 10

5.1.2 Per: LoaMgrPer1 10

5.1.2.1 Design Rationale 10

5.1.2.2 Store Module Inputs to Local copies 10

5.1.2.3 (Processing of function)……… 10

5.1.2.4 Store Local copy of outputs into Module Outputs 10

5.2 Server Runables 10

5.3 Interrupt Functions 10

5.4 Module Internal (Local) Functions 10

5.4.1 Local Function \#1 10

5.4.1.1 Design Rationale 10

5.4.1.2 Processing 11

5.4.2 Local Function \#2 11

5.4.2.1 Design Rationale 11

5.4.2.2 Processing 11

5.4.3 Local Function \#3 11

5.4.3.1 Design Rationale 11

5.4.3.2 Processing 11

5.4.4 Local Function \#4 11

5.4.4.1 Design Rationale 11

5.4.4.2 Processing 11

5.4.5 Local Function \#5 12

5.4.5.1 Design Rationale 12

5.4.5.2 Processing 12

5.4.6 Local Function \#6 12

5.4.6.1 Design Rationale 12

5.4.6.2 Processing 12

5.4.7 Local Function \#7 12

5.4.7.1 Design Rationale 12

5.4.7.2 Processing 13

5.4.8 Local Function \#8 13

5.4.8.1 Design Rationale 13

5.4.8.2 Processing 13

5.5 GLOBAL Function/Macro Definitions 13

6 Known Limitations with Design 14

7 UNIT TEST CONSIDERATION 15

Appendix A Abbreviations and Acronyms 16

Appendix B Glossary 17

Appendix C References 18

# Introduction

## Purpose

## 

> MDD for Loss of Assist Manager

# LoaMgr High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of LoaMgr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF049A_LoaMgr_Impl/doc/mediax/media/image2.jpeg"
style="width:4.72917in;height:5.98958in"
alt="C:\Users\ramachandran.mg\Desktop\SF049A_LoaMgr_Impl_2.1.0\MDD_Image.JPG" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| Refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: LoaMgrInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: LoaMgrPer1

## Design Rationale

*Refer FDD*

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

|                      |                       |         |       |      |
|----------------------|-----------------------|---------|-------|------|
| **Function Name**    | ReqHwTqResp           | Type    | Min   | Max  |
| **Arguments Passed** | HwTqIdptMin_Cnt_T_u08 | uint8   | 0     | 4    |
|                      | TqLoaAvl_Cnt_T_lgc    | boolean | FALSE | TRUE |
| **Return Value**     | HwTqResp_Cnt_T_u08    | uint8   | 0     | 5    |

## Design Rationale

None

## Processing

Refer to ‘HwTqResp’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Request_Responses’

## Local Function \#2

|                      |                           |         |       |      |
|----------------------|---------------------------|---------|-------|------|
| **Function Name**    | ReqMotAgResp              | Type    | Min   | Max  |
| **Arguments Passed** | MotAgIdptMin_Cnt_T_u08    | uint8   | 0     | 3    |
|                      | MotAgSnsrlsAvl_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | MotAgResp_Cnt_T_u08       | uint8   | 0     | 5    |

## Design Rationale

None

## Processing

Refer to ‘MotAgResp’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Request_Responses’

## Local Function \#3

|                      |                           |       |     |     |
|----------------------|---------------------------|-------|-----|-----|
| **Function Name**    | ReqCurrMeasResp           | Type  | Min | Max |
| **Arguments Passed** | CurrMeasIdptMin_Cnt_T_u08 | uint8 | 0   | 2   |
| **Return Value**     | CurrMeasResp_Cnt_T_u08    | uint8 | 0   | 5   |

## Design Rationale

None

## Processing

Refer to ‘CurrMeasResp’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Request_Responses’

## Local Function \#4

|                      |                       |       |     |     |
|----------------------|-----------------------|-------|-----|-----|
| **Function Name**    | ReqInvtrResp          | Type  | Min | Max |
| **Arguments Passed** | IvtrIdptMin_Cnt_T_u08 | uint8 | 0   | 2   |
| **Return Value**     | InvtrResp_Cnt_T_u08   | uint8 | 0   | 5   |

## Design Rationale

None

## Processing

Refer to ‘CurrMeasResp’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Request_Responses’

## Local Function \#5

|                      |                        |         |       |      |
|----------------------|------------------------|---------|-------|------|
| **Function Name**    | CntSwBasdMtgtnChk      | Type    | Min   | Max  |
| **Arguments Passed** | Resp_Cnt_T_u08         | uint8   | 0     | 5    |
|                      | PrevMtgtnEna_Cnt_T_lgc | boolean | FALSE | TRUE |
| **Return Value**     | MtgtnEna_Cnt_T_lgc     | boolean | FALSE | TRUE |

## Design Rationale

None

## Processing

This function corresponds to common logic (for all requests) in
‘CntSwBasdMtgtn’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Arbitrate_Responses’

## Local Function \#6

|                      |                          |        |     |     |
|----------------------|--------------------------|--------|-----|-----|
| **Function Name**    | SelFinalResp             | Type   | Min | Max |
| **Arguments Passed** | MultiMtgtnResp_Cnt_T_u08 | uint8  | 0   | 5   |
|                      | HwTqResp_Cnt_T_u08       | uint8  | 0   | 5   |
|                      | MotAgResp_Cnt_T_u08      | uint8  | 0   | 5   |
|                      | CurrMeasResp_Cnt_T_u08   | uint8  | 0   | 5   |
|                      | InvtrResp_Cnt_T_u08      | uint8  | 0   | 5   |
| **Return Value**     | LoaSt_Cnt_T_enum         | LoaSt1 | 0   | 5   |

## Design Rationale

None

## Processing

This function corresponds to ‘SelFinalResp’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Arbitrate_Responses’

## Local Function \#7

|                      |                           |        |     |     |
|----------------------|---------------------------|--------|-----|-----|
| **Function Name**    | SetFaults                 | Type   | Min | Max |
| **Arguments Passed** | LoaSt_Cnt_T_enum          | LoaSt1 | 0   | 5   |
|                      | HwTqIdptMin_Cnt_T_u08     | uint8  | 0   | 4   |
|                      | MotAgIdptMin_Cnt_T_u08    | uint8  | 0   | 3   |
|                      | CurrMeasIdptMin_Cnt_T_u08 | uint8  | 0   | 2   |
|                      | IvtrIdptMin_Cnt_T_u08     | uint8  | 0   | 2   |
| **Return Value**     | None                      |        |     |     |

## Design Rationale

None

## Processing

This function corresponds to ‘Set_Faults’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1’

## Local Function \#8

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | SwMtgtnEn                     | Type    | Min   | Max  |
| **Arguments Passed** | HwTqLoaMtgtnEna_Cnt_T_lgc     | boolean | FALSE | TRUE |
|                      | MotAgLoaMtgtnEna_Cnt_T_lgc    | boolean | FALSE | TRUE |
|                      | CurrMeasLoaMtgtnEna_Cnt_T_lgc | boolean | FALSE | TRUE |
|                      | IvtrLoaMtgtnEna_Cnt_T_lgc     | boolean | FALSE | TRUE |
|                      | \*LoaSca_Uls_T_f32            | float32 | 0     | 1    |
|                      | \*LoaRateLim_UlsPerSec_T_f32  | float32 | 0.01  | 500  |
| **Return Value**     | None                          |         |       |      |

## Design Rationale

None

## Processing

This function corresponds to ‘SwMtgtn’ block in FDD at
‘SF049A_LoaMgr/LoaMgr/LoaMgrPer1/Assign_Scale’.

Note that ‘\*LoaSca_Uls_T_f32’ and ‘\*LoaRateLim_UlsPerSec_T_f32’ are
the outputs of this function.

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
| 5           | FDD : SF049A_LoaMgr_Design                                                                                                                                            | See Synergy sub project version |

{% endraw %}