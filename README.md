# Transforming my Raspberry Pi into a Dynamic Keyboard and Mouse Emulator

This project uses a Raspberry Pi to act as a virtual keyboard and mouse, sending input commands to a connected computer. Using the zero_hid library, it manages HID (Human Interface Device) signals, effectively turning the Raspberry Pi into an input device capable of mouse clicks, movements, and keystrokes.

- Each input action (click, scroll, type) triggers a sequence of HID codes to send to the connected computer, which interprets them as inputs.
- The mouse and keyboard, inputs are cleared using 0x0 to prevent commands from remaining "pressed," ensuring the virtual device responds like a real HID device.
- The zero_hid library facilitates USB HID emulation, while USBhid-dump inspects and tests USB communication codes.

For reference, visit the [GitHub repository](https://github.com/thewh1teagle/zero-hid/tree/main/zero_hid).

## Instructions
# 1. Setting Up Classes

- Ensure the files from the link above correctly reference the required Mouse and Keyboard classes.
- These classes may differ from those in Python’s default library because they were downloaded as part of the project.
- To confirm which class the code references, use Python’s dir() function to inspect the loaded classes and methods.
- Due to versioning, some methods may not be available. Double-check these class definitions for compatibility.
  
# 2. Understanding USB Mouse Codes and Connections
For more detailed information on USB mouse codes, refer to [this Guide](https://wiki.osdev.org/Mouse_Input). *Remember that every mouse configures differently when connected to a new device.*

- To identify the hex codes your mouse sends when a button is clicked:
- Open a terminal and enter: sudo usbhid-dump --entity=all

# 3. Mouse Hex Codes and Binary Representation
USB mouse commands are represented in binary, with a structure like this:

```arduino

Y overflow : X overflow : Y sign bit : X sign bit : Always 1 : Middle button : Right button : Left button

```

Here are the universal hex codes for mouse buttons:
```
Left button: 0x01
Right button: 0x02
Middle button (scroll): 0x04

```

For example:

The middle button has a binary representation of 0000100, equivalent to the hex 0x04.

# 4. Code Overview for Mouse Events
The code uses send_mouse_event(self.dev, 0x0, 0, 0, 0, 0) where:

- The structure includes five hex positions, represented as *\x(Button) \x(X Position) \x(Y Position) \x(Scroll Wheel)*
- An additional zero is added at the end to support certain mice with a side scroll wheel.

#5. Scrolling Hex Codes
For scrolling, coordinates range from 1 to 255:

- Scroll Up: 0x01
- Scroll Down: 0xFF (hex representation of 255)

# 6. Clearing Mouse Commands
To clear mouse commands and reset any button presses, follow these steps:

- Use a time delay with import time to control the timing of each command.
- Set any pressed button to 0x0 to release it after an action, preventing unintended continued input.
