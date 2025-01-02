---
layout: default
title: StHlthSigNormn_MDD
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**State of Health Signal Normalization**

**June 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|             |                       |                      |             |             |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**       | **Author**           | **Version** | **Date**    |
| 1           | Initial Version       | Akilan Rathakrishnan | 1.0         | 09-Feb-2016 |
| 2           | Updated for EA4# 5445 | Akilan Rathakrishnan | 2.0         | 02-May-2016 |
| 3           | Updated for EA4#7305  | Akilan Rathakrishnan | 3.0         | 27-Sep-2016 |

<u>Table of Contents</u>

[**1** **StHlthSignNormn High-Level Description**
**5**](#sthlthsignnormn-high-level-description)

[2 Design details of software module
6](#design-details-of-software-module)

[2.1.1.1 Graphical representation of StHlthSigNormn
6](#graphical-representation-of-sthlthsignormn)

[2.1.1.2 Data Flow Diagram 7](#data-flow-diagram)

[2.1.2 Component level DFD 8](#component-level-dfd)

[2.1.3 Function level DFD 8](#function-level-dfd)

[3 Constant Data Dictionary 9](#constant-data-dictionary)

[3.1.1.1 Program (fixed) Constants 9](#program-fixed-constants)

[3.1.2 Embedded Constants 9](#embedded-constants)

[4 Software Component Implementation
10](#software-component-implementation)

[4.1.1 Sub-Module Functions 10](#sub-module-functions)

[4.1.1.1 Init: StHlthSigNormnInit1 10](#init-sthlthsignormninit1)

[4.1.1.2 Per: None 10](#per-none)

[4.1.2 Interrupt Service Routines 10](#interrupt-service-routines)

[4.1.3 Server Runnable Functions 10](#server-runnable-functions)

[4.1.3.1 UpdRawSig 10](#updrawsig)

[4.1.3.1.1 Design Rationale 10](#design-rationale-1)

[4.1.3.1.2 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies)

[4.1.3.1.3 (Processing of function)……… 10](#processing-of-function)

[4.1.3.1.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs)

[4.1.4 Module Internal (Local) Functions
11](#module-internal-local-functions)

[4.1.4.1 Local Function \#1 11](#local-function-1)

[4.1.4.1.1 Description 11](#description)

[4.1.4.2 Local Function \#2 Rationale 11](#local-function-2-rationale)

[4.1.4.2.1 Description 11](#description-1)

[4.1.4.3 Local Function \#3 Rationale 11](#local-function-3-rationale)

[4.1.4.3.1 Description 11](#description-2)

[4.1.4.4 Local Function \#4 Rationale 12](#local-function-4-rationale)

[4.1.4.4.1 Description 12](#description-3)

[4.1.4.5 Local Function \#5 Rationale 12](#local-function-5-rationale)

[4.1.4.5.1 Description 12](#description-4)

[4.1.4.6 Local Function \#6 Rationale 12](#local-function-6-rationale)

[4.1.4.6.1 Description 12](#description-5)

[4.1.4.7 Local Function \#7 Rationale 12](#local-function-7-rationale)

[4.1.4.7.1 Description 13](#description-6)

[4.1.4.8 Local Function \#8 Rationale 13](#local-function-8-rationale)

[4.1.4.8.1 Description 13](#description-7)

[4.1.4.9 Local Function \#9 Rationale 13](#local-function-9-rationale)

[4.1.4.9.1 Description 13](#description-8)

[4.1.4.10 Local Function \#10 Rationale
13](#local-function-10-rationale)

[4.1.4.10.1 Description 13](#description-9)

[4.1.4.11 Local Function \#11 Rationale
14](#local-function-11-rationale)

[4.1.4.11.1 Description 14](#description-10)

[4.1.4.12 Local Function \#12 Rationale
14](#__RefHeading___Toc462826298)

[4.1.4.12.1 Description 14](#__RefHeading___Toc462826299)

[4.1.4.13 Local Function \#13 Rationale
14](#__RefHeading___Toc462826300)

[4.1.4.13.1 Description 14](#__RefHeading___Toc462826301)

[4.1.5 Transition Functions 14](#transition-functions)

[5 Known Limitations with Design 15](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION 16](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 17](#abbreviations-and-acronyms)

[Appendix B Glossary 18](#glossary)

[Appendix C References 19](#references)

# StHlthSignNormn High-Level Description

This component acts as an interface component between ES106A (State of
Health Signal Statistics) and rest of the components from which signals
need to be monitored. It reads data or status values from different
components, applies normalization algorithm to convert it as State of
Health information which will be in the scale of 0 to 100. It also
provides auxiliary output for some signals to indicate the additional
information about monitored signals.

# Design details of software module

*See FDD.*

## Graphical representation of StHlthSigNormn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES105A_StHlthSigNormn_Impl/doc/mediax/media/image2.png"
style="width:4.07292in;height:8.34375in" />

## Data Flow Diagram

See FDD.

### Component level DFD

See FDD.

### Function level DFD

See FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                      |            |         |        |
|--------------------------------------|------------|---------|--------|
| Constant Name                        | Resolution | Units   | Value  |
| TMAXRNGVAL_CNT_U08                   | 1          | Cnt     | 15     |
| VLTGMAXRNGVAL_CNT_U08                | 1          | Cnt     | 15     |
|                                      |            |         |        |
|                                      |            |         |        |
|                                      |            |         |        |
| PHAVLTGDIVBYZEROPROTNVAL_NANOSEC_U32 | 1          | NanoSec | 180000 |

**\* Also see** **FDD ES105A_StHlthSigNormn_DataDict.m file**

# Software Component Implementation

\<The detailed design of the function is provided in the FDD. The detail
design shall only be added to the MDD when it is not provided in the FDD
or the FDD is not adequate and clarification is needed.\>

### Sub-Module Functions

## Init: StHlthSigNormnInit1

##### **Design Rationale**

None

##### **Module Outputs**

See FDD

##### **Module Internal** 

See FDD

## Per: None

### Interrupt Service Routines

None

### Server Runnable Functions

## UpdRawSig

## Design Rationale

*None*

## Store Module Inputs to Local copies

*See FDD*

## (Processing of function)………

*See* *FDD*

## Store Local copy of outputs into Module Outputs

*See FDD*

### Module Internal (Local) Functions

##  Local Function \#1 

|                      |              |       |     |     |
|----------------------|--------------|-------|-----|-----|
| **Function Name**    | EcuTFildMon  | Type  | Min | Max |
| **Arguments Passed** | None         | N/A   | N/A | N/A |
| **Return Value**     | CtrlrTStHlth | Uint8 | 0   | 100 |
| **Return Value**     | CtrlrTRng    | Uint8 | 0   | 15  |

##   [section]

## Description

This function implements “Controller Temperature” block in the FDD

## Local Function \#2 Rationale

|                      |                |       |     |     |
|----------------------|----------------|-------|-----|-----|
| **Function Name**    | OutpAssiMon    | Type  | Min | Max |
| **Arguments Passed** | None           | N/A   | N/A | N/A |
| **Return Value**     | OutpAssiStHlth | Uint8 | 0   | 100 |
| **Return Value**     | VltgRng        | Uint8 | 0   | 15  |

## Description

This function implements “Health of Assist Due To Voltage” block in the
FDD

## Local Function \#3 Rationale

|                      |                     |               |     |     |
|----------------------|---------------------|---------------|-----|-----|
| **Function Name**    | DigTqSnsrStHlthCalc | Type          | Min | Max |
| **Arguments Passed** | SigId_Arg           | StHlthMonSig2 | 0   | 20  |
| **Return Value**     | DigTqSnsrAStHlth    | Uint8         | 0   | 100 |
| **Return Value**     | DigTqSnsrBStHlth    | Uint8         | 0   | 100 |
| **Return Value**     | DigTqIdptSigStHlth  | Uint8         | 0   | 100 |

## Description

This function implements “Digital Torque Sensor” block in the FDD

## Local Function \#4 Rationale

|                      |                        |       |     |     |
|----------------------|------------------------|-------|-----|-----|
| **Function Name**    | DutyCycExcddStHlthCalc | Type  | Min | Max |
| **Arguments Passed** | None                   | N/A   | N/A | N/A |
| **Return Value**     | DutyCycStHlth          | Uint8 | 0   | 100 |

## Description

This function implements “Duty Cycle” block in the FDD

## Local Function \#5 Rationale

|                      |                        |       |     |     |
|----------------------|------------------------|-------|-----|-----|
| **Function Name**    | EotImpctCntrStHlthCalc | Type  | Min | Max |
| **Arguments Passed** | None                   | N/A   | N/A | N/A |
| **Return Value**     | EotImpctStHlth         | Uint8 | 0   | 100 |

## Description

This function implements “EOT Impact” block in the FDD

## Local Function \#6 Rationale

|                      |                   |       |     |     |
|----------------------|-------------------|-------|-----|-----|
| **Function Name**    | MotPosnStHlthCalc | Type  | Min | Max |
| **Arguments Passed** | None              | N/A   | N/A | N/A |
| **Return Value**     | MotPosStHlth      | Uint8 | 0   | 100 |

## Description

This function implements “Motor Position” block in the FDD

## Local Function \#7 Rationale

|                      |                        |               |     |     |
|----------------------|------------------------|---------------|-----|-----|
| **Function Name**    | MotPosnErrStHlthCalc   | Type          | Min | Max |
| **Arguments Passed** | SigId_Arg              | StHlthMonSig2 | 0   | 20  |
| **Return Value**     | AbsltMotPosABDifStHlth | Uint8         | 0   | 100 |
| **Return Value**     | AbsltMotPosACDifStHlth | Uint8         | 0   | 100 |
| **Return Value**     | AbsltMotPosBCDifStHlth | Uint8         | 0   | 100 |

## Description

This function implements “Motor Position Phase Difference” block in the
FDD

## Local Function \#8 Rationale

|                      |                      |               |     |     |
|----------------------|----------------------|---------------|-----|-----|
| **Function Name**    | CurrMotSumStHlthCalc | Type          | Min | Max |
| **Arguments Passed** | SigId_Arg            | StHlthMonSig2 | 0   | 20  |
| **Return Value**     | CurrMotSumABCStHlth  | Uint8         | 0   | 100 |
| **Return Value**     | CurrMotSumDEFStHlth  | Uint8         | 0   | 100 |

## Description

This function implements “Current Motor Sum” block in the FDD

## Local Function \#9 Rationale

|                      |                   |               |     |     |
|----------------------|-------------------|---------------|-----|-----|
| **Function Name**    | PhaVltgStHlthCalc | Type          | Min | Max |
| **Arguments Passed** | SigId_Arg         | StHlthMonSig2 | 0   | 20  |
| **Return Value**     | PhaAStHlth        | Uint8         | 0   | 100 |
| **Return Value**     | PhaBStHlth        | Uint8         | 0   | 100 |
| **Return Value**     | PhaCStHlth        | Uint8         | 0   | 100 |
| **Return Value**     | PhaDStHlth        | Uint8         | 0   | 100 |
| **Return Value**     | PhaEStHlth        | Uint8         | 0   | 100 |
| **Return Value**     | PhaFStHlth        | Uint8         | 0   | 100 |

## Description

This function implements “Health of Phase” block in the FDD

## Local Function \#10 Rationale

|                      |                             |       |     |     |
|----------------------|-----------------------------|-------|-----|-----|
| **Function Name**    | RamEccSngBitCorrnStHlthCalc | Type  | Min | Max |
| **Arguments Passed** | None                        | N/A   | N/A | N/A |
| **Return Value**     | RamEccSngBitCorrnStHlth     | Uint8 | 0   | 100 |

## Description

This function implements “Single Bit Correction” block in the FDD

## Local Function \#11 Rationale

|                      |                          |         |     |            |
|----------------------|--------------------------|---------|-----|------------|
| **Function Name**    | PhaVltgCalcStHlth        | Type    | Min | Max        |
| **Arguments Passed** | MotDrvErrX_NanoSec_T_f32 | float32 | 0,0 | 40000000,0 |
| **Return Value**     | PhaXStHlth_Cnt_T_u08     | Uint8   | 0   | 100        |

## Description

This function implements a sub-section in“Health of Phase”” block in the
FDD

## Local Function \#12 Rationale

|                      |                      |      |     |     |
|----------------------|----------------------|------|-----|-----|
| **Function Name**    | FricEstimnStHlthCalc | Type | Min | Max |
| **Arguments Passed** | None                 | NA   |     |     |
| **Return Value**     | None                 | NA   |     |     |

## Description

This function implements a sub-section in“Friction Estimation”” block in
the FDD

## Local Function \#13 Rationale

|                      |                        |      |     |     |
|----------------------|------------------------|------|-----|-----|
| **Function Name**    | WhlImbRejctnStHlthCalc | Type | Min | Max |
| **Arguments Passed** | None                   | NA   |     |     |
| **Return Value**     | None                   | NA   |     |     |

## Description

This function implements a sub-section in“Wheel Imbalance Rejection””
block in the FDD

### Transition Functions

None.

# Known Limitations with Design

> None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**            |
|-----------------------------|----------------------------|
| DFD                         | Design functional diagram  |
| MDD                         | Module design Document     |
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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                 | Process Release 04.02.01       |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | Process Release 04.02.01       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | Process Release 04.02.01       |
| 5           | FDD: ES105A_StHlthSigNormn_Design                                                                                                                             | See Synergy subproject version |

{% endraw %}