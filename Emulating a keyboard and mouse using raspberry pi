from zero_hid import Mouse, Keyboard, KeyCodes
from zero_hid.hid.mouse import send_mouse_event
from zero_hid.hid.keyboard import send_keystroke, release_keys
import time
from typing import Union

# Mouse Emulation Class
class OMouse(Mouse):
    leftbutton = 0x01
    rightbutton = 0x02
    wheelbutton = 0x04
    noButtons = 0x0
    scrollUP = 0x01
    scrollDOWN = 0xFF
    __delay = 0.01
    
    def __init__(self):
        super().__init__()
        
    def left_click(self):
        send_mouse_event(self.dev, OMouse.leftbutton, 0, 0, 0, 0)
        time.sleep(OMouse.__delay)
        send_mouse_event(self.dev, OMouse.noButtons, 0, 0, 0, 0)
   
    def right_click(self):
        send_mouse_event(self.dev, OMouse.rightbutton, 0, 0, 0, 0)
        time.sleep(OMouse.__delay)
        send_mouse_event(self.dev, OMouse.noButtons, 0, 0, 0, 0)
        
    def scrollup(self):
        send_mouse_event(self.dev, 0, 0, 0, OMouse.scrollUP, 0)
        
    def scrolldown(self):
        send_mouse_event(self.dev, 0, 0, 0, OMouse.scrollDOWN, 0)
        
    def wheelClick(self):
        send_mouse_event(self.dev, OMouse.wheelbutton, 0, 0, 0, 0)
        time.sleep(OMouse.__delay)
        send_mouse_event(self.dev, OMouse.noButtons, 0, 0, 0, 0)
        
    def createEvent(self, buttons: Union[int, list] = 0, relX: int = 0, relY: int = 0, scroll: int = 0):
        buttonsPressed = 0
        if isinstance(buttons, int):
            buttons = [buttons]
        for but in buttons:
            buttonsPressed |= but
        send_mouse_event(self.dev, buttonsPressed, relX, relY, scroll, 0)

if __name__ == "__main__":
    for i in range(1):
        m = OMouse()
        print("Wait for it")
        m.createEvent(OMouse.wheelbutton)
        m.createEvent(OMouse.wheelbutton, 10, 10)
        m.createEvent()
        print("done")

# Keyboard Emulation Class
class CustomKeyboard(Keyboard):
    
    def __init__(self):
        super().__init__()
        
    def is_connected(self) -> bool:
        try:
            with open(self.dev, 'ab+') as hid_handle:
                hid_handle.write(bytearray([0]))
            return True
        except BlockingIOError:
            return False
    
    def press(self, mods: Union[int, list], key_code: int = 0, release: bool = True) -> None:
        """
        Sends keystrokes to the PC, including modifiers like CTRL
        """
        if isinstance(mods, list):
            if len(mods) == 1:
                mods = mods[0]
            else:
                mods = sum(mods)
        send_keystroke(self.dev, mods, key_code, release=release)

    def type_keys(self, text: str, delay: int = 0) -> bool:
        try:
            self.type(text, delay)
            return True
        except:
            return False

if __name__ == "__main__":
    k = CustomKeyboard()
    if k.is_connected():
        print("Keyboard connected:", k.is_connected())
        k.type_keys("A")
        print("Done")
    else:
        print("Please connect the keyboard.")
