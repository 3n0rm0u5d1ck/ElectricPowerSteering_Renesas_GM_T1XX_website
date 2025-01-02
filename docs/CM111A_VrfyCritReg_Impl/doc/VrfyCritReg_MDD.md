---
layout: default
title: VrfyCritReg_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**VrfyCritReg**

**Apr 14, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Selva Sengottaiyan**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                                       |                        |             |             |
|------------------------|---------------------|--------------|--------------|
| **Description**                                                       | **Author**             | **Version** | **Date**    |
| Initial Version                                                       | Sankardu Varadapureddi | 1           | 14-Jan-2016 |
| Updated to “ Critical register” checks at init and periodic functions | Selva Sengottaiyan     | 2           | 14-Apr-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 VrfyCritReg High-Level Description
[6](#vrfycritreg-high-level-description)](#vrfycritreg-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of VrfyCritReg
[7](#graphical-representation-of-vrfycritreg)](#graphical-representation-of-vrfycritreg)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: VrfyCritRegInit1
[9](#init-vrfycritreginit1)](#init-vrfycritreginit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: VrfyCritRegPer1
[9](#per-vrfycritregper1)](#per-vrfycritregper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.3 Interrupt Functions
[9](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[9](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#2 [9](#section)](#section)

[5.4.1.1 Description [9](#section-1)](#section-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[11](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[12](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[13](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [14](#glossary)](#glossary)

[Appendix C References [15](#references)](#references)

# Introduction

## Purpose

## Scope

# VrfyCritReg High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of VrfyCritReg

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM111A_VrfyCritReg_Impl/doc/mediax/media/image1.png"
style="width:1.83333in;height:1.55in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

Refer .m file

#### Local Constants

| Constant Name         | Data Type | Value |
|-----------------------|-----------|-------|
| SYSCRITREGFLT_CNT_U08 | uint8     | 2     |
| CRITREGFLT_CNT_U08    | uint8     | 1     |
| NOFLT_CNT_U08         | uint8     | 0     |
|                       |           |       |
|                       |           |       |
|                       |           |       |
|                       |           |       |

# Software Component Implementation

## Sub-Module Functions

## Init: VrfyCritRegInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*None*

## Per: VrfyCritRegPer1

## Design Rationale

Refer FDD

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                                          |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | SysCritReg\<Register Short Name\>IninChk | Type    | Min   |      | Max |
| **Arguments Passed** | NA                                       |         |       |      |     |
| **Return Value**     | &SysRegsOk_Uls_T_lgc                     | boolean | FALSE | TRUE |     |

## Description

Set ' SysRegsOk_Uls_T_lgc to FALSE if CPU System Register values are not
equal to expected values. This is configured to be called from trusted
function because it needs to run in supervisor mode

## Local Function \#2

|                      |                                         |         |       |      |     |
|--------------|---------------------|--------------|------------|--|-----------|
| **Function Name**    | SysCritReg\<Register Short Name\>PerChk | Type    | Min   |      | Max |
| **Arguments Passed** | NA                                      |         |       |      |     |
| **Return Value**     | &SysRegsOk_Uls_T_lgc                    | boolean | FALSE | TRUE |     |

## Description

Set ' SysRegsOk_Uls_T_lgc to FALSE if CPU System Register values are not
equal to expected values. This is configured to be called from trusted
function because it needs to run in supervisor mode

## 

|     |     |     |     |     |     |
|-----|-----|-----|-----|-----|-----|
|     |     |     |     |     |     |
|     |     |     |     |     |     |
|     |     |     |     |     |     |

## 

## GLOBAL Function/Macro Definitions

## Global Function \#1

|                      |                        |       |     |     |     |
|----------------------|------------------------|-------|-----|-----|-----|
| **Function Name**    | CritRegPerChk          | Type  | Min |     | Max |
| **Arguments Passed** | NA                     |       |     |     |     |
| **Return Value**     | NtcParamInfo_Cnt_T_u08 | uint8 | 0U  | 2U  |     |

## Description

Set ' NtcParamInfo_Cnt_T_u08 to 1 if CPU Non System Register values are
not values. Set ' NtcParamInfo_Cnt_T_u08 to 2 if CPU System Register
values are not equal to expected values. Set ' NtcParamInfo_Cnt_T_u08 to
0 if none of the above conditions are true. This is configured as a
trusted function because it needs to run in supervisor mode

## Global Function \#2

|                      |                        |       |     |     |     |
|----------------------|------------------------|-------|-----|-----|-----|
| **Function Name**    | CritRegInitChk         | Type  | Min |     | Max |
| **Arguments Passed** | NA                     |       |     |     |     |
| **Return Value**     | NtcParamInfo_Cnt_T_u08 | uint8 | 0U  | 2U  |     |

## Description

Set ' NtcParamInfo_Cnt_T_u08 to 1 if CPU Non System Register values are
not equal to expected values. Set ' NtcParamInfo_Cnt_T_u08 to 2 if CPU
System Register values are not equal to expected values. Set '
NtcParamInfo_Cnt_T_u08 to 0 if none of the above conditions are true.
This is configured as a trusted function because it needs to run in
supervisor mode

## Global Function \#3

|                      |                     |         |       |      |     |
|----------------------|---------------------|---------|-------|------|-----|
| **Function Name**    | SysCritRegIninChk   | Type    | Min   |      | Max |
| **Arguments Passed** | NA                  |         |       |      |     |
| **Return Value**     | SysRegsOk_Uls_T_lgc | boolean | FALSE | TRUE |     |

## Description

Set ' SysRegsOk_Uls_T_lgc to FALSE if CPU System Register values are not
equal to expected values. This is configured to be called from trusted
function because it needs to run in supervisor mode

## Global Function \#4

|                      |                     |         |       |      |     |
|----------------------|---------------------|---------|-------|------|-----|
| **Function Name**    | SysCritRegPerChk    | Type    | Min   |      | Max |
| **Arguments Passed** | NA                  |         |       |      |     |
| **Return Value**     | SysRegsOk_Uls_T_lgc | boolean | FALSE | TRUE |     |

## Description

Set ' SysRegsOk_Uls_T_lgc to FALSE if CPU System Register values are not
equal to expected values. This is configured to be called from trusted
function because it needs to run in supervisor mode

# Known Limitations with Design

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
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | EA4 01.00.01                    |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : CM111A_VrfyCritReg_Design                                                                                                                                       | See Synergy sub project version |

{% endraw %}