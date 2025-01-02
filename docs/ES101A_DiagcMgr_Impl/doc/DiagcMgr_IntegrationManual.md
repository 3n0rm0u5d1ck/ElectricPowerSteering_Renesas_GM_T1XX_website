---
layout: default
title: DiagcMgr_IntegrationManual
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Diagnostic Manager**

**VERSION:** **6.0**

**DATE:** **07-DEC-2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                       |                 |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                       | **Author**      | **Version** | **Date**    |
| 1           | Initial version                       | Spandana Balani | 1.0         | 23-Apr-2015 |
| 2           | Updated to FDD version 2              | Spandana Balani | 2.0         | 11-Mar-2016 |
| 3           | Updated to FDD version 3              | Spandana Balani | 3.0         | 22-APR-2016 |
| 4           | Updated to FDD version 4              | Spandana Balani | 4.0         | 22-Jun-2016 |
| 5           | Added new parameter in configurator   | Spandana Balani | 5.0         | 30-Nov-2016 |
| 6           | Remove Nvm block id for SnpshtDataAry | Spandana Balani | 6.0         | 07-Dec-2016 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config. 7](#build-time-config.)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
8](#davinci-interrupt-configuration-changes)

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

|                  |                                         |
|------------------|-----------------------------------------|
| **Abbreviation** | **Description**                         |
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                 |                                |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                       | **Version**                    |
| \<1\>       | \<MDD Guidelines\>              | Process 04.02.01               |
| \<2\>       | \<Software Naming Conventions\> | Process 04.02.01               |
| \<3\>       | \<Coding standards\>            | Process 04.02.01               |
| \<4\>       | FDD – ES101A Diagnostic Manager | See Synergy Subproject version |
|             | \<Add if more available\>       |                                |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

DiagcMgrPwrDwn() –Non RTE Server Runnable, called from BswM. It copies
the appropriate information for upto 20 NTCs from Application
NtcInfoArys and stores it to Nvm PIM. And, calls "SetRamBlockSts".

RestoreNtcFltAryDft() , RestoreSnpshtAryDft() – Non RTE Server
Runnables, called from Nvm Manager if the Nvm Data is corrupted.

# Configuration REQUIREMeNTS

Only proxies components that have active NTCs should be brought into
developer worksace. Stub needs to be integrated for connection to the
core's client ports for all the un-implemented applications. Proper .gpj
fles needs to be selected for inclusion in the project’s .gpj file.

The Integrator must configure one and only one
“/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn” for configured DTC in
the DEM

## Build Time Config.

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

DiagcMgr_Cfg.h

DiagcMgr_Cfg.c

Note: Include “DiagcMgr_Cfg.h” in the “Rte_UserTypes.h” header file

## Da Vinci Parameter Configuration Changes

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 44%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Parameter</strong></td>
<td><strong>Notes</strong></td>
<td><strong>SWC</strong></td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr</strong></td>
<td>Configuration of the DiagcMgr module</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR</strong></td>
<td>Container with NTC number properties</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/NTCOsApplicationRef</strong></td>
<td>NTC Os Application. This defines the application corresponding to a
particular NTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/NTCNR/Debounce</strong></td>
<td>Set to true if NTC is type debounce</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn</strong></td>
<td>Container with DTC ENABLE Criteria</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/DTC</strong></td>
<td>This defines the DEM DTC Class.</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/Bit_X<sup>1</sup></strong></td>
<td>Set to true if Enable Condition for Bit X<sup>1</sup> is applicable
to configured DTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DTCEnaCndn/DiagcMgrDTCIdx</strong></td>
<td>Value represents index value DiagcMgr uses internally for NTC
mapping to DTCs to the Event ID that the Dem identifies for a particular
DTC</td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral</strong></td>
<td>Container with General DiagcMgr configuration</td>
<td>DiagcMgr</td>
</tr>
<tr class="odd">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral/DIAGCMGR_DEMCHK</strong></td>
<td><p>Set to true to enable DET consistency check between DEM and
DiagcMgr DTC configuration.</p>
<p>This check assumes the Dem will generate the constant table named”
Dem_C_DtcTable” that will be sized to the configured DTCs + 1. If this
assumption is not true, turn this parameter OFF.</p></td>
<td>DiagcMgr</td>
</tr>
<tr class="even">
<td><strong>/Nexteer/EcucDefs_DiagcMgr/DiagcMgr/DiagcMgrGeneral/DEMTOTNROFDTC</strong></td>
<td>This needs to be configured to an expression that would result in
the total number DTCs that are configured in the system based on
generated Dem code</td>
<td>DiagcMgr</td>
</tr>
</tbody>
</table>

**^1^** Note: X = \_0 to 15

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **N/A**      |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                            |                                                                                                                                                                |             |
|-------------------|--------------------------------------|---------------|
| **Init**                   | **Scheduling Requirements**                                                                                                                                    | **Trigger** |
| **DiagcMgProxyApplXInit1** | Init function needs to run before any other init function that is trying to set an NTC and it therefore should be called early on in the initialization tasks. | Rte_Init    |

|                                |                             |                         |
|----------------------|----------------------------------|-----------------|
| **Runnable**                   | **Scheduling Requirements** | **Trigger**             |
| **DiagcMgrPer1**               | None                        | RTE 2ms Task            |
| **DiagcMgrPer2**               | None                        | RTE 100ms Task          |
| **ClrAllDiagc_Oper**           | Server Runnable             | Client Call             |
| **ClrSnpshtData_Oper**         | Server Runnable             | Client Call             |
| **DiagcMgrIninCore_Oper**      | Server Runnable             | Internal to DiagcMgr^2^ |
| **GetNtcActvCore_Oper**        | Server Runnable             | Internal to DiagcMgr^2^ |
| **GetNtcQlfrStsCore_Oper**     | Server Runnable             | Internal to DiagcMgr^2^ |
| **GetNtcStsCore_Oper**         | Server Runnable             | Internal to DiagcMgr^2^ |
| **ReadNtcFltAryCore_Oper**     | Server Runnable             | Client Call             |
| **ReadNtcInfoAndDebCntr_Oper** | Server Runnable             | Client Call             |
| **ReadSnpshtData_Oper**        | Server Runnable             | Client Call             |
| **SetNtcStsCore_Oper**         | Server Runnable             | Internal to DiagcMgr^2^ |
| **DiagcMgrPwrDwn**             | Non RTE Server Runnable     | Client Call             |
| **RestoreNtcFltAryDft**        | Non RTE Server Runnable     | Client Call             |
| **RestoreSnpshtAryDft**        | Non RTE Server Runnable     | Client Call             |
| **DiagcMgrProxyApplXInit1^1^** | On Init                     | RTE Init                |
| **DiagcMgrProxyApplXPer1^1^**  | None                        | RTE 10ms Task           |
| **GetDiagcDataApplX_Oper^1^**  | Server Runnable             | Internal to DiagcMgr^2^ |
| **GetNtcActvX_Oper^1,3^**      | Server Runnable             | Client Call             |
| **GetNtcDebCntrAppl0_Oper^1^** | Server Runnable             | Client Call             |
| **GetNtcInfoApplX_Oper^1^**    | Server Runnable             | Internal to DiagcMgr^2^ |
| **GetNtcQlfrStsX_Oper^1,3^**   | Server Runnable             | Client Call             |
| **GetNtcStsX_Oper^1,3^**       | Server Runnable             | Client Call             |
| **SetNtcStsX_Oper^1,3^**       | Server Runnable             | Client Call             |
| **UpdDtcEnaCdn^4^**            | Non RTE Server Runnable     | Client Call             |

Note: 1 – X in the Runnable name represent the application number. There
11 applications varying from 0 to 10 and each application has a
ProxyDiagcMgr component. One set of all these server runnables exist in
each proxy component.

2 – Runnables with trigger ‘Internal to DiagcMgr’ are local to DiagcMgr
main component and 11 proxy components, other components will not have
access to these functions. Whenever a component inside an application
calls one of the server runnables, the ProxyDiagcMgr of that application
will make a client call to the DiagcMgr main component.

3 – These Server Runnables must be defined with “can be invoked
concurrently” enabled in Developer.

4 – This function is assumed to be called by bswm providing periodic
updates of DTC enable condition.

DTC enable conditions should be defined by the fault code requirement.

# Memory Map REQUIREMENTS

## Mapping

|                                                   |              |           |
|------------------------------------|------------------|-------------------|
| **Memory Section**                                | **Contents** | **Notes** |
| **GlobalShared_START_SEC_VAR_NOINIT_UNSPECIFIED** |              |           |
|                                                   |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|                            |         |         |
|----------------------------|---------|---------|
| **Feature**                | **RAM** | **ROM** |
| **\<Memmap usuage info\>** |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

\*See DataDict.m

This component assumes that the integrator will keep the default NvM
block name and the Block ID name will be
"NvMConf_NvMBlockDescriptor_Rte_NvmBlock_DiagcMgr_DiagcMgrNtcFltAry”.

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*\<This section is for appendix\>*

{% endraw %}