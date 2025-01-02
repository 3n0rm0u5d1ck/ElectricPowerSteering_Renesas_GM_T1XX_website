---
layout: default
title: ExcpnHndlg Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**ExcpnHndlg**

**VERSION:** **4**

**DATE:** **04/05/16**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                               |                |             |          |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                                               | **Author**     | **Version** | **Date** |
| 1           | Initial version                                                               | Lucas Wendling | 1.0         | 01/19/16 |
| 2           | Updated for ChkForStrtUpTest() functions and Clock Monitor FE                 | Avinash James  | 2.0         | 02/10/16 |
| 3           | Updated for DTS RAM Double bit ECC error from FENMI to SYSERR                 | Avinash James  | 3.0         | 03/22/16 |
| 4           | Updates for New FENMI Handlers for mode error and removed SPI Dbt Bit handler | Avinash James  | 4.0         | 04/05/16 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 8](#configuration-requirements)

[4.1 Build Time Config 8](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
8](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
8](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#__RefHeading___Toc447790833)

[4.5 Manual Configuration Changes 8](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
9](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 9](#required-global-data-inputs)

[5.2 Required Global Data Outputs 9](#required-global-data-outputs)

[5.3 Specific Include Path present 9](#specific-include-path-present)

[6 Runnable Scheduling 10](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 11](#memory-map-requirements)

[7.1 Mapping 11](#mapping)

[7.2 Usage 11](#usage)

[7.3 NvM Blocks 11](#nvm-blocks)

[8 Compiler Settings 12](#compiler-settings)

[8.1 Preprocessor MACRO 12](#preprocessor-macro)

[8.2 Optimization Settings 12](#optimization-settings)

[9 Appendix 13](#appendix)

# Abbrevations And Acronyms

|                  |                 |
|------------------|-----------------|
| **Abbreviation** | **Description** |
|                  |                 |
|                  |                 |
|                  |                 |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |           |             |
|-------------|-----------|-------------|
| **Sr. No.** | **Title** | **Version** |
|             |           |             |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

**SetMcuDiagcIdnData** – Non-Rte Server Interface (called as needed)

**GetMcuDiagcIdnData** – Non-Rte Server Interface (called as needed)

**SysErrIrq/Patched_SysErrIrq** – Interrupt Handler Routine (triggered
by Interrupt)

**FpuErrIrq/Patched_FpuErrIrq** – Interrupt Handler Routine (triggered
by Interrupt)

**AlgnErrIrq** – Interrupt Handler Routine (triggered by Interrupt)

**ResdOperIrq** – Interrupt Handler Routine (triggered by Interrupt)

**ExcpnHndlgInit1** – Non-RTE initialization function (called during
startup before RTE is initialized)

**FeNmiPeg** – Callout function for interrupt response handling (to be
called by FENMI Interrupt handler)

**FeNmiDmaTrf** – Callout function for interrupt response handling (to
be called by FENMI Interrupt handler)

**FeNmiDmaRegAcsProtnErr** – Callout function for interrupt response
handling (to be called by FENMI Interrupt handler)

**FeNmiEcmMstChkrCmp** – Callout function for interrupt response
handling (to be called by FENMI Interrupt handler)

**FeNmiWdg** – Callout function for interrupt response handling (to be
called by FENMI Interrupt handler)

**ProcUkwnExcpnErr** – Callout function for OS error response handling
(to be called by OS error handler)

**ProcMpuExcpnErr** – Callout function for OS error response handling
(to be called by OS error handler)

**ProcPrvlgdInstrExcpnErr** – Callout function for OS error response
handling (to be called by OS error handler)

**ProcPrmntOsErr** – Callout function for OS error response handling (to
be called by OS error handler)

**ProcNonCritOsErr** – Callout function for OS error response handling
(to be called by OS error handler)

**ChkForStrtUpTest_Oper** – (called as needed from both RTE and non-RTE
context))

**FeNmiClkMonr0RtLowrLimFlt** – Callout function responding to Clock
Monitor 0 Runtime Lower Limit Failure(to be called by FENMI Interrupt
handler)

**FeNmiClkMonr0RtUpprLimFlt** – Callout function responding to Clock
Monitor 0 Runtime Upper Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr1RtLowrLimFlt** – Callout function responding to Clock
Monitor 1 Runtime Lower Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr1RtUpprLimFlt** – Callout function responding to Clock
Monitor 1 Runtime Upper Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr2RtLowrLimFlt** – Callout function responding to Clock
Monitor 2 Runtime Lower Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr2RtUpprLimFlt** – Callout function responding to Clock
Monitor 2 Runtime Upper Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr3RtLowrLimFlt** – Callout function responding to Clock
Monitor 3 Runtime Lower Limit Failure

(to be called by FENMI Interrupt handler)

**FeNmiClkMonr3RtUpprLimFlt** – Callout function responding to Clock
Monitor 3 Runtime Upper Limit Failure

(to be called by FENMI Interrupt handler)

FeNmiOperModErrSngChipInactv – Callout function responding to Single
Chip Mode inactive in Single chip mode (to be called by FENMI Interrupt
handler)

FeNmiOperModErrFlsProgmModStrtd – Callout function responding to Flash
programming Mode active in Single chip mode (to be called by FENMI
Interrupt handler)

FeNmiOperModErrTestModStrtd – Callout function responding to Test Mode
active in Single chip mode (to be called by FENMI Interrupt handler)

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
|             |           |     |

## Configuration Files to be provided by Integration Project

N/A

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
|               |           |         |

## DaVinci Interrupt Configuration Changes

|                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------------------|-------------------------------------------|
| **ISR Name**          | **Notes**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Patched_SysErrIrq** | The ExcpnHndlg module implements an interrupt that needs a patch for a hardware problem that exists on the P1M hardware (see Renesas Technical Update TN-RH8-S001A/E). Nexteer has created the appropriate workaround that subsequently calls the normal interrupt handler code. Therefore, when configuring the SysErrIrq interrupt in the O/S the interrupt handler name should be configured to the Nexteer code with the workaround (“Patched_SysErrIrq”) instead of directly referencing the normal interrupt handler code. |
| **Patched_FpuErrIrq** | The ExcpnHndlg module implements an interrupt that needs a patch for a hardware problem that exists on the P1M hardware (see Renesas Technical Update TN-RH8-S001A/E). Nexteer has created the appropriate workaround that subsequently calls the normal interrupt handler code. Therefore, when configuring the FpuErrIrq interrupt in the O/S the interrupt handler name should be configured to the Nexteer code with the workaround (“Patched_FpuErrIrq”) instead of directly referencing the normal interrupt handler code. |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
|              |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

## Required Global Data Outputs

## Specific Include Path present

Yes

# Runnable Scheduling 

API usage and scheduling of BSW components expected to be captured at a
project architectural level and is beyond the scope of this document.
Third party documentation can be referenced as needed.

|                 |                                                             |                    |
|-------------------|---------------------------------------|---------------|
| **Init**        | **Scheduling Requirements**                                 | **Trigger**        |
| ExcpnHndlgInit1 | Pre-RTE initializaton                                       | Once at init       |
| ExcpnHndlgInit2 | After diagnostic manager is initialized and NTCs can be set | RTE initialization |
|                 |                                                             |                    |

|                    |                             |             |
|--------------------|-----------------------------|-------------|
| **Runnable**       | **Scheduling Requirements** | **Trigger** |
| **ExcpnHndlgPer1** |                             | 2ms         |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
|                    |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

## NvM Blocks

# Compiler Settings

##  Preprocessor MACRO

## Optimization Settings

# Appendix

*\<This section is for appendix\>*

{% endraw %}