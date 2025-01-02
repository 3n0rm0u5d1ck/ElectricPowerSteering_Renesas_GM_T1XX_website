---
layout: default
title: CM111A_VrfyCritReg
nav_order: 1
parent: Component Design
---
{% raw %}
**Verify Critical Register**

**(VrfyCritReg)**

**FDD \#CM111A**

[1. High Level Description 3](#high-level-description)

[2. Sub-Function In This Document 3](#sub-function-in-this-document)

[3. Critical Registers 3](#critical-registers)

[3.1. Sub-Function: VrfyCritRegInit1 3](#__RefHeading___Toc448933443)

[3.1.1. NTCs 3](#ntcs)

[3.1.2. SAN Linkage 3](#san-linkage)

[3.1.3. Description 4](#description)

[3.1.4. Rationale 4](#rationale)

[3.1.5. Implementation 5](#implementation)

[3.2. Sub-Function: VrfyCritRegPer1 6](#sub-function-vrfycritregper1)

[3.2.1. NTCs 6](#ntcs-1)

[3.2.2. SAN Linkage 6](#san-linkage-1)

[3.2.3. Description 6](#description-1)

[3.2.4. Rationale 6](#rationale-1)

[3.2.5. Implementation 6](#implementation-1)

[3.2.6. Verification Method 8](#verification-method)

[4. Revision Record & Change Approval 8](#__RefHeading___Toc448933456)

# High Level Description

This document describes the microcontroller configuration for the
critical register verification functions. Critical registers are ones
whose contained values are considered vital to safety or function
(secondary to safety) beyond the protections provided by protection
hardware and software.

The functions described herein perform read back and value verification
functions. If a mismatch is detected in the result shall be transition
to a safe state preceded by non-volatile storage of the specific cause
of this decision if possible.

The initial lists of critical registers were obtained by reviewing the
recommendations of Renesas’ Safety Application Note ver 1.20.

Some of these recommendations were not followed because they would
require masking off of unpredictable bits and some may have been
rejected if the particular hardware interface is not used.

# Sub-Function In This Document

Below is a list of all sub-functions owned by this document.

|                                                                      |                                         |
|---------------------------------------------------------|---------------|
| **Sub-Function Name**                                                | **Link**                                |
| Check critical registers once at initialization ( VrfyCritRegInit1 ) | [3.1](#_Sub-Function:_VrfyCritRegInit1) |
| Check critical registers during periodic updates ( VrfyCritRegPer1 ) | [3.2](#_Sub-Function:_<Name_of)         |
| Empty Initial Sub-function ( VrfyCritRegInit2 )                      | [3.3](#_Sub-Function:_VrfyCritRegInit2) |

# Critical Registers

## Sub-Function: VrfyCritRegInit1

### NTCs

N/A

### SAN Linkage

5.2 Read back of configuration static register should be done at
start-up \[SAN-P1x-0504\].

7.2 Read back the static configuration registers shall be done once at
start-up \[SAN-P1x-0704\]. This includes to check that ECC is enabled,
error notification to ECM and test registers.

8.2 At startup it shall be checked that the address parity check is
enabled by reading back the related control register.

9.2 Read back DFECCCTL and FERRINT registers should be done once at
start-up.

10.2 Read back the static configuration register once at start-up shall
be done to ensure that the correct values are set \[SAN-P1x-1005\]. This
includes to check that ECC is enabled and error notification to the ECM.

11.2 Read back the static configuration register once at start-up shall
be done to ensure that the default settings are correctly set.

13.2 Read back the static configuration register once at start-up shall
be done to ensure that the correct values are set. This includes to
check that ECC is enabled and error notification to ECM as well
\[SAN-P1x-1305\].

14.2 The control register shall be also read back once after
configuration to ensure the CLM is enable \[SAN-P1x-

1403\].

15.2 In order to confirm the operation of the locking function, the SW
shall write "0" to CVMDIAGMEW and CVMFBISTMEW bits and verify that "1"
is not overwritten by "0" by reading back CVMDE register
\[SAN-P1x-1508\].

15.2 Moreover static configuration register shall be read-back and
verified to ensure that the correct values are

set.

16.2 Static configuration register shall be read back and verified once
at start-up to ensure that the related register

have the proper configuration.

25.2 The configuration from the mode register shall be read to confirm
that the correct operating mode (normal

mode) has been entered and/or that the proper value has been applied to
the external mode pins.

29.2 Field BIST control register shall be read back and verified to
ensure that the Field BIST is enabled \[SAN-P1x-2902\].

31.2 the user shall check that the transfer of the data is carried out
without error. This can be done by reading back the option byte register
and checking the content.

### Description

This sub-function reads values from critical registers and verifies that
the stable portion retains the expected value which has been deemed to
be critical.

### Rationale

This function is intended to be called once per update period so that it
can verify that critical registers still hold the values expected.
Because an NTC code is set on failure, this function must not be called
until after the Diagnostic Manager has run to start the handling of
these calls

Caution: In order to record a unique number which will identify which
value has failed this test, the number of “periodic” test critical
registers must be maintained/communicated to the “initialization” code
to use as the starting value for its count.

### Implementation

Each entry in the register table shall be read, bitwise masked (an AND
operation) with a value specific to the register to handle unused or
dynamic bits and compared to the expected value. Any mismatch indicates
a non-recoverable error so the code shall set a NTC diagnostic code and
stop iterating.

struct NonSysCritRegRec1

{

uint CritRegAdr;

uint CritRegVal;

uint CritRegMask;

}

struct NonSysCritRegRec1
**Inin**CritReg**8**BitChk\[NROFININCRITREG8BIT_CNT_U16\];

struct NonSysCritRegRec1
**Inin**CritReg**16**BitChk\[NROFININCRITREG16BIT_CNT_U16\];

struct NonSysCritRegRec1
**Inin**CritReg**32**BitChk\[NROFININCRITREG32BIT_CNT_U16\];

struct NonSysCritRegRec1
**Per**CritReg**8**BitChk\[NROFPERCRITREG8BIT_CNT_U16\];

struct NonSysCritRegRec1
**Per**CritReg**16**BitChk\[NROFPERCRITREG16BIT_CNT_U16\];

struct NonSysCritRegRec1
**Per**CritReg**32**BitChk\[NROFPERCRITREG32BIT_CNT_U16\];

void VrfyCritRegInit1( void )

{

temp boolean CritRegInitTestPassd = TRUE;

> //CritRegFltTyp = 0 when there is no error, CritRegFltTyp = 1 when
> there is a non-system critical //register error, CritRegFltTyp = 2
> when there is a system critical error

uint CritRegFltTyp = 0;

//If there is one bad comparison no other critical registers need to be
verified

//configure IninCritReg#BitChk as a trusted function because it needs to
run in supervisor mode

> For each **Inin**CritReg**\#**BitChk\[\] struct instance, loop over
> all “init” critical register values until CritRegFltTyp != 0;
>
> {
>
> Read the register’s value,
>
> mask the register’s value with the mask value for this register;
>
> if (the masked value != expected value)
>
> CritRegFltTyp = 1;
>
> else
>
> Nothing;

}

//configure SysCritRegIninChk as a trusted function because it needs to
run in supervisor mode

For each SysCritRegIninChk, verify all “init” critical register values
until CritRegFltTyp != 0;

> {
>
> Read the register’s value,
>
> mask the register’s value with the mask value for this register;
>
> if (the masked value != expected value)
>
> SysCritRegInitTestPassd = FALSE;
>
> CritRegFltTyp = 2;
>
> else
>
> Nothing;

}

if (CritRegFltTyp = 0)

> SetNtcSts( NtcNr1.NTCNR_0x20, 0, NtcSts1.NTCSTS_PASSD, 0);
>
> else
>
> SetNtcSts( NtcNr1.NTCNR_0x20, CritRegFltTyp, NtcSts1.NTCSTS_FAILD, 0);

}

## Sub-Function: VrfyCritRegPer1

Return to sub-function list link: Sub-Function In This Document

### NTCs

Critical Register Verification Fault NTC \#0x20.

### SAN Linkage

4.5.1 For PBG0A the customer should ensure that the guard setting
settings are not  
accidently changed (e.g. periodic check of the protection setting
register, MPU and so on).

### Description

This sub-function reads values from critical registers and verifies that
the stable portion retains the expected value which has been deemed to
be critical.

### Rationale

This function is intended to be called once per update period so that it
can verify that critical registers still hold the values expected.

### Implementation

Each entry in the register table shall be read, bitwise “ANDed” with a
mask specific to the register and compared to the expected value. Any
mismatch indicates a non-recoverable error so the code shall set an NTC
code.

void VrfyCritRegPer1( void )

{

temp boolean CritRegPerTestPassd = TRUE;

> //CritRegFltTyp = 0 when there is no error, CritRegFltTyp = 1 when
> there is a non-system critical //register error, CritRegFltTyp = 2
> when there is a system critical error

CritRegFltTyp = 0

//If there is one bad comparison no other critical registers need to be
verified

//configure PerCritReg#BitChk as a trusted function because it needs to
run in supervisor mode

> For each **Per**CritReg**\#**BitChk\[\] struct instance, loop over all
> “periodic” critical register values until CritRegFltTyp != 0;
>
> {
>
> Read the register’s value,
>
> mask the register’s value with the mask value for this register;
>
> if (the masked value != expected value)
>
> CritRegFltTyp = 1;
>
> else
>
> Nothing;

}

//configure SysCritRegIninChk as a trusted function because it needs to
run in supervisor mode

For each SysCritRegPerChk, verify all “init” critical register values
until CritRegFltTyp != 0;

> {
>
> Read the register’s value,
>
> mask the register’s value with the mask value for this register;
>
> if (the masked value != expected value)
>
> CritRegFltTyp = 2;
>
> else
>
> Nothing;

}

if (CritRegFltTyp = 0)

> SetNtcSts( NtcNr1.NTCNR_0x20, 0, NtcSts1.NTCSTS_PASSD, 0);
>
> else
>
> SetNtcSts( NtcNr1.NTCNR_0x20, CritRegFltTyp, NtcSts1.NTCSTS_FAILD, 0);

}

#### Periodic

Iteration period T =10 msec second.

### Verification Method

N/A

# Revision Record & Change Approval

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 13%" />
<col style="width: 12%" />
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
<td>01/14/2016</td>
<td>2772</td>
<td>EC</td>
<td>Initial Release</td>
</tr>
<tr class="odd">
<td>02.00.00</td>
<td>03/28/2016</td>
<td>4992</td>
<td>EC</td>
<td>Restore separate init entry and masks, both set NTC once per entry
with second parameter being index to the problem register</td>
</tr>
<tr class="even">
<td>02.01.00</td>
<td>04/07/2016</td>
<td>4992</td>
<td>SK</td>
<td><p>Deleted Init2 because we already have an RTE Init1.</p>
<p>Updated Init1 and Per1 to show different parameter byte info for
different register index.</p></td>
</tr>
<tr class="odd">
<td>02.02.00</td>
<td>04/20/2016</td>
<td>5444</td>
<td>GM</td>
<td><p>Add structure definitions for 8bit, 16bit and 32bit non-system
critical register check.</p>
<p>Add separate definition for system critical register check.</p>
<p>Manage system and non-system critical register faults with different
NTC parameter bits.</p></td>
</tr>
</tbody>
</table>

{% endraw %}