
**I2C peripherals**
a 7-bit 12c device address is used to specify the intended subordinate
register-based interactions
the device datasheet tells you what you need to know
- the device address
- the number, nature and addresses of registers

**CODAL**
runtime cut down operating system

supports co-operative (non pre-emptive) threading and eventing
- a busy loop will prevent anything else from running
provides functions to interface with on-board hardware via the microbit object
- create an instance of it, like a variable
- access the functions like you would members of a struct
- be aware that asynchronous operations may take an appreciable amount of time

Clone, lancaster-university microbit v2 samples


**Debugging with CODAL**

serial monitor 

defaults to 8 data bits and no parity at 115200 bps

