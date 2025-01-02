---
layout: default
title: CM109A_ClkCfgAndMon
nav_order: 1
parent: Component Design
---
{% raw %}
**Clock Configuration and Monitoring RH850**

**(ClkCfgAndMon)**

**FDD \#CM109A**

[1. Function In This Document 5](#function-in-this-document)

[2. Critical Registers 5](#__RefHeading___Toc442887716)

[3. Sub-functions 6](#__RefHeading___Toc442887717)

[3.1. NTCs 6](#ntcs)

[3.2. SAN Linkage 6](#san-linkage)

[3.3. Description 6](#description)

[3.4. Rationale 6](#rationale)

[3.5. Implementation 6](#implementation)

[3.6. Reference 8](#reference)

[3.7. Verification Method 12](#verification-method)

[4. Revision Record & Change Approval 12](#__RefHeading___Toc442887726)

#   [section]

Renesas Document References:

Hardware User’s Manual (HWUM) version 1.00 dated July 2015

Safety Application Note (SAN) R01AN2118EJ0120 Rev. 1.20 Release December
1, 2015

# Function In This Document

N/A

#  [section-1]

## NTCs

N/A

## SAN Linkage

N/A

## Description

This function configures and starts the PE’s clock monitor logic. This
logic will cause a signal to the ECM if the monitored clocks exceed
their low or high limit thresholds over their sample intervals.

Each of four clock monitor circuits compares the number of rising clock
edges which occur on two clock signals. In the time required for each
“sampling clock” to produce 16 rising edges (after each reference rising
edge) the rising edges of the corresponding “monitored clock” are
counted and compared to programmed low and high limits for that monitor
circuit. A comparison outside the range defined by the limits causes a
signal to the ECM.

Per HWUM 31.5.3.2 and 31.5.3.3, each clock monitor channel’s enable bit,
when set to one, locks that channel’s low and high limit registers until
any reset occurs. Each clock monitor channel’s enable bit can be
controlled by writing to the respective control register CLMAnCTL0.

## Rationale

The sample and monitor clocks of CLMA1 and CLMA3 are both derived from
the same basic oscillator. For this reason, variation in these sources
will occur in both sample and monitor clock circuit inputs and the
resulting counts will not show the variation that will occur with CLMA0
and CLMA2 where the two oscillator inputs have independent variations.
Instead of adding the two tolerances which is appropriate with
independent error sources, a fraction of the total tolerance should be
used by MCAL with the positively correlated errors of CLMA1 and CLMA3.
Unless Renesas describes new sources of frequency error it may be
desirable to tighten the tolerances of CLMA1 and CLMA3.

Assumption:

A programmable “option byte” OPBT0 value affects the values used with
the Renesas formulae here. The assumption used here are that
OPBT0\[21:20\] is either 0b00 or 0b11. These two values yield identical
upper and lower limit values for the clock monitor circuits. Currently
CM106A documents the use of OPBT0\[21:20\] = 0b00.

All four monitor circuits will be initialized and armed since, in
addition to the existence of a reasonable frequency pulse stream from
the two oscillators, the additional channels each verifies that some
distinct frequency divider flip-flops are functioning.

## Implementation

The following table lists the values available from different sources
which may be used to initialize the clock monitor circuits.

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 15%" />
<col style="width: 15%" />
<col style="width: 14%" />
<col style="width: 13%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th>Clock monitor</th>
<th>OPBT0 [21:20]</th>
<th>monitored clock</th>
<th>sampling clock</th>
<th><p>Renesas formula min hex</p>
<p>(%tol.)</p></th>
<th><p>Renesas formula max hex</p>
<p>(%tol.)</p></th>
<th>Derived Tolerance for MCAL (+/-%)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>CLMA0</td>
<td>Don’t Care</td>
<td>Main Osc</td>
<td>HS intOsc / 4</td>
<td><p>73</p>
<p>(-10.16)</p></td>
<td><p>8F</p>
<p>(11.72)</p></td>
<td>(10, -10), (1, -1)</td>
</tr>
<tr class="even">
<td>CLMA1</td>
<td>Don’t Care</td>
<td>Peripheral clk /2</td>
<td>Main Osc / 8</td>
<td><p>9E</p>
<p>(-1.25)</p></td>
<td><p>A1</p>
<p>(0.625)</p></td>
<td>(1, -1) (1, -1)</td>
</tr>
<tr class="odd">
<td>CLMA2</td>
<td>00</td>
<td>WDTCLKI = 8Mhz</td>
<td>Main Osc / 16</td>
<td><p>72</p>
<p>(-10.94)</p></td>
<td><p>8D</p>
<p>(10.16)</p></td>
<td>(10, -10), (1, -1)</td>
</tr>
<tr class="even">
<td>CLMA3</td>
<td>Don’t Care</td>
<td>Clk CPU</td>
<td>Main Osc / 2</td>
<td><p>13E</p>
<p>(-0.625)</p></td>
<td><p>141</p>
<p>(0.313)</p></td>
<td>(1, -1) (1, -1)</td>
</tr>
</tbody>
</table>

Note: Renesas also documents a hardware requirement that each clock
monitor lower limit be larger than zero and that each upper limit must
be greater than or equal to the corresponding lower limit plus three.

The use of “Don’t Care“ in this table means that the value has no impact
on the circuit behavior.

The Renesas formulae compute clock monitor limit values assuming that
the two clocks of each monitor have independent variation from nominal.
While this is completely true for CLMA0 and CLMA2, it is wrong for CLMA1
and CLMA3 which use the same oscillator as the source of both inputs.
Those channels’ limits are likely wider than they need to be but the
digital hardware design limits on how close the two limit values of each
monitor can be to each other prevents those tolerances from being very
much tighter.

Renesas’ MCAL provides an input tolerance for each of the clocks
involved with each monitor circuit. MCAL accepts input tolerance
quantized to whole percentage so the minimum non-zero tolerance of one
percent is used for CLMA1 and CLMA3 inputs. The minimum crystal
oscillator tolerance (one percent) is used with the ten percent
tolerance of the “high-frequency” oscillator for CLMA0 and CLMA2.

A snapshot of the spreadsheet used to evaluate clock monitor limit
values has been included in the “reference data” section below.

MCAL Input:

In the McuGeneralConfiguration container

McuClm0Operation true

McuClm0MonitoringClockAccuracy 1

McuClm0SamplingClockAccuracy 10

McuClm1Operation true

McuClm1MonitoringClockAccuracy 1

McuClm1SamplingClockAccuracy 1

McuClm2Operation true

McuClm2MonitoringClockAccuracy 1

McuClm2SamplingClockAccuracy 10

McuClm3Operation true

McuClm3MonitoringClockAccuracy 1

McuClm3SamplingClockAccuracy 1

## Reference 

### <img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM109A_ClkCfgAndMon_Design/Design/mediax/media/image1.wmf"
style="width:5.98958in;height:7.85417in" /> [section-2]

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM109A_ClkCfgAndMon_Design/Design/mediax/media/image2.wmf"
style="width:5.99167in;height:7.00625in" />

<img
src="ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM109A_ClkCfgAndMon_Design/Design/mediax/media/image3.jpeg"
style="width:5.12431in;height:3.38194in" />

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/CM109A_ClkCfgAndMon_Design/Design/mediax/media/image4.wmf)

## Verification Method 

N/A

# Revision Record & Change Approval

|          |            |                       |         |                        |
|--------|----------|----------|-------|--------------------------------------|
| **Rev**  | **Date**   | **Change Control \#** | **Drw** | **Change Description** |
| 01.00.00 | 03/02/2016 | 2475                  | EC      | Initial release        |
|          |            |                       |         |                        |
|          |            |                       |         |                        |
|          |            |                       |         |                        |
|          |            |                       |         |                        |

{% endraw %}