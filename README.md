# Python
Python Notes and Examples

### Definitions 
- Module; a program that can be imported to other programs, so that the fucntions and operations defined in the module can be reused in another program 

## Python Classes 

**import numpy**
**import pandas**
Used for working with data sets - analyzing, cleaning, exploring and manipulation of data 


**import re**
**import os**
**import glob**
**import atexit**


.append function is used to increase the number of elements in a fuction - to add a statement to a statement
```
#Class 1 
def printsmth():
  print "Hiya:)"
  
#Class2
import myfirstmodule
myfirstmodule.printsmth()

#Output ;
#Hiya:)
```

- __ is used to create a local variable to the class 

Example: __delay; is only local to the class it is initialised if called from another class it is not found 

## if __name__ == "__main__":
- tells the program that the code inside this if statement should only be executed if the program is executed as a standalone program 
- If the class containing this line is called from another program the lines of code under if __name__ == "__main__": will not be executed 
- hence if __name__ == "__main__": is used for testing purposes to make sure that the program works properly 

Difference between == and is operator 
  - The 'is' operator compares the identity of two objects while the == operator compares the values of two objects

Working with JSON 
```
import json 

from typing import Union !! research
```
JSON -> Python 
```
json.loads(x)
```
Python -> JSON
```
json.dumps(x)

file_name = "data1.json"
with open(file_name) as f:
    data = json.load(f)
    
print(data)
```
### Special Variables in Python 

A double underscore variable in Python is usually referred to as a dunder
  - python uses these variables in a 'special way'

The __init__ method for initialization is invoked when an instance of a class is created 

__init__ is a **constructor**

```
#Prints only the memory address of the string object 
# declare our own string class
class String:
      
    # magic method to initiate object
    def __init__(self, string):
        #Self allows access to the attributes and methods of each object in python (like this. in Java )
        self.string = string
          
# Driver Code
if __name__ == '__main__': #important used to check that class is working properly without affecting other classes 
      
    # object creation
    string1 = String('Hello')
  
    # print object location
    print(string1)
    
    #Output
    #<__main__.String object at 0x7fe992215390>
```

Representing our object using __repr__
```
# declare our own string class
class String:
      
    # magic method to initiate object
    #always put self as a parameter 
    #string is the parameter passed to the class
    def __init__(self, string):
        self.string = string
          
    # print our string object
    def __repr__(self):
        return 'Object: {}'.format(self.string)
  
# Driver Code
if __name__ == '__main__':
      
    # object creation
    string1 = String('Hello')
  
    # print object location
    print(string1)
    
    #output
    #Object: Hello
```

__file__ - contains the path to the module that is currently being imported from a different class 
         - this variable is updated using the import system
         
```
#Creating a method called 'hello' in a diff class 
def hello():
  print("this is imported from a different class");
  
#Importing the above and creating a new module 
import HelloWorld

#Calling the method created inside the module 
HelloWorld.hello()

#Printing the path of the HelloWorld file 
print(HelloWorld.__file__)
```
__new__ method
- Creates and returns the instance of a class
- __new__ method is a static method 
- It is required to pass a parameter cls 
- cls represents the class that is needed to be instantiated and the compiler automatically provides this parameter at the time of instantiaiton
- Using the cls keyword, we can only access the members of the class, whereas using the self keyword, we can access both the instance variables and the class attributes.
```
class Students(object):
	def __init__(self, idNo, grade):
		self._idNo = idNo
		self._grade = grade

	def __new__(cls, idNo, grade):
		print("Creating Instance")
		instance = super(Students, cls).__new__(cls)
		if 5 <= grade <= 10:
			return instance
		else:
			return None

	def __str__(self):
		return '{0}({1})'.format(self.__class__.__name__, self.__dict__)


stud1 = Students(1, 7)
print(stud1)

stud2 = Students(2, 12)
print(stud2)

```
### Syntax: super()

Return : Return a proxy object which represents the parent’s class.

#### First let us understand how inheritance in Python works 
Creating a Parent Class 
```
#Creating a Person class with Display methods 

# In Python 3.x "class Person" is
# equivalent to "class Person(object)"
class Person(object):

	#constructor of class 
	def __init__(self, name, id)
		self.name = name 
		self.id = id 
		
	#To check if the person is an employee 
	def Display(self):
		print(self.name, self.id)
		
	#Driver code 
	emp = Person("Mia", 102) #An object of a Person 
	emp.Display()
```
Creating a Child Class

```
class Emp(Person):
	 def Print(self):
	 	print("Emp class called:")
	Emp_details = Emp("Amy", 103)
	
	#calling the parent class function 
	Emp_details.Display()
	
	#calling child class function 
	Emp_details.Print()
```

Now

In an inherited subclass, a parent class can be referred with the used of the **super()** function. The super function returns a temporary object of the superclass that allows access to all of its methods to its child class

advantages; 
- You don't need to specify the parent class name to access its methods - can be used in both single and multiple inheritances 
- Super function is dynamic which continues to prove how Python is a dynamic language

```
#The classes dogs, cats and horses are a subclasses of animal class - single inheritance 
#Super function below
class Animals: 
	#initializing constructor 
	def __init__(self):
		self.legs = 4
		self.domestic = True 
		self.tail = True 
		self.mammals = True 
		
	def isMammal(self):
		if self.mammals:
			print("It is a mammal.")
#Dogs is a subclass of super class Animals 			
class Dogs(Animals)
	def __init__(self):
		super().__init__()
	
	def isMammal(self):
		super().isMammal()

class Horses(Animals):
	def __init__(self):
		super().__init__()
		
	def hasTailandLegs(self):
		if self.tail and self.legs == 4:
			print("Has legs and tail")
			
#Driver code 
Tom = Dogs()
Tom.isMammal()
Bruno = Horses()
Bruno.hasTailandLegs 
```

Syntax: from typing import Union 

## Global keyword 
**global** variable belongs to the global scope of the class 

##Socket Class 

### .gethostname 
returns the host name of the current system under which the Python interpreter is executed 
```
# Local host name
myHostName = socket.gethostname()
print("Name of the localhost is {}".format(myHostName))

#IP address of the local host 
myIP = socket.gethostbyname(myHostName)
print("IP address of the localhost is {}".format(myIP))
```

9th September 2022
Emulating a Keyboard and Mouse using a Raspberry Pi 
Project outline:
-	Basically, the raspberry pi is going to be connected to a machine which has outdated software ie we are not able to connect its screen through VNC (virtual network computing) hence we can’t control it remotely 
-	So a raspberry pi will be connected to these machines with outdated software, we will remotely (through vnc) connect to the raspberry pi, so if from my laptop I type ‘hello world’ the raspberry pi will receive these key strokes and will translate them to write these keystrokes on the machine 
-	The objective is to write a program to manage to translate these keystrokes and mouse movements from the laptop to the machine (rpi is basically a translator)
How to connect to VNC:
-	Name the rpi: in this case pierastry (ERAS being the project we’re working on)
-	The domain here is kir.st.com so to connect we use pierastry.kir.st.com 
-	The network port is 22 since we are using SFTP – SSH FTP – Secure Shell File Transfer Protocol (FTP is 21) 
-	You enter the username and password and then you can connect (ask from where they came from)
FileZilla is used to transfer files from the laptop to the rpi when using VNC 
Note before switching off
-	Make sure to shut down the Raspberry Pi on VNC 
Research:
-	Implement the config file since UDC does not have any devices included
Config file sys/class/udc
Friday: 
-	Try run main.py but you need the config before 
Pi cvm – go to website (pi cvm wikipage)
What needs to be done:
-	We found code on Git that was used for emulating a keyboard and mouse however it wasn’t used on a raspberry pi 
-	Understand and break down the code to try run it 
-	Open notes on laptop as a remote connection of the rpi
-	Make sure all the python libraries are installed 
-	Check how caps works 
-	Shift, control, alt 
-	Create class try.pi to test out 
To open terminal
-	Ctrl + alt +t
-	~~~~
-	Etc/g
-	Create class that has a number for keys 
-	Check how the keyboard class works 
Raspberry Pi, C and custom HID Devices – A BIT OF MYSTERY (damnsoft.org)
keyboard - Sending the right HID Keycode? - Stack Overflow
HID – Using the Keyboard Driver – Tetherscript
•	Bit 0 = LCTRL: Left Control Key
•	Bit 1 = LSHIFT: Left Shift Key
•	Bit 2 = LALT: Left Alt Key
•	Bit 3 = LWIN: Left Control Key
•	Bit 4 = RCTRL: Right Control Key
•	Bit 5 = RSHIFT: Right Shift Key
•	Bit 6 = RALT: Right Alt Key
•	Bit 7 = RWIN: Right Windows Key

Turn Raspberry Pi Zero in USB Keyboard | Random Nerd Tutorials
Good method but it said it doesn’t work for rpi 3 
-	Zero-hid library
-	Keymap file – hexadecimal char - Keybaord = '/dev/hidg0' - mouse = '/dev/hidg1'




from typing import List
ModuleNotFoundError; thonny.plugins.cpython.hid
from .hid.keyboard import send_keystroke, release_keys
from .hid.keycodes import KeyCodes
from time import sleep
import json
import operator
from functools import reduce
import pkgutil
from typing import Listmodule
in   def type(self, text, delay=0):
        for c in text:
            key_map = self.US_KEYBOARD['Mapping'][c]
            key_map = key_map[0]
            mods = key_map['Modifiers']
            keys = key_map['Keys']
            mods = [KeyCodes[i] for i in mods]
            keys = [KeyCodes[i] for i in keys]
            
            if len(mods) == 1:
                mods = mods[0]
            else:
                mods = reduce(operator.and_, mods, 0)
            send_keystroke(self.dev, mods, keys[0])
            sleep(delay)
Press keys class: 
from zero_hid import Keyboard, KeyCodes
from zero_hid.hid.keyboard import send_keystroke, release_keys
from typing import Union
class stKeyboard(Keyboard):
    def __init__(self):
        super().__init__() 
    def press(self, mods: Union[int, list] , key_code: int=0, release=True)-> None:
        """
        Sends keystroked to PC. Including modifiers like CTRL
        """
        if type(mods) is list:
            if len(mods) == 1:
                mods = mods[0]
            else:
                allmods = 0
                for i in mods:
                    allmods |= i
                mods = allmods
        send_keystroke(self.dev, mods, key_code, release=release)
        
    def type_keys(self, text:str, delay=0)-> None:
        self.type(text, delay) 
   
if __name__ == "__main__":
    
    k = stKeyboard()
    k.type_keys("A")
    #send_keystroke(k.dev, KeyCodes.MOD_LEFT_SHIFT, KeyCodes.KEY_A)
    #k.press([KeyCodes.MOD_LEFT_CONTROL, KeyCodes.MOD_LEFT_ALT], KeyCodes.KEY_DELETE)



Examples:
(Left click) adb shell "echo -e -n '\x01\x0\x0\x0' > /dev/hidg1"
which is followed by adb shell "echo -e -n '\x0\x0\x0\x0' > /dev/hidg1"
This is because a click is a click and then release (left click then no click)
(Move Mouse) adb shell "echo -e -n '\x0\x7f\x7f\x0' > /dev/hidg1"
This moves the mouse 127 pixels to the right and 127 pixels down (7f is hex for 127)
(Mouse Move 2) adb shell "echo -e -n '\x0\x81\x81\x0' > /dev/hidg1"
This moves the mouse 127 pixels to the left and 127 pixels up (81 is hex for -127)
Do not enter x80 as I think this is effectively negative 0 or whatever. So to get other negative numbers you keep going e.g 82 is -126, 83 is -125 etc
Another note: you do not have to move in both the x and y direction at the same time you can just do one at time.
(Mouse Scroll Up) adb shell "echo -e -n '\x00\x0\x0\x01' > /dev/hidg1"
(Mouse Scroll Down) adb shell "echo -e -n '\x00\x0\x0\xff' > /dev/hidg1"

IMPORTANT: All of these values need to be input as hex using the format above so you can use a hex converter to get the values you need.











Definitions for me; 
-	Network ports 
o	SFTP stands for SSH File Transfer Protocol and it is a secure way to send and receive files over the network. As we mentioned, FTP can transfer files between server and client, but the FTP is not adequately designed for the security.

Keyboard.py is stored in /usr/local/lib/python3.7/dist-packages/zero_hid

def press_keys(self, keys: List[int], release):
        send_keystroke(self.dev, keys, [], release=release)

Python notes: 

Used in terminal: to see usb mouse codes needed to send commands 
sudo usbhid-dump --entity=all

is connected 
mouse move event 
keystroke 0 
handle exeptions if raspberry pi is not connected 
exception using super, try 
error handling 
functions returns bool; 
global function is connected; bool 


Traceback (most recent call last):
  File "/home/pi/Dieattach/DieAttachAutomation/DieAttach_Mia.py", line 69, in extract_and_save_errors
    mes_df['TXNTIMESTAMP'] = mes_df['TXNTIMESTAMP'].dt.round('10T')\

mes_df = pd.DataFrame()

class pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=None) 

  File "/usr/local/lib/python3.7/dist-packages/pandas/core/frame.py", line 3458, in __getitem__
    indexer = self.columns.get_loc(key)
  File "/usr/local/lib/python3.7/dist-packages/pandas/core/indexes/base.py", line 3363, in get_loc
    raise KeyError(key) from err
KeyError: 'TXNTIMESTAMP'
>>>

