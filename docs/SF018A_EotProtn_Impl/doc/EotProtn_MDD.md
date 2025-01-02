---
layout: default
title: EotProtn_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**EotProtn**

**Jul 1, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Spandana Balani,**

**  
<u>Change History</u>**

|          |                                         |                                |             |             |
|----------|---------------------|------------------|------------|-------------|
| **SNo.** | **Description**                         | **Author**                     | **Version** | **Date**    |
| 1        | Initial Version                         | Sarika Natu(KPIT Technologies) | 1.0         | 01-Oct-2015 |
| 2        | Implemented SF018A design version 1.5.0 | SB                             | 2.0         | 01-Jul-2016 |

**  
**

<u>Table of Contents</u>

1 EotProtn & High-Level Description 5

2 Design details of software module 6

2.1 Graphical representation of EotProtn 6

2.2 Data Flow Diagram 7

2.2.1 Component level DFD 7

2.2.2 Function level DFD 7

3 Constant Data Dictionary 8

3.1 Program (fixed) Constants 8

3.1.1 Embedded Constants 8

4 Software Component Implementation 9

4.1 Sub-Module Functions 9

4.1.1 Init: EotProtn_Init1 9

4.1.1.1 Design Rationale 9

4.1.1.2 Module Outputs 9

4.1.2 Per: EotProtn_Per1 9

4.1.2.1 Design Rationale 9

4.1.2.2 Store Module Inputs to Local copies 9

4.1.2.3 (Processing of function)……… 9

4.1.2.4 Store Local copy of outputs into Module Outputs 9

4.2 Server Runables 9

4.3 Interrupt Functions 9

4.4 Module Internal (Local) Functions 9

4.4.1 Local Function \#1 9

4.4.1.1 Design Rationale 10

4.4.1.2 Processing 10

4.4.2 Local Function \#2 10

4.4.2.1 Design Rationale 10

4.4.2.2 Processing 10

4.4.3 Local Function \#3 10

4.4.3.1 Design Rationale 10

4.4.3.2 Processing 10

4.4.4 Local Function \#4 11

4.4.4.1 Design Rationale 11

4.4.4.2 Processing 11

4.4.5 Local Function \#5 11

4.4.5.1 Design Rationale 11

4.4.5.2 Processing 11

4.4.6 Local Function \#6 11

4.4.6.1 Design Rationale 11

4.4.6.2 Processing 11

4.4.7 Local Function \#7 11

4.4.7.1 Design Rationale 12

4.4.7.2 Processing 12

4.4.8 Local Function \#8 12

4.4.8.1 Design Rationale 12

4.4.8.2 Processing 12

4.4.9 Local Function \#9 12

4.4.9.1 Design Rationale 13

4.4.9.2 Processing 13

4.5 GLOBAL Function/Macro Definitions 13

5 Known Limitations with Design 14

6 UNIT TEST CONSIDERATION 15

Appendix A Abbreviations and Acronyms 16

Appendix B Glossary 17

Appendix C References 18

# EotProtn & High-Level Description

The End of Travel Protection function specifies performance attributes
as the steering system approaches the mechanical end of travel of the
steering gear.

# Design details of software module

## Graphical representation of EotProtn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF018A_EotProtn_Impl/doc/mediax/media/image2.png"
style="width:3.21667in;height:4.90833in" />

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

|                         |           |
|-------------------------|-----------|
| **Constant**            | **Value** |
| DAMPGPTSIZE_CNT_U08     | 2         |
| DAMPGVEHSPDSIZE_CNT_U08 | 4         |
| GAINVEHSPDSIZE_CNT_U08  | 5         |

# Software Component Implementation

## Sub-Module Functions

## Init: EotProtn_Init1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: EotProtn_Per1

## Design Rationale

EotProtn_Per1 function is divided into various functions to reduce the
cyclomatic complexity.

The limiting of ‘EotAssiSca’ output is performed in SoftEndStop
subsystem in FDD. But in code it is limiting calculations are done where
the output is calculated i.e. FildEotGain function.

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

None

## Interrupt Functions

None

## Module Internal (Local) Functions

## Local Function \#1

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | EotVelImpct                  | Type    | Min   | Max  |
| **Arguments Passed** | HwAgEotCw_HwDeg_T_f32        | float32 | 360   | 900  |
|                      | HwAgEotCcw_HwDeg_T_f32       | float32 | -900  | -360 |
|                      | HwAg_HwDeg_T_f32             | float32 | -1440 | 1440 |
|                      | VehSpd_Kph_T_f32             | float32 | 0     | 511  |
|                      | HwAgAuthy_Uls_T_f32          | float32 | 0     | 1    |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
| **Return Value**     | EotMotTqLim_MotNwtMtr_T_f32  | float32 | 0     | 8.8  |

## Design Rationale

None

Note: Outputs of “EotVelImpct” function is -
EotMotTqLim_MotNwtMtr_T_f32.

## Processing

Refer to the “EotVelImpct” subsystem of the Simulink model of the design

## Local Function \#2

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | LimPosnDetd                   | Type    | Min   | Max  |
| **Arguments Passed** | RackTrvlLimrRngEna_Cnt_T_logl | boolean | False | True |
|                      | HwAgEotCw_HwDeg_T_f32         | float32 | 360   | 900  |
|                      | HwAgEotCcw_HwDeg_T_f32        | float32 | -900  | -360 |
|                      | HwAg_HwDeg_T_f32              | float32 | -1440 | 1440 |
| **Return Value**     | LimPosn_HwDeg_T_f32           | float32 | -1440 | 1440 |

## Design Rationale

None

Note: Outputs of “LimPosnDetd” function is - LimPosn_HwDeg_T_f32.

## Processing

Refer to the “LimPosnDetd” subsystem of the Simulink model of the design

## Local Function \#3

|                      |                     |         |       |      |
|----------------------|---------------------|---------|-------|------|
| **Function Name**    | CalcEntrGain        | Type    | Min   | Max  |
| **Arguments Passed** | HwAg_HwDeg_T_f32    | float32 | -1440 | 1440 |
|                      | VehSpd_Kph_T_f32    | float32 | 0     | 511  |
|                      | LimPosn_HwDeg_T_f32 | float32 | -1440 | 1440 |
| **Return Value**     | EntrGain_Uls_T_f32  | float32 | 0     | 1    |

## Design Rationale

None

Note: Outputs of “CalcEntrGain” function is - EntrGain_Uls_T_f32.

## Processing

Refer to the “CalcEntrGain” subsystem of the Simulink model of the
design

## Local Function \#4

|                      |                     |         |     |     |
|----------------------|---------------------|---------|-----|-----|
| **Function Name**    | CalcExitGain        | Type    | Min | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32 | float32 | -10 | 10  |
| **Return Value**     | ExitGain_Uls_T_f32  | float32 | 0   | 1   |

## Design Rationale

Calculation of Filtered Handwheel torque is done after ‘CalcExitGain’
function is executed.

Note: Outputs of “CalcExitGain” function is - FildHwTq_HwNwtMtr_T_f32

## Processing

Refer to the “CalcExitGain” subsystem of the Simulink model of the
design

## Local Function \#5

|                      |                    |         |     |     |
|----------------------|--------------------|---------|-----|-----|
| **Function Name**    | CalcEotGain        | Type    | Min | Max |
| **Arguments Passed** | EntrGain_Uls_T_f32 | float32 | 0   | 1   |
|                      | ExitGain_Uls_T_f32 | float32 | 0   | 1   |
| **Return Value**     | EotGain_Uls_T_f32  | float32 | 0   | 1   |

## Design Rationale

None

Note: Outputs of “CalcEotGain” function is - EotGain_Uls_T_f32

## Processing

Refer to the “CalcEotGain” subsystem of the Simulink model of the design

## Local Function \#6

|                      |                      |         |     |     |
|----------------------|----------------------|---------|-----|-----|
| **Function Name**    | FildEotGain          | Type    | Min | Max |
| **Arguments Passed** | EotGain_Uls_T_f32    | float32 | 0   | 1   |
| **Return Value**     | EotAssiSca_Uls_T_f32 | float32 | 0   | 1   |

## Design Rationale

Limit of EotAssiSca is moved to local function FildEotGain.

Note: Outputs of “FildEotGain” function is - EotAssiSca_Uls_T_f32

## Processing

Refer to the “FildEotGain” subsystem of the Simulink model of the design

## Local Function \#7

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | CalcEotDampg                 | Type    | Min   | Max  |
| **Arguments Passed** | HwAg_HwDeg_T_f32             | float32 | -1440 | 1440 |
|                      | VehSpd_Kph_T_f32             | float32 | 0     | 511  |
|                      | HwAgEotCw_HwDeg_T_f32        | float32 | 360   | 900  |
|                      | HwAgEotCcw_HwDeg_T_f32       | float32 | -900  | -360 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
| **Return Value**     | EotDampgCmd_MotNwtMtr_T_f32  | float32 | -8.8  | 8.8  |

## Design Rationale

None

Note: Outputs of “CalcEotDampg” function is -
EotDampgCmd_MotNwtMtr_T_f32

## Processing

Refer to the “CalcEotDampg” calculation of the Simulink model of the
design

## Local Function \#8

|                      |                              |         |       |      |
|----------------------|------------------------------|---------|-------|------|
| **Function Name**    | EotActvCmdCalc               | Type    | Min   | Max  |
| **Arguments Passed** | RackTrvlLimrDi_Cnt_T_logl    | boolean | False | True |
|                      | HwAgAuthy_Uls_T_f32          | float32 | 0     | 1    |
|                      | VehSpd_Kph_T_f32             | float32 | 0     | 511  |
|                      | HwAg_HwDeg_T_f32             | float32 | -1440 | 1440 |
|                      | MotVelCrf_MotRadPerSec_T_f32 | float32 | -1350 | 1350 |
|                      | LimPosn_HwDeg_T_f32          | float32 | -1440 | 1440 |
| **Return Value**     | EotActvCmd_MotNwtMtr_T_f32   | float32 | -8.8  | 8.8  |

## Design Rationale

None

Note: Outputs of “EotActvCmdCalc” function is -
EotActvCmd_MotNwtMtr_T_f32

## Processing

Refer to the “EotActvCmdCalc” calculation of the Simulink model of the
design

## Local Function \#9

|                      |                          |         |          |         |
|----------------------|--------------------------|---------|----------|---------|
| **Function Name**    | SoftEndStopStCtrl        | Type    | Min      | Max     |
| **Arguments Passed** | VehSpd_Kph_T_f32         | float32 | 0        | 511     |
|                      | HwAgAuthy_Uls_T_f32      | float32 | 0        | 1       |
|                      | EotProtnDi_Cnt_T_Logl    | boolean | 0        | 1       |
|                      | EotDetd_Cnt_T_Logl       | boolean | 0        | 1       |
|                      | HwAg_HwDeg_T_f32         | float32 | -1440    | 1440    |
|                      | FildHwTq_HwNwtMtr_T_f32  | float32 | -3.4E+38 | 3.4E+38 |
|                      | SysMotTqCmdSca_Uls_T_f32 | float32 | 0        | 1       |
|                      | LimPosn_HwDeg_T_f32      | float32 | -1440    | 1440    |
| **Return Value**     | None                     | float32 | -8.8     | 8.8     |

## Design Rationale

None

## Processing

Refer to the “SoftEndStopStCtrl” calculation of the Simulink model of
the design

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

> None

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
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | Process release 04.02.01       |
| 2           | MDD Guideline                                                                                                                                                         | Process release 04.02.01       |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | Process release 04.02.01       |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | Process release 04.02.01       |
| 5           | SF018A_EotProtn_Design                                                                                                                                                | See Synergy subproject version |

{% endraw %}