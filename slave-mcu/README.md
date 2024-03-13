# 🌀 Slave Controller Code 

## Overview
The slave controller, based on the PIC18F46K20 microcontroller, communicates with a master controller via the I2C bus. It receives temperature data from the master and controls a DC motor based on the received temperature value. This readme provides an overview of the slave controller code and its functionalities.

## Code Explanation
### Initialization
- `SYSTEM_Initialize()`: Initializes the device peripherals and configurations.
  
- `INTERRUPT_GlobalInterruptHighEnable()`: Enables high priority global interrupts.
  
- `INTERRUPT_GlobalInterruptLowEnable()`: Enables low priority global interrupts.
  
- `INTERRUPT_PeripheralInterruptEnable()`: Enables peripheral interrupts.

### I2C Communication
- `I2C_Open()`: Opens the I2C communication in slave mode.
  
- `I2C_SlaveSetReadIntHandler(Custom_I2C_SlaveDefRdInterruptHandler)`: Sets a custom function as the handler for the I2C read interrupt.

### Custom I2C Read Interrupt Handler
- `Custom_I2C_SlaveDefRdInterruptHandler()`: This function is called when the slave receives data from the master. It reads the received temperature value from `SSPBUF`.

### DC Motor Control
- The main loop checks the received temperature value (`RecTC74_A7_TempValue`) and controls the DC motor accordingly:
  - If the temperature is greater than 35, it sets one GPIO pin to high and the other to low. This likely corresponds to clockwise rotation of the DC motor.
  - If the temperature is 35 or below, it sets both GPIO pins to low, likely stopping the motor.

## Note
- Modify GPIO pin assignments and motor control logic as needed for specific hardware setup.
- Adjust temperature thresholds for desired fan speed control.
