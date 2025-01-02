---
layout: default
title: HowDetn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HowDetn**

**December 01, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**TATA ELXSI,**

**CHENNAI, INDIA** **  
<u>Change History</u>**

<table style="width:100%;">
<colgroup>
<col style="width: 33%" />
<col style="width: 28%" />
<col style="width: 18%" />
<col style="width: 19%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Description</strong></td>
<td><strong>Author</strong></td>
<td><strong>Version</strong></td>
<td><strong>Date</strong></td>
</tr>
<tr class="even">
<td>Initial Version</td>
<td>BG</td>
<td>1</td>
<td>01/29/2016</td>
</tr>
<tr class="odd">
<td><p>Server runnables, Interrupt functions, Module Internal (Local)
Functions, GLOBAL Function/Macro Definitions - sub portions were
removed</p>
<p>Footer template updated to EA4 01.00.01</p></td>
<td>BG</td>
<td>2</td>
<td>02/15/2016</td>
</tr>
<tr class="even">
<td>Updated to design version 2.0.0</td>
<td>TATA</td>
<td>3</td>
<td>01-Dec-16</td>
</tr>
</tbody>
</table>

<u>Table of Contents</u>

1.Introduction 5

1.1 Purpose 5

1.2 Scope 5

2 HowDetn High-Level Description 6

2.1 Graphical representation of HowDetn 6

2.2 Data Flow Diagram 6

2.2.1 Component level DFD 6

2.2.2 Function level DFD 6

3 Constant Data Dictionary 7

3.1 Program (fixed) Constants 7

3.1.1 Embedded Constants 7

4 Software Component Implementation 8

4.1 Sub-Module Functions 8

4.1.1 Init: HowDetnInit1 8

4.1.1.1 Design Rationale 8

4.1.1.2 Module Outputs 8

4.1.2 Per: HowDetnPer1 8

4.1.2.1 Design Rationale 8

4.1.2.2 Store Module Inputs to Local copies 8

4.1.2.3 (Processing of function)……… 8

4.1.2.4 Store Local copy of outputs into Module Outputs 8

4.2 Server Runables 8

4.3 Interrupt Functions 8

4.4 Module Internal (Local) Functions 8

4.5 GLOBAL Function/Macro Definitions 8

5 Known Limitations with Design 9

6 UNIT TEST CONSIDERATION 10

Appendix A Abbreviations and Acronyms 11

Appendix B Glossary 12

Appendix C References 13

# 1. Introduction [introduction]

## Purpose

The purpose of this document is to document the module level design for
a HowDetn software module which is the part of the software related to
Nexteer’s Electrical Steering Systems product line.

## Scope

Scope of the document is to capture the software implementation details
of HowDetn Module.

# HowDetn High-Level Description

> Determination of a continuous valued estimate that represents the
> likelihood that a driver's hands are on the steering wheel (value =1)
> or off the steering wheel (value=0). A discrete value corresponding to
> the confidence of the estimate is also specified Design details of
> software module

## Graphical representation of HowDetn

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF044A_HowDetn_Impl/doc/mediax/media/image2.jpeg"
style="width:4.5in;height:4.55208in"
alt="C:\Users\vignesh.l\Desktop\SF044A_HowDetn_Impl_2.0.0\MDD_Image.JPG" />

## Data Flow Diagram

Refer to FDD

### Component level DFD

Refer to FDD

### Function level DFD

Refer to FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                   | Resolution | Units | Value |
|---------------------------------|------------|-------|-------|
| Refer SF044A_HowDetn_DataDict.m | NA         | NA    | NA    |

# Software Component Implementation

Refer FDD

## Sub-Module Functions

## Init: HowDetnInit1

## Design Rationale

*Refer FDD*

## Module Outputs

*Refer FDD*

## Per: HowDetnPer1

## Design Rationale

*Refer FDD*

## Store Module Inputs to Local copies

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Store Local copy of outputs into Module Outputs

*Refer FDD*

## Server Runables 

*None*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

*None*

## GLOBAL Function/Macro Definitions

*None*

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
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 2.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1                             |
| 5           | FDD : SF044A_HowDetn_Design                                                                                                                                           | See Synergy sub project version |

{% endraw %}