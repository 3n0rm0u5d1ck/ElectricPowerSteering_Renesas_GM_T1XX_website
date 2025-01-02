---
layout: default
title: StabyCmp_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**StabyCmp**

**Jan 27, 2017**

**Prepared By:**

**Shruthi Raghavan,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                               |                        |             |              |
|------------------------|---------------------|--------------|--------------|
| **Description**               | **Author**             | **Version** | **Date**     |
| Initial Version               | Sankardu Varadapureddi | 1.0         | 21-July-2015 |
| Updated for FDD version 1.1.0 | Sankardu Varadapureddi | 2.0         | 11-Mar-2016  |
| Updated to FDD version 1.3.0  | Shruthi Raghavan       | 3.0         | 27-Jan-2017  |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#section)](#section)

[2 StabyCmp High-Level Description
[5](#stabycmp-high-level-description)](#stabycmp-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of ‘StabyCmp’
[6](#_Toc425411990)](#_Toc425411990)

[3.2 Data Flow Diagram [6](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[6](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [6](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[7](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[7](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [7](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[8](#software-component-implementation)](#software-component-implementation)

[5.1.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.2 Interrupt Service Routines
[8](#interrupt-service-routines)](#interrupt-service-routines)

[5.1.3 Server Runnable Functions
[8](#server-runnable-functions)](#server-runnable-functions)

[5.1.4 Module Internal (Local) Functions
[8](#module-internal-local-functions)](#module-internal-local-functions)

[5.2 Local Function \#1 [8](#local-function-1)](#local-function-1)

[5.3 Description [8](#description)](#description)

[5.4 Local Function \#2 [9](#local-function-2)](#local-function-2)

[5.5 Description [9](#description-1)](#description-1)

[5.5.1 Transition Functions
[9](#transition-functions)](#transition-functions)

[6 Known Limitations with Design
[10](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[11](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[12](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [13](#glossary)](#glossary)

[Appendix C References [14](#references)](#references)

# Introduction

## Purpose

## 

Module design document for Stability Compensation.

# StabyCmp High-Level Description

*Refer FDD*

# Design details of software module

## Graphical representation of ‘StabyCmp’

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF029A_StabyCmp_Impl/doc/mediax/media/image1.png"
style="width:3.94167in;height:5.25in" />

## Data Flow Diagram

### 

### Component level DFD

> Refer FDD

### Function level DFD

> Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

> Refer .m file
>
> ***Local Constants***
>
> None

# Software Component Implementation

### Sub-Module Functions

##### Initialization sub-module {StabyCmpInit1}

##### 

**Design Rational:**

> FDD details are not complete for notch filter initialization. Upon
> discussion with FDD owner, implemented in line with EA3
> implementation.

#####  Periodic sub-module {StabyCmpPer1}

Refer FDD for details

> **Design Rational:**
>
> In design version 1.3.0, .m file has some additional PIMs for notch
> filters, which are not required in the notch filter implementation.
> Notch filter implementation in SW based on design 1.0.0 .m file PIMs
> is not changed.
>
> New FDD model was requested but this wasn’t done on time and due to
> time crunch the difference between implementation and the model still
> exists.

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

##### Local Function \#1

|                      |                    |                  |                             |     |     |
|------------------|----------------------|-----------------|-------|---------|--|
| **Function Name**    | FilNotchInit       | Type             | Min                         | Max |     |
| **Arguments Passed** | Inp                | float32          | See unit test consideration |     |     |
|                      | FilNotchStRecPtr   | FilNotchStRec1   |                             |     |     |
|                      | FilNotchGainRecPtr | FilNotchGainRec1 |                             |     |     |
| **Return Value**     | None               |                  |                             |     |     |

###### Description [description]

Notch filter initialization function implemented based on EA3 design.

##### Local Function \#2

|                      |                         |                  |                             |     |
|---------------|-------------------|--------------|-------------|------------|
| **Function Name**    | FilNotchFullUpdOutp_f32 | Type             | Min                         | Max |
| **Arguments Passed** | Inp                     | float32          | See unit test consideration |     |
|                      | FilNotchStRecPtr        | FilNotchStRec1   |                             |     |
|                      | FilNotchGainRecPtr      | FilNotchGainRec1 |                             |     |
| **Return Value**     | FilOut                  | float32          |                             |     |

###### Description [description-1]

> Notch filter output calculation. Implemented based on ‘Compensator1’
> block functionality. Compensator2, Compensator3 and Compensator4 also
> have the same functionality.

###  Transition Functions

None

# Known Limitations with Design

Design has 8 PIMs to represent notch filters and a model block for notch
filter has not been designed. This hasn’t been done yet in this revision
due to the need to baseline on time for builds. No anomaly has been
written but the Systems group was notified.

# UNIT TEST CONSIDERATION

Since the notch filter implementation used in this module is dynamic in
nature, absolute ranges are difficult to determine without pre-defined
knowledge on the combination of coefficient values (A1, A2, B0, B1, B2).
Because of this, the systems group ran simulations on 10 different
combinations of coefficients (2 with defined default calibrations, 8
considered extreme cases of notch filters) and logged the ranges of the
filter state variables and outputs during a frequency sweep. The ranges
given throughout this module were taken as the worst case results of all
of the given test cases.

To provide useful cases for unit testing, the boundary checks tested
during unit testing should be altered to test the state variable minimum
and maximum for each of the 10 test cases with the given coefficients
set to the values given in that test case. In the case where the default
values of the coefficients are used in a vector, the unit tester should
not test the corresponding state variables with values over the range
defined for that set of coefficients. See attached simulation results.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF029A_StabyCmp_Impl/doc/mediax/media/image2.emf)

(Note: this section is copied from EA3 Stability Compensation
documentation)

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

| **Ref. \#** | **Title**                                                                                                                                                               | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                      | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                           | EA4 01.00.00                    |
| 3           | EA4 [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc) | 01.00.00                        |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc)   | 2.1                             |
| 5           | FDD - SF029A_StabyCmp_Design                                                                                                                                            | See Synergy sub project version |

{% endraw %}