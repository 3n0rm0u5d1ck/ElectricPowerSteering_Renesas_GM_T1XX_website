---
layout: default
title: CurrMeasCorrln_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Current Measurement Correlation**

**April 13, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                                                                  |            |             |              |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                  | **Author** | **Version** | **Date**     |
| Initial Version                                                  | Selva      | 1.0         | 09- Apr-2015 |
| Updated for v2.1.0 of Design                                     | Selva      | 2.0         | 21 –Sep 2015 |
| Updated graphical representation                                 | Nick S.    | 3.0         | 13-Apr-2016  |
| Updated graphical representation with added fault injection port | Nick S.    | 4.0         | 06-Sep-2016  |

<u>Table of Contents</u>

[**1** **Introduction 4**](#introduction)

[1.1 Purpose 4](#purpose)

[1.2 Scope 4](#scope)

[2 Current Measurement Correlation & High-Level Description
5](#current-measurement-correlation-high-level-description)

[3 Design details of software module
6](#design-details-of-software-module)

[3.1 Graphical representation of Current Measurement Correlation
6](#graphical-representation-of-current-measurement-correlation)

[3.2 Data Flow Diagram 6](#data-flow-diagram)

[3.2.1 Component level DFD 6](#component-level-dfd)

[3.2.2 Function level DFD 6](#function-level-dfd)

[4 Constant Data Dictionary 7](#constant-data-dictionary)

[4.1 Program (fixed) Constants 7](#program-fixed-constants)

[4.1.1 Embedded Constants 7](#embedded-constants)

[4.1.1.1 Local 7](#local)

[5 Software Component Implementation
8](#software-component-implementation)

[5.1 Sub-Module Functions 8](#sub-module-functions)

[5.1.1 Initialization Functions 8](#initialization-functions)

[5.1.1.1 INIT 8](#init)

[5.1.1.2 Design Rationale 8](#design-rationale)

[5.1.1.3 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies)

[5.1.1.4 (Processing of function)……… 8](#processing-of-function)

[5.1.1.5 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs)

[5.1.2 PERIODIC FUNCTIONS 8](#periodic-functions)

[5.1.2.1 Per: CurrMeasCorrlnPer1 8](#per-currmeascorrlnper1)

[5.1.2.2 Design Rationale 8](#design-rationale-1)

[5.1.2.3 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies-1)

[5.1.2.4 (Processing of function)……… 8](#processing-of-function-1)

[5.1.2.5 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables 8](#server-runables)

[5.3 Interrupt Functions 8](#interrupt-functions)

[5.4 Module Internal (Local) Functions
9](#module-internal-local-functions)

[5.5 Local Function/Macro Definitions
9](#local-functionmacro-definitions)

[5.5.1 Local Function \#1 SigAvlCheck 9](#local-function-1-sigavlcheck)

[5.5.1.1 Description 9](#description)

[5.5.2 Local Function \#1 CurrMeasCorrlnChk
9](#local-function-1-currmeascorrlnchk)

[5.5.2.1 Description 9](#description-1)

[5.6 GLOBAL Function/Macro Definitions
9](#global-functionmacro-definitions)

[6 Known Limitations with Design 11](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 16](#references)

# Introduction

## Purpose

None

## Scope

-   None

# Current Measurement Correlation & High-Level Description

Current Measurement Correlation determines number of independent current
measurement channels available and also correlation status of those
channels.

Refer the Design for high level Description

# Design details of software module

*None*

## Graphical representation of Current Measurement Correlation

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES209A_CurrMeasCorrln_Impl/doc/mediax/media/image2.png"
style="width:4.88542in;height:4.71875in" />

## Data Flow Diagram

### Component level DFD

None

### Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

## Local

|                         |       |       |
|-------------------------|-------|-------|
| Constant Name           | Units | Value |
| CORRLNSTSABC_CNT_U08    | Cnt   | 0x07  |
| CORRLNSTSDEF_CNT_U08    | Cnt   | 0x38  |
| MAXVALSIGSTALL_CNT_U08  | Cnt   | 255   |
| CURRMOTSUMLOLIM_AMP_F32 | Amp   | 0.0   |
| CURRMOTSUMHILIM_AMP_F32 | Amp   | 600.0 |

# Software Component Implementation

## Sub-Module Functions

## Initialization Functions

## INIT

None

## Design Rationale

None

## Store Module Inputs to Local copies

None

##  (Processing of function)………

None

## Store Local copy of outputs into Module Outputs

None

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “ Periodic Functions” and follow the same
sub-section design shown below). If none required, place the text
“None”)\>*

## Per: CurrMeasCorrlnPer1

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function/Macro Definitions

## Local Function \#1 SigAvlCheck

|                      |                                    |          |               |               |
|-------------|------------------------------|--------|-----------|-----------|
| **Function Name**    | SigAvlCheck                        | Type     | Min           | Max           |
| **Arguments Passed** | CurrMeasSigQlfr_T_enum             | SigQlfr1 | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | CurrMeasSigRollgCntr_Cnt_T_u08     | uint8    | 0             | 255           |
|                      | PrevCurrMeasSigRollgCntr_Cnt_T_u08 | uint8    | 0             | 255           |
|                      | CurrMeasSigStall_Cnt_T_u08         | uint8    | 0             | 255           |
| **Return Value**     | SignalAvailable_Cnt_T_logl         | boolean  | FALSE         | TRUE          |

## Description

Refer FDD.

## Local Function \#1 CurrMeasCorrlnChk

|                      |                                               |         |       |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CurrMeasCorrlnChk                             | Type    | Min   | Max   |
| **Arguments Passed** | MotCurrCorrdSig1_Amp_T_f32                    | float32 | -200  | 200   |
|                      | MotCurrCorrdSig2_Amp_T_f32                    | float32 | -200  | 200   |
|                      | MotCurrCorrdSig3_Amp_T_f32                    | float32 | -200  | 200   |
|                      | CurrMeasCorrlnNtcFailStep                     | uint16  | 0     | 65535 |
|                      | CurrMeasCorrlnNtcPassStep                     | uint16  | 0     | 65535 |
|                      | NtcNr_T_enum                                  | NtcNr1  | 0x4D  | 0x4E  |
|                      | \*CurrMeasLongTermCorrlnStsVldSig1_Cnt_T_logl | boolean | FALSE | TRUE  |
|                      | \*CurrMotSum_Amp_T_f32                        | float32 | 0.0   | 600.0 |
| **Return Value**     | CurrMeasImdtCorrlnStsVldSig1_Cnt_T_logl       | boolean | FALSE | TRUE  |

## Description

Refer FDD.

In FDD, there are two sub functions CorrlnChkABC and CorrlnChkDEF but
the both functions are functionally same other than the NTCs. Hence the
software merges these functions in single function with NTC as
parameter.

\*CurrMeasLongTermCorrlnStsVldSig1_Cnt_T_logl and \*CurrMotSum_Amp_T_f32
are outputs of this function.

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**            |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2      |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00           |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                    |
| 5           | FDD - ES209A Current Measurement Correlation                                                                                                                  | See synergy subversion |

{% endraw %}