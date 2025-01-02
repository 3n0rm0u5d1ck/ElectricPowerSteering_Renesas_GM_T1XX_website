---
layout: default
title: TunSelnAuthy_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**TunSelnAuthy**

**June 17, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                           |              |             |
|---------------------------|--------------|-------------|
| **Description**           | **Author**   | **Date**    |
| Initial Version           | N. Saxton    | 09-Oct-2015 |
| Updated as per FDD v1.1.0 | Krishna Anne | 17-Jun-2016 |

**  
**

<u>Table of Contents</u>1 TunSelnAuthy High-Level Description 4

2 Design details of software module 5

2.1 Graphical representation of TunSelnAuthy 5

2.2 Data Flow Diagram 5

2.2.1 Component level DFD 5

2.2.2 Function level DFD 5

3 Constant Data Dictionary 6

3.1 Program (fixed) Constants 6

3.1.1 Embedded Constants 6

4 Software Component Implementation 7

4.1 Sub-Module Functions 7

4.1.1 Init: TunSelnAuthyInit1 7

4.1.1.1 Design Rationale 7

4.1.1.2 Module Outputs 7

4.2 Server Runables 7

4.2.1 RtCalChgReq 7

4.2.1.1 Design Rationale 7

4.2.1.2 (Processing of function)……… 7

4.2.2 XcpCalChgReq 7

4.2.2.1 Design Rationale 7

4.2.2.2 (Processing of function)……… 7

4.3 Interrupt Functions 7

4.3.1 Interrupt Function Name 7

4.4 Module Internal (Local) Functions 7

4.5 GLOBAL Function/Macro Definitions 7

5 Known Limitations with Design 9

6 UNIT TEST CONSIDERATION 10

Appendix A Abbreviations and Acronyms 11

Appendix B Glossary 12

Appendix C References 13

# TunSelnAuthy High-Level Description

*Refer FDD*

# Design details of software module

*Refer FDD*

## Graphical representation of TunSelnAuthy

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF023A_TunSelnAuthy_Impl/doc/mediax/media/image2.png"
style="width:3.06944in;height:3.15625in" />

## Data Flow Diagram

Refer FDD

### Component level DFD

Refer FDD

### Function level DFD

Refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name               | Resolution | Units | Value |
|-----------------------------|------------|-------|-------|
| Refer .m file for constants |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: TunSelnAuthyInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*None*

## Server Runables 

## RtCalChgReq

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## XcpCalChgReq

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

*None*

## Interrupt Function Name

*None*

## Module Internal (Local) Functions

None

## GLOBAL Function/Macro Definitions

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0                            |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                            |
| 5           | FDD – SF023A_TunSelnAuthy_Design                                                                                                                                      | See Synergy subproject version |

{% endraw %}