---
layout: default
title: CM103A_RamMem
nav_order: 1
parent: Component Design
---
{% raw %}
**RAM Memory RH850**

**(RamMem)**

**FDD CM103A**

[1. High Level Description 3](#high-level-description)

[2. Sub-Functions In This Document 4](#sub-functions-in-this-document)

[3. Critical Registers 5](#critical-registers)

[4. Sub-functions 6](#sub-functions)

[4.1. Sub-Function: RAM NTCs Initialization
6](#sub-function-ram-ntcs-initialization)

[4.1.1. NTCs 6](#ntcs)

[4.1.2. SAN Linkage 6](#san-linkage)

[4.1.3. Description 6](#description)

[4.1.4. Rationale 7](#rationale)

[4.1.5. Implementation 7](#implementation)

[4.1.6. Reference Registers 7](#reference-registers)

[4.1.7. Verification Method 7](#verification-method)

[4.2. Sub-Function: RAM ECC -2 Bit and Address Parity Faults
7](#sub-function-ram-ecc--2-bit-and-address-parity-faults)

[4.2.1. NTCs 8](#ntcs-1)

[4.2.2. SAN Linkage 8](#san-linkage-1)

[4.2.3. Description 8](#description-1)

[4.2.4. Rationale 8](#rationale-1)

[4.2.5. Implementation 8](#__RefHeading___Toc451438549)

[4.2.6. Reference 10](#reference)

[4.2.7. Verification Method 12](#verification-method-1)

[4.3. Sub-Function: Local RAM ECC - 1 Bit
13](#sub-function-local-ram-ecc---1-bit)

[4.3.1. NTCs 13](#ntcs-2)

[4.3.2. SAN Linkage 13](#san-linkage-2)

[4.3.3. Description 13](#description-2)

[4.3.4. Rationale 13](#rationale-2)

[4.3.5. Implementation 14](#implementation-1)

[4.3.6. Reference Registers 20](#reference-registers-1)

[4.3.7. Verification Method 23](#verification-method-2)

[4.4. Sub-Function: I-Cache ECC & Setting the NTCs
24](#sub-function-i-cache-ecc-setting-the-ntcs)

[4.4.1. NTCs 24](#ntcs-3)

[4.4.2. SAN Linkage 24](#san-linkage-3)

[4.4.3. Description 25](#description-3)

[4.4.4. Rationale 25](#rationale-3)

[4.4.5. Implementation 26](#implementation-2)

[4.4.6. Reference Registers 33](#reference-registers-2)

[4.4.7. Verification Method 37](#verification-method-3)

[5. Revision Record & Change Approval
38](#revision-record-change-approval)

# High Level Description

This document describes the diagnostics configuration for all RAM memory
in the RH850 based design. RAM initialization is also included in this
document.

**Local RAM:**

PE1 is capable of simultaneously writing or reading up to 128 bits of
data at a time to or from the local RAM. Meanwhile, ECC bits are
provided for each 32 bits of data and the locations for storage of each
32-bit data segment are referred to as banks 0 to 3.

-   ECC error detection and correction are carried out (2-bit error
    detection and 1-bit error detection and correction are carried out)

A status register is provided, which indicates the status of 2-bit ECC
error detection and 1- bit ECC error detection. If an error occurs while
no error status is set, the corresponding status is set. The error
status can be cleared using the clear register.

**Instruction Cache RAM:**

ECC error detection and correction can be either enabled or disabled.

When enabled, either of the following settings can be selected.

-   For instruction cache (data), ECC error detection and correction are
    carried out (2- bit error detection and 1-bit error detection and
    correction) or ECC error detection is carried out (2-bit error
    detection and 1-bit error detection).

-   For instruction cache (TAG), ECC error detection is carried out
    (2-bit error detection and 1-bit error detection and correction).

Upon occurrence of an ECC error, it is notified to the error control
module.

-   Error notification can be either enabled or disabled upon detection
    of a 2-bit ECC error.

-   Error notification can be either enabled or disabled upon detection
    of a 1-bit ECC error.

A status register is provided, which indicates the statuses of 2-bit ECC
error detection and 1-bit ECC error detection. If an error occurs while
no error status is set, the corresponding status is set. The error
status can be cleared using the clear register.

**Peripheral RAM:**

This is an ECC module for the RAM of the following peripheral modules:

RS-CAN, FlexRay, CSIHn (n = 0 to 3)

Seven-bit ECC data is appended to the 32-bit RAM data.

This ECC circuit provides 2-bit ECC error detection and 1-bit ECC error
detection and correction.

Enabling or disabling ECC error detection and correction

-   ECC error detection can be either enabled or disabled.

-   One-bit ECC error correction can be either enabled or disabled.

-   If all the bits of RAM output data are stuck to 0 or 1, it is
    detected as a 2-bit ECC error.

Error notification

-   Error notification is made to the ECM upon detection of a 2-bit ECC
    error (notification can be either enabled or disabled).

-   Error notification is made to the ECM upon detection of a 1-bit ECC
    error (notification can be either enabled or disabled).

Once an error is notified to the ECM, another error notification is not
made until the corresponding error status flag is cleared even if
another ECC error is detected. Special registers are provided to clear
error status.

# Sub-Functions In This Document

Below is a linked list of all sub-functions owned by this document.

|                                         |                                   |
|----------------------------------------------------|--------------------|
| **Sub-Function Name**                   | **Link**                          |
| RAM Register Configuration              | 4.1                               |
| RAM ECC 2-Bit and Address Parity Faults | 4.2                               |
| Local RAM 1-Bit ECC and Data Parity     | 4.3                               |
| Peripheral RAM Single Bit ECC           | Error: Reference source not found |
| I-Cache                                 | 4.4                               |

# Critical Registers

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 17%" />
<col style="width: 13%" />
<col style="width: 9%" />
<col style="width: 15%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Register</strong></td>
<td><p><strong>Register No.</strong></p>
<p><strong>(regID, selID)</strong></p></td>
<td><strong>Access Permission</strong></td>
<td><p><strong>Init/Periodic</strong></p>
<p><strong>Verification</strong></p></td>
<td><strong>Masking</strong></td>
<td><strong>Expected Value</strong></td>
<td><p><strong>Protn Score From</strong></p>
<p><strong>Eval Sheet</strong></p></td>
</tr>
<tr class="even">
<td>LRSTCLR_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="odd">
<td>LROVFSTR_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="even">
<td>LR1STERSTR_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="odd">
<td>LR1STEADR0_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="even">
<td>LR1STEADR1_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="odd">
<td>LR1STEADR2_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="even">
<td>LR1STEADR3_PE1</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>2</td>
</tr>
<tr class="odd">
<td>ECCCSIH0CTL</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0018</td>
<td>1</td>
</tr>
<tr class="even">
<td>ECCCSIH1CTL</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0018</td>
<td>1</td>
</tr>
<tr class="odd">
<td>ECCCSIH2CTL</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0018</td>
<td>1</td>
</tr>
<tr class="even">
<td>ECCCSIH3CTL</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0018</td>
<td>1</td>
</tr>
<tr class="odd">
<td>ECCCSIH0EAD0</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>1</td>
</tr>
<tr class="even">
<td>ECCCSIH1EAD0</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>1</td>
</tr>
<tr class="odd">
<td>ECCCSIH2EAD0</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>1</td>
</tr>
<tr class="even">
<td>ECCCSIH3EAD0</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>1</td>
</tr>
<tr class="odd">
<td>ECCRCAN0CTL</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0018</td>
<td>1</td>
</tr>
<tr class="even">
<td>ECCRCAN0EAD0</td>
<td>Memory Mapped</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x0000 0000</td>
<td>1</td>
</tr>
</tbody>
</table>

# Sub-functions

## Sub-Function: RAM NTCs Initialization

Return to sub-function list link: Sub-Functions In This Document

### NTCs

012.0: Local RAM ECC – Single Bit Correction (Soft Fault)

012.2: I-Cache ECC Error Detection (Cache Miss)

012.4: CAN RAM ECC Single Bit Correction (Soft Fault)

012.6: CSIH0-3 RAM ECC Single Bit Correction (Soft Fault)

017.1: CSIH0 RAM ECC Double Bit (Hard Fault)

018.1: CSIH1 RAM ECC Double Bit (Hard Fault)

019.1: CSIH 2 RAM ECC Double Bit (Hard Fault)

01A.1: CSIH 3 RAM ECC Double Bit (Hard Fault)

01B.2: CAN RAM ECC Double Bit Fault

01D.1: Flexray Message RAM ECC Double Bit Fault

01D.3: Flexray Buffer A RAM ECC Double Bit Fault

01D.5: Flexray Buffer B RAM ECC Double Bit Fault

### SAN Linkage

N/A

### Description

This RTE Initialization function sets all the NTCs to Passed State.

### Rationale

N/A

### Implementation

N/A

#### Initialization (RamMemInit1)

<u>Psuedo Code:</u>

SpiErrChFlg = 255;

// Set NTC 012 to Passed

SetNtcSts (0x012, 0x00, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 017 to Passed

SetNtcSts (0x017, 0x02, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 018 to Passed

SetNtcSts (0x018, 0x02, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 019 to Passed

SetNtcSts (0x019, 0x02, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 01A to Passed

SetNtcSts (0x01A, 0x02, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 01B to Passed

SetNtcSts (0x01B, 0x00, NtcSts1.NTCSTS_PASSD, 0);

// Set NTC 01D to Passed

SetNtcSts (0x01D, 0x00, NtcSts1.NTCSTS_PASSD, 0);

### Reference Registers

N/A

### Verification Method

N/A

## Sub-Function: RAM ECC -2 Bit and Address Parity Faults

Return to sub-function list link: Sub-Functions In This Document

Refer to FDD CM101A_ExcpnHndlg for information on RAM double bit
failures (local RAM and DTS RAM) and Address Parity Failures.

### NTCs

N/A

### SAN Linkage

None

### Description

N/A

### Rationale

N/A

#### Event Driven

N/A

### Reference

N/A

### Verification Method

NA

## Sub-Function: Local RAM ECC - 1 Bit

Return to sub-function list link: Sub-Functions In This Document

### NTCs

N/A

### SAN Linkage

**SAN-402 – 406**

In case 1-bit corruption is flagged by the ECC logic, a SW test
**shall** be executed to check if the error was due to:

1.  Transient failure of one of the logical word corresponding cell

2.  Permanent failure of one of the logical word corresponding cell

3.  Multiple bits (\> 2bits) corruption

4.  An address failure

**SAN-407**

In case of a) the operation **can** be continued. In the unlikely event
that the corruption is confirmed (permanent fault) and the related data
is not duplicated in other locations, it is up to the user whether or
not to move to the safe state or to tolerate the error.

**SAN-408**

In case c) and d) transition to the MCU and the system into the safe
state **shall** be done. Unless, the data is duplicated in two different
locations

**SAN-409**

Whenever an ECC error has occurred, it **should** be handled and the
corresponding flag should be cleared by means of LRSTCLR register.

### Description

This sub-function is called by the MCU handler and addresses single bit
ECC / data parity issues. It is also responsible for confirming if the
single bit error is “real” as based on the hardware, multiple failures
could present as single bit faults when they are not. In this instance,
a flag is set and the NTC is monitored in a periodic function.

### Rationale

Design sets a flag within the exception for triggering of NTCs in a
periodic function as NTC setting is not allowed in an exception
(architecture requirement).

Design assumes that 1 bit ECC Error detection and correction has been
enabled and hence we do not perform software reset on multiple single
bit ECC Errors in the same word line addresses.

NxtrSwRstFromExcpn function is designed to clear the ECM bits that
triggered the interrupt and hence the ECC bits corresponding to Local
RAM 1-bit failure in the ECM register will not be cleared in the
periodic tasks.

R7F701311 has 128KB of RAM with a Base address of 0xFEB8 0000 and the
Offset starting at 0x0006 0000. Based on this data, we check if the
address that we read from the Error Address register has a valid offset
address. If not, we log a fault and drive software reset since we could
be accessing invalid RAM addresses.

When doing RAM failure mode classification check, we loop through all 8
address locations to read them and we clear any single bit ECC faults if
they occurred during the 8 reads. In this small window, there is a
chance that DMA can make an access to local RAM and set a single bit ECC
fault which can be misinterpreted as a single bit ECC fault from reading
the 8 addresses. Also, we have setup the local RAM double bit ECC fault
to be configured as a SYSERR. In the event a double bit error occurs
while reading the 8 addresses a SYSERR will take us to safe state, hence
there is no explicit check for the double bit ECC fault.

### Implementation

Applicable Registers’ Information:

<table style="width:100%;">
<colgroup>
<col style="width: 19%" />
<col style="width: 59%" />
<col style="width: 9%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td rowspan="2"><strong>Register</strong></td>
<td rowspan="2"><strong>Use</strong></td>
<td colspan="2"><strong>Access</strong></td>
</tr>
<tr class="even">
<td><strong>SV</strong></td>
<td><strong>UM</strong></td>
</tr>
<tr class="odd">
<td>LRSTCLR_PE1</td>
<td>Used in the design to clear error information in the register
LR1STERSTR_PE1</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>LROVFSTR_PE1</td>
<td>Used in design to indicate address location of error</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="odd">
<td>LR1STERSTR_PE1</td>
<td>Used in design to indicate RAM bank (to identify which register to
read for LR1STEADRn_PE1) and identify failure type</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td><p>LR1STEADRn_PE1</p>
<p>n = 0,1,2,3</p></td>
<td>Multiple registers, one for each bank. Contains the address of the
memory having the issue.</td>
<td>R/W</td>
<td>R/W</td>
</tr>
</tbody>
</table>

#### Event (RamMemLclRamSngBitEcc)

**// From EIINT Handler in MCU**

// Disable all the EI Interrupts

SuspendAllInterrupts ();

// Identify responsible bank – Check for Bank 0

If ((ECCCPU1ERROVF0 == 1)

{

// Check if the saved address in the valid range

LclRamFailrAdr = (ECCCPU1LR1STEADR0_PE1 \<\< 4);

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

ElseIf (ECCCPU1SEDF0 == 1)

{

// Save Failure Address

LclRamFailrAdr = (ECCCPU1LR1STEADR0_PE1 \<\< 4);

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// No overflow

// Clear RAM Bank 0 error info only

ECCCPU1STCLR0 = 1;

// Clears the following

// 1) LROVFSTR_PE1.ERROVF0 (overflow flag)

// 2) LR1STERSTR_PE1.SEDF0 (error status flag)

// 3) LR1STEADR0_PE1 (error address)

// Check for multibit errors or address errors disguised as single bit

RamFailrModClassnChk (LclRamFailrAdr, 0x0000 0001, 0x0000 0001);

}

// Identify responsible bank – Check for Bank 1

If ((ECCCPU1ERROVF1 == 1)

{

// Check if the saved address in the valid range

LclRamFailrAdr = (ECCCPU1LR1STEADR1_PE1 \<\< 4) \| 0x04;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

ElseIf (ECCCPU1SEDF1 == 1)

{

// Save Failure Address

LclRamFailrAdr = (ECCCPU1LR1STEADR1_PE1 \<\< 4) \| 0x04;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// No overflow

// Clear RAM Bank 1 error info only

ECCCPU1STCLR1 = 1;

// Clears the following

// 1) LROVFSTR_PE1.ERROVF1 (overflow flag)

// 2) LR1STERSTR_PE1.SEDF1 (error status flag)

// 3) LR1STEADR1_PE1 (error address)

// Check for multibit errors or address errors disguised as single bit

RamFailrModClassnChk (LclRamFailrAdr, 0x0000 0002, 0x0000 0100);

}

// Identify responsible bank – Check for Bank 2

If ((ECCCPU1ERROVF2 == 1) Then

{

// Check if the saved address in the valid range

LclRamFailrAdr = (ECCCPU1LR1STEADR2_PE1 \<\< 4) \| 0x08;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

ElseIf (ECCCPU1SEDF2 == 1)

{

// Save Failure Address

LclRamFailrAdr = (ECCCPU1LR1STEADR2_PE1 \<\< 4) \| 0x08;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// No overflow

// Clear RAM Bank 2 error info only

ECCCPU1STCLR2 = 1;

// Clears the following

// 1) LROVFSTR_PE1.ERROVF2 (overflow flag)

// 2) LR1STERSTR_PE1.SEDF2 (error status flag)

// 3) LR1STEADR2_PE1 (error address)

// Check for multibit errors or address errors disguised as single bit

RamFailrModClassnChk (LclRamFailrAdr, 0x0000 0004, 0x0001 0000);

}

// Identify responsible bank – Check for Bank 3

If ((ECCCPU1ERROVF3 == 1)

{

// Check if the saved address in the valid range

LclRamFailrAdr = (ECCCPU1LR1STEADR3_PE1 \<\< 4) \| 0x0C;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// Overflow detected

// API Call for Software Reset

> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

ElseIf (ECCCPU1SEDF3 == 1)

{

// Save Failure Address

LclRamFailrAdr = (ECCCPU1LR1STEADR3_PE1 \<\< 4) \| 0x0C;

If (LclRamFailrAdr & 0xFFFE 0000 != 0x0006 0000)

{

> // Invalid Address Found
>
> // API Call for Software Reset
>
> NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_LCLRAMECCSNGBITHARDFAILR,
> LclRamFailrAdr)

}

// Get the valid RAM address by OR-ing the Base address with the Offset

LclRamFailrAdr = LclRamFailrAdr \| 0xFEB8 0000;

// No overflow

// Clear RAM Bank 3 error info only

ECCCPU1STCLR3 = 1;

// Clears the following

// 1) LROVFSTR_PE1.ERROVF3 (overflow flag)

// 2) LR1STERSTR_PE1.SEDF3 (error status flag)

// 3) LR1STEADR3_PE1 (error address)

// Check for multibit errors or address errors disguised as single bit

RamFailrModClassnChk (LclRamFailrAdr, 0x0000 0008, 0x0100 0000);

}

RamFailrModClassnChk (LclRamFailrAdr, ClrErrInfo, SngBitErrMask)

{

WordLineAdr = LclRamFailrAdr & 0xFFFF FF1F;

WordLineAdrIdx_u08 = 0;

LclRamEccSngBitSoftFailr = TRUE;

While (WordLineAdrIdx_u08 \< 8)

{

// Implementation must ensure all 8 reads happen

LclRamWordLineRead = \*WordLineAdr;

> WordLineAdrIdx_u08++;
>
> WordLineAdr = WordLineAdr + 0x0000 0020;

}

// Wait until read from the RAM word line is complete

\_\_asm ("SYNCM");

// Clear Bank Specific Error Info

ECCCPU1LRSTCLR_PE1 = ClrErrInfo;

// Clears the following in Bank Specific RAM Status Register

// 1) Overflow flag

// 2) Error status flag

// 3) Error address

// Single Bit faults detected, Single Bit Soft Fault Flag is already set

}

// Re-enable all the disabled EI Interrupts

ResumeAllInterrupts ();

### Reference Registers

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image1.png"
style="width:5.99861in;height:5.89236in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image2.png"
style="width:5.99931in;height:6.07986in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image3.png"
style="width:5.99583in;height:5.80972in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image4.png"
style="width:5.99306in;height:5.575in" />

### Verification Method

N/A

## Sub-Function: I-Cache ECC & Setting the NTCs

Return to sub-function list link: Sub-Functions In This Document

### NTCs

012.0: Local RAM ECC – Single Bit Correction (Soft Fault)

012.2: I-Cache ECC Error Detection

012.4: CAN RAM ECC Single Bit Correction (Soft Fault)

012.6: CSIH0-3 RAM ECC Single Bit Correction (Soft Fault)

017.1: CSIH0 RAM ECC Double Bit (Hard Fault)

018.1: CSIH1 RAM ECC Double Bit (Hard Fault)

019.1: CSIH2 RAM ECC Double Bit (Hard Fault)

01A.1: CSIH3 RAM ECC Double Bit (Hard Fault)

01B.1: CAN RAM ECC Double Bit Fault

01D.1: Flexray Message RAM ECC Double Bit Fault

01D.3: Flexray Buffer A RAM ECC Double Bit Fault

01D.5: Flexray Buffer B RAM ECC Double Bit Fault

### SAN Linkage

**SAN528:**

The ECC error detection and the notification to the ECM **should** not
be disabled.

**SAN 871:**

The detection of all error types and the status interrupt for each RSCAN
module should be enabled. Whether or not to execute a loop back for
safety purposes depends on the implemented system level safety measures
and should be decided by the user.

**SAN 507 - 508:**

Whenever an ECC occurs, the corresponding flags shall be cleared by
means of IDSTCLR_PE1 and ITSTCLR_PE1 register. Otherwise, the error
event remains active and the error status will not be updated. The ECC
check of the instruction cache data read out from tag or data RAM is
automatically enabled.

**SAN 509:**

Up on detection of a 1-bit/2-bit ECC error, the corresponding flag will
be set in the error status register and the original data will be
reloaded from the Code Flash (treated as cache miss). This behavior may
lead to performance loss. The critical performance loss can be detected
by timeout monitoring. In the case of the critical performance loss, the
MCU shall be moved into the safe state.

### Description

This function is called by the MCU handler and addresses ECC problems
with the peripheral RAM (for the Nexteer design this includes four SPI
channels and two CAN channels).

This function also includes an action when a CAN RAM ECC double bit
fault error occurs.

Added content… DTS single bit, FR, Cntr

ECM status registers are periodically polled looking for an I-Cache ECC
problem. In the event of an I-Cache Error, the respective NTC is set in
a periodic and the Error Status Register is cleared.

This sub function reads all the Flags related to Single Bit ECC fault
from Local RAM, CSIH RAM and CAN RAM (Singe Bit and Double Bit ECC
faults) and takes the following actions

-   Setting an NTC if required in a periodic task

-   Clearing the respective ECM Status Register bit

Registers in use:

|                                                                      |                                                                                                                                                                                           |            |        |
|--------------------|----------------------------------|---------|---------|
| **Register**                                                         | **Use**                                                                                                                                                                                   | **Access** |        |
|                                                                      |                                                                                                                                                                                           | **SV**     | **UM** |
| IDSTCLR_PE1 (Instruction Cache Data RAM Error Status Clear Register) | IDSTCLR clears the error flags in the error status register (ID1STERSTR), the overflow flag in the error overflow status register (IDOVFSTR), and the error address register (ID1STEADR). | R/W        | R/W    |
| ITSTCLR_PE1 (Instruction Cache Tag RAM Error Status Clear Register)  | ITSTCLR clears the error flags in the error status register (IT1STERSTR), the overflow flag in the error overflow status register (ITOVFSTR), and the error address register (IT1STEADR). | R/W        | R/W    |

### Rationale

No startup tests are required as the ECC circuit of the peripheral
modules is target of LBIST and the associated RAMs are target of the
M-BIST as mentioned in the **SAN 530**.

CAN RAM single bit and double bit ECC, Flexray single bit and double bit
ECC, SPI RAM single bit and double bit ECC are all polled in the
periodic as a step towards reducing throughput impact (in case of a
single bit memory failure).

SPI use in the design applies to several critical functions that may
have redundant data sources (motor position, gate drive and power supply
control).

SPI has four channels and all four channel errors are routed to a single
bit in the ECM error source. To provide flexibility, each of these SPI
channels are associated with a unique NTC which can be configured to be
an F1 or F3 fault depending on their use case.

Since the I-Cache is configured to reload from flash with a problem
(cache misses) there is no need to take action other than notifying via
a trouble code and clearing the Error Flags in the Error Status
Register.

This design sets NTCs in a periodic function as NTC setting is not
allowed in an exception due to design constraints of the Diagnostic
Manager getting interrupted in the middle of an NTC (architecture
requirement).

When we read from a corrupted address in Peripheral RAM, ECEMF bit is
set. The ECEMF bit self clears when uncorrupted data is read from
Peripheral RAM. In order to clear the ECER2F or ECER1F bit, according to
the Hardware Manual, it is necessary that the ECEMF bit is ‘0’,
otherwise a write to ECER1C or ECER2C would not clear the ECER1F or
ECER2F bits respectively. Therefore, an attempt to clear to error status
flag is done in the periodic assuming that an uncorrupted read from the
Peripheral RAM would have occurred.

### Implementation

Applicable Registers

|                                                         |                                            |                                                        |            |        |
|----------------|-------------------------|-------------------|-------|-------|
| **Register**                                            | **Use**                                    | **Comments**                                           | **Access** |        |
|                                                         |                                            |                                                        | **SV**     | **UM** |
| ECCCSIHnCTL (SPI 3 Peripheral RAM ECC Control Register) | ECCCSIHnCTL.ECSEDF0                        | When set, indicates 1 bit error found at address EAD0  | R/W        | R/W    |
|                                                         | ECCCSIHnCTL.ECER1C                         | When set, will clear ECER1F bit                        | R/W        | R/W    |
|                                                         | ECCCSIHnCTL.ECER1F                         | When set, indicates a 1 bit error occurred             | R/W        | R/W    |
|                                                         | ECCCSIHnCTL.ECEMF                          | When set, indicates the RAM output data has bit errors | R/W        | R/W    |
| ECCCSIH0EAD0                                            | Address of ECC error – SPI 0               |                                                        | R/W        | R/W    |
| ECCCSIH1EAD0                                            | Address of ECC error – SPI 1               |                                                        | R/W        | R/W    |
| ECCCSIH2EAD0                                            | Address of ECC error – SPI 2               |                                                        | R/W        | R/W    |
| ECCCSIH3EAD0                                            | Address of ECC error – SPI 3               |                                                        | R/W        | R/W    |
| ECCRCAN0CTL (CAN Peripheral RAM ECC Control)            | ECCRCAN0CTL.ECSEDF0                        | When set, indicates 1 bit error found at address EAD0  | R/W        | R/W    |
|                                                         | ECCRCAN0CTL.ECER1C                         | When set, will clear ECER1F bit                        | R/W        | R/W    |
|                                                         | ECCRCAN0CTL.ECER1F                         | When set, indicates a 1 bit error occurred             | R/W        | R/W    |
|                                                         | ECCRCAN0CTL.ECEMF                          | When set, indicates the RAM output data has bit errors | R/W        | R/W    |
| ECCRCAN0EAD0                                            | Address of ECC error – CAN                 |                                                        | R/W        | R/W    |
| ECCFLX0CTL                                              | ECCFLX0CTL.ECSEDF0                         | When set, indicates 1 bit error found at address EAD0  | R/W        | R/W    |
|                                                         | ECCFLX0CTL.ECER1C                          | When set, will clear ECER1F bit                        | R/W        | R/W    |
|                                                         | ECCFLX0CTL.ECER1F                          | When set, indicates a 1 bit error occurred             | R/W        | R/W    |
|                                                         | ECCFLX0CTL.ECEMF                           | When set, indicates the RAM output data has bit errors | R/W        | R/W    |
| ECCFLX0EAD0                                             | Address of ECC error – FlexRay             |                                                        |            |        |
| ECCFLX0T1CTL                                            | ECCFLX0T1CTL.ECSEDF0                       | When set, indicates 1 bit error found at address EAD0  | R/W        | R/W    |
|                                                         | ECCFLX0T1CTL.ECER1C                        | When set, will clear ECER1F bit                        | R/W        | R/W    |
|                                                         | ECCFLX0T1CTL.ECER1F                        | When set, indicates a 1 bit error occurred             | R/W        | R/W    |
|                                                         | ECCFLX0T1CTL.ECEMF                         | When set, indicates the RAM output data has bit errors | R/W        | R/W    |
| ECCFLX0T1EAD0                                           | Address of ECC error – FlexRay             |                                                        |            |        |
| ECCFLX0T0CTL                                            | ECCFLX0T0CTL.ECSEDF0                       | When set, indicates 1 bit error found at address EAD0  | R/W        | R/W    |
|                                                         | ECCFLX0T0CTL.ECER1C                        | When set, will clear ECER1F bit                        | R/W        | R/W    |
|                                                         | ECCFLX0T0CTL.ECER1F                        | When set, indicates a 1 bit error occurred             | R/W        | R/W    |
|                                                         | ECCFLX0T0CTL.ECEMF                         | When set, indicates the RAM output data has bit errors | R/W        | R/W    |
| ECCFLX0T0EAD0                                           | Address of ECC error – FlexRay             |                                                        |            |        |
| ECCCSIH0CTL (ECC Control / Status Register for SPI 0)   | Indicates a SPI double bit error in SPI 0  |                                                        | R/W        | R/W    |
| ECCCSIH1CTL (ECC Control / Status Register for SPI 1)   | Indicates a SPI double bit error in SPI 1  |                                                        | R/W        | R/W    |
| ECCCSIH2CTL (ECC Control / Status Register for SPI 2)   | Indicates a SPI double bit error in SPI 2. |                                                        | R/W        | R/W    |
| ECCCSIH3CTL (ECC Control / Status Register for SPI 2)   | Indicates a SPI double bit error in SPI 3. |                                                        | R/W        | R/W    |

#### Periodic - 2ms (RamMemPer1)

<u>Pseudo Code:</u>

// SPI Single bit failures

If ((ECCCSIH0CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemSpiRamEccErrAdr = ECCCSIH0EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCCSIH0CTL = 0x0000 0200;

// Set NTC 012.6 to Failed

SetNtcSts (0x012, 0x40, NtcSts1.NTCSTS_FAILD, 0) ;

}

Else If ((ECCCSIH1CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemSpiRamEccErrAdr = ECCCSIH1EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCCSIH1CTL = 0x0000 0200;

// Set NTC 012.6 to Failed

SetNtcSts (0x012, 0x40, NtcSts1.NTCSTS_FAILD, 0) ;

}

Else If ((ECCCSIH2CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemSpiRamEccErrAdr = ECCCSIH2EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCCSIH2CTL = 0x0000 0200;

// Set NTC 012.6 to Failed

SetNtcSts (0x012, 0x40, NtcSts1.NTCSTS_FAILD, 0) ;

}

Else If ((ECCCSIH3CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemSpiRamEccErrAdr = ECCCSIH3EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCCSIH13CTL = 0x0000 0200;

// Set NTC 012.6 to Failed

SetNtcSts (0x012, 0x40, NtcSts1.NTCSTS_FAILD, 0) ;

}

Else

{

// Do Nothing

}

// SPI 0 ECC Double Bit Fault

If (ECCCSIH0CTL & 0x0002 0004 != 0)

{

SetNtcSts (0x017, 0x02, NtcSts1.NTCSTS_FAILD, 0)

// Stores address information for debug

dRamMemSpi0RamEccErrAdr = ECCCSIH0EAD0;

// Clear error flags by setting the ECMCLSSE018 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0004 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCCSIH0CTL = 0x0000 0400;

}

// SPI 1 ECC Double Bit Fault

If (ECCCSIH1CTL & 0x0002 0004 != 0)

{

SetNtcSts (0x018, 0x02, NtcSts1.NTCSTS_FAILD, 0)

// Stores address information for debug

dRamMemSpi1RamEccErrAdr = ECCCSIH1EAD0;

// Clear error flags by setting the ECMCLSSE018 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0004 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCCSIH1CTL = 0x0000 0400;

}

// SPI 2 ECC Double Bit Fault

If (ECCCSIH2CTL & 0x0002 0004 != 0)

{

SetNtcSts (0x019, 0x02, NtcSts1.NTCSTS_FAILD, 0)

// Stores address information for debug

dRamMemSpi2RamEccErrAdr = ECCCSIH2EAD0;

// Clear error flags by setting the ECMCLSSE018 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0004 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCCSIH2CTL = 0x0000 0400;

}

// SPI 3 ECC Double Bit Fault

If (ECCCSIH3CTL & 0x0002 0004 != 0)

{

SetNtcSts (0x01A, 0x02, NtcSts1.NTCSTS_FAILD, 0)

// Stores address information for debug

dRamMemSpi3RamEccErrAdr = ECCCSIH3EAD0;

// Clear error flags by setting the ECMCLSSE018 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0004 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCCSIH3CTL = 0x0000 0400;

}

// Check if a CAN RAM single bit ECC error was detected

If ((ECCRCAN0CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemCanRamSngBitEccErrAdr = ECCRCAN0EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCRCAN0CTL = 0x0000 0200;

// Set NTC 012.4 to Failed

SetNtcSts (0x012, 0x10, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a CAN RAM double bit ECC error was detected

If ((ECCRCAN0CTL & 0x0002 0004) != 0)

{

> // Stores address information for debug
>
> dRamMemCanRamDblBitEccErrAdr = ECCRCAN0EAD0;

// Clear error flags by setting the ECMCLSSE017 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0008 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCRCAN0CTL = 0x0000 0400;

// Set NTC 01B.1 to Failed

SetNtcSts (0x01B, 0x02, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a FlexRay RAM single bit ECC error was detected

If ((ECCFLX0CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemFrRamSngBitEccErrAdr = ECCFLX0EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCFLX0CTL = 0x0000 0200;

// Set NTC 012.5 to Failed

SetNtcSts (0x012, 0x20, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a FlexRay Temporary buffer (TBF B) RAM single bit ECC error
was detected

Else If ((ECCFLX0T0CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemFrRamSngBitEccErrAdr = ECCFLX0T0EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCFLX0T0CTL = 0x0000 0200;

// Set NTC 012.5 to Failed

SetNtcSts (0x012, 0x20, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a FlexRay Temporary buffer (TBF A) RAM single bit ECC error
was detected

Else If ((ECCFLX0T1CTL & 0x0001 0002) != 0)

{

// Stores address information for debug

dRamMemFrRamSngBitEccErrAdr = ECCFLX0T1EAD0;

// Clear error flags by setting the ECMCLSSE107 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0080;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

ECCFLX0T1CTL = 0x0000 0200;

// Set NTC 012.5 to Failed

SetNtcSts (0x012, 0x20, NtcSts1.NTCSTS_FAILD, 0);

}

Else

{

> // Do Nothing

}

// Check if a FlexRay RAM double bit ECC error was detected

If ((ECCFLX0CTL & 0x0002 0004) != 0)

{

> // Stores address information for debug
>
> dRamMemFrRamDblBitEccErrAdr = ECCFLX0EAD0;

// Clear error flags by setting the ECMCLSSE020 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0010 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCFLX0CTL = 0x0000 0400;

// Set NTC 01D.1 to Failed

SetNtcSts (0x01D, 0x02, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a FlexRay Temporary buffer (TBF B) RAM double bit ECC error
was detected

If ((ECCFLX0T0CTL & 0x0002 0004) != 0)

{

> // Stores address information for debug
>
> dRamMemFrRamTmpBufBDblBitEccErrAdr = ECCFLX0T0EAD0;

// Clear error flags by setting the ECMCLSSE020 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0010 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCFLX0T0CTL = 0x0000 0400;

// Set NTC 01D.5 to Failed

SetNtcSts (0x01D, 0x20, NtcSts1.NTCSTS_FAILD, 0);

}

// Check if a FlexRay Temporary buffer (TBF A) RAM double bit ECC error
was detected

If ((ECCFLX0T1CTL & 0x0002 0004) != 0)

{

> // Stores address information for debug
>
> dRamMemFrRamTmpBufADblBitEccErrAdr = ECCFLX0T1EAD0;

// Clear error flags by setting the ECMCLSSE020 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x0010 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear the 2 Bit Error Detection Flag

ECCFLX0T1CTL = 0x0000 0400;

// Set NTC 01D.3 to Failed

SetNtcSts (0x01D, 0x08, NtcSts1.NTCSTS_FAILD, 0);

}

If ((DMASSDTSER2 & 0x0000 8000) != 0)

{

// Stores address information for debug

dRamMemDtsRamEccErrAdr = DMASSRAMSECAD;

// Clear error flags by setting the ECMCLSSE106 bit of the ECMESSTC1
register

ECMESSTC1_Desired = 0x0000 0040;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

// Clear the 1 Bit Error Detection Flag

DMASSDTSERC = 0x0000 8000;

// Set NTC 012.3 to Failed

SetNtcSts (0x012, 0x08, NtcSts1.NTCSTS_FAILD, 0);

}

// Check for Local RAM Single Bit Soft Failures and set NTC

If (LclRamEccSngBitSoftFailr == TRUE)

{

// Set NTC 012.0 to Failed

SetNtcSts (0x012, 0x01, NtcSts1.NTCSTS_FAILD, 0)

LclRamEccSngBitSoftFailr = FALSE;

> // Increment counter and saturate at LCLRAMSNGBITCNTRMAX_CNT_U08
>
> LclRamEccSngBitCntr++;
>
> // Output Counter value
>
> LclRamEccSngBitCntrOutp = LclRamEccSngBitCntr;

}

// Check ECM status registers for an I-Cache ECC indication .ECMmSSE014
bit

If (((ECMMESSTR0 & 0x0000 4000) != 0) OR ((ECMCESSTR0 & 0x0000 4000) !=
0)))

{

> // Clear error flags by setting the ECMCLSSE014 bit of the ECMESSTC0
> register
>
> ECMESSTC0_Desired = 0x0000 4000;
>
> WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);
>
> // Clear the Error Flags in the Error Status Register
>
> ECCIC1IDSTCLR_PE1 = 0x0000 0003;
>
> ECCIC1ITSTCLR_PE1 = 0x0000 0001;
>
> // Set NTC 012.2 to Failed

SetNtcSts (0x012, 0x04, NtcSts1.NTCSTS_FAILD, 0);

}

### Reference Registers

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image5.wmf"
style="width:5.99583in;height:7.92569in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image6.wmf"
style="width:5.99306in;height:7.27847in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image7.wmf"
style="width:5.99722in;height:4.75069in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image8.png"
style="width:5.99653in;height:5.91736in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM103A_RamMem_Design/Design/mediax/media/image9.png"
style="width:5.99583in;height:5.07986in" />

### Verification Method

N/A

# Revision Record & Change Approval

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 8%" />
<col style="width: 54%" />
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
<td>01.00.00</td>
<td>10/21/2015</td>
<td>EA4#1735</td>
<td>SK</td>
<td>Initial Release</td>
</tr>
<tr class="odd">
<td>01.01.00</td>
<td>11/19/2015</td>
<td>EA4#2568</td>
<td>SK</td>
<td>Corrected the polled ECM Bits for I Cache. Refer Anomaly
EA4#2524</td>
</tr>
<tr class="even">
<td>02.00.00</td>
<td>03/29/2016</td>
<td>EA4#4865</td>
<td>GM</td>
<td><p>Change from EI Interrupt to Periodic Polling:</p>
<p>CAN single bit and double bit</p>
<p>SPI single bit</p>
<p>Added Flex Ray Single and Double Bit ECC</p>
<p>In RAM failure mode classification check function, error flag is
cleared after all 8 addresses have been read.</p>
<p>Added counter for Local RAM single bit ECC</p>
<p>Added SPI RAM double bit ECC from CM101A</p>
<p>Single bit DTS Ram ECC also added to periodic</p></td>
</tr>
<tr class="odd">
<td>02.00.01</td>
<td>3/31/2016</td>
<td>EA4#5094</td>
<td>GM</td>
<td>Add rationale to Local RAM ECC - 1 Bit</td>
</tr>
<tr class="even">
<td>02.01.00</td>
<td>4/11/2016</td>
<td>EA4#5279</td>
<td>SK</td>
<td><p>Combined Reference Registers sections 4.4.6 and 4.4.7</p>
<p>Added SetMcuDiagcIdnData() in SpiDblBitEcc</p>
<p>Added new PIMs for FlexRay Double Bit ECC and CAN Double ECC</p>
<p>Added coniditon to saturate LclRamEccSngBitCntr on reaching
LCLRAMSNGBITCNTRMAX</p></td>
</tr>
<tr class="odd">
<td>2.2.0</td>
<td>4/18/2016</td>
<td>EA4#5405</td>
<td>GM</td>
<td><p>Remove set MCU Diag data from SPI double bit ECC</p>
<p>Remove mask from ECC Error Message Flag in CTL registers</p></td>
</tr>
<tr class="even">
<td>3.0.0</td>
<td>07/25/2016</td>
<td>EA4#6656</td>
<td>SK</td>
<td>SPI ECC 2 Bit changed from EI to Polling</td>
</tr>
<tr class="odd">
<td>3.0.1</td>
<td>08/28/2016</td>
<td>EA4#7051</td>
<td>SK</td>
<td>Added instructions to clear ECC Status Registers of CAN, FlexRay and
DTS RAM</td>
</tr>
</tbody>
</table>

{% endraw %}