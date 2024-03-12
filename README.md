### 🌪️ Fan Controller System 
- Overall System Readme
This project is a Fan Controller System based on two PIC18F46K20 microcontrollers communicating with each other through the I2C bus. One microcontroller acts as the master controller, responsible for timekeeping and temperature sensing, while the other serves as the slave controller, controlling the fan based on temperature readings. Here's a breakdown of the system:

## Master Controller
- Manages the Real-Time Clock (DS1307) for timekeeping.
- Utilizes an EEPROM (24C02C) for storing configuration values.
- Interfaces with a Temperature Sensor (TC74) to read ambient temperature.
- Communicates with the Slave Controller via I2C to control fan operation.
## Slave Controller
- Monitors the ambient temperature received from the Master Controller.
- Controls a DC motor for fan operation based on temperature thresholds.
