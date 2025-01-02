---
layout: default
title: CM800A_SyncCrc_FDD
nav_order: 1
parent: Component Design
---
{% raw %}
**Synchronous Cyclic Redundancy Check**

**FDD \#CM-800A**

[1. High Level Description
[3](#high-level-description)](#high-level-description)

[2. Derived Requirements
[3](#derived-requirements)](#derived-requirements)

[3. Sub-Function Data Flow
[3](#sub-function-data-flow)](#sub-function-data-flow)

[4. Design Rationale [3](#design-rationale)](#design-rationale)

[5. Sub-Functions [4](#sub-functions)](#sub-functions)

[5.1. Management of CRC Hardware Units
[4](#management-of-crc-hardware-units)](#management-of-crc-hardware-units)

[5.1.1. Initialization of Management RAM (SyncCrcInit0)
[5](#initialization-of-management-ram-synccrcinit0)](#initialization-of-management-ram-synccrcinit0)

[5.1.2. RTE Initialization (SyncCrcInit1)
[5](#rte-initialization-synccrcinit1)](#rte-initialization-synccrcinit1)

[5.1.3. Sub-Function: RelsCrcHwUnit
[5](#sub-function-relscrchwunit)](#sub-function-relscrchwunit)

[5.1.4. Sub-Function: GetAvlCrcHwUnit
[6](#sub-function-getavlcrchwunit)](#sub-function-getavlcrchwunit)

[5.1.5. Sub-Function: ResvCrcHwUnit
[7](#sub-function-resvcrchwunit)](#sub-function-resvcrchwunit)

[5.2. SyncCrc API Functions
[9](#synccrc-api-functions)](#synccrc-api-functions)

[5.2.1. Sub-Function: 32-Bit Ethernet CRC
[10](#sub-function-32-bit-ethernet-crc)](#sub-function-32-bit-ethernet-crc)

[5.2.1.1. Hardware Related Design
[10](#hardware-related-design)](#hardware-related-design)

[5.2.1.2. Software Related Design
[10](#software-related-design)](#software-related-design)

[5.2.1.2.1. Calc32BitCrc_u08 [10](#calc32bitcrc_u08)](#calc32bitcrc_u08)

[5.2.1.2.2. Calc32BitCrc_u16 [11](#calc32bitcrc_u16)](#calc32bitcrc_u16)

[5.2.1.2.3. Calc32BitCrc_u32 [11](#calc32bitcrc_u32)](#calc32bitcrc_u32)

[5.2.2. Sub-Function: 16-Bit CRC
[12](#sub-function-16-bit-crc)](#sub-function-16-bit-crc)

[5.2.2.1. Hardware Related Design
[12](#hardware-related-design-1)](#hardware-related-design-1)

[5.2.2.2. Software Related Design
[12](#software-related-design-1)](#software-related-design-1)

[5.2.2.2.1. Calc16BitCrc_u08 [12](#calc16bitcrc_u08)](#calc16bitcrc_u08)

[5.2.2.2.2. Calc16BitCrc_u16 [12](#calc16bitcrc_u16)](#calc16bitcrc_u16)

[5.2.3. Sub-Function: 8-Bit SAE-J1850 CRC
[13](#sub-function-8-bit-sae-j1850-crc)](#sub-function-8-bit-sae-j1850-crc)

[5.2.3.1. Hardware Related Design
[13](#hardware-related-design-2)](#hardware-related-design-2)

[5.2.3.2. Software Related Design
[13](#software-related-design-2)](#software-related-design-2)

[5.2.3.2.1. Calc8BitCrc [13](#calc8bitcrc)](#calc8bitcrc)

[5.2.4. Sub-Function: 8-Bit 0x2F CRC
[14](#sub-function-8-bit-0x2f-crc)](#sub-function-8-bit-0x2f-crc)

[5.2.4.1. Hardware Related Design
[14](#hardware-related-design-3)](#hardware-related-design-3)

[5.2.4.2. Software Related Design
[14](#software-related-design-3)](#software-related-design-3)

[5.2.4.2.1. Calc8BitCrc0X2F [14](#calc8bitcrc0x2f)](#calc8bitcrc0x2f)

[5.3. Sub-Function: AUTOSAR API Wrapper
[15](#sub-function-autosar-api-wrapper)](#sub-function-autosar-api-wrapper)

[5.3.1. Sub-Function: Crc_CalculateCRC32
[15](#sub-function-crc_calculatecrc32)](#sub-function-crc_calculatecrc32)

[5.3.2. Sub-Function: Crc_CalculateCRC16
[15](#sub-function-crc_calculatecrc16)](#sub-function-crc_calculatecrc16)

[5.3.3. Sub-Function: Crc_CalculateCRC8
[15](#sub-function-crc_calculatecrc8)](#sub-function-crc_calculatecrc8)

[5.3.4. Sub-Function: Crc_CalculateCRC8H2F
[15](#sub-function-crc_calculatecrc8h2f)](#sub-function-crc_calculatecrc8h2f)

[6. Timing / Execution Constraints
[16](#timing-execution-constraints)](#timing-execution-constraints)

[6.1. Rationale / Comments
[16](#rationale-comments)](#rationale-comments)

[6.2. Rates and State Execution
[16](#rates-and-state-execution)](#rates-and-state-execution)

[7. Serial Communications Interfaces
[16](#serial-communications-interfaces)](#serial-communications-interfaces)

[8. Additional Information
[16](#additional-information)](#additional-information)

[9. Revision Record & Change Approval
[17](#revision-record-change-approval)](#revision-record-change-approval)

#  High Level Description

This document describes the design of the application programming
interface (API) to allow application software components (SWCs) to
interact with the cyclic redundancy check (CRC) hardware peripheral
included in the microcontroller in EA4 hardware.

# Derived Requirements

N/A

#  Sub-Function Data Flow

The follow block diagram depicts how the data flow inside the
microcontroller CRC peripheral.

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image1.png"
style="width:6in;height:3.52743in" />

#  Design Rationale

The design of the API was intended to meet the AUTOSAR CRC API
definition as closely as possible. This allows the software
configuration to utilize the hardware instead of using software
libraries to save on throughput for software calculations. While the
direct API does not match the AUTOSAR API definitions, wrapper functions
are included to interface with components using the AUTOSAR API with the
SyncCRC API.

# Sub-Functions

## Management of CRC Hardware Units

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_48, CM800A_49, CM800A_50, CM800A_67,
CM800A_68, CM800A_69, CM800A_70, CM800A_81***

The software implementation shall provide a mechanism to utilize one of
the CRC hardware units for a synchronous CRC calculation from a software
component calling one of the API functions. Upon completion of the job,
the software shall release the hardware unit to be available by another
software component. This management shall be implemented by a RAM table
that has holds the task ID and the of the CRC hardware index. No
periodic function is required to manage the RAM since the calculations
are synchronous, released at the end of the API call, or permanently
reserved. Furthermore, each API function will update the RAM after the
job has been completed.

The implementation shall also provide a way to reserve one or more units
to dedicate to a particular function if a program requires. The
reservation shall be done by the pre-compile configuration or by a
function call. The pre-compile configuration shall provide a permanent
reservation of the CRC hardware unit. The reservation shall start from
the highest hardware index. Any hardware CRC unit that is permanently
reserved shall not be used by the SyncCRC API or a temporary reservation
of a hardware CRC unit and should be considered as not enabled or
available.

The function call shall provide a temporary allocation of one of the
available, non-permanently reserved, CRC hardware units. This CRC
hardware unit shall be reserved until the calling function releases it.
The details of this function are described later in this document.

The management shall also provide protection from preemption of higher
priority tasks by utilizing the OS task ID of the calling function as an
authority to use that CRC hardware unit.

An example of the RAM table is shown below. Hardware index 0 is
temporarily reserved. Hardware index 1 is assigned to task ID 2 until
the calculation has completed. Index 2 is available for the next caller.
Hardware index 3 is permanently reserved and not available to software
applications invoking the API, but is be available to a dedicated source
if required by the program.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image2.emf)

###  Initialization of Management RAM (SyncCrcInit0)

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_71, CM800A_50***

The RAM shall be initialized according to the following pseudo code.
This allows the pre-compile configuration to block access to the CRC
hardware units that are not available to the application software
components. In order for this to be effective, the initialization is
required to be scheduled before any software components invoke the API.
This function shall be called from outside of the RTE during “cold
init.”

For each CRC Hardware Unit:

CrcHwSts\[HwUnit\].TaskId = Invalid Task ID

If HwIdx \< Number of Active Hardware Units:

CrcHwSts\[HwUnit\].CrcHwSts = Available

Else:

CrcHwSts\[HwUnit\].CrcHwSts = Crc Not Enabled

End If

End For Loop

### RTE Initialization (SyncCrcInit1)

This function stub is required to properly place the SyncCrc component
within the correct application within a program. This function is called
by the RTE during initialization.

### Sub-Function: RelsCrcHwUnit

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_48***

This sub-function shall be used by the API to release a CRC hardware
unit. This shall be called after the CRC calculation is complete for any
of the API functions calls. The operation of the function shall meet the
following pseudo code.

Function Inputs:

CrcHwIdx := This value represents which hardware index the action should
go against.

Function Outputs:

Void

Function:

CrcHwSts\[CrcHwIdx\].TaskId = Invalid Task ID

CrcHwSts\[CrcHwIdx\].CrcHwSts = Available

### Sub-Function: GetAvlCrcHwUnit

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_48, CM800A_67, CM800A_81***

This sub-function shall be used by the API to allocate a CRC hardware
unit for the caller. This shall be called at the start of any of the CRC
API functions calls. The operation of the function shall meet the
following pseudo code. The ReserveTaskId is a set of four (4) known
values that will be used for the task ID of a hardware unit that is
temporarily reserved.

Function Inputs:

ResvCrcCall := Input to decide if the call is for a Crc unit reservation
or a standard synchronous

calculation.

Function Outputs:

Void

Function:

GetTaskId(TaskId)

EnterExclusiveArea()

For each Active CRC Hardware Unit:

If CrcHwIdxSts == Available:

If ResvCrcCall == False:

> CrcHwSts\[CrcHwIdx\].CrcHwSts = Busy

CrcHwSts\[CrcHwIdx\].TaskId = TaskId

> Else:
>
> CrcHwSts\[CrcHwIdx\].CrcHwSts = Reserve

CrcHwSts\[CrcHwIdx\].TaskId = ReserveTaskId\[CrcHwIdx\]

> End If
>
> Break For Loop

End If

End For Loop

ExitExclusiveArea()

### Sub-Function: ResvCrcHwUnit

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_48, CM800A_67, CM800A_68, CM800A_70***

This function shall allow components to reserve a single hardware unit
to compute a larger CRC utilizing hardware features, such as DMA. The
function shall temporarily reserve the hardware unit until released by
the component. A reservation key will be provided when an index is
reserved. This key will need to be stored in the caller’s RAM as it is
used to determine which hardware index to release when called.

Pseudo code notes:

-   The function CrcRegConfig() is not a function

    -   It represents setting the DCRA register sections ISZ and POL,
        and setting COUT to the StartValue to meet the desired CRC
        calculation as desired by CrcConfg.

-   LoopCrcHwIdxInReg and LoopCrcHwIdxOutReg are the CIN and COUT for
    each of the CRC hardware units.

Function Inputs:

In: Mode := 1= CRCHWRESVMOD_RESV, 0= CRCHWRESVMOD_RELS

In: CrcConfig := See table below

| Enumeration                     | CrcConfig (Enum Value) | DCRAnISZ | DCRAnPOL | Meaning                                          |
|--------------------------|------------|---------|----------|----------------|
| CRCHWRESVCFG_32BITCRC32BITWIDTH | 0                      | 0        | 0        | 32-Bit CRC / 32-Bit Access Width                 |
| CRCHWRESVCFG_32BITCRC16BITWIDTH | 1                      | 0        | 1        | 32-Bit CRC / 16-Bit Access Width                 |
| CRCHWRESVCFG_32BITCRC8BITWIDTH  | 2                      | 0        | 2        | 32-Bit CRC / 8-Bit Access Width                  |
| CRCHWRESVCFG_16BITCRC16BITWIDTH | 3                      | 1        | 1        | 16-Bit CRC / 16-Bit Access Width                 |
| CRCHWRESVCFG_16BITCRC8BITWIDTH  | 4                      | 1        | 2        | 16-Bit CRC / 8-Bit Access Width                  |
| CRCHWRESVCFG_8BITCRC            | 5                      | 2        | 2        | 8-Bit CRC / 8-Bit Access Width (SAE-J 1850)      |
| CRCHWRESVCFG_8BITCRCH2F         | 6                      | 3        | 2        | 8-Bit CRC / 8-Bit Access Width (Polynomial 0x2F) |

Out: CrcHwIdxInReg

Out: CrcHwIdxOutReg

In: StartValue

In/Out: ResvKey

Function Outputs:

Standard Return

-   OK = Successful reservation.

-   NOT_OK = Reservation failed, CRC not configured.

Function:

FuncReturn = NOT_OK

If Mode == Reserve and CrcConfig \< 7:

> For each Active CRC Hardware Unit:
>
> If CrcHwIdxSts == Available:
>
> GetAvlCrcHwUnit(TRUE)
>
> ResvKey = ReserveTaskId\[CrcHwLoopIdx\]
>
> CrcResvd = TRUE
>
> CrcHwIdx = CrcHwLoopIdx
>
> Break For Loop
>
> End If
>
> End For Loop
>
> If (CrcResvd == TRUE):
>
> CrcRegConfig(CrcConfig, StartValue)
>
> CrcHwIdxInReg = Address of Selected Index Input Register
>
> CrcHwIdxOutReg = Address of Selected Output Register
>
> FuncReturn = OK

End If

If(FuncReturn == NOT_OK):

> CrcHwIdxInReg = 0
>
> CrcHwIdxOutReg = 0
>
> ResvKey = 0

End If

Else If Mode == Release:

/\* Release path \*/

> For each Active CRC Hardware Unit:
>
> If ((CrcHwIdxSts == Reserved) and
>
> (ResvKey = CrcHwSts\[CrcHwIdx\].Taskid)):
>
> RelsCrcHwUnit(CrcHwIdx)
>
> FuncReturn = OK
>
> Break For Loop

End If

End For Loop

If(FuncReturn == NOT_OK):

> CrcHwIdxInReg = 0
>
> CrcHwIdxOutReg = 0
>
> ResvKey = 0

End If

Else:

FuncReturn = NOT_OK

CrcHwIdxInReg = 0

CrcHwIdxOutReg = 0

ResvKey = 0

End If

## SyncCrc API Functions

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_64, CM800A_66***

The functions defined in the following sub sections shall follow the
following format and functionally meet the pseudo code.

Function Inputs:

In/Out: DataPtr_Arg†

In: Len_Arg

In: StrtVal_Arg†

In: FirstCall_Arg

In/Out: CalcCrcRes_Arg†

† - Argument data type depends on the API function (choices are 8, 16,
or 32-bit).

Function Outputs:

Standard Return

-   OK = Successful CRC calculation.

-   NOT_OK = CRC Hardware unit could not be reserved, no calculation
    performed. CalcCrcRes_Arg shall be set to 0.

Function:

ErrRtn = OK

GetTaskId(TaskId)

GetAvlCrcHwUnit()

For each Active CRC Hardware Unit:

If TaskId == RAMTable.TaskId:

CrcHwIdx = LoopIdx

Break For Loop

End If

End For Loop

If CrcHwIdx != Invalid CRC Index:

CrcRegConfig() /\* Configure Registers for the function type \*/

If FirstCall_Arg == True:

COUT = Default CRC Init Value

Else:

COUT = StrtVal_Arg

End If

For 0 to Len_Arg:

CIN = DataPtr\[LenIdx\]

End For

CalcCrcRes_Arg = COUT

RelsCrcHwUnit(CrcHwIdx)

Else:

CalcCrcRes_Arg = 0

ErrRtn = NOT_OK

End If

### Sub-Function: 32-Bit Ethernet CRC

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_52, CM800A_64***

The CRC module shall implement the CRC32 routine based on the IEEE-802.3
CRC32 Ethernet Standard. In the event a CRC cannot be calculated the
function shall return a CRC result of 0 and notify the calling software
component that the CRC result was not calculated.

#### Hardware Related Design

N/A

#### Software Related Design

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_53, CM800A_54***

The following table defines the parameters used to define the 32-Bit
Ethernet functions.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr class="header">
<th>CRC Result Width</th>
<th>32 Bits</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Polynomial</td>
<td><p>0x04C11DB7</p>
<p>or</p>
<p>X<sup>32</sup> + X<sup>26</sup> + X<sup>23</sup> + X<sup>22</sup> +
X<sup>16</sup> + X<sup>12</sup> + X<sup>11</sup> + X<sup>10</sup> +
X<sup>8</sup> + X<sup>7</sup> + X<sup>5</sup> + X<sup>4</sup> +
X<sup>2</sup> + X<sup>1</sup> + 1</p>
<p>or</p>
<p><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image3.png"
style="width:4.432in;height:1.24342in" /></p></td>
</tr>
<tr class="even">
<td>Initial Value</td>
<td>0xFFFFFFFF</td>
</tr>
<tr class="odd">
<td>Input Data Width</td>
<td>8-Bit / 16-Bit / 32-Bit</td>
</tr>
<tr class="even">
<td>Input Data Reflected</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>Result Data Reflected</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>XOR Value</td>
<td>0xFFFFFFFF</td>
</tr>
<tr class="odd">
<td>Check</td>
<td>0xCBF43926</td>
</tr>
<tr class="even">
<td>Magic Check</td>
<td>0xDEBB20E3</td>
</tr>
</tbody>
</table>

##### Calc32BitCrc_u08

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_55***

This function shall implement the algorithm defined in Section 5.2.1.2.
The input data shall be accessed in 8-Bit segments. This function shall
be used in place of the AUTOSAR Crc_CalculateCRC32 function and
described in section 5.3.

##### Calc32BitCrc_u16

This function shall implement the algorithm defined in Section 5.2.1.2.
The input data shall be accessed in 16-Bit segments. This requires that
the input data be aligned for 16-Bit access.

##### Calc32BitCrc_u32

This function shall implement the algorithm defined in Section 5.2.1.2.
The input data shall be accessed in 32-Bit segments. This requires that
the input data be aligned for 32-Bit access.

### Sub-Function: 16-Bit CRC

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_56, CM800A_64***

The CRC module shall implement the CRC16 routine based on the CCITT
CRC16 Standard. In the event a CRC cannot be calculated the function
shall return a CRC result of 0 and notify the calling software component
that the CRC result was not calculated.

#### Hardware Related Design

N/A

#### Software Related Design

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_57, CM800A_58***

The following table defines the parameters used to define the 16-Bit
functions.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr class="header">
<th>CRC Result Width</th>
<th>16 Bits</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Polynomial</td>
<td><p>0x1021</p>
<p>or</p>
<p>X<sup>16</sup> + X<sup>12</sup> + X<sup>5</sup> + 1</p>
<p>or</p>
<p><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image4.png"
style="width:4.3209in;height:1.00867in" /></p></td>
</tr>
<tr class="even">
<td>Initial Value</td>
<td>0xFFFF</td>
</tr>
<tr class="odd">
<td>Input Data Width</td>
<td>8-Bit / 16-Bit</td>
</tr>
<tr class="even">
<td>Input Data Reflected</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Result Data Reflected</td>
<td>No</td>
</tr>
<tr class="even">
<td>XOR Value</td>
<td>0x0000</td>
</tr>
<tr class="odd">
<td>Check</td>
<td>0x29B1</td>
</tr>
<tr class="even">
<td>Magic Check</td>
<td>0x0000</td>
</tr>
</tbody>
</table>

##### Calc16BitCrc_u08

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_59***

This function shall implement the algorithm defined in Section 5.2.2.2.
The input data shall be accessed in 8-Bit segments. This function shall
be used in place of the AUTOSAR Crc_CalculateCRC16() function and
described in section 5.3.

##### Calc16BitCrc_u16

This function shall implement the algorithm defined in Section 5.2.2.2.
The input data shall be accessed in 16-Bit segments. This requires that
the input data be aligned for 16-Bit access.

### Sub-Function: 8-Bit SAE-J1850 CRC

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_60, CM800A_64***

The CRC module shall implement the CRC8 routine based on the SAE-J1850
CRC8 Standard. In the event a CRC cannot be calculated the function
shall return a CRC result of 0 and notify the calling software component
that the CRC result was not calculated.

#### Hardware Related Design

N/A

#### Software Related Design

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_61, CM800A_62***

The following table defines the parameters used to define the 8-Bit
functions.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr class="header">
<th>CRC Result Width</th>
<th>8 Bits</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Polynomial</td>
<td><p>0x1D</p>
<p>or</p>
<p>X<sup>8</sup> + X<sup>4</sup> + X<sup>3</sup> + X<sup>2</sup> + 1</p>
<p>or</p>
<p><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image5.png"
style="width:3.88422in;height:1.17854in" /></p></td>
</tr>
<tr class="even">
<td>Initial Value</td>
<td>0xFF</td>
</tr>
<tr class="odd">
<td>Input Data Width</td>
<td>8-Bits</td>
</tr>
<tr class="even">
<td>Input Data Reflected</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Result Data Reflected</td>
<td>No</td>
</tr>
<tr class="even">
<td>XOR Value</td>
<td>0xFF</td>
</tr>
<tr class="odd">
<td>Check</td>
<td>0x4B</td>
</tr>
<tr class="even">
<td>Magic Check</td>
<td>0xC4</td>
</tr>
</tbody>
</table>

##### Calc8BitCrc

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_63***

This function shall implement the algorithm defined in Section 5.2.3.2.
The input data shall be accessed in 8-Bit segments. This function shall
be used in place of the AUTOSAR Crc_CalculateCRC8() function and
described in section 5.3.

### Sub-Function: 8-Bit 0x2F CRC

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_60, CM800A_64***

The CRC module shall implement the CRC8 routine based with a 0x2F
polynomial. In the event a CRC cannot be calculated the function shall
return a CRC result of 0 and notify the calling software component that
the CRC result was not calculated.

#### Hardware Related Design

N/A

#### Software Related Design

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_61, CM800A_62***

The following table defines the parameters used to define the 8-Bit
functions.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr class="header">
<th>CRC Result Width</th>
<th>8 Bits</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Polynomial</td>
<td><p>0x2F</p>
<p>or</p>
<p>X<sup>8</sup> + X<sup>5</sup> + X<sup>3</sup> + X<sup>2</sup> +
X<sup>1</sup> + 1</p>
<p>or</p>
<p><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM800A_SyncCrc_Design/Design/mediax/media/image6.png"
style="width:4.15672in;height:1.11023in" /></p></td>
</tr>
<tr class="even">
<td>Initial Value</td>
<td>0xFF</td>
</tr>
<tr class="odd">
<td>Input Data Width</td>
<td>8-Bit</td>
</tr>
<tr class="even">
<td>Input Data Reflected</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Result Data Reflected</td>
<td>No</td>
</tr>
<tr class="even">
<td>XOR Value</td>
<td>0xFF</td>
</tr>
<tr class="odd">
<td>Check</td>
<td>0xDF</td>
</tr>
<tr class="even">
<td>Magic Check</td>
<td>0x42</td>
</tr>
</tbody>
</table>

##### Calc8BitCrc0X2F

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_63***

This function shall implement the algorithm defined in Section 5.2.4.2.
The input data shall be accessed in 8-Bit segments. This function shall
be used in place of the AUTOSAR Crc_CalculateCRC8H2F() function and
described in section 5.3.

## Sub-Function: AUTOSAR API Wrapper

***\#REQ: The following requirement(s) are met by the design feature
below: Requirement ID: CM800A_51***

The following API wrapper functions shall be to replace the AUTOSAR CRC
API libraries for software CRC calculations. The return value of
OK/NOT_OK from the SyncCrc functions are ignored as AUTOSAR does not
provide this error handling in their requirements.

Function Inputs:

In/Out: DataPtr_Arg

In: Len_Arg

In: StrtVal_Arg†

In: FirstCall_Arg

† - Argument data type depends on the API function (8, 16, or 32-bit).

Function Outputs:

CrcRes†: Result of the CRC calculation.

† - Argument data type depends on the API function.

### Sub-Function: Crc_CalculateCRC32

Function:

Calc32BitCrc_u08_Oper( DataPtr_Arg, Len_Arg, StrtVal_Arg,

FirstCall_Arg, &CrcRes)

Return CrcRes

### Sub-Function: Crc_CalculateCRC16

Function:

Calc16BitCrc_u08_Oper( DataPtr_Arg, Len_Arg, StrtVal_Arg,

FirstCall_Arg, &CrcRes)

Return CrcRes

### Sub-Function: Crc_CalculateCRC8

Function:

Calc8BitCrc_Oper ( DataPtr_Arg, Len_Arg, StrtVal_Arg,

FirstCall_Arg, &CrcRes)

Return CrcRes

### Sub-Function: Crc_CalculateCRC8H2F

Function:

Calc8BitCrc0X2F_Oper ( DataPtr_Arg, Len_Arg, StrtVal_Arg,

FirstCall_Arg, &CrcRes)

Return CrcRes

# Timing / Execution Constraints

## Rationale / Comments

The functions defined in this document are synchronous functions and are
not required to be scheduled to run at a periodic rate.

## Rates and State Execution

| **Sub-Function Name** | **Rate (ms)** | **Cold Init**  | **Warm Init**  | **Operate**    | **Disable**    |
|----------------|---------|------------|------------|------------|------------|
| SyncCrcInit0          | N/A           | Y\*            | Do Not Execute | Do Not Execute | Do Not Execute |
| SyncCrcInit1          | N/A           | Do Not Execute | Y              | Do Not Execute | Do Not Execute |
| Calc32BitCrc_u08      | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc32BitCrc_u16      | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc32BitCrc_u32      | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc16BitCrc_u08      | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc16BitCrc_u16      | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc8BitCrc0X2F       | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Calc8BitCrc           | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Crc_CalculateCRC32    | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Crc_CalculateCRC16    | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Crc_CalculateCRC8     | N/A           | Do Not Execute | N/A            | N/A            | N/A            |
| Crc_CalculateCRC8H2F  | N/A           | Do Not Execute | N/A            | N/A            | N/A            |

Y\* -- No CRC calculations can be performed with this component before
this function is executed.

# Serial Communications Interfaces

N/A

# Additional Information

N/A

#  Revision Record & Change Approval

|          |           |                       |         |                                  |
|--------|----------|----------|-------|--------------------------------------|
| **Rev**  | **Date**  | **Change Control \#** | **Drw** | **Change Description**           |
| 01.00.00 | 12-Jan-16 | EA4#1843              | KJS     | Initial Release of this document |

{% endraw %}