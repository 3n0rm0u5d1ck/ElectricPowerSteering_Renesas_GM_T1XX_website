---
layout: default
title: ES006A_NvM_FDD
nav_order: 12
parent: Component Design
---
{% raw %}
**Non Volatile RAM Manager And**

**Non Volatile RAM Manager Proxy**

**FDD \#ES-006A**

**Contents**

[1. High Level Description
[4](#high-level-description)](#high-level-description)

[2. Derived Requirements
[4](#derived-requirements)](#derived-requirements)

[3. Sub-Function Data Flow
[4](#sub-function-data-flow)](#sub-function-data-flow)

[4. Design Rationale [5](#design-rationale)](#design-rationale)

[5. Components [6](#components)](#components)

[5.1. NvM: Non Volatile Memory (AUTOSAR BSW)
[6](#nvm-non-volatile-memory-autosar-bsw)](#nvm-non-volatile-memory-autosar-bsw)

[5.1.1. BSW Configuration [6](#bsw-configuration)](#bsw-configuration)

[5.1.1.1. NvMCommon [6](#nvmcommon)](#nvmcommon)

[5.1.2. Periodic Functions
[7](#periodic-functions)](#periodic-functions)

[5.1.2.1. NvM_MainFunction [7](#nvm_mainfunction)](#nvm_mainfunction)

[5.1.2.1.1. Function Definition
[7](#function-definition)](#function-definition)

[5.1.3. Service Sub-Functions
[8](#service-sub-functions)](#service-sub-functions)

[5.1.3.1. API Configuration Class 1
[9](#api-configuration-class-1)](#api-configuration-class-1)

[5.1.3.1.1. Sub-Function: NvM_Init
[9](#sub-function-nvm_init)](#sub-function-nvm_init)

[5.1.3.1.2. Sub-Function: NvM_ReadAll
[10](#sub-function-nvm_readall)](#sub-function-nvm_readall)

[5.1.3.1.3. Sub-Function: NvM_WriteAll
[11](#sub-function-nvm_writeall)](#sub-function-nvm_writeall)

[5.1.3.1.4. Sub-Function: NvM_GetErrorStatus
[12](#sub-function-nvm_geterrorstatus)](#sub-function-nvm_geterrorstatus)

[5.1.3.1.5. Sub-Function: NvM_SetRamBlockStatus
[13](#sub-function-nvm_setramblockstatus)](#sub-function-nvm_setramblockstatus)

[5.1.3.1.6. Sub-Function: NvM_CancelWriteAll
[14](#sub-function-nvm_cancelwriteall)](#sub-function-nvm_cancelwriteall)

[5.1.3.2. API Configuration Class 2
[15](#api-configuration-class-2)](#api-configuration-class-2)

[5.1.3.2.1. Sub-Function: NvM_SetDataIndex
[15](#sub-function-nvm_setdataindex)](#sub-function-nvm_setdataindex)

[5.1.3.2.2. Sub-Function: NvM_GetDataIndex
[16](#sub-function-nvm_getdataindex)](#sub-function-nvm_getdataindex)

[5.1.3.2.3. Sub-Function: NvM_ReadBlock
[17](#sub-function-nvm_readblock)](#sub-function-nvm_readblock)

[5.1.3.2.4. Sub-Function: NvM_WriteBlock
[18](#sub-function-nvm_writeblock)](#sub-function-nvm_writeblock)

[5.1.3.2.5. Sub-Function: NvM_RestoreBlockDefaults
[19](#sub-function-nvm_restoreblockdefaults)](#sub-function-nvm_restoreblockdefaults)

[5.1.3.2.6. Sub-Function: NvM_CancelJobs
[20](#sub-function-nvm_canceljobs)](#sub-function-nvm_canceljobs)

[5.1.3.3. API Configuration Class 3
[21](#api-configuration-class-3)](#api-configuration-class-3)

[5.1.3.3.1. Sub-Function: NvM_SetBlockProtection
[21](#sub-function-nvm_setblockprotection)](#sub-function-nvm_setblockprotection)

[5.1.3.3.2. Sub-Function: NvM_EraseNvBlock
[22](#sub-function-nvm_erasenvblock)](#sub-function-nvm_erasenvblock)

[5.1.3.3.3. Sub-Function: NvM_InvalidateNvBlock
[23](#sub-function-nvm_invalidatenvblock)](#sub-function-nvm_invalidatenvblock)

[5.1.4. Type Definitions [24](#type-definitions)](#type-definitions)

[5.1.4.1. Std_ReturnType [24](#std_returntype)](#std_returntype)

[5.1.4.2. NvM_RequestResultType
[24](#nvm_requestresulttype)](#nvm_requestresulttype)

[5.1.4.3. NvM_BlockIdType [25](#nvm_blockidtype)](#nvm_blockidtype)

[5.2. NvM_Proxy: Non Volatile Memory Proxy (Nexteer CDD)
[26](#nvm_proxy-non-volatile-memory-proxy-nexteer-cdd)](#nvm_proxy-non-volatile-memory-proxy-nexteer-cdd)

[5.2.1. Design Rationale [26](#design-rationale-1)](#design-rationale-1)

[5.2.2. Sub-Functions [26](#sub-functions)](#sub-functions)

[5.2.2.1. Sub-Function: NvMProxy_Init
[26](#sub-function-nvmproxy_init)](#sub-function-nvmproxy_init)

[5.2.2.1.1. Hardware Related Design
[26](#hardware-related-design-15)](#hardware-related-design-15)

[5.2.2.1.2. Software Related Design
[26](#software-related-design-15)](#software-related-design-15)

[6. Timing / Execution Constraints
[27](#timing-execution-constraints)](#timing-execution-constraints)

[6.1. Rationale / Comments
[27](#rationale-comments)](#rationale-comments)

[6.2. Rates and State Execution: NvM
[27](#rates-and-state-execution-nvm)](#rates-and-state-execution-nvm)

[6.3. Rates and State Execution: NvMProxy
[28](#rates-and-state-execution-nvmproxy)](#rates-and-state-execution-nvmproxy)

[7. Serial Communications Interfaces
[28](#serial-communications-interfaces)](#serial-communications-interfaces)

[8. Additional Information
[29](#additional-information)](#additional-information)

[8.1. NvM block definition Considerations
[29](#nvm-block-definition-considerations)](#nvm-block-definition-considerations)

[8.1.1. Scenario 1 [29](#scenario-1)](#scenario-1)

[8.1.2. Scenario 2 [29](#scenario-2)](#scenario-2)

[8.2. Software Component Design Considerations
[30](#software-component-design-considerations)](#software-component-design-considerations)

[8.2.1. API Port Selection
[30](#api-port-selection)](#api-port-selection)

[9. Revision Record & Change Approval
[31](#revision-record-change-approval)](#revision-record-change-approval)

#  High Level Description

This design document describes the functionality, API, and the
configuration of the AUTOSAR basic software (BSW) module NVRAM Manager
(NvM) and the NvM Proxy (NvMProxy).

The NvM provides services to ensure the data storage and maintenance of
NV (non-volatile) data. The NvM module is able to administrate the NV
data for an EEPROM and/or a Flash EEPROM Emulation (FEE) device.

The NvMProxy provides an interface for software components outside of
the application of the NvM to communicate with the NvM component.

# Derived Requirements

None

#  Sub-Function Data Flow

None

#  Design Rationale

The NvM and NvMProxy components are integrated below the application
layer in the basic software layer of the AUTOSAR model.

NvMProxy was designed so that all software components can send their NvM
requests to the proxy interface, which will communicate the request to
the NvM and report the results back to the calling component. This
simplifies the design of software components by only requiring one
interface for defining NvM needs and providing the needed functionality
to switch the OS context in the event the calling application is
different than the application NvM is integrated.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image1.emf)

#  Components

The following sections describe the NvM and NvM proxy components.

## NvM: Non Volatile Memory (AUTOSAR BSW)

### BSW Configuration

#### NvMCommon

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 33%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuration Parameter</th>
<th>Value</th>
<th>Rationale</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>API Configuration Class</td>
<td>MVM_API_CONFIG_CLASS_3</td>
<td>Class 3 shall be used to provide all API options to software
components. This is to prevent rework of existing components if use
cases change and require API functions that may not have been available
during component development under a different API class.</td>
</tr>
<tr class="even">
<td>Compiled Configuration Id</td>
<td>1</td>
<td>Version of the NV memory layout, always shall start at 1 and be
revised if the memory layout changes</td>
</tr>
<tr class="odd">
<td>Crc Number of Bytes</td>
<td>64</td>
<td>Dummy value, not used.</td>
</tr>
<tr class="even">
<td>Dataset Selection Bits</td>
<td>1</td>
<td><p>Shall be set to 1 if the only block types are “native” and
“redundant.” If a dataset is required, then the number needs to be set
satisfy the following equation:</p>
<p><em>2^(Selection Bits) &gt;= max(dataset)</em></p>
<p>For example, if the largest dataset for all configured blocks was 30,
the selection bits are required to be set to 5.<br />
2^5 = 32 &gt;= 30</p></td>
</tr>
<tr class="odd">
<td>Development Error Detection</td>
<td>FALSE</td>
<td>Only should be true for early development. Shall not be used in
production level software</td>
</tr>
<tr class="even">
<td>Drivers Mode Switch</td>
<td>True</td>
<td>Disables processing of background sector switching from startup and
shutdown events.</td>
</tr>
<tr class="odd">
<td>Dynamic Configuration Handling</td>
<td>True</td>
<td>Allows for adapting new FEE layouts over existing layouts. See
section 5.1.3.2.2 for details on the impact of this setting.</td>
</tr>
<tr class="even">
<td>Job Prioritization</td>
<td>False</td>
<td>No requirement for prioritization of any blocks</td>
</tr>
<tr class="odd">
<td>Maximum Number of Write Retries</td>
<td>3</td>
<td>Default setting</td>
</tr>
<tr class="even">
<td>Multi Block Callback</td>
<td>NvMProxy_MultiBlkCallBack</td>
<td></td>
</tr>
<tr class="odd">
<td>Multi block Job Status Information</td>
<td>False</td>
<td></td>
</tr>
<tr class="even">
<td>Polling Mode</td>
<td>True</td>
<td>Enabled to provide the application the ability to poll the status of
the asynchronous request.</td>
</tr>
<tr class="odd">
<td>Repeat Mirror Operations</td>
<td>0</td>
<td>Default setting</td>
</tr>
<tr class="even">
<td>SetRamBlockStatus API</td>
<td>True</td>
<td>Applications shall use SetRamBlockStatus API to indicate their RAM
shadows have updated.</td>
</tr>
<tr class="odd">
<td>Size Of Immediate Status Information</td>
<td>N/A</td>
<td>Not used</td>
</tr>
<tr class="even">
<td>Size Of Standard Job Queue</td>
<td>8</td>
<td>Default setting</td>
</tr>
<tr class="odd">
<td>Version Information API</td>
<td>False</td>
<td>N/A</td>
</tr>
</tbody>
</table>

### Periodic Functions

#### NvM_MainFunction

This function has to be called cyclically. It is the entry point for the
NvM component. In this function processing of all asynchronous jobs are
handled (read/write/erase/invalidate/CRC calculation).

##### Function Definition

| Prototype                      |
|--------------------------------|
| void NvM_MainFunction ( void ) |
| Parameter                      |
| N/A                            |
| Return Code                    |
| N/A                            |

###  Service Sub-Functions

The value of the API configuration class determines which API server
ports are available to the system. The image below shows the breakdown
of the functionality for each API Configuration Class.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image2.emf)

In the following sub sections, the APIs are defined for application
software components (SWCs) and BSW components. The application function
definition shall be used for components that sit above the RTE layer in
the AUTOSAR model. The RTE generator will absorb some of the dynamic
arguments, such as BlockId, and create a macro with the proper
definition for the software component. Complex device drivers and other
BSWs that sit below the RTE layer shall use the CDD function definition.

####   [section]

#### API Configuration Class 1

The following sections contain a description of the functions provided
by the AUTOSAR NvM basic software component with API Configuration Class
1 configured.

##### Sub-Function: NvM_Init

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |                                                                     |
|---------------------|---------------------------------------------------|
| Request Type             | Synchronous                                                         |
| Re-entrant               | Yes                                                                 |
| Expected Caller Context  | Shall only be called from ECU state manager or equivalent function. |

Before the NvM component can be used, it has to be initialized.
Depending on the program the NvM is integrated, the BSWs from lower
levels shall be initialized prior to the NvM. The table below is an
example of this strategy for Fee and Ea use cases for initialize modules
from the low level components up to the NvM.

|                      | Fee | Ea      |
|----------------------|-----|---------|
| Low level driver     | Fls | SPI/EEP |
| Device Abstraction   | FEE | EA      |
| Non-Volatile Manager | NvM |         |

The NvM AUTOSAR component compliant with ASIL-D standards, NvM_Init
shall be called as a trusted function. This will allow the NvM_Init
function access to all the permanent RAM shadows defined in software,
regardless of their ASIL rating. This reduces the RAM and throughput
during start up to move data from application to another.

####### Application Function Definition

None

####### CDD Function Definition

| Prototype              |
|------------------------|
| void NvM_Init ( void ) |
| Parameter              |
| N/A                    |
| Return Code            |
| N/A                    |

#####  Sub-Function: NvM_ReadAll

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |                                                                     |
|---------------------|---------------------------------------------------|
| Request Type             | Asynchronous                                                        |
| Re-entrant               | No                                                                  |
| Expected Caller Context  | Shall only be called from ECU state manager or equivalent function. |

This function shall only be called after NvM_Init has been executed. The
request loads all the RAM blocks that have the option
NVM_SELECT_BLOCK_FOR_READALL selected.

Note: Non-permanent blocks and data set blocks are skipped during
execution of this function and must be loaded manually by calling
NvM_ReadBlock().

During the execution of NvM_ReadAll(), the value in the *configuration
ID* (block 1) is compared with the compiled ID version in the NvM
settings. With the *Dynamic Configuration Handling* option set to True,
any NvM blocks with the option *Resistant to Changed Software* enabled
will be processed and loaded into RAM as if the configuration IDs
matched. If the option *Resistant to Changed Software* is not enabled,
the blocks will be treated is if they were invalid or blank.

####### Application Function Definition

None

####### CDD Function Definition

| Prototype                 |
|---------------------------|
| void NvM_ReadAll ( void ) |
| Parameter                 |
| N/A                       |
| Return Code               |
| N/A                       |

#####  Sub-Function: NvM_WriteAll

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |                                                                     |
|---------------------|---------------------------------------------------|
| Request Type             | Asynchronous                                                        |
| Re-entrant               | No                                                                  |
| Expected Caller Context  | Shall only be called from ECU state manager or equivalent function. |

Request to write all blocks with RAM data that has been changed and have
the option NVM_SELECT_BLOCK_FOR_WRITEALL selected.

Note: Non-permanent blocks and data set blocks are skipped during
execution of this function and must be written manually by calling
NvM_WriteBlock().

####### Application Function Definition

None

####### CDD Function Definition

| Prototype                  |
|----------------------------|
| void NvM_WriteAll ( void ) |
| Parameter                  |
| N/A                        |
| Return Code                |
| N/A                        |

#####  Sub-Function: NvM_GetErrorStatus

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |             |
|--------------------------|-------------|
| Request Type             | Synchronous |
| Re-entrant               | Yes         |
| Expected Caller Context  | Application |

The request reads the block dependent status/error information and
writes it to the given address. The status/error information was set by
a former or current asynchronous request. This API can also be requested
with the block id 0 (multi block). The multi block status/error
information are only set by NvM_ReadAll() and NvM_WriteAll() requests.

####### Application Function Definition

| Prototype                                                                                                      |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_GetErrorStatus (uint8\* RequestResultPtr )                        |
| Parameter                                                                                                      |
| RequestResultPtr – Pointer were the result shall be written. See section 5.1.4.2 for details on return values. |
| Return Code                                                                                                    |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                            |

####### CDD Function Definition

| Prototype                                                                                                      |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_GetErrorStatus ( NvMBlockIdType BlockId, uint8\* RequestResultPtr )                         |
| Parameter                                                                                                      |
| BlockId – The block identifier                                                                                 |
| RequestResultPtr – Pointer were the result shall be written. See section 5.1.4.2 for details on return values. |
| Return Code                                                                                                    |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                            |

#####  [section-1]

#####  Sub-Function: NvM_SetRamBlockStatus

###### Hardware Related Design

None

###### Software Related Design

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 71%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Function Particularities</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Request Type</td>
<td><p>Synchronous (If <em>NVM_CALC_RAM_BLOCK_CRC</em> is False)</p>
<p>Asynchronous (If <em>NVM_CALC_RAM_BLOCK_CRC</em> is True)</p></td>
</tr>
<tr class="even">
<td>Re-entrant</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>Expected Caller Context</td>
<td>Application</td>
</tr>
</tbody>
</table>

The request sets a block’s status to valid/changed and also to
unchanged. Setting a block to valid/changed will mark it for writing
during NvM_WriteAll(). If a block has the CRC option
NVM_CALC_RAM_BLOCK_CRC set to True, the CRC calculation of the RAM is
initialed as a background task.

####### Application Function Definition

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Prototype</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Std_ReturnType Rte_Call_&lt;SWCSvcPortName&gt;_SetRamBlockStatus
(Boolean BlockChanged )</td>
</tr>
<tr class="even">
<td>Parameter</td>
</tr>
<tr class="odd">
<td><p>BlockChanged – TRUE: Validates the RAM block and marks it as
changed.</p>
<p>FALSE: Mark the block as unchanged</p></td>
</tr>
<tr class="even">
<td>Return Code</td>
</tr>
<tr class="odd">
<td>Std_ReturnType – See section 5.1.4.1 definition of this return
type</td>
</tr>
</tbody>
</table>

####### CDD Function Definition

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Prototype</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Std_ReturnType NvM_SetRamBlockStatus ( NvMBlockIdType BlockId,
Boolean BlockChanged )</td>
</tr>
<tr class="even">
<td>Parameter</td>
</tr>
<tr class="odd">
<td>BlockId – The block identifier</td>
</tr>
<tr class="even">
<td><p>BlockChanged – TRUE: Validates the RAM block and marks it as
changed.</p>
<p>FALSE: Mark the block as unchanged</p></td>
</tr>
<tr class="odd">
<td>Return Code</td>
</tr>
<tr class="even">
<td>Std_ReturnType – See section 5.1.4.1 definition of this return
type</td>
</tr>
</tbody>
</table>

#####  Sub-Function: NvM_CancelWriteAll

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |                                                                     |
|---------------------|---------------------------------------------------|
| Request Type             | Asynchronous                                                        |
| Re-entrant               | No                                                                  |
| Expected Caller Context  | Shall only be called from ECU state manager or equivalent function. |

Request to cancel a running NvM_WriteAll() request.

####### Application Function Definition

None

####### CDD Function Definition

| Prototype                        |
|----------------------------------|
| void NvM_CancelWriteAll ( void ) |
| Parameter                        |
| None                             |
| Return Code                      |
| None                             |

###  [section-2]

####  API Configuration Class 2

The following sections contain a description of the functions provided
by the AUTOSAR NvM basic software component with API Configuration Class
2 configured.

##### Sub-Function: NvM_SetDataIndex

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |             |
|--------------------------|-------------|
| Request Type             | Synchronous |
| Re-entrant               | Yes         |
| Expected Caller Context  | Application |

The request sets the specified index to associate a dataset NV block
(with or without ROM blocks) with its corresponding RAM block. The
DataIndex needs to have a valid value before read, write, erase or
invalidate requests are initiated.

If the dataset block has a set of ROM defaults, the function is used to
select the appropriate ROM set (prior to NvM_ReadBlock()).

####### Application Function Definition

| Prototype                                                                    |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_SetDataIndex (uint8 DataIndex ) |
| Parameter                                                                    |
| DataIndex – Index position of a block in the NV block Dataset type           |
| Return Code                                                                  |
| Std_ReturnType – See section 5.1.4.1 definition of this return type          |

####### CDD Function Definition

| Prototype                                                                   |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_SetDataIndex ( NvMBlockIdType BlockId, uint8 DataIndex ) |
| Parameter                                                                   |
| BlockId – The block identifier                                              |
| DataIndex – Index position of a block in the NV block Dataset type          |
| Return Code                                                                 |
| Std_ReturnType – See section 5.1.4.1 definition of this return type         |

<span class="mark">  
</span>

##### Sub-Function: NvM_GetDataIndex

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |             |
|--------------------------|-------------|
| Request Type             | Synchronous |
| Re-entrant               | Yes         |
| Expected Caller Context  | Application |

The request passes the current DataIndex of the specified dataset block.

####### Application Function Definition

| Prototype                                                                         |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_GetDataIndex (uint8\* DataIndexPtr ) |
| Parameter                                                                         |
| DataIndexPtr – Address where the current DataIndex shall be written to            |
| Return Code                                                                       |
| Std_ReturnType – See section 5.1.4.1 definition of this return type               |

####### CDD Function Definition

| Prototype                                                                        |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_GetDataIndex ( NvMBlockIdType BlockId, uint8\* DataIndexPtr ) |
| Parameter                                                                        |
| BlockId – The block identifier                                                   |
| DataIndexPtr – Address where the current DataIndex shall be written to           |
| Return Code                                                                      |
| Std_ReturnType – See section 5.1.4.1 definition of this return type              |

##### Sub-Function: NvM_ReadBlock

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request to copy the data of the NV block to its corresponding RAM block.
This function queues the read request and returns the acceptance result
synchronously.

####### Application Function Definition

| Prototype                                                                                                                                 |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_ReadBlock (uint8\* NvM_DstPtr )                                                              |
| Parameter                                                                                                                                 |
| NvM_DstPtr – Pointer where the data of a non-permanent RAM block shall be written to. If the block is permanent NULL_PTR shall be passed. |
| Return Code                                                                                                                               |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                       |

####### CDD Function Definition

| Prototype                                                                                                                                 |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_ReadBlock ( NvMBlockIdType BlockId, uint8\* NvM_DstPtr)                                                                |
| Parameter                                                                                                                                 |
| BlockId – The block identifier                                                                                                            |
| NvM_DstPtr – Pointer where the data of a non-permanent RAM block shall be written to. If the block is permanent NULL_PTR shall be passed. |
| Return Code                                                                                                                               |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                       |

##### Sub-Function: NvM_WriteBlock

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request for copying data from the RAM block to its corresponding NV
block. This function queues the write request and returns the acceptance
result synchronously.

If the block has a CRC, the RAM block CRC will be recalculated before
the data and the CRC are written to the NV memory, even if the service
NvM_SetRamBlockStatus() was called before and the configuration was set
that within this service, the CRC calculation should be done.

If writing the data to NV memory fails, the NVM will retry writing. The
number of write retries is a configuration option.

####### Application Function Definition

| Prototype                                                                                                                                 |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_WriteBlock (const uint8\* NvM_SrcPtr )                                                       |
| Parameter                                                                                                                                 |
| NvM_SrcPtr – Pointer where the data of a non-permanent RAM block shall be read from. If the block is permanent, NULL_PTR shall be passed. |
| Return Code                                                                                                                               |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                       |

####### CDD Function Definition

| Prototype                                                                                                                                 |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_WriteBlock ( NvMBlockIdType BlockId, const uint8\* NvM_SrcPtr)                                                         |
| Parameter                                                                                                                                 |
| BlockId – The block identifier                                                                                                            |
| NvM_SrcPtr – Pointer where the data of a non-permanent RAM block shall be read from. If the block is permanent, NULL_PTR shall be passed. |
| Return Code                                                                                                                               |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                       |

##### Sub-Function: NvM_RestoreBlockDefaults

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request to copy the ROM block default data to its corresponding RAM
block. The selected block needs either ROM defaults or an initialization
callback. This function queues the restore request and returns the
acceptance results synchronously.

####### Application Function Definition

| Prototype                                                                                                                                  |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_RestoreBlockDefaults (uint8\* NvM_DstPtr )                                                    |
| Parameter                                                                                                                                  |
| NvM_DstPtr – Pointer where the data of a non-permanent RAM block shall be written to. If the block is permanent, NULL_PTR shall be passed. |
| Return Code                                                                                                                                |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                        |

####### CDD Function Definition

| Prototype                                                                                                                                  |
|------------------------------------------------------------------------|
| Std_ReturnType NvM_RestoreBlockDefaults ( NvMBlockIdType BlockId, uint8\* NvM_DstPtr)                                                      |
| Parameter                                                                                                                                  |
| BlockId – The block identifier                                                                                                             |
| NvM_DstPtr – Pointer where the data of a non-permanent RAM block shall be written to. If the block is permanent, NULL_PTR shall be passed. |
| Return Code                                                                                                                                |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                                                                        |

##### Sub-Function: NvM_CancelJobs

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request to cancel pending job for a NV block.

####### Application Function Definition

None

####### CDD Function Definition

| Prototype                                                           |
|---------------------------------------------------------------------|
| Std_ReturnType NvM_CancelJobs ( NvMBlockIdType BlockId )            |
| Parameter                                                           |
| BlockId – The block identifier                                      |
| Return Code                                                         |
| Std_ReturnType – See section 5.1.4.1 definition of this return type |

#### API Configuration Class 3

The following sections contain a description of the functions provided
by the AUTOSAR NvM basic software component with API Configuration Class
3 configured.

##### Sub-Function: NvM_SetBlockProtection

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |             |
|--------------------------|-------------|
| Request Type             | Synchronous |
| Re-entrant               | Yes         |
| Expected Caller Context  | Application |

The request sets the write protection for the NV block. Any further
write, erase, and invalidate requests to the NVRAM block is rejected
synchronously if the NV block-write protection is set. The data area of
the RAM block remains writeable in any case.

####### Application Function Definition

| Prototype                                                                                     |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_SetBlockProtection ( Boolean ProtectionEnabled ) |
| Parameter                                                                                     |
| ProtectionEnabled – True: Enable protection. False: Disable protection                        |
| Return Code                                                                                   |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                           |

####### CDD Function Definition

| Prototype                                                                                     |
|------------------------------------------------------------------------|
| Std_ReturnType NvM\_ SetBlockProtection ( NvMBlockIdType BlockId, Boolean ProtectionEnabled ) |
| Parameter                                                                                     |
| BlockId – The block identifier                                                                |
| ProtectionEnabled – True: Enable protection. False: Disable protection                        |
| Return Code                                                                                   |
| Std_ReturnType – See section 5.1.4.1 definition of this return type                           |

##### Sub-Function: NvM_EraseNvBlock

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request to erase the specified NV block. This function queues the erase
request and returns the acceptance result synchronously. The NvM can
notify the application by callback when the service is finished. This
function performs the same action as NvM_InvalidateNvBlock for FEE.

####### Application Function Definition

| Prototype                                                           |
|---------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_EraseNvBlock ( void )  |
| Parameter                                                           |
| None                                                                |
| Return Code                                                         |
| Std_ReturnType – See section 5.1.4.1 definition of this return type |

####### CDD Function Definition

| Prototype                                                           |
|---------------------------------------------------------------------|
| Std_ReturnType NvM_EraseNvBlock ( NvMBlockIdType BlockId )          |
| Parameter                                                           |
| BlockId – The block identifier                                      |
| Return Code                                                         |
| Std_ReturnType – See section 5.1.4.1 definition of this return type |

##### Sub-Function: NvM_InvalidateNvBlock

###### Hardware Related Design

None

###### Software Related Design

| Function Particularities |              |
|--------------------------|--------------|
| Request Type             | Asynchronous |
| Re-entrant               | Yes          |
| Expected Caller Context  | Application  |

Request to invalidate the specified NV block. This function queues the
erase request and returns the acceptance result synchronously. The NvM
can notify the application by callback when the service is finished.

####### Application Function Definition

| Prototype                                                               |
|------------------------------------------------------------------------|
| Std_ReturnType Rte_Call\_\<SWCSvcPortName\>\_InvalidateNvBlock ( void ) |
| Parameter                                                               |
| None                                                                    |
| Return Code                                                             |
| Std_ReturnType – See section 5.1.4.1 definition of this return type     |

####### CDD Function Definition

| Prototype                                                           |
|---------------------------------------------------------------------|
| Std_ReturnType NvM_InvalidateNvBlock ( NvMBlockIdType BlockId )     |
| Parameter                                                           |
| BlockId – The block identifier                                      |
| Return Code                                                         |
| Std_ReturnType – See section 5.1.4.1 definition of this return type |

### Type Definitions

The following section outlines the data types used by the NvM component.

#### Std_ReturnType

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 51%" />
<col style="width: 37%" />
</colgroup>
<thead>
<tr class="header">
<th>C-Type</th>
<th>Description</th>
<th>Value Range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>uint8</td>
<td>Standard return type for functions</td>
<td><p>NVM_REQ_OK (0)</p>
<p><em>The last request has been accepted</em></p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><p>NVM_REQ_NOT_OK (1)</p>
<p><em>The last request has not been accepted</em></p></td>
</tr>
</tbody>
</table>

#### NvM_RequestResultType

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 51%" />
<col style="width: 37%" />
</colgroup>
<thead>
<tr class="header">
<th>C-Type</th>
<th>Description</th>
<th>Value Range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td rowspan="7">uint8</td>
<td rowspan="7">An asynchronous API service can have the following
results or status that can be polled by NvM_GetErrorStatus</td>
<td><p>NVM_REQ_OK (0)</p>
<p><em>The last request has finished successfully.</em></p></td>
</tr>
<tr class="even">
<td><p>NVM_REQ_NOT_OK (1)</p>
<p><em>The last request has finished unsuccessfully</em></p></td>
</tr>
<tr class="odd">
<td><p>NVM_REQ_PENDING (2)</p>
<p><em>The last request is currently being processed</em></p></td>
</tr>
<tr class="even">
<td><p>NVM_REQ_INTEGRITY_FAILED (3)</p>
<p><em>A NV block with data corruption caused by a CRC mismatch or FEE
or EA components reported an inconsistency</em></p></td>
</tr>
<tr class="odd">
<td><p>NVM_REQ_BLOCK_SKIPPED (4)</p>
<p><em>The block was skipped during a multi-block request (ReadAll or
WriteAll requests)</em></p></td>
</tr>
<tr class="even">
<td><p>NVM_REQ_NV_INVALIDATED (5)</p>
<p><em>The block is marked as invalid</em></p></td>
</tr>
<tr class="odd">
<td>NVM_REQ_CANCELLED (6)</td>
</tr>
</tbody>
</table>

#### NvM_BlockIdType

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 51%" />
<col style="width: 37%" />
</colgroup>
<thead>
<tr class="header">
<th>C-Type</th>
<th>Description</th>
<th>Value Range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>uint16</td>
<td><p>It is the type of a block handle that is used by the application
in order to access a NVM block. There are two reserved IDs:</p>
<ul>
<li><p>Block ID 0 for multi block requests (Block ID 0 is only allowed
for API NvM_GetErrorStatus())</p></li>
<li><p>Block ID 1 for the configuration Id block.</p></li>
</ul>
<p>The block handles are created as defines in an ascending define
list.</p></td>
<td><p>0..(2^(16 - <em>Dataset Selection Bits</em>) – 1)</p>
<p><em>Dataset Selection Bits</em> is the maximum number of bits that
are needed in order to store the maximum dataset value as is configured
by the software integration team.</p>
<p>Following the example from section 5.1.1.1 where <em>Dataset
Selection Bits</em> was equal to 5, the max number of block handles
would be 2^(16-5)-1=2047</p></td>
</tr>
</tbody>
</table>

## NvM_Proxy: Non Volatile Memory Proxy (Nexteer CDD)

### Design Rationale

The NvM_Proxy provides and interface to the NvM for all software
components. The interface shall consist of the API modules defined in
the previous sections for the AUTOSAR NvM component with the prefix of
NvMProxy instead of NvM.

If the calling component is in the same ASIL application as the NvM, the
proxy shall just forward the request on directly. If the component is
not in the same ASIL application as the NvM, the proxy shall call a
nontrusted function to switch the OS context to the application of the
NvM and then call the desired function.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image3.emf)

The NvMProxy component shall also be responsible for settings NTC 0x06,
0x07, 0x08 and 0x0A when a block that is invalid by not being written or
when the CRC check fails if one is applied to the block. This check
shall be done during the initialization routine of the NvMProxy
component.

NvMProxy shall also store all RAM status flags during shutdown to RAM,
so they can be restored during a quick ignition cycle. The restoration
shall take place if the NvM_WriteAll is completed, canceled or killed by
the BswM.

### Sub-Functions

#### Sub-Function: NvMProxy_Init

##### Hardware Related Design

None

##### Software Related Design

| Function Particularities |                                                                     |
|---------------------|---------------------------------------------------|
| Request Type             | Synchronous                                                         |
| Re-entrant               | Yes                                                                 |
| Expected Caller Context  | Shall only be called from ECU state manager or equivalent function. |

Before the NvMProxy component can be used, it has to be initialized.
This call also must be performed after the NvM_ReadAll() has finished
executing to properly diagnose all NvM blocks for any data corruption.

# Timing / Execution Constraints

## Rationale / Comments

## Rates and State Execution: NvM

In the following table, functions marked with 0ms run rate are function
calls that can be called from the states indicated by “Execute.”

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 13%" />
<col style="width: 14%" />
<col style="width: 15%" />
<col style="width: 11%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Sub-Function Name</strong></th>
<th><strong>Rate (ms)</strong></th>
<th><strong>Cold Init</strong></th>
<th><strong>Warm Init</strong></th>
<th><strong>Operate</strong></th>
<th><strong>Disable</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NvM_Init</td>
<td>0</td>
<td>Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
</tr>
<tr class="even">
<td>NvM_MainFunction</td>
<td>10</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_ReadAll</td>
<td>0</td>
<td>Execute*</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
</tr>
<tr class="even">
<td>NvM_WriteAll</td>
<td>0</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_GetErrorStatus</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_SetRamBlockStatus</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_CancelWriteAll</td>
<td>0</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_SetDataIndex</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_GetDataIndex</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_ReadBlock</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_WriteBlock</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_RestoreBlockDefaults</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_CancelJobs</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_SetBlockProtection</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvM_EraseNvBlock</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvM_InvalidateNvBlock</td>
<td>0</td>
<td>Execute**</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td colspan="6"><p><em>* Execution is allowed, but only after NvM_Init()
has completed.</em></p>
<p><em>** Execution is allowed, but only after NvM_ReadAll() has
completed.</em></p></td>
</tr>
</tbody>
</table>

##  [section-3]

## Rates and State Execution: NvMProxy

In the following table, functions marked with 0ms run rate are function
calls that can be called from the states indicated by “Execute.”

<table>
<colgroup>
<col style="width: 38%" />
<col style="width: 10%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Sub-Function Name</strong></th>
<th><strong>Rate (ms)</strong></th>
<th><strong>Cold Init</strong></th>
<th><strong>Warm Init</strong></th>
<th><strong>Operate</strong></th>
<th><strong>Disable</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NvMProxy_Init</td>
<td>0</td>
<td>Execute**</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_GetErrorStatus</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_SetRamBlockStatus</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_CancelWriteAll</td>
<td>0</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Do Not Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_SetDataIndex</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_GetDataIndex</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_ReadBlock</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_WriteBlock</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_RestoreBlockDefaults</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_CancelJobs</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_SetBlockProtection</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td>NvMProxy_EraseNvBlock</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="odd">
<td>NvMProxy_InvalidateNvBlock</td>
<td>0</td>
<td>Execute*</td>
<td>Execute</td>
<td>Execute</td>
<td>Execute</td>
</tr>
<tr class="even">
<td colspan="6"><p><em>* Execution is allowed, but only after
NvMProxy_Init() has completed.</em></p>
<p><em>** Execution is allowed, but only after NvM_ReadAll() has
completed.</em></p></td>
</tr>
</tbody>
</table>

# Serial Communications Interfaces

None

# Additional Information

## NvM block definition Considerations

NvM block can be made from a single value to multiple values grouped as
one element. It is up to the function designer to determine how their
NvM blocks should be structured, but the following considerations should
be considered when defining an NvM block.

### Scenario 1

Consider a design with 3 PIMs defined for storage in NvM. If the PIMs
were defined in the m-files as separate entries, the software component
developer would create three separate NvM blocks for those pieces of
data as shown below.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image4.emf)

This would mean that each PIM, is independent of the other PIMs,
however, it is a waste of FEE memory if the data does not truly need to
be independent. Instead the three values should be grouped into a
structure so the NvM block created looks like below.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image5.emf)

This provides the designer with the same design (three separate
variables) but the data is grouped together to make one CRC to cover all
three values and only requires one instance of the FEE header saving FEE
space.

### Scenario 2

Consider a design with 3 PIMs, 2 of the PIMs are written during
manufacturing and the other PIM is learned during function execution and
saved at shutdown. In this case, it would make sense to group the PIMs
by functionality.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES006A_NvM_Design/Doc/mediax/media/image6.emf)

This saves FEE space by grouping like content, but also protects the
data that is written during manufacturing from being discarded in case
the data that is written during shutdown encountered a power loss or
other type of data corruption. Only the learned data would be considered
invalid and the other block would be valid.

## Software Component Design Considerations

### API Port Selection

The NvM component will generate different API ports depending on the
configuration required a given block. It shall be up to the developer of
the software component to configure the service port with the correct
API during development to ensure a proper match with the integration
project.

Based on the settings in section 5.1.1, the API port will begin with
“NvMService_AC3_SRBS”. This is because the API class is level 3 (AC3)
and the set ram block status API is enable (SRBS).

The following table is for all API access except for NvM\_
SetBlockProtection.

| Configuration Matrix |           |         |             | Suffix    | Port Name to Use in SWC     |
|-------|----------|--------|--------------|----------|--------------------------|
| Block Type           |           |         | ROM Default |           |                             |
| Native               | Redundant | Dataset |             |           |                             |
| Y                    | N         | N       | N           | N/A       | NvMService_AC3_SRBS         |
| Y                    | N         | N       | Y           | \_Defs    | NvMService_AC3_SRBS_Defs    |
| N                    | Y         | N       | N           | N/A       | NvMService_AC3_SRBS         |
| N                    | Y         | N       | Y           | \_Defs    | NvMService_AC3_SRBS_Defs    |
| N                    | N         | Y       | N           | \_DS      | NvMService_AC3_SRBS_DS      |
| N                    | N         | Y       | Y           | \_DS_Defs | NvMService_AC3_SRBS_DS_Defs |

The following table is only for API to NvM\_ SetBlockProtection.

| Configuration Matrix |           |         |             | Suffix | Port Name to Use in SWC |
|-------|----------|--------|--------------|----------|--------------------------|
| Block Type           |           |         | ROM Default |        |                         |
| Native               | Redundant | Dataset |             |        |                         |
| Y                    | N         | N       | N           | N/A    | NvMAdministration       |
| Y                    | N         | N       | Y           |        |                         |
| N                    | Y         | N       | N           |        |                         |
| N                    | Y         | N       | Y           |        |                         |
| N                    | N         | Y       | N           |        |                         |
| N                    | N         | Y       | Y           |        |                         |

#  Revision Record & Change Approval

|          |          |                       |         |                                           |
|--------|--------|----------|-------|---------------------------------------|
| **Rev**  | **Date** | **Change Control \#** | **Drw** | **Change Description**                    |
| 01.00.00 | 01Sep15  | EA4#471               | KJS     | Initial Release                           |
| 02.00.00 | 01Oct16  | EA4#7778              | KJS     | Updates for quick ignition cycle handling |

{% endraw %}