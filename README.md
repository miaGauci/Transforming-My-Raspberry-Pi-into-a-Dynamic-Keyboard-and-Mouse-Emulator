# Transforming my Raspberry Pi into a Dynamic Keyboard and Mouse Emulator

This project uses a Raspberry Pi to act as a virtual keyboard and mouse, sending input commands to a connected computer. Using the zero_hid library, it manages HID (Human Interface Device) signals, effectively turning the Raspberry Pi into an input device capable of mouse clicks, movements, and keystrokes.

- Each input action (click, scroll, type) triggers a sequence of HID codes to send to the connected computer, which interprets them as inputs.
- The mouse and keyboard, inputs are cleared using 0x0 to prevent commands from remaining "pressed," ensuring the virtual device responds like a real HID device.
- The zero_hid library facilitates USB HID emulation, while USBhid-dump inspects and tests USB communication codes.
