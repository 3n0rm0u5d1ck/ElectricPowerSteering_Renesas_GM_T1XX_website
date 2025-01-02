---
layout: default
title: EcuTMeas_MDD
nav_order: 3
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For** **ECU Temperature Measurement**

**VERSION:** **2.0**

**DATE:** **21-MAR-2016**

**Prepared By:**

**Krishna Anne,**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Revision History**

|             |                              |            |             |             |
|------|------------------------------|--------------|----------|-------------|
| **Sl. No.** | **Description**              | **Author** | **Version** | **Date**    |
| 1           | Initial Version              | SB         | 1.0         | 23-Mar-2015 |
| 2           | ADC Hooks are added as input | KK         | 2.0         | 21-Mar-2016 |
|             |                              |            |             |             |
|             |                              |            |             |             |
|             |                              |            |             |             |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 Ecutmeas & High-Level Description
7](#ecutmeas-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of Ecutmeas
8](#graphical-representation-of-ecutmeas)

[4.2 Data Flow Diagram 8](#data-flow-diagram)

[4.2.1 Module level DFD 8](#module-level-dfd)

[4.2.2 Sub-Module level DFD 8](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 8](#component-flow-diagram)

[5 Constant Data Dictionary 9](#__RefHeading___Toc446340958)

[5.1.1.1 9](#__RefHeading___Toc446340961)

[5.1.2 Module specific Lookup Tables Constants
9](#module-specific-lookup-tables-constants)

[6 Software Module Implementation 10](#software-module-implementation)

[6.1 Sub-Module Functions 10](#sub-module-functions)

[6.1.1 Initialization Functions 10](#initialization-functions)

[6.1.1.1 INIT: EcuTMeasINIT1 10](#init-ecutmeasinit1)

[6.1.1.2 Design Rationale 10](#design-rationale)

[6.1.1.3 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies)

[6.1.1.4 (Processing of function)……… 10](#processing-of-function)

[6.1.1.5 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs)

[6.1.2 PERIODIC FUNCTIONS 10](#periodic-functions)

[6.1.2.1 Per: EcuTMeasPer1 10](#per-ecutmeasper1)

[6.1.2.2 Design Rationale 10](#design-rationale-1)

[6.1.2.3 Store Module Inputs to Local copies
10](#store-module-inputs-to-local-copies-1)

[6.1.2.4 (Processing of function)……… 10](#processing-of-function-1)

[6.1.2.5 Store Local copy of outputs into Module Outputs
10](#store-local-copy-of-outputs-into-module-outputs-1)

[6.2 Interrupt Functions 10](#interrupt-functions)

[6.3 Serial Communication Functions 11](#serial-communication-functions)

[6.4 Local Function/Macro Definitions
11](#local-functionmacro-definitions)

[6.5 GLObAL Function/Macro Definitions
11](#global-functionmacro-definitions)

[6.6 TRANSIENT FUNCTIONS 11](#transient-functions)

[7 Known Limitations With Design 12](#known-limitations-with-design)

[8 UNIT TEST CONSIDERATION 13](#unit-test-consideration)

[9 Appendix 14](#appendix)

# Abbrevations And Acronyms

|              |                           |
|--------------|---------------------------|
| Abbreviation | Description               |
| DFD          | Design functional diagram |
| MDD          | Module design Document    |
|              |                           |
|              |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                          |                                            |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                                    | Version                                    |
| 1       | MDD Guidelines                           | Process 3.06.00                            |
| 2       | Software Naming Conventions              | Process 3.06.00                            |
| 3       | Coding standards                         | Process 3.06.00                            |
| 4       | FDD - ES210A Ecu Temperature Measurement | (See project group sub-version in synergy) |
|         |                                          |                                            |

# Ecutmeas & High-Level Description

Measures and diagnoses thermistor on ECU.

# Design details of software module

## Graphical representation of Ecutmeas

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES210A_EcuTMeas_Impl/doc/mediax/media/image2.png"
style="width:3.69861in;height:3.47847in" />

## Data Flow Diagram

## Module level DFD

N/A

## Sub-Module level DFD

N/A

## COMPONENT FLOW DIAGRAM

N/A

# 

# 

# 

# 

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

## Variable definition for enumerated types

|     |     |     |
|-----|-----|-----|
|     |     |     |
|     |     |     |

1.  <span id="__RefHeading___Toc446340958"
    class="anchor"></span>Constant Data Dictionary

## 

## 

##  [section-6]

|               |            |       |       |
|---------------|------------|-------|-------|
| Constant Name | Resolution | Units | Value |
| Refer FDD     |            |       |       |

## 

## 

|     |
|-----|
|     |
|     |
|     |
|     |

## Module specific Lookup Tables Constants

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| NA            |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

None

## Initialization Functions

## INIT: EcuTMeasINIT1

## Design Rationale

Per FDD author intent is to use standard Nexteer FilLp functions

## Store Module Inputs to Local copies

Refer to FDD

## (Processing of function)………

Refer to FDD

## Store Local copy of outputs into Module Outputs

Refer to FDD

## PERIODIC FUNCTIONS 

(Note: For multiple periodic functions, insert new headers at the
“Header 2” level – subset of “9.1.2 Periodic Functions” and follow the
same sub-section design shown below). If none required, place the text
“None”)

## Per: EcuTMeasPer1

## Design Rationale

Per FDD author intent is to use standard Nexteer FilLp functions

## Store Module Inputs to Local copies

Refer to FDD

## (Processing of function)………

Refer to FDD

## Store Local copy of outputs into Module Outputs

Refer to FDD

## Interrupt Functions

None

## Serial Communication Functions

None

## Local Function/Macro Definitions

Local Function \#1

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

None

## GLObAL Function/Macro Definitions

## GLObAL Function \#1

|     |     |     |     |     |
|-----|-----|-----|-----|-----|
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |
|     |     |     |     |     |

## 

## N/A

## TRANSIENT FUNCTIONS 

None

# Known Limitations With Design

None

# UNIT TEST CONSIDERATION

1.  The Per Instance Memory in .m file EcuTMeasFilStVarPrev given as
    float32 type, represents the State variable of the filter FilSt,
    element of the struct FilLpRec1

    1.  Range of Rte_Pim_EcuTMeasFilStVarPrev.FilSt is the range given
        in the .m file

2.  the equation to calculate filter gain is:

FilGain = 1 - exp(-2PI \* FrqPole \* TiStep)

1.  FrqPole is Rte_Prm_EcuTMeasFilTau_Val

2.  TiStep is 100ms

3.  Range of Rte_Pim_EcuTMeasFilStVarPrev.FilGain is calculated using
    the range of Rte_Prm_EcuTMeasFilTau_Val

```{=html}
<!-- -->
```
1.  The equation to calculate the filter output is:

Outp = ((Inp - FilSt) \* FilGain) + FilSt

# Appendix

*None*

{% endraw %}