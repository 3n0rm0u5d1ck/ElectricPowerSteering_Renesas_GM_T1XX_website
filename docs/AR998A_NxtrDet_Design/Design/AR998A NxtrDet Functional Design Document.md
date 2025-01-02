---
layout: default
title: AR998A NxtrDet Functional Design Document
nav_order: 1
parent: Component Design
---
{% raw %}
**Nexteer Det**

**FDD \#AR998A**

[1. High Level Description 3](#high-level-description)

[2. Function I/O 3](#function-io)

[2.1. Input Description 3](#input-description)

[2.2. Output Description 4](#output-description)

[2.3. Sub-Function Data Flow 5](#data-flow)

[3. Design Rationale 6](#design-rationale)

[4. Sub-Functions 6](#sub-functions)

[4.1. Sub-Function: Initialization 6](#__RefHeading___Toc362253455)

[4.1.1. Software Related Design 6](#__RefHeading___Toc362253456)

[4.2. Sub-Function: Signal Processing of Battery and Switched Voltages
6](#__RefHeading___Toc362253457)

[4.2.1. Hardware Related Design 6](#__RefHeading___Toc362253458)

[4.2.2. Software Related Design 6](#__RefHeading___Toc362253459)

[4.2.3. Sub Function Calibrations 6](#__RefHeading___Toc362253460)

[\* Location Legend 7](#__RefHeading___Toc362253461)

[4.2.4. Signal Availability 7](#__RefHeading___Toc362253462)

[4.3. Sub-Function: Next Sub-function 7](#__RefHeading___Toc362253463)

[5. Timing / Execution Constraints 7](#timing-execution-constraints)

[5.1. Rationale / Comments 7](#__RefHeading___Toc362253465)

[5.2. Rates and State Execution 7](#__RefHeading___Toc362253466)

[6. Additional Information 8](#additional-information)

[7. Revision Record & Change Approval
9](#revision-record-change-approval)

# High Level Description

The Det (Development Error Tracer) is an AUTOSAR defined module used to
aid in detecting development errors. Ideally, Det is used during project
development only, and is disabled/turned off once the project
development and testing reaches a stage where enough confidence has been
gained in the design. Example of typical types of errors that are mapped
to the Det module include:

-   Incorrect usage of an API (e.g. arguments that are out of range)

-   Attempted usage of a function that is not yet initialized

-   Incorrect / incompatible configuration

In addition to Det usage already incorporated into 3rd party software
(e.g. AUTOSAR BSW and MCAL modules), Det error checking usage can be
incorporated into Nexteer designed components as additional error
checking during project development via a specified interface into the
Det AUTOSAR module. This design document outlines the details of the
strategy of incorporating Det error checking in Nexteer designed
components, defines the constants which control turning on and off
specific Nexteer Det error checking functionality, and also centrally
defines the constants controlling the Det “ModuleID” assigned to each
Nexteer component which has Det functionality.

# Function I/O

None - N/A

## Input Description

None - N/A

|            |             |
|------------|-------------|
| Input Name | Description |
|            |             |

## Output Description

None - N/A

|             |             |
|-------------|-------------|
| Output Name | Description |
|             |             |

##   Data Flow

None –N/A

# Design Rationale

## Strategy Overview:

Det error checking is intended to strictly be an aid in detecting errors
during project development. It is assumed that all Det error checking
will be disabled at some point prior to production intent software
builds. Additionally, Det error checking logic will have some impact on
memory and cpu utilization metrics. For this reason, all Det logic will
be conditionally compiled based on if any given component has its
particular Det errors enabled.

The constants controlling these error enables are defined in this
component (AR998A_NxtrDet). Additionally, the AUTOSAR Det module
contains a global DET_ENABLED flag to be used as a single enable that
can be used to turn off all Det error checks. Therefore, this global
DET_ENABLED flag must be “enabled” in order for any Nexteer defined Det
error checks to be enabled as shown below:

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/AR998A_NxtrDet_Design/Design/mediax/media/image1.wmf)

## AUTOSAR Det API Interface Details:

void Det_ReportError(uint16 ModuleId, uint8 InstanceId, uint8 ApiId,
uint8 ErrorId)

-   ModuleId: Unique Id for each component that has Det Errors

```{=html}
<!-- -->
```
-   **Nexteer’s components will start from 65535 and decrement (0-255
    are reserved for AUTOSAR modules). This component (AR998A NxtrDet)
    will define all of the Nexteer defined ModuleId values.**

```{=html}
<!-- -->
```
-   InstanceId: Only used if more than one instance of a module exists

```{=html}
<!-- -->
```
-   **Always will be “0” for current Nexteer component designs**

```{=html}
<!-- -->
```
-   ApiId: Unique Id within a module for a given API/Function

```{=html}
<!-- -->
```
-   **Controlled** **by Nexteer component’s Det error design (value
    outside of scope of AR998A NxtrDet)**

```{=html}
<!-- -->
```
-   ErrorId: Unique Id within a module’s API/Function for a specific
    error check being done

```{=html}
<!-- -->
```
-   **Controlled** **by Nexteer component’s Det error design (value
    outside of scope of AR998A NxtrDet)**

## Nexteer Component Det Design Guidelines:

While the individual Det error detection design details for Nexteer
components are outside the scope of this document, some high level
design guidelines are given:

-   Det error checking design details are outside the scope of
    FDD/Design component development. The software group will take
    responsibility for defining Det error checking in the implementation
    of the design where deemed appropriate (i.e. these are optional for
    implementation). Det design will be captured in the implementation
    documentation (e.g. MDD) of any given component (as opposed to in
    the design itself).

-   All Det error checking logic will be conditionally compiled, and if
    turned off, the resulting compiled code will exactly match the
    specified design. (i.e. turning Det error checking off will remove
    all associated Det logic from the compilation). Further,
    implementation of Det error checking logic should not compromise the
    functionality of the core design (this should implicitly be verified
    during component unit testing).

# Sub-Functions

None – N/A

# Timing / Execution Constraints

None – N/A

# Additional Information

# Revision Record & Change Approval

|         |          |                       |                        |
|---------|----------|-----------------------|------------------------|
| **Rev** | **Date** | **Change Control \#** | **Change Description** |
| 1       | 10/09/15 | EA4#1915              | Initial Version        |

{% endraw %}