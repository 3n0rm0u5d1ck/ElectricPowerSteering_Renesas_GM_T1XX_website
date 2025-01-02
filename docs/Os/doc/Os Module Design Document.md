---
layout: default
title: Os Module Design Document
nav_order: 3
parent: OS
---
{% raw %}
**Module Design Document**

**For**

**Os**

**1/6/16**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |                |             |          |
|-----------------|----------------|-------------|----------|
| **Description** | **Author**     | **Version** | **Date** |
| Initial Version | Lucas Wendling | 1           | 1/6/16   |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[1.2 Scope [5](#scope)](#scope)

[2 Os & High-Level Description
[6](#high-level-description)](#high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of Os
[7](#graphical-representation-of-nxtroserrhndlg-expected-external-intefaces)](#graphical-representation-of-nxtroserrhndlg-expected-external-intefaces)

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

[5.1.1 Init: Os_Init\<n\> [9](#init)](#init)

[5.1.1.1 Design Rationale [9](#_Toc439862842)](#_Toc439862842)

[5.1.1.2 Module Outputs [9](#_Toc439862843)](#_Toc439862843)

[5.1.2 Per: Os_Per\<n\> [9](#per)](#per)

[5.1.2.1 Design Rationale [9](#_Toc439862845)](#_Toc439862845)

[5.1.2.2 Store Module Inputs to Local copies
[9](#_Toc439862846)](#_Toc439862846)

[5.1.2.3 (Processing of function)………
[9](#_Toc439862847)](#_Toc439862847)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#_Toc439862848)](#_Toc439862848)

[5.2 Server Runables [9](#server-runables)](#server-runables)

[5.2.1 \<Server Runable Name\> [9](#_Toc439862850)](#_Toc439862850)

[5.2.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.2.1.2 (Processing of function)………
[10](#_Toc439862852)](#_Toc439862852)

[5.3 Interrupt Functions
[10](#interrupt-functions)](#interrupt-functions)

[5.3.1 Interrupt Function Name [10](#_Toc439862854)](#_Toc439862854)

[5.3.1.1 Design Rationale [10](#_Toc439862855)](#_Toc439862855)

[5.3.1.2 (Processing of the ISR function)…..
[10](#_Toc439862856)](#_Toc439862856)

[5.4 Module Internal (Local) Functions
[10](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [10](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[10](#design-rationale-1)](#design-rationale-1)

[5.4.1.2 Processing [10](#processing-1)](#processing-1)

[5.5 GLOBAL Function/Macro Definitions
[10](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [10](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[11](#design-rationale-2)](#design-rationale-2)

[5.5.1.2 processing [11](#processing-2)](#processing-2)

[6 Known Limitations with Design
[12](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[13](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[14](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [15](#glossary)](#glossary)

[Appendix C References [16](#references)](#references)

# Introduction

## Purpose

This design document will capture the design of the Nexteer Os Error
Handling (NxtrOsErrHndlg) functionality. This is the only portion of
this component that is designed by Nexteer rather than a 3^rd^ party.

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# High-Level Description

The Nexteer designed portions of the Os component consist of the Os
error processing. This Nexteer specific design was embedded within the
Os component itself since this functionality is specifically tied to the
errors and names that this particular Os supports. This error handling
is expected to be called by the Os protection and error callout
functions in any given project. It interfaces with the Exception Handler
that is created to react to the different categories of Os errors.

# Design details of software module

*\<The Data Flow Diagrams should be created in the absence of this
representation with the FDD.\>*

## Graphical representation of NxtrOsErrHndlg (Expected External Intefaces)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/Os/doc/mediax/media/image1.emf)

## Data Flow Diagram

### Component level DFD

### Function level DFD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
| None          |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: 

*None*

###  [section]

## Per: 

*None*

## Server Runables 

## NxtrOsErrHndlg

## Design Rationale

*This runnable will parse through the different Os errors that can be
detected and interface into the Exception Handler component for handling
of the different categories of errors. This runnable is expected to be
called by both the Os ErrorHook and the Os ProtectionHook as it handles
all categories of Os errors.*

##  Processing

*switch (OSErrorGetosCANError())*

*case osdErrUEUnhandledException:*

*case osdErrUEUnhandledCoreException:*

*case osdErrUEUnhandledDirectBranch:*

*/\* Unhandled Exceptions \*/*

*ProcUkwnExcpnErr(OSErrorGetosCANError())*

*break*

*case osdErrEXMemoryViolation:*

*/\* MPU Violations \*/*

*ProcMpuExcpnErr(OSErrorGetosCANError());*

*break*

*case osdErrEXPrivilegedInstruction:*

*/\* Privileged Instruction Exceptions \*/*

*ProcPrvlgdInstrExcpnErr(OSErrorGetosCANError());*

*break*

*case osdErrATWrongTaskPrio:*

*case osdErrTTNotActivated:*

*case osdErrTTNoImmediateTaskSwitch:*

*case osdErrTTWrongActiveTaskID:*

*case osdErrHTNotActivated:*

*case osdErrHTNoImmediateTaskSwitch:*

*case osdErrHTWrongActiveTaskID:*

*case osdErrSHScheduleNotAllowed:*

*case osdErrSHWrongActiveTaskID:*

*case osdErrGSOddInvocation:*

*case osdErrGIOddInvocation:*

*case osdErrMTMissingTerminateTask:*

*case osdErrEAIntAPIWrongSequence:*

*case osdErrDAIntAPIDisabled:*

*case osdErrSDWrongCounter:*

*case osdErrREWrongCounter:*

*case osdErrSGWrongCounter:*

*case osdErrRGWrongCounter:*

*case osdErrGRPriorityOccupied:*

*case osdErrGRNoAccessRights:*

*case osdErrGRWrongTaskID:*

*case osdErrRRCeilingPriorityNotSet:*

*case osdErrRRWrongTask:*

*case osdErrRRNoReadyTaskFound:*

*case osdErrRRWrongTaskID:*

*case osdErrRRWrongHighRdyPrio:*

*case osdErrSEWrongTaskPrio:*

*case osdErrGEOddInvocation:*

*case osdErrCAAlarmInternal:*

*case osdErrWAWrongIDonHeap:*

*case osdErrWAHeapOverflow:*

*case osdErrWAUnknownAction:*

*case osdErrWAWrongCounterID:*

*case osdErrSOStackOverflow:*

*case osdErrSUWrongTaskID:*

*case osdErrCLWrongLibrary:*

*case osdErrEHInterruptsEnabled:*

*case osdErrSTMemoryError:*

*case osdErrSTNoImmediateTaskSwitch:*

*case osdErrSTWrongAppMode:*

*case osdErrSTConfigCRCError:*

*case osdErrSTConfigMagicNrError:*

*case osdErrSTInvalidMajorVersion:*

*case osdErrSTInvalidMinorVersion:*

*case osdErrSTInvalidSTCfg:*

*case osdErrQIWrongTaskPrio:*

*case osdErrQRInterruptsEnabled:*

*case osdErrQRWrongTaskID:*

*case osdErrQRWrongTaskPrio:*

*case osdErrQRWrongHighRdyPrio:*

*case osdErrQSInterruptsEnabled:*

*case osdErrQSNoReadyTaskFound:*

*case osdErrQSWrongPriority:*

*case osdErrQOWrongTaskID:*

*case osdErrSPUnknownCase:*

*case osdErrSGOddInvocation:*

*case osdErrWSUnknownAction:*

*case osdErrWSUnknownReaction:*

*case osdErrWSWrongID:*

*case osdErrGCOddInvocation:*

*case osdErrBMResAlreadyMeasured:*

*case osdErrBMInvalidProcessInStart:*

*case osdErrBMInvalidProcessInStop:*

*case osdErrBMInvalidResource:*

*case osdErrETNoCurrentProcess:*

*case osdErrASOddInvocation:*

*case osdErrTAInvalidTaskState:*

*case osdErrRSWrongTaskPrio:*

*case osdErrPAInvalidAreaIndex:*

*case osdErrPANoAccessRight:*

*case osdErrPAInvalidAddress:*

*case osdErrYOSystemStackOverflow:*

*case osdErrYOTaskStackOverflow:*

*case osdErrYOISRStackOverflow:*

*case osdErrSCWrongSysCallParameter:*

*case osdErrDPStartValidContext:*

*case osdErrDPResumeInvalidContext:*

*case osdErrDPInvalidTaskIndex:*

*case osdErrDPInvalidApplicationID:*

*case osdErrSUInvalidTaskIndex:*

*case osdErrSUInvalidIsrIndex:*

*case osdErrSUInvalidIsrPrioLevel:*

*case osdErrCIInvalidIsrIndex:*

*case osdErrCIInvalidIsrPrioLevel:*

*case osdErrCIInvalidApplicationID:*

*case osdErrCIMissingIntRequest:*

*case osdErrCIInterruptIsMasked:*

*case osdErrCIWrongIntPriority:*

*case osdErrPIGetIMRInvalidIndex:*

*case osdErrPISetIMRInvalidIndex:*

*case osdErrPIClearIMRInvalidIndex:*

*case osdErrPIWriteIMR8InvalidAddr:*

*case osdErrPIWriteIMR16InvalidAddr:*

*case osdErrPIWriteIMR32InvalidAddr:*

*case osdErrPISetICRMaskInvalidAddr:*

*case osdErrPIClearICRMaskInvalidAddr:*

*case osdErrPISetICRReqInvalidAddr:*

*case osdErrPIClearICRReqInvalidAddr:*

*case osdErrPIWriteICR8InvalidAddr:*

*case osdErrPIWriteICR16InvalidAddr:*

*case osdErrPIWriteICRxLoInvalidIndex:*

*case osdErrPIWriteICRxHiInvalidIndex:*

*case osdErrPIWriteICRx16InvalidIndex:*

*case osdErrCRInvalidSettingOSTM:*

*case osdErrCRInvalidSettingMPU:*

*/\* Fatal OS fault for assertion / syscheck errors - set data for reset
cause \*/*

*ProcPrmntOsErr(OSErrorGetosCANError())*

*break*

*default:*

*/\* Assumed to be a non-fatal OSEK fault - Set data for periodic sweep
up \*/*

*ProcNonCritOsErr(OSErrorGetosCANError())*

*break*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |     |      |     |     |
|----------------------|-----|------|-----|-----|
| **Function Name**    |     | Type | Min | Max |
| **Arguments Passed** |     |      |     |     |
|                      |     |      |     |     |
| **Return Value**     |     |      |     |     |

## Design Rationale

## Processing

## GLOBAL Function/Macro Definitions

## GLOBAL Function \#1

|                      |     |      |     |     |
|----------------------|-----|------|-----|-----|
| **Function Name**    |     | Type | Min | Max |
| **Arguments Passed** |     |      |     |     |
|                      |     |      |     |     |
| **Return Value**     |     |      |     |     |

## Design Rationale

## Processing

# Known Limitations with Design

\<Any known limitations with the design shall be documented clearly in
this section.\>

# UNIT TEST CONSIDERATION

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0               |

{% endraw %}