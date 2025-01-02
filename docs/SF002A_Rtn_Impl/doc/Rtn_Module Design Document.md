---
layout: default
title: Rtn_Module Design Document
nav_order: 4
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**Return**

**Nov 29, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI**

**CHENNAI, INDIA**

**  
<u>Change History</u>**

|                               |            |             |             |
|-------------------------------|------------|-------------|-------------|
| **Description**               | **Author** | **Version** | **Date**    |
| Initial Version               | SB         | 1           | 30-Jun-2015 |
| Updated per design rev. 2.0.0 | TATA       | 2.0         | 29-Nov-2016 |

<u>Table of Contents</u>

1 Introduction 3

1.1 Purpose 3

2 Rtn High-Level Description 4

3 Design details of software module 5

3.1 Graphical representation of Rtn 5

3.2 Data Flow Diagram 5

3.2.1 Component level DFD 5

3.2.2 Function level DFD 5

4 Constant Data Dictionary 6

4.1 Program (fixed) Constants 6

4.1.1 Embedded Constants 6

5 Software Component Implementation 7

5.1.1 Sub-Module Functions 7

5.1.2 Interrupt Service Routines 7

5.1.3 Server Runnable Functions 7

5.1.4 Module Internal (Local) Functions 7

5.1.5 Transition Functions 7

6 Known Limitations with Design 8

7 UNIT TEST CONSIDERATION 9

Appendix A Abbreviations and Acronyms 10

Appendix B Glossary 11

Appendix C References 12

# Introduction

## Purpose

MDD for Return

##  

# Rtn High-Level Description

Refer to FDD

# Design details of software module

## Graphical representation of Rtn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF002A_Rtn_Impl/doc/mediax/media/image2.jpeg"
style="width:3.03125in;height:5.77083in"
alt="C:\Component\SF002A_Rtn_Impl_1.4.2\snapp.JPG" />

## Data Flow Diagram

### Component level DFD

Refer to FDD

### Function level DFD

Refer to FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

None

# Software Component Implementation

### Sub-Module Functions

#### Initialization sub-module RtnInit1 

#### 

#### Periodic sub-module RtnPer1

Design Rationale - *Fault Injection client call is conditional compiled
based on “FLTINJENA” build constant.*

### Interrupt Service Routines

None

### Server Runnable Functions

None

### Module Internal (Local) Functions

None

### Transition Functions

None

# Known Limitations with Design

None

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD – SF002A_Rtn_Design                                                                                                                                               | See Synergy Sub project version |

{% endraw %}