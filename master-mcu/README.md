# 🌀 Master Controller Code Readme 🌀

## Overview
This readme explains the code for the master controller of an embedded fan controller system. The master controller, based on the PIC18F46K20 microcontroller, communicates with a slave controller via the I2C bus. It reads temperature data from a TC74 sensor and sends this data to the slave controller for fan speed control. Additionally, it interacts with a Real Time Clock (DS1307) and an EEPROM (24C02C) for system initialization and logging.

## Code Explanation
### Initialization
- `SYSTEM_Initialize()`: Initializes the device peripherals and configurations.
  
- `INTERRUPT_GlobalInterruptHighEnable()`: Enables high priority global interrupts.
  
- `INTERRUPT_GlobalInterruptLowEnable()`: Enables low priority global interrupts.
  
- `INTERRUPT_PeripheralInterruptEnable()`: Enables peripheral interrupts.

### Real Time Clock (DS1307)
- `RealTimeClockDS1307_Get_Date_Time()`: Reads date and time from the DS1307 Real Time Clock module.
  
- `Print_RealTimeClockDS1307()`: Logs the date and time through UART for debugging or monitoring purposes.

### EEPROM (24C02C) Initialization
- `EEPROM_24C02C_Write_Byte(0xA2, 0x08, 5)`: Writes a byte (value 5) to the EEPROM at address 0x08.
  
- `EEPROM_24C02C_Write_Byte(0xA6, 0x08, 6)`: Writes a byte (value 6) to the EEPROM at address 0x08.
  
- `U4RecValue = EEPROM_24C02C_Read_Byte(0xA2, 0x08)`: Reads a byte from EEPROM address 0x08 into `U4RecValue`.
  
- `U5RecValue = EEPROM_24C02C_Read_Byte(0xA6, 0x08)`: Reads a byte from EEPROM address 0x08 into `U5RecValue`.

### Temperature Sensor (TC74)
- `TC74_A7_TempValue = TempSensor_TC74_Read_Temp(0x9E)`: Reads the temperature value from the TC74 sensor with the I2C address 0x9E.
  
- `I2C_Write1ByteRegister(0x70, 0x00, TC74_A7_TempValue)`: Writes the temperature value to the slave controller with the I2C address 0x70.

### Main Loop
- The main loop continuously performs the following tasks:
  1. Reads the current date and time from the RTC.
  2. Logs the date and time through UART.
  3. Reads the temperature from the TC74 sensor.
  4. Writes the temperature value to the slave controller.
  5. Delays for 500 milliseconds before repeating.
  
