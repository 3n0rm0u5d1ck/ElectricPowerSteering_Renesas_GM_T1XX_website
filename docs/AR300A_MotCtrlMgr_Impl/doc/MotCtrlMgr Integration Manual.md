---
layout: default
title: MotCtrlMgr Integration Manual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**MotCtrlMgr**

**VERSION: 3**

**DATE:** **09/21/16**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                 |                |             |          |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No.** | **Description**                                                 | **Author**     | **Version** | **Date** |
| 1           | Initial version                                                 | Lucas Wendling | 1           | 05/29/15 |
| 2           | Updates for Signal Mapping                                      | Lucas Wendling | 2           | 10/28/15 |
| 3           | Updates describing tool that generates MotCtrlMgr configuration | Lucas Wendling | 3           | 09/21/16 |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#davinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
7](#__RefHeading___Toc389222325)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 10](#memory-map-requirements)

[7.1 Mapping 10](#mapping)

[7.2 Usage 10](#usage)

[7.3 Non RTE NvM Blocks 10](#nvm-blocks)

[7.4 RTE NvM Blocks 10](#__RefHeading___Toc389222336)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                                         |
|------------------|-----------------------------------------|
| **Abbreviation** | **Description**                         |
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                             |                                |
|-------------|-----------------------------|--------------------------------|
| **Sr. No.** | **Title**                   | **Version**                    |
| 1           | MDD Guidelines              | Process 04.00.00               |
| 2           | Software Naming Conventions | Process 04.00.00               |
| 3           | Software Coding Standards   | Process 04.00.00               |
| 4           | AR300A_MotCtrlMgr_Design    | See Synergy subproject version |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
|            |                      |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

MotCtrlMgrIrq – This is a category 1 interrupt (see details below)

# Configuration REQUIREMeNTS

In addition to configuration based .c and .h files, the MotCtrlMgr
generator will also generate a .m file data dictionary for MotCtrlMgr.
In addition to documentation purposes, this data dictionary is intended
to aid in the creation of the AUTOSAR SWC model that is required to be
created for the MotCtrlMgr’s signal interface to the RTE. While the
generator will create the RTE runnables and runnable contents
automatically, the SWC model to be used in the AUTOSAR authoring tools
(e.g. Davinci Developer) is not automatically created by the generator
and will need either a separate tool to create, or will need to be
manually created.

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

CDD_MotCtrlMgr.c

CDD_MotCtrlMgr_Data.c

CDD_MotCtrlMgr_Data.h

CDD_MotCtrlMgr_Irq.c

## DaVinci Parameter Configuration Changes

Most of the configuration parameters in the table below are determined
from extracted data from the component data dictionaries of a given
project. This includes all of the motor control related runnables as
well as all of the signals that interface to motor control related
runnables (on either sender or receiver side).

The DataDictionary tool has been updated to support generation of the
majority of the MotCtrlMgr configuration listed below. The inputs this
tool requires is a project’s collection of component DataDictionaries, a
signal mapping xml, as well as the latest FDD tool data management
folder. The DataDictionary tool currently generates a .arxml file with
all of the MotCtrlMgr configuration except the following parameters
which still need to be manually populated:

/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/IncludeHeaders

/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable/SequenceOrder

The DataDictionary tool version which was used for testing of this
component is embedded within this component’s baseline. This particular
version of the tool is included mostly for reference purposes, and isn’t
required to be used at an integration level for the actual generation of
the MotCtrlMgr configuration so long as the version that is being used
produces the correct output.

|                                                                                                |                                                                                                                                                                                                                                                                                                                                                |            |
|------------------------|--------------------------------------|----------|
| **Parameter**                                                                                  | **Notes**                                                                                                                                                                                                                                                                                                                                      | **SWC**    |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/IncludeHeaders                      | All of the includes that are required to provide runnable prototypes (e.g. “MyHeader.h”)                                                                                                                                                                                                                                                       | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable                            | All of the runnables that are required in a given project that run at the “MotorControl” or “MotorControlx2” Rate. The shortname needs to exactly match the runnable function name                                                                                                                                                             | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable/RunnableRate               | Selection of the rate at which the given runnable executes (MotorControl or MotorControlx2)                                                                                                                                                                                                                                                    | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/RunnableManagement/Runnable/SequenceOrder              | Sequence order number to help define the ordering of the runnables relative to each other. Lower numbers are executed prior to higher numbers. Ordering does not need to be sequential, but it is recommended for clarity. Please note that if all MotorControlx2 runnables are not grouped together, there will be throughput inefficiencies. | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/IncludeHeaders                        | All of the includes that may be required to provide signal initial values (e.g. “MyHeader.h”). This is possibly required if initial values are required to be tied to a global constant that is defined in a certain header for example.                                                                                                       | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum                            | All of the enumeration definitions required outside of the RTE. The short name needs to exactly match the desired enumeration name.                                                                                                                                                                                                            | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumImplementationDataType | Implementation Data Type of the given enumeration. Selection of the supported types of “uint8”, “uint16”, and “uint32”.                                                                                                                                                                                                                        | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumElement                | Elements of a given enumeration. The short name should be the enumeration element name.                                                                                                                                                                                                                                                        | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum/EnumElement/Value          | Numeric value of a given enumeration element                                                                                                                                                                                                                                                                                                   | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping                         | Contains the configuration required for mapping differently named signals to eachother. This component specifically requires, at a minimum, all of the mapping of names related to signals that flow into, out of, or through the Motor Control runnables. Recommended “Short Name” of container is “*\<OutputSignal\>*Map”                    | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping/OutputSignalName        | Output signal name of signal needing mapping                                                                                                                                                                                                                                                                                                   | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/SignalMapping/InputSignalName         | Input signal name (or names) of signal needing mapping. Note that it is allowed to map more than one input name to each output.                                                                                                                                                                                                                | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal                                | Contains the required details of a given signal. The short name should match the base signal name (excluding “MotCtrl” prefix)                                                                                                                                                                                                                 | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/EnumerationNameReference       | Selection of Enumeration (if applicable - this should only exist on signals that are enumerations). Enumeration needs to be added to “/Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/NonRteEnum” configuration before it can be selected.                                                                                            | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ImplementationDataType         | Selection of Implementation Data Type of signal. For enumerations, this should be selected to match the underlying enumeration datatype.                                                                                                                                                                                                       | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/InitialValue                   | Initial Value, for arrays this should be a comma separated list (e.g. you would enter: 10,20,30,40). Suffixes of “F”, “U”, etc should be on appropriate signals as required.                                                                                                                                                                   | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Max                            | Maximum Value as indicated by m file defining signal.                                                                                                                                                                                                                                                                                          | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Min                            | Minimum Value as indicated by m file defining signal.                                                                                                                                                                                                                                                                                          | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadInMotCtrlRunnable          | This flag indicates if a given signal is read in a runnable that runs at “MotorControl” or “MotorControlx2” rate                                                                                                                                                                                                                               | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/ReadIn2msRunnable              | This flag indicates if a given signal is read in a runnable that runs at 2ms (or slower) RTE task                                                                                                                                                                                                                                              | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenInMotCtrlRunnable       | This flag indicates if a given signal is written in a runnable that runs at “MotorControl” or “MotorControlx2” rate                                                                                                                                                                                                                            | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/WrittenIn2msRunnable           | This flag indicates if a given signal is written in a runnable that runs at 2ms (or slower) RTE task                                                                                                                                                                                                                                           | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Size                           | Size of signal. This needs to be 1 for standard signals and if greater than 1, the signal is considered to be an array                                                                                                                                                                                                                         | MotCtrlMgr |
| /Nexteer/MotCtrlMgr/MotCtrlMgrConfigSet/SignalManagement/Signal/Units                          | Units of signal as indicated by m file defining signal.                                                                                                                                                                                                                                                                                        | MotCtrlMgr |

## DaVinci Interrupt Configuration Changes

|                   |                                |                                                                               |                                                                                |                                                                     |
|------------|--------|--------------------|------------------|---------------|
| **ISR Name**      | **Interrupt Category (FE/EI)** | **Interrupt Channel Number**                                                  | **Priority Dependency**                                                        | **Notes**                                                           |
| **MotCtrlMgrIrq** | EI                             | Needs to be gathered from program specific CM###\_XXXXMcuCfg_Design component | Needs to be an appropriate priority for the high speed motor control interrupt | This ISR should be category 1 ISR and mapped to trusted application |

## Manual Configuration Changes

|     |           |         |
|-----|-----------|---------|
|     | **Notes** | **SWC** |
|     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

This module defines all non-RTE motor control data structures

## Required Global Data Outputs

This module defines all non-RTE motor control data structures

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|          |                             |             |
|----------|-----------------------------|-------------|
| **Init** | **Scheduling Requirements** | **Trigger** |
|          |                             |             |

|                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                |
|-----------------|-----------------------------------|--------------------|
| **Runnable**       | **Scheduling Requirements**                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | **Trigger**                                                                                    |
| **MotCtrlMgrIrq**  | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | ISR – exact ISR source to be gathered from program specific CM###\_XXXXMcuCfg_Design component |
| **MotCtrlMgrPer1** | MotCtrlMgrPer1 should execute near the start of the 2ms loop before any other functions that need data that is output by runnables running at the Motor Control rate. The DMA transfer that is populating MotCtrlMgr_TwoMilliSecFromMotCtrl_Rec shall run before MotCtrlMgrPer1 and ideally enough other functionality runs in-between these two events that the transfer can complete with minimal wait time in MotCtrlMgrPer1 (since this function is waiting for DMA transfer completion). | 2ms RTE                                                                                        |
| **MotCtrlMgrPer2** | MotCtrlMgrPer2 should execute as the final function of the forward path to allow minimal lag on computation of new PWM commands in the Motor Control loop.                                                                                                                                                                                                                                                                                                                                    | 2ms RTE                                                                                        |

**.**

# Memory Map REQUIREMENTS

## Mapping

|                                                    |                                                   |                                                                                                                                                                                                                                                                 |
|--------------------------------------|----------------|------------------|
| **Memory Section**                                 | **Contents**                                      | **Notes**                                                                                                                                                                                                                                                       |
| **MotCtrl_START_SEC_CODE**                         | Interrupt code                                    | This code section also includes a static function scope variable, and therefore needs to open and close variable mapping statements and this should be mapped to the same application that the ISR is mapped to.                                                |
| **CDD_MotCtrlMgr_DmaWrite_START_SEC_VAR_INIT_128** | Data that a DMA channel writes to during run-time | This gets mapped to a “.data_dma_128” section that will need to be explicitly added to the linker file. The intent of this section is to be placed in a RAM memory section that only the DMA has write access to (processor in user mode only has read access). |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
|             |         |         |

## NvM Blocks

None

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*\<This section is for appendix\>*

{% endraw %}