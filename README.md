<a href="https://www.microchip.com" rel="nofollow"><img src="images/microchip.png" alt="MCHP" width="300"/></a>

# Getting Started with Digital to Analog Converter (DAC) using the AVR64DD32 Microcontroller Generated with MCC Melody

<br>The repository contains four MPLAB® X projects:

1.  [Generating a Constant Analog Signal](#1-generating-a-constant-analog-signal-using-the-10-bit-dac) - This use case shows how to generate a constant signal using the DAC peripheral.
2.  [Generating a Sine Wave Signal](#2-generating-a-sine-wave-signal-using-the-10-bit-dac) - This use case shows how to generate a Sine Wave signal using the DAC peripheral.
3.  [Generating a Amplitude Modulated Signal](#3-generating-a-amplitude-modulated-signal-using-the-10-bit-dac) - This use case shows how to generate the Amplitude Modulated (AM) signal using the DAC peripheral.
4.  [Reading DAC with ADC](#4-reading-the-dac-internally-with-the-adc) - This project provides a bare metal code example for a basic DAC configuration. This use case shows how to read the voltage on DAC0 output with the Analog to Digital Converter (ADC0).

## Related Documentation

More details and code examples on the AVR64DD32 can be found at the following links:

- [AVR64DD32 Product Page](https://www.microchip.com/wwwproducts/en/AVR64DD32)
- [AVR64DD32 Code Examples on GitHub](https://github.com/microchip-pic-avr-examples?q=AVR64DD32)
- [AVR64DD32 Project Examples in START](https://start.atmel.com/#examples/AVR64DD32CuriosityNano)

## Software Used

- [MPLAB® X IDE](http://www.microchip.com/mplab/mplab-x-ide) v6.00 or newer
- [MPLAB® XC8](http://www.microchip.com/mplab/compilers) v2.36 or newer
- [AVR-Dx Series Device Pack](https://packs.download.microchip.com/) v2.1.152 or newer
- [MPLAB® Code Configurator Melody](https://www.microchip.com/en-us/tools-resources/configure/mplab-code-configurator/melody) v2.1.9 or newer
- AVR Devices Library v4.4.0 or newer
- Content Manager v2.3.6 or newer

## Hardware Used

- The AVR64DD32 Curiosity Nano Development Board is used as a test platform.
  <br><img src="images/AVR64DD32.PNG" width="640">
- Oscilloscope/Logic Analyzer

## Operation

To program the Curiosity Nano board with this MPLAB® X project, follow the steps provided in the [How to Program the Curiosity Nano board](#how-to-program-curiosity-nano-board) chapter.<br><br>

## 1. Generating a Constant Analog Signal Using the 10-Bit DAC

This use case shows how to generate a constant signal using the DAC peripheral. Initialize the DAC, set the 2.048V internal voltage reference for the DAC peripheral, set the DAC to output a specific constant voltage.

### 1.1 Setup

The following configurations must be made for this project:

- System clock is configured at 4 MHz (default)
- V<sub>REF</sub>:
  - Select the 2.048V internal voltage reference for the DAC peripheral
  - Set the Voltage Reference in Always On mode
- DAC0:
  - Enable DAC
  - Enable the output buffer
  - Enable Run-In Standby (RUNSTBY) mode
  - Disable digital input buffer and the pull-up resistor for the DAC output external pin (PD6)

### 1.2 Demo

<br>PD6 - Constant analog signal (1.2V) on Channel 0 (black) below.
<br><img src="images/AVR-DD_DAC_demo1-1.png">

### 1.3 Summary

This example represents a basic functionality of the DAC peripheral. The DAC peripheral is used to generate a constant signal.<br><br>
[Back to top](#getting-started-with-digital-to-analog-converter-dac-using-the-avr64dd32-microcontroller-generated-with-mcc-melody)<br>

## 2. Generating a Sine Wave Signal Using the 10-Bit DAC

This use case shows how to generate a Sine Wave signal using the DAC peripheral. Initialize the DAC, set the 2.048V internal voltage reference for the DAC peripheral, set the DAC to output in a loop the samples of a sine wave.

### 2.1 Setup

The following configurations must be made for this project:

- System clock is configured at 4 MHz (default)
- V<sub>REF</sub>:
  - Select the 2.048V internal voltage reference for the DAC peripheral
  - Set the Voltage Reference in Always On mode
- DAC0:
  - Enable DAC
  - Enable the output buffer
  - Enable Run-In Standby (RUNSTBY) mode
  - Disable digital input buffer and the pull-up resistor for the DAC output external pin (PD6)

### 2.2 Demo

<br>PD6 - Sine wave on Channel 0 (black) below.
<br><img src="images/AVR-DD_DAC_demo2-1.png">

### 2.3 Summary

This example represents a basic functionality of the DAC peripheral. The DAC peripheral is used to generate a Sine Wave signal by setting the output in a loop.<br><br>
[Back to top](#getting-started-with-digital-to-analog-converter-dac-using-the-avr64dd32-microcontroller-generated-with-mcc-melody)<br>

## 3. Generating a Amplitude Modulated Signal Using the 10-Bit DAC

This use case shows how to generate the AM signal using the DAC peripheral. Initialize the DAC with external voltage reference and link the signal that must be modulated to the external reference pin (PD7). The AVR® core will continuously change the Data (DACn.DATA) register to create a modulated signal.

### 3.1 Setup

The following configurations must be made for this project:

- System clock is configured at 4 MHz (default)
- V<sub>REF</sub>:
  - Select the external voltage reference on VREFA pin (PD7) for the DAC peripheral
  - Set the Voltage Reference in Always On mode
- DAC0:
  - Enable DAC
  - Enable the output buffer
  - Enable RUNSTBY mode
  - Disable digital input buffer and the pull-up resistor for the DAC output external pin (PD6)

|     Pin     | Configuration  |
| :---------: | :------------: |
| PD7 (VREFA) |  Analog Input  |
|     PD6     | Digital Output |

### 3.2 Demo

<br>External Analog Signal (information signal) on VREFA (PD7) pin - Channel 1 (orange) in the screenshot below.
<br>AM Signal on PD6 - Channel 2 (blue) in the screenshots below.

<br><img src="images/AVR-DA_DAC_demo3-1.jpg" width="500">

<br><img src="images/AVR-DA_DAC_demo3-2.jpg" width="500">

### 3.3 Summary

This example represents a basic functionality of the DAC peripheral. The DAC peripheral is used to generate an AM signal using an external signal.<br><br>
[Back to top](#getting-started-with-digital-to-analog-converter-dac-using-the-avr64dd32-microcontroller-generated-with-mcc-melody)<br>

## 4. Reading the DAC Internally with the ADC

This project provides a bare metal code example for a basic DAC configuration. This use case shows how to read the voltage on DAC0 output with the ADC0. First, initialize the DAC and ADC, set the DAC peripheral as input for the ADC, set the 2.048V internal voltage reference for the DAC and ADC peripherals, increment the DAC output and read it with the ADC for each step.

### 4.1 Setup

The following configurations must be made for this project:

- System clock is configured at 4 MHz (default)
- V<sub>REF</sub>:
  - Select the 2.048V internal voltage reference for the DAC peripheral
  - Select the 2.048V internal voltage reference for the ADC peripheral
  - Set the Voltage References in Always On mode
- DAC0:
  - Enable DAC
- ADC0:
  - Enable ADC
  - Select 12-bit resolution
  - Select DIV2 prescaler
  - Set the DAC peripheral as input for the ADC

### 4.2 Demo

<br>Theoretical results for dacVal = 100
<br><img src="images/AVR-DD_DAC_demo4-1.png" width="500">
<br>Practical results for dacVal = 100 using Debug Mode
<br><img src="images/AVR-DD_DAC_demo4-2.png" width="900">

### 4.3 Summary

This example represents a basic functionality of the DAC peripheral. The ADC peripheral reads the value from a step-by-step incremented value for the DAC peripheral.<br><br>
[Back to top](#getting-started-with-digital-to-analog-converter-dac-using-the-avr64dd32-microcontroller-generated-with-mcc-melody)<br>

## How to Program Curiosity Nano board

This chapter shows how to use the MPLAB® X IDE to program an AVR® device with an Example_Project.X. This can be applied for any other projects.

- Connect the board to the PC.

- Open the Example_Project.X project in MPLAB® X IDE.

- Set the Example_Project.X project as main project.

  - Right click the project in the **Projects** tab and click **Set as Main Project**.
    <br><img src="images/Program_Set_as_Main_Project.PNG" width="600">

- Clean and build the Example_Project.X project.

  - Right click the **Example_Project.X** project and select **Clean and Build**.
    <br><img src="images/Program_Clean_and_Build.PNG" width="600">

- Select **AVRxxxxx Curiosity Nano** in the Connected Hardware Tool section of the project settings:

  - Right click the project and click **Properties**.
  - Click the arrow under the Connected Hardware Tool.
  - Select **AVRxxxxx Curiosity Nano** (click the **SN**), click **Apply** and then **OK**:
    <br><img src="images/Program_Tool_Selection.PNG" width="600">

- Program the project to the board.
  - Right click the project and click **Make and Program Device**.
    <br><img src="images/Program_Make_and_Program_Device.PNG" width="600">

<br>

- [Back to 1. Generating a Constant Analog Signal](#1-generating-a-constant-analog-signal-using-the-10-bit-dac)
- [Back to 2. Generating a Sine Wave Signal](#2-generating-a-sine-wave-signal-using-the-10-bit-dac)
- [Back to 3. Generating a Amplitude Modulated Signal](#3-generating-a-amplitude-modulated-signal-using-the-10-bit-dac)
- [Back to 4. Reading DAC with ADC](#4-reading-the-dac-internally-with-the-adc)
- [Back to top](#getting-started-with-digital-to-analog-converter-dac-using-the-avr64dd32-microcontroller-generated-with-mcc-melody)
