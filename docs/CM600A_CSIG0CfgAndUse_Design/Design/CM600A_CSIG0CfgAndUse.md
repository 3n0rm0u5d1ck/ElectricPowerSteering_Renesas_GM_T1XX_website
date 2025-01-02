---
layout: default
title: CM600A_CSIG0CfgAndUse
nav_order: 1
parent: Component Design
---
{% raw %}
**CSIG0 Configuration And Use**

**FDD \# CM600A**

[1. High Level Description 3](#high-level-description)

[2. Derived Requirements 3](#derived-requirements)

[Sub-Function Data Flow 3](#sub-function-data-flow)

[3. Design Rationale 4](#design-rationale)

[4. Sub-Functions 4](#sub-functions)

[4.1. Sub-Function: 4](#sub-function)

[4.1.1. Hardware Related Design 4](#hardware-related-design)

[4.1.2. Software Related Design 4](#software-related-design)

4.1.2.1. SPI Driver Configurations (General).……………..…………………………………..6

4.1.2.2. SPI Driver Configurations (PwrSply/TmplMonr
specific)..……...…………………..7

4.1.2.3. PORT Configurations (PwrSply/TmplMonr
specific)..……………………………..27

4.1.2.4. OS Configurations (PwrSply/TmplMonr
specific)..…….…………………………..27

4.1.2.5. API Descriptions…………………………….…….…….……………………………..28

[5. Timing / Execution Constraints 29](#timing-execution-constraints)

[5.1. Rationale / Comments 29](#rationale-comments)

[5.2. Rates and State Execution 29](#rates-and-state-execution)

[6. Serial Communications Interfaces
29](#serial-communications-interfaces)

[7. Additional Information 30](#additional-information)

[8. Revision Record & Change Approval
31](#revision-record-change-approval)

# High Level Description

FDD CM-600X provides the interface to the ES FDDs which need to
communicate with the external peripherals connected to the main micro
through CSIG0 SPI channel. RENESAS AUTOSAR SPI driver is used to achieve
the communication requirements. CM-600A constitutes the required
configurations of RENESAS AUTOSAR SPI DRIVER for communicating with
PwrSply/TmplMonr IC through CSIG0 SPI channel. This document also
contains the API (client/server functions) descriptions used for
communicating with PwrSply/TmplMonr IC using CSIG0.

Following picture depicts the top level interface.

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM600A_CSIG0CfgAndUse_Design/Design/mediax/media/image1.png"
style="width:5.99722in;height:3.10486in" />

Note: Implementation of CM600A will be a part of the RENESAS AUTOSAR SPI
driver component which represents the driver configuration and APIs (or
interfaces) specific to CSIG0 SPI channel used for PwrSply/TmplMonr IC.

# Derived Requirements

None.

#  Sub-Function Data Flow [sub-function-data-flow]

None.

# Design Rationale

None.

# Sub-Functions

## Sub-Function: 

### Hardware Related Design

None.

### Software Related Design

Following version (version used in Synergy) of RENESAS AUTOSAR SPI
driver is used to make the configurations for CSIG0.

*Spi_Renesas_Ar4.0.3_01.05.00_0*

RENESAS SPI driver is developed following the AUTOSAR SPI driver/handler
specifications. So the following definitions from the AUTOSAR SPI driver
specification need to be realized to understand the configuration.

|                   |                                                                                                                                                                                                                                                   |
|------------|------------------------------------------------------------|
| ***Definition:*** | ***Description:***                                                                                                                                                                                                                                |
| Channel           | A Channel is a software exchange medium for data that are defined with the same criteria: Config. Parameters, Number of Data elements with same size and data pointers (Source & Destination) or location.                                        |
| Job               | A Job is composed of one or several Channels with the same Chip Select (is not released during the processing of Job). A Job is considered atomic and therefore cannot be interrupted by another Job. A Job has an assigned priority.             |
| Sequence          | A Sequence is a number of consecutive Jobs to transmit but it can be rescheduled between Jobs using a priority mechanism. A Sequence transmission is interruptible (by another Sequence transmission) or not depending on a static configuration. |

For simplicity and to make sure the minimal changes of this FDD for any
future changes in the ES function (which uses/depends on this FDD) it is
decided to define the Channel, Job and Sequence as following.

Channel: A bunch of channels are defined which can be used to transmit
read/write command for any register to the PwrSply/TmplMonr IC. No
channel ID is specific to any particular register. So any channel can be
used for any register read/write operation.

Job: For each of the channel a job is defined. So one job contains only
one channel.

Sequence: For each of the job a sequence is defined. So one sequence
contains only one job.

Note: Sequence is used to initiate a transmission. Channel maintains the
Tx/Rx buffer. Each sequence is tied with one specific channel.

SPI driver configuration constitutes three main sections/containers –
‘SpiDriver’, ‘SpiGeneral’ and ‘SpiPublishedInformation’. The last two
containers contain the general configurations which are common for all
Spi channels used and hence fixed for a program or for all program. So
only the container ‘SpiDriver’ contains the peripheral specific
configurations which is PwrSply/TmplMonr IC.

#### SPI Driver Configurations (General)

Table below contains the configurations for ‘SpiGeneral’ and
‘SpiPublishedInformation’ containers.

|                                            |                            |                                                                                                                                 |                                                                                                                         |
|-----------------------|---------------|-------------------|---------------|
| **Configuration Parameter**                | **Value**                  | **Rationale**                                                                                                                   | **Remark**                                                                                                              |
|                                            |                            |                                                                                                                                 |                                                                                                                         |
| **Container: Spi/SpiPublishedInformation** | <span class="mark"></span> | <span class="mark"></span>                                                                                                      | <span class="mark"></span>                                                                                              |
| Short Name                                 | SpiPublishedInformation    | <span class="mark"></span>                                                                                                      | <span class="mark"></span>                                                                                              |
| Max Hw Unit                                | 5                          | Five Hw units are available in Renesas R7F701311 device. CSIG0, CSIH0, CSIH1, CSIH2, and CSIH3                                  | This parameter can be made to 3 as CSIH1 and CSIH3 do not use RENESAS Spi driver for communication with its peripheral. |
| <span class="mark"></span>                 |                            |                                                                                                                                 | <span class="mark"></span>                                                                                              |
| **Container: Spi/SpiGeneral**              | <span class="mark"></span> | <span class="mark"></span>                                                                                                      | <span class="mark"></span>                                                                                              |
| Short Name                                 | SpiGeneral                 | <span class="mark"></span>                                                                                                      | <span class="mark"></span>                                                                                              |
| Already Init Det Check                     | FALSE                      |                                                                                                                                 | Recommended to be retained TRUE during development phase                                                                |
| Cancel Api                                 | FALSE                      | Switches the Spi_Cancel function ON or OFF. Not required per current requirement.                                               |                                                                                                                         |
| Channel Buffers Allowed                    |  0                         | 0 = Internal Buffer. 1 = External Buffer. There will not be more than 128 words transactions required. Hence IB should suffice. |                                                                                                                         |
| Critical Section Protection                | TRUE                       | Interrupt blocking time by SchM is around 1us                                                                                   |                                                                                                                         |
| Data Consistency Check Enable              | TRUE                       | It is recommended to enable this as per the Safety Application Note                                                             |                                                                                                                         |
| Data Width Selection                       | BITS_16                    | Both Gate Drive and Power Supply have max of 16 bit SPI transfers                                                               |                                                                                                                         |
| Dev Error Detect                           | FALSE                      |                                                                                                                                 | Recommended to be retained TRUE during development phase                                                                |
| Device Name                                | R7F701311                  |                                                                                                                                 |                                                                                                                         |
| Dma Mode                                   | FALSE                      | Not required as the data length is not so big                                                                                   |                                                                                                                         |
| Dma Type Used                              | SPI_DMA_TYPE_TWO           | This parameter could be configured to only one value.                                                                           |                                                                                                                         |
| High Priority Hw Handling Enable           | FALSE                      | Currently no requirement is seen for this.                                                                                      |                                                                                                                         |
| Hw Status Api                              | FALSE                      | Currently no requirement is seen for this API.                                                                                  |                                                                                                                         |
| Interruptible Seq Allowed                  | FALSE                      | Currently no requirement is seen for this functionality.                                                                        |                                                                                                                         |
| Level Delivered                            | 1                          | Current assumption is to use Asynchronous mode with interrupt based job processing.                                             |                                                                                                                         |
| Max Baudrate                               | PCLK_DIV_BY_8              | Maximum acceptable baud rate for the Job should be less than or equal to PCLK/8 (which is 10Mbps)                               |                                                                                                                         |
| Persistent HW Configuration                | TRUE                       | Enabled from safety perspective                                                                                                 |                                                                                                                         |
| Seq Start Notification Enable              | FALSE                      |                                                                                                                                 |                                                                                                                         |
| Support Concurrent Sync Transmit           | FALSE                      | This is not applicable for Level 1                                                                                              |                                                                                                                         |
| Sync Seq End Notification Enable           | FALSE                      | This is not applicable for Level 1                                                                                              |                                                                                                                         |
| Time Out                                   | 65535                      |                                                                                                                                 |                                                                                                                         |
| Version Check External Modules             | TRUE                       | Enabled from safety perspective                                                                                                 |                                                                                                                         |
| Version Info Api                           | FALSE                      |                                                                                                                                 |                                                                                                                         |

The DEM error reporting related configuration is also common for all Spi
channels though this resides under the ‘SpiDrivers’ container. Table
below contains DEM error reporting configuration.

|                                                                  |                                 |                                                                                             |                            |
|--------------------------|-----------------------|----------------|--------|
| **Configuration Parameter**                                      | **Value**                       | **Rationale**                                                                               | **Remark**                 |
|                                                                  |                                 |                                                                                             |                            |
| **Container: Spi/SpiDrivers/SpiDriver/SpiDemEventParameterRefs** | <span class="mark"></span>      |                                                                                             |                            |
| <span class="mark"></span>                                       |                                 |                                                                                             |                            |
| Short Name                                                       | SpiDemEventParameterRefs        | <span class="mark"></span>                                                                  | <span class="mark"></span> |
| E DATA TX TIMEOUT FAILURE                                        | SPI\_ E_DATA_TX_TIMEOUT_FAILURE | Reference to the DemEventParameter which shall be issued when a time out error was detected | <span class="mark"></span> |
| E HARDWARE ERROR                                                 | SPI\_ E_HARDWARE_ERROR          | Reference to the DemEventParameter which shall be issued when a hardware error was detected | <span class="mark"></span> |

#### SPI Driver Configurations (PwrSply/TmplMonr specific)

Container/section ‘SpiDriver’ contains the PwrSply/TmplMonr specific
configurations which are divided into the following sub containers:

SpiChannels

SpiDmas

SpiExternalDevices

SpiJobs

SpiMemoryModes

SpiSequences

SpiDemEventParameterRefs

Table below contains all of the channels definitions for
PwrSply/TmplMonr which resides under the container ‘SpiChannels’.

|                                                     |             |                                                                                                              |                                      |
|-----------------------|---------------|-------------------|-----------------|
| **Configuration Parameter**                         | **Value**   | **Rationale**                                                                                                | **Remark**                           |
|                                                     |             |                                                                                                              |                                      |
| **Container: Spi/SpiDrivers/SpiDriver/SpiChannels** |             |                                                                                                              |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | TmplMonrCh1 |                                                                                                              | Configuration for TmplMonr channel 1 |
| Channel Id                                          | 52          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | <span class="mark">All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity</span> |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | <span class="mark">For all the cases, a 1 size for IB NBuffer would suffice.</span>                          |                                      |
| Transfer Start                                      | MSB         | <span class="mark">Communicate with MSB first.</span>                                                        |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | TmplMonrCh2 |                                                                                                              | Configuration for TmplMonr channel 2 |
| Channel Id                                          | 53          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | TmplMonrCh3 |                                                                                                              | Configuration for TmplMonr channel 3 |
| Channel Id                                          | 54          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | TmplMonrCh4 |                                                                                                              | Configuration for TmplMonr channel 4 |
| Channel Id                                          | 55          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | TmplMonrCh5 |                                                                                                              | Configuration for TmplMonr channel 5 |
| Channel Id                                          | 56          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh1  |                                                                                                              | Configuration for PwrSply channel 1  |
| Channel Id                                          | 57          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh2  |                                                                                                              | Configuration for PwrSply channel 2  |
| Channel Id                                          | 58          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh3  |                                                                                                              | Configuration for PwrSply channel 3  |
| Channel Id                                          | 59          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh4  |                                                                                                              | Configuration for PwrSply channel 4  |
| Channel Id                                          | 60          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh5  |                                                                                                              | Configuration for PwrSply channel 5  |
| Channel Id                                          | 61          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh6  |                                                                                                              | Configuration for PwrSply channel 6  |
| Channel Id                                          | 62          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh7  |                                                                                                              | Configuration for PwrSply channel 7  |
| Channel Id                                          | 63          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh8  |                                                                                                              | Configuration for PwrSply channel 8  |
| Channel Id                                          | 64          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh9  |                                                                                                              | Configuration for PwrSply channel 9  |
| Channel Id                                          | 65          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |
|                                                     |             |                                                                                                              |                                      |
| Short Name                                          | PwrSplyCh10 |                                                                                                              | Configuration for PwrSply channel 10 |
| Channel Id                                          | 66          | To be assigned in sequence                                                                                   |                                      |
| Channel Type                                        | IB          | This prevents additional variable requirements from the Application software                                 |                                      |
| Data Width                                          | 15          | All SPI sequences are 16 bits long which contains 15 bits of data and 1 bit parity                           |                                      |
| Default Data                                        | 0           | Better to set a value which requests a Read of the corresponding Register                                    |                                      |
| Eb Max Length                                       | 1           | EB is not used. Hence this parameter is not applicable.                                                      |                                      |
| Ib NBuffers                                         | 1           | For all the cases, a 1 size for IB NBuffer would suffice.                                                    |                                      |
| Transfer Start                                      | MSB         | Communicate with MSB first.                                                                                  |                                      |

Note: The channel ids used in the above table is for reference only and
do not represent the actual channel number in the implementation.

Table below contains DMA related configuration of PwrSply/TmplMonr which
resides under the container ‘SpiDmas’.

|                                                 |                            |               |            |
|-------------------------|---------------|-----------------|----------------|
| **Configuration Parameter**                     | **Value**                  | **Rationale** | **Remark** |
|                                                 |                            |               |            |
| **Container: Spi/SpiDrivers/SpiDriver/SpiDmas** | <span class="mark"></span> |               |            |
| <span class="mark"></span>                      |                            |               |            |
|                                                 | NONE                       |               |            |

Table below contains external device configuration for PwrSply/TmplMonr
which resides under the container ‘SpiExternalDevices’.

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 28%" />
<col style="width: 26%" />
<col style="width: 12%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Configuration Parameter</strong></td>
<td><strong>Value</strong></td>
<td><strong>Rationale</strong></td>
<td><strong>Remark</strong></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><strong>Container:
Spi/SpiDrivers/SpiDriver/SpiExternalDevices</strong></td>
<td colspan="3"><mark></mark></td>
</tr>
<tr class="even">
<td><mark></mark></td>
<td></td>
<td></td>
<td><mark></mark></td>
</tr>
<tr class="odd">
<td>Short Name</td>
<td>PwrSplyTmplMonr</td>
<td><mark></mark></td>
<td><mark></mark></td>
</tr>
<tr class="even">
<td>Baudrate Configuration</td>
<td>10</td>
<td><p><mark>Required baudrate is 1Mbps. This is achieved using 2
parameters m and k, where k is configured in ‘Baudrate Configuration’,
and m is configured in ‘Input Clock Select’.</mark></p>
<p><mark>Baudrate = Pclk/((2^m) * k * 2)</mark></p>
<p><mark></mark></p>
<p><mark>Pclk = 80Mhz.</mark></p>
<p><mark>To achieve 1Mbps,</mark></p>
<p><mark>M = 2</mark></p>
<p><mark>K = 10</mark></p></td>
<td><mark></mark></td>
</tr>
<tr class="odd">
<td>Baudrate Register Select</td>
<td>CSIH_BAUDRATE_REGISTER_0</td>
<td><mark></mark></td>
<td></td>
</tr>
<tr class="even">
<td>Baudrate</td>
<td> 0</td>
<td>Unused parameter</td>
<td> </td>
</tr>
<tr class="odd">
<td>Broadcasting Priority</td>
<td>DOMINANT (default)</td>
<td><mark>This parameter is applicable only when priority implementation
is used.</mark></td>
<td> </td>
</tr>
<tr class="even">
<td>Clk2 Cs Count</td>
<td>5</td>
<td><mark>To be adjusted to achieve 30ns</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Clock Frequency Ref</td>
<td>McuHighspeedPeriClk</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Cs Hold Timing</td>
<td>HOLD_TIME_0_POINT_5</td>
<td><mark>Not sure about the difference between this parameter and ‘Clk2
Cs Count’. Mantis ticket 0026854 raised for clarification</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Cs Identifier</td>
<td>NULL (default)</td>
<td>Unused parameter</td>
<td></td>
</tr>
<tr class="even">
<td>Cs Idle Enforcement</td>
<td>TRUE</td>
<td>Since every transfer is limited to 16 bits, this parameter does not
have any significance to our usecase.</td>
<td></td>
</tr>
<tr class="odd">
<td>Cs Idle Timing</td>
<td>IDLE_TIME_3_POINT_5</td>
<td><mark>Idle time must be minimum 300ns</mark></td>
<td></td>
</tr>
<tr class="even">
<td>Cs Inactive After Last Data</td>
<td>TRUE</td>
<td>Since every transfer is limited to 16 bits, this parameter does not
have any significance to our usecase.</td>
<td></td>
</tr>
<tr class="odd">
<td>Cs Inter Data Delay</td>
<td>INTER_DATA_TIME_0_POINT_5</td>
<td><mark>Minimum Inter data delay expected is 10ns</mark></td>
<td></td>
</tr>
<tr class="even">
<td>Cs Polarity</td>
<td>LOW</td>
<td><mark>Chip select is active low for PwrSply/TmplMonr IC</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Cs Selection</td>
<td>CS_VIA_GPIO</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Cs Setup Time</td>
<td>SETUP_TIME_0_POINT_5</td>
<td><mark>Minimum setup time of 30ns required</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Data Shift Edge</td>
<td>LEADING</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Enable Cs</td>
<td>TRUE*</td>
<td><mark>If single chip is connected to the SPI bus, and if the CS pin
of the peripheral chip is connected to ground, then this parameter can
be made FALSE.</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Fifo Time Out</td>
<td>0</td>
<td><mark>FIFO mode is not planned to be used</mark></td>
<td></td>
</tr>
<tr class="even">
<td>Hw Unit</td>
<td>CSIG0</td>
<td>PwrSply/TmplMonr IC uses CSIG0</td>
<td></td>
</tr>
<tr class="odd">
<td>Input Clock Select</td>
<td>PCLK_DIVBY_4</td>
<td><p>Required baudrate is 1Mbps. This is achieved using 2 parameters m
and k, where k is configured in ‘Baudrate Configuration’ and m is
configured in ‘Input Clock Select’.</p>
<p>Baudrate = Pclk/((2^m) * k * 2)</p>
<p>Pclk = 80Mhz.</p>
<p>To achieve 1Mbps,</p>
<p>M = 2</p>
<p>K = 10</p></td>
<td></td>
</tr>
<tr class="even">
<td>Interrupt Delay Mode</td>
<td>FALSE</td>
<td>No delay required in triggering the interrupts</td>
<td></td>
</tr>
<tr class="odd">
<td>Parity Selection</td>
<td>ODD_PARITY</td>
<td><mark>PwrSply/TmplMonr requires Odd parity</mark></td>
<td></td>
</tr>
<tr class="even">
<td>Shift Clock Idle Level</td>
<td>HIGH</td>
<td><mark>PwrSply/TmplMonr chip retains Clock high on idle
state</mark></td>
<td></td>
</tr>
<tr class="odd">
<td>Time Clk2 Cs</td>
<td>0 (default)</td>
<td>Unused parameter</td>
<td></td>
</tr>
</tbody>
</table>

As discussed before every channel is grouped under one Spi job. Table
below contains Spi jobs configurations for PwrSply/TmplMonr which
resides under the container ‘SpiJobs’.

|                                                 |                            |                                                  |                                      |
|-----------------------|---------------|---------------------|--------------|
| **Configuration Parameter**                     | **Value**                  | **Rationale**                                    | **Remark**                           |
|                                                 |                            |                                                  |                                      |
| **Container: Spi/SpiDrivers/SpiDriver/SpiJobs** |                            |                                                  |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | TmplMonrJob1               |                                                  | Job configuration for TmplMonr job 1 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 52                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | TmplMonrCh1                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | TmplMonrJob2               |                                                  | Job configuration for TmplMonr job 2 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 53                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | TmplMonrCh2                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | TmplMonrJob3               |                                                  | Job configuration for TmplMonr job 3 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 54                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | TmplMonrCh3                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | TmplMonrJob4               |                                                  | Job configuration for TmplMonr job 4 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 55                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | TmplMonrCh4                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | TmplMonrJob5               |                                                  | Job configuration for TmplMonr job 5 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 56                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | TmplMonrCh5                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob1                |                                                  | Job configuration for PwrSply job 1  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 57                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh1                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob2                |                                                  | Job configuration for PwrSply job 2  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 58                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh2                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob3                |                                                  | Job configuration for PwrSply job 3  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 59                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh3                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob4                |                                                  | Job configuration for PwrSply job 4  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 60                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh4                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob5                |                                                  | Job configuration for PwrSply job 5  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 61                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh5                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob6                |                                                  | Job configuration for PwrSply job 6  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 62                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh6                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob7                |                                                  | Job configuration for PwrSply job 7  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 63                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh7                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob8                |                                                  | Job configuration for PwrSply job 8  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 64                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh8                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob9                |                                                  | Job configuration for PwrSply job 9  |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 65                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh9                 |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |
|                                                 |                            |                                                  |                                      |
| Short Name                                      | PwrSplyJob10               |                                                  | Job configuration for PwrSply job 10 |
| Device Assignment                               | PwrSplyTmplMonr            |                                                  |                                      |
| Hw Unit Synchronous                             | ASYNCHRONOUS               | Level 1 support only Asynchronous job            |                                      |
| Job End Notification                            | NULL                       |                                                  |                                      |
| Job Id                                          | 66                         | Should be increased sequentially                 |                                      |
| Job Priority                                    | 3 (Default)                |                                                  |                                      |
| Port Pin Select                                 | PORTGROUP_5_PORTPIN_9      | Chip select line                                 |                                      |
| **Sub Container: .…/SpiChannel Lists**          | <span class="mark"></span> |                                                  |                                      |
| Short Name                                      | SpiChannelList             |                                                  |                                      |
| Channel Assignment                              | PwrSplyCh10                |                                                  |                                      |
| Channel Index                                   | 0                          | Specify the order of the channel inside the job. |                                      |

Note: The job ids used in the above table is for reference only and do
not represent the actual job number in the implementation.

Table below contains Spi hardware unit selection and memory mode
selection configuration for PwrSply/TmplMonr which resides under the
container ‘SpiMemoryModes’.

|                                                             |                            |               |            |
|------------------------|-----------------|-------------------|-------------|
| **Configuration Parameter**                                 | **Value**                  | **Rationale** | **Remark** |
|                                                             |                            |               |            |
| **Container: Spi/SpiDrivers/SpiDriver/** **SpiMemoryModes** | <span class="mark"></span> |               |            |
| <span class="mark"></span>                                  |                            |               |            |
| Not Applicable for CSIG0                                    |                            |               |            |

As discussed before every job is grouped under one Spi sequence. Table
below contains Spi sequence configurations for PwrSply/TmplMonr which
resides under the container ‘SpiSequences’.

|                                                      |              |                                                                        |                                       |
|------------------------|---------------|--------------------|--------------|
| **Configuration Parameter**                          | **Value**    | **Rationale**                                                          | **Remark**                            |
|                                                      |              |                                                                        |                                       |
| **Container: Spi/SpiDrivers/SpiDriver/SpiSequences** |              |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | TmplMonrSeq1 |                                                                        | Configuration for TmplMonr sequence 1 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 52           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | TmplMonrJob1 |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | TmplMonrSeq2 |                                                                        | Configuration for TmplMonr sequence 2 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 53           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | TmplMonrJob2 |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | TmplMonrSeq3 |                                                                        | Configuration for TmplMonr sequence 3 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 54           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | TmplMonrJob3 |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | TmplMonrSeq4 |                                                                        | Configuration for TmplMonr sequence 4 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 55           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | TmplMonrJob4 |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | TmplMonrSeq5 |                                                                        | Configuration for TmplMonr sequence 5 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 56           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | TmplMonrJob5 |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq1  |                                                                        | Configuration for PwrSply sequence 1  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 57           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob1  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq2  |                                                                        | Configuration for PwrSply sequence 2  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 58           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob2  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq3  |                                                                        | Configuration for PwrSply sequence 3  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 59           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob3  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq4  |                                                                        | Configuration for PwrSply sequence 4  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 60           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob4  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq5  |                                                                        | Configuration for PwrSply sequence 5  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 61           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob5  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq6  |                                                                        | Configuration for PwrSply sequence 6  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 62           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob6  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq7  |                                                                        | Configuration for PwrSply sequence 7  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 63           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob7  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq8  |                                                                        | Configuration for PwrSply sequence 8  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 64           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob8  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq9  |                                                                        | Configuration for PwrSply sequence 9  |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 65           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob9  |                                                                        |                                       |
|                                                      |              |                                                                        |                                       |
| Short Name                                           | PwrSplySeq10 |                                                                        | Configuration for PwrSply sequence 10 |
| High Priority Hw Sequence                            | FALSE        |                                                                        |                                       |
| Interruptible Sequence                               | FALSE        | It would be recommended to keep all the sequences as Non-Interruptible |                                       |
| Seq End Notification                                 | NULL         |                                                                        |                                       |
| Seq Start Notification                               | NULL         |                                                                        |                                       |
| Sequence Id                                          | 66           | Should be increased sequentially                                       |                                       |
| Job Assignment                                       | PwrSplyJob10 |                                                                        |                                       |

Note: The sequence ids used in the above table is for reference only and
do not represent the actual sequence implemented.

#### PORT Configurations (PwrSply/TmplMonr specific)

It is assumed that the CSIG0 SPI pins are configured properly in PORT
configuration. The required pin settings are below:

|               |               |                   |
|---------------|---------------|-------------------|
| **CSIG0 Pin** | **Port Name** | **Pin Direction** |
|               |               |                   |
| Chip Select   | P5_9          | Out               |
| MISO          | P5_0          | In                |
| MOSI          | P5_1          | Out               |
| SCK           | P5_4          | Out               |

#### OS Configurations (PwrSply/TmplMonr specific)

Following table contains interrupt configurations.

|                                                         |                         |                                                           |                                                    |
|------------------------|-------------------|----------------|--------------|
| **Configuration Parameter**                             | **Value**               | **Rationale**                                             | **Remark**                                         |
|                                                         |                         |                                                           |                                                    |
| **Container: Os/OsIsrs**                                |                         |                                                           |                                                    |
|                                                         |                         |                                                           |                                                    |
| Short Name                                              | SPI_CSIG0_TIC_CAT2_ISR  |                                                           | Configuration for ‘Communication Status Interrupt’ |
| Isr Category                                            | CATEGORY_2              |                                                           |                                                    |
| Isr Enable Nesting                                      | TRUE                    |                                                           |                                                    |
| Isr Accessing Application                               | NONE                    |                                                           |                                                    |
| Isr Resource Ref.                                       | NONE                    |                                                           |                                                    |
| **Sub Container: …../OsIsrUseResourceOccupations**      |                         |                                                           |                                                    |
|                                                         | None                    |                                                           |                                                    |
| **Sub Container: …../** **OsIsrExceptionType**          |                         |                                                           |                                                    |
| Short Name                                              | EIINT                   |                                                           |                                                    |
| Isr Int channel                                         | 175                     |                                                           |                                                    |
| Isr Interrupt Priority                                  | 14                      | Example only. Actual value will be changed in the program |                                                    |
| Isr Interrupt Stack Size                                | 512                     | Example only. Actual value will be changed in the program |                                                    |
| **Sub Container: …../** **OsIsrUseSpecialFunctionName** |                         |                                                           |                                                    |
| Short Name                                              | FALSE                   |                                                           |                                                    |
|                                                         |                         |                                                           |                                                    |
| Short Name                                              | SPI_CSIG0_TIRE_CAT2_ISR |                                                           | Configuration for ‘Communication Error Interrupt’  |
| Isr Category                                            | CATEGORY_2              |                                                           |                                                    |
| Isr Enable Nesting                                      | TRUE                    |                                                           |                                                    |
| Isr Accessing Application                               | NONE                    |                                                           |                                                    |
| Isr Resource Ref.                                       | NONE                    |                                                           |                                                    |
| **Sub Container: …../OsIsrUseResourceOccupations**      |                         |                                                           |                                                    |
|                                                         | None                    |                                                           |                                                    |
| **Sub Container: …../** **OsIsrExceptionType**          |                         |                                                           |                                                    |
| Short Name                                              | EIINT                   |                                                           |                                                    |
| Isr Int channel                                         | 174                     |                                                           |                                                    |
| Isr Interrupt Priority                                  | 14                      | Example only. Actual value will be changed in the program |                                                    |
| Isr Interrupt Stack Size                                | 512                     | Example only. Actual value will be changed in the program |                                                    |
| **Sub Container: …../** **OsIsrUseSpecialFunctionName** |                         |                                                           |                                                    |
| Short Name                                              | FALSE                   |                                                           |                                                    |
|                                                         |                         |                                                           |                                                    |
| Short Name                                              | SPI_CSIG0_TIR_CAT2_ISR  |                                                           | Configuration for ‘Receive Status Interrupt’       |
| Isr Category                                            | CATEGORY_2              |                                                           |                                                    |
| Isr Enable Nesting                                      | TRUE                    |                                                           |                                                    |
| Isr Accessing Application                               | NONE                    |                                                           |                                                    |
| Isr Resource Ref.                                       | NONE                    |                                                           |                                                    |
| **Sub Container: …../OsIsrUseResourceOccupations**      |                         |                                                           |                                                    |
|                                                         | None                    |                                                           |                                                    |
| **Sub Container: …../** **OsIsrExceptionType**          |                         |                                                           |                                                    |
| Short Name                                              | EIINT                   |                                                           |                                                    |
| Isr Int channel                                         | 176                     |                                                           |                                                    |
| Isr Interrupt Priority                                  | 14                      | Example only. Actual value will be changed in the program |                                                    |
| Isr Interrupt Stack Size                                | 512                     | Example only. Actual value will be changed in the program |                                                    |
| **Sub Container: …../** **OsIsrUseSpecialFunctionName** |                         |                                                           |                                                    |
| Short Name                                              | FALSE                   |                                                           |                                                    |

***Important Note:** Keep all of the interrupts configured above under a
trusted application. Because they require to run in
Supervisory/Privilege mode. Also add the SPI driver API*

*Spi_AsyncTransmit() as a trusted function under a trusted application.*

#### API Descriptions

Following table describes available APIs (Client/Server functions) per
current configurations for PwrSply/TmplMonr.

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 23%" />
<col style="width: 21%" />
<col style="width: 19%" />
<col style="width: 18%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>API Name</strong></td>
<td><strong>Functionality</strong></td>
<td><strong>Syntax</strong></td>
<td><strong>Argument</strong></td>
<td><strong>Return</strong></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Spi_Init</td>
<td>Initializes the SPI module. Shall be called by EcuM or BswM</td>
<td>void Spi_Init( const Spi_ConfigType* ConfigPtr)</td>
<td>SpiDriver. This is a pointer constant points to the Spi config
structure.</td>
<td>None</td>
</tr>
<tr class="even">
<td>Spi_WriteIB</td>
<td>Function to specify the data which has to be transmitted over the
SPI bus intended to a particular register.</td>
<td><p>Std_ReturnType Spi_WriteIB(</p>
<p>Spi_ChannelType Channel, const Spi_DataType* DataBufferPtr )</p></td>
<td><p>Channel = (Channel ID for the specific register)</p>
<p>DataBufferPtr = (Pointer to the 16 bit data buffer which need to
transmit. Note: the function takes the lower significant 15 bits of data
and calculate the odd parity and append it as a LSB with the 15 bits
data)</p></td>
<td><p>E_OK: write command has been accepted.</p>
<p>E_NOT_OK: write command has not been accepted.</p></td>
</tr>
<tr class="odd">
<td>Call_Spi_AsyncTransmit</td>
<td>Function to initiate the SPI transmission intended for a particular
register.</td>
<td>Std_ReturnType Call_Spi_AsyncTransmit( Spi_SequenceType Sequence
)</td>
<td>Sequence = (Sequence ID for the specific register)</td>
<td><p>E_OK: Transmit command has been accepted.</p>
<p>E_NOT_OK: Transmit command has not been accepted.</p></td>
</tr>
<tr class="even">
<td>Spi_ReadIB</td>
<td>Function to get the data that has been received from the SPI bus
during a transmission intended for a register.</td>
<td>Std_ReturnType Spi_ReadIB( Spi_ChannelType Channel, Spi_DataType*
DataBufferPointer )</td>
<td><p>Channel = (Channel ID for the specific register)</p>
<p>DataBufferPtr = (Pointer to the 16 bit data buffer where the received
SPI data supposed to store. Note: the function takes off the parity bits
and gives the rest 15 bits of data in 16 bit format)</p></td>
<td><p>E_OK: Read command has been accepted.</p>
<p>E_NOT_OK: Read command has not been accepted.</p></td>
</tr>
<tr class="odd">
<td>Spi_GetSequenceResult</td>
<td>Function to get the result of the last transmission intended for a
particular register.</td>
<td>Spi_SeqResultType Spi_GetSequenceResult( Spi_SequenceType Sequence
)</td>
<td>Sequence: Sequence ID for the register.</td>
<td><p>SPI_SEQ_OK.</p>
<p>SPI_SEQ_PENDING.</p>
<p>SPI_SEQ_FAILED.</p>
<p>SPI_SEQ_CANCELLED</p></td>
</tr>
</tbody>
</table>

*Note:*

*For both server and client the API name will be same. The use method of
server/client functions are described in
“CM600A_CSIG0CfgAndUse_DataDict.m” file.*

*Use the API **Call_Spi_AsyncTransmit ()** if it is being called from a
software component which does not reside under a trusted application.*

## Sub-Function: Next Sub-function

**None**

# Timing / Execution Constraints

## Rationale / Comments

Per RENESAS user manual Spi_Init() should be placed before Port_Init()
in the ECU startup sequence.

The order of API function calls when transmit any SPI message:

Spi_WriteIB()

Call_Spi_AsyncTransmit()

The order of API function calls to receive or read any SPI message when
the transmission is finished:

Spi_GetSequenceResult() ---🡪 Optional. Use this if want to verify
whether the transmission is done or

not before reading the buffer.

Spi_ReadIB()

Note: In a 2ms loop use separate SequenceID for transmitting each of the
message. For example if we have n different message to transmit in a 2ms
loop then use n different SequenceID for each of the transmission. The
SequenceID can be reused once the transmission is done, i.e in the next
2ms loop same SequenceID can be reused.

## Rates and State Execution

None.

# Serial Communications Interfaces

None.

# Additional Information

None.

# Revision Record & Change Approval

|         |            |                       |         |                        |
|---------|--------|------------|------|--------------------------------------|
| **Rev** | **Date**   | **Change Control \#** | **Drw** | **Change Description** |
| 1.0.0   | 07-01-2015 | CR ID: EA4#1027       |         | Initial version        |
|         |            |                       |         |                        |
|         |            |                       |         |                        |
|         |            |                       |         |                        |
|         |            |                       |         |                        |

{% endraw %}