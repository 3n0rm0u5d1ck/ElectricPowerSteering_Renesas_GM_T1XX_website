---
layout: default
title: GmOvrlStMgr_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**GmOvrlStMgr**

**Feb 02, 2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Jayakrishnan T,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                               |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                               | **Author**             | **Version** | **Date**    |
| Initial Version                                                               | Sankardu Varadapureddi | 1           | 6-Oct-2015  |
| Added HwTq based intervention for LKA, handwheel buzz based on LoA key cycles | Nick Saxton            | 2           | 11-Feb-2016 |
| Changed argument names of ESCFlt local function                               | Nick Saxton            | 3           | 13-Jun-2016 |
| Updated graphical representation and edited local function section            | Nick Saxton            | 4           | 24-Jun-2016 |
| Updated for FDD v4.0.0                                                        | Nick Saxton            | 5           | 22-Aug-2016 |
| Updated to design version 4.1.0                                               | TATA                   | 6           | 12-Dec-16   |
| Anomaly fix EA4#8726, Removed local function LkaCheck                         | JK                     | 7           | 02-Feb-17   |

**  
**

<u>Table of Contents</u>

1 GmOvrlStMgr High-Level Description 6

2 Design details of software module 7

2.1 Graphical representation of GmOvrlStMgr 7

2.2 Data Flow Diagram 8

2.2.1 Component level DFD 8

2.2.2 Function level DFD 8

3 Constant Data Dictionary 9

3.1 Program (fixed) Constants 9

3.1.1 Embedded Constants 9

4 Software Component Implementation 10

4.1 Sub-Module Functions 10

4.1.1 Init: GmOvrlStMgrInit1 10

4.1.1.1 Design Rationale 10

4.1.1.2 Module Outputs 10

4.1.2 Per: GmOvrlStMgrPer1 10

4.1.2.1 Design Rationale 10

4.1.2.2 Store Module Inputs to Local copies 10

4.1.2.3 (Processing of function)……… 10

4.1.2.4 Store Local copy of outputs into Module Outputs 10

4.2 Server Runables 10

4.2.1 GetGmLoaIgnCntr_Oper 10

4.2.1.1 Design Rationale 10

4.2.1.2 Store Module Inputs to Local copies 10

4.2.1.3 (Processing of function)……… 10

4.2.1.4 Store Local copy of outputs into Module Outputs 10

4.2.2 SetGmLoaIgnCntr_Oper 11

4.2.2.1 Design Rationale 11

4.2.2.2 Store Module Inputs to Local copies 11

4.2.2.3 (Processing of function)……… 11

4.2.2.4 Store Local copy of outputs into Module Outputs 11

4.3 Interrupt Functions 11

4.4 Module Internal (Local) Functions 11

4.4.1 Local Function \#1 11

4.4.1.1 Description 11

4.4.2 Local Function \#2 11

4.4.2.1 Description 11

4.4.3 Local Function \#3 11

4.4.3.1 Description 12

4.4.4 Local Function \#4 12

4.4.4.1 Description 12

4.4.5 Local Function \#5 12

4.4.5.1 Description 12

4.4.6 Local Function \#6 12

4.4.6.1 Description 12

4.4.7 Local Function \#7 13

4.4.7.1 Description 13

4.4.8 Local Function \#8 13

4.4.8.1 Description 13

4.4.9 Local Function \#9 13

4.4.9.1 Description 14

4.4.10 Local Function \#10 14

4.4.10.1 Description 14

4.4.11 Local Function \#11 14

4.4.11.1 Description 15

4.4.12 Local Function \#12 15

4.4.12.1 Description 15

4.4.13 Local Function \#13 16

4.4.13.1 Description 16

4.4.14 Local Function \#14 16

4.4.14.1 Description 16

4.4.15 Local Function \#15 16

4.4.15.1 Description 16

4.4.16 Local Function \#16 16

4.4.16.1 Description 17

4.4.17 Local Function \#17 17

4.4.17.1 Description 17

4.4.18 Local Function \#18 17

4.4.18.1 Description 17

4.4.19 Local Function \#19 17

4.4.19.1 Description 17

4.4.20 Local Function \#20 17

4.4.20.1 Description 18

4.4.21 Local Function \#21 18

4.4.21.1 Description 18

4.4.22 Local Function \#22 18

4.4.22.1 Description 18

4.4.23 Local Function \#23 18

4.4.23.1 Description 19

4.4.24 Local Function \#24 19

4.4.24.1 Description 19

4.5 GLOBAL Function/Macro Definitions 19

5 Known Limitations with Design 20

6 UNIT TEST CONSIDERATION 21

Appendix A Abbreviations and Acronyms 22

Appendix B Glossary 23

Appendix C References 24

# GmOvrlStMgr High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of GmOvrlStMgr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CF009A_GmOvrlStMgr_Impl/doc/mediax/media/image1.jpeg"
style="width:3.15441in;height:7.44792in"
alt="C:\Component\CF009A_GmOvrlStMgr_Impl_4.1.0\MDD.JPG" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

# Software Component Implementation

## Sub-Module Functions

## Init: GmOvrlStMgrInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: GmOvrlStMgrPer1

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

###  GetGmLoaIgnCntr_Oper

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

### SetGmLoaIgnCntr_Oper

## Design Rationale

Refer FDD for the overall functionality.

## Store Module Inputs to Local copies

*Refer FDD*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                 |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | VehStandStillTmrElpdChk         | Type    | Min   |      | Max |
| **Arguments Passed** | VehSpdSecurMax_Kph_T_f32        | float32 | 0     | 511  |     |
| **Return Value**     | VehStandStillTiExcdd_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

"Timer for VehStandStill" block implementation.

## Local Function \#2

|                      |                               |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | ShiftLvrRvsTmrElpdChk         | Type    | Min   |      | Max |
| **Arguments Passed** | ShiftLvrRvs_Cnt_T_logl        | boolean | FALSE | TRUE |     |
| **Return Value**     | ShiftLvrRvsTiExcdd_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

"Timer for ShiftLvrRvs" block implementation.

## Local Function \#3

|                      |                     |         |       |      |     |
|----------------------|---------------------|---------|-------|------|-----|
| **Function Name**    | ApaIntv             | Type    | Min   |      | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32 | float32 | -10   | 10   |     |
| **Return Value**     | ApaIntv_Cnt_T_logl  | boolean | FALSE | TRUE |     |

## Description

"ApaIntv" block implementation.

## Local Function \#4

|                      |                                |         |       |      |     |
|--------------|----------------------|-------------|------------|--|-----------|
| **Function Name**    | HaptcEnaDurnElpdChk            | Type    | Min   |      | Max |
| **Arguments Passed** | HwHaptcEna_Cnt_T_logl          | boolean | FALSE | TRUE |     |
| **Return Value**     | HwHaptcEnaDurnExcdd_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

"Timer for HwHaptcEna" block implementation.

## Local Function \#5

|                      |                                |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | LkaFltActvChk                  | Type    | Min   |      | Max |
| **Arguments Passed** | Msg17DBusHiSpdMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
|                      | Msg180BusHiSpdMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
|                      | Msg180BusHiSpdInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | Msg1E9BusHiSpdMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
|                      | Msg214BusHiSpdInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | Msg214BusHiSpdMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
|                      | VehSpdSecurMaxVld_Cnt_T_logl   | boolean | FALSE | TRUE |     |
|                      | VehSpdSecurMinVld_Cnt_T_logl   | boolean | FALSE | TRUE |     |
| **Return Value**     | LkaFlt_Cnt_T_logl              | boolean | FALSE | TRUE |     |

## Description

Determination of 'LkaFlt'.

## Local Function \#6

|                      |                                |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | LkaInhbChk                     | Type    | Min   |      | Max |
| **Arguments Passed** | Msg17DBusHiSpdInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | VehStabyEnhmtActv_Cnt_T_logl   | boolean | FALSE | TRUE |     |
|                      | AbsActvProtd_Cnt_T_logl        | boolean | FALSE | TRUE |     |
|                      | Msg1E9BusHiSpdInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
| **Return Value**     | LkaInhb_Cnt_T_logl             | boolean | FALSE | TRUE |     |

## Description

Determination of ' LkaInhb'.

## Local Function \#7

|                      |                                |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | ApaRcvrlFltChk                 | Type    | Min   |      | Max |
| **Arguments Passed** | Msg1F5BusHiSpdInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | VehSpdSecurMaxVld_Cnt_T_logl   | boolean | FALSE | TRUE |     |
|                      | VehSpdSecurMinVld_Cnt_T_logl   | boolean | FALSE | TRUE |     |
| **Return Value**     | ApaRcvrlFlt_Cnt_T_logl         | boolean | FALSE | TRUE |     |

## Description

Determination of ‘ ApaRcvrlFlt’.

## Local Function \#8

|                      |                          |               |            |                      |     |
|------------|--------------------|-----------|-----------|--|------------------|
| **Function Name**    | ApaTmpInhbExitCdnsChk    | Type          | Min        |                      | Max |
| **Arguments Passed** | ApaNrcvrlFlt_Cnt_T_logl  | boolean       | FALSE      | TRUE                 |     |
|                      | LoaSt_Cnt_T_enum         | LoaSt1 (enum) | LOAST_NORM | LOAST_IMDTSHTDWNREQD |     |
|                      | VehSpdSecurMax_Kph_T_f32 | float32       | 0          | 511                  |     |
|                      | ApaEna_Cnt_T_logl        | boolean       | FALSE      | TRUE                 |     |
|                      | HwHaptcEna_Cnt_T_logl    | boolean       | FALSE      | TRUE                 |     |
|                      | ApaRcvrlFlt_Cnt_T_logl   | boolean       | FALSE      | TRUE                 |     |
|                      | SysSt_Cnt_T_enum         | SysSt1        | SYSST_DI   | SYSST_WRMIN          |     |
|                      | \*ApaSt_Cnt_T_u08        | uint8         | 0          | 4                    |     |
| **Return Value**     | None                     |               |            |                      |     |

## Description

This function validates conditions for all state transitions from ‘ APA
Temporarily Inhibited’ state.

‘\*ApaSt_Cnt_T_u08’ is an output of this function.

## Local Function \#9

|                      |                          |               |            |                      |     |
|------------|--------------------|-----------|-----------|--|------------------|
| **Function Name**    | ApaActvExitCdnsChk       | Type          | Min        |                      | Max |
| **Arguments Passed** | ApaNrcvrlFlt_Cnt_T_logl  | boolean       | FALSE      | TRUE                 |     |
|                      | LoaSt_Cnt_T_enum         | LoaSt1 (enum) | LOAST_NORM | LOAST_IMDTSHTDWNREQD |     |
|                      | VehSpdSecurMax_Kph_T_f32 | float32       | 0          | 511                  |     |
|                      | ApaEna_Cnt_T_logl        | boolean       | FALSE      | TRUE                 |     |
|                      | HwHaptcEna_Cnt_T_logl    | boolean       | FALSE      | TRUE                 |     |
|                      | ApaRcvrlFlt_Cnt_T_logl   | boolean       | FALSE      | TRUE                 |     |
|                      | ApaIntv_Cnt_T_logl       | boolean       | FALSE      | TRUE                 |     |
|                      | SysSt_Cnt_T_enum         | SysSt1        | SYSST_DI   | SYSST_WRMININ        |     |
|                      | \*ApaSt_Cnt_T_u08        | uint8         | 0          | 4                    |     |
| **Return Value**     | None                     |               |            |                      |     |

## Description

This function validates conditions for all state transitions from ‘ APA
Active’ state.

‘\*ApaSt_Cnt_T_u08’ is an output of this function.

## Local Function \#10

|                      |                                        |         |          |               |     |
|-----------|--------------------------|----------|----------|--|---------------|
| **Function Name**    | ApaCtrlAvlExitCdnsChk                  | Type    | Min      |               | Max |
| **Arguments Passed** | VehSpdSecurMax_Kph_T_f32               | float32 | 0        | 511           |     |
|                      | ApaRcvrlFlt_Cnt_T_logl                 | boolean | FALSE    | TRUE          |     |
|                      | HwHaptcEnaDurnExcdd_Cnt_T_logl         | boolean | FALSE    | TRUE          |     |
|                      | VehStandStillTiExcdd_Cnt_T_logl        | boolean | FALSE    | TRUE          |     |
|                      | ShiftLvrRvsTiExcdd_Cnt_T_logl          | boolean | FALSE    | TRUE          |     |
|                      | ApaEna_Cnt_T_logl                      | boolean | FALSE    | TRUE          |     |
|                      | HwHaptcEna_Cnt_T_logl                  | boolean | FALSE    | TRUE          |     |
|                      | HaptcStTranActvToWaitFlg_Cnt_T_logl    | boolean | FALSE    | TRUE          |     |
|                      | TranHaptcWaitToApaStActvFlg_Cnt_T_logl | boolean | FALSE    | TRUE          |     |
|                      | SysSt_Cnt_T_enum                       | SysSt1  | SYSST_DI | SYSST_WRMININ |     |
|                      | \*HaptcSt_Cnt_T_u08                    | uint8   | 0        | 2             |     |
|                      | \*ApaSt_Cnt_T_u08                      | uint8   | 0        | 4             |     |
| **Return Value**     | None                                   |         |          |               |     |

## Description

This function validates conditions for all state transitions from and
within ‘APA Availability for Control’ state.

‘\*ApaSt_Cnt_T_u08 and \*HaptcSt_Cnt_T_u08’ are outputs of this
function.

## Local Function \#11

|                      |                          |         |            |                      |     |
|-----------|----------------------|----------|-----------|--|------------------|
| **Function Name**    | LkaStTran                | Type    | Min        |                      | Max |
| **Arguments Passed** | LkaMfgEna_Cnt_T_logl     | boolean | FALSE      | TRUE                 |     |
|                      | LkaPrmntFlt_Cnt_T_logl   | boolean | FALSE      | TRUE                 |     |
|                      | LoaSt_Cnt_T_enum         | boolean | LOAST_NORM | LOAST_IMDTSHTDWNREQD |     |
|                      | LkaFlt_Cnt_T_logl        | boolean | FALSE      | TRUE                 |     |
|                      | LkaInhb_Cnt_T_logl       | boolean | FALSE      | TRUE                 |     |
|                      | EscSt_Cnt_T_u08          | uint8   | 0          | 4                    |     |
|                      | LkaEna_Cnt_T_logl        | boolean | FALSE      | TRUE                 |     |
|                      | VehSpdSecurMin_Kph_T_f32 | float32 | 0          | 511                  |     |
|                      | VehSpdSecurMax_Kph_T_f32 | float32 | 0          | 511                  |     |
|                      | LKAIntv_Cnt_T_logl       | boolean | FALSE      | TRUE                 |     |
|                      | MfgOvrlDi_Cnt_T_logl     | boolean | FALSE      | TRUE                 |     |
|                      | SysSt_Cnt_T_enum         | SysSt1  | SYSST_DI   | SYSST_WRMININ        |     |
|                      | \* LkaSt_Cnt_T_u08       | uint8   | 0          | 4                    |     |
| **Return Value**     | None                     |         |            |                      |     |

## Description

Implementation of all LKA state transitions.

‘\*LkaSt_Cnt_T_u08’ is the output of this function.

## Local Function \#12

|                      |                          |         |            |                      |     |
|-----------|----------------------|----------|-----------|--|------------------|
| **Function Name**    | EscStTran                | Type    | Min        |                      | Max |
| **Arguments Passed** | EscMfgEna_Cnt_T_logl     | boolean | FALSE      | TRUE                 |     |
|                      | EscFlt_Cnt_T_logl        | boolean | FALSE      | TRUE                 |     |
|                      | LoaSt_Cnt_T_enum         | boolean | LOAST_NORM | LOAST_IMDTSHTDWNREQD |     |
|                      | VehSpdSecurMax_Kph_T_f32 | boolean | 0          | 511                  |     |
|                      | EscEna_Cnt_T_logl        | boolean | FALSE      | TRUE                 |     |
|                      | EscLimdActv_Cnt_T_logl   | boolean | FALSE      | TRUE                 |     |
|                      | MfgOvrlDi_Cnt_T_logl     | boolean | FALSE      | TRUE                 |     |
|                      | SysSt_Cnt_T_enum         | SysSt1  | SYSST_DI   | SYSST_WRMININ        |     |
|                      | \* EscSt_Cnt_T_u08       | uint8   | 0          | 4                    |     |
| **Return Value**     | None                     |         |            |                      |     |

## Description

Implementation of all ESC state transitions.

‘\*EscSt_Cnt_T_u08’ is the output of this function.

## Local Function \#13

|                      |                             |         |       |      |     |
|-----------|----------------------|----------|-----------|--|------------------|
| **Function Name**    | HwAgServo                   | Type    | Min   |      | Max |
| **Arguments Passed** | HwAgTrajEna_Cnt_T_logl      | boolean | FALSE | TRUE |     |
|                      | ApaSt_Cnt_T_u08             | uint8   | 0     | 4    |     |
|                      | HwAgTraj_HwDeg_T_f32        | float32 | -1440 | 1440 |     |
|                      | HwAgTarLimd_HwDeg_T_f32     | float32 | -1440 | 1440 |     |
|                      | \* HwAgServoCmd_HwDeg_T_f32 | float32 | -1440 | 1440 |     |
| **Return Value**     | HwAgServoEna_Cnt_T_logl     | boolean | FALSE | TRUE |     |

## Description

Implementation of all ESC state transitions.

‘\*HwAgServoCmd_HwDeg_T_f32’ is the output of this function.

## Local Function \#14

|                      |                      |         |     |       |     |
|----------------------|----------------------|---------|-----|-------|-----|
| **Function Name**    | InctIgnCntrOnce      | Type    | Min |       | Max |
| **Arguments Passed** | IgnCntrLcl_Cnt_T_u16 | boolean | 0   | 65535 |     |
| **Return Value**     | N/A                  |         |     |       |     |

## Description

Implementation of “InctIgnCntrOnce” block

## Local Function \#15

|                      |                               |         |       |      |     |
|-----------|----------------------|----------|-----------|--|------------------|
| **Function Name**    | HwTqFildChk                   | Type    | Min   |      | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32           | float32 | -10.0 | 10.0 |     |
| **Return Value**     | HwTqFildWithinIntl_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Implementation of”HwTqFildIntlChk” block.

## Local Function \#16

|                      |                             |         |       |      |     |
|-----------|----------------------|----------|-----------|--|------------------|
| **Function Name**    | LKAIntv                     | Type    | Min   |      | Max |
| **Arguments Passed** | HwTq_HwNwtMtr_T_f32         | float32 | -10.0 | 10.0 |     |
|                      | LkaTqCmdCdnd_HwNwtMtr_T_f32 | float32 | -3.0  | 3.0  |     |
| **Return Value**     | LKAIntv_Cnt_T_logl          | boolean | FALSE | TRUE |     |

## Description

Implementation of “LKAIntv” block.

## Local Function \#17

|                      |                        |         |       |      |     |
|----------------------|------------------------|---------|-------|------|-----|
| **Function Name**    | LkaPrmntFlt            | Type    | Min   |      | Max |
| **Arguments Passed** | LkaFlt_Cnt_T_logl      | boolean | FALSE | TRUE |     |
| **Return Value**     | LkaPrmntFlt_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Calculates LkaPrmntFlt to be used in state transitions.

## Local Function \#18

|                      |                                     |         |       |      |     |
|-----------|------------------------|----------|-----------|--|-----------------|
| **Function Name**    | HaptcStTranActvToWaitFlg            | Type    | Min   |      | Max |
| **Arguments Passed** | None                                |         |       |      |     |
| **Return Value**     | HaptcStTranActvToWaitFlg_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Implementation of “HaptcStTranActvToWaitFlg” block.

## Local Function \#19

|                      |                                        |         |       |      |     |
|-----------|--------------------------|----------|----------|--|---------------|
| **Function Name**    | TranHaptcWaitToApaStActvFlg            | Type    | Min   |      | Max |
| **Arguments Passed** | None                                   |         |       |      |     |
| **Return Value**     | TranHaptcWaitToApaStActvFlg_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Implementation of TranHaptcWaitToApaStActvFlg_Cnt_T_logl block.

## Local Function \#20

|                      |                                |         |       |      |     |
|-----------|------------------------|----------|-----------|--|-----------------|
| **Function Name**    | EnHaptcFb                      | Type    | Min   |      | Max |
| **Arguments Passed** | \*HwOscnEna_Cnt_T_logl         | boolean | FALSE | TRUE |     |
|                      | \*HwOscnMotAmp_MotNwtMtr_T_f32 | float32 | 0     | 1.2  |     |
|                      | \*HwOscnFrq_Hz_T_f32           | float32 | 10    | 50   |     |
| **Return Value**     | None                           |         |       |      |     |

## Description

Implementation of “EnHaptcFb” block.

‘\*HwOscnEna_Cnt_T_logl , \* HwOscnMotAmp_MotNwtMtr_T_f32,
\*HwOscnFrq_Hz_T_f32 are the outputs of this function.

## Local Function \#21

|                      |                                   |         |       |       |     |
|-----------|------------------------|----------|-----------|--|-----------------|
| **Function Name**    | HaptcFbPostStrtUp                 | Type    | Min   |       | Max |
| **Arguments Passed** | ApaSt_Cnt_T_u08                   | uint8   | 0     | 4     |     |
|                      | HaptcSt_Cnt_T_u08                 | uint8   | 0     | 2     |     |
|                      | HwTqFildWithinIntl_Cnt_T_logl     | boolean | FALSE | TRUE  |     |
|                      | VehSpd_Kph_T_f32                  | float32 | 0     | 511   |     |
|                      | IgnCntrLcl_Cnt_T_u16              | uint16  | 0     | 65535 |     |
|                      | LoaStLimdOrSwBasdMtgtn_Cnt_T_logl | boolean | FALSE | TRUE  |     |
|                      | \*HwOscnEna_Cnt_T_logl            | boolean | FALSE | TRUE  |     |
|                      | \*HwOscnMotAmp_MotNwtMtr_T_f32    | float32 | 0     | 1.2   |     |
|                      | \*HwOscnFrq_Hz_T_f32              | float32 | 10    | 50    |     |
| **Return Value**     | None                              |         |       |       |     |

## Description

Implementation of "En Or Di HaptcFb After Checking At Start Up" block.

‘\*HwOscnEna_Cnt_T_logl , \* HwOscnMotAmp_MotNwtMtr_T_f32,
\*HwOscnFrq_Hz_T_f32 are the outputs of this function.

## Local Function \#22

|                      |                                     |         |       |      |     |
|-----------|------------------------|----------|-----------|--|----------------|
| **Function Name**    | ApaNrcvrlFlt                        | Type    | Min   |      | Max |
| **Arguments Passed** | Msg337BusChassisExpInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | Msg337BusChassisExpMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
| **Return Value**     | ApaNrcvrlFlt_Cnt_T_logl             | boolean | FALSE | TRUE |     |

## Description

Determine ApaNrcvrlFlt status.

## Local Function \#23

|                      |                                     |         |       |      |     |
|-----------|------------------------|----------|-----------|--|----------------|
| **Function Name**    | EscFlt                              | Type    | Min   |      | Max |
| **Arguments Passed** | Msg180BusChassisExpInvld_Cnt_T_logl | boolean | FALSE | TRUE |     |
|                      | Msg180BusChassisExpMiss_Cnt_T_logl  | boolean | FALSE | TRUE |     |
| **Return Value**     | EscFlt_Cnt_T_logl                   | boolean | FALSE | TRUE |     |

## Description

Determine EscFlt status.

## Local Function \#24

|                      |                         |         |       |      |     |
|----------------------|-------------------------|---------|-------|------|-----|
| **Function Name**    | LkaCheck                | Type    | Min   |      | Max |
| **Arguments Passed** | \*LkaFlt_Cnt_T_logl     | boolean | FALSE | TRUE |     |
|                      | \*LkaInhb_Cnt_T_logl    | boolean | FALSE | TRUE |     |
|                      | \*LkaPrmnFlt_Cnt_T_logl | boolean | FALSE | TRUE |     |

## Description

Implements LKA Check subsystem in model. The arguments to this function
are all returned as output.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

1.  DataDict.m includes a default value for GmLoaIgnCntr NVM. This is
    redundant because the design uses the NVM GetErrorStatus function
    call to determine if this NVM value should be set to its default
    value of 0.

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : CF009A\_ GmOvrlStMgr_Design                                                                                                                                     | See Synergy sub project version |

{% endraw %}