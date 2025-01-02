---
layout: default
title: CM102A_FlsMem
nav_order: 1
parent: Component Design
---
{% raw %}
**Flash Memory RH850**

**(FlsMem)**

**FDD CM102A**

[1. High Level Description
[3](#high-level-description)](#high-level-description)

[2. Sub-Function In This Document
[3](#sub-function-in-this-document)](#sub-function-in-this-document)

[3. Critical Register Verification References
[3](#critical-register-verification-references)](#critical-register-verification-references)

[4. Sub-functions [4](#sub-functions)](#sub-functions)

[4.1. Sub-Function: Code Flash Init (FlsMemInit1)
[4](#sub-function-code-flash-init-flsmeminit1)](#sub-function-code-flash-init-flsmeminit1)

[4.2. Sub-Function: Code Flash 2-Bit and Address Parity
[5](#sub-function-code-flash-2-bit-and-address-parity)](#sub-function-code-flash-2-bit-and-address-parity)

[4.3. Sub-Function: Code Flash CRC
[5](#sub-function-code-flash-crc)](#sub-function-code-flash-crc)

[4.3.1. NTCs [5](#ntcs)](#ntcs)

[4.3.2. SAN Linkage [5](#san-linkage)](#san-linkage)

[4.3.3. Description [5](#description)](#description)

[4.3.4. Rationale [5](#rationale)](#rationale)

[4.3.5. Implementation [5](#implementation)](#implementation)

[4.3.6. Reference [10](#reference)](#reference)

[4.3.7. NTC Verification Method (Special Code)
[10](#ntc-verification-method-special-code)](#ntc-verification-method-special-code)

[4.4. Sub-Function: Code Flash Single Bit ECC
[10](#sub-function-code-flash-single-bit-ecc)](#sub-function-code-flash-single-bit-ecc)

[4.4.1. NTCs [10](#ntcs-1)](#ntcs-1)

[4.4.2. SAN Linkage [10](#san-linkage-1)](#san-linkage-1)

[4.4.3. Description [10](#description-1)](#description-1)

[4.4.4. Rationale [10](#rationale-1)](#rationale-1)

[4.4.5. Implementation [11](#implementation-1)](#implementation-1)

[4.4.6. Reference [13](#reference-1)](#reference-1)

[4.4.7. NTC Verification Method (Special Code)
[13](#ntc-verification-method-special-code-1)](#ntc-verification-method-special-code-1)

[5. Revision Record & Change Approval
[14](#revision-record-change-approval)](#revision-record-change-approval)

# High Level Description

This document describes the microcontroller configuration for flash
memory diagnostics for the RH850. It includes ECC, address parity and
CRC confirmations. It also includes logic to look for frequent
corrections on a given address to predict failures.

# Sub-Function In This Document

Below is a linked list of all sub-functions owned by this document.

| **Sub-Function Name**               | **Link**                            |
|----------------------------------------------------|--------------------|
| Code Flash Init                     | [4.1](#_Sub-Function:_Code_Flash)   |
| Code Flash 2-Bit and Address Parity | [4.2](#_Sub-Function:_Code_Flash_1) |
| Code Flash CRC                      | [4.3](#_Sub-Function:_Code_Flash_2) |

# Critical Register Verification References

This table contains the information needed for critical register
verification as configured or used in this document.

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Register</strong></th>
<th><p><strong>Init / Periodic</strong></p>
<p><strong>Verification</strong></p></th>
<th><strong>Masking</strong></th>
<th><strong>Expected Value</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>None – Flash ECC registers will be covered in CM110A</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Sub-functions

## Sub-Function: Code Flash Init (FlsMemInit1)

Return to sub-function list link: <u>Sub-Function In This Document</u>

This is an empty Initialization function that contains no logic.   
FlsMemInit1 is an RTE function which is required for memory mapping PIM
and Calibration definitions

## Sub-Function: Code Flash 2-Bit and Address Parity  

Return to sub-function list link: <u>Sub-Function In This Document</u>

Refer to FDD CM101A_ExcpnHndling for information on 2-Bit code flash ECC
/ Address Parity faults.

## Sub-Function: Code Flash CRC

Return to sub-function list link: <u>Sub-Function In This Document</u>

### NTCs

002.0 Code Flash Single Bit ECC

004.0 Flash Memory Code Flash Crc Fault

### SAN Linkage

| Requirement \# | DOORs Link                                                                                  |
|--------------|----------------------------------------------------------|
| 234            | http://usmisag-ap40.nexteer.com:8080/dwa/rm/urn:rational::1-399d8406295f0f5f-O-234-0000e801 |
| 242            | http://usmisag-ap40.nexteer.com:8080/dwa/rm/urn:rational::1-399d8406295f0f5f-O-242-0000e801 |
| 248            | http://usmisag-ap40.nexteer.com:8080/dwa/rm/urn:rational::1-399d8406295f0f5f-O-248-0000e801 |

### Description

This sub-function handles code flash Crc Check using RH850 Crc Hardware.

### Rationale

32-bit Crc Ethernet algorithm is used considering Crc Hardware supports
max 32-bit width Crc Check.

Crc Check Only tested if ECU is Power On Reset, because In the scenario
of other than Power Reset, it might get into continuous reset loop.

### Implementation

The Code Flash CRC Check shall use **32-Bit CRC / 32-bit Access** width
schema for computing CRC.

The Header per Crc Region shall exclude in Crc Calculation.

Note: The Prescence patterns per Crc Region shall exclude in Crc
Calculation for GM customer.

#### Sub-Function: Code Flash CRC Check Init (FlsMemInit2)

This function will setup the CRC hardware and the DTS Channel
initialize.

In order to setup CRC hardware, first need to reserve one of the CRC
hardware out of 4 the CRC hardware by calling “ResCrcHwUnit” client
call.

Considering current estimation of DTS channels 32 max shall be used, so
0 to 31 the DTS channels are reserved for CRC operation.

DTS channels shall configure dynamically using configurator tool. The
DTS channel shall allow 0xFFFF max block size for data transfer. If the
transfer count is more than 65535, the DTS channel configuration shall
break transfer into multiple the DTS channel(s).

##### Execution

“FlsMemInit2” shall schedule after OS Start – Refer CM100A Start up
sequence.

“DtsInin” function shall run in supervisor mode.

PEG shall need to configure before “FlsMemInit2”.

CrcHw Init shall schedule before “FlsMemInit2”.

##### Software

Refer below pseudo code for implementation.

//Power on Reset

{

ChkForStrtUpTest (&ExecStrtUpTest);  
If (ExecStrtUpTest ) // True Perform the start up test.

> {
>
> // ResvCrcHwUnit is Client call for reserve Crc Hw
>
> CrcHwIdxKey = 0;
>
> Call_ResvCrcHwUnit(CRCHWRESVMOD_RESV, CRCHWRESVCFG_32BITCRC32BITWIDTH,
>
> CrcHwIdxInReg, CrcHwIdxOutReg, 0, CrcHwIdxKey)
>
> if (ResvCrcHwUnit Return == E_OK)
>
> {
>
> //Dynamic DTS channel configuration setup
>
> Call_DTSInit (CrcHwIdxInReg, CrcHwIdxOutReg)
>
> }
>
> //capture the system time and store to PIM
>
> Call\_ GetRefTmr100MicroSec32bit (CodFlsCrcChkStrtTi )
>
> } else
>
> {
>
> PwrOnRstCrcChkCmpl =TRUE;
>
> }

}

DtsInin()

{

> While (Number of Crc Region)
>
> {
>
> Calculate the number of channel(s) per Crc Region required.
>
> // The DTS Channels (Required only), transfer request register should
> Clear prior to configure the rest of the register in the channel

DMASSDTFSCnnn. DRQC = 1

> Configure the DTS channel as per the Refer
> “CM102A_FlsMem_DTSPeripheralCfg.xlsx” for transfer code flash data to
> Crc hardware.
>
> Configure the DTS channel for transfer result to PIM (HwCrcCalcdRes)
>
> Configure the next DTS channel for Crc hardware start clear for next
> operation
>
> }
>
> Configure the last DTS channel in chain for the interrupt, when Crc
> Complete. Interrupt flag shall be monitored in FlsMemPer2 function

Clear the DTS Interrupt flag (“RegOutINTIFPINTCLR0”).

Start DTS Operation (0th DTS Channel start transfer enables).

}

Constant value 0 shall use for clear Hardware Crc (clearing Hardware Crc
output register).

Software Crc Memory table (CodFlsSwCrc ) shall generate using the
configurator tool. It shall contain at least Crc Start Address, Crc
region size and Software Crc Calculated result (SwCrcCalRes) for that
Crc region.

#### Sub-Function: Code Flash CRC Check Periodic (FlsMemPer2)

This function intent to Compare Software Crc calculated Result Vs
Hardware Crc calculated result, perform diagnostic, Milestone Flag
update and release Crc hardware.

The HwCrcCalcdRes shall reside in DTS writable local RAM area.

The Software Crc Calculated Result shall reside in their respective Crc
Region.

After completion of the CRC check, the DTS registers for the source and
destination addresses are re-initialized with the reset value and
transfer request flag if any pending is also cleared to ensure no
unintended transfers happen. The cleanup of the registers should happen
in supervisor mode as the registers are protected by the channel master
settings to be modifiable only in supervisor mode. Hence we make use of
a trusted function to do the cleanup.

##### Execution

FlsMemPer2 shall schedule at 100ms rate.

“DtsClnUp” function shall run in supervisor mode.

##### Software

Refer below pseudo code for implementation.

FlsMemPer2(Void)

{ // Check the Crc Check Complete Status, If complete then don’t execute
logic

if (CrcChkCmpl != TRUE) then

{

// power On Reset flag is true

if (PwrOnRstCrcChkCmpl ==TRUE) then

{ SetNtcSts(NtcNr1.NTCNR_0x004, 0x00, NtcSts1.NTCSTS_PASSD, 0)

CrcChkCmpl = TRUE;

}

else

{

// Check if Crc Complete Interrupt flag set by DTS

if (RegInpINTIFPINT0 != 0) then

{ Call_ResvCrcHwUnit(CRCHWRESVMOD_RELS, 0, 0, 0, 0, CrcHwIdxKey)

for(i=0; i\<Number of Crc Region; i++)

{ if (CodFlsSwCrc\[i\].SwCrcCalRes != HwCrcCalcdRes\[i\]) then

{CrcChkCompFail =\| ((uint8)1U \<\< \[i\]U);

}

}

if (CrcChkCompFail == TRUE) then

{ SetNtcSts(NtcNr1.NTCNR_0x004, CrcChkCompFail,

> NtcSts1.NTCSTS_FAILD, 0);

}

else

{ SetNtcSts(NtcNr1.NTCNR_0x004, 0x00,

NtcSts1.NTCSTS_PASSD, 0)

CrcChkCmpl = TRUE;

}

}

else

{ // If Crc Complete interrupt flag is not set. check Crc Check Allowed

> // time expired

Call\_ GetTiSpan100MicroSec32bit(CodFlsCrcChkStrtTi,

CodFlsCrcElpdTi)

if (CodFlsCrcElpdTi \>= CRCCHKMAXALLWDTI_CNT_U32)

{ Call_ResvCrcHwUnit(CRCHWRESVMOD_RELS, 0, 0, 0, 0,

> CrcHwIdxKey)

SetNtcSts(NtcNr1.NTCNR_0x004, 0xFF,

NtcSts1.NTCSTS_FAILD, 0)

CrcChkCmpl = TRUE;

}

> }

If (CrcChkCmpl)

{

> // Perform the DTS Clean Up – Disable the DTS Channels
>
> // Trusted Function call to DTS cleanup
>
> DtsClnUp ()

}

}

}

> // CodFlsCrcChkCmpl output signal is used for Milepost indicator.

CodFlsCrcChkCmpl = CrcChkCmpl;

}

DtsClnUp()

for(i=0; i\<=31; i++)

{

> // Source Address to 0
>
> // Destination Address to 0
>
> // Clear the DTSFSL transfer request enable bit
>
> // Disable the DTS Channel; DTFSL\[i\].REQEN = 0

}

If (CodFlsSngBitErr == TRUE)

{

SetNtcSts (NtcNr1.NTCNR_0x002, 0x01, NtcSts1.NTCSTS_FAILD, 0);

CodFlsSngBitErr = FALSE;

}

Else

{

SetNtcSts (NtcNr1.NTCNR_0x002, 0x01, NtcSts1.NTCSTS_PASSD, 0);

}

### Reference

RH850 Hardware manual.

### NTC Verification Method (Special Code)

Test Case 1:

Perform the Crc Check see NTC004

Verify NTC004 should indicate pass.

Test Case 2:

Inject Crc Initial start value (Constant Value) 0xFFFF FFFF instead of 0
and calculate Crc.

Verify NTC004 should indicate fail.

> Start value can be change for individual Crc Region for verify each
> failure (depends on Test Scope)

Test Case 3: Time Out Test

Do not configure last DTS Channel Interrupt, which would lead time out
condition check.

Verify NTC004 should indicate fail.

Test Case 4: Power On Reset Condition Test.

PwrOnRstCrcChkCmpl, Flag should be set, when Power On Reset Occur.

Verify NTC004 should indicate pass.

## Sub-Function: Code Flash Single Bit ECC

Return to sub-function list link: <u>Sub-Function In This Document</u>

### NTCs

NA

### SAN Linkage

The error flag **shall** be cleared soon after the error occurrence
**\[SAN-P1x-0707\]**. Otherwise, the error event continues to be active
and the error status is not updated if a second ECC 1-bit error occurs.
In that case an error count overflow will occur.

In case ECC 1-bit error has occurred, a CRC test **\[SAN-P1x-0703\]**
**shall** be executed to check whether or not the error is due single
bit or multi-bit corruption that is potentially caused by address
decoder failure.

### Description

This sub-function does a SW Test to provide greater than 99% coverage on
Code Flash Single Bit ECC Error.

### Rationale

See the document attached.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM102A_FlsMem_Design/Design/mediax/media/image1.wmf)

### Implementation

#### Sub-Function: Code Flash Single Bit ECC Test (CodFlsSngBitEcc)

##### Software

<u>Pseudo code:</u>

SuspendAllInterrupts();

CodFlsSngBitErr = TRUE;

// Clear the Error from ECM Status Register

ECMESSTC1_Desired = 0x0000 0010;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Check for Overflow

If (ECCFLICFOVFSTR_PE1 != 0)

{

// Save Address for debug purpose

CodFlsErrAdr = ECCFLICF1STEADR0_PE1;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CODFLSSNGBITHARDFLT,
> CodFlsErrAdr);

}

// Single Bit ECC Fault

Else If (ECCFLICF1STERSTR_PE1 & 0x0000 0001 !=0)

{

> CodFlsErrAdr *=* ECCFLICF1STEADR0_PE1;
>
> // Read from 4 other locations to make sure it’s not an address
> decoder fault
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE1F));
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE2F));
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE4F));

DummyRead = \*(CodFlsErrAdr & (0xFFFF FE8F));

> // Clear the Error from CF Status Register

ECCFLICFSTCLR_PE1 = 0x0000 0001;

}

Else

{

> // Do Nothing

}

// Check for Overflow

If (ECCFLICFOVFSTR_VCI != 0)

{

// Save Address for debug purpose

CodFlsErrAdr = ECCFLICF1STEADR0_VCI;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CODFLSSNGBITHARDFLT,
> CodFlsErrAdr);

}

// Single Bit ECC Fault

Else If (ECCFLICF1STERSTR_VCI & 0x0000 0001 !=0)

{

> CodFlsErrAdr = ECCFLICF1STEADR0_VCI;
>
> // Read from 4 other locations to make sure it’s not an address
> decoder fault
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE1F));
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE2F));
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE4F));
>
> DummyRead = \*(CodFlsErrAdr & (0xFFFF FE8F));
>
> // Clear the Error from CF Status Register

ECCFLICFSTCLR_VCI = 0x0000 0001;

}

Else

{

> // Do Nothing

}

ResumeAllInterrupts();

### Reference

RH850 Hardware manual.

### NTC Verification Method (Special Code)

NA

# Revision Record & Change Approval

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 10%" />
<col style="width: 13%" />
<col style="width: 8%" />
<col style="width: 60%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Rev</strong></td>
<td><strong>Date</strong></td>
<td><strong>Change Control #</strong></td>
<td><strong>Drw</strong></td>
<td><strong>Change Description</strong></td>
</tr>
<tr class="even">
<td>1.0.0</td>
<td>21OC15</td>
<td>EA4#1829</td>
<td>MK</td>
<td>Initial release for implementation</td>
</tr>
<tr class="odd">
<td>2.0.0</td>
<td>06JAN16</td>
<td>EA4#2942</td>
<td>KP</td>
<td>Crc Check Function added</td>
</tr>
<tr class="even">
<td>2.1.0</td>
<td>15JAN16</td>
<td>EA4#2942</td>
<td>KP</td>
<td>Crc Check – DTS Channel Interrupt On Second Last Channel
Correction</td>
</tr>
<tr class="odd">
<td>2.2.0</td>
<td>15FEB16</td>
<td>EA4#3859</td>
<td>KP</td>
<td>Crc Check for the Startup Test Client Call added in FlsMemInit2</td>
</tr>
<tr class="even">
<td>3.0.0</td>
<td>29MAR16</td>
<td>EA4#5004</td>
<td>KP</td>
<td>DTS Transfer Request Clear prior to configure</td>
</tr>
<tr class="odd">
<td>4.0.0</td>
<td>30MAR16</td>
<td>EA4#4959</td>
<td>KP</td>
<td>Remove 1 Bit ECC &amp; DTS Clean Up Added</td>
</tr>
<tr class="even">
<td>4.0.1</td>
<td>12APR16</td>
<td>EA4#5257</td>
<td>KP</td>
<td>Remove PIM “CodFlsFailrAdr” from m file</td>
</tr>
<tr class="odd">
<td>4.1.0</td>
<td>19APR16</td>
<td>EA4#5421</td>
<td>SK</td>
<td>Added trusted function call DTSCleanup() in 4.3.5.2</td>
</tr>
<tr class="even">
<td>4.2.0</td>
<td>03MAY16</td>
<td>EA4#5619</td>
<td>SK</td>
<td>Disable the DTS Channel at the end of DTSCleanup</td>
</tr>
<tr class="odd">
<td>5.0.0</td>
<td>27JUL16</td>
<td>EA4#6649</td>
<td>SK</td>
<td><p>Added SW Test for Single Bit ECC Correction</p>
<p>DTSCleanup -&gt; DtsClnUp</p>
<p>DTSInit -&gt; DtsInin</p></td>
</tr>
<tr class="even">
<td>5.1.0</td>
<td>31AUG16</td>
<td>EA4#7339</td>
<td>SK</td>
<td>Added logic for Code Flash Single Bit Hard Fault – Overflow
Error</td>
</tr>
</tbody>
</table>

{% endraw %}