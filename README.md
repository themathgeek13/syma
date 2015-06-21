Syma S107 Arduino Driver and Python GUI Controller
--------------------------------------------------

This project contains code for an Arduino Driver for the Syma S107 RC Helicopter, as well as a virtual remote-control (in Python) for the same. The Syma S107 RC Helicopter responds to IR signals. The Arduino Driver converts information from the virtual remote-control into IR pulses that the Syma S107 can understand. 

The Python program creates a GUI representation of the remote control (albeit a crude one) and lets the user control the helicopter through a computer. The hardware aspect is pretty simple; all that is required is an IR LED that should be connected to the output-pin specified in the Arduino sketch. 

Most of the work on the driver was done by "Aqualung" from the RCGroups forum. I cleaned up the code, added comments, and reversed the polarities from the original driver. I also added some primitive flow-control to take into account the discrepancies between the data-transmission-rate between the arduino and the python GUI. 

The GUI sends data twice as fast as the arduino can consume it and so I added some code that to the driver that sends an ACK back to the GUI to let it know that it can send data. Until then, the GUI will queue up data. The code is heavily commented and should be easy to understand.

The library as forked from Vivin had some issues, since serial communication with Python is not a very good idea when working in real time. The backlog of commands can create serious issues when flying something that could be potentially dangerous. Having said that, I feel that the code was extremely well documented, and easy to understand and modify for my own purposes. I give Vivin full credit for that.

More than one IR led will be necessary to provide a larger field of view for the helicopter to work in, since a single IR led requires precise angling towards the heli to work properly. I read online about using NPN switching transistors to control three LEDs simultaneously, so I will be incorporating that soon.
