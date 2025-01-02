---
layout: default
title: ExcpnHndlg Module Design Document
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**ExcpnHndlg**

**April 5, 2016**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                 |               |             |             |
|-----------------|---------------|-------------|-------------|
| **Description** | **Author**    | **Version** | **Date**    |
| Initial Version | Avinash James | 1.0         | 05-Apr-2016 |

**  
**

**<u>Table of Contents</u>**

1 Introduction [7](#introduction)

[1.1 Purpose [7](#purpose)](#purpose)

[1.2 Scope [7](#scope)](#scope)

[2 ExcpnHndlg & High-Level Description
[8](#excpnhndlg-high-level-description)](#excpnhndlg-high-level-description)

[3 Design details of software module
[9](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of ExcpnHndlg
[9](#graphical-representation-of-excpnhndlg)](#graphical-representation-of-excpnhndlg)

[3.2 Data Flow Diagram [9](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[9](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [9](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[10](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[13](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[13](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: ExcpnHndlgInit1
[13](#init-excpnhndlginit1)](#init-excpnhndlginit1)

[5.1.1.1 Design Rationale [13](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [13](#module-outputs)](#module-outputs)

[5.1.2 Init: ExcpnHndlgInit2
[13](#init-excpnhndlginit2)](#init-excpnhndlginit2)

[5.1.2.1 Design Rationale
[13](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Module Outputs [13](#module-outputs-1)](#module-outputs-1)

[5.1.3 Per: ExcpnHndlgPer1
[13](#per-excpnhndlgper1)](#per-excpnhndlgper1)

[5.1.3.1 Design Rationale
[13](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[13](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.3.3 (Processing of function)………
[13](#processing-of-function)](#processing-of-function)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[13](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.2 Server Runables [13](#server-runables)](#server-runables)

[5.2.1 ChkForStrtUpTest [13](#chkforstrtuptest)](#chkforstrtuptest)

[5.2.1.1 Design Rationale
[13](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 (Processing of function)………
[13](#processing-of-function-1)](#processing-of-function-1)

[5.2.2 FeNmiClkMonr0RtLowrLimFlt
[14](#fenmiclkmonr0rtlowrlimflt)](#fenmiclkmonr0rtlowrlimflt)

[5.2.2.1 Design Rationale
[14](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 (Processing of function)………
[14](#processing-of-function-2)](#processing-of-function-2)

[5.2.3 FeNmiClkMonr0RtUpprLimFlt
[14](#fenmiclkmonr0rtupprlimflt)](#fenmiclkmonr0rtupprlimflt)

[5.2.3.1 Design Rationale
[14](#design-rationale-5)](#design-rationale-5)

[5.2.3.2 (Processing of function)………
[14](#processing-of-function-3)](#processing-of-function-3)

[5.2.4 FeNmiClkMonr1RtLowrLimFlt
[14](#fenmiclkmonr1rtlowrlimflt)](#fenmiclkmonr1rtlowrlimflt)

[5.2.4.1 Design Rationale
[14](#design-rationale-6)](#design-rationale-6)

[5.2.4.2 (Processing of function)………
[14](#processing-of-function-4)](#processing-of-function-4)

[5.2.5 FeNmiClkMonr1RtUpprLimFlt
[14](#fenmiclkmonr1rtupprlimflt)](#fenmiclkmonr1rtupprlimflt)

[5.2.5.1 Design Rationale
[14](#design-rationale-7)](#design-rationale-7)

[5.2.5.2 (Processing of function)………
[14](#processing-of-function-5)](#processing-of-function-5)

[5.2.6 FeNmiClkMonr2RtLowrLimFlt
[14](#fenmiclkmonr2rtlowrlimflt)](#fenmiclkmonr2rtlowrlimflt)

[5.2.6.1 Design Rationale
[14](#design-rationale-8)](#design-rationale-8)

[5.2.6.2 (Processing of function)………
[14](#processing-of-function-6)](#processing-of-function-6)

[5.2.7 FeNmiClkMonr2RtUpprLimFlt
[14](#fenmiclkmonr2rtupprlimflt)](#fenmiclkmonr2rtupprlimflt)

[5.2.7.1 Design Rationale
[14](#design-rationale-9)](#design-rationale-9)

[5.2.7.2 (Processing of function)………
[15](#processing-of-function-7)](#processing-of-function-7)

[5.2.8 FeNmiClkMonr3RtLowrLimFlt
[15](#fenmiclkmonr3rtlowrlimflt)](#fenmiclkmonr3rtlowrlimflt)

[5.2.8.1 Design Rationale
[15](#design-rationale-10)](#design-rationale-10)

[5.2.8.2 (Processing of function)………
[15](#processing-of-function-8)](#processing-of-function-8)

[5.2.9 FeNmiClkMonr3RtUpprLimFlt
[15](#fenmiclkmonr3rtupprlimflt)](#fenmiclkmonr3rtupprlimflt)

[5.2.9.1 Design Rationale
[15](#design-rationale-11)](#design-rationale-11)

[5.2.9.2 (Processing of function)………
[15](#processing-of-function-9)](#processing-of-function-9)

[5.2.10 FeNmiDmaTrf [15](#fenmidmatrf)](#fenmidmatrf)

[5.2.10.1 Design Rationale
[15](#design-rationale-12)](#design-rationale-12)

[5.2.10.2 (Processing of function)………
[15](#processing-of-function-10)](#processing-of-function-10)

[5.2.11 FeNmiDmaRegAcsProtnErr
[15](#fenmidmaregacsprotnerr)](#fenmidmaregacsprotnerr)

[5.2.11.1 Design Rationale
[15](#design-rationale-13)](#design-rationale-13)

[5.2.11.2 (Processing of function)………
[15](#processing-of-function-11)](#processing-of-function-11)

[5.2.12 FeNmiEcmMstChkrCmp
[15](#fenmiecmmstchkrcmp)](#fenmiecmmstchkrcmp)

[5.2.12.1 Design Rationale
[15](#design-rationale-14)](#design-rationale-14)

[5.2.12.2 (Processing of function)………
[15](#processing-of-function-12)](#processing-of-function-12)

[5.2.13 FeNmiOperModErrFlsProgmModStrtd
[16](#fenmiopermoderrflsprogmmodstrtd)](#fenmiopermoderrflsprogmmodstrtd)

[5.2.13.1 Design Rationale
[16](#design-rationale-15)](#design-rationale-15)

[5.2.13.2 (Processing of function)………
[16](#processing-of-function-13)](#processing-of-function-13)

[5.2.14 FeNmiOperModErrSngChipInactv
[16](#fenmiopermoderrsngchipinactv)](#fenmiopermoderrsngchipinactv)

[5.2.14.1 Design Rationale
[16](#design-rationale-16)](#design-rationale-16)

[5.2.14.2 (Processing of function)………
[16](#processing-of-function-14)](#processing-of-function-14)

[5.2.15 FeNmiOperModErrTestModStrtd
[16](#fenmiopermoderrtestmodstrtd)](#fenmiopermoderrtestmodstrtd)

[5.2.15.1 Design Rationale
[16](#design-rationale-17)](#design-rationale-17)

[5.2.15.2 (Processing of function)………
[16](#processing-of-function-15)](#processing-of-function-15)

[5.2.16 FeNmiPeg [16](#fenmipeg)](#fenmipeg)

[5.2.16.1 Design Rationale
[16](#design-rationale-18)](#design-rationale-18)

[5.2.16.2 (Processing of function)………
[16](#processing-of-function-16)](#processing-of-function-16)

[5.2.17 FeNmiWdg [16](#fenmiwdg)](#fenmiwdg)

[5.2.17.1 Design Rationale
[16](#design-rationale-19)](#design-rationale-19)

[5.2.17.2 (Processing of function)………
[16](#processing-of-function-17)](#processing-of-function-17)

[5.2.18 GetMcuDiagcIdnData
[17](#getmcudiagcidndata)](#getmcudiagcidndata)

[5.2.18.1 Design Rationale
[17](#design-rationale-20)](#design-rationale-20)

[5.2.18.2 (Processing of function)………
[17](#processing-of-function-18)](#processing-of-function-18)

[5.2.19 ProcMpuExcpnErr [17](#procmpuexcpnerr)](#procmpuexcpnerr)

[5.2.19.1 Design Rationale
[17](#design-rationale-21)](#design-rationale-21)

[5.2.19.2 (Processing of function)………
[17](#processing-of-function-19)](#processing-of-function-19)

[5.2.20 ProcNonCritOsErr [17](#procnoncritoserr)](#procnoncritoserr)

[5.2.20.1 Design Rationale
[17](#design-rationale-22)](#design-rationale-22)

[5.2.20.2 (Processing of function)………
[17](#processing-of-function-20)](#processing-of-function-20)

[5.2.21 ProcPrmntOsErr [17](#procprmntoserr)](#procprmntoserr)

[5.2.21.1 Design Rationale
[17](#design-rationale-23)](#design-rationale-23)

[5.2.21.2 (Processing of function)………
[17](#processing-of-function-21)](#processing-of-function-21)

[5.2.22 ProcPrvlgdInstrExcpnErr
[17](#procprvlgdinstrexcpnerr)](#procprvlgdinstrexcpnerr)

[5.2.22.1 Design Rationale
[17](#design-rationale-24)](#design-rationale-24)

[5.2.22.2 (Processing of function)………
[17](#processing-of-function-22)](#processing-of-function-22)

[5.2.23 ProcUkwnExcpnErr [18](#procukwnexcpnerr)](#procukwnexcpnerr)

[5.2.23.1 Design Rationale
[18](#design-rationale-25)](#design-rationale-25)

[5.2.23.2 (Processing of function)………
[18](#processing-of-function-23)](#processing-of-function-23)

[5.2.24 SetMcuDiagcIdnData
[18](#setmcudiagcidndata)](#setmcudiagcidndata)

[5.2.24.1 Design Rationale
[18](#design-rationale-26)](#design-rationale-26)

[5.2.24.2 (Processing of function)………
[18](#processing-of-function-24)](#processing-of-function-24)

[5.3 Interrupt Functions
[18](#interrupt-functions)](#interrupt-functions)

[5.3.1 AlgnErrIrq [18](#algnerrirq)](#algnerrirq)

[5.3.1.1 Design Rationale
[18](#design-rationale-27)](#design-rationale-27)

[5.3.1.2 (Processing of the ISR function)…..
[18](#processing-of-the-isr-function..)](#processing-of-the-isr-function..)

[5.3.2 FpuErrIrq [18](#fpuerrirq)](#fpuerrirq)

[5.3.2.1 Design Rationale
[18](#design-rationale-28)](#design-rationale-28)

[5.3.2.2 (Processing of the ISR function)…..
[18](#processing-of-the-isr-function..-1)](#processing-of-the-isr-function..-1)

[5.3.3 SysErrIrq [18](#syserrirq)](#syserrirq)

[5.3.3.1 Design Rationale
[18](#design-rationale-29)](#design-rationale-29)

[5.3.3.2 (Processing of the ISR function)…..
[18](#processing-of-the-isr-function..-2)](#processing-of-the-isr-function..-2)

[5.3.4 ResdOperIrq [19](#resdoperirq)](#resdoperirq)

[5.3.4.1 Design Rationale
[19](#design-rationale-30)](#design-rationale-30)

[5.3.4.2 (Processing of the ISR function)…..
[19](#processing-of-the-isr-function..-3)](#processing-of-the-isr-function..-3)

[5.4 Module Internal (Local) Functions
[19](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 ProcStrtUpOrSwRst [19](#procstrtuporswrst)](#procstrtuporswrst)

[5.4.1.1 Design Rationale
[19](#design-rationale-31)](#design-rationale-31)

[5.4.1.2 Processing [19](#processing)](#processing)

[5.4.2 ProcEcmRst [19](#procecmrst)](#procecmrst)

[5.4.2.1 Design Rationale
[19](#design-rationale-32)](#design-rationale-32)

[5.4.2.2 Processing [19](#processing-1)](#processing-1)

[5.4.3 ProcPinRst [19](#procpinrst)](#procpinrst)

[5.4.3.1 Design Rationale
[20](#design-rationale-33)](#design-rationale-33)

[5.4.3.2 Processing [20](#processing-2)](#processing-2)

[5.5 GLOBAL Function/Macro Definitions
[20](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[5.5.1 GLOBAL Function \#1 [20](#global-function-1)](#global-function-1)

[5.5.1.1 Design Rationale
[20](#design-rationale-34)](#design-rationale-34)

[5.5.1.2 processing [20](#processing-3)](#processing-3)

[6 Known Limitations with Design
[21](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[22](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[23](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [24](#glossary)](#glossary)

[Appendix C References [25](#references)](#references)

# Introduction

## Purpose

This document details the design in the FDD and also lists out any
deviations which were made from the design for the implementation due to
any constraints in development. ExcpnHndlg MDD describes the exception
handling / reset cause determination for microcontroller diagnostics

## Scope

The following definitions are used throughout this document:

-   **<u>Shall</u>**: indicates a mandatory requirement without
    exception in compliance.

-   **<u>Should</u>**: indicates a mandatory requirement; exceptions
    allowed only with documented justification.

-   **<u>May</u>**: indicates an optional action.

# ExcpnHndlg & High-Level Description

Refer FDD

# Design details of software module

## Graphical representation of ExcpnHndlg

## Data Flow Diagram

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Impl/doc/mediax/media/image1.png"
style="width:2.33333in;height:1.63194in" />

### Component level DFD

**N/A**

### Function level DFD

**N/A**

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name                       | Resolution | Units  | Value                   |
|---------------------------|-------------|----------|-----------------------|
| FPCFGININVAL_CNT_T_U32              | 1          | Counts | 0x0000001CU             |
| FPCFGREGID_CNT_S32                  | 1          | Counts | 10                      |
| FPCFGSELNID_CNT_S32                 | 1          | Counts | 0                       |
| FPUINVLDOPERSTSBIT_CNT_U32          | 1          | Counts | ((uint32)(0x00004000U)) |
| FPUDIVBYZEROSTSBIT_CNT_U32          | 1          | Counts | ((uint32)(0x00002000U)) |
| FPUOVFSTSBIT_CNT_U32                | 1          | Counts | ((uint32)(0x00001000U)) |
| MEMERRINFOREADWRBIT_CNT_U32         | 1          | Counts | ((uint32)(0x00000001U)) |
| CF1STERSTRADRPARMASK_CNT_U32        | 1          | Counts | ((uint32)(0x00000004U)) |
| CF1STERSTRDBLBITMASK_CNT_U32        | 1          | Counts | ((uint32)(0x00000002U)) |
| CF1STERSTRSNGBITMASK_CNT_U32        | 1          | Counts | ((uint32)(0x00000001U)) |
| PRPHLBUSDATAPARMASK_CNT_U32         | 1          | Counts | ((uint32)(0x10000000U)) |
| DTSDBLBITMASK_CNT_U32               | 1          | Counts | ((uint32)(0x80000000U)) |
| CODFLSSNGBITHARDFLT_CNT_U08         | 1          | Counts | 1U                      |
| CODFLSECCDBLBIT_CNT_U08             | 1          | Counts | 2U                      |
| CODFLSADRPAR_CNT_U08                | 1          | Counts | 4U                      |
| MEMBISTSTRTUPTESTFAILR_CNT_U08      | 1          | Counts | 1U                      |
| LCLRAMECCSNGBITHARDFLT_CNT_U08      | 1          | Counts | 1U                      |
| LCLRAMECCDBLBIT_CNT_U08             | 1          | Counts | 2U                      |
| INVLDRAMAREA_CNT_U08                | 1          | Counts | 4U                      |
| DTSDBLBIT_CNT_U08                   | 1          | Counts | 2U                      |
| SPI0PRPHLRAMDBLBIT_CNT_U08          | 1          | Counts | 2U                      |
| SPI1PRPHLRAMDBLBIT_CNT_U08          | 1          | Counts | 2U                      |
| SPI2PRPHLRAMDBLBIT_CNT_U08          | 1          | Counts | 2U                      |
| SPI3PRPHLRAMDBLBIT_CNT_U08          | 1          | Counts | 2U                      |
| BISTCODECCFAILR_CNT_U08             | 1          | Counts | 1U                      |
| LOGLBISTSTRTUPTESTFAILR_CNT_U08     | 1          | Counts | 4U                      |
| BISTNOTCMPL_CNT_U08                 | 1          | Counts | 16U                     |
| CPULOCKSTEPSTRTUPTESTFAILR_CNT_U08  | 1          | Counts | 32U                     |
| LOCKSTEPCOMP_CNT_U08                | 1          | Counts | 1U                      |
| SYSVCIE_CNT_U08                     | 1          | Counts | 2U                      |
| RESDOPER_CNT_U08                    | 1          | Counts | 4U                      |
| ALGNREAD_CNT_U08                    | 1          | Counts | 8U                      |
| ALGNWR_CNT_U08                      | 1          | Counts | 16U                     |
| INSTRFETCH_CNT_U08                  | 1          | Counts | 32U                     |
| CLKMONR0RTLOWRLIMFLT_CNT_U08        | 1          | Counts | 4U                      |
| CLKMONR0RTUPPRLIMFLT_CNT_U08        | 1          | Counts | 8U                      |
| CLKMONR2RTLOWRLIMFLT_CNT_U08        | 1          | Counts | 64U                     |
| CLKMONR2RTUPPRLIMFLT_CNT_U08        | 1          | Counts | 128U                    |
| OPERMODERRFLSPROGMMODSTRTD_CNT_U08  | 1          | Counts | 1U                      |
| OPERMODERRTESTMODSTRTD_CNT_U08      | 1          | Counts | 2U                      |
| OPERMODERRSNGCHIPINACTV_CNT_U08     | 1          | Counts | 4U                      |
| CLKMONR1RTLOWRLIMFLT_CNT_U08        | 1          | Counts | 4U                      |
| CLKMONR1RTUPPRLIMFLT_CNT_U08        | 1          | Counts | 8U                      |
| CLKMONR3RTLOWRLIMFLT_CNT_U08        | 1          | Counts | 64U                     |
| CLKMONR3RTUPPRLIMFLT_CNT_U08        | 1          | Counts | 128U                    |
| DATAPROTNERR_CNT_U08                | 1          | Counts | 1U                      |
| INSTRPROTNERR_CNT_U08               | 1          | Counts | 2U                      |
| ECMSTSFLT_CNT_U08                   | 1          | Counts | 1U                      |
| ECMMSTSTRTUPTESTFAILR_CNT_U08       | 1          | Counts | 4U                      |
| ECMCHKRSTRTUPTESTFAILR_CNT_U08      | 1          | Counts | 8U                      |
| ECMRTMSTCHKRCOMPFLT_CNT_U08         | 1          | Counts | 128U                    |
| FPUINVLDOPEREXCPN_CNT_U08           | 1          | Counts | 2U                      |
| FPUDIVBYZEROEXCPN_CNT_U08           | 1          | Counts | 4U                      |
| FPUOVFEXCPN_CNT_U08                 | 1          | Counts | 8U                      |
| FPUUKWNEXCPN_CNT_U08                | 1          | Counts | 16U                     |
| UKWNRST_CNT_U08                     | 1          | Counts | 1U                      |
| UKWNECMRST_CNT_U08                  | 1          | Counts | 2U                      |
| UKWNSWRST_CNT_U08                   | 1          | Counts | 16U                     |
| BACKUPRAMTSTFAILR_CNT_U08           | 1          | Counts | 32U                     |
| FLSBTLDRPREOSSRTUPEXCPN_CNT_U08     | 1          | Counts | 64U                     |
| STRTUPRSTINFOFAILD_CNT_U08          | 1          | Counts | 128U                    |
| PROGFLOW_CNT_U08                    | 1          | Counts | 1U                      |
| DEADLINEMONR_CNT_U08                | 1          | Counts | 2U                      |
| ALVMONR_CNT_U08                     | 1          | Counts | 4U                      |
| WDGTOUT_CNT_U08                     | 1          | Counts | 1U                      |
| PEGRTFLT_CNT_U08                    | 1          | Counts | 2U                      |
| IPGRTFLT_CNT_U08                    | 1          | Counts | 8U                      |
| PBGSTRTUPTSTAILR_CNT_U08            | 1          | Counts | 16U                     |
| PBGRTFLT_CNT_U08                    | 1          | Counts | 32U                     |
| DBGRST_CNT_U08                      | 1          | Counts | 1U                      |
| OSCRITFLT_CNT_U08                   | 1          | Counts | 1U                      |
| UKWNEXCPN_CNT_U08                   | 1          | Counts | 2U                      |
| OSNONCRITFLT_CNT_U08                | 1          | Counts | 1U                      |
| DMATRFERR_CNT_U08                   | 1          | Counts | 1U                      |
| DMAREGACSPROTCNERR_CNT_U08          | 1          | Counts | 2U                      |
| PRPHLBUSDATAPARSTRTUPFLT_CNT_U08    | 1          | Counts | 64U                     |
| PRPHLBUSDATAPARPRTFLT_CNT_U08       | 1          | Counts | 128U                    |
| CVMOVERVLTGSTRTUPTESTFAILR_CNT_U08  | 1          | Counts | 1U                      |
| CVMUNDERVLTGSTRTUPTESTFAILR_CNT_U08 | 1          | Counts | 2U                      |
| INTCVMOVERVLTGMONR_CNT_U08          | 1          | Counts | 1U                      |
| INTCVMUNDERVLTGMONR_CNT_U08         | 1          | Counts | 2U                      |
| INTMONRLOVCCFLT_CNT_U08             | 1          | Counts | 16U                     |
| EXTVLTGMONRFLT_CNT_U08              | 1          | Counts | 128U                    |
| UPPR16BITMASK_CNT_U32               | 1          | Counts | ((uint32)(0xFFFF0000U)) |
| LOWR16BITMASK_CNT_U32               | 1          | Counts | ((uint32)(0x0000FFFFU)) |

# Software Component Implementation

## Sub-Module Functions

## Init: ExcpnHndlgInit1

## Design Rationale

*Non-RTE function because it needs to be called before the OS is
started - so that floating point exceptions can be enabled before
anything uses floating point*

## Module Outputs

*None*

## Init: ExcpnHndlgInit2

## Design Rationale

*RTE function to initialize all the NTCs to pass*

## Module Outputs

*None*

## Per: ExcpnHndlgPer1

## Design Rationale

*RTE Periodic function called every 2 ms to check for OS errors*

## Store Module Inputs to Local copies

*Refer MDD*

##  (Processing of function)………

*Triggered on Timing Event every 2ms*

## Store Local copy of outputs into Module Outputs

*None*

## Server Runables 

## ChkForStrtUpTest

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr0RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr0RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr1RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr1RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr2RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr2RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr3RtLowrLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiClkMonr3RtUpprLimFlt

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiDmaTrf

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiDmaRegAcsProtnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiEcmMstChkrCmp

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrFlsProgmModStrtd

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrSngChipInactv

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiOperModErrTestModStrtd

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiPeg

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## FeNmiWdg

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## GetMcuDiagcIdnData

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcMpuExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcNonCritOsErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcPrmntOsErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcPrvlgdInstrExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## ProcUkwnExcpnErr

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## SetMcuDiagcIdnData

## Design Rationale

*Refer FDD*

##  (Processing of function)………

*Refer FDD*

## Interrupt Functions

## AlgnErrIrq 

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## FpuErrIrq 

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## SysErrIrq

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## ResdOperIrq

## Design Rationale

*Refer FDD*

## (Processing of the ISR function)…..

*Refer FDD*

## Module Internal (Local) Functions

## ProcStrtUpOrSwRst 

|                      |                   |      |     |     |
|----------------------|-------------------|------|-----|-----|
| **Function Name**    | ProcStrtUpOrSwRst | Type | Min | Max |
| **Arguments Passed** | None              |      |     |     |
|                      |                   |      |     |     |
| **Return Value**     | NA                |      |     |     |

## Design Rationale

*Refer FDD*

## Processing

## ProcEcmRst

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | ProcEcmRst | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
|                      |            |      |     |     |
| **Return Value**     | NA         |      |     |     |

## Design Rationale

*Refer FDD*

## Processing

## ProcPinRst 

|                      |            |      |     |     |
|----------------------|------------|------|-----|-----|
| **Function Name**    | ProcPinRst | Type | Min | Max |
| **Arguments Passed** | None       |      |     |     |
|                      |            |      |     |     |
| **Return Value**     | NA         |      |     |     |

## Design Rationale

*Refer FDD*

## Processing

## GLOBAL Function/Macro Definitions

\<If these are numerous and defined in a separate source file then
reference the source file only.\>

## GLOBAL Function \#1

|                      |                                                    |                               |                               |                               |
|--------------|------------------------------|----------|----------|----------|
| **Function Name**    | (Exact name used)                                  | Type                          | Min                           | Max                           |
| **Arguments Passed** | (if none, write None)                              | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> | \<Refer MDD guidelines\[1\]\> |
|                      | (Insert more rows for additional passed arguments) |                               |                               |                               |
| **Return Value**     | (if no value returned, write N/A)                  |                               |                               |                               |

## Design Rationale

## processing

(Place flowchart/design for local function)

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

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**       |
|-------|-------------------------------------------------|-----------------|
| 1           | AUTOSAR Specification of Memory Mapping (Link:[AUTOSAR_SWS_MemoryMapping.pdf](http://www.autosar.org/download/R4.0/AUTOSAR_SWS_MemoryMapping.pdf))                    | v1.3.0 R4.0 Rev 2 |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.01      |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.0               |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.1               |

{% endraw %}