---
layout: default
title: DutyCycThermProtn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**DutyCycThermProtn**

**Sep** **29, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Anne**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
<u>Change History</u>**

|                                 |                                |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                 | **Author**                     | **Version** | **Date**    |
| Initial Version                 | Sarika Natu(KPIT Technologies) | 1.0         | 02-Oct-2015 |
| Updated to version 2.0.0 of FDD | Krishna Anne                   | 2.0         | 07-Apr-2016 |
| Fix for anomaly EA4# 7558       | Krishna Anne                   | 3.0         | 29-Sep-2016 |

**  
**

**<u>Table of Contents</u>**

[1 DutyCycThermProtn & High-Level Description
[5](#dutycycthermprotn-high-level-description)](#dutycycthermprotn-high-level-description)

[2 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[2.1 Graphical representation of DutyCycThermProtn
[6](#graphical-representation-of-dutycycthermprotn)](#graphical-representation-of-dutycycthermprotn)

[2.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[2.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[2.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[3 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[3.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[3.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[4 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[4.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[4.1.1 Init: DutyCycThermProtn_Init1
[9](#init-dutycycthermprotn_init1)](#init-dutycycthermprotn_init1)

[4.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[4.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[4.1.2 Per: DutyCycThermProtn_Per1
[9](#per-dutycycthermprotn_per1)](#per-dutycycthermprotn_per1)

[4.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[4.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[4.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[4.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[4.2 Server Runables [9](#server-runables)](#server-runables)

[4.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[4.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[4.4.1 Local Function \#1 [9](#local-function-1)](#local-function-1)

[4.4.1.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[4.4.1.2 Processing [10](#processing)](#processing)

[4.4.2 Local Function \#2 [10](#local-function-2)](#local-function-2)

[4.4.2.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[4.4.2.2 Processing [10](#processing-1)](#processing-1)

[4.4.3 Local Function \#3 [10](#local-function-3)](#local-function-3)

[4.4.3.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[4.4.3.2 Processing [10](#_Toc432081565)](#_Toc432081565)

[4.4.4 Local Function \#4 [10](#local-function-4)](#local-function-4)

[4.4.4.1 Design Rationale
[11](#design-rationale-5)](#design-rationale-5)

[4.4.4.2 Processing [11](#processing-3)](#processing-3)

[4.4.5 Local Function \#5 [11](#local-function-5)](#local-function-5)

[4.4.5.1 Design Rationale
[11](#design-rationale-6)](#design-rationale-6)

[4.4.5.2 Processing [11](#_Toc432081571)](#_Toc432081571)

[4.4.6 Local Function \#6 [11](#local-function-6)](#local-function-6)

[4.4.6.1 Design Rationale
[11](#design-rationale-7)](#design-rationale-7)

[4.4.6.2 Processing [12](#processing-5)](#processing-5)

[4.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [17](#references)](#references)

# DutyCycThermProtn & High-Level Description

The purpose of the Thermal Duty Cycle Protection is to limit and protect
the system from excessive use, based on motor rotational velocity and
system temperature. It also provides protection status information for
use by other functions.

# Design details of software module

## Graphical representation of DutyCycThermProtn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF009A_DutyCycThermProtn_Impl/doc/mediax/media/image1.png"
style="width:4.75978in;height:8.352in" />

## Data Flow Diagram

See FDD

### Component level DFD

See FDD

### Function level DFD

See FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

Refer .m file

| Constant Name            | Value |
|--------------------------|-------|
| DUTYCYCTHERMSIZE_CNT_U08 | 5     |
| THERMLOADLIMSIZE_CNT_U08 | 8     |
| MULTFILTERSIZE_CNT_U08   | 6     |

# Software Component Implementation

## Sub-Module Functions

## Init: DutyCycThermProtn_Init1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: DutyCycThermProtn_Per1

## Design Rationale

DutyCycThermProtn_Per1 function is divided into various functions to
reduce the cyclomatic complexity.

The subsystems ‘Multiplier’ and ‘FilterPercMax’ are clubbed into
‘MultiFilterPercMax’ local function.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                     |         |     |         |
|----------------------|---------------------|---------|-----|---------|
| **Function Name**    | FiltSVReinit        | Type    | Min | Max     |
| **Arguments Passed** | IgnTiOff_Cnt_T_u32  | uint32  | 0   | 1720000 |
|                      | VehTiVld_Cnt_T_Logl | Boolean | 0   | 1       |
| **Return Value**     | None                |         |     |         |

## Design Rationale

Name of local function matches with subsystem name from FDD

## Processing

## Local Function \#2

|                      |                                |         |     |     |
|----------------------|--------------------------------|---------|-----|-----|
| **Function Name**    | TemperatureSelection           | Type    | Min | Max |
| **Arguments Passed** | DiagcStsLimdTPrfmnc_Cnt_T_Logl | boolean | 0   | 1   |
|                      | EcuTFild_DegCgrd_T_f32         | float32 | -50 | 150 |
|                      | MotFetT_DegCgrd_T_f32          | float32 | -50 | 200 |
|                      | MotMagT_DegCgrd_T_f32          | float32 | -50 | 150 |
|                      | MotWidgT_DegCgrd_T_f32         | float32 | -50 | 300 |
|                      | \*Mult12Temp_DegCgrd_T\_ s15p0 | Sint16  | -50 | 200 |
|                      | \*Mult36Temp_DegCgrd_T_s15p0   | Sint16  | -50 | 300 |
| **Return Value**     | SlcTemp_DegCgrd_T_s15p0        | sint16  | -50 | 300 |

## Design Rationale

Name of local function matches with subsystem name from FDD

Note: The outputs of the function are Mult12Temp_DegCgrd_T_s15p0,
Mult36Temp_DegCgrd_T_s15p0 and SlcTemp_DegCgrd_T_f32.

## Processing

None

## Local Function \#3

|                      |                                        |         |     |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | TemperatureLimiting                    | Type    | Min | Max  |
| **Arguments Passed** | EcuTFild_DegCgrd_T_f32                 | float32 | -50 | 150  |
|                      | MotWidgT_DegCgrd_T_f32                 | float32 | -50 | 300  |
| **Return Value**     | AbsTempLimitSlew_MotNwtMtrPerSec_T_f32 | float32 | 0   | 8.79 |

## Design Rationale

<span id="_Toc432081565" class="anchor"></span>Name of local function
matches with subsystem name from FDD

## Processing

None

## Local Function \#4

|                      |                                     |         |       |       |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | MultiFilterPercMax                  | Type    | Min   | Max   |
| **Arguments Passed** | Mult12Temp_DegCgrd_T_s15p0          | sint16  | -50   | 200   |
|                      | Mult36Temp_DegCgrd_T_s15p0          | sint16  | -50   | 300   |
|                      | DutyCycThermProtnDi_Cnt_T_Logl      | boolean | 0     | 1     |
|                      | MotVelCrf_MotRadPerSec_T_f32        | float32 | -1350 | 1350  |
|                      | MotCurrPeakEstimd_AmprSqd_T_f32     | float32 | 0     | 62500 |
|                      | MotCurrPeakEstimdFild_AmprSqd_T_f32 | float32 | 0     | 62500 |
|                      | \*MaxOut_Uls_T_u16p0                | uint16  | 0     | 200   |
| **Return Value**     | ThermLimSlowFilMax_Uls_T_f32        | float32 | 0     | 200   |

## Design Rationale

The subsystems ‘Multiplier’ and ‘FilterPercMax’ are clubbed into
‘MultiFilterPercMax’ local function.

Note: The outputs of the function are MaxOut_Uls_T_u16p0 and
ThermLimSlowFilMax_Uls_T_f32.

## Processing

None

## Local Function \#5

|                      |                                |         |       |      |
|----------------------|--------------------------------|---------|-------|------|
| **Function Name**    | ThermalLoadLimit               | Type    | Min   | Max  |
| **Arguments Passed** | MotVelCrf_MotRadPerSec_T_f32   | float32 | -1350 | 1350 |
|                      | SlcTemp_DegCgrd_T_s15p0        | sint16  | -50   | 300  |
|                      | MaxOut_Uls_T_u16p0             | uint16  | 0     | 200  |
| **Return Value**     | ThermalLoadLmt_MotNwtMtr_T_f32 | float32 | 0     | 8.79 |

## Design Rationale

<span id="_Toc432081571" class="anchor"></span>Name of local function
matches with subsystem name from FDD

## Processing

None

## Local Function \#6

|                      |                                        |         |     |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | ThermalLimitStatus                     | Type    | Min | Max  |
| **Arguments Passed** | AbsTempLimitSlew_MotNwtMtrPerSec_T_f32 | float32 | 0   | 8.79 |
|                      | DutyCycThermProtnDi_Cnt_T_Logl         | Boolean | 0   | 1    |
|                      | ThermalLoadLmt_MotNwtMtr_T_f32         | float32 | 0   | 8.79 |
|                      | MaxOut_Uls_T_u16p0                     | uint16  | 0   | 200  |
|                      | \*ThermMotTqLim_MotNwtMtr_T_f32        | float32 | 0   | 8.8  |
| **Return Value**     | ThermRednFac_Uls_T_f32                 | float32 | 0   | 1    |

## Design Rationale

Name of local function matches with subsystem name from FDD

Note: The outputs of the function are ThermMotTqLim_MotNwtMtr_T_f32 and
ThermRednFac_Uls_T_f32.

## Local Function \#6

|                      |                                   |        |      |      |
|---------------|--------------------------------|---------|---------|---------|
| **Function Name**    | UseInpLowr                        | Type   | Min  | Max  |
| **Arguments Passed** | \*TableX_Cnt_T_s16                | sint16 | FULL | FULL |
|                      | \*TableY_Cnt_T_u16                | uint16 | FULL | FULL |
|                      | Size_Cnt_T_u16                    | uint16 | 1    | 20   |
|                      | Input_Cnt_T_s16                   | sint16 | FULL | FULL |
| **Return Value**     | TableY_Cnt_T_u16\[Idx_Cnt_T_u08\] | uint16 | FULL | FULL |

## Design Rationale

None.

## Processing

None

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

-   

-   Function UseInpLowr to be tested only as called by the component;
    input and output ranges will not be reached.

-   Function UseInpLowr’s TableX must have strictly increasing elements.

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 02.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD – SF009A_DutyCycThermProtn_Design                                                                                                                                 | See Synergy sub project version |

{% endraw %}