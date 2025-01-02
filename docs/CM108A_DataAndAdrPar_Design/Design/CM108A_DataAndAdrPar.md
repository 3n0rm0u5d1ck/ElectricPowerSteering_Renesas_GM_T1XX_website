---
layout: default
title: CM108A_DataAndAdrPar
nav_order: 1
parent: Component Design
---
{% raw %}
**Data And Address Parity RH850**

**(DataAndAdrPar)**

**FDD \#CM108A**

[1. High Level Description 3](#high-level-description)

[2. Sub-Function In This Document 3](#sub-function-in-this-document)

[3. Critical Registers 3](#critical-registers)

[4. Sub-functions 3](#sub-functions)

[4.1. Sub-Function: DataAndAdrParInit1
3](#sub-function-dataandadrparinit1)

[4.1.1. NTCs 4](#ntcs)

[4.1.2. SAN Linkage 4](#san-linkage)

[4.1.3. Description 4](#description)

[4.1.4. Rationale 4](#rationale)

[4.1.5. Implementation 6](#implementation)

[4.1.6. Reference 8](#reference)

[4.1.7. Verification Method 14](#verification-method)

[4.2. Sub-Function: DataAndAdrParInit2
15](#sub-function-dataandadrparinit2)

[4.2.1. Description 15](#description-1)

[5. Revision Record & Change Approval
15](#revision-record-change-approval)

# High Level Description

This document covers the functions which address protection of data and
address buses. Data bus protection consists of the detection of errors
in conveying data between peripheral devices and bus masters per HWUM
table 31.56. Address bus protection consists of the detection of errors
in conveying addresses to the code flash only. The default power-up
values enable this detection and notification to the ECM so no action is
needed for this function. This function is mentioned here because there
is a SAN requirement to verify the detection and notification status
which will be satisfied by an init (one time only) check of the relevant
registers as critical registers.

Renesas Document References:

Hardware User’s Manual (HWUM) version 1.10 dated Feb 2016

Safety Application Note (SAN) R01AN2118EJ0120 Rev. 1.20 Release December
1, 2015

Data parity self-test (SAN-P1x-1802) Feb 16, 2016

# Sub-Function In This Document

Below is a linked list of all sub-functions owned by this document.

|                       |                                              |
|-----------------------|----------------------------------------------|
| **Sub-Function Name** | **Link**                                     |
| DataAndAdrParInit1    | [4.1](#_Sub-Function:_DataAndAddressParInit) |
| DataAndAdrParInit2    | [4.2](#_Sub-Function:__DataAndAdrParInit2)   |

# Critical Registers

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 14%" />
<col style="width: 17%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Register</strong></td>
<td><p><strong>Register No.</strong></p>
<p><strong>(regID, selID)</strong></p></td>
<td><strong>Access Permission</strong></td>
<td><strong>Init/Periodic Verification</strong></td>
<td><strong>Masking</strong></td>
<td><strong>Expected Value</strong></td>
<td><p><strong>Protn Score From</strong></p>
<p><strong>Eval Sheet</strong></p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

# Sub-functions

## Sub-Function: DataAndAdrParInit1

Return to sub-function list link: <u>Sub-Function In This Document</u>

### NTCs

N/A

### SAN Linkage

SAN version 1.20

Para 29.1

The LBIST checks all error signal paths from the modules to the ECM that
are themselves targeted by the LBIST except the error signal paths from
the DMA compare unit, the PBG3A, and **from OR-gate for data parity**.

### Description

This function verifies that the signal path from the data parity OR gate
to the ECM is functional. Since the SAN section describing the LBIST
coverage mentions this function as one which is not checked, it is
chosen to implement this test.

There has been no requirement identified to perform a startup test on
the address parity unit so none has been created.

### Rationale

This function tests the signal path which the LBIST misses according to
the SAN. Per the SAN, only one of the data parity sources is tested and
both read and write to the tested peripheral are checked. See HWUM table
31.6 for a list of the data parity sources which can be used. This
design arbitrarily uses the CHBB0 group (CSIG group B) to perform the
test.

By convention, all ‘once per power cycle’ tests are always entered and
each calls a function (ChkForStrtUpTest) which determines whether the
test should perform its test or trivially return.

The design deviates slightly from the SAN flowchart:

The SAN flowchart does not address the impact of this error’s drive to
the SYSERR function. Because of this, the SEGCONT register must have a
bit cleared during testing to prevent SYSERR exceptions and one bit in
the SEGFLAG register must have one cleared after testing because the
testing set it. Similarly, the driving of the ERROROUT pin must be
masked off from the error signals which will occur during the test.
These registers (SEGCONT and ECMEMK0) must be restored before the test
returns.

The SAN flowchart of figure 18.4-3 shows two undefined “Wait”
operations. Renesas provided additional information and a modified
flowchart which explains that this test may repeatedly sample the ECM
register field (ECMMESSTR0 bit 28) and that the appearance of the value
one in that bit indicates the test has succeeded but, failing to observe
that value after injecting an error, the sampling must continue until
either that one is observed or at least one sample is taken after the
requisite amount of time has passed. This time is different for reads
and writes and also has different values for different peripheral
groups. Renesas provided a table of latencies where the values for any
peripheral to be used in this data parity test can be found, but they
recommend using the worst case write and read times over all peripherals
regardless of which one is chosen to be tested. Their table’s read and
write values are to be multiplied by four and used for the corresponding
flowchart wait times.

One option offered was to follow the Renesas recommendation except in
the area of the backup loop termination condition. The backup condition
chosen is to use a large number of loop iterations, with 1000 thought to
be sufficient to guarantee more sampling time than the Renesas table
demands. When this count is exhausted without seeing the error bit
appear in the ECM register the test will be judged to have failed.

These are all functionally equivalent as long as care is taken to
provide for a means for the logic to exit in the case of a hardware
failure. The main difference between them is the amount of time in the
normal and fail paths and these are not very large in this case.

Another area where the design deviates from the SAN flowchart is the
area where the writing of the test mode occurs. Renesas has evaluated
the design and advised that writing 10B to APDPTMC.APDPTMC may occur
using the same write used to write the test mode control bits contrary
to the two step write illustrated in the SAN flowchart.

Another area where the design deviates from the SAN flowchart is that
after inducing each write error, the specific error detection bit is
cleared by writing one to the corresponding clear register, delaying
(via syncm) and verifying the clear. Only a simple clear is mentioned in
the SAN flowchart. Rev 1.10 is the first version of the Hardware User’s
Manual which states this requirement for this syncm.

Conducting the test

After preventing the normally terminal consequences of data parity
errors, an error is inserted using the processor’s test facilities. It
is verified that the error signal propagated to the ECM unit from a read
and a write operation before clearing the record of the ECM error before
restoring the error detection circuitry to its operational
configuration.

NOTE: This code writes to and reads from SEG registers SEGCONT and
SEGFLAG. These are protected by IPG (guard) bits. The current settings
elsewhere in CM107A allow reading but cause writing to be a guard
violation. To avoid this, this startup test must run before the IPG is
initialized by CM107A.

Meaning of the second parameter of the calls to the function
SetMcuDiagcIdnData:

|                     |                                                                             |
|-------------|-----------------------------------------------------------|
| 2^nd^ param. Bit \# | Failure cause                                                               |
| 0                   | VCIF set before testing began                                               |
| 1                   | ECM bit 28 set before testing began                                         |
| 2                   | Fail report bit did not reach ECM BIT28 during peripheral read              |
| 3                   | Fail report bit did not reach ECM BIT28 during peripheral write             |
| 4                   | Fail report bit did not reach error status register during peripheral write |
| 5                   | Failure to clear error status                                               |
| 6                   | Test Mode Control reg. did not verify                                       |

### Implementation

static const uint32_t BIT28 = 1 \<\< 28;

//after inducing an error that should show up in ECMMESSTR0 bit28

//call this… will spin until the error appears or timeout, then return
true if it is set (test pass)

static boolean waitForECMBit28 ( void)

{

boolean returnValue;

loop, sampling ECMMESSTR0 until BIT28 is set or 1000 samples have been
taken

or time has elapsed (see text)

if 1000 samples were taken or timed out without seeing ECMMESSTR0.BIT28

{

returnValue = false; //value for a fail

}

else

{

returnValue = true; // backupCount was not zero so the bit was there

}

return returnValue;

}

static void WriteTmc(uint32_t value, uint32_t\* errorCode) //implicitly,
we need to verify

{

APDPTMC_CHBB0 = value;

if ( (value & 15) != APDPTMC_CHBB0) //upper bits always read as zero

\* errorCode \|= 1UL\<\<6;

}

// This code requires Supervisor mode!!!

void DataAndAdrParInit1 (void )

{

uint32_t vcif = SEGFLAG.VCIF; //sample the volatile register

uint32_t ecmBit28 = (ECMMESSTR0 & BIT28) \>\>28; //sample the volatile
register

uint32_t errorCode = (ecmBit28 \<\<1) + vcif;

Boolean ExecStrtUpTest;

ChkForStrtUpTest ( &ExecStrtUpTest);

if (ExecStrtUpTest && ( 0 == errorCode) )

{

uint8_t bucket; //test data is read to or written from here

uint32_t ECMEMK0SAV = ECMEMK0;

uint16_t SEGCONTSAV = SEGCONT;

// set BIT28 to prevent (mask off) test induced data parity error

// from getting to the errorout pin

WrProtdRegEcm_u32 ( ECMEMK0SAV \| BIT28, ECMEMK0 ); //this function
verifies

// prevent SYSERR when the test induces errors

// the following line requires Supervisor mode!!!!

SEGCONT.VCIE = 0; // turn off syserr response to VCIE things

WriteTmc ( 0x400FUL, &errorCode); // the “4” is an enable key

// “F” injects errors in all four byte lanes

if (0 == errorCode)

{

bucket = CSIG0BCTL0; // read from a reg in the module, this injects an
error

if (waitForECMBit28())

{ // parity error was detected so the test is passing so far

WrProtdRegEcm_u32 (BIT28, &ECMESSTC0 ); //clear the ecm error bit

WriteTmc ( 0x400FUL, &errorCode); // the “4” is an enable key, “F”
selects all four byte lanes

if (0 == errorCode)

{

CSIG0BCTL0 = bucket; //write to inject error

if ( ! waitForECMBit28())

{ // error status was not detected, fail

errorCode \|= 1UL\<\<3; //pass an error code for write

}

if (0 == APDPERRST_CHBB0 )

{ // ECM error status was not detected, fail

errorCode \|= 1UL\<\<4; //pass an error code for write

}

WrProtdRegEcm_u32 (BIT28, ECMESSTC0); //clear the ecm error bit

APDPERRSTC_CHBB0 = 1; // clear the error status near the source

asm( "syncm" ); // delay to let the test mode propagate

if ( 1 == APDPERRST_CHBB0) // see if the error status bit cleared

errorCode \|= 1UL\<\<5; //it did not clear, pass an error code

} // if (0 == errorCode)

} //end of successful read test

else

{

errorCode \|= 1UL\<\<2; //pass an error code for read

}

} // if (0 == errorCode)

//turn off test mode

WriteTmc ( 0x4000UL, &errorCode); // the “0” is an enable key, “0”
selects zero byte lanes errored

// restore normal operation of ECM Resets, interrupts when subsequent
code causes an error.

SEGFLAG.VCIF = 0; // clear VCIF, this gets set despite VCIE being 0

SEGCONT = SEGCONTSAV; // restore syserr response to VCIE things per
entry value

//check that this test didn’t generate CF or DF etc errors

// maybe they will just happen when SEGCONT.VCIE was set to one above

// 0x400 3800 checks for PBG error (bit 26) or

// (DTSRAM, DF, CF ) 2bit ECC errors or CF address parity bits 15, 16,
17

//if ( ECMMESSTR0 & 0x403 8000 ) // optional, delete if these failures
are not worth the effort

// DoSyserr(); // optional, delete if these failures are not worth the
effort

// restore ECMEMK0 to allow PBG error to get to the ERROROUT pin
(unmask) per entry value

WrProtdRegEcm_u32 ( ECMEMK0SAV, &ECMEMK0); //this function verifies

if (0 \< errorCode)

SetMcuDiagcIdnData ( McuDiagc1.MCUDIAGC_PRPHLBUSDATAPARSTRTUPFLT*,*

errorCode);

}

else if (ExecStrtUpTest)

{

SetMcuDiagcIdnData ( McuDiagc1.MCUDIAGC_PRPHLBUSDATAPARSTRTUPFLT*,*

errorCode);

}

}

### Reference

This flowchart is from SAN ver 1.20:

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image1.wmf"
style="width:6.03611in;height:4.57292in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image2.wmf"
style="width:5.98889in;height:8.22361in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image3.wmf"
style="width:5.99028in;height:3.71319in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image4.wmf"
style="width:5.99514in;height:5.23056in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image5.wmf"
style="width:5.99167in;height:3.86528in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM108A_DataAndAdrPar_Design/Design/mediax/media/image6.wmf"
style="width:6.49583in;height:7.51667in" />

### Verification Method

N/A

## Sub-Function: DataAndAdrParInit2

Return to sub-function list link: Sub-Function In This Document

###  Description

This is a null sub-function.

NOTE: Register values which have been established by bootloader or by
reset:

|               |       |        |
|---------------|-------|--------|
| Register name | value | Set by |
| CFERRINT_PE1  | 7     | FBL    |
| CFAPCTL       | 0     | Reset  |

# Revision Record & Change Approval

|          |            |                       |         |                                                                                   |
|--------|----------|----------|-------|-------------------------------------|
| **Rev**  | **Date**   | **Change Control \#** | **Drw** | **Change Description**                                                            |
| 01.00.00 | 03/14/2016 | EA4#2762              | EC      | Initial Release                                                                   |
| 01.00.01 | 03/15/2016 | EA4#2762              | EC      | Add mfile function name, correct para. indices and convert list to variable table |
| 01.01.00 | 03/29/2016 | EA4#5007              | EC      | Remove some syncms                                                                |

{% endraw %}