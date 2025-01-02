---
layout: default
title: Adc0CfgAndUse_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**Adc0 Cfg And Use**

**VERSION:** **3.0**

**DATE:** **09-Jun-2016**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                               |                    |             |             |
|-----|--------------------------------|-------------|----------|-------------|
| **Sl. No.** | **Description**               | **Author**         | **Version** | **Date**    |
| 1           | Initial version               | Selva Sengottaiyan | 1.0         | 4-May-2015  |
| 2           | Updated for design rev. 2.0.0 | Rijvi              | 2.0         | 05-Feb-2016 |
| 3           | Updated fro design rev 2.1.0  | Avinash James      | 3.0         | 09-Jun-2016 |

: ARM Cortex R4 Memory Usage

**<u>  
Table of Contents</u>**

1 Abbrevations And Acronyms 4

2 References 5

3 Dependencies 6

3.1 SWCs 6

3.2 Global Functions(Non RTE) to be provided to Integration Project 6

4 Configuration REQUIREMeNTS 7

4.1 Build Time Config 7

4.2 Configuration Files to be provided by Integration Project 7

4.3 Da Vinci Parameter Configuration Changes 7

4.4 DaVinci Interrupt Configuration Changes 7

4.5 Manual Configuration Changes 7

5 Integration DATAFLOW REQUIREMENTS 8

5.1 Required Global Data Inputs 8

5.2 Required Global Data Outputs 8

5.3 Specific Include Path present 8

6 Runnable Scheduling 9

7 Memory Map REQUIREMENTS 10

7.1 Mapping 10

7.2 Usage 10

7.3 NvM Blocks 10

8 Compiler Settings 11

8.1 Preprocessor MACRO 11

8.2 Optimization Settings 11

1 Appendix 12

# Abbrevations And Acronyms

| **Abbreviation** | **Description**                         |
|------------------|-----------------------------------------|
| DFD              | Design functional diagram               |
| MDD              | Module design Document                  |
|                  | \<ADD more to the table if applicable\> |
|                  |                                         |
|                  |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| **Sr. No.** | **Title**                  | **Version**                     |
|-------------|----------------------------|---------------------------------|
| \<1\>       | FDD – CM300A Adc0CfgAndUse | See synergy sub project version |
|             |                            |                                 |
|             |                            |                                 |
|             |                            |                                 |
|             |                            |                                 |

# Dependencies

## SWCs

| **Module**     | **Required Feature**                                                                                                             |
|-----------------------|-------------------------------------------------|
| **MotCtrlMgr** | Generated struct type declarations for the Motor Control loop / RTE interface data; macros for access of Motor Control loop data |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

# Configuration REQUIREMeNTS

## Build Time Config

| Adc0CfgAndUsePer1 : To be called ever other motor control ISR loop and updates the start and end pointers of ADC diagnostics and scan group 1 **Modules** | **Notes** |     |
|---------------------------|--------------------------------------|--------|
| None                                                                                                                                                      |           |     |

## Configuration Files to be provided by Integration Project

Yes

## Da Vinci Parameter Configuration Changes

| **Parameter**                    | **Notes** | **SWC** |
|----------------------------------|-----------|---------|
| Refer the . m file in the design |           |         |

## DaVinci Interrupt Configuration Changes

| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
|--------------|------------|-------------------------|-----------|
| **N/A**      |            |                         |           |

## Manual Configuration Changes

| **Constant** | **Notes** | **SWC** |
|--------------|-----------|---------|
| **N/A**      |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

Refer DataDict.m file

## Required Global Data Outputs

Refer DataDict.m file

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| **Init**           | **Scheduling Requirements** | **Trigger** |
|--------------------|-----------------------------|-------------|
| Adc0CfgAndUseInit1 | None                        | RTE/Init    |

| **Runnable**          | **Scheduling Requirements** | **Trigger**                      |
|-----------------------------|-------------------------------|-------------|
|                       |                             |                                  |
| **Adc0CfgAndUsePer1** | None                        | Non RTE/2xMotor Control ISR rate |

# Memory Map REQUIREMENTS

## Mapping

| **Memory Section**                      | **Contents** | **Notes** |
|-----------------------------------------|--------------|-----------|
| **CDD_Adc0CfgAndUse_MotCtrl_START_SEC** |              |           |
|                                         |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| **Feature** | **RAM** | **ROM** |
|-------------|---------|---------|
| **None**    |         |         |

## NvM Blocks

\*See DataDict.m

##  [section]

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

# Appendix

*None*

{% endraw %}