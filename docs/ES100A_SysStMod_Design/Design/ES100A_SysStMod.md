---
layout: default
title: ES100A_SysStMod
nav_order: 1
parent: Component Design
---
{% raw %}
**System States and Modes**

**FDD \#ES100A**

[1. High Level Description 3](#high-level-description)

[2. Derived Requirements 3](#derived-requirements)

[3. Sub-Function Data Flow 3](#sub-function-data-flow)

[4. Design Rationale 3](#design-rationale)

[5. Sub-Functions 3](#sub-functions)

[5.1.1. Hardware Related Design 3](#hardware-related-design)

[5.1.2. Software Related Design 3](#software-related-design)

[6. Timing / Execution Constraints 4](#timing-execution-constraints)

[6.1. Rationale / Comments 4](#rationale-comments)

[6.2. Rates and State Execution 4](#rates-and-state-execution)

[7. Serial Communications Interfaces
4](#serial-communications-interfaces)

[8. Revision Record & Change Approval
5](#revision-record-change-approval)

# High Level Description

This function controls the primary system state machine for the
application. New states are computed based on current state and the
inputs to the function.

Four states are identified – OFF, WARM INIT, DISABLE and ENABLE.

# Derived Requirements

All requirements are contained in the ES100A_SysStMod DOORs module. All
requirements are derived.

#  Sub-Function Data Flow

Refer to the accompanying Simulink Model in the Functional Design
Package.

# Design Rationale

1.  The design was decided to take a lookup table based approach to
    allow for future flexibility should it be required. Changes might
    only require constant changes rather than a redesign.

2.  Transition Vector was developed to cover all current states – see
    the “Vector Analysis” spreadsheet included in the functional design
    package.

3.  Inputs for the following place certain requirements on the owning
    function:

    1.  **SysStReqDi:** Required to indicate TRUE if the state output
        control function has ramped assist to zero due to the Diagnostic
        input or the normal operational input. Things like start/stop
        are excluded from this to prevent transition to disable using
        that function (for improved start up times).

    2.  **SysStFltOutpReqDi:** Required to indicate TRUE if the
        diagnostic manager is responsible for removing output and has
        completed the ramp out (which could be a step in rapid shutdown
        mode).

Graphical model of the state machine implementation

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/ES100A_SysStMod_Design/Design/mediax/media/image1.wmf)

# Sub-Functions

Refer to the accompanying Simulink Model in the Functional Design
Package.

Requirements are linked between DOORs FR Document ES100A_SysStMod and
the Simulink Model.

### Hardware Related Design

None

### Software Related Design

Refer to the accompanying Simulink Model in the Functional Design
Package.

# Timing / Execution Constraints

## Rationale / Comments

The states and modes function shall be run at the end of the main
control loop (2ms). This is to reduce lag in shutdown, requiring all
inputs to the state machine to be computed in the same loop prior to
executing the function.

## Rates and State Execution

In general, the system state columns should be filled in as “Execute” or
“Do Not Execute”

|                                                          |               |                |               |            |             |         |
|--------------------|---------|---------|---------|---------|---------|---------|
| **Sub-Function Name**                                    | **Rate (ms)** | **Cold Init**  | **WARM INIT** | **ENABLE** | **DISABLE** | **OFF** |
| Refer to the \*.m file in the Functional Design Package. | See m file    | Do Not Execute | Execute       | Execute    | Execute     | Execute |
|                                                          |               |                |               |            |             |         |

# Serial Communications Interfaces

Nexteer Manufacturing Services will be used to read out the SysStMod
output (SysSt)

# Revision Record & Change Approval

|          |          |                       |         |                        |
|----------|----------|-----------------------|---------|------------------------|
| **Rev**  | **Date** | **Change Control \#** | **Drw** | **Change Description** |
| 01.00.00 | 24FE15   | EA4_144               | MK      | Initial Release        |
|          |          |                       |         |                        |
|          |          |                       |         |                        |
|          |          |                       |         |                        |
|          |          |                       |         |                        |

{% endraw %}