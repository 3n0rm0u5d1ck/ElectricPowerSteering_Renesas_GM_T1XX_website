---
layout: default
title: MotAg1Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Motor Angle 1 Measurement**

**June 19, 2015**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|             |                               |             |             |              |
|------|----------------------|----------------------|----------|-------------|
| **Sl. No.** | **Description**               | **Author**  | **Version** | **Date**     |
| 1           | Initial Version               | Rijvi Ahmed | 1.0         | 13-July-2015 |
| 2           | Updated for FDD rev. 02.01.00 | Rijvi Ahmed | 2.0         | 06-Oct-2015  |
| 3           | Updated per FDD rev. 02.03.00 | Rijvi Ahmed | 3.0         | 08-Dec-2015  |

<u>Table of Contents</u>

[**1** **MotAg1Meas & High-Level Description
5**](#motag1meas-high-level-description)

[2 Design details of software module
6](#design-details-of-software-module)

[2.1.1.1 Graphical representation of CDD_MotAg1Meas
6](#graphical-representation-of-cdd_motag1meas)

[2.1.1.2 Data Flow Diagram 6](#data-flow-diagram)

[2.1.2 Component level DFD 6](#component-level-dfd)

[2.1.3 Function level DFD 6](#function-level-dfd)

[3 Constant Data Dictionary 7](#constant-data-dictionary)

[3.1.1.1 Program (fixed) Constants 7](#program-fixed-constants)

[3.1.2 Embedded Constants 7](#embedded-constants)

[4 Software Component Implementation
8](#software-component-implementation)

[4.1.1 Sub-Module Functions 8](#sub-module-functions)

[4.1.1.1 Init: MotAg1MeasInit1 8](#init-motag1measinit1)

[4.1.1.2 Per: MotAg1MeasPer1 8](#per-motag1measper1)

[4.1.1.3 Per: MotAg1MeasPer2 9](#per-motag1measper2)

[4.1.2 Interrupt Service Routines 9](#interrupt-service-routines)

[4.1.3 Server Runnable Functions 9](#server-runnable-functions)

[4.1.3.1 MotAg1MeasMotAg1CoeffTblRead 9](#motag1measmotag1coefftblread)

[4.1.3.1.1 Design Rationale 9](#design-rationale-3)

[4.1.3.1.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies-2)

[4.1.3.1.3 (Processing of function)……… 9](#processing-of-function-2)

[4.1.3.1.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs-2)

[4.1.3.2 MotAg1MeasMotAg1CoeffTblWr 9](#motag1measmotag1coefftblwr)

[4.1.3.2.1 Design Rationale 9](#design-rationale-4)

[4.1.3.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies-3)

[4.1.3.2.3 (Processing of function)……… 10](#processing-of-function-3)

[4.1.3.2.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-3)

[4.1.4 Module Internal (Local) Functions
10](#module-internal-local-functions)

[4.1.5 Local Function \#1 10](#local-function-1)

[4.1.5.1 Design Rationale 10](#design-rationale-5)

[4.1.6 Transition Functions 10](#transition-functions)

[5 Known Limitations with Design 11](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION 12](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 13](#abbreviations-and-acronyms)

[Appendix B Glossary 14](#glossary)

[Appendix C References 15](#references)

# MotAg1Meas & High-Level Description

The CDD_MotAg1Meas component is the complex driver for the motor angle 1
measurement subsystem. This function initializes the registers for CSIH3
SPI channel for communicating with the motor angle 1 measurement sensor
board. The SPI transmission is triggered periodically by DMA component.
This function receives the RAW sensor data at 62.5uS rate. The component
contains two source files, both described in this MDD: CDD_MotAg1Meas.c
contains the RTE runnables and services; CDD_MotAg1Meas_MotCtrl.c
contains the motor control runnable.

# Design details of software module

*See FDD.*

## Graphical representation of CDD_MotAg1Meas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM640A_MotAg1Meas_Impl/doc/mediax/media/image1.png"
style="width:3.55in;height:1.74167in" />

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

|                              |            |       |           |
|------------------------------|------------|-------|-----------|
| Constant Name                | Resolution | Units | Value     |
| ARYIDXRAWERRREG_CNT_U08      | 1          | Cnt   | 0u        |
| ARYIDXRAWTURNCNTRREG_CNT_U08 | 1          | Cnt   | 1u        |
| ARYIDXRAWAGREG_CNT_U08       | 1          | Cnt   | 2u        |
| SIXTEENBITMAXVAL_CNT_U16     | 1          | Cnt   | 65535U    |
| MOTAGRAWRESHILIM_CNT_U32     | 1          | Cnt   | 67108863U |

**\* Also see see FDD – CM640A_MotAg1Meas_DataDict.m file**

# Software Component Implementation

\<The detailed design of the function is provided in the FDD. The detail
design shall only be added to the MDD when it is not provided in the FDD
or the FDD is not adequate and clarification is needed.\>

### Sub-Module Functions

## Init: MotAg1MeasInit1

##### **Design Rationale**

All register initialization that is allowed at the register level (see
Register/Field coloumn of the
CM640A_MotAg1Meas_RegisterConfiguration.xlsm spreadsheet in the FDD) is
done at the register level to save execution time as compared to the
read/modify/writes that would be needed to initialize at the field
level. Field level initialization done only where required by the
spreadsheet.

##### **Module Outputs**

See FDD: MotAg1MeasInit1 model block.

##### **Module Internal** 

See FDD: MotAg1MeasInit1 model block for Per Instance Memory.

## Per: MotAg1MeasPer1

##### Design Rationale

> For run time efficiency in the motor control loop the **Compensate
> MechMtrPos** block is implemented in a optimized way in the code by
> letting a uint16 variable be overflown.

##### Store Module Inputs to Local copies

> See FDD: MotAg1MeasPer1 model block.

##### (Processing of function)………

> See FDD: MotAg1MeasPer1 model block.

##### Store Local copy of outputs into Module Outputs

> See FDD: MotAg1MeasPer1 model block

## Per: MotAg1MeasPer2

##### Design Rationale

> None

##### Store Module Inputs to Local copies

> See FDD: MotAg1MeasPer2 model block.

##### (Processing of function)………

> See FDD: MotAg1MeasPer2 model block.

##### Store Local copy of outputs into Module Outputs

> See FDD: MotAg1MeasPer2 model block

### Interrupt Service Routines

None

### Server Runnable Functions

## MotAg1MeasMotAg1CoeffTblRead

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See* MotAg1MeasMotAg1CoeffTblRead*block in the FDD*

## Store Local copy of outputs into Module Outputs

*None*

## MotAg1MeasMotAg1CoeffTblWr

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See* MotAg1MeasMotAg1CoeffTblWr*block in the FDD*

## Store Local copy of outputs into Module Outputs

*See* MotAg1MeasMotAg1CoeffTblWr*block in the FDD*

### Module Internal (Local) Functions

##  Local Function \#1

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | CalcCorrnTbl | Type | Min | Max |
| **Arguments Passed** | None         | N/A  | N/A | N/A |
| **Return Value**     | N/A          | N/A  | N/A | N/A |

## Design Rationale

See “Calculate Correction Table” block in the Simulink model of the
design.

### Transition Functions

None.

# Known Limitations with Design

> None.

# UNIT TEST CONSIDERATION

Following variables are used as rolling counters, so the overflow of
these variables is intentional.

Rte_Pim_MotAg1ErrParFltCntPrev

Rte_Pim_MotAg1VltgFltCntPrev

Rte_Pim_MotAg1ParFltCntPrev

Rte_Pim_MotAg1MeclRollgCntrPrev

There is an unreachable code in the SinCos_f32() function, because the
input of this function is always positive. This is ok as the
SinCos_f32() is a library function.

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
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                            |
| 5           | FDD: CM640A_MotAg1Meas_Design                                                                                                                                 | See Synergy subproject version |

{% endraw %}