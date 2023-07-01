# Device Server
The device server can be used to control smart home devices, etc.
Description of the Arduino-based device server
The server can be used to control smart home devices, etc.

The server consists of:
1. Arduino Mega, Uno, Mini or Nano board;
2. Wi-Fi adapter for connecting to the home network;
3. GSM module for connecting to the cellular network (optional);
4. A power supply board converting 12 volts to 5V and 3.3V (optional);
5. Logic level converter board from 3.3V to 5.5V to control the GSM module (optional);
6. Power supply unit powered from 220V with 12V output voltage.

Interaction with the server is via the HTTP protocol. Initially, a port map is sent to the device server, which describes what is connected to each port of the Arduino. According to this map, the control program will manage the devices connected to the ports. 
After receiving the port map, the server configures the ports to work with the corresponding communication protocols. 
The port map can not be sent as a whole for all ports, but directly together with a command to control a particular port or with a command to get the port status. This will not store the port map and allows you to easily reconnect the devices to different ports on the arduino. 
Commands can be sent to the server:
- [request status of all ports], 
- request the state of a specific port,
- command to set the output port value to an appropriate state. 
When requesting the status of the ports, the server collects information from all connected devices (using the protocols described in the port map) and sends it to the HTTP client.
A server port can consist of one or more physical Arduino ports. 
For example, a server port for connecting a stepper motor control driver (linear servo driver port) consists of the following physical Arduino ports:
1. PWM (step) port,
2. DIR port
3. Left end sensor port
4. Right end sensor port.
So the motor control port takes up 4 physical ports on the Arduino.
The control port of the ultrasonic distance sensor consists of the ports necessary for the I2C protocol which is used to control the distance sensor.
The relay control port consists of only one arduino port
The limit sensor port consists of one arduina port.
The variable resistor port consists of one analog port.
So the server port is not identical to the arduino port and is more complicated to control on the software level.

