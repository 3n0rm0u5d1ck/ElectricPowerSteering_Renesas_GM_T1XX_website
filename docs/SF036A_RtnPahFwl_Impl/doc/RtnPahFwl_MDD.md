---
layout: default
title: RtnPahFwl_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**RtnPahFwl**

**February 3, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Akhil Krishna N D (Tata Elxsi),**

**Trivandrum, INDIA**

**<u>Change</u>** History

|                 |                   |              |            |
|-----------------|-------------------|--------------|------------|
| **Description** | **Author**        | **Version**  | **Date**   |
| Initial Version | Akhil Krishna N D | EA4 01.00.01 | 3-Feb-2015 |

**<u>Table of Contents</u>**

[1 Introduction 4](#introduction)

[1.1 Purpose 4](#purpose)

[2 RtnPahFwl & High-Level Description
5](#rtnpahfwl-high-level-description)

[3 Design details of software module
6](#design-details-of-software-module)

[3.1 Graphical representation of RtnPahFwl
6](#graphical-representation-of-rtnpahfwl)

[3.2 Data Flow Diagram 6](#data-flow-diagram)

[3.2.1 Component level DFD 6](#component-level-dfd)

[3.2.2 Function level DFD 6](#function-level-dfd)

[4 Constant Data Dictionary 7](#constant-data-dictionary)

[4.1 Program (fixed) Constants 7](#program-fixed-constants)

[4.1.1 Embedded Constants 7](#embedded-constants)

[5 Software Component Implementation
8](#software-component-implementation)

[5.1 Sub-Module Functions 8](#sub-module-functions)

[5.1.1 Init: RtnPahFwlInit1 8](#init-rtnpahfwlinit1)

[5.1.1.1 Design Rationale 8](#design-rationale)

[5.1.1.2 Module Outputs 8](#module-outputs)

[5.1.2 Per: RtnPahFwlPer1 8](#per-rtnpahfwlper1)

[5.1.2.1 Design Rationale 8](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
8](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)……… 8](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
8](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables 8](#server-runables)

[5.3 Interrupt Functions 8](#interrupt-functions)

[5.4 Module Internal (Local) Functions
8](#module-internal-local-functions)

[5.5 GLOBAL Function/Macro Definitions
8](#global-functionmacro-definitions)

[6 Known Limitations with Design 9](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION 10](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms 11](#abbreviations-and-acronyms)

[Appendix B Glossary 12](#glossary)

[Appendix C References 13](#references)

# Introduction

## Purpose

MDD for Return Path Firewall.

# RtnPahFwl & High-Level Description

Please refer FDD

# Design details of software module

## Graphical representation of RtnPahFwl

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/SF036A_RtnPahFwl_Impl/doc/mediax/media/image1.jpeg"
style="width:2.66667in;height:3.21875in" />

## Data Flow Diagram

Please refer FDD

### Component level DFD

Please refer FDD

### Function level DFD

Please refer FDD

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

|                                   |            |       |       |
|-----------------------------------|------------|-------|-------|
| Constant Name                     | Resolution | Units | Value |
| NODEBSTEP_CNT_U16                 | 1          | Cnt   | 65535 |
| Please refer .m file for the rest |            |       |       |

# Software Component Implementation

## Sub-Module Functions

## Init: RtnPahFwlInit1

## Design Rationale

None

## Module Outputs

None

## Per: RtnPahFwlPer1

## Design Rationale

None

## Store Module Inputs to Local copies

None

## (Processing of function)………

Please refer FDD

## Store Local copy of outputs into Module Outputs

Please refer FDD

## Server Runables 

None

## Interrupt Functions

None

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

| **Ref. \#** | **Title**                                                                                                                                                     | **Version**                     |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))            | v1.3.0 R4.0 Rev 2               |
| 2           | MDD Guideline                                                                                                                                                 | EA4 01.00.00                    |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software Naming Conventions 03x(In Work).doc)   | 1.0                             |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software Design and Coding Standards.doc) | 2.0                             |
| 5           | FDD: SF036A_RtnPahFwl_Design                                                                                                                                  | See Synergy sub project version |

{% endraw %}