---
layout: default
title: CM101A_ExcpnHndlg
nav_order: 1
parent: Component Design
---
{% raw %}
**Exception Handling**

**(ExcpnHndlg)**

**FDD CM101A**

[1. High Level Description 6](#high-level-description)

[2. Sub-Functions In This Document 8](#sub-functions-in-this-document)

[3. Critical Register Verification References
9](#critical-register-verification-references)

[4. Sub-functions 10](#sub-functions)

[4.1. Sub-Function: Exception Handling Configuration
10](#sub-function-exception-handling-configuration)

[4.1.1. NTCs 10](#ntcs)

[4.1.2. SAN Linkage 10](#san-linkage)

[4.1.3. Description 10](#description)

[4.1.4. Rationale 10](#rationale)

[4.1.5. Implementation 10](#implementation)

[4.1.6. Reference 12](#reference)

[4.1.7. Diagnostic Verification Method
13](#diagnostic-verification-method)

[4.2. Sub-Function: Exception Handling Routine SYSERR
14](#sub-function-exception-handling-routine-syserr)

[4.2.1. NTCs 14](#ntcs-1)

[4.2.2. SAN Linkage 14](#san-linkage-1)

[4.2.3. Description 14](#description-1)

[4.2.4. Rationale 14](#rationale-1)

[4.2.5. Implementation 15](#implementation-1)

[4.2.6. Reference 17](#reference-1)

[4.2.7. Verification Method 20](#verification-method)

[4.3. Sub-Function: Exception Handling Routine Floating Point
20](#sub-function-exception-handling-routine-floating-point)

[4.3.1. NTCs 20](#ntcs-2)

[4.3.2. SAN Linkage 20](#san-linkage-2)

[4.3.3. Description 20](#description-2)

[4.3.4. Rationale 20](#rationale-2)

[4.3.5. Implementation 20](#implementation-2)

[4.3.6. Reference 22](#reference-2)

[4.3.7. Verification Method 24](#verification-method-1)

[4.4. Sub-Function: Exception Handling Routine Misalignment
25](#sub-function-exception-handling-routine-misalignment)

[4.4.1. NTCs 25](#ntcs-3)

[4.4.2. SAN Linkage 25](#san-linkage-3)

[4.4.3. Description 25](#description-3)

[4.4.4. Rationale 25](#rationale-3)

[4.4.5. Implementation 25](#implementation-3)

[4.4.6. Reference 26](#reference-3)

[4.4.7. Verification Method 27](#verification-method-2)

[4.5. Sub-Function: Exception Handling Routine Reserved Instruction
28](#sub-function-exception-handling-routine-reserved-instruction)

[4.5.1. NTCs 28](#ntcs-4)

[4.5.2. SAN Linkage 28](#san-linkage-4)

[4.5.3. Description 28](#description-4)

[4.5.4. Rationale 28](#rationale-4)

[4.5.5. Implementation 28](#implementation-4)

[4.5.6. Verification Method 28](#verification-method-3)

[4.6. Sub-Function: Server Routine FENMI PEG
29](#sub-function-server-routine-fenmi-peg)

[4.6.1. NTCs 29](#ntcs-5)

[4.6.2. SAN Linkage 29](#san-linkage-5)

[4.6.3. Description 29](#description-5)

[4.6.4. Rationale 29](#rationale-5)

[4.6.5. Implementation 29](#implementation-5)

[4.6.6. Verification Method 29](#verification-method-4)

[4.7. Sub-Function: Server Routine FENMI SPI 2 Bit ECC Error
30](#__RefHeading___Toc445994432)

[4.7.1. NTCs 30](#__RefHeading___Toc445994433)

[4.7.2. SAN Linkage 30](#__RefHeading___Toc445994434)

[4.7.3. Description 30](#__RefHeading___Toc445994435)

[4.7.4. Rationale 30](#__RefHeading___Toc445994436)

[4.7.5. Implementation 30](#__RefHeading___Toc445994437)

[4.7.6. Reference 32](#__RefHeading___Toc445994438)

[4.7.7. Verification Method 34](#__RefHeading___Toc445994439)

[4.8. Sub-Function: Server Routine FENMI DMA Transfer Error
35](#sub-function-server-routine-fenmi-dma-transfer-error)

[4.8.1. NTCs 35](#ntcs-6)

[4.8.2. SAN Linkage 35](#san-linkage-6)

[4.8.3. Description 35](#description-6)

[4.8.4. Rationale 35](#rationale-6)

[4.8.5. Implementation 35](#implementation-6)

[4.8.6. Reference 36](#reference-4)

[4.8.7. Verification Method 36](#verification-method-5)

[4.9. Sub-Function: Server Routine FENMI DMA Access Violation Error
37](#sub-function-server-routine-fenmi-dma-access-violation-error)

[4.9.1. NTCs 37](#ntcs-7)

[4.9.2. SAN Linkage 37](#san-linkage-7)

[4.9.3. Description 37](#description-7)

[4.9.4. Rationale 37](#rationale-7)

[4.9.5. Implementation 37](#implementation-7)

[4.9.6. Reference 38](#reference-5)

[4.9.7. Verification Method 38](#verification-method-6)

[4.10. Sub-Function: Server Routine FENMI ECM Master/Checker Compare
39](#sub-function-server-routine-fenmi-ecm-masterchecker-compare)

[4.10.1. NTCs 39](#ntcs-8)

[4.10.2. SAN Linkage 39](#san-linkage-8)

[4.10.3. Description 39](#description-8)

[4.10.4. Rationale 39](#rationale-8)

[4.10.5. Implementation 39](#implementation-8)

[4.10.6. Verification Method 39](#verification-method-7)

[4.11. Sub-Function: Server Routine FENMI Watchdog
40](#sub-function-server-routine-fenmi-watchdog)

[4.11.1. NTCs 40](#ntcs-9)

[4.11.2. SAN Linkage 40](#san-linkage-9)

[4.11.3. Description 40](#description-9)

[4.11.4. Rationale 40](#rationale-9)

[4.11.5. Implementation 40](#implementation-9)

[4.11.6. Verification Method 41](#verification-method-8)

[4.12. Sub-Function: FENMI Clock Monitor 0 RunTime Lower Limit Fault
42](#sub-function-fenmi-clock-monitor-0-runtime-lower-limit-fault)

[4.12.1. NTCs 42](#ntcs-10)

[4.12.2. SAN Linkage 42](#san-linkage-10)

[4.12.3. Description 42](#description-10)

[4.12.4. Rationale 42](#rationale-10)

[4.12.5. Implementation 42](#implementation-10)

[4.12.1. Verification Method 42](#verification-method-9)

[4.13. Sub-Function: FENMI Clock Monitor 0 RunTime Upper Limit Fault
42](#sub-function-fenmi-clock-monitor-0-runtime-upper-limit-fault)

[4.13.1. NTCs 42](#ntcs-11)

[4.13.2. SAN Linkage 42](#san-linkage-11)

[4.13.1. Description 43](#description-11)

[4.13.2. Rationale 43](#rationale-11)

[4.13.3. Implementation 43](#implementation-11)

[4.13.4. Verification Method 43](#verification-method-10)

[4.14. Sub-Function: FENMI Clock Monitor 1 RunTime Lower Limit Fault
43](#sub-function-fenmi-clock-monitor-1-runtime-lower-limit-fault)

[4.14.1. NTCs 43](#ntcs-12)

[4.14.2. SAN Linkage 43](#san-linkage-12)

[4.14.1. Description 43](#description-12)

[4.14.2. Rationale 43](#rationale-12)

[4.14.3. Implementation 44](#implementation-12)

[4.14.4. Verification Method 44](#verification-method-11)

[4.15. Sub-Function: FENMI Clock Monitor 1 RunTime Upper Limit Fault
44](#sub-function-fenmi-clock-monitor-1-runtime-upper-limit-fault)

[4.15.1. NTCs 44](#ntcs-13)

[4.15.2. SAN Linkage 44](#san-linkage-13)

[4.15.3. Description 44](#description-13)

[4.15.4. Rationale 44](#rationale-13)

[4.15.5. Implementation 44](#implementation-13)

[4.15.6. Verification Method 45](#verification-method-12)

[4.16. Sub-Function: FENMI Clock Monitor 2 RunTime Lower Limit Fault
45](#sub-function-fenmi-clock-monitor-2-runtime-lower-limit-fault)

[4.16.1. NTCs 45](#ntcs-14)

[4.16.2. SAN Linkage 45](#san-linkage-14)

[4.16.3. Description 45](#description-14)

[4.16.4. Rationale 45](#rationale-14)

[4.16.5. Implementation 45](#implementation-14)

[4.16.6. Verification Method 45](#verification-method-13)

[4.17. Sub-Function: FENMI Clock Monitor 2 RunTime Upper Limit Fault
45](#sub-function-fenmi-clock-monitor-2-runtime-upper-limit-fault)

[4.17.1. NTCs 45](#ntcs-15)

[4.17.2. SAN Linkage 45](#san-linkage-15)

[4.17.3. Description 46](#description-15)

[4.17.4. Rationale 46](#rationale-15)

[4.17.5. Implementation 46](#implementation-15)

[4.17.6. Verification Method 46](#verification-method-14)

[4.18. Sub-Function: FENMI Clock Monitor 3 RunTime Lower Limit Fault
46](#sub-function-fenmi-clock-monitor-3-runtime-lower-limit-fault)

[4.18.1. NTCs 46](#ntcs-16)

[4.18.2. SAN Linkage 46](#san-linkage-16)

[4.18.3. Description 46](#description-16)

[4.18.4. Rationale 46](#rationale-16)

[4.18.5. Implementation 47](#implementation-16)

[4.18.6. Verification Method 47](#verification-method-15)

[4.19. Sub-Function: FENMI Clock Monitor 3 RunTime Upper Limit Fault
47](#sub-function-fenmi-clock-monitor-3-runtime-upper-limit-fault)

[4.19.1. NTCs 47](#ntcs-17)

[4.19.2. SAN Linkage 47](#san-linkage-17)

[4.19.3. Description 47](#description-17)

[4.19.4. Rationale 47](#rationale-17)

[4.19.5. Implementation 47](#implementation-17)

[4.19.6. Verification Method 48](#verification-method-16)

[4.20. Sub Function: Server Routine Process Unknown Exception Error
48](#sub-function-server-routine-process-unknown-exception-error)

[4.20.1. NTCs 48](#ntcs-21)

[4.20.2. SAN Linkage 48](#san-linkage-21)

[4.20.3. Description 48](#description-21)

[4.20.4. Rationale 48](#rationale-21)

[4.20.5. Implementation 48](#implementation-21)

[4.20.6. Verification Method 48](#verification-method-20)

[4.21. Sub-Function: Server Routine Process Memory Protection Unit
Exception Error
49](#sub-function-server-routine-process-memory-protection-unit-exception-error)

[4.21.1. NTCs 49](#ntcs-22)

[4.21.2. SAN Linkage 49](#san-linkage-22)

[4.21.3. Description 49](#description-22)

[4.21.4. Rationale 49](#rationale-22)

[4.21.5. Implementation 49](#implementation-22)

[4.21.6. Verification Method 49](#verification-method-21)

[4.22. Sub-Function: Server Routine Process Privileged Instruction
Exception Error
49](#sub-function-server-routine-process-privileged-instruction-exception-error)

[4.22.1. NTCs 49](#ntcs-23)

[4.22.2. SAN Linkage 49](#san-linkage-23)

[4.22.3. Description 49](#description-23)

[4.22.4. Rationale 50](#rationale-23)

[4.22.5. Implementation 50](#implementation-23)

[4.22.6. Verification Method 50](#verification-method-22)

[4.23. Sub-Function: Server Routine Process Permanent Os Error
50](#sub-function-server-routine-process-permanent-os-error)

[4.23.1. NTCs 50](#ntcs-24)

[4.23.2. SAN Linkage 50](#san-linkage-24)

[4.23.3. Description 50](#description-24)

[4.23.4. Rationale 50](#rationale-24)

[4.23.5. Implementation 50](#implementation-24)

[4.23.6. Verification Method 50](#verification-method-23)

[4.24. Sub-Function: Server Routine Process Non Critical Os Error
50](#sub-function-server-routine-process-non-critical-os-error)

[4.24.1. NTCs 50](#ntcs-25)

[4.24.2. SAN Linkage 50](#san-linkage-25)

[4.24.3. Description 51](#description-25)

[4.24.4. Rationale 51](#rationale-25)

[4.24.5. Implementation 51](#implementation-25)

[4.24.6. Verification Method 51](#verification-method-24)

[4.24.7. Periodic (ExcpnHndlgPer1) 51](#periodic-excpnhndlgper1)

[4.24.8. Verification Method 51](#verification-method-25)

[4.25. Sub-Function: Server Routine Shutdown Hook
52](#sub-function-server-routine-shutdown-hook)

[4.26. Sub-Function: Exception Handling Routine EIINT
52](#sub-function-exception-handling-routine-eiint)

[4.27. Sub-Function: Reset Source Determination
53](#sub-function-reset-source-determination)

[4.27.1. NTCs 53](#ntcs-26)

[4.27.2. SAN Linkage 54](#san-linkage-26)

[4.27.3. Description 54](#description-26)

[4.27.4. Rationale 54](#rationale-26)

[4.27.5. Implementation 55](#implementation-26)

[4.27.6. Verification Method 61](#verification-method-26)

[5. Special Functions 61](#special-functions)

[6. Revision Record & Change Approval
63](#revision-record-change-approval)

# High Level Description

This document describes the exception handling / reset cause
determination for microcontroller diagnostics. Note that the MCU handler
is in place to parse / identify FE and EI exception sources (of the 43
shown). The MCU will call server functions in this FDD for FE type
interrupts. EI based interrupts will call server functions directly to
the FDD.

Additionally, any pre-OS type failures that are detected are “saved”
using backup RAM until the reset cause functionality is performed. The
reset cause algorithm uses the backup RAM (modified by both Exceptions
and pre-OS start up tests) to set appropriate fault codes. For this FDD,
NTCs are only set in the reset cause function.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image1.wmf)

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image2.wmf)

# Sub-Functions In This Document

Below is a linked list of all sub-functions owned by this document.

|                                                                |                                   |
|----------------------------------------------------|--------------------|
| **Sub-Function Name**                                          | **Link**                          |
| Exception Handling Configuration                               | 4.1                               |
| Exception Handling Routine SYSERR                              | 4.2                               |
| Exception Handling Routine Floating Point                      | 4.3                               |
| Exception Handling Routine Misalignment                        | 4.4                               |
| Exception Handling Routine Reserved Instruction                | 4.5                               |
| Server Routine FENMI PEG                                       | 4.6                               |
| Server Routine FENMI SPI 2 Bit ECC                             | Error: Reference source not found |
| Server Routine FENMI DMA Transfer Error                        | 4.7                               |
| Server Routine FENMI DMA Access Violation Error                | 4.8                               |
| Server Routine FENMI Master Checker Compare                    | 4.9                               |
| Server Routine FENMI Watchdog                                  | 4.10                              |
| Server Routine FENMI DTS Double Bit ECC                        | 4.11                              |
| Server Routine FENMI Clock Monitor 0 RunTime Lower Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 0 RunTime Upper Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 1 RunTime Lower Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 1 RunTime Upper Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 2 RunTime Lower Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 2 RunTime Upper Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 3 RunTime Lower Limit Fault |                                   |
| Server Routine FENMI Clock Monitor 3 RunTime Upper Limit Fault |                                   |
| Server Routine FENMI Unknown                                   | Error: Reference source not found |
| Server Routine Protection Hook                                 | Error: Reference source not found |
| Server Routine Error Hook                                      | 4.23                              |
| Server Routine Shutdown Hook                                   | 4.27                              |
| Exception Handling Routine EIINT                               | Error: Reference source not found |
| Reset Source Determination                                     | 4.29                              |

# Critical Register Verification References

This table contains the information needed for critical register
verification as configured or used in this document.

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
<td>FPCFG</td>
<td>SR10, 0</td>
<td>CU0</td>
<td>Init</td>
<td>None</td>
<td>0x0000 001C</td>
<td>0</td>
</tr>
</tbody>
</table>

# Sub-functions

## Sub-Function: Exception Handling Configuration

Return to sub-function list link: Sub-Functions In This Document

### NTCs

NA

### SAN Linkage

**SAN-49:** After reset the generation of SYSERR exception request due
to the errors shown in the Error notification Control Register (SEGCONT)
is disabled. This notification **can** be enabled by setting the related
bits accordingly.

**SAN-263:** Generation of SYSERR exception in case of uncorrectable
error (e.g. DED, Address parity) during instruction fetch cannot be
masked for instruction fetch unit in SEGCONT. However, such errors
**shall** be always handled by ECM within DTI.

**SAN-278:** Transition to the safe state **shall** take place when an
ECC 2-bit error, or an overflow error has occurred. For this purpose,
the ECM **shall** be configured accordingly.

**SAN-342:** Transition the MCU and the system to the safe state
**shall** take place when an address parity error has occurred. For this
purpose, the ECM shall be configured accordingly.

**SAN-401:** Transition to the safe state **shall** take place when
2-bits error, an error count overflow or an address error has been
detected. For this purpose, configure the appropriate response in the
ECM accordingly.

**SAN-413:** Upon detection of non-correctable bit error in the local
RAM, a system error exception request will be sent to SEG to generate a
SYSERR (FE-level) exception (if it is enabled).

### Description

This sub-function configures or identifies the exception handling
characteristics for the RH850 related to microcontroller diagnostics.

### Rationale

The Nexteer approach planned for exception handling involves two types –
those serious errors that will be handled by forcing a software reset of
the microcontroller and those that do not. This sub-function is intended
to show the list of exceptions and highlight those that will be
configured to be a system error (SYSERR) via the use of the SEGCONT
register. Floating point exceptions must also be configured.

Exception Handler assumes that the MCAL will configure the CVMREN
register to cause a reset when the CVM Fails.

### Implementation

#### Initialization (ExcpnHndlgInit1)

Register Configuration Summary

<table>
<colgroup>
<col style="width: 23%" />
<col style="width: 33%" />
<col style="width: 26%" />
<col style="width: 8%" />
<col style="width: 8%" />
</colgroup>
<tbody>
<tr class="odd">
<td rowspan="2"><strong>Register</strong></td>
<td rowspan="2"><strong>Value</strong></td>
<td rowspan="2"><strong>Comments</strong></td>
<td colspan="2"><strong>Access</strong></td>
</tr>
<tr class="even">
<td><strong>SV</strong></td>
<td><strong>UM</strong></td>
</tr>
<tr class="odd">
<td>FPCFG (Floating-point operation configuration)</td>
<td><p>FPCFG.XE.V = 1 (Validity)</p>
<p>FPCFG.XE.Z = 1 (Divide by Zero)</p>
<p>FPCFG.XE.O = 1 (Overflow)</p>
<p>FPCFG.XE.U = 0 (Underflow)</p>
<p>FPCFG.XE.I = 0 (Imprecise)</p></td>
<td>Only addresses configuring the exception bits</td>
<td>R/W</td>
<td>R/W</td>
</tr>
<tr class="even">
<td>* SYSCVMDEW (CVM Detection Enable Register)</td>
<td>SYSCVMDEW. CVMDIAGMEW = 0</td>
<td><p>Enable CVM Diagnosis</p>
<p><strong>NOTE: This is a protected register. Can only be written to
once.</strong></p></td>
<td>R/W</td>
<td>R/W</td>
</tr>
</tbody>
</table>

\*Denotes that no direct write is required as the default value meets
the requirement.

NOTE: MCU configuration has a checkbox selection for the self-test –
consider this in the future design.

// Configure floating point <u>exceptions</u> – note that other FPU
configuration is done in the FBL

FPCFG = 0x0000 001C

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image3.wmf"
style="width:5.99931in;height:7.65903in" />

FPSR (See boot loader CM110A for configuration function):

<u>Bits 31 to 24:</u> Status bits – NA for configuration – initialize to
zero

<u>Bit 23</u>: FN Flush to Nearest: recommend setting this bit to 1 –
along with the FS (Flush Subnormal) bit set to 1 and the RM bits set to
RN (round to nearest) , this setting will cause subnormal numbers to be
flushed to either zero or +/- the smallest magnitude normal number,
whichever is closer to the subnormal result – essentially rounds the
subnormal result rather than flushing to zero always. (See FS setting
for EA3 comparison)

<u>Bit 22</u>: IF: status bit – NA for configuration – initialize to
zero

<u>Bit 21</u>: PEM: recommend setting to 0 – for imprecise floating
point exceptions. This does not allow resuming execution after the
exception handler, which is ok since the expected design is to cause a
reset. Precise exceptions would allow resuming execution but causes
slower operation (different pipelining to allow for precise exceptions).

<u>Bit 20</u>: Reserved: must write a 0

<u>Bits 19 and 18</u>: RM, rounding mode, recommend setting is 00 for RN
round to nearest. This matches the setting used in EA3.

<u>Bit 17</u>: FS flush subnormal – recommend setting this bit to 1 to
enable flush subnormal. This is the default setting of this bit. The
floating point coprocessor does not have hardware processing of
subnormal numbers; therefore if FS is disabled, any subnormal operand or
result causes an exception so that software processing can occur;
recommend flush subnormal for throughput optimization. NOTE that this
differs from the EA3 setting. The EA3 processor has hardware support for
subnormal number processing and we do not flush subnormal numbers; not
flushing is the default setting for the EA3 processor.

<u>Bit 16</u>: reserved: must write a 0

<u>Bits 15 to 10:</u> Status bits – NA for configuration – initialize to
zero

<u>Bits 9 to 5</u>: Exception enable bits: recommend setting as in EA3
FDD (although no EA3 program has turned these settings on yet)

Bit 9 – V – invalid operation – set to 1 to enable exception

Bit 8 – Z – divide by zero – set to 1 to enable exception

Bit 7 – O – overflow – set to 1 to enable exception

Bit 6 – U – underflow – set to 0 to disable exception

Bit 5 – I – inexact – set to 0 to disable exception

<u>Bits 4 to 0:</u> Status bits – NA for configuration – initialize to
zero

### Diagnostic Verification Method

NA as this is a configuration sub-function

## Sub-Function: Exception Handling Routine SYSERR

Return to sub-function list link: <u>Sub-Functions In This Document</u>

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-166:** If SYSERR exception is generated, a reset of the device
**shall** be issued.

**SAN-263:** Generation of SYSERR exception in case of uncorrectable
error (e.g. DED, Address parity) during instruction fetch cannot be
masked for instruction fetch unit in SEGCONT. However, such errors
**shall** be always handled by ECM within DTI.

**SAN-278:** Transition to the safe state **shall** take place when an
ECC 2-bit error, or an overflow error has occurred. For this purpose,
the ECM **shall** be configured accordingly.

**SAN-342:** Transition the MCU and the system to the safe state shall
take place when an address parity error has occurred. For this purpose,
the ECM shall be configured accordingly.

**SAN-343:** In case an address parity error has occurred, a system
error (SYSERR) exception will be generated. This exception is
terminating and a reset from the ECM or from the pin becomes necessary.

**SAN-401:** Transition to the safe state shall take place when 2-bits
error, an error count overflow or an address error has been detected.
For this purpose, configure the appropriate response in the ECM
accordingly.

**SAN-413:** Upon detection of non-correctable bit error in the local
RAM, a system error exception request will be sent to SEG to generate a
SYSERR (FE-level) exception (if it is enabled).

**SAN-P1x-0703:**

In case ECC 1-bit error has occurred, a CRC test \[SAN-P1x-0703\] shall
be executed to check whether or not the error is due single bit or
multi-bit corruption that is potentially caused by address decoder
failure.

**SAN-P1x-1307:**

In case an ECC 2-bit has occurred, the related flag will set in DTSER2
register and an internal error signal will be generated towards ECM to
take proper action. Moreover, the handling of the DMA transfer request
is terminated without executing a DMA cycle and TI write back. In that
case the MCU shall be moved into safe state unless the application has
implemented further measures to allow the operation to continue.

### Description

This sub-function handles the SYSERR exceptions (after the RBASE / EBASE
Switch - refer to start up sequence).

Note that some errors are configured to generate a SYSERR based on the
contents of the SEGCONT register (see CM110A for details). The design
stores information into back up registers, generates a software reset
and then the “Reset Source Determination” sub-function identifies the
source of the reset and identifies the NTC.

SYSERRs occurring <u>prior</u> to the RTE initialization will result in
an interrupt restarting the FBL.

### Rationale

SYSERR approach was selected over ECM as it seems to be a more direct
response in cases of serious failures. Note that the ECM error out pin
is also configured to go the safe state as another redundant disabling
mechanism; however, no EI or FE interrupts are configured as enabled.

Design assumes that if none of the SEGFLAG bits are set, then the
assumption is an instruction fetch failure.

R7F701311 has 128KB of RAM with a Base address of 0xFEB8 0000 and the
Offset starting at 0x0006 0000.

If TCMF flag was set due to uncorrectable ECC error to local RAM or due
to an access to RAM-unimplemented area, it can be determined which
source caused the error by looking at the local RAM 1st error status
register LR1STERSTR_PE1 flags. If any of the status flags are set in
this register then TCMF setting was due to ECC error, otherwise TCMF
setting was due to access to RAM-unimplemented area.

Because VCIE is configured to trigger a SYSERR (corresponding bit in
SEGCONT = 1), all peripheral data bus parity errors will cause a SYSERR.
 SYSERR handling must include a software reset -- it is not possible to
return from a SYSERR interrupt.  Therefore, the Nexteer design responds
to all peripheral data bus parity errors, regardless of which peripheral
they occur on, by pulling the ERROROUT pin low (through an ECM
configuration), setting a reset cause, and performing a software reset;
after the reset, the reset cause will be used to set an NTC.  Since the
reset must happen due to the SYSERR handling, there is no benefit in
checking the 40-some peripheral registers to determine whether the error
occurred on a safety-critical or non-critical peripheral.

The NTC Master List has 2 separate NTCs for safety-critical and
non-critical peripheral registers. We choose to implement only the NTC
for safety-critical peripheral for the reason mentioned above and not to
differentiate between the peripherals.

SAN states “In case ECC 1-bit error has occurred, a CRC test
\[SAN-P1x-0703\] shall be executed to check whether or not the error is
due single bit or multi-bit corruption that is potentially caused by
address decoder failure.” Nexteer does not perform any CRC calculation
on code flash at run time. We disable single bit ECC correction on code
flash. Therefore we configure the code flash single bit ECC as a SYSERR
through VCIF.

Reasons:

-   Cannot differentiate code flash ECC and address decoder failure.

-   More work needs to be done on DTS channel usage before using DTS to
    calculate CRC at run time.

-   Excessive bus load at run time

### Implementation

The SYSERR exception has an offset of 0x010.

#### Event Driven (SysErrIrq)

Registers used

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 43%" />
<col style="width: 11%" />
<col style="width: 11%" />
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
<td>SEGFLAG (Error Occurrence Retention Register)</td>
<td>Contains bits to indicate the source of the system error.</td>
<td>R/W</td>
<td><p>Read</p>
<p>Only</p></td>
</tr>
<tr class="even">
<td>SEGADDR (Error Address)</td>
<td>Contains the error address information that caused the system
error.</td>
<td>R/W</td>
<td><p>Read</p>
<p>Only</p></td>
</tr>
<tr class="odd">
<td>CF1STEADR0_PE1 (Code Flash 1st Error Address Register)</td>
<td>Register provides information on address of failure – used for debug
purposes</td>
<td>R/W</td>
<td>R/W</td>
</tr>
</tbody>
</table>

*TmpData* = 0

// Determine source of error from the SEGFLAG bits and indicate in
BRAMDAT0

If (SEGVPGF = 1) Then

*TmpSrc* = McuDiagc1.MCUDIAGC_PRPHLBUSGUARD

ElseIf (SEGVCRF = 1) Then

*TmpSrc* = McuDiagc1.MCUDIAGC_INTPRPHLGUARD

ElseIf (SEGTCMF = 1) Then

// Identify bank that failed to get address information from the correct
register

> If (ECCCPU1DEDF0 = 1) Then
>
> // TmpData is the Offset Address of Local RAM ‘OR’ed with Base Addr
> (0xFEB8 0000) and Bank Addr (0x0)

*TmpData* = ((ECCCPU1LR1STEADR0_PE1 \<\< 4) \| 0xFEB8 0000)

> *TmpSrc* = McuDiagc1.MCUDIAGC_LCLRAMDBLBIT

Else If (ECCCPU1DEDF1 = 1)

> // TmpData is the Offset Address of Local RAM ‘OR’ed with Base Addr
> (0xFEB8 0000) and Bank Addr (0x4)
>
> *TmpData* = ((ECCCPU1LR1STEADR1_PE1 \<\< 4) \| 0xFEB8 0004)
>
> *TmpSrc* = McuDiagc1.MCUDIAGC_LCLRAMDBLBIT
>
> Else If (ECCCPU1DEDF2 = 1)
>
> // TmpData is the Offset Address of Local RAM ‘OR’ed with Base Addr
> (0xFEB8 0000) and Bank Addr (0x8)
>
> *TmpData* = ((ECCCPU1LR1STEADR2_PE1 \<\< 4) \| 0xFEB8 0008)
>
> *TmpSrc* = McuDiagc1.MCUDIAGC_LCLRAMDBLBIT
>
> Else If (ECCCPU1DEDF3 = 1)
>
> // TmpData is the Offset Address of Local RAM ‘OR’ed with Base Addr
> (0xFEB8 0000) and Bank Addr (0xC)
>
> *TmpData* = ((ECCCPU1LR1STEADR3_PE1 \<\< 4) \| 0xFEB8 000C)
>
> *TmpSrc* = McuDiagc1.MCUDIAGC_LCLRAMDBLBIT
>
> Else
>
> // Else TCMF setting was due to access to RAM-unimplemented area.
>
> *TmpSrc* = McuDiagc1.MCUDIAGC_INVLDRAMAREA
>
> EndIf

ElseIf ((SEGROMF = 1) or (SEGVCIF = 1)) Then // Both bits have code
flash ECC

If (ECCFLICF1STERSTR_PE1 & 0x0000 0004 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_ADRPAR

*TmpData* = ECCFLICF1STEADR0_PE1

Else If (ECCFLICF1STERSTR_PE1 & 0x0000 0002 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_CODFLSDBLBIT

*TmpData* = ECCFLICF1STEADR0_PE1

Else If (ECCFLICF1STERSTR_PE1 & 0x0000 0001 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_CODFLSECCSNGBITERR

*TmpData* = ECCFLICF1STEADR0_PE1

Else If (ECCFLICF1STERSTR_VCI & 0x0000 0004 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_ADRPAR

*TmpData* = ECCFLICF1STEADR0_VCI

Else If (ECCFLICF1STERSTR_VCI & 0x0000 0002 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_CODFLSDBLBIT

*TmpData* = ECCFLICF1STEADR0_VCI

Else If (ECCFLICF1STERSTR_VCI & 0x0000 0001 !=0) Then

> *TmpSrc* = McuDiagc1.MCUDIAGC_CODFLSECCSNGBITERR

*TmpData* = ECCFLICF1STEADR0_VCI Else If (ECMMESSTR0 & 0x1000 0000 != 0)

> *TmpSrc* = McuDiagc1.MCUDIAGC_PRPHLBUSDATAPAR

Else If (DMASSDTSER2 & 0x8000 0000 != 0)

> *TmpSrc* = McuDiagc1. MCUDIAGC_DTSDBLBIT
>
> *TmpData =* DMASSDTSER2

Else

> // Other VCIE cause
>
> *TmpSrc* = McuDiagc1.MCUDIAGC_VCIE

End If

Else

// Assume instruction fetch error drove SYSERR

*TmpSrc* = McuDiagc1.MCUDIAGC_INSTRFETCH

End If

NxtrSwRstFromExcpn (*TmpSrc, TmpData*)

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image4.wmf"
style="width:5.98889in;height:4.79861in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image5.wmf"
style="width:5.99306in;height:3.86319in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image6.wmf"
style="width:5.97361in;height:6.75in" />

### Verification Method

**<u>At 2ms rate:</u>**

// Invokes a double bit ECC code flash fault

If ((McuDiagcTest = McuDiagcTestTyp.CODFLSDBLBIT)

> Temp = Read from Code Flash Test Address 0x0100 A8B0 // invokes a
> double bit ECC

McuDiagcTest = McuDiagcTestTyp.NoTest

EndIf

**// Check on section 8.4.2 in SAN for address parity fault injection
options**

**// Need to find other ways to invoke a SYSERR**

## Sub-Function: Exception Handling Routine Floating Point

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None identified

### Description

This sub-function is used to handle the exceptions configured for the
floating point unit (FPU). Based on the configurations, the handler can
identify / discriminate faults for overflow, divide by zero and invalid
operations.

### Rationale

The FPU “E bit” functionality is a function of the FPU configuration.

Page 173/174 of the software user manual (R01UH0436EJ0100 Rev.1.00)
states - "If the FS bit of the FPSR register is set to 1, an
unimplemented operation exception (E) <u>will not occur under any
circumstances</u>."

Nexteer is setting the FS bit to 1, therefore, there is no need to check
for the “E Bit” failure in the FSPR register. Should it set for some
reason, it will be swept into the “unknown” category.

### Implementation

The Floating Point exception has an offset of 0x070.

#### Event Driven (FpuErrIrq)

Registers used

|              |                                                                                     |                     |        |
|------------------------|------------------------------|---------|---------|
| **Register** | **Use**                                                                             | **Register Access** |        |
|              |                                                                                     | **SV**              | **UM** |
| FPSR         | This register is used to control and monitor the cause of floating point exceptions | R/W                 | No     |
| FPEPC        | This register stores the program counter value where the exception occurs.          | R/W                 | No     |

// Get data relating to the fault

*TmpData* = FPEPC

If (FPSR & 0x0000 4000 != 0) Then

*TmpSrc* = McuDiagc1.MCUDIAGC\_ FPUERRINVLDOPER // Invalid Operation

Else If (FPSR & 0x0000 2000 != 0)

*TmpSrc* = McuDiagc1.MCUDIAGC_FPUERRDIVBYZERO // Divide by Zero

Elseif (FPSR & 0x0000 1000 != 0)

*TmpSrc* = McuDiagc1.MCUDIAGC_FPUERROVF // Overflow

Elseif

*TmpSrc* = McuDiagc1.MCUDIAGC_FPUERRUKWN // Unknown (not expected)

EndIf

NxtrSwRstFromExcpn (*TmpSrc*, *TmpData*)

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image7.wmf"
style="width:5.99583in;height:5.78958in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image8.wmf"
style="width:5.63125in;height:8.27708in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image9.wmf"
style="width:5.99792in;height:3.3875in" />

### Verification Method

**NA**

## Sub-Function: Exception Handling Routine Misalignment

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-148:** When a MPU violation is detected, the access is not
granted, but the related information such as access type (read, write),
data size, and instruction type are stored in the memory error
information register MEI. The memory error address register is used to
store the address when a MAE (misaligned) or MPU exception occurs. Both
registers **can** be accessed in the CPU supervisor mode only.

### Description

This sub-function handles exceptions generated by a memory misalignment
error.

### Rationale

**TBD**

### Implementation

The memory misalignment exception has an offset of 0x0C0.

#### Event Driven (AlgnErrIrq)

Registers used

<table>
<colgroup>
<col style="width: 26%" />
<col style="width: 35%" />
<col style="width: 18%" />
<col style="width: 9%" />
<col style="width: 9%" />
</colgroup>
<tbody>
<tr class="odd">
<td rowspan="2"><strong>Register</strong></td>
<td rowspan="2"><strong>Use</strong></td>
<td rowspan="2"><strong>Register No. (regID,selID)</strong></td>
<td colspan="2"><strong>Register Access</strong></td>
</tr>
<tr class="even">
<td><strong>SV</strong></td>
<td><strong>UM</strong></td>
</tr>
<tr class="odd">
<td>MEI</td>
<td>Memory error information register – used to indicate if the
misalignment was caused during read or write</td>
<td>SR8, 2</td>
<td>Yes</td>
<td><p>No</p>
<p>(via SAN)</p></td>
</tr>
<tr class="even">
<td>MEA</td>
<td><p>Memory error address register - These bits store an address when
a MAE (misaligning) or MPU violation</p>
<p>occurs.</p></td>
<td>SR6, 2</td>
<td>Yes</td>
<td><p>No</p>
<p>(via SAN)</p></td>
</tr>
</tbody>
</table>

// Determine source of error and indicate in BRAMDAT0

*TmpData* = MEA

If (MEI & 0x0000 0001 = 0x0000 00001) Then

*TmpSrc* = McuDiagc1.MCUDIAGC_ALGNWR

Else

*TmpSrc* = McuDiagc1.MCUDIAGC_ALGNREAD

End If

NxtrSwRstFromExcpn (*TmpSrc*, *TmpData*)

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image10.wmf"
style="width:5.99236in;height:7.14792in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image11.wmf"
style="width:5.98889in;height:2.05764in" />

### Verification Method

**NA**

## Sub-Function: Exception Handling Routine Reserved Instruction

Return to sub-function list link: Sub-Functions In This Document

### NTCs

N/A

### SAN Linkage

None

### Description

### Rationale

This is basically an exception generated by processing an illegal opcode
function.

### Implementation

The Reserved Instruction exception has an offset of 0x060.

#### Event Driven (ResdOperIrq)

Registers used

|              |         |                     |        |
|--------------|---------|---------------------|--------|
| **Register** | **Use** | **Register Access** |        |
|              |         | **SV**              | **UM** |
| None         |         |                     |        |

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_RESDOPER, 0)

### Verification Method

N/A

## Sub-Function: Server Routine FENMI PEG

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-183:** For PE guard violations, a proper error handling **shall**
be performed. For this the ECM shall be configured accordingly.

### Description

This server function is called by the MCU handler and is responsible for
responding to a PEG (Processor Element Guard) error. The Nexteer design
has this configured in the ECM to be an exception of type FENMI. The
design notes the source of the error (for later use in the reset cause
function), clears the ECM status registers and issues a software reset.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function FeNmiPeg is called from the MCU handler.

### Implementation

#### Event Driven (FeNmiPeg)

Registers used

|              |         |                     |        |
|--------------|---------|---------------------|--------|
| **Register** | **Use** | **Register Access** |        |
|              |         | **SV**              | **UM** |
| None         |         |                     |        |

// Identify reset cause and reset

NxtrSwRstFromExcpn(McuDiagc1.MCUDIAGC_PROCRELMGUARD, 0)

### Verification Method

NA

## Sub-Function: Server Routine FENMI DMA Transfer Error

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-723:** When a data parity error is detected, a flag will be set in
P-Bus data parity status register APDPERRST_xx (xx stands for the module
name) and an internal error signal is propagated towards ECM. In this
case the MCU should move to safe state.

**SAN-724:** If a data parity error has occurred during DMA transfer, a
DMA transfer error will be notified.

### Description

This server routine is called from the MCU handler and is responsible
for responding to DMA transfer errors. The Nexteer design has this
configured in the ECM to be an exception of type FENMI. The design notes
the source of the error (for later use in the reset cause function),
clears the ECM status registers and issues a software reset.

### Rationale

N/A

### Implementation

#### Event Driven (FeNmiDmaTrf)

Registers used

|              |                                               |                     |        |
|------------------------|------------------------------|---------|---------|
| **Register** | **Use**                                       | **Register Access** |        |
|              |                                               | **SV**              | **UM** |
| DMASSDMACER  | Indicates the status of the two DMAC channels | Yes                 | Yes    |

// Indicate data for reset cause (Data0) and information on the
responsible DMA channel (Data1)

NxtrSwRstFromExcpn(McuDiagc1.MCUDIAGC_DMATRFERR, DMASSDMACER)

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image12.wmf"
style="width:5.99375in;height:5.28056in" />

### Verification Method

NA

## Sub-Function: Server Routine FENMI DMA Access Violation Error

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-100:** When the CPU makes an illegal access to the global DMA
registers (e.g. access in user mode), then an access violation flag will
be set in the related transfer module and an internal error signal will
be propagated to the ECM to take the proper action.

### Description

This server routine is called from the MCU handler and is responsible
for responding to DMA privileged access errors. The Nexteer design has
this configured in the ECM to be an exception of type FENMI. The design
notes the source of the error (for later use in the reset cause
function), clears the ECM status registers and issues a software reset.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ExcpnHndlgFeNmiDMAREGACSPROTECNERR is called from
the MCU handler.

In future versions of this document we may want to consider using the
registers DM0CMV, DM1CMV and DTSCMV to provide more information when the
fault is triggered. Note that these registers require supervisor mode to
be accessed – note that the exceptions are already be in SV mode.
Initial design will not include them.

### Implementation

#### Event Driven (FeNmiDmaRegAcsProtnErr)

Registers used

|              |                                               |                     |        |
|------------------------|------------------------------|---------|---------|
| **Register** | **Use**                                       | **Register Access** |        |
|              |                                               | **SV**              | **UM** |
| DMASSDMACER  | Indicates the status of the two DMAC channels | Yes                 | Yes    |

// Indicate data for reset cause (Data0) and information on the
responsible DMA channel (Data1)

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_DMAREGACSPROTECNERR, DMASSDMACER)

### Reference

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image12.wmf"
style="width:5.99375in;height:5.28056in" />

### Verification Method

NA

## Sub-Function: Server Routine FENMI ECM Master/Checker Compare

Return to sub-function list link: Sub-Functions In This Document

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**SAN-656:** If there is a mismatch between ECM master and checker an
ECM compare error will be set in the ECMmESSTR0/1 register. In that
case, the safe state shall be entered.

When the compare unit has detected a comparison mismatch between the DMA
Master and Checker, an error signal is propagated to the ECM to take the
proper action^6^.

^6^ User is required to set up the appropriate error response depending
on the application.

### Description

This server routine is called from the MCU handler and is responsible
for responding errors in which the master and checker compare error. The
Nexteer design has this configured in the ECM to be an exception of type
FENMI. The design notes the source of the error (for later use in the
reset cause function), clears the ECM status registers and issues a
software reset.

### Rationale

N/A

### Implementation

#### Event Driven (FeNmiEcmMstChkrCmp)

Registers used

|              |         |                     |        |
|--------------|---------|---------------------|--------|
| **Register** | **Use** | **Register Access** |        |
|              |         | **SV**              | **UM** |
| None         |         |                     |        |

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_ECMMSTCHKRERR, 0)

### Verification Method

**NA**

## Sub-Function: Server Routine FENMI Watchdog 

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

This server routine is called from the MCU handler and is responsible
for responding internal watchdog failures. Note that the design is
intended to use this server function to also sort to see if the timing
failure can be further discriminated to a watchdog, program flow, alive
monitor or a deadline monitor failure It is assumed that the MCU will
provide the capability to allow Nexteer to select / direct unused
features in the design to this routine.

The Nexteer design has configured in the ECM to be an exception of type
FENMI without a Reset. The design notes the source of the error (for
later use in the reset cause function), clears the ECM status registers
and issues a software reset.

### Rationale

The SAN recommends a reset when using the ECM for watchdog failures. The
Nexteer design will defeat the reset and replace the functionality with
a software reset – this is to allow the capability to store parse the
fault into watchdog, program flow, alive monitoring and deadline
monitoring and provide more information for debug purposes. The ECM
configuration as a reset would not allow this to be done.

Note that the function FeNmiWdg is called from the MCU handler.

### Implementation

#### Event Driven (FeNmiWdg)

Registers used

|                                                                |                                                                                                                                                           |                     |        |
|------------------------|------------------------------|---------|---------|
| **Register**                                                   | **Use**                                                                                                                                                   | **Register Access** |        |
|                                                                |                                                                                                                                                           | **SV**              | **UM** |
| EntityStatusGRef (not a register, but key part of this design) | This is a structure contained within the AutoSAR module that will provide the means to discriminate different failures that result in a watchdog timeout. | NA                  | NA     |

<u>Pseudo Code</u>

*TmpSrc* = McuDiagc1.MCUDIAGC_FENMIWDG

*TmpData* = 0

For Each SupervisedEntityID

If (EntityStatusGRef🡪ProgramFlowViolationCnt != 0) Then // Program Flow

*TmpSrc* = McuDiagc1.MCUDIAGC_FENMIPROGFLOW

*TmpData* = SupervisedEntityID

End the For Loop

ElseIf (EntityStatusGRef🡪FailedSupervisionRefCycles !=0) // Alive
Monitor

*TmpSrc* = McuDiagc1.MCUDIAGC_FENMIALVMONR

*TmpData* = SupervisedEntityID

End the For Loop

ElseIf (EntityStatusGRef🡪DeadlineViolationCnt !=0) // Deadline Monitor

*TmpSrc* = McuDiagc1.MCUDIAGC_FENMIDEADLINEMONR

*TmpData* = SupervisedEntityID

End the For Loop

Else

End If

End For

// Store data for reset cause use and reset

NxtrSwRstFromExcpn (*TmpSrc*, *TmpData*)

### Verification Method

**NA**

##  Sub-Function: FENMI Clock Monitor 0 RunTime Lower Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 0 Runtime Lower Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr0RtLowrLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr0RtLowrLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR0RTLOWRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 0 RunTime Upper Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 0 Runtime Upper Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr0RtUpprLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr0RtUpperLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR0RTUPPRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 1 RunTime Lower Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 1 Runtime Lower Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr1RtLowrLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr1RtLowrLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR1RTLOWRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 1 RunTime Upper Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 1 Runtime Upper Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr1RtUpperLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr1RtUpperLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR1RTUPPRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 2 RunTime Lower Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 2 Runtime Lower Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr2RtLowrLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr2RtLowrLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR2RTLOWRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 2 RunTime Upper Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 2 Runtime Upper Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr2RtUpperLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr2RtUpperLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR2RTUPPRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 3 RunTime Lower Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 3 Runtime Lower Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr3RtLowrLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr3RtLowrLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR3RTLOWRLIMFLT, 0)

### Verification Method

**NA**

## Sub-Function: FENMI Clock Monitor 3 RunTime Upper Limit Fault

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-1404\]**

In case an abnormal operation of the monitored clock is detected, an
error signal will be generated to the

ECM. In that case the MCU shall be entered into the safe state.

### Description

This server routine is called from the MCU handler and is responsible
for responding to Clock Monitor 3 Runtime Upper Limit Failure.

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

Note that the function ClkMonr3RtUpperLimFlt is called from the MCU
handler.

### Implementation

#### Event Driven (FeNmiClkMonr3RtUpperLimFlt)

<u>Pseudo Code</u>

// Identify reset cause and reset

NxtrSwRstFromExcpn (McuDiagc1.MCUDIAGC_CLKMONR3RTUPPRLIMFLT, 0)

### Verification Method

**NA**

## Sub Function: FENMI Operating Mode Error Single Chip Mode Inactive

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-2503\]**

Unintended mode activation during run-time is notified to the ECM via a
dedicated error signal. When the current operation mode is “Single Chip
mode” and the internal signal which indicates Flash programming mode
becomes valid, an internal error signal is propagated to the ECM becomes
active (high). Similarly, when the internal signal which indicates that
“Single Chip Mode” is deactivate, internal error signals are propagated
to the ECM. In that case, transition to the safe state shall be
performed \[SAN-P1x-2503\].

### Description

This server routine is called from the MCU handler and is responsible
for responding to Mode error (single-chip mode is inactive in
single-chip mode)

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

### Implementation

#### Event Driven (FeNmiOperModErrSngChipInactv)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_OPERMODERRSNGCHIPINACTV, 0)

### Verification Method

**NA**

## Sub Function: FENMI Operating Mode Error Flash Programming Mode is Started in Single-Chip Mode

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-2503\]**

Unintended mode activation during run-time is notified to the ECM via a
dedicated error signal. When the current operation mode is “Single Chip
mode” and the internal signal which indicates Flash programming mode
becomes valid, an internal error signal is propagated to the ECM becomes
active (high). Similarly, when the internal signal which indicates that
“Single Chip Mode” is deactivate, internal error signals are propagated
to the ECM. In that case, transition to the safe state shall be
performed \[SAN-P1x-2503\].

### Description

This server routine is called from the MCU handler and is responsible
for responding to Mode error (flash programming mode is started in
single-chip mode)

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

### Implementation

#### Event Driven (FeNmiOperModErrFlsProgmModStrtd)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_OPERMODERRFLSPROGMMODSTRTD, 0)

### Verification Method

**NA**

## Sub Function: FENMI Operating Mode Error Test Mode Started in Single Chip Mode

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

**\[SAN-P1x-2503\]**

Unintended mode activation during run-time is notified to the ECM via a
dedicated error signal. When the current operation mode is “Single Chip
mode” and the internal signal which indicates Flash programming mode
becomes valid, an internal error signal is propagated to the ECM becomes
active (high). Similarly, when the internal signal which indicates that
“Single Chip Mode” is deactivate, internal error signals are propagated
to the ECM. In that case, transition to the safe state shall be
performed \[SAN-P1x-2503\].

### Description

This server routine is called from the MCU handler and is responsible
for responding to Mode error (test mode is started in single-chip mode)

### Rationale

FENMI Interrupts are used to represent serious failures within the
microcontroller or it’s peripherals that are critical to the overall
design. As a result, the Nexteer strategy is to indicate the fault type
in backup memory (data retained through a software reset) and force a
software reset where the reset type is then indicated and the fault is
set (assuming the system can operate to that point).

### Implementation

#### Event Driven (FeNmiOperModErrTestModStrtd)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_OPERMODERRTESTMODSTRTD, 0)

### Verification Method

**NA**

## Sub Function: Server Routine Process Unknown Exception Error

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

The Process Unknown Exception Error needs to be called when the OS
detects an unknown exception.

### Rationale

### Implementation

#### Event Driven (ProcUkwnExcpnErr)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_UKWNEXCPN, McuDiagcData1_Arg)

### Verification Method

**NA**

## Sub-Function: Server Routine Process Memory Protection Unit Exception Error

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

The Process Memory Protection Unit Exception Error needs to be called
when the OS detects a memory protection violation.

### Rationale

### Implementation

#### Event Driven (ProcMpuExcpnErr)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_MPU, McuDiagcData1_Arg)

### Verification Method

**NA**

## Sub-Function: Server Routine Process Privileged Instruction Exception Error

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

The Process Privileged Instruction Exception Error needs to be called
when the OS detects a protection violation.

### Rationale

### Implementation

#### Event Driven (ProcPrvlgdInstrExcpnErr)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_PRVLGDINSTREXCPN, McuDiagcData1_Arg)

### Verification Method

**NA**

## Sub-Function: Server Routine Process Permanent Os Error

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

The Process Permanent Os Error needs to be called when the OS detects a
fatal, permanent failure.

### Rationale

### Implementation

#### Event Driven (ProcPrmntOsErr)

// Perform software reset from exception and pass appropriate arguments

NxtrSwRstFromExcpn(MCUDIAGC_PRMNTOSERR, McuDiagcData1_Arg)

### Verification Method

**NA**

## Sub-Function: Server Routine Process Non Critical Os Error

### NTCs

None – NTCs are addressed in section 4.29 (Reset Source)

### SAN Linkage

None

### Description

The Process Non Critical Os Error needs to be called when the OS detects
a non-fatal failure.

### Rationale

### Implementation

#### Event Driven (ProcNonCritOsErr)

// Update error code variable that is polled in periodic function

ExcpnHndlgOsErrCod_C = McuDiagcData1_Arg

### Verification Method

**NA**

### Periodic (ExcpnHndlgPer1)

\*\* NOTE: variable ExcpnHndlgOsErrCod must reside in global shared
memory \*\*

If (ExcpnHndlgOsErrCod != 0x0000) then

// Set code for non-fatal OS error – Error Code is on the data
ExcpnHndlgOsErrCod

SetNtcSts(NtcNr1.NTCNR_0x031, 1, NtcSts1.NTCSTS_FAILD, 0)

End If

### Verification Method

**NA**

## Sub-Function: Server Routine Shutdown Hook 

Call EcuM_Shutdown()

## Sub-Function: Exception Handling Routine EIINT

Return to sub-function list link: Sub-Functions In This Document

It is assumed that the MCU configuration will directly provide a
client/server call to the necessary FDDs to accomplish their tasks. It
would be redundant to place them within this document only to call out
another document, so this is the chosen approach.

Please refer to other microcontroller diagnostic FDDs to see their
specific exception handler functionality.

## Sub-Function: Reset Source Determination

Return to sub-function list link: Sub-Functions In This Document

### NTCs

003.0 Code Flash ECC Single Bit (Hard Fault)

003.1 Code Flash ECC Double Bit Detection

003.2 Code Flash ECC Address Parity Fault

010.0 MBIST Startup Test Failure

013.0 Local RAM ECC Single Bit (Hard Fault)

013.1 Local RAM ECC Double Bit (Hard Fault)

013.2 Local RAM Address Fault

016.1 DTS ECC Double Bit (Hard Fault)

021.0 BIST Code ECC Failure

021.2 LBIST Startup Test Failure

021.4 BIST Not Complete

021.5 CPU Lock Step Error Forcing Startup Test Failure

021.6 DMA Lock Step Error Forcing Startup Test Failure

022.0 Lock Step Compare Fault

022.1 System VCIE Bit Error

022.2 Reserved Instruction (Illegal Op Code) Fault

022.3 Memory Misalignment - Read

022.4 Memory Misalignment - Write

022.5 Instruction Fetch Error

022.6 FACI Reset Transfer Error

023.2 CLMA 0 Runtime Lower Limit Fault

023.3 CLMA 0 Runtime Upper Limit Fault

023.6 CLMA 2 Runtime Lower Limit Fault

023.7 CLMA 2 Runtime Upper Limit Fault

024.0 Mode Error (Flash Programming Mode is Started in Single-Chip Mode)

024.1 Mode Error (Test Mode Started in Single Chip Mode)

024.2 Mode Error (Single Chip Mode Inactive in Single Chip Mode)

025.0 MPU Violation (this convers MDP and MIP Exception)

025.1 Privilege Instruction Execution

026.0 ECM Status Bit Set Prior to ECM Init

026.2 ECM Startup Master nERROR Output Control Fault

026.3 ECM Startup Checker nERROR Output Control Fault

026.7 ECM Runtime Master-Checker Compare Fault027

027.2 CLMA 1 Runtime Lower Limit Fault

027.3 CLMA 1 Runtime Upper Limit Fault

027.6 CLMA 3 Runtime Lower Limit Fault

027.7 CLMA 3 Runtime Upper Limit Fault

028.1 FPU Invalid Operation (V Bit)

028.2 FPU Divide by Zero (Z Bit)

028.3 FPUOverflow (O Bit)

028.4 FPU Unknown Error

029.0 Unknown Reset Reason

029.1 Unknown ECM Reset Reason

029.4 Unknown Software Reset

029.5 Failed Backup RAM Read Write Test

029.6 FBL Pre-OS Startup Exception

029.7 Corrupt Start up / Reset Information

02A.0 Program Flow

02A.1 Deadline Monitoring

02A.2 Alive Monitoring

02C.0 Watchdog Timeout

02D.1 PEG Runtime Fault

02D.3 IPG RunTime Fault

02D.4 PBG (Peripheral Guard) Startup Test Failure

02D.5 PBG Runtime Fault

02F.0 External Debug Device Connected

030.0 Operating System Fatal Fault

030.1 Unhandled Exception

031.0 Operating System Non-Fatal Fault

036.0 DMA Transfer Error

036.1 DMA Register Access Protection Violation

037.6 P-Bus Data Parity Fault Startup Test Failure

037.7 P Bus Data Parity Runtime Fault

048.0 CVM Over Voltage Startup Test Failure

048.1 CVM Under Voltage Startup Test Failure

049.0 Internal CVM Over Voltage Monitor Fault

049.1 Internal CVM Under Voltage Monitor Fault

049.7 External Over Voltage Monitor Fault

### SAN Linkage

**SAN-621:** Upon detection of under/overvoltage of the core power
supply, the signal at the CVMOUT pin changes its state to low and a
dedicated flag will be set in the CVMF register. It is also possible to
generate a reset if the software has enabled it. In that case,
transition the MCU into the safe state **shall** be entered.

**SAN-1024:** As the usage of backup registers is strongly application
dependents, the user should judge whether or not to apply the proposed
write verify check. Moreover, if the data retained in the back-up
register will be frequently used in the safety related application, then
the contain should be moved to LRAM as it is protected by ECC and thus
provide a high fault coverage.

**SAN-1094:** As the usage of backup registers is strongly application
dependents, the user should judge whether or not to apply the proposed
write verify check. Moreover, if the data retained in the back-up
register will be frequently used in the safety related application, then
the contain should be moved to LRAM as it is protected by ECC and thus
provide a high fault coverage.

**SAN-1096:** Detected failures during the execution of the test shall
be handled at application level.

### Description

This function processes information from pre-OS tests and resets to
determine the cause of anything unexpected and log the correct Nexteer
Trouble Code. Backup RAM data is used to provide this information to the
function.

### Rationale

In order to log Nexteer Trouble Code information, the Diagnostic Manager
must be initialized prior to setting or clearing NTCs.

### Implementation

#### Initialization (ExcpnHndlgInit2)

SetNtcSts(NtcNr1.NTCNR_0x003, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x010, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x013, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x016, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x021, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x022, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x023, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x024, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x025, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x026, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x027, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x028, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x029, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x02A, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x02C, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x02D, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x02F, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x030, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x031, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x036, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x037, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x048, 0, NtcSts1.NTCSTS_PASSD, 0)

SetNtcSts(NtcNr1.NTCNR_0x049, 0, NtcSts1.NTCSTS_PASSD, 0)

// Confirm state of backup data is valid

If (((BRAMDAT0 & 0xFFFF 0000) \>\> 16) XOR (BRAMDAT0 & 0x0000 FFFF)) !=
0x0000 FFFF) Then

// Set fault – BRAMDAT0 data is corrupt and cannot be trusted

SetNtcSts(NtcNr1.NTCNR_0x029, 128, NtcSts1.NTCSTS_FAILD, 0)

Else If ((BRAMDAT0 = McuDiagc1.MCUDIAGC_PWRONRST) OR (BRAMDAT0 =
McuDiagc1.MCUDIAGC_FLSPROGMCMPL) OR (BRAMDAT0 =
McuDiagc1.MCUDIAGC_HARDRST) OR (BRAMDAT0 = McuDiagc1.MCUDIAGC_SOFTRST))
Then

// No checks needed – normal power on start up or flash programming
event or soft/hard reset

Else If ((SYSBSEQ0ST.DEBUGMODE = 1) AND (SYSBSEQ0STB. DEBUGMODEB = 0))

// No checks needed in debug mode

Else If (BRAMDAT0 = McuDiagc1.MCUDIAGC_ECMRST)

ProcEcmRst() // Reset from ECM

ElseIf (BRAMDAT0 = McuDiagc1.MCUDIAGC_PINRST)

ProcPinRst() // Reset from External Pin (Power Supply)

ElseIf (BRAMDAT0 = McuDiagc1.MCUDIAGC_COREVLTGMONRHI) // Overvoltage
internal to uC

SetNtcSts(NtcNr1.NTCNR_0x049, 1, NtcSts1.NTCSTS_FAILD, 0)

ElseIf (BRAMDAT0 = McuDiagc1.MCUDIAGC_COREVLTGMONRLO) // Low voltage
internal to uC

SetNtcSts(NtcNr1.NTCNR_0x049, 2, NtcSts1.NTCSTS_FAILD, 0)

Else

ProcStrtUpOrSwRst() // Check for start-up, non-reset faults

End If

#### FunctionCall ProcEcmRst

//Check for lock step fault in either core

// By design, lock step is the only ECM fault resulting in a reset -
confirm

If ((ECMMSSE001 = 1) or (ECMCSSE001 = 1)) Then

// Set lock step fault

SetNtcSts(NtcNr1.NTCNR_0x022, 1, NtcSts1.NTCSTS_FAILD, 0)

Else

// Set unknown ECM reset fault

SetNtcSts(NtcNr1.NTCNR_0x029, 2, NtcSts1.NTCSTS_FAILD, 0)

End If

// Clear all the bits of ECMmESSTR0

ECMESSTC0_Desired = 0xFDFF DFF3;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Clear all the bits of ECMmESSTR1

ECMESSTC1_Desired = 0x6000 07F7;

WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

#### FunctionCall ProcStrtUpOrSwRst

Switch: BRAMDAT0

// Pre-OS failures, (non-sw reset)

> Case: McuDiagc1.MCUDIAGC_MEMBISTERR
>
> SetNtcSts(NtcNr1.NTCNR_0x010, 1, NtcSts1.NTCSTS_FAILD, 0) // MBIST
> Proof
>
> Break

Case: McuDiagc1.MCUDIAGC_BISTECCERR

SetNtcSts(NtcNr1.NTCNR_0x021, 1, NtcSts1.NTCSTS_FAILD, 0) //BIST 2 bit
ECC

Break

Case: McuDiagc1.MCUDIAGC_LOGLBISTERR

> SetNtcSts(NtcNr1.NTCNR_0x021, 4, NtcSts1.NTCSTS_FAILD, 0) //LBIST
> Proof
>
> Break

Case: McuDiagc1.MCUDIAGC_BISTNOTCMPLERR

> SetNtcSts(NtcNr1.NTCNR_0x021, 16, NtcSts1.NTCSTS_FAILD, 0) //BIST not
> complete
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_CPULOCKSTEPERR
>
> SetNtcSts(NtcNr1.NTCNR_0x021, 32, NtcSts1.NTCSTS_FAILD, 0) //CPU Lock
> Step Proof
>
> Break

Case: McuDiagc1.MCUDIAGC_DMALOCKSTEPERR

> SetNtcSts(NtcNr1.NTCNR_0x021, 64, NtcSts1.NTCSTS_FAILD, 0) //DMA Lock
> Step Proof
>
> Break

Case: McuDiagc1. MCUDIAGC_ECMSTSSTRTUPFLT

> SetNtcSts(NtcNr1.NTCNR_0x026, 1, NtcSts1.NTCSTS_FAILD, 0) // ECM
> Status Prob
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_MSTERROUTPCTRLFLT
>
> SetNtcSts(NtcNr1.NTCNR_0x026, 4, NtcSts1.NTCSTS_FAILD, 0) //Master
> Control Proof
>
> Break

Case: McuDiagc1.MCUDIAGC_CHKRERROUTPCTRLFLT

SetNtcSts(NtcNr1.NTCNR_0x026, 8, NtcSts1.NTCSTS_FAILD, 0) //Checker
Control Proof

Break

Case: McuDiagc1. MCUDIAGC_BACKUPRAMTSTFAILR

> SetNtcSts(NtcNr1.NTCNR_0x029, 32, NtcSts1.NTCSTS_FAILD, 0) //Back-Up
> Test Fail
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_PREOSEXCPN
>
> SetNtcSts(NtcNr1.NTCNR_0x029, 64, NtcSts1.NTCSTS_FAILD, 0) //Pre-OS
> Exception
>
> Break

Case: McuDiagc1.MCUDIAGC_STRTUPCOREVLTGMONROVER

> SetNtcSts(NtcNr1.NTCNR_0x048, 1, NtcSts1.NTCSTS_FAILD, 0) //CVM OV
> Proof
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_STRTUPCOREVLTGMONRUNDER
>
> SetNtcSts(NtcNr1.NTCNR_0x048, 2, NtcSts1.NTCSTS_FAILD, 0) //CVM UV
> Proof
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_PBGSTRTUPTST
>
> SetNtcSts(NtcNr1.NTCNR_0x02D, 16, NtcSts1.NTCSTS_FAILD, 0) //PBG
> (Peripheral Guard) Startup Test Failure
>
> Break
>
> Case: McuDiagc1.MCUDIAGC_PRPHLBUSDATAPARSTRTUPFLT
>
> SetNtcSts(NtcNr1.NTCNR_0x037, 64, NtcSts1.NTCSTS_FAILD, 0) // P-Bus
> Data Parity Fault Startup Test Failure
>
> Break

Case: McuDiagc1.MCUDIAGC_RSTUKWN

SetNtcSts(NtcNr1.NTCNR_0x029, 1, NtcSts1.NTCSTS_FAILD, 0) // Unknown Rst
to FBL

Break

// Software Resets

Case: McuDiagc1.MCUDIAGC_DBGRST

SetNtcSts(NtcNr1.NTCNR_0x02F, 1, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_CODFLSSNGBITHARDFLT

SetNtcSts(NtcNr1.NTCNR_0x003, 1, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_CODFLSDBLBIT

SetNtcSts(NtcNr1.NTCNR_0x003, 2, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: MCUDIAGC_PRPHLBUSDATAPAR

SetNtcSts(NtcNr1.NTCNR_0x037, 128, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_ADRPAR

> SetNtcSts(NtcNr1.NTCNR_0x003, 4, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1. MCUDIAGC_LCLRAMECCSNGBITHARDFAILR

SetNtcSts(NtcNr1.NTCNR_0x013, 1, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_LCLRAMDBLBIT

SetNtcSts(NtcNr1.NTCNR_0x013, 2, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_INVLDRAMAREA

SetNtcSts(NtcNr1.NTCNR_0x013, 4, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_DTSDBLBIT

SetNtcSts(NtcNr1.NTCNR_0x016, 2, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_SPIRAMDBLBIT0

> SetNtcSts(NtcNr1.NTCNR_0x017, 2, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_SPIRAMDBLBIT1

> SetNtcSts(NtcNr1.NTCNR_0x018, 2, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_SPIRAMDBLBIT2

> SetNtcSts(NtcNr1.NTCNR_0x019, 2, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_SPIRAMDBLBIT3

> SetNtcSts(NtcNr1.NTCNR_0x01A, 2, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_VCIE

SetNtcSts(NtcNr1.NTCNR_0x022, 2, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_RESDOPER

SetNtcSts(NtcNr1.NTCNR_0x022, 4, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_ALGNREAD

SetNtcSts(NtcNr1.NTCNR_0x022, 8, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_ALGNWR

SetNtcSts(NtcNr1.NTCNR_0x022, 16, NtcSts1.NTCSTS_FAILD, 0)

> Break

Case: McuDiagc1.MCUDIAGC_INSTRFETCH

SetNtcSts(NtcNr1.NTCNR_0x022, 32, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_FACIRSTTRFERR

SetNtcSts(NtcNr1.NTCNR_0x022, 64, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_OPERMODERRFLSPROGMMODSTRTD

SetNtcSts(NtcNr1.NTCNR_0x024, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_OPERMODERRTESTMODSTRTD

SetNtcSts(NtcNr1.NTCNR_0x024, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_OPERMODERRSNGCHIPINACTV

SetNtcSts(NtcNr1.NTCNR_0x024, 4, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC\_ MPU

SetNtcSts(NtcNr1.NTCNR_0x025, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC\_ PRVLGDINSTREXCPN

SetNtcSts(NtcNr1.NTCNR_0x025, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC\_ ECMMSTCHKRERR

SetNtcSts(NtcNr1.NTCNR_0x026, 128, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_FPUERRINVLDOPER

> SetNtcSts(NtcNr1.NTCNR_0x028, 2, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_FPUERRDIVBYZERO

> SetNtcSts(NtcNr1.NTCNR_0x028, 4, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_FPUERROVF

> SetNtcSts(NtcNr1.NTCNR_0x028, 8, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_FPUERRUKWN

> SetNtcSts(NtcNr1.NTCNR_0x028, 16, NtcSts1.NTCSTS_FAILD, 0)
>
> Break

Case: McuDiagc1.MCUDIAGC_FENMIPROGFLOW

SetNtcSts(NtcNr1.NTCNR_0x02A, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_FENMIDEADLINEMONR

SetNtcSts(NtcNr1.NTCNR_0x02A, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_FENMIALVMONR

SetNtcSts(NtcNr1.NTCNR_0x02A, 4, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_FENMIWDG

SetNtcSts(NtcNr1.NTCNR_0x02C, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR0RTLOWRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x023, 4, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR0RTUPPRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x023, 8, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR1RTLOWRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x027, 4, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR1RTUPPRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x027, 8, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR2RTLOWRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x023, 64, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR2RTUPPRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x023, 128, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR3RTLOWRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x027, 64, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_CLKMONR3RTUPPRLIMFLT

SetNtcSts(NtcNr1.NTCNR_0x027, 128, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_PROCRELMGUARD

SetNtcSts(NtcNr1.NTCNR_0x02D, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_INTPRPHLGUARD

SetNtcSts(NtcNr1.NTCNR_0x02D, 8, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_PRPHLBUSGUARD

SetNtcSts(NtcNr1.NTCNR_0x02D, 32, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_PRMNTOSERR

SetNtcSts(NtcNr1.NTCNR_0x030, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_UKWNEXCPN

SetNtcSts(NtcNr1.NTCNR_0x030, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_DMATRFERR

SetNtcSts(NtcNr1.NTCNR_0x036, 1, NtcSts1.NTCSTS_FAILD, 0)

Break

Case: McuDiagc1.MCUDIAGC_DMAREGACSPROTECNERR

SetNtcSts(NtcNr1.NTCNR_0x036, 2, NtcSts1.NTCSTS_FAILD, 0)

Break

Default:

SetNtcSts(NtcNr1.NTCNR_0x029, 16, NtcSts1.NTCSTS_FAILD, 0) // unknown SW
Reset

Break

End Switch

#### FunctionCall ProcPinRst

SetNtcSts(NtcNr1.NTCNR_0x049, 128, NtcSts1.NTCSTS_FAILD, 0) // External
Pin Reset

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM101A_ExcpnHndlg_Design/Design/mediax/media/image13.wmf"
style="width:5.99722in;height:3.4125in" />

### Verification Method

NA

# Special Functions

For this design, some special functions are used to identify the first
failure of data and respond. Once data is changed from its known, good
states (power on reset or flash programming complete) the BRAMDAT0 will
not be updated until a valid power up process occurs or a flash program
event is requested.

Data 1 is ONLY updated by the reset cause in the case of a back-up
register corruption. This is done to not “lose” data following an NTC
event.

// SetMcuDiagcIdnData(Microcontroller Diagnostic Identification Data)

SetMcuDiagcIdnData (McuDiagcData0, McuDiagcData1)

> // Update data if different from PwrOnRst or FlsProgmCmpl – OR if
> flash prog is requested
>
> If ((BRAMDAT0 = McuDiagc1.MCUDIAGC_FLSPROGMREQ) OR
>
> (BRAMDAT0 = McuDiagc1.MCUDIAGC_PWRONRST) OR
>
> (BRAMDAT0 = McuDiagc1.MCUDIAGC_DBGRST) OR
>
> (BRAMDAT0 = McuDiagc1.MCUDIAGC_FLSPROGMCMPL) OR (BRAMDAT0 =
> McuDiagc1.MCUDIAGC_HARDRST) OR (BRAMDAT0 =
> McuDiagc1.MCUDIAGC_SOFTRST)) Then
>
> BRAMDAT0 = McuDiagcData0
>
> BRAMDAT1 = McuDiagcData1
>
> End If

Done

‘ChkForStrtUpTest’ function is used to check if a startup test has to be
performed or not.

The point of this test is to avoid getting into continuous reset loops
due to some faults getting set. We perform start up tests on only those
kinds of resets which are not a result of faults being set. When a reset
causing fault occurs, we’d only want to reset the controller and move to
a safe state. Therefore, we only run start up tests only when we come
out of a Power On Reset, or when the Flash Programming is Complete or
when we received reset commands from Serial Communication such as Soft
Reset and Hard Reset.

ChkForStrtUpTest (P2VAR ExecStrtUpTest)

{

If ((BRAMDAT0 = McuDiagc1.MCUDIAGC_PWRONRST) OR 

(BRAMDAT0 = McuDiagc1.MCUDIAGC_FLSPROGMCMPL) OR 

(BRAMDAT0 = McuDiagc1.MCUDIAGC_HARDRST) OR 

(BRAMDAT0 = McuDiagc1.MCUDIAGC_SOFTRST))

{

> \*ExecStrtUpTest = TRUE;

}

Else

{

> \*ExecStrtUpTest = FALSE;

}

}

# Revision Record & Change Approval

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 13%" />
<col style="width: 13%" />
<col style="width: 8%" />
<col style="width: 57%" />
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
<td>10/20/2015</td>
<td>EA4#1831</td>
<td>MK</td>
<td>Initial Release</td>
</tr>
<tr class="odd">
<td>1.1.0</td>
<td>11/19/2015</td>
<td>EA4#2536</td>
<td>SK</td>
<td>Removed CVMREN Initialization. Refer Anomaly EA4#2522</td>
</tr>
<tr class="even">
<td>1.2.0</td>
<td>01/08/16</td>
<td>EA4#3186</td>
<td>LWW</td>
<td>Replaced Os Protection and Error Hook</td>
</tr>
<tr class="odd">
<td>2.0.0</td>
<td>01/21/2016</td>
<td>EA4#3413</td>
<td>SK</td>
<td>Added Clock Monitor FE, Soft Reset, Hard Reset conditions, P Bus
Data Parity Check</td>
</tr>
<tr class="even">
<td>2.1.0</td>
<td>02/08/2016</td>
<td>EA4#3729</td>
<td>SK</td>
<td>Updated SAN section for DTS 2Bit ECC, ECM Master/Checker Compare,
Added Start Up Test for P Bus and PBG Start up test, Added function
ChkForStrtUpTest </td>
</tr>
<tr class="odd">
<td>2.1.1</td>
<td>02/12/2016</td>
<td>EA4#3847</td>
<td>SK</td>
<td>Corrected parameter bit for NTC of PBGSTRTUPTST, Update Clock
Monitors FENMI ISR for typos.</td>
</tr>
<tr class="even">
<td>2.2.0</td>
<td>03/17/2016</td>
<td>EA4#4519</td>
<td>SK</td>
<td>Removed DTS Double RAM FENMI Section and added the DTS Double RAM
ECC as a part of SYSERR</td>
</tr>
<tr class="odd">
<td>3.0.0</td>
<td>03/29/2016</td>
<td>EA4#4863</td>
<td>GM</td>
<td><p>Added new MCUDIAGC_INVLDRAMAREA, MCUDIAGC_FACIRSTTRFERR,
MCUDIAGC_SNGCHIPINACTV, MCUDIAGC_CODFLSECCSNGBITERR, MCUDIAGC_DBGRST</p>
<p>Added new NTC 013.2, 022.6 and 02F.0</p>
<p>Removed SPI double bit ECC faults (added to CM103A)</p>
<p>NTC 021.0 name changed from BIST Code 2-bit ECC Failure to 021.0 BIST
Code ECC Failure</p></td>
</tr>
<tr class="even">
<td>3.0.1</td>
<td>04/07/2016</td>
<td>EA4#5184</td>
<td>GM</td>
<td><p>Add NTC 13.2 to NTC list in section 4.29.1</p>
<p>Add NTC 02F.0 to NTC list in section 4.29.1</p>
<p>Change NTC 025.0 description to MPU Violation (this convers MDP and
MIP Exception) from Data Protection Violation (MDP Exception) in section
4.29.1</p>
<p>Change NTC 025.1 description to Privilege Instruction Execution from
Execution Protection Violation (MIP Exception) in section
4.29.1</p></td>
</tr>
</tbody>
</table>

{% endraw %}