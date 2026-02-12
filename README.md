# Environmental_data_logger
The Environmental Data Logger is a microcontroller-based smart monitoring system designed to measure key environmental parameters such as temperature, humidity, light intensity, and air quality. The system supports real-time data display on an external LCD and allows long-term storage using a MicroSD card. It operates on a 5V USB power supply and is organized into three major functional blocks for modular and reliable design.


1)Control unit:
The control unit is built around the ATmega328-P microcontroller, supported by a crystal oscillator for precise clock generation and a push button for user interaction. Acting as the brain of the system, it executes programmed instructions, manages communication protocols such as SPI and I²C, and controls data acquisition from connected sensors.


2)Power managment block:
This block regulates the incoming 5V supply to a stable 3.3V required by low-voltage peripherals. Decoupling capacitors are used to filter noise and ensure a stable voltage rail. A status LED, along with a current-limiting resistor, provides visual confirmation of proper power delivery and system operation.



3)Sensor and Interfaces:
The system integrates a MicroSD card operating in SPI mode for reliable data logging. Pull-up and pull-down resistors are used to prevent floating signals, ensuring defined logic levels and improving communication stability. Additionally, BSS138 MOSFET-based level shifters safely translate logic between 5V and 3.3V devices, protecting sensitive components and enabling bidirectional communication.

Overall, the design follows a modular architecture that improves scalability, simplifies debugging, and enhances system reliability.
