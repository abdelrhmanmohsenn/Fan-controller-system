### 🌪️ Fan Controller System 
This project is a Fan Controller System based on two PIC18F46K20 microcontrollers communicating with each other through the I2C bus. One microcontroller acts as the master controller, responsible for timekeeping and temperature sensing, while the other serves as the slave controller, controlling the fan based on temperature readings. Here's a breakdown of the system:

## Hardware Requirements
- Two PIC18F46K20 microcontrollers
- TC74 temperature sensor
- DC motor for fan control
- RealTimeClockDS1307 for time tracking
- EEPROM_24C02C for storing 

## Master Controller
- Manages the Real-Time Clock (DS1307) for timekeeping.
- Utilizes an EEPROM (24C02C) for storing configuration values.
- Interfaces with a Temperature Sensor (TC74) to read ambient temperature.
- Communicates with the Slave Controller via I2C to control fan operation.
  
## Slave Controller
- Monitors the ambient temperature received from the Master Controller.
- Controls a DC motor for fan operation based on temperature thresholds.

## schematic
![image](https://github.com/abdelrhmanmohsenn/Fan-controller-system/assets/146861505/68891ca1-5b78-418b-a99c-6f3c7936c0b0)

## Notes
- Make sure to properly initialize the I2C bus and configure the communication addresses.
- Adjust temperature thresholds and fan speed control as needed for your application.

## Acknowledgements
This project utilizes Microchip's MCC generated files for I2C communication, real-time clock, EEPROM, and temperature sensor interfacing.
