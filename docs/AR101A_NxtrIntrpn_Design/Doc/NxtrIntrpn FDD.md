---
layout: default
title: NxtrIntrpn FDD
nav_order: 1
parent: Component Design
---
{% raw %}
**Functional Design Document**

**For**

**NxtrIntrpn**

**VERSION: 1.0**

**DATE: 20-Feb-2015**

**Prepared By:**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**  
**

**Revision History**

|             |                 |            |                      |             |                 |
|----------|-------------------|--------------|--------|-----------|-----------|
| **Version** | **Description** | **Author** | **Section Modified** | **Date**    | **Approved By** |
| 1.0         | Initial Version | K. Smith   | All                  | 20-Feb-2015 | Nexteer         |

**<u>  
Table of Contents</u>**

[1 Abbrevations And Acronyms
[4](#abbrevations-and-acronyms)](#abbrevations-and-acronyms)

[2 References [5](#references)](#references)

[3 Purpose [6](#purpose)](#purpose)

[4 Interpolation Design [7](#_Toc412195618)](#_Toc412195618)

[4.1 Linear Interpolation
[7](#linear-interpolation)](#linear-interpolation)

[4.1.1 Linear Interpoliation Accuracy
[8](#linear-interpoliation-accuracy)](#linear-interpoliation-accuracy)

[4.2 Fixed X-Axis Linear Interpolation Functions
[9](#fixed-x-axis-linear-interpolation-functions)](#fixed-x-axis-linear-interpolation-functions)

[4.2.1 API [9](#api)](#api)

[4.2.1.1 Truncating Functions
[9](#truncating-functions)](#truncating-functions)

[4.2.1.2 Rounding Functions
[9](#rounding-functions)](#rounding-functions)

[4.3 Variable X-Axis Linear Interpolation Functions
[10](#variable-x-axis-linear-interpolation-functions)](#variable-x-axis-linear-interpolation-functions)

[4.3.1 API [10](#api-1)](#api-1)

[4.3.1.1 Truncating Functions
[10](#truncating-functions-1)](#truncating-functions-1)

[4.3.1.2 Rounding Functions
[12](#rounding-functions-1)](#rounding-functions-1)

[4.4 Bilinear Interpolation
[14](#bilinear-interpolation)](#bilinear-interpolation)

[4.4.1 Common X Axis Bilinear Interpolation Functions
[16](#common-x-axis-bilinear-interpolation-functions)](#common-x-axis-bilinear-interpolation-functions)

[4.4.1.1 API [16](#api-2)](#api-2)

[4.4.2 Variable X Axis Bilinear Interpolation Functions
[19](#variable-x-axis-bilinear-interpolation-functions)](#variable-x-axis-bilinear-interpolation-functions)

[4.4.2.1 API [19](#api-3)](#api-3)

[5 Know Limitations With Design
[22](#known-limitations-with-design)](#known-limitations-with-design)

[6 Appendix A [23](#appendix-a)](#appendix-a)

[7 Appendix B [24](#appendix-b)](#appendix-b)

[7.1 Truncating Linear Interpolation Functions
[24](#truncating-linear-interpolation-functions)](#truncating-linear-interpolation-functions)

[7.1.1 Fixed X-Axis Interpolation Function
[24](#fixed-x-axis-interpolation-function)](#fixed-x-axis-interpolation-function)

[7.1.2 Variable X-Axis Interpolation Function
[24](#variable-x-axis-interpolation-function)](#variable-x-axis-interpolation-function)

[7.2 Rounding Linear Interpolation Functions
[24](#rounding-linear-interpolation-functions)](#rounding-linear-interpolation-functions)

[7.2.1 Fixed X-Axis Interpolation Function
[24](#fixed-x-axis-interpolation-function-1)](#fixed-x-axis-interpolation-function-1)

[7.2.2 Variable X-Axis Interpolation Function
[24](#variable-x-axis-interpolation-function-1)](#variable-x-axis-interpolation-function-1)

[8 Appendix C [25](#appendix-c)](#appendix-c)

# Abbrevations And Acronyms

| Abbreviation | Description                   |
|--------------|-------------------------------|
| BS           | Bilinear Selection            |
| API          | Application Program Interface |

# References

This section lists the title & version of all the documents that are
referred for development of this document

| Sr. No.    | Title                                    | Version        |
|------------|------------------------------------------|----------------|
| Appendix C | RH850/P1x Series User’s Manual: Software | 0.10 Jan, 2014 |

# Purpose

The purpose of this document is to describe the functions contained
within the Nexteer interpolation library and as an API reference in
designing functional requirements, models, and software components.

# Interpolation Design

## Linear Interpolation

Linear interpolation is used to determine an output value between a set
of known data points for a given input. In the image below, the input
point (x) is between the known points (x~0~,y~0~) and (x~1~,y~1~).

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/AR101A_NxtrIntrpn_Design/Doc/mediax/media/image1.emf)

The linear interpolant is defined as the straight line between the two
known points (x~0~,y~0~) and (x~1~,y~1~) and is defined in equation (1).

|     | $$\frac{\left( y - y_{0} \right)}{\left( x - x_{0} \right)} = \frac{\left( y_{1} - y_{0} \right)}{\left( x_{1} - x_{0} \right)}$$ | \(1\) |
|------|------------------------------------------------------------|------|

Solving equation (1) for the desired output (y) is described below in
equation (2).

|     | $$y = y_{0} + (y_{1} - y_{0})\frac{\left( x - x_{0} \right)}{\left( x_{1} - x_{0} \right)}$$ | \(2\) |
|------|------------------------------------------------------------|------|

If the delta between neighboring points on the X-axis is the same,
equation (2) can be modified with that delta as shown in equation (3).

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 86%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><p><span class="math display">$$x_{0} = \left\lfloor
\frac{x}{\mathrm{\Delta}x} \right\rfloor*\mathrm{\Delta}x$$</span></p>
<p><span class="math display">$$y = y_{0} + (y_{1} - y_{0})\frac{\left(
x - x_{0} \right)}{\mathrm{\Delta}x}$$</span></p></th>
<th>(3)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Linear Interpoliation Accuracy

The operations required to perform equations (2) and (3) shall be
implemented using fixed point math. This is to save on execution time to
perform the interpolation compared to using floating point math
functions (See Appendix C). This also means that there can be
information loss because the operations can produce results that have
more bits than the operands. In order to keep the same number of bits as
the operands, the answer must be rounded or truncated.

The interpolation library shall support both truncation and rounding
methods in all linear interpolation functions. These methods are
described in Appendix B. The error produced by the truncated function
results can be +/- one count. Depending on the resolution of the
calibration and the resolution required by the design, this may be
negligible. The function designer shall use the truncation library
functions in all cases where this error is acceptable in order to save
on execution time.

## Fixed X-Axis Linear Interpolation Functions

The following functions are available for linear interpolation with a
fixed X-axis and are based on equation (3). The table below defines each
argument used in the API. Note that some functions require and/or return
unsigned or signed values. It is up to the designer to pick the proper
interpolation function for their design.

| Argument | Notes                                                                                                                                                         |
|----------|--------------------------------------------------------------|
| DeltaX   | Provides the delta between points in the X-axis for interpolation. A value of 0 shall return the first value in YTbl.                                         |
| YTbl\[\] | Y table values                                                                                                                                                |
| Size     | Number of elements in YTbl                                                                                                                                    |
| Inp      | Input value (x). Values that are less than or equal to DeltaX or larger than DeltaX \* (Size – 1) will return the first or last value respectively from YTbl. |

## API

The input and output variables are defined as uint16 or sint16 for
purposes of min and max ranges. However, calibrations with different
resolutions, for example u8p8, can be used because they are still
represented as a 16-bit value within these functions.

## Truncating Functions

|                      |                                |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpn_u16_u16FixdXu16VariY | Type       | Min | Max   |
| **Arguments Passed** | DeltaX                         | uint16     | 0   | 65535 |
|                      | YTbl\[\]                       | uint16\[\] | 0   | 65535 |
|                      | Size                           | uint16     | 1   | 65535 |
|                      | Inp                            | uint16     | 0   | 65535 |
| **Return Value**     |                                | uint16     | 0   | 65535 |

|                      |                                |            |        |       |
|-------------|-------------------------|------------|-----------|------------|
| **Function Name**    | LnrIntrpn_s16_u16FixdXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | DeltaX                         | uint16     | 0      | 65535 |
|                      | YTbl\[\]                       | sint16\[\] | -32768 | 32767 |
|                      | Size                           | uint16     | 1      | 65535 |
|                      | Inp                            | uint16     | 0      | 65535 |
| **Return Value**     |                                | sint16     | -32768 | 32767 |

## Rounding Functions

|                      |                                         |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpnWithRound_u16_u16FixdXu16VariY | Type       | Min | Max   |
| **Arguments Passed** | DeltaX                                  | uint16     | 0   | 65535 |
|                      | YTbl\[\]                                | uint16\[\] | 0   | 65535 |
|                      | Size                                    | uint16     | 1   | 65535 |
|                      | Inp                                     | uint16     | 0   | 65535 |
| **Return Value**     |                                         | uint16     | 0   | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|------------|-----------|------------|
| **Function Name**    | LnrIntrpnWithRound_s16_u16FixdXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | DeltaX                                  | uint16     | 0      | 65535 |
|                      | YTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | Size                                    | uint16     | 1      | 65535 |
|                      | Inp                                     | uint16     | 0      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

## Variable X-Axis Linear Interpolation Functions

The following functions are available for linear interpolation with a
variable X-axis and are based on equation (2). The table below defines
each argument used in the API. Note that some functions require and/or
return unsigned or signed values. It is up to the designer to pick the
proper interpolation function for their design.

| Argument | Notes                                                                                                                                                        |
|----------|--------------------------------------------------------------|
| XTbl\[\] | X Table                                                                                                                                                      |
| YTbl\[\] | Y Table                                                                                                                                                      |
| Size     | Number of elements in the XTbl and YTbl                                                                                                                      |
| Inp      | Input value (x). Values that are less than or equal to XTbl\[0\] or larger than XTbl\[Size – 1\] will return the first or last value respectively from YTbl. |

## API

The input and output variables are defined as uint16 or sint16 for
purposes of min and max ranges. However, calibrations with different
resolutions, for example u8p8, can be used because they are still
represented as a 16-bit value within these functions.

## Truncating Functions

|                      |                                |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpn_u16_u16VariXu16VariY | Type       | Min | Max   |
| **Arguments Passed** | XTbl\[\]                       | uint16\[\] | 0   | 65535 |
|                      | YTbl\[\]                       | uint16\[\] | 0   | 65535 |
|                      | Size                           | uint16     | 1   | 65535 |
|                      | Inp                            | uint16     | 0   | 65535 |
| **Return Value**     |                                | uint16     | 0   | 65535 |

|                      |                                |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpn_u16_s16VariXu16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                       | sint16\[\] | -32768 | 32767 |
|                      | YTbl\[\]                       | uint16\[\] | 0      | 65535 |
|                      | Size                           | uint16     | 1      | 65535 |
|                      | Inp                            | sint16     | -32768 | 32767 |
| **Return Value**     |                                | uint16     | 0      | 65535 |

|                      |                                |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpn_s16_s16VariXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                       | sint16\[\] | -32768 | 32767 |
|                      | YTbl\[\]                       | sint16\[\] | -32768 | 32767 |
|                      | Size                           | uint16     | 1      | 65535 |
|                      | Inp                            | sint16     | -32768 | 32767 |
| **Return Value**     |                                | sint16     | -32768 | 32767 |

|                      |                                |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpn_s16_u16VariXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                       | uint16\[\] | 0      | 65535 |
|                      | YTbl\[\]                       | sint16\[\] | -32768 | 32767 |
|                      | Size                           | uint16     | 1      | 65535 |
|                      | Inp                            | uint16     | 0      | 65535 |
| **Return Value**     |                                | sint16     | -32768 | 32767 |

## Rounding Functions

|                      |                                         |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpnWithRound_u16_u16VariXu16VariY | Type       | Min | Max   |
| **Arguments Passed** | XTbl\[\]                                | uint16\[\] | 0   | 65535 |
|                      | YTbl\[\]                                | uint16\[\] | 0   | 65535 |
|                      | Size                                    | uint16     | 1   | 65535 |
|                      | Inp                                     | uint16     | 0   | 65535 |
| **Return Value**     |                                         | uint16     | 0   | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpnWithRound_u16_s16VariXu16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | YTbl\[\]                                | uint16\[\] | 0      | 65535 |
|                      | Size                                    | uint16     | 1      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
| **Return Value**     |                                         | uint16     | 0      | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpnWithRound_s16_s16VariXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | YTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | Size                                    | uint16     | 1      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | LnrIntrpnWithRound_s16_u16VariXs16VariY | Type       | Min    | Max   |
| **Arguments Passed** | XTbl\[\]                                | uint16\[\] | 0      | 65535 |
|                      | YTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | Size                                    | uint16     | 1      | 65535 |
|                      | Inp                                     | uint16     | 0      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

## Bilinear Interpolation

Bilinear interpolation is linear interpolation with expanded coverage
into three dimensions. To calculate the result, three linear
interpolations are required to be performed.

![](ElectricPowerSteering_Renesas_GM_T1XX_website/docs/AR101A_NxtrIntrpn_Design/Doc/mediax/media/image2.emf)

The first two interpolations are between the two data sets (shown in red
and green in the image) and are described with the equations (4) and
(5).

|     | $$Y_{1} = y_{0} + \left( y_{1} - y_{0} \right)\left( \frac{(x - x_{0})}{(x_{1} - x_{0})} \right)$$ | \(4\) |
|------|------------------------------------------------------------|------|

|     | $$Y_{2} = y_{2} + \left( y_{3} - y_{2} \right)\left( \frac{(x - x_{2})}{(x_{3} - x_{2})} \right)$$ | \(5\) |
|------|------------------------------------------------------------|------|

Equations (4) and (5) provide the endpoints for the interpolant between
the two sets of data. The third interpolation determines how close the
desired output is to each of the data sets. This is described in
equation (6).

|     | $$y = Y_{1} + \left( Y_{2} - Y_{1} \right)\left( \frac{(BS - {BS}_{1})}{({BS}_{2} - {BS}_{1})} \right)$$ | \(6\) |
|------|------------------------------------------------------------|------|

Since divisions are throughput intensive operations, equation (6) is not
efficient for an embedded environment because it contains three division
steps when substitutions are made for Y~1~ and Y~2~. However, the terms
can be rearranged to reduce the amount of divisions for additional
multiplications and additions, which typically are much less in
throughput consumption. Staring with equations (4) and (5), the terms
can be reordered into equations (7) and (8).

|     | $$Y_{1} = \frac{\left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) + \left( x_{1} - x_{0} \right)y_{0}}{\left( x_{1} - x_{0} \right)} = \frac{Y_{1_{Num}}}{Y_{1_{Den}}}$$ | \(7\) |
|------|------------------------------------------------------------|------|

|     | $$Y_{2} = \frac{\left( x - x_{2} \right)\left( y_{3} - y_{2} \right) + \left( x_{3} - x_{2} \right)y_{2}}{\left( x_{3} - x_{2} \right)} = \frac{Y_{2_{Num}}}{Y_{2_{Den}}}$$ | \(8\) |
|------|------------------------------------------------------------|------|

Equations (7) and (8) can be substituted back in equation (6) and the
simplified result is shown in equation (9).

|     | $$y = \frac{\left( BS - {BS}_{1} \right)\left( Y_{2_{Num}} \right)\left( Y_{1_{Den}} \right) - \left( BS - {BS}_{1} \right)\left( Y_{1_{Num}} \right)\left( Y_{2_{Den}} \right) + \left( {BS}_{2} - {BS}_{1} \right)\left( Y_{1_{Num}} \right)\left( Y_{2_{Den}} \right)}{\left( {BS}_{2} - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( Y_{2_{Den}} \right)}$$ | \(9\) |
|------|------------------------------------------------------------|------|

Finally, the numerator in equation (9) can also be rearranged and split
into multiple terms. The steps taken between equations (9) and (10) are
provided in Appendix A. The final equation, requiring only one division
step, is shown in equation (10).

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 86%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>1<em>a</em></sub> = (<em>x</em><sub>3</sub>−<em>x</em><sub>2</sub>)(<em>y</em><sub>1</sub> − <em>y</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>1<em>b</em></sub> = (<em>x</em> − <em>x</em><sub>0</sub>)(<em>B</em><em>S</em><sub>2</sub> − <em>B</em><em>S</em><sub>1</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>2<em>a</em>3<em>a</em></sub> = (<em>x</em><sub>2</sub> − <em>x</em><sub>0</sub>)(<em>B</em><em>S</em> − <em>B</em><em>S</em><sub>1</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>2<em>b</em></sub> = (<em>x</em><sub>3</sub> − <em>x</em><sub>2</sub>)(<em>y</em><sub>2</sub> − <em>y</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>3<em>b</em></sub> = (<em>x</em> − <em>x</em><sub>3</sub>)(<em>y</em><sub>3</sub> − <em>y</em><sub>2</sub>)</span></p>
<p><span class="math display">$$y = y_{0} + \left( \frac{\left(
{Term}_{2a3a} \right)\left( {Term}_{3b} \right) + \left( {Term}_{2a3a}
\right)\left( {Term}_{2b} \right) + \left( {Term}_{1a} \right)\left(
{Term}_{1b} \right)}{\left( {BS}_{2} - {BS}_{1} \right)\left( x_{1} -
x_{0} \right)\left( x_{3} - x_{2} \right)} \right)$$</span></p></th>
<th>(10)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Common X Axis Bilinear Interpolation Functions

The following functions are available for bilinear interpolation with a
common X-axis and are based on equation (10). The table below defines
each argument used in the API. Note that some functions require and/or
return unsigned or signed values. It is up to the designer to pick the
proper interpolation function for their design.

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>BilnrSeln</td>
<td><p>Bilinear Selection (BS-axis).</p>
<p><em>If BilnrSeln is less than or equal to BilnrSelnTbl[0], BilnrSeln
will be assigned BilnrSelnTbl[0] and the BS index will be set to 0. If
BilnrSeln is greater or equal to BilnrSerlnTbl[BilnrSelnSize – 1], then
the BilnrSeln will be assigned BilnrSelnTbl[BilnrSelnSize – 1] and the
BS index will be set to BilnrSelnSize – 2.</em></p></td>
</tr>
<tr class="even">
<td>Inp</td>
<td><p>Input (X-axis).</p>
<p><em>If Inp is less than or equal to XTbl[0], the value will be
assigned XTbl[0] and the X index will be set to 0. If it is greater than
or equal to XTbl[XSize – 1], Inp will be assigned XTbl[XSize – 1] and
the X index will be set to XSize – 2.</em></p></td>
</tr>
<tr class="odd">
<td>BilnrSelnTbl[]</td>
<td>Bilinear selection table</td>
</tr>
<tr class="even">
<td>BilnrSelnSize</td>
<td>Number of elements in Bilinear selection table</td>
</tr>
<tr class="odd">
<td>XTbl[]</td>
<td>X table</td>
</tr>
<tr class="even">
<td>MplYTbl[]</td>
<td><p>Y table (Number of elements = BilnrSelnSize * XSize)</p>
<p><em>In most cases, Y table will be a 2-D table, and is declared as
MplYTbl[BilnrSelnSize][XSize]</em></p></td>
</tr>
<tr class="odd">
<td>XSize</td>
<td>Size of X table</td>
</tr>
</tbody>
</table>

## API

The input and output variables are defined as uint16 or sint16 for
purposes of min and max ranges. However, calibrations with different
resolutions, for example u8p8, can be used because they are still
represented as a 16-bit value within these functions.

|                      |                                         |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_u16_u16CmnXu16MplY | Type       | Min | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0   | 65535 |
|                      | Inp                                     | uint16     | 0   | 65535 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0   | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1   | 65535 |
|                      | XTbl\[\]                                | uint16\[\] | 0   | 65535 |
|                      | MplYTbl\[\]                             | uint16\[\] | 0   | 65535 |
|                      | XSize                                   | uint16     | 1   | 65535 |
| **Return Value**     |                                         | uint16     | 0   | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_s16_u16CmnXs16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | uint16     | 0      | 65535 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | XTbl\[\]                                | uint16\[\] | 0      | 65535 |
|                      | MplYTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_s16_s16CmnXs16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | XTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | MplYTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_u16_s16CmnXu16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | XTbl\[\]                                | sint16\[\] | -32768 | 32767 |
|                      | MplYTbl\[\]                             | uint16\[\] | 0      | 65535 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | uint16     | 0      | 65535 |

## Variable X Axis Bilinear Interpolation Functions

The following functions are available for bilinear interpolation with a
variable X-axis and are based on equation (10). The table below defines
each argument used in the API. Note that some functions require and/or
return unsigned or signed values. It is up to the designer to pick the
proper interpolation function for their design.

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr class="header">
<th>Argument</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>BilnrSeln</td>
<td><p>Bilinear Selection (BS-axis).</p>
<p><em>If BilnrSeln is less than or equal to BilnrSelnTbl[0], BilnrSeln
will be assigned BilnrSelnTbl[0] and the BS index will be set to 0. If
BilnrSeln is greater or equal to BilnrSerlnTbl[BilnrSelnSize – 1], then
the BilnrSeln will be assigned BilnrSelnTbl[BilnrSelnSize – 1] and the
BS index will be set to BilnrSelnSize – 2.</em></p></td>
</tr>
<tr class="even">
<td>Inp</td>
<td><p>Input (X-axis).</p>
<p><em>If Inp is less than or equal to XTbl[0], the value will be
assigned XTbl[0] and the X index will be set to 0. If it is greater than
or equal to XTbl[XSize – 1], Inp will be assigned XTbl[XSize – 1] and
the X index will be set to XSize – 2.</em></p></td>
</tr>
<tr class="odd">
<td>BilnrSelnTbl[]</td>
<td>Bilinear selection table</td>
</tr>
<tr class="even">
<td>BilnrSelnSize</td>
<td>Number of elements in Bilinear selection table</td>
</tr>
<tr class="odd">
<td>MplXTbl []</td>
<td><p>X table (Number of elements = BilnrSelnSize * XSize)</p>
<p><em>In most cases, X table will be a 2-D table, and is declared as
MplXTbl[BilnrSelnSize][XSize]</em></p></td>
</tr>
<tr class="even">
<td>MplYTbl[]</td>
<td><p>Y table (Number of elements = BilnrSelnSize * XSize)</p>
<p><em>In most cases, Y table will be a 2-D table, and is declared as
MplYTbl[BilnrSelnSize][XSize]</em></p></td>
</tr>
<tr class="odd">
<td>XSize</td>
<td>Size of X table</td>
</tr>
</tbody>
</table>

## API

The input and output variables are defined as uint16 or sint16 for
purposes of min and max ranges. However, calibrations with different
resolutions, for example u8p8, can be used because they are still
represented as a 16-bit value within these functions.

|                      |                                         |            |     |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_u16_u16MplXu16MplY | Type       | Min | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0   | 65535 |
|                      | Inp                                     | uint16     | 0   | 65535 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0   | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1   | 65535 |
|                      | MplXTbl\[\]                             | uint16\[\] | 0   | 65535 |
|                      | MplYTbl\[\]                             | uint16\[\] | 0   | 65535 |
|                      | XSize                                   | uint16     | 1   | 65535 |
| **Return Value**     |                                         | uint16     | 0   | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_u16_s16MplXu16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | MplXTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | MplYTbl\[\]                             | uint16\[\] | 0      | 65535 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | uint16     | 0      | 65535 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_s16_s16MplXs16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | sint16     | -32768 | 32767 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | MplXTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | MplYTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

|                      |                                         |            |        |       |
|-------------|-------------------------|-------------|----------|-------------|
| **Function Name**    | BilnrIntrpnWithRound_s16_u16MplXs16MplY | Type       | Min    | Max   |
| **Arguments Passed** | BilnrSeln                               | uint16     | 0      | 65535 |
|                      | Inp                                     | uint16     | 0      | 65535 |
|                      | BilnrSelnTbl\[\]                        | uint16\[\] | 0      | 65535 |
|                      | BilnrSelnSize                           | uint16     | 1      | 65535 |
|                      | MplXTbl\[\]                             | uint16\[\] | 0      | 65535 |
|                      | MplYTbl\[\]                             | sint16\[\] | -32768 | 32767 |
|                      | XSize                                   | uint16     | 1      | 65535 |
| **Return Value**     |                                         | sint16     | -32768 | 32767 |

# Known Limitations With Design

1.  The linear interpolation functions are implemented using signed
    32-bit values for the calculation of the interpolation. If the
    product of the X and Y terms in the numerator are greater than or
    equal to 2,147,483,648 or 0x80000000 the rounding functions will
    apply the rounding incorrectly resulting in a 1 count error due to
    an overflow of the sign-bit. The truncating functions should be used
    in these situations.

2.  The bilinear functions are calculated using single-precision
    floating point math.

3.  Values of tables for linear interpolation X-axis and each row in the
    x-axis in a bilinear interpolation are assumed to be increasing in
    value.

4.  Consider the array of values below:

| Index  | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
|--------|-----|-----|-----|-----|-----|-----|-----|-----|
| X-Axis | 0   | 1   | 2   | 2   | 2   | 2   | 2   | 2   |
| Y-Axis | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 |

> These values can be used in the interpolation library. If the input
> value is less than 2, then the interpolation will be performed as
> described in this document. If the value is greater than or equal to
> 2, then index 7 will be returned. This also is true for the bilinear
> selection table.

1.  Consider the array of values below:

| Index  | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
|--------|-----|-----|-----|-----|-----|-----|-----|-----|
| X-Axis | 0   | 1   | 2   | 2   | 2   | 2   | 2   | 4   |
| Y-Axis | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 |

> These values can also be used in the interpolation library. If the
> input value is less than 2, then the interpolation will be performed
> as described in this document. If the value is greater than or equal
> to 2 and less than 4, the function will interpolate between index 6
> and 7 as described in this document. If the value is greater than or
> equal to 4, index 7 is returned. This also is true for the bilinear
> selection table.

1.  All division operations in linear interpolation functions are not
    protected for division by zero to save on execution time. The
    designer shall take all efforts to ensure that the values selected
    for the tables will not result in a divide by zero operation.

# Appendix A

The following section will demonstrate how equation (9) is recorded into
the equation (10) described in the section Bilinear Interpolation.

Using equation (9) from section 5.2, the numerator and denominator can
be subsitutituted for y~num~ and y~den~ as shown in equation (A1).

|     | $$y = \frac{\left( BS - {BS}_{1} \right)\left( Y_{2_{Num}} \right)\left( Y_{1_{Den}} \right) - \left( BS - {BS}_{1} \right)\left( Y_{1_{Num}} \right)\left( Y_{2_{Den}} \right) + \left( {BS}_{2} - {BS}_{1} \right)\left( Y_{1_{Num}} \right)\left( Y_{2_{Den}} \right)}{\left( {BS}_{2} - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( Y_{2_{Den}} \right)} = \frac{y_{num}}{y_{den}}$$ | (A1) |
|----|---------------------------------------------------------------|------|

Substituting back in all the terms in y~num~, the numerator can be
simplified as shown in equations A2 to A4.

Expanding the Y~1Num~ and Y~2Num~ term:

|     | $$y_{num} = \left( BS - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( \left( x - x_{2} \right)\left( y_{3} - y_{2} \right) + \left( Y_{2_{Den}} \right)y_{2} \right) - \left( BS - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( \left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) + \left( Y_{1_{Den}} \right)y_{0} \right) + \left( {BS}_{2} - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( \left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) + \left( Y_{1_{Den}} \right)y_{0} \right)$$ |     |
|----|---------------------------------------------------------------|------|

|     | $$y_{num} = \left( BS - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( x - x_{2} \right)\left( y_{3} - y_{2} \right) + \left( BS - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( Y_{2_{Den}} \right)y_{2} - \left( BS - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) - \left( BS - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( Y_{1_{Den}} \right)y_{0} + \left( {BS}_{2} - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) + \left( {BS}_{2} - {BS}_{1} \right)\left( Y_{2_{Den}} \right)\left( Y_{1_{Den}} \right)y_{0}$$ | (A2) |
|----|---------------------------------------------------------------|------|

Simplifying (A2)

|     | $$y_{num} = \left( BS - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( x - x_{2} \right)\left( y_{3} - y_{2} \right) + \left( BS - {BS}_{1} \right)\left( Y_{1_{Den}} \right)\left( Y_{2_{Den}} \right)\left( y_{2} - y_{0} \right) + \left( {BS}_{2} - BS \right)\left( Y_{2_{Den}} \right)\left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right) + \left( y_{den} \right)\left( y_{0} \right)$$ | (A3) |
|----|---------------------------------------------------------------|------|

Now equation (A3) can be grouped into smaller terms and simplified.

|     | $$y_{num} = \left( BS - {BS}_{1} \right)\left( x_{1} - x_{0} \right)\left( x - x_{2} \right)\left( y_{3} - y_{2} \right) + \left( BS - {BS}_{1} \right)\left( x_{1} - x_{0} \right)\left( x_{3} - x_{2} \right)\left( y_{2} - y_{0} \right) + \left( {BS}_{2} - BS \right)\left( {x - x}_{0} \right)\left( {y_{1} - y}_{0} \right)\left( x_{3} - x_{2} \right) + \left( y_{den} \right)\left( y_{0} \right)$$ |     |
|----|---------------------------------------------------------------|------|

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 86%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>1<em>a</em></sub> = (<em>x</em><sub>3</sub>−<em>x</em><sub>2</sub>)(<em>y</em><sub>1</sub> − <em>y</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>1<em>b</em></sub> = (<em>B</em><em>S</em><sub>2</sub> − <em>B</em><em>S</em><sub>1</sub>)(<em>x</em> − <em>x</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>2<em>a</em>3<em>a</em></sub> = (<em>B</em><em>S</em> − <em>B</em><em>S</em><sub>1</sub>)(<em>x</em><sub>1</sub> − <em>x</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>2<em>b</em></sub> = (<em>x</em><sub>3</sub> − <em>x</em><sub>2</sub>)(<em>y</em><sub>2</sub> − <em>y</em><sub>0</sub>)</span></p>
<p><span
class="math display"><em>T</em><em>e</em><em>r</em><em>m</em><sub>3<em>b</em></sub> = (<em>x</em> − <em>x</em><sub>2</sub>)(<em>y</em><sub>3</sub> − <em>y</em><sub>2</sub>)</span></p>
<p><span class="math display">$$y = \frac{y_{num}}{y_{den}} = y_{0} +
\left( \frac{\left( {Term}_{2a3a} \right)\left( {Term}_{3b} \right) +
\left( {Term}_{2a3a} \right)\left( {Term}_{2b} \right) + \left(
{Term}_{1a} \right)\left( {Term}_{1b} \right)}{\left( {BS}_{2} -
{BS}_{1} \right)\left( x_{1} - x_{0} \right)\left( x_{3} - x_{2}
\right)} \right)$$</span></p></th>
<th>(A4)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Appendix B

The equations below can be used by a designer to see the impact of the
truncating and rounding functions on their design.

## Truncating Linear Interpolation Functions

From equations (2) and (3), the truncated result can be characterized by
equations (B1) and (B2).

## Fixed X-Axis Interpolation Function

|     | $$y = y_{0} + \left\lfloor (y_{1} - y_{0})\frac{\left( x - x_{0} \right)}{\mathrm{\Delta}x} \right\rfloor$$ | (B1) |
|------|------------------------------------------------------------|------|

## Variable X-Axis Interpolation Function

|     | $$y = y_{0} + \left\lfloor (y_{1} - y_{0})\frac{\left( x - x_{0} \right)}{\left( x_{1} - x_{0} \right)} \right\rfloor$$ | (B2) |
|------|------------------------------------------------------------|------|

## Rounding Linear Interpolation Functions

From equations (2) and (3), the rounding result can be characterized by
equations (B3) and (B4).

## Fixed X-Axis Interpolation Function

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 86%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><p><span class="math display">$$y = y_{0} + \frac{\left( \left(
y_{1} - y_{0} \right)\left( x - x_{0} \right) + \left(
\frac{\mathrm{\Delta}x}{2} \right) \right)}{\mathrm{\Delta}x},\ if\
\left( y_{1} - y_{0} \right)\left( x - x_{0} \right) \geq 0$$</span></p>
<p><span class="math display">$$y = y_{0} + \frac{\left( \left( y_{1} -
y_{0} \right)\left( x - x_{0} \right) - \left(
\frac{\mathrm{\Delta}x}{2} \right) \right)}{\mathrm{\Delta}x},\ if\
\left( y_{1} - y_{0} \right)\left( x - x_{0} \right) &lt;
0$$</span></p></th>
<th>(B3)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Variable X-Axis Interpolation Function

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 86%" />
<col style="width: 6%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><p><span class="math display">$$y = y_{0} + \frac{\left( \left(
y_{1} - y_{0} \right)\left( x - x_{0} \right) + \left( \frac{\left(
x_{1} - x_{0} \right)}{2} \right) \right)}{\left( x_{1} - x_{0}
\right)},\ if\ \left( y_{1} - y_{0} \right)\left( x - x_{0} \right) \geq
0$$</span></p>
<p><span class="math display">$$y = y_{0} + \frac{\left( \left( y_{1} -
y_{0} \right)\left( x - x_{0} \right) - \left( \frac{\left( x_{1} -
x_{0} \right)}{2} \right) \right)}{\left( x_{1} - x_{0} \right)},\ if\
\left( y_{1} - y_{0} \right)\left( x - x_{0} \right) &lt;
0$$</span></p></th>
<th>(B4)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Appendix C

The chart below shows the estimated number of clock cycles that are
required for the fixed x-axis linear interpolation for various
calculation methods. The source file was converted to assembly code for
the Renesas RH850 microcontroller targeted for EA4 applications. The
number of cycles for each instruction was determined based on the
software user’s manual \[1\]. The best/worst case values are based on
all predictive branching passing or failing and all other optimizations
are ignored.

Based on the information, use of floating point calculations is too
costly in terms of clock cycles for use throughout the project. Where
the truncating and rounding functions offer the same results for almost
half the execution time.

{% endraw %}