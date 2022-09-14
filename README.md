# Python
Python Notes and Examples

### Definitions 
- Module; a program that can be imported to other programs, so that the fucntions and operations defined in the module can be reused in another program 

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
Syntax: super()

Return : Return a proxy object which represents the parent’s class.


