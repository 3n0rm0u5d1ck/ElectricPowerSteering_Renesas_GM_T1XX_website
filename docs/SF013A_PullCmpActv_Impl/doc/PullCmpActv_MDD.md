---
layout: default
title: PullCmpActv_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Active Pull Compensation**

**Jan 17, 2017**

**Prepared For:**

**Software Engineering**

**,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser,**

**,**

**Saginaw, MI, USA  
<u>Change History</u>**

|             |                                                           |                   |             |             |
|------|------------------------------|----------------|----------|-----------|
| **Sl. No.** | **Description**                                           | **Author**        | **Version** | **Date**    |
| 1           | Initial Version                                           | Akhil Krishna N D | 1.0         | 16-Oct-2015 |
| 2           | Updated to FDD version SF013A_PullCmpActv_Design_1.4.0    | SB                | 2.0         | 29-Feb-2016 |
| 3           | Updated to design version SF013A_PullCmpActv_Design_1.6.0 | SN                | 3.0         | 20-Jun-2016 |
| 4           | Updated to design version 2.0.0                           | ML                | 4.0         | 17-Jan-2017 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#_Toc431305567)](#_Toc431305567)

[1.1 Purpose [5](#_Toc431305568)](#_Toc431305568)

[1.2 Scope [5](#_Toc431305569)](#_Toc431305569)

[2 Active Pull Compensation & High-Level Description
[6](#active-pull-compensation-high-level-description)](#active-pull-compensation-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of Active Pull Compensation
[7](#graphical-representation-of-active-pull-compensation)](#graphical-representation-of-active-pull-compensation)

[3.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[8](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [8](#_Toc375924737)](#_Toc375924737)

[4 Constant Data Dictionary
[9](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[9](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [9](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[10](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[10](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: PullCmpActvInit1
[10](#init-pullcmpactvinit1)](#init-pullcmpactvinit1)

[5.1.1.1 Design Rationale [10](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [10](#module-outputs)](#module-outputs)

[5.1.2 Per: PullCmpActvPer1
[10](#per-pullcmpactvper1)](#per-pullcmpactvper1)

[5.1.2.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[10](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: PullCmpActvPer2
[10](#per-pullcmpactvper2)](#per-pullcmpactvper2)

[5.1.3.1 Design Rationale
[10](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runnables [11](#server-runnables)](#server-runnables)

[5.2.1 GetPullCmpPrm [11](#getpullcmpprm)](#getpullcmpprm)

[5.2.1.1 Design Rationale
[11](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 (Processing of function)………
[11](#processing-of-function-2)](#processing-of-function-2)

[5.2.2 RstPullCmp [11](#rstpullcmp)](#rstpullcmp)

[5.2.2.1 Design Rationale
[11](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 (Processing of function)………
[11](#processing-of-function-3)](#processing-of-function-3)

[5.2.3 SetPullCmpLongTerm
[11](#setpullcmplongterm)](#setpullcmplongterm)

[5.2.3.1 Design Rationale
[11](#design-rationale-5)](#design-rationale-5)

[5.2.3.2 (Processing of function)………
[11](#processing-of-function-4)](#processing-of-function-4)

[5.2.4 SetPullCmpShoTerm [11](#setpullcmpshoterm)](#setpullcmpshoterm)

[5.2.4.1 Design Rationale
[11](#design-rationale-6)](#design-rationale-6)

[5.2.4.2 (Processing of function)………
[11](#processing-of-function-5)](#processing-of-function-5)

[5.3 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[12](#design-rationale-7)](#design-rationale-7)

[5.4.1.2 Processing [12](#processing)](#processing)

[5.4.2 Local Function \#2 [12](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[12](#design-rationale-8)](#design-rationale-8)

[5.4.2.2 Processing [12](#processing-1)](#processing-1)

[5.4.3 Local Function \#1 [12](#local-function-3)](#local-function-3)

[5.4.3.1 Design Rationale
[13](#design-rationale-9)](#design-rationale-9)

[5.4.3.2 Processing [13](#processing-2)](#processing-2)

[5.5 GLOBAL Function/Macro Definitions
[13](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [13](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[13](#design-rationale-10)](#design-rationale-10)

[5.5.1.2 processing [13](#processing-3)](#processing-3)

[6 Known Limitations with Design
[14](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[15](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[16](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [17](#glossary)](#glossary)

[Appendix C References [18](#references)](#references)

# Active Pull Compensation & High-Level Description

*The Active Pull Compensation Function corrects vehicle pull issues by
compensating for HW torque offsets detected by the steering system.
These torque offsets are classified as short-term and long-term, each of
which is compensated for independently by the algorithm. When the
compensation is applied, the need for the driver to provide a constant
input torque to counter these offsets is greatly reduced.*

# Design details of software module

## Graphical representation of Active Pull Compensation

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF013A_PullCmpActv_Impl/doc/mediax/media/image2.png"
style="width:3.42509in;height:6.27483in" />

## Data Flow Diagram

Please refer FDD.

### Component level DFD

<span id="_Toc375924737" class="anchor"></span>Please refer FDD.

### Function level DFD

Please refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
| Please refer .m file |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: PullCmpActvInit1

## Design Rationale

None

## Module Outputs

None

###  [section]

## Per: PullCmpActvPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Per: PullCmpActvPer2

## Design Rationale

Please refer FDD*.*

## Store Module Inputs to Local copies

Please refer FDD and design rationale noted above.

## (Processing of function)………

Please refer FDD.

## Store Local copy of outputs into Module Outputs

None

## Server Runnables 

## GetPullCmpPrm

## Design Rationale

None

##  (Processing of function)………

See GetPullCmpPrm block in FDD

## RstPullCmp

## Design Rationale

None

##  (Processing of function)………

See RstPullCmp block in FDD

## SetPullCmpLongTerm

## Design Rationale

None

## (Processing of function)………

See SetPullCmpLongTerm block in FDD

## SetPullCmpShoTerm

## Design Rationale

None

##  (Processing of function)………

See SetPullCmpShoTerm block in FDD

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                       |         |       |        |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ActvCmpEna                            | Type    | Min   | Max    |
| **Arguments Passed** | PullCmpActvShoTermRst_Cnt_T_logl      | boolean | FALSE | TRUE   |
|                      | AbslHwTqFild_HwNwtMtr_T_f32           | float32 | 0.0   | 10.0   |
|                      | AbslHwAg_HwDeg_T_f32                  | float32 | 0.0   | 1440.0 |
|                      | AbslVehYawRateFild_VehDegPerSec_T_f32 | float32 | 0.0   | 128.0  |
|                      | AbslVehLatA_MtrPerSecSqd_T_f32        | float32 | 0.0   | 10.0   |
|                      | PinionAgConf_Uls_T_f32                | float32 | 0.0   | 1.0    |
|                      | VehSpd_Kph_T_f32                      | float32 | 0.0   | 511.0  |
|                      | VehSpdVld_Cnt_T_logl                  | boolean | FALSE | TRUE   |
|                      | AbslHwVel_HwRadPerSec_T_f32           | float32 | 0.0   | 42.0   |
|                      | PullCmpCustLrngDi_Cnt_T_logl          | Boolean | FALSE | TRUE   |
|                      | VehYawRateVld_Cnt_T_logl              | boolean | FALSE | TRUE   |
| **Return Value**     | LrngEnad_Cnt_T_logl                   | boolean | FALSE | TRUE   |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “ActvCmpEna” block of the Simulink model of the design.

## Local Function \#2

|                      |                                   |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | CalcIntgrGain                     | Type    | Min   | Max  |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32               | float32 | -10.0 | 10.0 |
|                      | PullCmpShoTermPrev_HwNwtMtr_T_f32 | float32 | -10.0 | 10.0 |
| **Return Value**     | IntgtrGainShoTerm_Uls_T_f32       | float32 | 0.0   | 1.0  |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “CalcIntgtrGain” block of the Simulink model of the design

## Local Function \#3

|                      |                                   |         |       |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ErrIntgtrActvLim                  | Type    | Min   | Max  |
| **Arguments Passed** | PullCmpActvShoTermRst_Cnt_T_logl  | boolean | FALSE | TRUE |
|                      | IntgtrGainShoTerm_Uls_T_f32       | float32 | 0.0   | 1.0  |
|                      | PullErrShoTerm_HwNwtMtr_T_f32     | float32 | -10.0 | 10.0 |
|                      | PullCmpShoTermPrev_HwNwtMtr_T_f32 | float32 | -10.0 | 10.0 |
|                      | RampDwnStepSize_HwNwtMtr_T_f32    | float32 | 0.0   | 0.6  |
|                      | ShoTermRst_Cnt_T_logl             | boolean | FALSE | TRUE |
| **Return Value**     | PullCmpShoTerm_HwNwtMtr_T_f32     | float32 | -10.0 | 10.0 |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “ErrIntgtr&ActvLim” block of the Simulink model of the
design.

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

None

## Design Rationale

## processing

(Place flowchart/design for local function)

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                         | Process release 04.02.01        |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process release 04.02.01        |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process release 04.02.01        |
| 5           | FDD : SF013A_PullCmpActv_Design                                                                                                                                       | See Synergy sub project version |

{% endraw %}