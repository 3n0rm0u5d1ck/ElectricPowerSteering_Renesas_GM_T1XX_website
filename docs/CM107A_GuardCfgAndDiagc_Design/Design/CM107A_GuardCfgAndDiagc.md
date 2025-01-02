---
layout: default
title: CM107A_GuardCfgAndDiagc
nav_order: 1
parent: Component Design
---
{% raw %}
**Guard Configuration And Diagnostics RH850**

**( GuardCfgAndDiagc )**

**FDD CM107A**

[1. High Level Description
[3](#high-level-description)](#high-level-description)

[1.1. Overview [3](#overview)](#overview)

[1.2. Slave Guards [3](#slave-guards)](#slave-guards)

[1.2.1. IPG – Internal Peripheral Guard
[4](#ipg-internal-peripheral-guard)](#ipg-internal-peripheral-guard)

[1.2.2. PEG – PE Guard Function
[4](#peg-pe-guard-function)](#peg-pe-guard-function)

[2. Sub-Functions in this Document
[5](#sub-functions-in-this-document)](#sub-functions-in-this-document)

[3. Sub-functions [5](#sub-functions)](#sub-functions)

[3.1 Sub-function: (GuardCfgAndDiagcInit1)
[5](#sub-function-guardcfganddiagcinit1)](#sub-function-guardcfganddiagcinit1)

[3.1.2. Guard Configuration Section: PEG Slave Guard Configuration
[6](#guard-configuration-section-peg-slave-guard-configuration)](#guard-configuration-section-peg-slave-guard-configuration)

[3.1.3. Guard Configuration Section: IPG Slave Guard Configuration
[13](#guard-configuration-section-ipg-slave-guard-configuration)](#guard-configuration-section-ipg-slave-guard-configuration)

[3.1.4. Guard Configuration Section: PBG Slave Guard Configuration
[19](#guard-configuration-section-pbg-slave-guard-configuration)](#guard-configuration-section-pbg-slave-guard-configuration)

[4.1 Sub-Function (GuardCfgAndDiagcInit2)
[28](#sub-function-guardcfganddiagcinit2)](#sub-function-guardcfganddiagcinit2)

[4.2 Sub-Function: (GuardCfgAndDiagcInit3)
[28](#sub-function-guardcfganddiagcinit3)](#sub-function-guardcfganddiagcinit3)

[3.1.5. NTCs [28](#ntcs-4)](#ntcs-4)

[3.1.6. SAN Linkage [28](#san-linkage-4)](#san-linkage-4)

[3.1.7. Description [29](#description-4)](#description-4)

[3.1.8. Rationale [29](#rationale-4)](#rationale-4)

[3.1.9. Implementation [30](#implementation-3)](#implementation-3)

[3.1.10. Reference [39](#reference-4)](#reference-4)

[3.1.11. Verification Method
[50](#verification-method-4)](#verification-method-4)

[4. Revision Record & Change Approval
[50](#revision-record-change-approval)](#revision-record-change-approval)

#  High Level Description

This document describes the microcontroller configuration for the micro
slave guard function. This function will selectively enable access to
microcontroller resources. On reset most of these resources are
unprotected so the net behavior of the slave guard function is to
constrain access.

Ref. Renesas’ Hardware User’s Manual Ver 1.10 Dtd Feb 2016

## 1.1. Overview [overview]

The RH850 P1M MCU provides protection features to prevent erroneous
access to memory and the control registers of the peripheral circuits
using the slave guard function.

## 1.2. Slave Guards [slave-guards]

There are three sections to the guard function:

1.  PEG – Processor Element Guard

2.  IPG – Internal Peripheral Guard

3.  PBG – Peripheral Bus Guard

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image1.png"
style="width:5.98889in;height:5.13056in" />

Fig 4.1-1 from SAN 1.20 edited to correct the Flexray PROTSPID to match
the value shown in the HWUM 1.1

### 1.2.1. IPG – Internal Peripheral Guard [ipg-internal-peripheral-guard]

The IPG section protects the CPU peripherals against illegal accesses by
SW components running on the CPU itself.

The IPG provides the following features:

-   Detects violation of peripheral device protection.

-   Stores unauthorized access information

-   Blocks unauthorized access.

-   Notifies violation through an exception.

-   Invalidates subsequent access (post violation).

### 1.2.2. PEG – PE Guard Function [peg-pe-guard-function]

The PE guard system section prevents unauthorized access to the
resources in the PE from an external master. This section protects
access to the local RAM in the PE.

The PEG provides the following features:

-   Protects local RAM against illegal access from FlexRay and the DMA.

-   Detects PE access violation.

-   Blocks unauthorized access.

-   Provides notification of an unauthorized access through the ECM.

-   Allows protection of up to 4 areas with 4K granularity.

##### 1.2.3. PBG – Peripheral Bus Guards [pbg-peripheral-bus-guards]

The PBG protects the control registers in the peripheral circuits and
memories from illegal access by the PE, Flexray and the DMA. The PBG
module is divided into multiple PBG groups, each of which is provided a
maximum of 16 protection channels.

A single PBG channel can designate the access against which a single
peripheral circuit should be protected. Each PBG group can hold the
information of the access that has been rejected.

**The PBG provides the following features:**

-   For protection against read access, an undefined value is read.

-   For protection against write access, the write access is ignored.

-   Provides notification of an unauthorized access through the ECM.

-   Stores unauthorized access information.

# *Sub-Functions in this Document*

Below is a linked list of all sub-functions owned by this document.

| **Sub-Function Name** | **Link**                                   |
|-----------------------|--------------------------------------------|
| GuardCfgAndDiagcInit1 | [4.1](#sub-function-guardcfganddiagcinit1) |
| GuardCfgAndDiagcInit2 | [4.2](#sub-function-guardcfganddiagcinit2) |
| GuardCfgAndDiagcInit3 | [4.3](#sub-function-guardcfganddiagcinit3) |

# Sub-functions

##  Sub-function: (GuardCfgAndDiagcInit1)

Return to subfunction list: [return](#sub-functions-in-this-document)

### NTCs

N/A

### SAN Linkage

See the SAN Linkage paragraph of each of the sections which make up this
sub-function.

### Description

This sub-function configures the RH850/P1M. This has been described in
three sections which correspond to the portions of the guard hardware
facilities which the microcontroller provides.

### Rationale

This sub-function has been defined in terms of the sections which
correspond to the hardware resources. This seems to have helped to
organize the information but what was thought to be an additional
benefit, supporting distinct initialization times for the different
guard hardware, has not been used and has not been maintained.

### Implementation

See the Implementation paragraph of each of the sections which make up
this sub-function.

### Initialization (GuardCfgAndDiagcInit1)

PegInin();

IpgInin();

PbgInin();

### Reference

See the Reference paragraph of each of the sections which make up this
sub-function.

### Verification Method

See the Verification Method paragraph of each of the sections which make
up this sub-function.

### Guard Configuration Section: PEG Slave Guard Configuration

Return to sub-function list link:
[return](#sub-functions-in-this-document)

Provides notification of an unauthorized access to the ECM.

#### NTCs

N/A

#### SAN Linkage

**SAN-169:** After reset, the access to the local RAM by bus masters
other than the PE (CPU) itself is disabled. Thus, protection- setting
registers **shall** be configured to authorize desired accesses by the
DMA and FlexRay. These registers are not protected by PEG and can be
thus protected by means of the MPU or the IPG.

#### Description

This sub-function configures the RH850/P1M for the PEG. The PEG provides
and limits access of masters other than the PE (the Flexray and DMA
channels) to LRAM.

#### Rationale

Using the 4Kbyte resolution of the PEGG memory protection capability,
the external masters (Flexray and DMA channels) have write access to the
same one 4K block of LRAM and may read all 128Kbytes. PEG0 registers
define and control the writable 4Kbyte memory block in the highest 4K
addresses of LRAM: 0xFEBFF000 through 0xFEBFFFFF. PEGG1 registers define
and control the readable 128Kbyte memory block which is all of LRAM:
0xFEBE0000 through 0xFEBFFFFF. Two PEGG register sets remain unused.

DMA channels which move data from peripheral to LRAM, from LRAM to
peripheral, or from LRAM to LRAM will have different SPIDs. Their access
rights will be determined by the SPIDs.

####  Implementation

PEG Protection Targets – Following access types are allowed or
restricted for bus masters of each SPID:

1.  SPID 0 – Read access allowed, Write access allowed.

2.  SPID 1 – Read access restricted, Write access restricted.

3.  SPID 2 – Read access allowed, Write access restricted.

4.  SPID 3 – Read access allowed, Write access allowed.

Per the IPG setup in section 4.1, the PEG registers cannot be changed in
user mode.

DMA channels will be assigned SPIDs corresponding to their respective
LRAM and peripheral access requirements (SPID 2 or 3).

Flexray uses SPID 3. Currently, the intent is to make no use of the
Flexray’s memory access capability but the SPID 3 ability to write to
only the special 4K block and to read the entire LRAM matches well with
possible future designs.

The CPU is, thus far, only using the Reset initialized SPID value of 1.

The “CAUTION” note following Table 3.63 of the HWUM states “PEGGnBA.GnEN
is cleared by writing to the PEGGnMK register.” Therefore, the PEGGnMK
must be written before PEGGnBA for every PEGGnBA where a “1” is desired
in the GnEN bit.

**Register Configuration Summary:**

<table>
<colgroup>
<col style="width: 11%" />
<col style="width: 22%" />
<col style="width: 52%" />
<col style="width: 5%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th rowspan="2"><strong>Register</strong></th>
<th rowspan="2"><strong>Value</strong></th>
<th rowspan="2"><strong>Comments</strong></th>
<th colspan="2"><strong>Access</strong></th>
</tr>
<tr class="odd">
<th><strong>SV</strong></th>
<th><strong>UM</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>PEGSP</td>
<td>0x0001</td>
<td>Enable detection of accesses by any external master with an enabled
SPID.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="even">
<td>PEGG0BA</td>
<td><p>0xFEBF F095</p>
<p>PEGG0BA.G0BASE = 0xFEBFF</p>
<p>PEGG0BA.G0SP3 = 1</p>
<p>PEGG0BA.G0SP2 = 0</p>
<p>PEGG0BA.G0SP1 = 0</p>
<p>PEGG0BA.G0SP0 = 1</p>
<p>PEGG0BA.G0WR = 1</p>
<p>PEGG0BA.G0RD = 0</p>
<p>PEGG0BA.G0EN = 1</p></td>
<td><p>Initialized to Local RAM start address in high order 20 bits.</p>
<p>Write access allowed for SPID 3 and SPID 0. Write Access not allowed
for SPID 2 and 1.</p></td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="odd">
<td>PEGG0MK</td>
<td><p>0x0000 0000</p>
<p>PEGG0MK.G0MASK = 0x00000</p></td>
<td>This memory region consists of one 4Kbyte block so a zero mask makes
all 20 bits of the G0BASE field of PEGG0BA significant.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="even">
<td>PEGG1BA</td>
<td><p>0xFEBE 00D3</p>
<p>PEGG1BA.G1BASE = 0xFEBE0</p>
<p>PEGG1BA.G1SP3 = 1</p>
<p>PEGG1BA.G1SP2 = 1</p>
<p>PEGG1BA.G1SP1 = 0</p>
<p>PEGG1BA.G1SP0 = 1</p>
<p>PEGG1BA.G1WR = 0</p>
<p>PEGG1BA.G1RD = 1</p>
<p>PEGG1BA.G1EN = 1</p></td>
<td><p>Initialized to 128Kb Local RAM’s start address.</p>
<p>Read access allowed for SPID 2, SPID 3 and SPID 0. Read Access not
allowed for SPID 1.</p></td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="odd">
<td>PEGG1MK</td>
<td><p>0x0001 F000</p>
<p>PEGG1MK.G1MASK = 0x0001F</p></td>
<td>With five mask bits set to one, only fifteen of the 20 bits of the
G1BASE field of PEGG1BA are compared. The entire local RAM is made read
accessible here since (32- 15 =) 17 bits addresses 128 Kbyte.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="even">
<td>PEGG2BA</td>
<td>0</td>
<td>Set to or allow to remain at the value of zero established by
reset.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="odd">
<td>PEGG2MK</td>
<td>0</td>
<td>Set to or allow to remain at the value of zero established by
reset.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="even">
<td>PEGG3BA</td>
<td>0</td>
<td>Set to or allow to remain at the value of zero established by
reset.</td>
<td>RW</td>
<td>RW*</td>
</tr>
<tr class="odd">
<td>PEGG3MK</td>
<td>0</td>
<td>Set to or allow to remain at the value of zero established by
reset.</td>
<td>RW</td>
<td>RW*</td>
</tr>
</tbody>
</table>

\* the access rights shown are the “after reset” defaults, these are
modified by the value written to IPGPMTUM4 as described in this
document.

##### Initialization (PegInin)

PEGG0MK = 0x0000 0000; //write each MK before the corresponding BA!!!

//side effect of writing PEGGnMK: it clears PEGGnBA.GnEN

PEGG0BA = 0xFEBF F095;

PEGG1MK = 0x0001 F000;

PEGG1BA = 0xFEBE 00D3;

//PEGG2MK = 0x0000 0000; // no register write is required as default
values are appropriate 

//PEGG2BA = 0x0000 0000; // no register write is required as default
values are appropriate 

//PEGG3MK = 0x0000 0000; // no register write is required as default
values are appropriate 

//PEGG3BA = 0x0000 0000; // no register write is required as default
values are appropriate 

PEGSP = 0x0001; //enable PEG

#### Reference 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image2.png"
style="width:6in;height:3.58472in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image3.emf"
style="width:6in;height:4.80208in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image4.emf"
style="width:6in;height:7.17014in" />

#### Verification Method

N/A

### Guard Configuration Section: IPG Slave Guard Configuration

Return to sub-function list link:
[return](#sub-functions-in-this-document)

Provides notification of an unauthorized access to the ECM.

#### NTCs

N/A

#### SAN Linkage

**SAN-153:** The IPG function is not automatically enabled (initial
setting). If a specific protection of the mentioned peripherals is
intended, then the CPU shall set the E bit in IPGENUM while in the
supervisor mode or if write permission for user mode is set by IPGPMTUM4
register.

#### Description

This sub-function configures the RH850/P1M IPG.

#### Rationale

It is desired to allow the processor (PE) user mode read access to all
peripherals including H-bus (Flexray). In contrast, user mode write
access will be allowed only to necessary devices: P-bus groups 0 to 3
and 5 and the H Bus. The processor (PE) has been granted no user mode
execute access to any peripherals. All other IPG protected resources:
COMPTEST, INTC1, SysErrGen, and user mode access to IPG and PBG
registers are limited to read access.

This initialization must run after the startup PBG test so that the
correct values are left in the guard registers for the initial Critical
register check and for periodic operation.

Implementation

**Register Configuration Summary:**

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 22%" />
<col style="width: 51%" />
<col style="width: 5%" />
<col style="width: 5%" />
</colgroup>
<thead>
<tr class="header">
<th rowspan="2"><strong>Register</strong></th>
<th rowspan="2"><strong>Value</strong></th>
<th rowspan="2"><strong>Comments</strong></th>
<th colspan="2"><strong>Access</strong></th>
</tr>
<tr class="odd">
<th><strong>SV</strong></th>
<th><strong>UM</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IPGENUM</td>
<td><p>0x03</p>
<p>IPGENUM.IRE = 1</p>
<p>IPGENUM.E = 1</p></td>
<td>Enable storing of access violation information in IPGECRUM and
IPGADRUM and enable the peripheral device protection.</td>
<td>RW</td>
<td>*</td>
</tr>
<tr class="even">
<td>IPGPMTUM0</td>
<td><p>0x33</p>
<p>IPGPMTUM0.X1 = 0</p>
<p>IPGPMTUM0.W1 = 1</p>
<p>IPGPMTUM0.R1 = 1</p>
<p>IPGPMTUM0.X0 = 0</p>
<p>IPGPMTUM0.W0 = 1</p>
<p>IPGPMTUM0.R0 = 1</p></td>
<td>Allow user mode Read and Write access to P-bus groups 0 to 3 and 5
and to the H Bus and restrict user mode execute access to P-bus groups 0
to 3 and 5 and to the H-bus.</td>
<td>RW</td>
<td>*</td>
</tr>
<tr class="odd">
<td>IPGPMTUM2</td>
<td><p>0x11</p>
<p>IPGPMTUM2.W1 = 0</p>
<p>IPGPMTUM2.R1 = 1</p>
<p>IPGPMTUM2.W0 = 0</p>
<p>IPGPMTUM2.R0 = 1</p></td>
<td>Allow user mode read access to COMPTEST and INTC1 and restrict user
mode write access to COMPTEST and INTC1</td>
<td>RW</td>
<td>*</td>
</tr>
<tr class="even">
<td>IPGPMTUM3</td>
<td><p>0x10</p>
<p>IPGPMTUM3.W1 = 0</p>
<p>IPGPMTUM3.R1 = 1</p></td>
<td>Allow user mode read access to SysErrGen and restrict user mode
write access to SysErrGen</td>
<td>RW</td>
<td>*</td>
</tr>
<tr class="odd">
<td>IPGPMTUM4</td>
<td><p>0x01</p>
<p>IPGPMTUM4.W0 = 0</p>
<p>IPGPMTUM4.R0 = 1</p></td>
<td>Allow user mode read access to own IPG and PEG in User Mode and
restrict user mode write access to own IPG and PEG in User Mode.</td>
<td>RW</td>
<td>*</td>
</tr>
</tbody>
</table>

\* - on reset neither read nor write access is allowed in UM. Later, UM
read access is enabled by the IPG initialize setting.

##### Initialization (IpgInin)

//must be in supervisor mode to write these!

IPGPMTUM0 = 0x33; //(8 bit) initialize

IPGPMTUM2 = 0x11; //(8 bit) initialize

IPGPMTUM3 = 0x10; //(8 bit) initialize

IPGPMTUM4 = 0x01; //(8 bit) initialize

IPGENUM = 0x03; //(8 bit) initialize to enable the protections selected
above.

//it may be ok to do IPGENUM earlier but it seems safest to do it last
of IPGs

#### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image5.emf"
style="width:5.99028in;height:5.15069in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image6.emf"
style="width:6in;height:7.82986in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image7.emf"
style="width:6in;height:6.5in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image8.png"
style="width:6.00972in;height:4.35833in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image9.emf"
style="width:5.99028in;height:6.39653in" />

#### Verification Method

N/A

### Guard Configuration Section: PBG Slave Guard Configuration

Return to sub-function list link:
[return](#sub-functions-in-this-document)

Provides notification of an unauthorized access to the ECM.

#### NTCs

N/A

#### SAN Linkage

**SAN-186**: After reset, access by the bus masters is enabled.
Protection setting registers should be configured to inhibit
respectively authorize desired accesses. The PBG protection register of
each PBG channel supports a write protection function by a lock bit.
When the lock bit is set to “1”, any further write to the protection
setting register is ignored. This bit can only be cleared by reset.

The PBG protection register of each PBG channel supports a write
protection function by a lock bit (except for PBG0A) **\[Rev1.20
SAN-P1x-0410\]**. For PBG0A the customer should ensure that the guard
setting settings are not accidently changed (e.g. periodic check of the
protection setting register, MPU and so on).

#### Description

This sub-function configures the RH850/P1M PBG. The PBG provides and
restricts DMA, Flexray and PE access to peripherals.

#### Rationale

PE is being given read and write access to all peripheral groups.

WARNING: Required DMA channels’ use of peripheral interfaces were traced
via the Hardware User’s manual to PBG group and channel numbers (the
peripheral registers used by each channel is mapped to an entry in the
table in para 31.4.2). Because of this unavoidable coupling, changes to
FDD CM200A_DmaCfgAndUse_PeripheralCfg are extremely likely to require
corresponding changes here and vice versa.

| **DMA Channel** | **SRC**                   | **DST**                   | **PBG RESOURCE** | **HW Manual 31.4.2 Group** | **HW Manual 31.4.2 Channel** |
|--------|--------------|--------------|------------|-------------|-------------|
| 0               | SPI Register (CSIH1)      | Local RAM (Motor Control) | CSIH1 group B    | PBG2A                      | 11                           |
| 1               | ADC Register (ADCD0)      | Local RAM (Motor Control) | ADCD0            | PBG3A                      | 10                           |
| 2               | SPI Register (CSIH3)      | Local RAM (Motor Control) | CSIH3 group B    | PBG2A                      | 15                           |
| 3               | Local RAM (Motor Control) | TSG3 (TSG31)              | TSG31            | PBG1A                      | 8                            |
| 4               | Local RAM (Motor Control) | TSG3 (TSG31)              | TSG31            | PBG1A                      | 8                            |
| 5               | none                      | none                      | none             | unused                     | unused                       |
| 6               | none                      | none                      | none             | unused                     | unused                       |
| 7               | none                      | none                      | none             | unused                     | unused                       |
| 8               | none                      | none                      | none             | unused                     | unused                       |
| 9               | Local RAM (Motor Control) | Local RAM                 | none             | N/A                        | N/A                          |
| 10              | Local RAM (Motor Control) | SPI Register (CSIH3)      | CSIH3 group B    | PBG2A                      | 15                           |
| 12              | Local RAM (Motor Control) | SPI Register (CSIH1)      | CSIH1 group B    | PBG2A                      | 11                           |
| 14              | ADC Register (ADCD1)      | Local RAM (Motor Control) | ADCD1            | PBG3A                      | 11                           |
| 15              | Local RAM (Motor Control) | Local RAM (Motor Control) | none             | N/A                        | N/A                          |

A system controlling access by PEID, SPID was established with the
following operations allowed:

| PEID | SPID | peripheral reads | peripheral writes | RAM reads | RAM writes |
|------|------|------------------|-------------------|-----------|------------|
| 1    | 0    |                  |                   | X         | X          |
| 1    | 1    | X                | X                 |           |            |
| 1    | 2    |                  | X                 | X         |            |
| 1    | 3    | X                |                   |           | X          |

Flexray’s use of PEID (Processor Identification number) 4 means that
this PBG design grants it NO ACCESS to peripherals since both PEID and
SPID must match to get PBG access. PEID match is not required for PEGG
access so Flexray does get RAM access based on its SPID 3.

Each DMA channel must use the PEID and SPID which provides the access it
needs to perform its reads and writes. SPID 1 is reserved for the PE
only. NOTE that PE access to LRAM does not use the same access sources
as other masters so this table need not provide LRAM access to the PE.

The DMA SPIDs needed by each PBG group, channel pair were gathered from
these.

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th>PBG Group</th>
<th>PBG Channel</th>
<th>SPIDs which need access</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><table>
<colgroup>
<col style="width: 34%" />
<col style="width: 35%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th>2A</th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
<td>8</td>
<td>2</td>
</tr>
<tr class="even">
<td>2A</td>
<td>11</td>
<td>2, 3</td>
</tr>
<tr class="odd">
<td>2A</td>
<td>15</td>
<td>2, 3</td>
</tr>
<tr class="even">
<td>3A</td>
<td>10</td>
<td>3</td>
</tr>
<tr class="odd">
<td>3A</td>
<td>11</td>
<td>3</td>
</tr>
</tbody>
</table>

Adding in allowing SPID 1 to provide access to every peripheral group
for PE1, PROTUM = 1 where access during periodic update is needed,
default values for RESERVED fields, read/write controls and the use of
PEID of 1 by all DMA channels established nearly all of the values for
all of the PBG protection registers.

Further special case additions are:

PE access in user mode also occurs to PBG group, channel (0A, 1) and
(5A, 0) so these require setting UM bits of two corresponding PBG
registers. The (0A, 1) access is necessary to set up periodic DMA
operations. The (5A, 0) access is related to flash write protection. The
(5A, 0) access has been found difficult to do without but it may be
reviewed in future since it enables writing of flash in user mode.

Further requirements for user mode access for the following group,
channel pairs are:

(1B, 0) - OSTM0

(1B, 1) - OSTM1

(1B, 3) - OSTM1_CLKSEL

(2A, 7) - BIST

####  Implementation 

Note: The high order one of the two fields which Renesas calls
“Reserved” is here renamed “RESERVED0” and the low order one is renamed
“RESERVED1”.

The following fields have the same value across all FSGDxxPROTn
registers:

FSGDxxPROTn.RESERVED0 = 1 Renesas does not describe any detail of the
function of this field.

FSGDxxPROTn.PROTPEID = 0b00000010 enables only processor ID (PEID) 1
masters’ access

to this resource group

FSGDxxPROTn.RESERVED1 = 255 Renesas does not describe any detail of the
function of this field.

FSGDxxPROTn.PROTDEB = 1 enables access to a debug master

FSGDxxPROTn.PROTRDPDEF = 1 denies default read access, a master must
pass the filter and PROTRD

FSGDxxPROTn.PROTWRPDEF = 1 denies default write access, a master must
pass the filter and PROTWR

FSGDxxPROTn.PROTRD = 1 enables read access to a master which passes the
filter

FSGDxxPROTn.PROTWR = 1 enables write access to a master which passes the
filter

One field has what is ‘close’ to a constant value for all of the PBG
registers. FSGDxxPROTn.PROTLOCK has the value zero for the two registers
of the ‘0A’ group and the value one for all of the rest of the PBG
registers. FSGDxxPROTn.PROTLOCK disables writing to the register
FSGDxxPROTn. Registers FSGD0ADPROT0 and FSGD0ADPROT1 do not have this
bit. Note that this bit is zeroed by any reset source in all registers
where it appears.

The remaining field values vary from register to register. These fields
are:

FSGDxxPROTn.PROTUM enables access to a master in user mode (must match
the filter otherwise)

FSGDxxPROTn.PROTSPID specifies with a bit each, which SPIDs pass the
filter

**Register Configuration Summary:**

<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 9%" />
<col style="width: 7%" />
<col style="width: 13%" />
<col style="width: 34%" />
<col style="width: 8%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th rowspan="2"><strong><u>Register</u></strong></th>
<th rowspan="2"><strong><u>Group</u></strong></th>
<th rowspan="2"><strong><u>Channel</u></strong></th>
<th rowspan="2"><strong><u>Value</u></strong></th>
<th rowspan="2"><strong><u>Channel Specific Settings</u></strong></th>
<th colspan="2"><strong><u>Access</u></strong></th>
</tr>
<tr class="odd">
<th><strong><u>SV</u></strong></th>
<th><strong><u>UM</u></strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>FSGD0ADPROT0</td>
<td>PBG0A</td>
<td>0</td>
<td>0x0405FE5F</td>
<td>FSGD0ADPROT0.PROTUM = 0 FSGD0ADPROT0.PROTSPID = 0b0010</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>FSGD0ADPROT1</td>
<td>PBG0A</td>
<td>1</td>
<td>0x0605FE5F</td>
<td>FSGD0ADPROT1.PROTUM = 1 FSGD0ADPROT1.PROTSPID = 0b0010</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT0</td>
<td>PBG1A</td>
<td>0</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT0.PROTUM = 1 FSGD1ADPROT0.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT1</td>
<td>PBG1A</td>
<td>1</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT1.PROTUM = 1 FSGD1ADPROT1.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT2</td>
<td>PBG1A</td>
<td>2</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT2.PROTUM = 1 FSGD1ADPROT2.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT3</td>
<td>PBG1A</td>
<td>3</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT3.PROTUM = 1 FSGD1ADPROT3.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT4</td>
<td>PBG1A</td>
<td>4</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT4.PROTUM = 1 FSGD1ADPROT4.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT5</td>
<td>PBG1A</td>
<td>5</td>
<td>0x8605FE5F</td>
<td><p>FSGD1ADPROT5.PROTUM = 1</p>
<p>FSGD1ADPROT5.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT6</td>
<td>PBG1A</td>
<td>6</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT6.PROTUM = 1 FSGD1ADPROT6.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT7</td>
<td>PBG1A</td>
<td>7</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT7.PROTUM = 1 FSGD1ADPROT7.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT8</td>
<td>PBG1A</td>
<td>8</td>
<td>0x8605FEDF</td>
<td>FSGD1ADPROT8.PROTUM = 1 FSGD1ADPROT8.PROTSPID = 0b0110</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT9</td>
<td>PBG1A</td>
<td>9</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT9.PROTUM = 1 FSGD1ADPROT9.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT10</td>
<td>PBG1A</td>
<td>10</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT10.PROTUM = 1 FSGD1ADPROT10.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT11</td>
<td>PBG1A</td>
<td>11</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT11.PROTUM = 1 FSGD1ADPROT11.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT12</td>
<td>PBG1A</td>
<td>12</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT12.PROTUM = 1 FSGD1ADPROT12.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1ADPROT13</td>
<td>PBG1A</td>
<td>13</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT13.PROTUM = 1 FSGD1ADPROT13.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1ADPROT14</td>
<td>PBG1A</td>
<td>14</td>
<td>0x8605FE5F</td>
<td>FSGD1ADPROT14.PROTUM = 1 FSGD1ADPROT14.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT0</td>
<td>PBG1B</td>
<td>0</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT0.PROTUM = 1 FSGD1BDPROT0.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT1</td>
<td>PBG1B</td>
<td>1</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT1.PROTUM = 1 FSGD1BDPROT1.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT2</td>
<td>PBG1B</td>
<td>2</td>
<td>0x8405FE5F</td>
<td>FSGD1BDPROT2.PROTUM = 0 FSGD1BDPROT2.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT3</td>
<td>PBG1B</td>
<td>3</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT3.PROTUM = 1 FSGD1BDPROT3.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT4</td>
<td>PBG1B</td>
<td>4</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT4.PROTUM = 1 FSGD1BDPROT4.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT5</td>
<td>PBG1B</td>
<td>5</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT5.PROTUM = 1 FSGD1BDPROT5.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT6</td>
<td>PBG1B</td>
<td>6</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT6.PROTUM = 1 FSGD1BDPROT6.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT7</td>
<td>PBG1B</td>
<td>7</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT7.PROTUM = 1 FSGD1BDPROT7.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT8</td>
<td>PBG1B</td>
<td>8</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT8.PROTUM = 1 FSGD1BDPROT8.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT9</td>
<td>PBG1B</td>
<td>9</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT9.PROTUM = 1 FSGD1BDPROT9.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT10</td>
<td>PBG1B</td>
<td>10</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT10.PROTUM = 1 FSGD1BDPROT10.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT11</td>
<td>PBG1B</td>
<td>11</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT11.PROTUM = 1 FSGD1BDPROT11.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT12</td>
<td>PBG1B</td>
<td>12</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT12.PROTUM = 1 FSGD1BDPROT12.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD1BDPROT13</td>
<td>PBG1B</td>
<td>13</td>
<td>0x8605FE5F</td>
<td><p>FSGD1BDPROT13.PROTUM = 1</p>
<p>FSGD1BDPROT13.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD1BDPROT14</td>
<td>PBG1B</td>
<td>14</td>
<td>0x8605FE5F</td>
<td>FSGD1BDPROT14.PROTUM = 1 FSGD1BDPROT14.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT0</td>
<td>PBG2A</td>
<td>0</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT0.PROTUM = 1 FSGD2ADPROT0.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT1</td>
<td>PBG2A</td>
<td>1</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT1.PROTUM = 1 FSGD2ADPROT1.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT2</td>
<td>PBG2A</td>
<td>2</td>
<td>0x8405FE5F</td>
<td>FSGD2ADPROT2.PROTUM = 0 FSGD2ADPROT2.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT3</td>
<td>PBG2A</td>
<td>3</td>
<td>0x8405FE5F</td>
<td>FSGD2ADPROT3.PROTUM = 0 FSGD2ADPROT3.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT4</td>
<td>PBG2A</td>
<td>4</td>
<td>0x8405FE5F</td>
<td>FSGD2ADPROT4.PROTUM = 0 FSGD2ADPROT4.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT5</td>
<td>PBG2A</td>
<td>5</td>
<td>0x8405FE5F</td>
<td>FSGD2ADPROT5.PROTUM = 0 FSGD2ADPROT5.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT6</td>
<td>PBG2A</td>
<td>6</td>
<td>0x8405FE5F</td>
<td>FSGD2ADPROT6.PROTUM = 0 FSGD2ADPROT6.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT7</td>
<td>PBG2A</td>
<td>7</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT7.PROTUM = 1 FSGD2ADPROT7.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT8</td>
<td>PBG2A</td>
<td>8</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT8.PROTUM = 1 FSGD2ADPROT8.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT9</td>
<td>PBG2A</td>
<td>9</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT9.PROTUM = 1 FSGD2ADPROT9.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT10</td>
<td>PBG2A</td>
<td>10</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT10.PROTUM = 1 FSGD2ADPROT10.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT11</td>
<td>PBG2A</td>
<td>11</td>
<td>0x8605FFDF</td>
<td>FSGD2ADPROT11.PROTUM = 1 FSGD2ADPROT11.PROTSPID = 0b1110</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT12</td>
<td>PBG2A</td>
<td>12</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT12.PROTUM = 1 FSGD2ADPROT12.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT13</td>
<td>PBG2A</td>
<td>13</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT13.PROTUM = 1 FSGD2ADPROT13.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD2ADPROT14</td>
<td>PBG2A</td>
<td>14</td>
<td>0x8605FE5F</td>
<td>FSGD2ADPROT14.PROTUM = 1 FSGD2ADPROT14.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD2ADPROT15</td>
<td>PBG2A</td>
<td>15</td>
<td>0x8605FFDF</td>
<td>FSGD2ADPROT15.PROTUM = 1 FSGD2ADPROT15.PROTSPID = 0b1110</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT0</td>
<td>PBG3A</td>
<td>0</td>
<td>0x8405FE5F</td>
<td>FSGD3ADPROT0.PROTUM = 0 FSGD3ADPROT0.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT1</td>
<td>PBG3A</td>
<td>1</td>
<td>0x8405FE5F</td>
<td>FSGD3ADPROT1.PROTUM = 0 FSGD3ADPROT1.PROTSPID = 0b0010</td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT2</td>
<td>PBG3A</td>
<td>2</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT2.PROTUM = 0</p>
<p>FSGD3ADPROT2.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT3</td>
<td>PBG3A</td>
<td>3</td>
<td>0x8605FE5F</td>
<td><p>FSGD3ADPROT3.PROTUM = 1</p>
<p>FSGD3ADPROT3.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT4</td>
<td>PBG3A</td>
<td>4</td>
<td>0x8605FE5F</td>
<td><p>FSGD3ADPROT4.PROTUM = 1</p>
<p>FSGD3ADPROT4.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT5</td>
<td>PBG3A</td>
<td>5</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT5.PROTUM = 0</p>
<p>FSGD3ADPROT5.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT6</td>
<td>PBG3A</td>
<td>6</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT6.PROTUM = 0</p>
<p>FSGD3ADPROT6.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT7</td>
<td>PBG3A</td>
<td>7</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT7.PROTUM = 0</p>
<p>FSGD3ADPROT7.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT8</td>
<td>PBG3A</td>
<td>8</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT8.PROTUM = 0</p>
<p>FSGD3ADPROT8.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT9</td>
<td>PBG3A</td>
<td>9</td>
<td>0x8405FE5F</td>
<td><p>FSGD3ADPROT9.PROTUM = 0</p>
<p>FSGD3ADPROT9.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD3ADPROT10</td>
<td>PBG3A</td>
<td>10</td>
<td>0x8605FF5F</td>
<td><p>FSGD3ADPROT10.PROTUM = 1</p>
<p>FSGD3ADPROT10.PROTSPID = 0b1010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="even">
<td>FSGD3ADPROT11</td>
<td>PBG3A</td>
<td>11</td>
<td>0x8605FF5F</td>
<td><p>FSGD3ADPROT11.PROTUM = 1</p>
<p>FSGD3ADPROT11.PROTSPID = 0b1010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
<tr class="odd">
<td>FSGD5ADPROT0</td>
<td>PBG5A</td>
<td>0</td>
<td>0x8605FE5F</td>
<td><p>FSGD5ADPROT0.PROTUM = 1</p>
<p>FSGD5ADPROT0.PROTSPID = 0b0010</p></td>
<td>R/W*</td>
<td>R/W*</td>
</tr>
</tbody>
</table>

\*Also SAN-186 describes a lock bit on these registers. If the lock bit
is set there is only one write which will function until the next reset.

##### Initialization (PbgInin)

FSGD0ADPROT0 = 0x405FE5F;  
FSGD0ADPROT1 = 0x605FE5F;

FSGD1ADPROT0 = 0x8605FE5F;  
FSGD1ADPROT1 = 0x8605FE5F;  
FSGD1ADPROT2 = 0x8605FE5F;  
FSGD1ADPROT3 = 0x8605FE5F;  
FSGD1ADPROT4 = 0x8605FE5F;  
FSGD1ADPROT5 = 0x8605FE5F;  
FSGD1ADPROT6 = 0x8605FE5F;  
FSGD1ADPROT7 = 0x8605FE5F;  
FSGD1ADPROT8 = 0x8605FEDF;  
FSGD1ADPROT9 = 0x8605FE5F;  
FSGD1ADPROT10 = 0x8605FE5F;  
FSGD1ADPROT11 = 0x8605FE5F;  
FSGD1ADPROT12 = 0x8605FE5F;  
FSGD1ADPROT13 = 0x8605FE5F;  
FSGD1ADPROT14 = 0x8605FE5F;

FSGD1BDPROT0 = 0x8605FE5F;  
FSGD1BDPROT1 = 0x8605FE5F;  
FSGD1BDPROT2 = 0x8405FE5F;  
FSGD1BDPROT3 = 0x8605FE5F;  
FSGD1BDPROT4 = 0x8605FE5F;  
FSGD1BDPROT5 = 0x8605FE5F;  
FSGD1BDPROT6 = 0x8605FE5F;  
FSGD1BDPROT7 = 0x8605FE5F;  
FSGD1BDPROT8 = 0x8605FE5F;  
FSGD1BDPROT9 = 0x8605FE5F;  
FSGD1BDPROT10 = 0x8605FE5F;  
FSGD1BDPROT11 = 0x8605FE5F;  
FSGD1BDPROT12 = 0x8605FE5F;  
FSGD1BDPROT13 = 0x8605FE5F;  
FSGD1BDPROT14 = 0x8605FE5F;

FSGD2ADPROT0 = 0x8605FE5F;  
FSGD2ADPROT1 = 0x8605FE5F;  
FSGD2ADPROT2 = 0x8405FE5F;  
FSGD2ADPROT3 = 0x8405FE5F;  
FSGD2ADPROT4 = 0x8405FE5F;  
FSGD2ADPROT5 = 0x8405FE5F;  
FSGD2ADPROT6 = 0x8405FE5F;  
FSGD2ADPROT7 = 0x8605FE5F;  
FSGD2ADPROT8 = 0x8605FE5F;  
FSGD2ADPROT9 = 0x8605FE5F;  
FSGD2ADPROT10 = 0x8605FE5F;  
FSGD2ADPROT11 = 0x8605FFDF;  
FSGD2ADPROT12 = 0x8605FE5F;  
FSGD2ADPROT13 = 0x8605FE5F;  
FSGD2ADPROT14 = 0x8605FE5F;  
FSGD2ADPROT15 = 0x8605FFDF;

FSGD3ADPROT0 = 0x8405FE5F;  
FSGD3ADPROT1 = 0x8405FE5F;  
FSGD3ADPROT2 = 0x8405FE5F;  
FSGD3ADPROT3 = 0x8605FE5F;  
FSGD3ADPROT4 = 0x8605FE5F;  
FSGD3ADPROT5 = 0x8405FE5F;  
FSGD3ADPROT6 = 0x8405FE5F;  
FSGD3ADPROT7 = 0x8405FE5F;  
FSGD3ADPROT8 = 0x8405FE5F;  
FSGD3ADPROT9 = 0x8405FE5F;  
FSGD3ADPROT10 = 0x8605FF5F;  
FSGD3ADPROT11 = 0x8605FF5F;

FSGD5ADPROT0 = 0x8605FE5F;

#### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image10.emf"
style="width:6in;height:7.40034in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image11.emf"
style="width:6in;height:4.0809in" />

#### Verification Method

N/A

## Sub-Function (GuardCfgAndDiagcInit2)

Return to subfunction list: [return](#sub-functions-in-this-document)

This is an empty Initialization function that contains no logic.

> GuardCfgAndDiagcInit2 is an RTE function which is required for memory
> mapping PIM and Calibration definitions.

## Sub-Function: (GuardCfgAndDiagcInit3)

Return to sub-function list link:
[return](#sub-functions-in-this-document)

### NTCs

N/A

### SAN Linkage

Ver 1.20 SAN-P1x-0403:

4.5.2 Failure Control The logic of the peripheral bus guard for each
group is targeted by LBIST. For the PBG3A group, the SW test described
in the subsequent section shall be additionally executed to increase the
DC with respect to latent faults and to cover the error signal path to
ECM \[SAN-P1x-0407\].

4.5.3.1 A SW test at start-up shall be executed for PBG3A (can be
optionally performed for other peripheral guard groups) by forcibly
violating the access permission attributes such as access with wrong
address or write attempt when no write permission is set.

4.5.3.2 SW Test Procedure In order to test the peripheral guard of group
3A, the flow given in Figure 4.5-3 shall be followed. In this flow each
Filter within the guard is associated with a target module (such as
ADCD0 etc..) of group 3A.

29.1 The LBIST checks all error signal paths from the modules to the ECM
that are themselves targeted by the LBIST except the error signal paths
from the DMA compare unit, the PBG3A, and from OR-gate for data parity.
For these items, countermeasures are already described in the dedicated
chapters in this document.

### Description

This sub-function performs a test that the PBG guard is functional. In
particular, it verifies that the signal path which reports each of
twelve PBG group 3A members read and write violations to the ECM. These
are not tested by the BIST so it is a shortfall reported by the SAN.

### Rationale

This test must be run before the PBG is initialized so that it does not
overwrite the initialization values needed during execution of periodic
functions. At this time the PBG registers are accessible. Also, PBG
critical register monitoring (initial) must occur after the PBG has been
set up for periodic running, not per the SAN PBG startup test.

This test is one of a group that will be run after some subset of all
types of resets has occurred. By convention, all of these tests are
always entered and each calls a function (ChkForStrtUpTest) which
determines whether the test should perform its test or trivially return.

The design doesn’t match the SAN flowchart for several reasons:

1.  The SAN flowchart tests only that the error is seen at the
    ERRSLVxxSTAT register. This does not accomplish the goal of
    verifying the signal path from the PBG3A module to the ECM per
    section 29.1 of the SAN. The design verifies that the error is
    caught in the ERRSLVxxSTAT register in addition to reaching
    ECMMESSTR0 which confirms the functional path to the ECM.

2.  The SAN flowchart details testing one “access” while looping through
    the 12 PBG 3A sections, then branches back to the beginning if both
    read and write tests have not been completed. The design tests read
    and then write of each of the 12 sections in turn verifying that
    both access types cause error signals to reach ERRSLVxxSTAT and the
    ECM.

3.  The SAN flowchart leaves each PBG 3A register with a value that
    allows reading and writing. The design stores the entry value of
    each PBG 3A register before testing it and restores that value
    before exiting.

4.  The SAN flowchart does not address the impact of this error’s drive
    to the SYSERR function. Because of this, the SEGCONT register must
    have two bits cleared during testing to prevent SYSERR exceptions.
    Similarly, the driving of the ERROROUT pin must be masked off from
    the error signals which will occur during the test. These must be
    restored before the test returns.

5.  The SAN flowchart has ignored the reality that the test must access
    regions protected by the PBG 3A registers that are not the same data
    length/type. The design has addressed this code-level matter.

### Implementation

The test loops through all twelve sections of the PBG 3A group. The
sections where the targets register is 8, 16 or 32 bits have been
grouped and are tested in group order. Each pass of the test loop in the
functions which handle 8, 16 or 32 bits ones verifies that first a read
access, then a write access records a violation at the group 3A error
status register and at the ECM level in bit 26 of ECMMESSTR0. The PBG
protection registers and their corresponding test targets are listed in
the following tables:

| Index | 8 Bit Register              |
|-------|-----------------------------|
| 0     | PBGFSGD3ADPROT0,DNFA0CTL    |
| 1     | PBGFSGD3ADPROT1,PORTJJPIBC0 |
| 2     | PBGFSGD3ADPROT5,FCLA0CTL0   |
| 3     | PBGFSGD3ADPROT6,FCLA1CTL0   |
| 4     | PBGFSGD3ADPROT7,FCLA2CTL0   |
| 5     | PBGFSGD3ADPROT8,FCLA3CTL0   |
| 6     | PBGFSGD3ADPROT9,FCLA4CTL0   |
| 7     | PBGFSGD3ADPROT10,ADCD0THACR |
| 8     | PBGFSGD3ADPROT11,ADCD1THACR |
|       |                             |

| Index | 16 Bit Register          |
|-------|--------------------------|
| 0     | PBGFSGD3ADPROT3,PORTPMC0 |

| Index | 32 Bit Register              |
|-------|------------------------------|
| 0     | PBGFSGD3ADPROT2,PORTJJPCR0_0 |
| 1     | PBGFSGD3ADPROT4,PORTPCR0_0   |

Any error detected during testing is recorded using the function
SetMcuDiagcIdnData  with a first parameter value
McuDiagc1.MCUDIAGC_PBGSTRTUPTST. Further information is encoded into a
second parameter according to the following table:

| **ECM Failure** | **PBG Failure** | **Configure Failure**    | **Write Error** | **Read Error** |
|-------------|-------------|--------------------|---------------|--------------|
| **Bit 10**      | **Bit 9**       | **Bit 8**                | **Bit 7**       | **Bit 6**      |
| 1 - ECM Error   | 1 - PBG Error   | 1 - Configuration Failed | 1 - Write Error | 1 - Read Error |
| 0 - No Error    | 0 - No Error    | 0 - No Error             | 0 - No Error    | 0 - No Error   |
|                 |                 |                          |                 |                |

| **Register Size** |           | **Index**                                                             |           |           |           |
|-----------|-----------|-------------|-------------|-------------|-------------|
| **Bit 5**         | **Bit 4** | **Bit 3**                                                             | **Bit 2** | **Bit 1** | **Bit 0** |
| 00 - 8 Bit Reg    |           | Taken from the appropriate length register table “Index” field above. |           |           |           |
| 01 - 16 Bit Reg   |           |                                                                       |           |           |           |
| 10 - 32 Bit Reg   |           |                                                                       |           |           |           |

All other bits of the second parameter are zero. The only exception to
this encoding is when an error is found flagged in register
PBGERRSLV3ASTAT before testing has begun. In this case, the second
parameter is set to all ones.

NOTE: Renesas has not documented that the SEGFLAG bits function is
upstream of SEGCONT. That is, in this case the SEGFLAG.VCIF and VCPF
will be set by this test’s generation of PBG3A violations even though
the SEGCONT.VCIE and VCPE, having been set to zero, prevent the signal
from causing any SYSERR reset. This is addressed in the design by
clearing SEGFLAG.VCIF and VCPF before setting SEGCONT.VCIE and VCPE
after all test loops have completed.

ANOTHER NOTE: The pseudocode below includes a commented off post-test
check for most of the syserr generating exceptions that had to be
blocked during the test. Once unit testing has confirmed that these are
not being tripped it is thought that the check is not of value in the
production executable code. There are some Syserr generating exceptions
that had to be blocked during the test which can not be captured in any
way. For a reference on the errors which may escape – see the function
of the VCIE bit in the SEGCONT register.

THIRD NOTE: This code writes to and reads from SEG registers SEGCONT and
SEGFLAG. These are protected by IPG (guard) bits. The current IPG
settings elsewhere in this FDD allow reading but cause writing to be a
guard violation. To avoid this, this test must run before the guard is
initialized by GuardCfgAndDiagcInit. This ordering is controlled
elsewhere.

#### Initialization

extrn void ChkForStrtUpTest (Boolean\* ExecStrtUpTest);

//configure, read back and set error code if it doesn’t verify

//”Configure Nth Filter” in the SAN Flowchart

static void ConfigureFilterN( uint32_t\* volatile PbgProtReg, uint32
value, uint32\* TestFailStsPtr)

{

\* PbgProtReg = value; //write to PbgProt register

if (value != \* PbgProtReg)

\*TestFailStsPtr \|= (uint32)(1\<\<8); //pass an error code -
configuration

}

//check that the error showed up, clear/verify the error, and set error
code if needed

static void ChkForPBGErr(Uint32 PbgProtReg, uint32\* TestFailStsPtr)

{

if (0 == (PBGERRSLV3ASTAT & 1)) // ERRSLV3ASTAT

{

\*TestFailStsPtr \|= ( 1\<\<9) ; //pass an error code - PBG level

}

else

{

PBGERRSLV3ACTL = 1; //clear error bit by write to ERRSLV3ACTL

if (0 != (PBGERRSLV3ASTAT & 1)) // ERRSLV3ASTAT

\*TestFailStsPtr \|= (1\<\<9 ) ; //pass an error code - PBG level

}

}

//check that the error showed up at the ECM, clear/verify the error, and
set error code if needed

static void ChkForECMErr ( Uint32 PbgProtReg, uint32\* TestFailStsPtr)

{

// test that the data got to the ECM

if (0 == (ECMESSTR0 & (1\<\<26)))

\*TestFailStsPtr \|= (1\<\<10) ; //error code ECM

// clear the ECM bit

WrProtdRegEcm_u32 (1\<\<26, &ECMESSTC0);

if (0 != (ECMMESSTR0 & (1\<\<26) ))

\*TestFailStsPtr \|= (1\<\<10); //error code ECM

}

static void testPbg8BitTargets(uint32\* TestFailStsPtr)

{

typedef struct

{

uint32\* PbgProtnReg;

uint8\* PortReg;

}PbgTestRec;

PbgTestRec PbgTestRecAry\[9\]=

{

{&PBGFSGD3ADPROT0,&DNFA0CTL},

{&PBGFSGD3ADPROT1,&PORTJJPIBC0},

{&PBGFSGD3ADPROT5,&FCLA0CTL0},

{&PBGFSGD3ADPROT6,&FCLA1CTL0},

{&PBGFSGD3ADPROT7,&FCLA2CTL0},

{&PBGFSGD3ADPROT8,&FCLA3CTL0},

{&PBGFSGD3ADPROT9,&FCLA4CTL0},

{&PBGFSGD3ADPROT10,&ADCD0THACR},

{&PBGFSGD3ADPROT11,&ADCD1THACR}

};

uint32\* PbgProtnReg;

uint8\* PortReg;

uint8 volatile Bucket;

uint32 SavePbgProtReg;

uint8_t LoopCntr = 0U;

while ( LoopCntr \< 9U && (0 == (\*TestFailStsPtr)) )

{

PbgProtnReg = PbgTestRecAry\[LoopCntr\].PbgProtnReg;

PortReg = PbgTestRecAry\[LoopCntr\].PortReg;

SavePbgProtReg = \* PbgProtnReg;

// NO ACCESS PERMISSION 0x405FE5C

ConfigureFilterN( PbgProtnReg, 0x405FE5C, TestFailStsPtr);

//read from the port, should generate error

Bucket = \*PortReg;

ChkForPBGErr(TestFailStsPtr);

ChkForECMErr(TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<6;

else

{

// write to the port, should generate error

\*PortReg = Bucket;

ChkForPBGErr(TestFailStsPtr);

ChkForECMErr(TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<7;

}

// Restore PBG register value

ConfigureFilterN( PbgProtnReg, SavePbgProtReg, TestFailStsPtr);

LoopCntr++;

}

if ( 0 \< (\* TestFailStsPtr))

\*PbgStrtUpTestFailSts \|= ( 0U \<\< 4) \| //\[4:5\] 0B 🡪 8 bit

(uint32)(LoopCntr -1U); //index into 8 bit list

}

} // testPbg8BitTargets

static void testPbg16BitTargets(uint32\* TestFailStsPtr)

{

typedef struct

{

uint32\* PbgProtnReg;

uint16\* PortReg;

}PbgTestRec;

PbgTestRec PbgTestRecAry\[1\]=

{

{&PBGFSGD3ADPROT3,&PORTPMC0}

};

uint32\* PbgProtnReg;

uint16\* PortReg;

uint16 volatile Bucket;

uint32 SavePbgProtReg;

uint8 LoopCntr = 0;

// while ( LoopCntr \< ?U && (0 == (\*TestFailStsPtr)) ) // if more of
these are added

{

PbgProtnReg = PbgTestRecAry\[LoopCntr\].PbgProtnReg;

PortReg = PbgTestRecAry\[LoopCntr\].PortReg;

SavePbgProtReg = \* PbgProtnReg;

// NO ACCESS PERMISSION 0x405FE5C

ConfigureFilterN( PbgProtnReg, 0x405FE5C, TestFailStsPtr);

//read from the port, should generate error

Bucket = \*PortReg;

ChkForPBGErr( TestFailStsPtr);

ChkForECMErr( TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<6;

else

{

// write to the port, should generate error

\*PortReg = Bucket;

ChkForPBGErr(TestFailStsPtr);

ChkForECMErr(TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<7;

}

// Restore PBG register value

ConfigureFilterN( PbgProtnReg, SavePbgProtReg, TestFailStsPtr);

LoopCntr++;

}

if ( 0 \< (\* TestFailStsPtr))

\*PbgStrtUpTestFailSts \|= ((uint32)1U\<\<4U) \| //\[4:5\] 01B 🡪 16 bit

(uint32)(LoopCntr -1U); //index into 16 bit list

} // testPbg16BitTargets

static void testPbg32BitTargets( uint32\* TestFailStsPtr)

{

typedef struct

{

uint32\* PbgProtnReg;

uint32\* PortReg;

}PbgTestRec;

PbgTestRec PbgTestRecAry\[2\]=

{

{&PBGFSGD3ADPROT2,&PORTJJPCR0_0},

{&PBGFSGD3ADPROT4,&PORTPCR0_0}

};

uint32\* PbgProtnReg;

uint32\* PortReg;

uint32 volatile Bucket;

uint32 SavePbgProtReg;

uint8 LoopCntr;

while ( LoopCntr \< 2U && (0 == (\*TestFailStsPtr)) )

{

PbgProtnReg = PbgTestRecAry\[LoopCntr\].PbgProtnReg;

PortReg = PbgTestRecAry\[LoopCntr\].PortReg;

SavePbgProtReg = \* PbgProtnReg;

// NO ACCESS PERMISSION 0x405FE5C

ConfigureFilterN( PbgProtnReg, 0x405FE5C, TestFailStsPtr);

//read from the port, should generate error

Bucket = \*PortReg;

ChkForPBGErr( TestFailStsPtr);

ChkForECMErr( TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<6;

else

{

// write to the port, should generate error

\*PortReg = Bucket;

ChkForPBGErr( TestFailStsPtr);

ChkForECMErr( TestFailStsPtr);

if ( 0 \< (\*TestFailStsPtr) )

\*TestFailStsPtr \|= 1\<\<7;

}

// Restore PBG register value

ConfigureFilterN( PbgProtnReg, SavePbgProtReg, TestFailStsPtr);

LoopCntr++;

}

if ( 0 \< (\* TestFailStsPtr))

\*PbgStrtUpTestFailSts \|= ((uint32)1U\<\<5U) \| // \[4:5\] 10B 🡪 32 bit

(uint32)(LoopCntr -1U); //index into 32 bit list

} // testPbg32BitTargets

// this code assumes that the ECM has NOT been configured to generate
exceptions or

// interrupts on PBG error detection. It DOES assume that SYSERR occurs
on PBG violation

// detection is configured so this code briefly disables that but
restores it before returning.

// run this test in Supervisor mode!!!!

void **GuardCfgAndDiagcInit3** ( void )

{

uint32\* volatile testPeripheralAddr; // peripheral test address

uint32 erroroutPinMaskSave = ECMEMK0;

uint32 savePbgProtectionReg;

uint32 saveSegCont = SEGCONT;

uint32 TestFailSts = 0;

Boolean ExecStrtUpTest;

ChkForStrtUpTest ( &ExecStrtUpTest);

if ( (true == ExecStrtUpTest) && (0 == (PBGERRSLV3ASTAT & 1)) && (0 ==
(ECMESSTR0 & (1\<\<26))) )

{

// set BIT26 to prevent (mask off) test induced PBG error from getting
to the ERROROUT pin

WrProtdRegEcm_u32 ( erroroutPinMaskSave\| (1 \<\< 26), &ECMEMK0);

// the following line requires Supervisor mode!!!!

SEGCONT.VCIE = 0; // turn off syserr response to several VCIE things

SEGCONT.VPGE = 0; // turn off syserr response to PBG write violation

asm(“syncm”); //ensure the written value has settled

testPbg8BitTargets( &TestFailSts);

if ( 0 == TestFailSts)

testPbg16BitTargets( &TestFailSts );

if ( 0 == TestFailSts)

testPbg32BitTargets( &TestFailSts );

// Cleanup

SEGFLAG.VPGF = 0; // clear VPGF, this gets set despite VPGE being 0

SEGFLAG.VCIF = 0; // clear VCIF, this gets set despite VCIE being 0

SEGCONT = SaveSegCont; // restore entry SEGCONT content

//check that this test didn’t generate errors other than the intended

// ones in bit 26 while VCIE was zeroed.

// 0x1003 8000 checks for bus data parity error bit 28

// (DTSRAM, DF, CF ) 2bit ECC errors or CF address parity bits 15, 16,
17

//if ( (\*ECMMESSTR0) & 0x1003 8000 )

// DoSyserr();

// restore the mask to the ERROROUT pin

WrProtdRegEcm_u32 ( erroroutPinMaskSave, &ECMEMK0);

}

else if (true == ExecStrtUpTest)

{

TestFailSts = 0xFFFFFFFFU;

}

else {}

if (TestFailSts)

SetMcuDiagcIdnData ( McuDiagc1.MCUDIAGC_PBGSTRTUPTST*,*

TestFailSts); //pass an error code

} //end of the function

### Reference 

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image12.emf"
style="width:6.5in;height:6.29236in" />

Figure 4.5.3 from SAN ver 1.20

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image13.emf"
style="width:6in;height:4.69845in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image14.emf"
style="width:6in;height:7.30617in" /> <img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image15.emf"
style="width:6in;height:1.79567in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image16.emf"
style="width:6in;height:3.8609in" /> <img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image17.emf"
style="width:6in;height:3.79701in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image18.emf"
style="width:6in;height:6.91616in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image19.emf"
style="width:6in;height:4.12603in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image20.emf"
style="width:6in;height:6.5817in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image21.emf"
style="width:6in;height:6.83095in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image22.emf"
style="width:6in;height:5.43098in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image23.emf"
style="width:6in;height:6.13941in" /><img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM107A_GuardCfgAndDiagc_Design/Design/mediax/media/image24.emf"
style="width:6in;height:4.60202in" />

### Verification Method

N/A

# Revision Record & Change Approval

|          |           |                       |         |                                                                                                                                                                                                                                                                                                                                   |
|--------|----------|----------|-------|--------------------------------------|
| **Rev**  | **Date**  | **Change Control \#** | **Drw** | **Change Description**                                                                                                                                                                                                                                                                                                            |
| 01.00.00 | 06AU15    | EA4#1822              | EC      | Initial Release                                                                                                                                                                                                                                                                                                                   |
| 01.01.00 | 22OC15    | EA4#1822              | EC      | Update from Integration adds user mode to four PBG chan.                                                                                                                                                                                                                                                                          |
| 02.00.00 | 10Feb16   | EA4#2752              | EC      | Removed some references to PBG lock bits, add startup PBG 3A test, added references to SAN Ver 1.20, made PBG group 0A group critical registers’ monitoring periodic, added detail about H-bus (flexray) access rights to peripherals and RAM related to Anomaly EA4#3071.                                                        |
| 02.01.00 | 24Feb16   | EA4#2752              | EC      | Changed one PBG target register where HWUM had identified the wrong PBG protection set, corrected lengths of some PBG target registers, revised pseudocode to more literally align with SAN flowchart and to align with coding standards                                                                                          |
| 03.00.00 | 28Mar2016 | EA4#4975              | EC      | Update PBG values and rationale to incorporate the ‘protlock’ lock bits and the correct Flexray SPID now documented by HWUM 1.10 DTD Feb 2016. Add time delay to pseudo code in the area where Renesas advises it is needed beyond the areas documented in the HWUM. Added check on ECM reg to Renesas recommended pretest check. |
| 03.00.01 | 05Apr2016 | EA4#4975              | GM      | Removed AND condition for else if statement under GuardCfgAndDiagcInit3 implementation                                                                                                                                                                                                                                            |
|          |           |                       |         |                                                                                                                                                                                                                                                                                                                                   |

{% endraw %}