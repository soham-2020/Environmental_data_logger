# Environmental_data_logger
Its a microcontroller based smart environmentalo data logger that can Measure temperature, humidity, light intensity, and air quality which can be connected to the socket present there 
and also it can display real tume reading on LCD which can be connected to the socket present.It requires a 5v USB power input it consist of three main units:
1)Control unit:
Contains atmega328-P a crystall oscillator and a push button it is a brain of the system it is responsible for executing programmable instruction managing communication protocols and controlling the
signals.
2)Power managment block:
It is responsible for managing the voltage rail and it regulates the voltage from 5v to 3.3v it filters out the noise by using capacitor,it also contain a led which is responsible for telling the user
that whether the power is reaching the board or not,voltage regulator is working finr and the board is not internally burnt it also have a resisitor which is important so that led doesnt burn.
3)Sensor and Interfaces:
Here we have a micro sd card which operates at 3.3v only, we use spi mode of communication for it we also have pull up and pull down resistors whoch is to prevent the floating signals(these are corrupted
data and unpredcitable voltage) we are using BSS138 mosfet as logic shifter for making 5v to 3.3v.
