---
layout: default
title: TmplMonr_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**\<Component Name\>**

**Aug 15, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**SEPGroup,**

**Nexteer Automotive,**

**<u>Saginaw, MI, USAChange</u>** History

<table>
<colgroup>
<col style="width: 52%" />
<col style="width: 20%" />
<col style="width: 11%" />
<col style="width: 14%" />
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
<td>Rijvi Ahmed</td>
<td>1.0</td>
<td>08-Apr-2015</td>
</tr>
<tr class="odd">
<td><p>Updated per implementation of design change.</p>
<p>Updated to the latest template.</p></td>
<td>Rijvi Ahmed</td>
<td>2.0</td>
<td>02-Aug-2015</td>
</tr>
<tr class="even">
<td>Update for anomaly EA4# 1338 fix</td>
<td>Rijvi Ahmed</td>
<td>3.0</td>
<td>17-Aug-2015</td>
</tr>
<tr class="odd">
<td>Updated per design rev. 2.3.0</td>
<td>Rijvi Ahmed</td>
<td>4.0</td>
<td>28-Sep-2015</td>
</tr>
<tr class="even">
<td>Updated per design rev. 2.6.0</td>
<td>Rijvi Ahmed</td>
<td>5.0</td>
<td>15-Aug-2016</td>
</tr>
</tbody>
</table>

<u>Table of Contents</u>

[**1** **Introduction 5**](#introduction)

[1.1 Purpose 5](#purpose)

[2 TmplMonr & High-Level Description
6](#component-name-high-level-description)

[3 Design details of software module
7](#design-details-of-software-module)

[3.1 Graphical representation of TmplMonr
7](#graphical-representation-of-tmplmonr)

[3.2 Data Flow Diagram 7](#data-flow-diagram)

[3.2.1 Component level DFD 7](#component-level-dfd)

[3.2.2 Function level DFD 7](#function-level-dfd)

[4 Constant Data Dictionary 8](#constant-data-dictionary)

[4.1 Program (fixed) Constants 8](#program-fixed-constants)

[4.1.1 Embedded Constants 8](#embedded-constants)

[5 Software Component Implementation
9](#software-component-implementation)

[5.1 Sub-Module Functions 9](#sub-module-functions)

[5.1.1 Init: TmplMonrInit1 9](#init-component-name)

[5.1.1.1 Design Rationale 9](#design-rationale)

[5.1.1.2 Module Outputs 9](#module-outputs)

[5.1.2 Per: TmplMonrPer1 9](#per-tmplmonrper1)

[5.1.2.1 Design Rationale 9](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 9](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
9](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: TmplMonrPer2 9](#per-tmplmonrper2)

[5.1.3.1 Design Rationale 9](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
9](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)……… 9](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables 10](#server-runables)

[5.3 Interrupt Functions 10](#interrupt-functions)

[5.4 Module Internal (Local) Functions
10](#module-internal-local-functions)

[5.4.1 Local Function \#1 10](#local-function-1)

[5.4.1.1 Design Rationale 10](#design-rationale-3)

[5.4.1.2 Processing 10](#processing)

[5.4.2 Local Function \#2 10](#local-function-2)

[5.4.2.1 Design Rationale 10](#design-rationale-4)

[5.4.2.2 Processing 10](#processing-1)

[5.4.3 Local Function \#3 10](#local-function-3)

[5.4.3.1 Design Rationale 11](#design-rationale-5)

[5.4.3.2 Processing 11](#processing-2)

[5.4.4 Local Function \#4 11](#local-function-4)

[5.4.4.1 Design Rationale 11](#design-rationale-6)

[5.4.4.2 Processing 11](#processing-3)

[5.4.5 Local Function \#5 11](#local-function-5)

[5.4.5.1 Design Rationale 11](#design-rationale-7)

[5.4.5.2 Processing 11](#processing-4)

[5.4.6 Local Function \#6 11](#local-function-6)

[5.4.6.1 Design Rationale 11](#design-rationale-8)

[5.4.6.2 Processing 12](#processing-5)

[5.4.7 Local Function \#7 12](#__RefHeading___Toc459039679)

[5.4.7.1 Design Rationale 12](#__RefHeading___Toc459039680)

[5.4.7.2 Processing 12](#__RefHeading___Toc459039681)

[5.5 GLOBAL Function/Macro Definitions
12](#global-functionmacro-definitions)

[6 Known Limitations with Design 13](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 14](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 15](#abbreviations-and-acronyms)

[Appendix B Glossary 16](#glossary)

[Appendix C References 18](#references)

# Introduction

## Purpose

Module design document for Temporal Monitor Function.

# \<Component Name\>& High-Level Description

*None*

# Design details of software module

## Graphical representation of TmplMonr

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES005A_TmplMonr_Impl/doc/mediax/media/image1.png"
style="width:3.77986in;height:2.27847in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                           |            |       |       |
|-------------------------------------------|------------|-------|-------|
| Constant Name                             | Resolution | Units | Value |
| Refer to the DataDictionary of the design |            |       |       |

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

## Init: \<Component Name\>

## Design Rationale

*None*

## Module Outputs

*Refer to FDD*

###  [section]

## Per: TmplMonrPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: TmplMonrPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runables 

None

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |             |      |     |     |
|----------------------|-------------|------|-----|-----|
| **Function Name**    | TMFInitTest | Type | Min | Max |
| **Arguments Passed** | None        |      |     |     |
| **Return Value**     | N/A         |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block of the Simulink model of the design.

## Local Function \#2

|                      |                                 |      |     |     |
|----------------------|---------------------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase10To11Case15To17 | Type | Min | Max |
| **Arguments Passed** | None                            |      |     |     |
| **Return Value**     | N/A                             |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 10, case 11, case 15, case 16
and case 17 of the Simulink model of the design.

## Local Function \#3

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase13 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 13 of the Simulink model of the
design.

## Local Function \#4

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase18 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 18 of the Simulink model of the
design.

## Local Function \#5

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase19 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 19 of the Simulink model of the
design.

## Local Function \#6

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase53 | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
| **Return Value**     | N/A               |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 53 of the Simulink model of the
design.

## Local Function \#7

|                      |                  |      |     |     |
|----------------------|------------------|------|-----|-----|
| **Function Name**    | TMFInitTestCase0 | Type | Min | Max |
| **Arguments Passed** | None             |      |     |     |
| **Return Value**     | N/A              |      |     |     |

## Design Rationale

None

## Processing

(Place flowchart/design for local function)

Refer to the “TMF Init Test” block case 0 of the Simulink model of the
design.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

None

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

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
| 5           | FDD – ES005A TmplMonr                                                                                                                                         | See Synergy subproject version |

{% endraw %}