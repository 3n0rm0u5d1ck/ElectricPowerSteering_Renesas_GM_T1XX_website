---
layout: default
title: XcpIf_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**XCP Interface (XcpIf)**

**VERSION: 2.0**

**DATE: 29-Aug-2016**

**Prepared By:**

**Kevin Smith**

**EPS Software,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                              |            |             |           |                 |
|-----|-------------------|-------------------|--------|-----------|-----------|
| **Sl. No.** | **Description**              | **Author** | **Version** | **Date**  | **Approved By** |
| 1           | Initial Version              | K. Smith   | 1.0         | 16-Jun-15 |                 |
| 2           | Updates for anomaly EA4#6672 | K. Smith   | 2.0         | 29-Aug-16 |                 |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[5](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [6](#references)](#references)

[3 XCP Interface & High-Level Description
[7](#xcp-interface-high-level-description)](#xcp-interface-high-level-description)

[4 Design details of software module
[8](#design-details-of-software-module)](#design-details-of-software-module)

[4.1 Graphical representation of XCP Interface
[8](#graphical-representation-of-xcp-interface)](#graphical-representation-of-xcp-interface)

[4.2 Data Flow Diagram [8](#data-flow-diagram)](#data-flow-diagram)

[4.2.1 Module level DFD [8](#module-level-dfd)](#module-level-dfd)

[4.2.2 Sub-Module level DFD
[8](#sub-module-level-dfd)](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM
[8](#component-flow-diagram)](#component-flow-diagram)

[5 Variable Data Dictionary
[9](#variable-data-dictionary)](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
[9](#user-defined-typedef-definitiondeclaration)](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
[9](#variable-definition-for-enumerated-types)](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary
[10](#constant-data-dictionary)](#constant-data-dictionary)

[6.1 Program(fixed) Constants
[10](#programfixed-constants)](#programfixed-constants)

[6.1.1 Embedded Constants
[10](#embedded-constants)](#embedded-constants)

[6.1.1.1 Local [10](#local)](#local)

[6.1.1.2 Global [10](#global)](#global)

[6.1.2 Module specific Lookup Tables Constants
[10](#module-specific-lookup-tables-constants)](#module-specific-lookup-tables-constants)

[7 Software Module Implementation
[11](#software-module-implementation)](#software-module-implementation)

[7.1 Sub-Module Functions
[11](#sub-module-functions)](#sub-module-functions)

[7.2 Initialization Functions
[11](#initialization-functions)](#initialization-functions)

[7.3 PERIODIC FUNCTIONS [11](#periodic-functions)](#periodic-functions)

[7.3.1 Xcp2msDaq [11](#xcp2msdaq)](#xcp2msdaq)

[7.3.1.1 Design Rationale [11](#design-rationale)](#design-rationale)

[7.3.1.2 Store Module Inputs to Local copies
[11](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[7.3.1.3 (Processing of function)………
[11](#processing-of-function)](#processing-of-function)

[7.3.1.4 Store Local copy of outputs into Module Outputs
[11](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[7.4 Non PERIODIC FUNCTIONS
[11](#non-periodic-functions)](#non-periodic-functions)

[7.5 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[7.6 Serial Communication Functions
[11](#serial-communication-functions)](#serial-communication-functions)

[7.7 Local Function/Macro Definitions
[11](#local-functionmacro-definitions)](#local-functionmacro-definitions)

[7.8 GLObAL Function/Macro Definitions
[11](#_Toc422301834)](#_Toc422301834)

[7.8.1 ApplXcpGetTimestamp
[11](#applxcpgettimestamp)](#applxcpgettimestamp)

[7.8.1.1 Description [12](#description)](#description)

[7.8.2 ApplXcpGetPointer [12](#applxcpgetpointer)](#applxcpgetpointer)

[7.8.2.1 Description [12](#description-1)](#description-1)

[7.8.3 ApplXcpCalibrationWrite [12](#_Toc422301839)](#_Toc422301839)

[7.8.3.1 Description [12](#description-2)](#description-2)

[7.8.4 ApplXcpWrCmn [13](#_Toc422301841)](#_Toc422301841)

[7.8.4.1 Description [13](#description-3)](#description-3)

[7.8.5 ApplXcpCalibrationRead
[13](#applxcpcalibrationread)](#applxcpcalibrationread)

[7.8.5.1 Description [13](#description-4)](#description-4)

[7.9 TRANSIENT FUNCTIONS
[13](#applxcpcheckwriteaccess)](#applxcpcheckwriteaccess)

[8 Unit Test Considerations
[14](#unit-test-considerations)](#unit-test-considerations)

[9 Known Limitations With Design
[15](#known-limitations-with-design)](#known-limitations-with-design)

[10 Appendix [16](#appendix)](#appendix)

# Abbrevations And Acronyms

| Abbreviation | Description                             |
|--------------|-----------------------------------------|
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| Sr. No. | Title                           | Version       |
|---------|---------------------------------|---------------|
| \<1\>   | \<MDD Guidelines\>              | 4.0.0         |
| \<2\>   | \<Software Naming Conventions\> | 4.0.0         |
| \<3\>   | \<Coding standards\>            | 4.0.0         |
| \<4\>   | \<FDD \>                        | Not available |
|         | \<Add if more available\>       |               |

# XCP Interface & High-Level Description

XCP Interface provides multiple functions that allow XCP end users and
tools to interface with software components contained in the
application.

# Design details of software module

## Graphical representation of XCP Interface

*None*

## Data Flow Diagram

*None*

## Module level DFD

*None*

## Sub-Module level DFD

*None*

## COMPONENT FLOW DIAGRAM

*None*

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Typedef Name</th>
<th>Element Name</th>
<th>User Defined Type</th>
<th><p>Legal Range</p>
<p>(min)</p></th>
<th><p>Legal Range</p>
<p>(max)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

| Enum Name | Element Name | Value |
|-----------|--------------|-------|
|           |              |       |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

## Local

| Constant Name | Resolution | Units | Value |
|---------------|------------|-------|-------|
|               |            |       |       |

## Global

| Constant Name             |
|---------------------------|
| XcpEventChannel_2ms_DAQ_2 |

## Module specific Lookup Tables Constants

| Constant Name | Resolution | Value | Software Segment |
|---------------|------------|-------|------------------|
|               |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*None*

## Initialization Functions

*None*

## PERIODIC FUNCTIONS 

## Xcp2msDaq

## Design Rationale

*This function is called every 2ms for executing the XcpEvent functions
for the 2ms DAQ.*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES104A_XcpIf_Impl/doc/mediax/media/image1.emf)

## Store Local copy of outputs into Module Outputs

*None*

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

None

<span id="_Toc422301834" class="anchor"></span>

## GLObAL Function/Macro Definitions

## ApplXcpGetTimestamp

|                      |                     |                     |                 |                 |
|-------------|----------------------------|--------------|---------|---------|
| **Function Name**    | ApplXcpGetTimestamp | Type                | Min             | Max             |
| **Arguments Passed** | None                |                     |                 |                 |
|                      |                     |                     |                 |                 |
| **Return Value**     | Timestamp_Cnt_T_u32 | XcpDaqTimestampType | See description | See description |

## Description

This function returns the timestamp that is based on a reference timer.
The range of return values vary depending on the configuration of the
Xcp Component. The data type can range from a full range of a uint8 to a
uint32 value.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES104A_XcpIf_Impl/doc/mediax/media/image2.emf)

## ApplXcpGetPointer

|                      |                   |            |     |            |
|----------------------|-------------------|------------|-----|------------|
| **Function Name**    | ApplXcpGetPointer | Type       | Min | Max        |
| **Arguments Passed** | addr_ext          | vuint8     | 0   | 255        |
|                      | addr              | vuint32    | 1   | 4294967295 |
| **Return Value**     | RtnAddr_Cnt_T_u32 | MTABYTEPTR | 1   | 4294967295 |

## Description

This function takes the extension and address of and returns the
physical address of the item.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES104A_XcpIf_Impl/doc/mediax/media/image3.emf)

<span id="_Toc422301839" class="anchor"></span>

## ApplXcpCalibrationWrite

|                      |                         |            |     |            |
|----------------------|-------------------------|------------|-----|------------|
| **Function Name**    | ApplXcpCalibrationWrite | Type       | Min | Max        |
| **Arguments Passed** | addr                    | MTABYTEPTR | 1   | 4294967295 |
|                      | size                    | Vuint8     | 0   | 255        |
|                      | data                    | BYTEPTR    | 1   | 4294967295 |
| **Return Value**     | XCP_CMD_OK              | Uint8      | 0   | 0          |

## Description

This function calls the common XCP writing function. For this deisgn,
the function call will be translated into a trusted function call.

<span id="_Toc422301841" class="anchor"></span>

## ApplXcpWrCmn

|                      |              |            |     |            |
|----------------------|--------------|------------|-----|------------|
| **Function Name**    | ApplXcpWrCmn | Type       | Min | Max        |
| **Arguments Passed** | addr         | MTABYTEPTR | 1   | 4294967295 |
|                      | size         | Vuint8     | 0   | 255        |
|                      | data         | BYTEPTR    | 1   | 4294967295 |
| **Return Value**     | XCP_CMD_OK   | Uint8      | 0   | 0          |

## Description

This function writes the data passed in by the XCP user to the
designated address.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES104A_XcpIf_Impl/doc/mediax/media/image5.emf)

## ApplXcpCalibrationRead

|                      |                        |            |     |            |
|----------------------|------------------------|------------|-----|------------|
| **Function Name**    | ApplXcpCalibrationRead | Type       | Min | Max        |
| **Arguments Passed** | addr                   | MTABYTEPTR | 1   | 4294967295 |
|                      | size                   | Vuint8     | 0   | 255        |
|                      | data                   | BYTEPTR    | 1   | 4294967295 |
| **Return Value**     | XCP_CMD_OK             | Uint8      | 0   | 0          |

## Description

This function reads the data in the designated address and returns it to
the XCP user.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES104A_XcpIf_Impl/doc/mediax/media/image6.emf)

##  ApplXcpCheckWriteAccess

|                      |                         |            |     |            |
|----------------------|-------------------------|------------|-----|------------|
| **Function Name**    | ApplXcpCheckWriteAccess | Type       | Min | Max        |
| **Arguments Passed** | addr                    | MTABYTEPTR | 1   | 4294967295 |
|                      | Size_Cnt_T_u08          | Vuint8     | 0   | 255        |
| **Return Value**     | XCP_CMD_OK              | Uint8      | 0   | 0          |

## Description

This function checks access for XCP writes. Since the functions in
tuning selection management handle the presmissions for writes, this
function shall always return a positive response.

## ApplXcpCheckReadAccess

|                      |                        |            |     |            |
|----------------------|------------------------|------------|-----|------------|
| **Function Name**    | ApplXcpCheckReadAccess | Type       | Min | Max        |
| **Arguments Passed** | addr                   | MTABYTEPTR | 1   | 4294967295 |
|                      | Size_Cnt_T_u08         | Vuint8     | 0   | 255        |
| **Return Value**     | XCP_CMD_OK             | Uint8      | 0   | 0          |

## Description

This function checks access for XCP reads. Since the functions in tuning
selection management handle the presmissions for reads, this function
shall always return a positive response.

## ApplXcpCheckDAQAccess

|                      |                       |            |     |            |
|----------------------|-----------------------|------------|-----|------------|
| **Function Name**    | ApplXcpCheckDAQAccess | Type       | Min | Max        |
| **Arguments Passed** | addr                  | MTABYTEPTR | 1   | 4294967295 |
|                      | Size_Cnt_T_u08        | Vuint8     | 0   | 255        |
| **Return Value**     | XCP_CMD_OK            | Uint8      | 0   | 0          |

## Description

This function checks access for XCP DAQ access. Since all reads are
allowed, this function will also always return a positive response.

## ApplXcpSetCalPage

|                      |                   |        |     |      |
|----------------------|-------------------|--------|-----|------|
| **Function Name**    | ApplXcpSetCalPage | Type   | Min | Max  |
| **Arguments Passed** | Seg_Cnt_T_u08     | Vuint8 | 0   | 255  |
|                      | Page_Cnt_T_u08    | Vuint8 | 0   | 255  |
|                      | Mod_Cnt_T_u08     | Vuint8 | 0   | 255  |
| **Return Value**     | Rtn_Cnt_T_u08     | Uint8  | 0   | 0x28 |

## Description

This function sets the calibration page access. It directly calls the
functions used in tuning selection management.

## ApplXcpGetCalPage

|                      |                   |        |     |      |
|----------------------|-------------------|--------|-----|------|
| **Function Name**    | ApplXcpGetCalPage | Type   | Min | Max  |
| **Arguments Passed** | Seg_Cnt_T_u08     | Vuint8 | 0   | 255  |
|                      | Mod_Cnt_T_u08     | Vuint8 | 0   | 255  |
| **Return Value**     | Rtn_Cnt_T_u08     | Uint8  | 0   | 0x28 |

## Description

This function sets the calibration page access. It directly calls the
functions used in tuning selection management.

## ApplXcpCopyCalPage

|                      |                    |        |     |      |
|----------------------|--------------------|--------|-----|------|
| **Function Name**    | ApplXcpCopyCalPage | Type   | Min | Max  |
| **Arguments Passed** | SrcSeg_Cnt_T_u08   | Vuint8 | 0   | 255  |
|                      | SrcPage_Cnt_T_u08  | Vuint8 | 0   | 255  |
|                      | DestSeg_Cnt_T_u08  | Vuint8 | 0   | 255  |
|                      | DestPage_Cnt_T_u08 | Vuint8 | 0   | 255  |
| **Return Value**     | XCP_CMD_OK         | Uint8  | 0   | 0x28 |

## Description

This function sets the calibration page access. It directly calls the
functions used in tuning selection management.

## ApplXcpUserService

|                      |                    |         |     |            |
|----------------------|--------------------|---------|-----|------------|
| **Function Name**    | ApplXcpUserService | Type    | Min | Max        |
| **Arguments Passed** | pCmd               | BYTEPTR | 0   | 4294967295 |
| **Return Value**     | XCP_CMD_OK         | Uint8   | 0   | 0x3        |

## Description

This function handles user service requests.

## ApplXcpOpenCmdIf

|                      |                  |         |     |            |
|----------------------|------------------|---------|-----|------------|
| **Function Name**    | ApplXcpOpenCmdIf | Type    | Min | Max        |
| **Arguments Passed** | pCmd             | BYTEPTR | 0   | 4294967295 |
|                      | pRes             | BYTEPTR | 0   | 4294967295 |
|                      | pLength          | BYTEPTR | 0   | 4294967295 |
| **Return Value**     | XCP_CMD_OK       | Uint8   | 0   | 0x3        |

## Description

This function handles XCP service requests that are not supported by the
driver but defined by the XCP protocol specification.

## NONTRUSTED_NtWrapS_Rte_Call_CopyCalPageReq_Oper

|                      |                                                 |                                    |     |       |
|--------|------------------------------|---------------------|-----|---------|
| **Function Name**    | NONTRUSTED_NtWrapS_Rte_Call_CopyCalPageReq_Oper | Type                               | Min | Max   |
| **Arguments Passed** | FunctionIndex                                   | NonTrustedFunctionIndexType        | 0   | 65535 |
|                      | FunctionParams                                  | NonTrustedFunctionParameterRefType | N/A | N/A   |
| **Return Value**     | N/A                                             | N/A                                | N/A | N/A   |

## Description

## NONTRUSTED_NtWrapS_Rte_Call_SetCalPageReq_Oper

|                      |                                                |                                    |     |       |
|--------|------------------------------|----------------------|-----|---------|
| **Function Name**    | NONTRUSTED_NtWrapS_Rte_Call_SetCalPageReq_Oper | Type                               | Min | Max   |
| **Arguments Passed** | FunctionIndex                                  | NonTrustedFunctionIndexType        | 0   | 65535 |
|                      | FunctionParams                                 | NonTrustedFunctionParameterRefType | N/A | N/A   |
| **Return Value**     | N/A                                            | N/A                                | N/A | N/A   |

## Description

## TRANSIENT FUNCTIONS 

*None*

# Unit Test Considerations

-   The value datatype of XcpDaqTimestampType can be uint8, uint16, or
    uint32 depending on the configuration of XCP. Unit testing shall
    test full ranges for all three types to ensure proper functionality.

# Known Limitations With Design

-   There are no protections in this design for executing on NULL_PTRs

# Appendix

*None*

{% endraw %}