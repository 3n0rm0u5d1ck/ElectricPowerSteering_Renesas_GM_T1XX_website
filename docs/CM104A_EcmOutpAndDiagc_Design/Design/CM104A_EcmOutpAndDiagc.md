---
layout: default
title: CM104A_EcmOutpAndDiagc
nav_order: 1
parent: Component Design
---
{% raw %}
**Error Control Module Output**

**And**

**Diagnostics**

**CM104A**

[1. High Level Description 3](#high-level-description)

[2. Sub-Function In This Document 3](#sub-function-in-this-document)

[3. Sub-functions 4](#sub-functions)

[3.1. Sub-Function: ErrorOut Generation
4](#sub-function-errorout-generation)

[3.1.1. NTCs 4](#ntcs)

[3.1.2. SAN Linkage 4](#san-linkage)

[3.1.3. Description 4](#description)

[3.1.4. Rationale 6](#rationale)

[3.1.5. Implementation 6](#implementation)

[3.1.6. Verification Method 8](#verification-method)

[3.2. Sub-Function: ECM Startup Master/Checker nERROR Output Control
Fault
8](#sub-function-ecm-startup-masterchecker-nerror-output-control-fault)

[3.2.1. NTCs 8](#ntcs-1)

[3.2.2. SAN Linkage 8](#san-linkage-1)

[3.2.3. Description 9](#description-1)

[3.2.4. Rationale 9](#rationale-1)

[3.2.5. Implementation 9](#implementation-1)

[3.2.6. Verification Method 11](#verification-method-1)

[3.3. Sub-Function: EI Interrupt StartUp Test
11](#sub-function-ei-interrupt-startup-test)

[3.3.1. NTCs 11](#ntcs-2)

[3.3.2. SAN Linkage 11](#san-linkage-2)

[3.3.3. Description 12](#description-2)

[3.3.4. Rationale 17](#rationale-2)

[3.3.5. Implementation 17](#implementation-2)

[3.3.6. Verification Method 19](#verification-method-2)

[3.4. Sub-Function: Pseudo Error Injection StartUp Test
19](#sub-function-pseudo-error-injection-startup-test)

[3.4.1. NTCs 19](#ntcs-3)

[3.4.2. SAN Linkage 19](#san-linkage-3)

[3.4.3. Description 19](#description-3)

[3.4.4. Rationale 20](#rationale-3)

[3.4.5. Implementation 20](#implementation-3)

[3.4.6. Verification Method 23](#verification-method-3)

[4. Revision Record & Change Approval
24](#revision-record-change-approval)

# High Level Description

The ECM incorporates the ECM master/checker error source status
register, which can be used to confirm the error status from the error
flag. The error flags are only cleared by the ECM error source status
clear trigger register, POCRES, CVMRES, or DBRES. In case of other reset
sources, the error flags are kept and the reset generation source can be
confirmed by reading the ECM master/checker error source status register
after reset.

Pseudo errors can be generated for debug and self-diagnosis. The
operation during injection of pseudo errors is identical to that for the
occurrence of real errors. All configurations for masking of the
ERROROUT output, interrupts, and internal resets (ECMRES) apply in the
same way.

The ECM incorporates a loop-back function of the ERROROUT output that is
used to diagnose the path to the ERROROUT pin. The status of the
ERROROUT pin is reflected to an internal register and can be confirmed
by reading the register.

Each of the errors associated with ECM are configured to be an EI level
Interrupt or FE level Interrupt or they could be configured to cause an
Internal Reset or they could pull the ErrorOut Pin to Low.

This are listed in the excel sheet below:

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Design/Design/mediax/media/image1.wmf)

# Sub-Function In This Document

Below is a linked list of all sub-functions owned by this document.

|                                                        |                                            |
|----------------------------------------------------|--------------------|
| **Sub-Function Name**                                  | **Link**                                   |
| ERROROUT Generation                                    | [3.1](#_Sub-Function:_ErrorOut_Generation) |
| ECM Startup Master/Checker nERROR Output Control Fault | [3.2](#_Sub-Function:_ECM_Startup)         |
| EI Interrupt StartUp Test                              | 3.3                                        |
| Pseudo Error Injection StartUp Test                    | 3.4                                        |

#  [section]

# Sub-functions

## Sub-Function: ErrorOut Generation

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

N/A

### Description

This sub-function describes how to drive the ERROROUT pin high or low
manually.

When the MCU is out of reset, the ERROROUT output signal will be
asserted low and remain low even if no ECM error sources are active.
Software must “manually” set the ERROROUT output to inactive high state
at system initialization. This design assumes that the above mentioned
functionality is done in the MCU driver MCU_Init () function.

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Design/Design/mediax/media/image2.jpeg"
style="width:5.75208in;height:3.76181in" />

Register Info:

|                                                              |                                                                                                                                                               |                 |     |
|---------------------|-------------------------------|-----------|----------|
| Register                                                     | Use                                                                                                                                                           | Register Access |     |
|                                                              |                                                                                                                                                               | SV              | UM  |
| ECMEMK0 (ECM Error Mask Register 0)                          | Used to mask the individual error sources of the ERROROUT output.                                                                                             | R/W             | R/W |
| ECMIRCFG0 (ECM Internal Reset Configuration Register 0)      | Used to set the generation of internal resets (ECMRES) in response to internal errors.                                                                        | R/W             | R/W |
| ECMMICFG0 (ECM EI Level Interrupt Configuration Register 0)  | Used to set the generation of the EI level interrupts.                                                                                                        | R/W             | R/W |
| ECMNMICFG0 (ECM FE Level Interrupt Configuration Register 0) | Used to set the generation of FE level interrupts.                                                                                                            | R/W             | R/W |
| ECMESSTC0 (ECM Error Source Status Clear Trigger Register 0) | Used to clear the individual error source status of the ECM master/checker error source status register 0.                                                    | R/W             | R/W |
| ECMESSTC1 (ECM Error Source Status Clear Trigger Register 1) | Used to clear the individual error source status of the ECM master/checker error source status register 1.                                                    | R/W             | R/W |
| ECMMESET (ECM Master Error Set Trigger Register)             | Used for selecting output of the error signal from the ERROROUT pin. When the ECMMEST bit is set to 1, the ERROROUT pin immediately outputs the error signal. | R/W             | R/W |
| ECMCESET (ECM Checker Error Set Trigger Register)            | Used for selecting output of the error signal from the ERROROUT pin. When the ECMCEST bit is set to 1, the ERROROUT pin immediately outputs the error signal. | R/W             | R/W |
| ECMMECLR (ECM Master Error Clear Trigger Register)           | Used for setting the error signal from the ERROROUT pin to the inactive level (high level).                                                                   | R/W             | R/W |
| ECMCECLR (ECM Checker Error Clear Trigger Register)          | Used for setting the error signal from the ERROROUT pin to the inactive level (high level).                                                                   | R/W             | R/W |

### Rationale

Clearing of the ERROROUT output is only possible if all errors not
masked by ECMEMK0/1, and the ECMmSSE130 bit in the ECMmESSTR1 register
are cleared beforehand.

Clearing or setting the ERROROUT output via the ECMmECLR and ECMmESET
register will set the ECMmSSE029 bit of the ECMmESSTR0 register (ECM
compare error) irrelevant to the setting of the error mask and hence has
to be cleared.

If ERROROUT mask is OFF and error is generated, ERROROUT goes low.  If
error status flag is cleared ERROROUT still remains low. ERROROUT has to
be manual driven to high state again.

The Master AND the Checker Error Set Trigger registers have to set their
ECMmECT bit in order to set the ErrorOut Pin High.

The Master OR the Checker OR Both the Error Clear Trigger registers have
to set their ECMmECT bit in order to set the ErrorOut Pin Low.

<u>Function Arguments:</u>

> PinSt:
>
> 1: STD_HIGH (ErrorOut = 1)
>
> 0: STD_LOW (ErrorOut = 0)
>
> TrigReg:
>
> 0x55: TrigReg1.TRIGREG_MST
>
> 0xAA: TrigReg1.TRIGREG_CHKR
>
> 0xFF: TrigReg1.TRIGREG_MSTANDCHKR

<u>Register Content Modification:</u>

This function is assumed to be called only once in cold init by this
function and at a 2ms periodic rate in warm init state by the Temporal
monitor function (ES005A). The design therefore doesn’t include
protection for something interrupting this sub-function. It is possible
that the code could execute with ECM Compare Error Notification and
Interrupts turned Off in Warm Init during Temporal Monitor testing.

If these registers are tested during run-time for their correct value,
it must be ensured that the test cannot interrupt this function.

### Implementation

#### Initialization

N/A

#### Event Driven (CtrlErrOut)

<u>Pseudo Code:</u>

CtrlErrOut (PinSt, TrigReg)

{

// Save contents of ECMEMK0, EMCIRCFG0, ECMMICFG0 and ECMNMICFG0 to a
temp

// variable in RAM

> ECMEMK0_Temp = ECMEMK0;
>
> ECMMICFG0_Temp = ECMMICFG0;
>
> ECMNMICFG0_Temp = ECMNMICFG0;
>
> ECMIRCFG0_Temp = ECMIRCFG0;

// Set the bit 29 of the ECMEMK0 register to “masked”

> ECMEMK0_Desired = ECMEMK0 \| 0x2000 0000;
>
> WrProtdRegEcm_u32 (ECMEMK0_Desired, Address of ECMEMK0);

// Set the bit 29 of the ECMMICFG0 register to “prohibited”

> ECMMICFG0_Desired = ECMMICFG0 & (\~ (0x2000 0000));
>
> WrProtdRegEcm_u32 (ECMMICFG0_Desired, Address of ECMMICFG0);

// Set the bit 29 of the ECMNMICFG0 register to “prohibited”

ECMNMICFG0_Desired = ECMNMICFG0 & (\~ (0x2000 0000));

WrProtdRegEcm_u32 (ECMNMICFG0_Desired, Address of ECMNMICFG0);

// Set the bit 29 of the ECMIRCFG0 register to “prohibited”

> ECMIRCFG0_Desired = ECMIRCFG0 & (\~ (0x2000 0000));
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Desired, Address of ECMIRCFG0);
>
> If (PinSt == STD_LOW)
>
> {
>
> If (TrigReg = TrigReg1.TRIGREG_MST)
>
> {
>
> //Drive the ERROROUT pin to Low Level
>
> WrProtdRegEcmm_u08 (0x01, Address of ECMMESET);
>
> }
>
> ElseIf (TrigReg = TrigReg1.TRIGREG_CHKR)
>
> {
>
> //Drive the ERROROUT pin to Low Level
>
> WrProtdRegEcmc_u08 (0x01, Address of ECMCESET);
>
> }
>
> Else
>
> {
>
> //Drive the ERROROUT pin to Low Level
>
> WrProtdRegEcmm_u08 (0x01, Address of ECMMESET);
>
> WrProtdRegEcmc_u08 (0x01, Address of ECMCESET);
>
> }

}

Else

{

> // Clear error flags by setting the ECMCLSSE130 bit of the ECMESSTC1
> register
>
> ECMESSTC1_Desired = ECMESSTC1 \| 0x4000 0000;
>
> WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);
>
> //Drive the ERROROUT pin to High Level
>
> WrProtdRegEcmm_u08 (0x01, Address of ECMMECLR);
>
> WrProtdRegEcmc_u08 (0x01, Address of ECMCECLR);

}

// Clear error flags by setting the ECMCLSSE029 bit of the ECMESSTC0
register

ECMESSTC0_Desired = 0x2000 0000;

WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);

// Restore the contents of the ECMEMK0, EMCIRCFG0, ECMMICFG0 and
ECMNMICFG0

// register

WrProtdRegEcm_u32 (ECMEMK0_Temp, Address of ECMEMK0);

> WrProtdRegEcm_u32 (ECMMICFG0_Temp, Address of ECMMICFG0);
>
> WrProtdRegEcm_u32 (ECMNMICFG0_Temp, Address of ECMNMICFG0);
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Temp, Address of ECMIRCFG0);

}

#### Periodic

N/A

### Verification Method

N/A

## Sub-Function: ECM Startup Master/Checker nERROR Output Control Fault

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

**SAN 640:**

The error status registers ECMmESSTR0/1 **shall** be checked and cleared
before executing any safety application.

If there is a mismatch between ECM master and checker an ECM compare
error will be set in the ECMmESSTR0/1 register. In that case, the safe
state **shall** be entered.

**\[SAN-P1x-1605\]**

The delay timer **shall** not be used for response on CLMA errors

The activation of "delay timer" within the ECM **shall** not be
configured for the error sources related to CLMA because no proper
counting is guaranteed due to clock failures.

### Description

This sub-function is responsible for verifying that the ERROROUT output
signal from the ECM is driven Low independently by the ECM Master and
ECM Checker.

Register Info:

|                                                         |                                                          |                 |     |
|----------------------|-----------------------------|-----------|----------|
| Register                                                | Use                                                      | Register Access |     |
|                                                         |                                                          | SV              | UM  |
| ECMMESSTR1 (ECM Master Error Source Status Register 1)  | Indicates the state of individual internal error sources | R/W             | R/W |
| ECMCESSTR1 (ECM Checker Error Source Status Register 1) | Indicates the state of individual internal error sources | R/W             | R/W |

### Rationale

This design assumes that the ERROROUT pin can be set ‘High’ by writing
to both the register ECMMECLR and ECMCECLR. If any other error is
causing the ErrorOut pin to go low in case of a fault, the pin will
remain low despite trying to set it high through the ECMmECLR (m=M/C).

This design assumes that the ERROROUT pin can be set Low by writing to
either the register ECMMESET or ECMCESET.

This test shall be executed only after ECM has been initialized and the
ErrorOut Pin has been manually driven ‘High’. A check is made to see if
the ErrorOut is pulled down to ‘Low’ due to any fault. In that scenario,
we shall skip all the tests because it is evident that the ErrorOut Pin
can be pulled Low because of a fault.

ECM Start up fault is intended to cover the **SAN 640.**

### Implementation

#### Initialization (EcmOutpAndDiagcInit1)

Write the Pseudo code here:

// Check if ECM Error Status Registers have all the Error Status Bits
set as 0

// ECMmESSTR1 Bit 31 is the loopback bit which is expected to be HIGH
after Mcu_Init()

ChkForStrtUpCnd (Address of ExecStrtUpTest)

// If ERROROUT output is normal output AND this is a reset where we run
start up test

If ((ECMMSSE131 == 1 AND ECMCSSE131 == 1) AND (ExecStrtUpTest = TRUE))

{

// Set ERROROUT output Low by only changing the value in ECMMESET Master
Register

CtrlErrOut (STD_LOW, TrigReg1.TRIGREG_MST);

If (ECMMSSE131 == 1 OR ECMCSSE131 == 1)

{

> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_MSTERROUTPCTRLFLT, ECMMESSTR1);

}

Else

{

> // Set ERROROUT output High by changing the value in ECMMESET (Master)
> Register
>
> CtrlErrOut (STD_HIGH, TrigReg1.TRIGREG_MST);
>
> If (ECMMSSE131 == 1 AND ECMCSSE131 == 1)
>
> {
>
> // Set ERROROUT output Low by only changing the value in ECMCESET
> Checker
>
> // Register
>
> CtrlErrOut (STD_LOW, TrigReg1.TRIGREG_CHKR);
>
> If (ECMMSSE131 == 1 OR ECMCSSE131 == 1)
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_CHKRERROUTPCTRLFLT,
> ECMMESSTR1);
>
> }
>
> Else
>
> {
>
> // Set ERROROUT output High by changing the value in ECMCESET
>
> // (Checker) Register
>
> CtrlErrOut (STD_HIGH, TrigReg1.TRIGREG_CHKR);
>
> }
>
> }

}

}

Else

{

// Do nothing because if there was a fault, it will be handled later in
the application

}

#### Initialization (EcmOutpAndDiagcInit2)

This is an empty Initialization function that contains no logic.

EcmOutpAndDiagcInit2 is an RTE function which is required for memory
mapping PIM and Calibration definitions.

#### Event Driven

N/A

#### Periodic

N/A

### Verification Method

N/A

## Sub-Function: EI Interrupt StartUp Test

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

**\[SAN-P1x-1604\]**

If the interrupt generation is configured in ECM as a response to an
error notification, an interrupt test at start-up **shall** be executed.

### Description

This sub-function is responsible for verifying that the interrupts
generated are propagated from the ECM to the INTC1.

<u>Register Info:</u>

|                                               |                                                                                                                                                             |                 |           |
|----------------------|-----------------------------|-----------|----------|
| Register                                      | Use                                                                                                                                                         | Register Access |           |
|                                               |                                                                                                                                                             | SV              | UM        |
| ECMEPE1 (ECM Pseudo Error Trigger Register 1) | The ECM pseudo error trigger register 1 is used to generate a pseudo error for test purposes.                                                               | R/W             | R/W       |
| EIC8 (EI Level Interrupt Control Registers 8) | These registers are used to set interrupt control conditions for each EI level interrupt source, and one register is provided for each source of this type. | R/W             | Read Only |

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Design/Design/mediax/media/image3.png"
style="width:6.5125in;height:9.19028in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Design/Design/mediax/media/image4.png"
style="width:6.69861in;height:7.84861in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM104A_EcmOutpAndDiagc_Design/Design/mediax/media/image5.png"
style="width:6.69861in;height:7.35833in" />

### Rationale

ECM is directly connected to INTC1. This interrupt is from the type
“synchronous edge detection” which means the flag will be automatically
cleared when the CPU has acknowledged the request. Thus the SW will not
be able to check the flag. Hence we disable all EI interrupt, inject
error and monitor the pending interrupt flag. If the interrupt flag is
set, we can confirm that interrupt has propagated to the INTC1.

ECM110 is responsible of setting the FACI related fault. This fault
happens only on a FACI reset transfer error. It is not possible that we
would set this bit when this start up test is running. FACI Reset
Transfer Error happens only when we come out of a reset. ECM110 is not
set on a Software Reset.

Similar check is not possible for ECM FE level interrupt because it is
not “maskable”. In this case execution of ISR needs to be checked. The
microcontroller design does not allow us to return from FE NMI
interrupt.

Since running an FE level interrupt would force a reset, it is
undesirable to run this test.

Errors that are configured as FE interrupts are also configured to set
the ERROROUT pin to go low. The controller would hence reach a safe
state even if the interrupt was not triggered. The ERROROUT pin has a
redundant feature that can be driven low by either Master or the Checker
ECM, for which there is a start up test mentioned in section “ECM
Startup Master/Checker nERROR Output Control Fault”. Because of this,
Nexteer has decided to exclude the ECM FE Interrupt Start Up test.

### Implementation

#### Initialization (EcmOutpAndDiagcInit3)

Write the Pseudo code here:

ChkForStrtUpTest (Address of ExecStrtUpTest)

If (ExecStrtUpTest == TRUE & ECMMESSTR0 == 0x0000 0000 & ECMCESSTR0 ==
0x0000 0000 & ECMMESSTR1 == 0x0000 0000 & ECMCESSTR1 == 0x0000 0000)

{

> // Global disable all EINT interrupts
>
> SuspendAllInterrupts();
>
> ECMMICFG1_Saved = ECMMICFG1;
>
> // Set the bit ECMMIE110 of the ECMMICFG0 register to enable it as an
> EI Interrupt
>
> ECMMICFG1_Desired = ECMMICFG1 \| (0x0000 0400);
>
> WrProtdRegEcm_u32 (ECMMICFG1_Desired, Address of ECMMICFG1);
>
> // Store the value of EIC8 into a temp var
>
> MaskState = osGetIMRmEI (8);
>
> // Enable interrupt processing for ECM EI interrupt; EIC8.EIMK8 = 0
>
> osClearIMRmEI (8); 
>
> // Generate ECM error using pseudo trigger register for the error
> source configured for EI interrupt.
>
> // For the purpose of this test, ECMmSSE110 is chosen to invoke an EI
> Interrupt
>
> ECMPE1_Desired = 0x0000 0400;
>
> WrProtdRegEcm_u32 (ECMPE1_Desired, Address of ECMPE1);

// Ensure the Error is injected before we check for the interrupt flag

> \_\_asm ("SYNCM");
>
> // Read the EIC8 Register
>
> EIC8_Val = osReadICR16 (addr of EIC8);
>
> // At this point ECM EI level ISR will NOT be executed but the
> EIC8.EIRF8 will be set to 1
>
> If ((EIC8_Val & 0x1000) == 0)
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_EIINTRPTSTRTUPFLT, EIC8_Val);
>
> }
>
> osClearICRReq (addr of EIC8);
>
> If (MaskState != 0)
>
> {
>
> // Disable interrupt processing for ECM EI interrupt; EIC8.EIMK8 = 0
>
> osSetIMRmEI (8);
>
> }
>
> // Clear the bit ECMMIE110 of the ECMMICFG0 register to disable it as
> an EI Interrupt
>
> ECMMICFG1_Desired = ECMMICFG1_Saved;
>
> WrProtdRegEcm_u32 (ECMMICFG1_Desired, Address of ECMMICFG1);
>
> // Clear the bit ECMmSSE110 bit of the ECMmESSTR1 register
>
> ECMESSTC1_Desired = ECMESSTC1 \| (0x0000 0400);
>
> WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);

ResumeAllInterrupts ();

}

Else If ((ECMMSSE110 == 1) OR (ECMCSSE110 == 1))

{

SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC\_ FACIRSTTRFERR, 0);

}

Else If (ECMMESSTR0 != 0x0000 0000 OR ECMCESSTR0 != 0x0000 0000 OR
ECMMESSTR1 != 0x0000 0000 OR ECMCESSTR1 != 0x0000 0000)

{

GetMcuDiagcIdnData (Address of McuDiagcData0);

If (McuDiagcData0 != McuDiagc1.MCUDIAGC_ECMRST)

{

> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_ECMSTSSTRTUPFLT, 0);

// The ECM Status Bits get cleared in the MCU Init following this
Function

}

}

Else

{

// Do Nothing because the reset cause is not one where we run Start up
Test

}

#### Event Driven

N/A

#### Periodic

N/A

### Verification Method

N/A

## Sub-Function: Pseudo Error Injection StartUp Test

Return to sub-function list link: Sub-Function In This Document

### NTCs

N/A

### SAN Linkage

**\[SAN-P1x-1603\]**

The Logic of the ECM master/checker and the related compare unit is
targeted by LBIST except the ECMmESSTR0/1 registers. Therefore, the
proposed pseudo-error test^44^ **shall** be executed once at start-up.

44 In dynamic mode of the ERROROUTZ, it is sufficient to check whether
the (injected) error flag are set. Thus, the responses such as ECM reset
and interrupts can be kept masked.

### Description

The Logic of the ECM master/checker and the related compare unit is
targeted by LBIST except the ECMmESSTR0/1 registers. This startup test
is to verify that ECMmESSTR0/1 registers record errors whenever their
corresponding error bits are triggered.

Register Info:

|                                                              |                                                                                                            |                 |     |
|----------------------|-----------------------------|-----------|----------|
| Register                                                     | Use                                                                                                        | Register Access |     |
|                                                              |                                                                                                            | SV              | UM  |
| ECMESSTC0 (ECM Error Source Status Clear Trigger Register 0) | Used to clear the individual error source status of the ECM master/checker error source status register 0. | R/W             | R/W |
| ECMESSTC1 (ECM Error Source Status Clear Trigger Register 1) | Used to clear the individual error source status of the ECM master/checker error source status register 1. | R/W             | R/W |
| ECMEPE0 (ECM Pseudo Error Trigger Register 0)                | The ECM pseudo error trigger register 0 is used to generate a pseudo error for test purposes.              | R/W             | R/W |
| ECMEPE1 (ECM Pseudo Error Trigger Register 1)                | The ECM pseudo error trigger register 1 is used to generate a pseudo error for test purposes.              | R/W             | R/W |
| ECMIRCFG0 (ECM Internal Reset Configuration Register 0)      | Used to set the generation of internal resets (ECMRES) in response to internal errors.                     | R/W             | R/W |
| ECMMICFG0 (ECM EI Level Interrupt Configuration Register 0)  | Used to set the generation of the EI level interrupts.                                                     | R/W             | R/W |
| ECMNMICFG0 (ECM FE Level Interrupt Configuration Register 0) | Used to set the generation of FE level interrupts.                                                         | R/W             | R/W |
| ECMIRCFG1 (ECM Internal Reset Configuration Register 1)      | Used to set the generation of internal resets (ECMRES) in response to internal errors.                     | R/W             | R/W |
| ECMMICFG1 (ECM EI Level Interrupt Configuration Register 1)  | Used to set the generation of the EI level interrupts.                                                     | R/W             | R/W |
| ECMNMICFG1 (ECM FE Level Interrupt Configuration Register 1) | Used to set the generation of FE level interrupts.                                                         | R/W             | R/W |

### Rationale

This test involves injecting an error into all the available bits of the
ECMmESSTR0 and ECMmESSTR1 register. Some these bits could have been
configured as an EI level interrupt trigger or FE level Interrupt or an
Internal Reset Generation. In order to prevent these bits from
triggering an interrupt or reset, all the bits must be masked. The
registers that would be used to mask the interrupts will be loaded with
their previous value after the test is complete to ensure the system
behaves as we expect it to have been configured.

This test also assumes the following:

1\) ERROROUT pin is in inactive state, i.e. high

2\) All ECM error status flags for all error sources are cleared

In case either of the 2 mentioned conditions above are not met, the test
will not be executed.

This test assumes that the non-dynamic behavior of the error signal
(ERROROUT) is being used.

When out of an ECM Reset, the BRAMDAT0 is loaded with ECMRESET value and
cannot be over written. This value is then checked in the Reset Cause
and the ECM Bits are checked if it's a Lockstep Error and the NTC is
logged.

The MCU_Init() clears the ECM Status Register Bits if the RESF bits have
a Non-Zero value. But the RESF Bits are cleared by the bootloader. Hence
the ECM Status Register Bits are never cleared by the MCU_Init().

On a Power On Reset, if no errors are observed, the ECM Bits are all
seen to be 0. If any of the safety critical (EI or FE Level Interrupt
Configured) ECM Bits are set after the MCU_Init(), an exception is
recorded and a Pre-OS Exception is logged. However, there is a small
window between EcmOutpAndDiagcInit3 and MCU_Init() where an ECM flag can
be set and go unnoticed. It is to capture this scenario, a check for ECM
Bit is placed in the Else condition of EcmOutpAndDiagcInit4 and set as
ECM Start up fault.

### Implementation

#### Initialization (EcmOutpAndDiagcInit4)

<u>Pseudo code:</u>

ChkForStrtUpCnd (Address of ExecStrtUpTest)

If (ExecStrtUpTest == TRUE)

{

> If (ECMMESSTR0 = 0x0000 0000 AND ECMCESSTR0 = 0x0000 0000 AND
> ECMMESSTR1 = 0x8000 0000 AND ECMCESSTR1 = 0x8000 0000)
>
> {
>
> ECMMICFG0_Temp = ECMMICFG0;
>
> ECMNMICFG0_Temp = ECMNMICFG0;
>
> ECMIRCFG0_Temp = ECMIRCFG0;
>
> ECMMICFG1_Temp = ECMMICFG1;
>
> ECMNMICFG1_Temp = ECMNMICFG1;
>
> ECMIRCFG1_Temp = ECMIRCFG1;
>
> // Set the ALL bits of the ECMMICFG0 to be configured as EI Interrupt
> generation disabled
>
> ECMMICFG0_Desired = ECMMICFG0 & (\~ (0xFDFF DFF3));
>
> WrProtdRegEcm_u32 (ECMMICFG0_Desired, Address of ECMMICFG0);
>
> // Set the ALL bits of the ECMNMICFG0 to be configured as FE Interrupt
> generation disabled
>
> ECMNMICFG0_Desired = ECMNMICFG0 & (\~ (0xFDFF DFF3));
>
> WrProtdRegEcm_u32 (ECMNMICFG0_Desired, Address of ECMNMICFG0);
>
> // Set the ALL bits of the ECMIRCFG0 to be configured as internal
> reset (ECMRES) generation disabled
>
> ECMIRCFG0_Desired = ECMIRCFG0 & (\~ (0xFDFF DFF3));
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Desired, Address of ECMIRCFG0);
>
> // Set the ALL bits of the ECMMICFG1 to be configured as EI Interrupt
> generation disabled
>
> ECMMICFG1_Desired = ECMMICFG1 & (\~ (0x0000 07F7));
>
> WrProtdRegEcm_u32 (ECMMICFG1_Desired, Address of ECMMICFG1);
>
> // Set the ALL bits of the ECMNMICFG1 to be configured as FE Interrupt
> generation disabled
>
> ECMNMICFG1_Desired = ECMNMICFG1 & (\~ (0x0000 07F7));
>
> WrProtdRegEcm_u32 (ECMNMICFG1_Desired, Address of ECMNMICFG1);
>
> // Set the ALL bits of the ECMIRCFG1 to be configured as internal
> reset (ECMRES) generation disabled
>
> ECMIRCFG1_Desired = ECMIRCFG1 & (\~ (0x2000 07F7));
>
> WrProtdRegEcm_u32 (ECMIRCFG1_Desired, Address of ECMIRCFG1);
>
> // Inject all errors by setting the corresponding bit in ECMPEn
>
> ECMPE0_Desired = 0xFDFF DFF3;
>
> WrProtdRegEcm_u32 (ECMPE0_Desired, Address of ECMPE0);
>
> ECMPE1_Desired = 0x2000 07F7;
>
> WrProtdRegEcm_u32 (ECMPE1_Desired, Address of ECMPE1);
>
> // Check ERROROUT output state
>
> If (ECMMSSE131 == 0)
>
> {
>
> // Set the ERROROUT pin to inactive state, HIGH
>
> CtrlErrOut (HIGH, TrigReg1.TRIGREG_MSTANDCHKR)
>
> // Clear all errors by setting the corresponding bit in ECMESSTCn
>
> ECMESSTC0_Desired = 0xFDFF DFF3;
>
> WrProtdRegEcm_u32 (ECMESSTC0_Desired, Address of ECMESSTC0);
>
> ECMESSTC1_Desired = 0x6000 07F7;
>
> WrProtdRegEcm_u32 (ECMESSTC1_Desired, Address of ECMESSTC1);
>
> If (ECMMESSTR0 != 0x0000 0000 AND ECMMESSTR1 != 0x8000 0000)
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_ECMPSDOERRINJFLT, 1);
>
> }
>
> }
>
> Else
>
> {
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC\_ ECMPSDOERRINJFLT, 2);
>
> }
>
> // Write back the initial values of ECMMICFG0, ECMNMICFG0 and
> ECMIRCFG0
>
> WrProtdRegEcm_u32 (ECMMICFG0_Temp, Address of ECMMICFG0);
>
> WrProtdRegEcm_u32 (ECMNMICFG0_Temp, Address of ECMNMICFG0);
>
> WrProtdRegEcm_u32 (ECMIRCFG0_Temp, Address of ECMIRCFG0);
>
> // Write back the initial values of ECMMICFG1, ECMNMICFG1 and
> ECMIRCFG1
>
> WrProtdRegEcm_u32 (ECMMICFG1_Temp, Address of ECMMICFG1);
>
> WrProtdRegEcm_u32 (ECMNMICFG1_Temp, Address of ECMNMICFG1);
>
> WrProtdRegEcm_u32 (ECMIRCFG1_Temp, Address of ECMIRCFG1);

}

> Else
>
> {
>
> // Bit was set during the window where the EcmOutpAndDiagcInit3 ends
> and the MCU_Init() configuration is complete
>
> SetMcuDiagcIdnData (McuDiagc1.MCUDIAGC_ECMSTSSTRTUPFLT, 0);
>
> }

}

#### Event Driven

N/A

#### Periodic

N/A

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
<td>10/20/2015</td>
<td>EA4#1736</td>
<td>SK</td>
<td>Initial Release</td>
</tr>
<tr class="odd">
<td>02.00.00</td>
<td>01/22/2016</td>
<td>EA4#3418</td>
<td>SK</td>
<td>Configuration updated for ECM and SAN requirements added in section
3.2</td>
</tr>
<tr class="even">
<td>02.01.00</td>
<td>02/02/2016</td>
<td>EA4#3635</td>
<td>SK</td>
<td>EI Interrupt enabled for for ECM Bit: ADC Parity, Added EI Interrupt
Start Up Test and Pseudo Error Injection Start Up Test, Added function
“ChkForStrtUpTest” for startup check of a function.</td>
</tr>
<tr class="odd">
<td>02.01.01</td>
<td>02/12/2016</td>
<td>EA4#3635</td>
<td>SK</td>
<td>Typing Error in EcmOutpAndDiagcInit4 Pseudo Code</td>
</tr>
<tr class="even">
<td>02.02.00</td>
<td>03/17/2016</td>
<td>EA4#4520</td>
<td>SK</td>
<td>Changed the DTS Double RAM Error to be configured to a SYSERR</td>
</tr>
<tr class="odd">
<td>03.00.00</td>
<td>03/29/2016</td>
<td>EA4#4866</td>
<td>GM</td>
<td><p>Added ChkForStrtUpCnd in EcmOutpAndDiagcInit1</p>
<p>Added McuDiagc1.MCUDIAGC_ FACIRSTTRFERR</p>
<p>Updated ECM configuration table</p></td>
</tr>
<tr class="even">
<td>03.01.00</td>
<td>04/04/2016</td>
<td>EA4#5192</td>
<td>GM</td>
<td><p>All Peripheral functions RAM ECC Single Bit Error (Soft Fault) no
longer an EI interrupt</p>
<p>Added condition to IF statement in section 3.2.5.1 ExecStrtUpTest =
TRUE</p></td>
</tr>
<tr class="odd">
<td>03.02.00</td>
<td>04/18/2016</td>
<td>EA4#</td>
<td>SK</td>
<td>ECM Error Source 4 and 5 interchanged in the spreadsheet</td>
</tr>
<tr class="even">
<td>03.03.00</td>
<td>06/14/2016</td>
<td>EA4#6364</td>
<td>SK</td>
<td>FACI check moved to Init3</td>
</tr>
<tr class="odd">
<td>04.00.00</td>
<td>07/25/2016</td>
<td>EA4#6648</td>
<td>SK</td>
<td><p>ECM Config Change:</p>
<p>SPI Double Bit – EI Interrupt to No Interrupt</p>
<p>Code Flash Single Bit – SYSERR to EI Interrupt</p>
<p>Added logic in Init4 for MCUDIAGC_ECMSTSSTRTUPFLT</p></td>
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

{% endraw %}