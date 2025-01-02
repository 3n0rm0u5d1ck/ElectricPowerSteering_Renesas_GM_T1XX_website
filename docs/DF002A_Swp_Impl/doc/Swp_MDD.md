---
layout: default
title: Swp_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Swp**

**Jan 20, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Kanth Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                          |                    |             |             |
|--------------------------|--------------------|-------------|-------------|
| **Description**          | **Author**         | **Version** | **Date**    |
| Initial Version          | Krishna Kanth Anne | 1.0.0       | 20-Oct-2015 |
| Fix for anomaly EA4#2461 | Krishna Kanth Anne | 1.1.0       | 20-Jan-2016 |

**  
**

**<u>Table of Contents</u>**

[1 Introduction [4](#introduction)](#introduction)

[1.1 Purpose [4](#purpose)](#purpose)

[1.2 Scope [4](#scope)](#scope)

[2 PullCmpActv & High-Level Description
[5](#swp-high-level-description)](#swp-high-level-description)

[3 Design details of software module
[6](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of PullCmpActv
[6](#graphical-representation-of-swp)](#graphical-representation-of-swp)

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

[5.1 Sub-Module Functions
[8](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: SwpInit1 [8](#init-swpinit1)](#init-swpinit1)

[5.1.2 Per: SwpPer1 [8](#per-swpper1)](#per-swpper1)

[5.1.3 Per: SwpPer2 [8](#per-swpper2)](#per-swpper2)

[5.2 Module Internal (Local) Functions
[8](#_Toc429993457)](#_Toc429993457)

[5.2.1 Local Function \#1 [8](#_Toc429993458)](#_Toc429993458)

[5.2.1.1 Design Rationale [8](#_Toc429993459)](#_Toc429993459)

[5.2.1.2 Processing [8](#_Toc429993460)](#_Toc429993460)

[6 Known Limitations with Design
[9](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[10](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[11](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [12](#glossary)](#glossary)

[Appendix C References [13](#references)](#references)

# Introduction

## Purpose

MDD for Sweep function

## Scope

> NA

# Swp & High-Level Description

> Please refer FDD.

# Design details of software module

> Please refer FDD.

## Graphical representation of Swp

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/DF002A_Swp_Impl/doc/mediax/media/image2.png"
style="width:2.68056in;height:3.32373in" />

## Data Flow Diagram

> Please refer FDD.

### Component level DFD

> Please refer FDD.

### Function level DFD

> Please refer FDD.

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                      | Resolution | Units | Value |
|------------------------------------|------------|-------|-------|
| Please refer DF002A_Swp_DataDict.m | NA         | NA    | NA    |
| SWPSTRT_CNT_U16                    | NA         | NA    | 0     |
| SWPTRAN_CNT_U16                    | NA         | NA    | 1     |
| SWPDWELL_CNT_U16                   | NA         | NA    | 2     |
| SWPSTOP_CNT_U16                    | NA         | NA    | 3     |
| SWPRAMP_CNT_U16                    | NA         | NA    | 4     |
| SWPDONE_CNT_U16                    | NA         | NA    | 5     |

# Software Component Implementation

> Please refer FDD.

## Sub-Module Functions

## Init: SwpInit1

> Please refer FDD.

## Design Rationale

> Dummy Initialization function to correlate with the FDD (.m file)

## Per: SwpPer1

> Please refer FDD.

## Design Rationale

1.  For DFs, it was decided to use the module level variables in place
    of PIMs defined in the FDD (PIM section of .m file), This is a
    deviation from regular EA4 process. This is to give control over
    MemMap to avoid MPU violations while writing these variables using
    xcp.

2.  All of the given PIMs from .m file are either defined as of Function
    level variables (if used in only one function) or Module level
    variables (if used in more than one function) in DFs.

3.  Each of the Function level and Module level variables shall be
    volatile only when they are intended to be user modifiable as per
    the data dictionary .m file.

4.  Deviations exist in the naming conventions for all of Function level
    and Module level variables from regular EA4 naming conventions.

## Per: SwpPer2

> Please refer FDD.

## Design Rationale

1.  For DFs, it was decided to use the module level variables in place
    of PIMs defined in the FDD (PIM section of .m file), This is a
    deviation from regular EA4 process. This is to give control over
    MemMap to avoid MPU violations while writing these variables using
    xcp.

2.  All of the given PIMs from .m file are either defined as of Function
    level variables (if used in only one function) or Module level
    variables (if used in more than one function) in DFs.

3.  Each of the Function level and Module level variables shall be
    volatile only when they are intended to be user modifiable as per
    the data dictionary .m file.

4.  Deviations exist in the naming conventions for all of Function level
    and Module level variables from regular EA4 naming conventions.

# Known Limitations with Design

None.

# UNIT TEST CONSIDERATION

1.  Please refer Init.txt file in the FDD design: DF002A_Swp_Design for
    initial values of Function level and Module level variables.

2.  For DFs, it was decided to use the module level variables in place
    of PIMs defined in the FDD (PIM section of .m file), This is a
    deviation from regular EA4 process.

3.  All of the given PIMs from .m file are either defined as of Function
    level variables (if used in only one function) or Module level
    variables (if used in more than one function) in DFs.

4.  Each of the Function level and Module level variables shall be
    volatile only when they are intended to be user modifiable as per
    the data dictionary .m file.

5.  Deviations exist in the naming conventions for all of Function level
    and Module level variables from regular EA4 naming conventions.

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.0                            |
| 5           | FDD: SF002A_Swp_Design                                                                                                                                                | See Synergy SubProject version |

{% endraw %}