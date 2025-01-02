---
layout: default
title: MotAgCorrln_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**‘MotAgCorrln’**

**Apr** **14,2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                                     |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                                     | **Author**             | **Version** | **Date**    |
| Initial Version                                                                     | Sankardu Varadapureddi | 1.0         | 22-May-2015 |
| Modified as per latest template EA4 01.00.01 and changes performed for FDD v02.1.01 | Sarika Natu            | 2.0         | 21-Aug-2015 |
| Updated for v 3.0.0 of the FDD                                                      | Selva Sengottaiyan     | 3.0         | 11-Nov-2015 |
| Updated for v 3.1.0 of the FDD                                                      | Krishna Anne           | 4.0         | 19-Mar-2016 |
| Updated for v 4.0.0 of the FDD                                                      | Krishna Anne           | 5.0         | 14-Apr-2016 |

**  
**

<u>Table of Contents</u>

1 Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 MotAgCorrln & High-Level Description 6

3 Design details of software module 7

3.1 Graphical representation of MotAgCorrln 7

3.2 Data Flow Diagram 7

3.2.1 Component level DFD 7

3.2.2 Function level DFD 7

4 Constant Data Dictionary 8

4.1 Program (fixed) Constants 8

4.1.1 Embedded Constants 8

5 Software Component Implementation 9

5.1 Sub-Module Functions 9

5.1.1 Init: MotAgCorrlnInit1 9

5.1.1.1 Design Rationale 9

5.1.1.2 Module Outputs 9

5.1.2 Per: MotAgCorrlnPer1 9

5.1.2.1 Design Rationale 9

5.1.2.2 Store Module Inputs to Local copies 9

5.1.2.3 (Processing of function)……… 9

5.1.2.4 Store Local copy of outputs into Module Outputs 9

5.2 Server Runables 9

5.3 *None*Interrupt Functions 9

5.3.1 Interrupt Function Name 9

5.3.1.1 Design Rationale 9

5.3.1.2 (Processing of the ISR function)….. 9

5.4 Module Internal (Local) Functions 10

5.4.1 Local Function \#1 10

5.4.1.1 Design Rationale 10

5.4.1.2 Processing 10

5.4.2 Local Function \#2 10

5.4.2.1 Design Rationale 10

5.4.2.2 Processing 11

5.4.3 Local Function \#3 11

5.4.3.1 Design Rationale 11

5.4.3.2 Processing 11

5.4.1 Local Function \#2 11

5.4.1.1 Design Rationale 11

5.4.1.2 Processing 11

5.5 GLOBAL Function/Macro Definitions 12

5.5.1 GLOBAL Function \#1 12

5.5.1.1 Design Rationale 12

5.5.1.2 processing 12

6 Known Limitations with Design 13

7 UNIT TEST CONSIDERATION 14

Appendix A Abbreviations and Acronyms 15

Appendix B Glossary 16

Appendix C References 17

# Introduction

## MDD for MotAgCorrln .

## 

-   
-   
-   

# MotAgCorrln & High-Level Description

*None*

# Design details of software module

## Graphical representation of MotAgCorrln

##  [section-1]

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES249A_MotAgCorrln_Impl/doc/mediax/media/image2.png"
style="width:4.44792in;height:4.55972in" />

## Data Flow Diagram

*Refer FDD*

### Component level DFD

*Refer FDD*

### Function level DFD

*Refer FDD*

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                | Resolution | Units | Value |
|------------------------------|------------|-------|-------|
| MOTAGMECLCORRLNSTMIN_CNT_U08 | None       | NA    | 0     |
| MOTAGMECLCORRLNSTMAX_CNT_U08 | None       | NA    | 7     |
| MOTAGMECLIDPTSIGMIN_CNT_U08  | None       | Cnt   | 0     |
| MOTAGMECLIDPTSIGMAX_CNT_U08  | None       | Cnt   | 3     |

# Software Component Implementation

## Sub-Module Functions

## Init: MotAgCorrlnInit1

*Refer FDD*

## Design Rationale

*Design follows implementation in FDD.*

## Module Outputs

*Refer FDD*

## Per: MotAgCorrlnPer1

*Refer FDD*

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer to FDD (Block ‘MotAgCorrlnPer1’)*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

## *None*Interrupt Functions

*None*

## Interrupt Function Name

*None*

## Design Rationale

*None*

## (Processing of the ISR function)…..

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                          |                 |               |               |
|--------------|-----------------------|---------------|-----------|-----------|
| **Function Name**    | MtrAgSigAvlCheck         | Type            | Min           | Max           |
| **Arguments Passed** | SigRollg_Cnt_T_u08       | uint8           | 0             | 255           |
|                      | SigQlfr_Cnt_T_enum       | Enum (SigQlfr1) | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | LstRollg_Cnt_T_u08       | uint8           | 0             | 255           |
|                      | LstStall_Cnt_T_u08       | uint8           | 0             | 255           |
|                      | \*StallCntOutp_Cnt_T_u08 | uint8           | 0             | 255           |
| **Return Value**     | SigAvl_Cnt_T_lgc         | boolean         | FALSE         | TRUE          |

## Design Rationale

Checks Signal Availability of Motor. Implementation of 'MtrAgA
SigAvlCheck', 'MtrAgB SigAvlCheck' and 'MtrAgC SigAvlCheck' blocks.

## Processing

**Note:** ‘\* StallCntOutp_Cnt_T_u08’ is an output of this function.

###  Local Function \#2

|                      |                           |         |       |        |
|----------------------|---------------------------|---------|-------|--------|
| **Function Name**    | TestOkCheck               | Type    | Min   | Max    |
| **Arguments Passed** | MotAgAMecl_MotRev_T_u0p16 | uint16  | 0     | 65535  |
|                      | MotAgBMecl_MotRev_T_u0p16 | uint16  | 0     | 65535  |
|                      | MotAgCMecl_MotRev_T_u0p16 | uint16  | 0     | 65535  |
|                      | \*MotAgOkA_Cnt_T_lgc      | boolean | FALSE | TRUE   |
|                      | \*MotAgOkB_Cnt_T_lgc      | boolean | FALSE | TRUE   |
|                      | \*MotAgOkC_Cnt_T_lgc      | boolean | FALSE | TRUE   |
|                      | \*MotAgABErrTerm_T_u0p16  | uint16  | 0U    | 32768U |
|                      | \*MotAgBCErrTerm_T_u0p16  | uint16  | 0U    | 32768U |
|                      | \*MotAgACErrTerm_T_u0p16  | uint16  | 0U    | 32768U |
| **Return Value**     | None                      |         |       |        |

## Design Rationale

Implementation of 'TestOk' check functionality. This function
corresponds to blocks 'MotAgA vs MotAgB', 'MotAgA vs MotAgC', 'MotAgB vs
MotAgC' and 'TestOk'.

## Processing

‘\*MotAgOkA_Cnt_T_lgc’, ‘\*MotAgOkB_Cnt_T_lgc’ and
‘\*MotAgOkC_Cnt_T_lgc’ are outputs of this function

### Local Function \#3

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | MtrAgNotFailedCheck           | Type    | Min   | Max  |
| **Arguments Passed** | \* MotAgANotFailed_Cnt_T_lgc  | boolean | FALSE | TRUE |
|                      | \* MotAgBNotFailed_Cnt_T_lgc  | boolean | FALSE | TRUE |
|                      | \* MotAgCNotFailed_Cnt_T_lgc  | boolean | FALSE | TRUE |
|                      | \* MotAgMeclIdptSig_Cnt_T_u08 | uint8   | 0     | 3    |
|                      | MotAgSigAvlA_Cnt_T_lgc        | boolean | FALSE | TRUE |
|                      | MotAgSigAvlB_Cnt_T_lgc        | boolean | FALSE | TRUE |
|                      | MotAgSigAvlC_Cnt_T_lgc        | boolean | FALSE | TRUE |
| **Return Value**     | None                          |         |       |      |

## Design Rationale

Implementation of 'NotFailed' block functionality.

MotAgANotFailed_Cnt_T_lgc, MotAgBNotFailed_Cnt_T_lgc,
MotAgCNotFailed_Cnt_T_lgc and MotAgMeclIdptSig_Cnt_T_u08 are outputs of
this function.

## Processing

All arguments are outputs of this function

### Local Function \#2

|                      |                           |        |     |       |
|----------------------|---------------------------|--------|-----|-------|
| **Function Name**    | CalcErrTerm               | Type   | Min | Max   |
| **Arguments Passed** | MotAgAMecl_MotRev_T_u0p16 | uint16 | 0   | 65535 |
|                      | MotAgBMecl_MotRev_T_u0p16 | uint16 | 0   | 65535 |
|                      | MotAgCMecl_MotRev_T_u0p16 | uint16 | 0   | 65535 |
| **Return Value**     | ErrorTerm_Rev_T_u0p16     | uint16 | 0   | 32768 |

## Design Rationale

MotAg“X” vs MotAg“Y” where X can be A,B and Y can be B, C block, the
implementation will not result in negative values as sign of Switch2 and
Abs are changed. Hence Abs1 function is redundant in implementation and
ignored.. (Note: Switch 2 always results in MAX VALUE of U0P16 Datatype.
So Subtraction of delta from it will not result in negative value)

## Processing

Delta between two input motor angle will outputs of this function

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

None

## Design Rationale

None

## processing

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**            |
|-----------------------------|----------------------------|
| FDD                         | Functional Design Document |

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.02                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.02                   |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | EA4 01.00.02                   |
| 5           | ES249A_MotAgCorrln_Design                                                                                                                                             | See Synergy subproject version |

{% endraw %}