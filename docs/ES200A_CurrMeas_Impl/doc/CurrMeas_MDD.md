---
layout: default
title: CurrMeas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**\<Component Name\>**

**November 18, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA** **ELXSI**

**CHENNAI, INDIA**

**<u>Change</u>** History

|             |                                                                              |             |             |                 |
|-----|-----------------------------------|--------------|---------|-----------|
| **Sl. No.** | **Description**                                                              | **Author**  | **Version** | **Date**        |
| 1           | Initial Version                                                              | Selva       | 1.0         | 4- May-2015     |
| 2.0         | Updated to v 3.1.0 of the FDD (Merged CurrMeas_MDD and CurrMeas_MotCtrl_MDD) | Selva       | 2.0         | 29-Sep-2015     |
| 3.0         | Updated per design rev. 4.2.0                                                | Rijvi Ahmed | 3.0         | 30-Mar-2016     |
| 4.0         | Added design limitation and unit test consideration. Design rev. 4.5.0       | Rijvi Ahmed | 4.0         | 05-October-2016 |
| 5.0         | Updated per design rev. 4.6.0                                                | TATA        | 5.0         | 18-Nov-2016     |
|             |                                                                              |             |             |                 |

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1.1 Purpose 5](#purpose)

[2 Current Measurement & High-Level Description
6](#component-name-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1.1 Data Flow Diagram 7](#data-flow-diagram)

[3.1.2 Component level DFD 7](#component-level-dfd)

[3.1.3 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.2 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#__RefHeading___Toc467524078)

[5.2 INIT: CurrMeasInit1 9](#__RefHeading___Toc467524079)

[5.3 PERIODIC FUNCTIONS 9](#periodic-functions)

[5.3.2 Per: CurrMeasPer2 10](#per-currmeasper2)

[5.3.3 Per: CurrMeasPer3 10](#per-currmeasper3)

[5.4 Server Runables 10](#server-runables)

[5.4.1 Serverrunnable: CurrMeasEolGainSTsReq
10](#serverrunnable-currmeaseolgainstsreq)

[5.4.2 Serverrunnable: CurrMeasEoloffsSTsReq
10](#serverrunnable-currmeaseoloffsstsreq)

[5.4.3 Serverrunnable: CurrMeasEoloffsReq
10](#serverrunnable-currmeaseoloffsreq)

[5.4.4 Serverrunnable: CurrMeasEolGainReq
11](#serverrunnable-currmeaseolgainreq)

[5.4.5 Serverrunnable: CurrMeasGainReadReq
11](#serverrunnable-currmeasgainreadreq)

[5.4.6 Serverrunnable: CurrMeasGainWrReq
11](#serverrunnable-currmeasgainwrreq)

[5.4.7 Serverrunnable: CurrMeasOffsReadReq
11](#serverrunnable-currmeasoffsreadreq)

[5.4.8 Serverrunnable: CurrMeasOffsWrReq
11](#serverrunnable-currmeasoffswrreq)

[5.5 Module Internal (Local) Functions
12](#module-internal-local-functions)

[5.5.1 Local Function \#1 PerformGainCalibration
12](#local-function-1-performgaincalibration)

[5.5.2 Local Function \#2 SigMaxMinGain
12](#local-function-2-sigmaxmingain)

[5.5.3 Local Function \#3 SigMaxMinOffs
12](#local-function-3-sigmaxminoffs)

[5.5.4 Local Function \#4 ProtocolChkWI
12](#local-function-4-protocolchkwi)

[5.5.5 Local Function \#1 ProtocolChkEn
13](#local-function-1-protocolchken)

[5.5.6 Local Function \#2 CalcMotCurrMotAgCorrd
13](#local-function-2-calcmotcurrmotagcorrd)

[5.5.7 Local Function \#3 OffsCalcABC 13](#local-function-3-offscalcabc)

[5.5.8 Local Function \#4 OffsCalcDEF 14](#local-function-4-offscalcdef)

[5.5.9 Local Function \#5 CalMotCurrCorrdABC
14](#local-function-5-calmotcurrcorrdabc)

[5.5.10 Local Function \#6 CalMotCurrCorrdDEF
15](#local-function-6-calmotcurrcorrddef)

[6 GLOBAL Function/Macro Definitions
16](#global-functionmacro-definitions)

[7 Known Limitations with Design 17](#known-limitations-with-design)

[8 UNIT TEST CONSIDERATION 18](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 19](#abbreviations-and-acronyms)

[Appendix B Glossary 20](#glossary)

[Appendix C References 22](#references)

# Introduction

## Purpose

MDD for Current Measurement

# \<Component Name\> & High-Level Description

*Refer FDD Design for Current Measurement*

# Design details of software module

Graphical representation of \<Component Name\>

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES200A_CurrMeas_Impl/doc/mediax/media/image1.png"
style="width:3.76667in;height:5.75833in" />

## Data Flow Diagram

## Component level DFD

None

## Function level DFD

None

# Constant Data Dictionary

## Program (fixed) Constants

## Embedded Constants

#### Local Constants

|                                                 |                                                 |                                                 |                                                 |
|---------------------------------|---------------|-----------|-------------|
| Constant Name                                   | Resolution                                      | Units                                           | Value                                           |
| CALPROCNOTSTRTD_CNT_U08                         | 1                                               | Cnt                                             | 0                                               |
| CALPROCSTRTD_CNT_U08                            | 1                                               | Cnt                                             | 1                                               |
| CALPROCPASS_CNT_U08                             | 1                                               | Cnt                                             | 2                                               |
| CALPROCPHAABCEOLOUTOFRNG_CNT_U08                | 1                                               | Cnt                                             | 4                                               |
| CALPROCPHADEFEOLOUTOFRNG_CNT_U08                | 1                                               | Cnt                                             | 8                                               |
| CALPROCPHAABCDEFEOLOUTOFRNG_CNT_U08             | 1                                               | Cnt                                             | 12                                              |
| CALPROCVEHSPDCNDNOTMET_CNT_U08                  | 1                                               | Cnt                                             | 16                                              |
| CALPROCMOTVELMRFCNDNOTMET_CNT_U08               | 1                                               | Cnt                                             | 32                                              |
| CALPROCBOTHIVTRINACTV_CNT_U08                   | 1                                               | Cnt                                             | 64                                              |
| DIFOFFSRNGCHKMAX_VOLT_F32                       | Single precision float                          | Ampr                                            | 1.0                                             |
| DIFOFFSRNGCHKMIN_VOLT_F32                       | Single precision float                          | Ampr                                            | -1.0                                            |
| NANOSECTOSEC_ULS_F32                            | float32                                         | Uls                                             | 0.000000001                                     |
| Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants | Refer DataDict.m file for other local constants |

# Software Component Implementation

1.  <span id="__RefHeading___Toc467524078"
    class="anchor"></span>Sub-Module Functions

2.  <span id="__RefHeading___Toc467524079" class="anchor"></span>INIT:
    CurrMeasInit1

#### Design Rationale

Init1 function is created so that it will allow a RTE model to be
created in the AUTOSAR tools which allows Per-Instance Memory and
calibration definition needs. The initialization function is doing
nothing

#### Store Module Inputs to Local copies

None

####  (Processing of function)………

None

#### Store Local copy of outputs into Module Outputs

None

## PERIODIC FUNCTIONS 

*(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “ Periodic Functions” and follow the same
sub-section design shown below). If none required, place the text
“None”)\>*

#### Per: CurrMeasPer1

#### Design Rationale

Refer the FDD

#### Store Module Inputs to Local copies

####  (Processing of function)………

Refer the FDD

#### Store Local copy of outputs into Module Outputs

> Refer the FDD

## Per: CurrMeasPer2

#### Design Rationale

*Refer to FDD*

#### Store Module Inputs to Local copies

*Refer to FDD*

#### (Processing of function)………

*Refer to FDD*

#### Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: CurrMeasPer3

#### Design Rationale

*Refer to FDD*

#### Store Module Inputs to Local copies

*Refer to FDD*

#### (Processing of function)………

*Refer to FDD*

#### Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

## Serverrunnable: CurrMeasEolGainSTsReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasEoloffsSTsReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasEoloffsReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasEolGainReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasGainReadReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasGainWrReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasOffsReadReq

#### Design Rationale

Refer the FDD

## Serverrunnable: CurrMeasOffsWrReq

#### Design Rationale

Refer the FDD

##  [section]

## Module Internal (Local) Functions

## Local Function \#1 PerformGainCalibration

|                   |                        |      |     |     |
|-------------------|------------------------|------|-----|-----|
| **Function Name** | PerformGainCalibration | Type | Min | Max |
| **Arguments**     | None                   |      |     |     |
|                   |                        |      |     |     |
|                   |                        |      |     |     |
| **Return Value**  | None                   |      |     |     |

#### Description

Refer FDD.

## Local Function \#2 SigMaxMinGain

|                   |               |      |     |     |
|-------------------|---------------|------|-----|-----|
| **Function Name** | SigMaxMinGain | Type | Min | Max |
| **Arguments**     | None          |      |     |     |
|                   |               |      |     |     |
|                   |               |      |     |     |
| **Return Value**  | None          |      |     |     |

#### Description

Refer FDD.

## Local Function \#3 SigMaxMinOffs

|                   |               |      |     |     |
|-------------------|---------------|------|-----|-----|
| **Function Name** | SigMaxMinOffs | Type | Min | Max |
| **Arguments**     | None          |      |     |     |
|                   |               |      |     |     |
|                   |               |      |     |     |
| **Return Value**  | None          |      |     |     |

#### Description

Refer FDD.

## Local Function \#4 ProtocolChkWI

|                   |                                  |         |       |      |
|-------------------|----------------------------------|---------|-------|------|
| **Function Name** | ProtocolChkWI                    | Type    | Min   | Max  |
|                   | MotCtrlMotCurrAdcVly1_Volt_T_f32 | float32 | 0.3   | 4.8  |
|                   | MotCtrlMotCurrAdcVly2_Volt_T_f32 | float32 | 0.3   | 4.8  |
|                   | MotCtrlMotCurrAdcVly3_Volt_T_f32 | float32 | 0.3   | 4.8  |
| **Return Value**  | ProtocolChk_Cnt_T_logl           | boolean | FALSE | TRUE |

#### Description

Refer FDD.

##  [section-1]

## Local Function \#1 ProtocolChkEn

|                      |                                          |         |       |      |
|-------------|-----------------------------|----------|-----------|----------|
| **Function Name**    | ProtocolChkEn                            | Type    | Min   | Max  |
| **Arguments Passed** | MotCtrlMotCurrAdcVly1AdcFaild_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | MotCtrlMotCurrAdcVly2AdcFaild_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | MotCtrlMotCurrAdcVly3AdcFaild_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | ProtocolChkEn_Cnt_T_logl                 | boolean | FALSE | TRUE |

#### Description

Refer FDD.

## Local Function \#2 CalcMotCurrMotAgCorrd

|                   |                                      |         |       |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name** | CalcMotCurrMotAgCorrd                | Type    | Min   | Max   |
|                   | MotCtrlMotAgElec_Rev_T_u0p16         | u0p16   | 0     | 65535 |
|                   | MotCtrlMotElecMeclPolarity_Uls_T_s08 | Sint8   | -1    | 1     |
|                   | MotCtrlMotVelMrf_MtrRadpS_T_f32      | float32 | -1350 | 1350  |
| **Return Value**  | MotCtrlCurrMeasMotAgCorrd_Rad_T_f32  | float32 | -6.28 | 6.28  |

#### Description

Refer FDD.

MotCtrlMotElecMeclPolarity_Uls_T_s08 takes -1 and +1 as its values

## Local Function \#3 OffsCalcABC

|                   |                               |         |     |       |
|-------------------|-------------------------------|---------|-----|-------|
| **Function Name** | OffsCalcABC                   | Type    | Min | Max   |
| **Arguments**     | MotCtrlBrdgVltg_Volt_T_f32    | float32 | 6   | 26.5  |
|                   | MotCtrlPhaOnTiA_NanoSec_T_u32 | uint32  | 0   | 71429 |
|                   | MotCtrlPhaOnTiB_NanoSec_T_u32 | uint32  | 0   | 71429 |
|                   | MotCtrlPhaOnTiC_NanoSec_T_u32 | uint32  | 0   | 71429 |
| **Return Value**  | \*MotCurrOffsA_Volt_T_f32     | float32 | 0   | 5     |
|                   | \*MotCurrOffsB_Volt_T_f32     | float32 | 0   | 5     |
|                   | \*MotCurrOffsC_Volt_T_f32     | float32 | 0   | 5     |

#### Description

Refer FDD.

## Local Function \#4 OffsCalcDEF

|                   |                               |         |     |       |
|-------------------|-------------------------------|---------|-----|-------|
| **Function Name** | OffsCalcDEF                   | Type    | Min | Max   |
| **Arguments**     | MotCtrlBrdgVltg_Volt_T_f32    | float32 | 6   | 26.5  |
|                   | MotCtrlPhaOnTiA_NanoSec_T_u32 | uint32  | 0   | 71429 |
|                   | MotCtrlPhaOnTiB_NanoSec_T_u32 | uint32  | 0   | 71429 |
|                   | MotCtrlPhaOnTiC_NanoSec_T_u32 | uint32  | 0   | 71429 |
| **Return Value**  | \*MotCurrOffsD_Volt_T_f32     | float32 | 0   | 5     |
|                   | \*MotCurrOffsE_Volt_T_f32     | float32 | 0   | 5     |
|                   | \*MotCurrOffsF_Volt_T_f32     | float32 | 0   | 5     |

#### Description

Refer FDD.

## Local Function \#5 CalMotCurrCorrdABC

|                   |                         |         |      |     |
|-------------------|-------------------------|---------|------|-----|
| **Function Name** | CalMotCurrCorrdABC      | Type    | Min  | Max |
|                   | MotCurrOffsA_Volt_T_f32 | float32 | 0    | 5   |
|                   | MotCurrOffsB_Volt_T_f32 | float32 | 0    | 5   |
|                   | MotCurrOffsC_Volt_T_f32 | float32 | 0    | 5   |
| **Return Value**  | MotCtrlMotCurrCorrdA    | float32 | -200 | 200 |
|                   | MotCtrlMotCurrCorrdB    | float32 | -200 | 200 |
|                   | MotCtrlMotCurrCorrdC    | float32 | -200 | 200 |

#### Description

Refer FDD.

Note: MotCtrlMotCurrCorrdA, MotCtrlMotCurrCorrdB, MotCtrlMotCurrCorrdC
are not updated every runnable loop as Motor Control Manager should
retain its last known good value.

## Local Function \#6 CalMotCurrCorrdDEF

|                   |                         |         |      |     |
|-------------------|-------------------------|---------|------|-----|
| **Function Name** | CalMotCurrCorrdDEF      | Type    | Min  | Max |
|                   | MotCurrOffsD_Volt_T_f32 | float32 | 0    | 5   |
|                   | MotCurrOffsE_Volt_T_f32 | float32 | 0    | 5   |
|                   | MotCurrOffsF_Volt_T_f32 | float32 | 0    | 5   |
| **Return Value**  | MotCtrlMotCurrCorrdD    | float32 | -200 | 200 |
|                   | MotCtrlMotCurrCorrdE    | float32 | -200 | 200 |
|                   | MotCtrlMotCurrCorrdF    | float32 | -200 | 200 |

#### Description

Note: MotCtrlMotCurrCorrdA, MotCtrlMotCurrCorrdB, MotCtrlMotCurrCorrdC
are not updated every runnable loop as Motor Control Manager should
retain its last known good value.

## Local Function \#7 McecsOffsCmdStrtandHi

|                   |                       |      |     |     |
|-------------------|-----------------------|------|-----|-----|
| **Function Name** | McecsOffsCmdStrtandHi | Type | Min | Max |
| **Inputs**        | NA                    | NA   | NA  | NA  |
| **Return Value**  | NA                    | NA   | NA  | NA  |

#### Description

Note: This function corresponds to MCECS_OFFSCMDSTRT and MCECS_OFFSCMDHI
cases in Per1

## Local Function \#8 McecsOffsCmdEndandAd

|                   |                      |      |     |     |
|-------------------|----------------------|------|-----|-----|
| **Function Name** | McecsOffsCmdEndandAd | Type | Min | Max |
| **Inputs**        | NA                   | NA   | NA  | NA  |
| **Return Value**  | NA                   | NA   | NA  | NA  |

#### Description

Note: This function corresponds to MCECS_OFFSCMDEND and MCECS_GAINCMDAD
cases in PerformGainCalibration()

# GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

1.  In the implementation of Simulink block “**CurrMeasPer2**” the
    source code has made a decision to implement the protocol checks
    first then the motor control based timing checks. This leads to a
    scenario where the counter **PhaOnTiErrCnt** will only get
    incremented when the ABC passes the protocol check, whereas the
    model will increment it regardless of protocol check status. This
    counter is in effect used for display purposes only. So it’s okay to
    keep this mismatch.

# UNIT TEST CONSIDERATION

1.  In the function **CalMotCurrCorrdABC** variables
    MotCtrlPhaOnTiA_NanoSec_T_u32, MotCtrlPhaOnTiB_NanoSec_T_u32 and
    MotCtrlPhaOnTiC_NanoSec_T_u32 are a percentage of
    MotCtrlPwmPerd_NanoSec_T_u32, 100% is the maximum. Therefore never
    use a value for MotCtrlPhaOnTiA_NanoSec_T_u32,
    MotCtrlPhaOnTiB_NanoSec_T_u32 and MotCtrlPhaOnTiC_NanoSec_T_u32
    which is greater than MotCtrlPwmPerd_NanoSec_T_u32.

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
| 5           | Current Meaurement Design ES200A_CurrMeas_Design                                                                                                              | See Synergy subversion |

{% endraw %}