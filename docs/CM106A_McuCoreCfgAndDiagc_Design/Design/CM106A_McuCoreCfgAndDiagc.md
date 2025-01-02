---
layout: default
title: CM106A_McuCoreCfgAndDiagc
nav_order: 1
parent: Component Design
---
{% raw %}
**Microcontroller Core Configuration**

**And**

**Diagnostics**

**CM106A**

[1. High Level Description 5](#high-level-description)

[2. Sub-Function In This Document 5](#sub-function-in-this-document)

[3. Critical Registers 6](#critical-registers)

[4. Sub-functions 6](#sub-functions)

[4.1. Sub-Function: BIST Failure Analysis
6](#sub-function-bist-failure-analysis)

[4.1.1. NTCs 6](#ntcs)

[4.1.2. SAN Linkage 6](#san-linkage)

[4.1.3. Description 6](#description)

[4.1.4. Rationale 14](#rationale)

[4.1.5. Implementation 14](#implementation)

[4.1.6. Verification Method 15](#verification-method)

[4.2. Sub-Function: CPU/DMA Lock Step Error Forcing Startup Test Failure
15](#sub-function-cpudma-lock-step-error-forcing-startup-test-failure)

[4.2.1. NTCs 15](#ntcs-1)

[4.2.2. SAN Linkage 15](#san-linkage-1)

[4.2.3. Description 16](#description-1)

[4.2.4. Rationale 20](#rationale-1)

[4.2.5. Implementation 21](#implementation-1)

[4.2.6. Verification Method 23](#verification-method-1)

[5. Revision Record & Change Approval
23](#revision-record-change-approval)

# High Level Description

This document describes start up test procedures related to BIST and
LockStep.

This MCU provides a BIST (build-in-Self-Test) function that is mainly
intended to detect latent faults within the parts which are used as a
safety mechanism. The BIST, termed field BIST, consists of LBIST
(Logical BIST) and MBIST (Memory BIST). The LBIST scans all flip flops
of the target modules and checks if the signature matches the expected
one. The result of the field BIST after its execution is stored in
BSEQ0ST register. Its initial setting indicates that the field BIST is
not passed and can only be replaced by the correct result if the field
BIST is executed and no error has been detected.

Lockstep Dual Core (LSDC) for PE (Processor Element):

A redundant Processor Element is implemented based on Lockstep Dual Core
(LSDC) architecture containing Master PE, Checker PE and the related
compare unit. Both PEs have identical inputs and perform the same
processing operations.

The lockstep mode is automatically enabled and cannot be disabled by
software. The Checker PE is delayed by two clocks to mitigate dependent
faults resulting from power supply or clock disturbances. The Master PE,
Checker PE and the related compare unit are target of the LBIST.

Lockstep Dual Core (LSDC) for DMA:

This MCU embodies a redundant Direct Memory Access (DMA Master and
Checker). As in the case of LSDC for PE, all inputs to the DMA checker
are delayed by two clocks and the outputs from the DMA Master and
Checker are compared by the related compare unit. Thus failures within
the DMA Master are detected by the compare unit. The lockstep mode is
automatically enabled and cannot be disabled by software.

# Sub-Function In This Document

Below is a linked list of all sub-functions owned by this document.

|                                                      |          |
|------------------------------------------------------|----------|
| **Sub-Function Name**                                | **Link** |
| BIST Failure Analysis                                | 4.1      |
| CPU/DMA Lock Step Error Forcing Startup Test Failure | 4.2      |

# Critical Registers

<table>
<colgroup>
<col style="width: 11%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 12%" />
<col style="width: 14%" />
<col style="width: 10%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Register</strong></td>
<td><p><strong>Register No.</strong></p>
<p><strong>(regID, selID)</strong></p></td>
<td><strong>Access Permission</strong></td>
<td><p><strong>Init / Periodic</strong></p>
<p><strong>Verification</strong></p></td>
<td><strong>Masking</strong></td>
<td><strong>Expected Value</strong></td>
<td><strong>Protn Score From Eval Sheet</strong></td>
</tr>
<tr class="even">
<td>OPBT0</td>
<td>N/A</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0x7F8F FFFB</td>
<td>1</td>
</tr>
<tr class="odd">
<td>OPBT2</td>
<td>N/A</td>
<td><p>SV – R/W</p>
<p>UM – R/W</p></td>
<td>Init</td>
<td>None</td>
<td>0xBFFF FFFF</td>
<td>1</td>
</tr>
</tbody>
</table>

# Sub-functions

## Sub-Function: BIST Failure Analysis

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

**SAN-1082:**

In case an ECC error during the transfer of the Field BIST parameters to
the Field BIST controller has occurred, an error signal will be issued
to ECM. In that case operation **shall** not be entered.

**SAN-1080:**

The result of the field BIST **shall** be checked before executing any
safety related application program. The execution of the Field BIST
**shall** not be disabled in order to detect latent faults of the
targeted parts.

### Description

This sub-function checks if an ECC 2-bit error has been detected during
the transfer of the Field BIST parameters to the Field BIST controller
during BIST execution.

This sub-function checks if the execution of MCU Field BIST completed
successfully. If the execution of the BIST is not completed, the result
of LBIST and MBIST cannot be checked.

This sub-function checks the results of MBIST (Memory BIST) and LBIST
(Logic BIST) when execution of BIST is completed successfully.

Register Info:

|                                                              |                                                                                                                |                     |        |
|---------------------|-------------------------------|-----------|----------|
| **Register**                                                 | **Use**                                                                                                        | **Register Access** |        |
|                                                              |                                                                                                                | **SV**              | **UM** |
| BSEQ0CTL (Field BIST Control Register)                       | Controls the execution of BIST after reset release                                                             | R/W                 | R/W    |
| ECMPE1 (ECM Pseudo Error Trigger Register 1)                 | Used to generate a pseudo error for test purposes                                                              | R/W                 | R/W    |
| ECMMESSTR1 (ECM Master Error Source Status Register 1)       | Indicates the state of individual internal error sources, which is irrelevant to the setting of the error mask | R/W                 | R/W    |
| ECMCESSTR1 (ECM Checker Error Source Status Register 1)      | Indicates the state of individual internal error sources, which is irrelevant to the setting of the error mask | R/W                 | R/W    |
| ECMESSTC1 (ECM Error Source Status Clear Trigger Register 1) | Used to clear the individual error source status of the ECM master/checker error source status register 1      | R/W                 | R/W    |
| BSEQ0ST (BIST Error Status Register)                         | Register holds the error status of field BIST                                                                  | R/W                 | R/W    |
| BSEQ0STB (BIST Error Status Inversion Register)              | Register holds the inverse of the bits of the BSEQ0ST register                                                 | R/W                 | R/W    |
| MBISTREF (Memory BIST Signature Register)                    | Register holds the expected value when memory BIST is executed.                                                | R/W                 | R/W    |
| MBISTSIG (Memory BIST Signature Result Register)             | Register holds the result value of memory BIST execution.                                                      | R/W                 | R/W    |
| LBISTREF1 (Logic BIST signature register 1)                  | Register holds the expected value when logic BIST1 is executed.                                                | R/W                 | R/W    |
| LBISTSIG1 (Logic BIST Signature Result Register 1)           | Register holds the result value of logic BIST1 execution.                                                      | R/W                 | R/W    |
| LBISTREF2 (Logic BIST signature register 2)                  | Register holds the expected value when logic BIST2 is executed.                                                | R/W                 | R/W    |
| LBISTSIG2 (Logic BIST Signature Result Register 2)           | Register holds the result value of logic BIST2 execution.                                                      | R/W                 | R/W    |

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image1.png"
style="width:6.49514in;height:5.94306in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image2.png"
style="width:6.49097in;height:7.15069in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image3.png"
style="width:6.49792in;height:7.72014in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image4.png"
style="width:6.49097in;height:7.29722in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image5.png"
style="width:6.49306in;height:5.18889in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image6.png"
style="width:6.49722in;height:4.91944in" />

### Rationale

BSEQ0CTL controls the execution of field BIST after reset release. This
register is only initialized by POCRES, CVMRES or DBRES.

Run BIST only on POCRES. So, write the bit BSEQ0CTL.HWBISTEXE = 0 to
disable BIST from running on EXTRES or ECM Reset. This test has been
excluded it from other types of resets to reduce start up time. SAN
mentions that we only need to perform this test once only on POR. It is
acceptable to not run BIST on CVM reset because the system will go to a
safe state in that case.

When BSEQ0CTL.HWBISTEXE is set to 1, BIST is executed at a pin reset
(EXTRES) or ECM reset (ECMRES). FieldBIST is not executed regardless of
the HWBISTEXE value at SWRES.

Single bit ECC faults in BIST are detected and corrected by the
Hardware.

The value of ECMMESSTR1 after a reset at cold start is 0000 0000H.
Design assumes that the ECMMESSTR1 register will indicate a BIST 2 bit
ECC failure. Single bit ECC errors are not described in this
sub-function.

### Implementation

#### Initialization (McuCoreCfgAndDiagcInit1)

<u>Pseudo Code:</u>

// Only perform test if the following resets have occurred:

// Power On Reset when not in debug mode

GetMcuDiagcIdnData( Address of McuDiagData0);

If (McuDiagData0 == McuDiagc1.MCUDIAGC_PWRONRST)

{

> // Check if the chip is in Debug Mode
>
> If ((SYSDEBUGMODE == 0) OR (SYSDEBUGMODEB == 1))
>
> {
>
> // Check if 1Bit or 2Bit ECC Error occurred during BIST execution
>
> If ((ECMMSSE108 == 1) OR (ECMCSSE108 == 1) OR
>
> (ECMMSSE109 == 1) OR (ECMCSSE109 == 1))
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_BISTECCERR, 0);
>
> }
>
> Else
>
> {
>
> //Check if Both Registers indicate BIST execution has NOT completed
> successfully
>
> If ((SYSBIST_RESULT != 02) AND (SYSBIST_RESULTB != 05))
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_BISTNOTCMPLERR, 0);
>
> }
>
> // At least one Register indicates BIST Completed Successfully
>
> Else
>
> {
>
> // Check if there were any errors during LBIST execution
>
> If (SYSLBISTSIG1 != LBISTSIG1) OR (SYSLBISTSIG2 != LBISTSIG2))
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_LOGLBISTERR, 0);
>
> }
>
> Else
>
> {
>
> // Check if there were any errors during MBIST execution
>
> If (SYSMBISTSIG != MBISTSIG)
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_MEMBISTERR, 0);
>
> }
>
> }
>
> }
>
> }
>
> }

}

#### Event Driven

N/A

#### Periodic

N/A

### Verification Method

N/A

## Sub-Function: CPU/DMA Lock Step Error Forcing Startup Test Failure

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

**SAN-62:**

It is possible to perform a functional test of the compare unit by fault
injection. This optional test **can** be executed at start-up.

**SAN-109,110:**

The LSDC self-test **shall** be executed by writing to the mentioned
register to forcibly cause a compare error:

111111_11111111_00000111_00001111 to DMACMPERR together with the PROT
bit in the PDMA_COMP_CNTRL register. Writing this value will generate an
error that is flagged as compare error in the ECM.

### Description

This sub-function is responsible for performing a diagnostic check that
the CPU and DMA controller lock step error detection mechanism of the
MCU is working correctly.

Register Info:

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 44%" />
<col style="width: 14%" />
<col style="width: 13%" />
</colgroup>
<tbody>
<tr class="odd">
<td rowspan="2"><strong>Register</strong></td>
<td rowspan="2"><strong>Use</strong></td>
<td colspan="2"><strong>Register Access</strong></td>
</tr>
<tr class="even">
<td><strong>SV</strong></td>
<td><strong>UM</strong></td>
</tr>
<tr class="odd">
<td>ECMEMK0 (ECM Error Mask Register 0)</td>
<td>Used to mask the individual error sources of the ERROROUT
output.</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>ECMIRCFG0 (ECM Internal Reset Configuration Register 0)</td>
<td><p>Used to set the generation of internal resets</p>
<p>(ECMRES) in response to internal errors</p></td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="odd">
<td>ECMESSTC0 (ECM Error Source Status Clear Trigger Register 0)</td>
<td>Used to clear the individual error source status of the ECM
master/checker error source status register 0</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>ECMMESSTR0 (ECM Master Error Source Status Register 0)</td>
<td>Indicates the state of individual internal error sources, which is
irrelevant to the setting of the error mask</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="odd">
<td>ECMCESSTR0 (ECM Checker Error Source Status Register 0)</td>
<td>Indicates the state of individual internal error sources, which is
irrelevant to the setting of the error mask</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>PDMA_COMP_CNTRL (DMA Control Register)</td>
<td>Can control the output signals on the checker side of the DMAC</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="odd">
<td>TESTCOMPREG0 (Comparator Test Register 0)</td>
<td>Used for the lockstep function of the CPU1. Combining TESTCOMPREG1
with TESTCOMPREG0 enables self-diagnosis of the lockstep function</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>TESTCOMPREG1 (Comparator Test Register 1)</td>
<td>Used for the lockstep function of the CPU1. Combining TESTCOMPREG1
with TESTCOMPREG0 enables self-diagnosis of the lockstep function</td>
<td>R/W</td>
<td>R/W</td>
</tr>
</tbody>
</table>

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image7.png"
style="width:6.49375in;height:7.81597in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image8.png"
style="width:6.49167in;height:7.90208in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image9.png"
style="width:6.49167in;height:7.80278in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM106A_McuCoreCfgAndDiagc_Design/Design/mediax/media/image10.png"
style="width:6.49167in;height:7.75in" />

### Rationale

After a reset is released and before the lockstep errors are enabled in
the ECM, registers in the master and the slave Processor Elements should
match. Otherwise, we could end up with a lockstep fault.

Some registers are ‘undefined’ following a reset, meaning it is likely
that the master PE and the checker PE registers will contain different
values. Master and slave registers should be initialized by the software
to avoid having different values. The application software needs to only
write to the master PE registers explicitly; the checker PE will reflect
those writes.

Uninitialized registers are assumed to be initialized with their
suggested initial values in the Bootloader.

We skip the startup test if a core compare fault already occurred
because the startup sequence does a check on all the status bits at
MCUinit() and notifies a CPU/DMA LockStep error. If an error is already
present and we are notified of it, there is no need to perform another
startup test to recreate the situation.

### Implementation

#### Initialization (McuCoreCfgAndDiagcInit2)

<u>Psuedo Code:</u>

// Only perform test if the following resets have occurred:

// Power On Reset, Flash Programming Complete, Soft Rest or Hard Reset

ChkForStrtUpTest (Address of ExecStrtUpTest);

If (ExecStrtUpTest == TRUE)

{

> // Check if the chip is in Debug Mode
>
> If ((SYSDEBUGMODE == 0) OR (SYSDEBUGMODEB == 1))
>
> {
>
> // Check if a DMA or CPU Lockstep compare fault has already occurred
>
> If ((ECMMSSE001 == 0) AND (ECMCSSE001 == 0))
>
> {
>
> // Save contents of ECMEMK0 and ECMIRCFG0 to a temp variable in RAM
>
> ECMEMK0_Temp = ECMEMK0;
>
> ECMMICFG0_Temp = ECMMICFG0;
>
> ECMNMICFG0_Temp = ECMNMICFG0;
>
> ECMIRCFG0_Temp = ECMIRCFG0;
>
> // Mask the Error Source 1, NMI Interrupt and MI Interrupt of the
> ECMmESSTR0
>
> ECMEMK0_Desired = ECMEMK0 \| 0x0000 0002;
>
> ECMMICFG0_Desired = ECMMICFG0 & \~ (0x0000 0002);
>
> ECMNMICFG0_Desired = ECMNMICFG0 & \~ (0x0000 0002);
>
> ECMIRCFG0_Desired = ECMIRCFG0 & \~ (0x0000 0002);
>
> WrProtdRegEcm_u32 (ECMEMK0_Desired, Address of ECMEMK0);
>
> WrProtdRegEcm_u32 (ECMMICFG0_Desired, Address of ECMMICFG0);
>
> WrProtdRegEcm_u32 (ECMNMICFG0_Desired, Address of ECMNMICFG0);
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Desired, Address of ECMIRCFG0);
>
> // Inject Fault to cause a DMA Lockstep Error
>
> PDMACOMPPDMA_COMP_CNTRL = 0xBFFF070F;
>
> // Wait until read from the TESTCOMPREG0 is complete to trigger the
> fault
>
> \_\_asm ("SYNCM");
>
> // Check if the DMA Lockstep fault was notified
>
> If ((ECMMSSE001 == 0) OR (ECMCSSE001 == 0)
>
> {
>
> // DMA Lockstep test failed
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_DMALOCKSTEPERR, 0);
>
> }
>
> Else
>
> {
>
> // Clear Notification
>
> ECMESSTC0_Desired = 0x0000 0002;
>
> WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);
>
> // Inject Fault to cause a CPU Lockstep Error
>
> TESTCOMPREG0 = 0x11111111;
>
> TESTCOMPREG1 = 0X22222222;
>
> // According to SAN, a Read is required to induce a CPU Lockstep Fault
>
> CoreCompTestRegRead = TESTCOMPREG0;
>
> // Wait until read from the TESTCOMPREG0 is complete to trigger the
> fault
>
> \_\_asm ("SYNCM");
>
> // Check if the CPU Lockstep fault was notified
>
> If ((ECMMSSE001 == 0) OR (ECMCSSE001 == 0))
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_CPULOCKSTEPERR, 0);
>
> }
>
> }
>
> // Clear Notification
>
> ECMESSTC0_Desired = 0x0000 0002;
>
> WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);
>
> // Restore the contents of the ECMEMK0 and EMCIRCFG0 register
>
> WrProtdRegEcm_u32 (ECMEMK0_Temp, Address of ECMEMK0);
>
> WrProtdRegEcm_u32 (ECMMICFG0\_ Temp, Address of ECMMICFG0);
>
> WrProtdRegEcm_u32 (ECMNMICFG0\_ Temp, Address of ECMNMICFG0);
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Temp, Address of ECMIRCFG0);
>
> }

}

}

#### Initialization (McuCoreCfgAndDiagcInit3)

This is an empty Initialization function that contains no logic.

McuCoreCfgAndDiagcInit3 is an RTE function which is required for memory
mapping PIM and Calibration definitions.

#### Event Driven

N/A

#### Periodic

N/A

### Verification Method

N/A

# Revision Record & Change Approval

|          |            |                       |         |                                                                                                                                                                                      |
|--------|----------|----------|-------|-------------------------------------|
| **Rev**  | **Date**   | **Change Control \#** | **Drw** | **Change Description**                                                                                                                                                               |
| 01.00.00 | 10/21/2015 | EA4#1736              | SK      | Initial Release                                                                                                                                                                      |
| 02.00.00 | 02/11/2016 | EA4#3810              | SK      | Replaced GetMcuDiagcData with ChkForStrtUpTest to check for startup test condition                                                                                                   |
| 02.01.00 | 03/29/2016 | EA4#5047              | EC      | Remove unnecessary syncms per latest Renesas guidance, handle 1 bit ECC Error during MBIST same as 2 bit, remove ChkForStrtUpTest and added check for McuDiagcData for poweron reset |
| 2.2.0    | 04/04/2016 | EA4#5047              | GM      | Added syncms that were removed in previous revision                                                                                                                                  |
| 2.2.1    | 04/05/2016 | EA4#5047              | GM      | Change BIST2BITERR to BISTECCERR in BIST Failure Analysis sub-function implementation                                                                                                |
|          |            |                       |         |                                                                                                                                                                                      |

{% endraw %}