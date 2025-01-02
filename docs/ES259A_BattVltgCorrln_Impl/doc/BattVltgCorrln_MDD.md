---
layout: default
title: BattVltgCorrln_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**BattVltgCorrln**

**May 24, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Nick Saxton,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

|                       |                        |             |             |
|-----------------------|------------------------|-------------|-------------|
| **Description**       | **Author**             | **Version** | **Date**    |
| Initial Version       | N. Saxton              | 1.00.00     | 08-Jul-2015 |
| Updated for FDD 1.2.2 | N. Saxton              | 2.00.00     | 06-Aug-2015 |
| Updated for FDD 1.4.0 | Sankardu Varadapureddi | 3           | 21-Mar-2016 |
| Updated for FDD 2.0.0 | N. Saxton              | 4           | 24-May-2016 |

**<u>Table of Contents</u>**

[1 BattVltgCorrln & High-Level Description
4](#battvltgcorrln-high-level-description)

[2 Design details of software module
5](#design-details-of-software-module)

[2.1 Graphical representation of BattVltgCorrln
5](#graphical-representation-of-battvltgcorrln)

[2.2 Data Flow Diagram 5](#data-flow-diagram)

[2.2.1 Component level DFD 5](#component-level-dfd)

[2.2.2 Function level DFD 5](#function-level-dfd)

[3 Constant Data Dictionary 6](#constant-data-dictionary)

[3.1 Program (fixed) Constants 6](#program-fixed-constants)

[3.1.1 Embedded Constants 6](#embedded-constants)

[4 Software Component Implementation
7](#software-component-implementation)

[4.1.1 Sub-Module Functions 7](#sub-module-functions)

[4.1.2 Interrupt Service Routines 7](#interrupt-service-routines)

[4.1.3 Server Runnable Functions 7](#server-runnable-functions)

[4.1.4 Module Internal (Local) Functions
7](#module-internal-local-functions)

[4.1.5 Transition Functions 9](#transition-functions)

[5 Known Limitations with Design 10](#known-limitations-with-design)

[6 UNIT TEST CONSIDERATION 11](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 12](#abbreviations-and-acronyms)

[Appendix B Glossary 13](#glossary)

[Appendix C References 15](#references)

# BattVltgCorrln & High-Level Description

This function determines the correlation between three input signals
(battery voltage, switched battery voltage 1, and switched battery
voltage 2) to conclude their validities.

# Design details of software module

## Graphical representation of BattVltgCorrln

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES259A_BattVltgCorrln_Impl/doc/mediax/media/image2.png"
style="width:4.91736in;height:4.71736in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                  |            |       |       |
|----------------------------------|------------|-------|-------|
| Constant Name                    | Resolution | Units | Value |
| BATTVLTGIDPTSIGLOLIMIT_CNT_U08   | None       | NA    | 0     |
| BATTVLTGIDPTSIGHILIMIT \_CNT_U08 | None       | NA    | 3     |

\* Refer FDD for other constant definition

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module {\_Init()}

None

#### Periodic sub-module {\_Per()}

##### BattVltgCorrlnPer1

###### Design Rationale

Refer to FDD

###### Store module inputs to local copies

Refer to FDD

###### (Processing of function)……

Refer to FDD

###### Store local copy of outputs into module outputs

Refer FDD

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

#### Local Function \#1

|                      |                                 |         |       |      |
|--------------|--------------------------------|----------|---------|---------|
| **Function Name**    | InstCorrln                      | Type    | Min   | Max  |
| **Arguments Passed** | Vltg_Volt_T_f32                 | float32 | 0     | 40   |
|                      | VltgSwd1_Volt_T_f32             | float32 | 0     | 40   |
|                      | VltgSwd2_Volt_T_f32             | float32 | 0     | 40   |
|                      | BattVltgAdcFaild_Cnt_T_logl     | boolean | FALSE | TRUE |
|                      | BattVltgSwd1AdcFaild_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | BattVltgSwd2AdcFaild_Cnt_T_logl | boolean | FALSE | TRUE |
|                      | \*VltgOk_Cnt_T_u08              | uint8   | 0     | 1    |
|                      | \*Swd1Ok_Cnt_T_u08              | uint8   | 0     | 1    |
|                      | \*Swd2Ok_Cnt_T_u08              | uint8   | 0     | 1    |
| **Return Value**     | BattSwdVltgLimd_Cnt_T_logl      | boolean | FALSE | TRUE |

##### Description

Refer FDD

#### Local Function \#2

|                      |                               |       |               |               |
|-------------|-----------------------------|----------|-----------|-----------|
| **Function Name**    | DetIdptSig                    | Type  | Min           | Max           |
| **Arguments Passed** | Ntc0x3CQlfrSts_Cnt_T_enum     | enum  | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | Ntc044QlfrSts_Cnt_T_enum      | enum  | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | Ntc0x4CQlfrSts_Cnt_T_enum     | enum  | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*VltgNotFailed_Cnt_T_u08     | uint8 | 0             | 1             |
|                      | \*VltgSwd1NotFailed_Cnt_T_u08 | uint8 | 0             | 1             |
|                      | \*VltgSwd2NotFailed_Cnt_T_u08 | uint8 | 0             | 1             |
| **Return Value**     | VltgCorrlnIdptSig_Cnt_T_u08   | uint8 | 0             | 3             |

##### Description

This function implements the Determine Independent Signals block in the
FDD but with a few differences. Instead of implementing the truth table
as shown in the FDD, each signal “not failed” variable is set based on
the signal’s OK status. Once a signal is considered “not failed”, the
variable representing the number of independent signals is incremented.
However, while possible in the code, it is not possible for a situation
to arise in which there is only one independent signal, therefore a
check is performed at the end of this function to set the number of
independent signals to 0 and each “not failed” variable to FALSE if this
situation occurs.

#### Local Function \#3

|                      |                               |         |       |      |
|----------------------|-------------------------------|---------|-------|------|
| **Function Name**    | GetCorrlnSts                  | Type    | Min   | Max  |
| **Arguments Passed** | VltgNotFailed_Cnt_T_u08       | uint8   | 0     | 1    |
|                      | VltgSwd1NotFailed_Cnt_T_u08   | uint8   | 0     | 1    |
|                      | VltgSwd2NotFailed_Cnt_T_u08   | uint8   | 0     | 1    |
|                      | VltgOk_Cnt_T_u08              | uint8   | 0     | 1    |
|                      | Swd1Ok_Cnt_T_u08              | uint8   | 0     | 1    |
|                      | Swd2Ok_Cnt_T_u08              | uint8   | 0     | 1    |
|                      | \* DftBrdgVltgActv_Cnt_T_logl | boolean | FALSE | TRUE |
| **Return Value**     | CorrlnSts_Cnt_T_u08           | uint8   | 0     | 7    |

\* DftBrdgVltgActv_Cnt_T_logl is an output of this function.

##### Description

Refer FDD

#### Local Function \#4

|                      |                      |         |       |      |
|----------------------|----------------------|---------|-------|------|
| **Function Name**    | DetSwdSat            | Type    | Min   | Max  |
| **Arguments Passed** | VltgSwd1_Volt_T_f32  | float32 | 0     | 40   |
|                      | VltgSwd2_Volt_T_f32  | float32 | 0     | 40   |
|                      | VltgSwd1Ok_Cnt_T_u08 | uint8   | 0     | 1    |
|                      | VltgSwd2Ok_Cnt_T_u08 | uint8   | 0     | 1    |
| **Return Value**     | SwdSat_Cnt_T_lgc     | boolean | FALSE | TRUE |

##### Description

This function determines if switched battery voltages have reached
saturation voltage and was created to reduce cyclomatic complexity and
static path count of the Instantaneous Correlation subfunction.

#### Local Function \#5

|                      |                           |         |               |               |
|-------------|-----------------------------|----------|-----------|-----------|
| **Function Name**    | DetNtcQlfrSts             | Type    | Min           | Max           |
| **Arguments Passed** | Invtr1Inctv_Cnt_T_logl    | boolean | FALSE         | TRUE          |
|                      | Invtr2Inctv_Cnt_T_logl    | boolean | FALSE         | TRUE          |
|                      | VltgOk_Cnt_T_u08          | uint8   | 0             | 1             |
|                      | Swd1Ok_Cnt_T_u08          | uint8   | 0             | 1             |
|                      | Swd2Ok_Cnt_T_u08          | uint8   | 0             | 1             |
|                      | \*Ntc3CQlfrSts_Cnt_T_enum | enum    | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*Ntc3CQlfrSts_Cnt_T_enum | enum    | SIGQLFR_NORES | SIGQLFR_FAILD |
|                      | \*Ntc3CQlfrSts_Cnt_T_enum | enum    | SIGQLFR_NORES | SIGQLFR_FAILD |

##### Description

This function implements the NTC \<xx\> blocks in the Determine
Independent Signals subfunction. It sets each NTC status based on the OK
status of each voltage signal. Then, the NTC qualifier status for each
signal is retrieved and saved in the corresponding enum parameter. This
function was created to reduce complexity and static path count of the
Determine Independent Signals subfunction.

#### Local Function \#6

|                      |                    |         |       |      |
|----------------------|--------------------|---------|-------|------|
| **Function Name**    | FlgChk             | Type    | Min   | Max  |
| **Arguments Passed** | FlgIn_Cnt_T_logl   | boolean | FALSE | TRUE |
|                      | \*FlgOut_Cnt_T_u08 | uint8   | 0     | 1    |
|                      |                    |         |       |      |

\*FlgOut_Cnt_T_u08 is an output of this function.

##### Description

If Input flag is 'TRUE', then set output flag to 'FASLE'. Otherwise
don't do anything. This function is added to reduce cyclomatic
complexity of 'InstCorrln' function.

#### Local Function \#7

|                      |                       |         |     |     |
|----------------------|-----------------------|---------|-----|-----|
| **Function Name**    | RngChk                | Type    | Min | Max |
| **Arguments Passed** | Vltg_Volt_T_f32       | float32 | 0   | 40  |
|                      | VltgSwd1_Volt_T_f32   | float32 | 0   | 40  |
|                      | VltgSwd2_Volt_T_f32   | float32 | 0   | 40  |
|                      | \*VltgRngOk_Cnt_T_u08 | uint8   | 0   | 1   |
|                      | \*Swd1RngOk_Cnt_T_u08 | uint8   | 0   | 1   |
|                      | \*Swd2RngOk_Cnt_T_u08 | uint8   | 0   | 1   |

\*VltgRngOk_Cnt_T_u08, \*Swd1RngOk_Cnt_T_u08 and \*Swd2RngOk_Cnt_T_u08
are outputs of this function.

##### Description

Implements “Range Check” block in the model. Created to reduce
cyclomatic complexity and static path count.

### Transition Functions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

None

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 2.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.1                            |
| 5           | FDD – ES259A Battery or Switched Voltage Correlation                                                                                                          | See Synergy subproject version |

{% endraw %}