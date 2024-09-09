# OOPS-in-python
classes and obejcts - [here](OOPS/classes and objects.ipynb](https://github.com/harish-AK/OOPS-in-python/blob/main/OOPS/classes%20and%20objects.ipynb)
exercises - [here](https://github.com/harish-AK/OOPS-in-python/blob/main/OOPS/classes%20and%20objects.ipynb)

Cannot access a variable that defined in one method in another method without using self (class instance).

## Super() 
super() function used to access parent class values in child class.

# Classes and objects

class is an user defined data structure which have its own methods and functions which can be accessed by creating an object for that class. Class attributes are always public.

If a class is created means every methods should have the parameter self which is used to access class attributes. to access class elements we need to pass self.attribute in the method.

`class dog:
``	a = "hello"
``	def display(self):
``		print(self.a)
`d = dog()
`d.display()
**output** is "hello"

in python class methods will form like **func(myclass,arg1)** even though the method has only one parameter like **func(arg1)**.

`class dog:
``	def __ init __ (self,name):
``		self.name = name
``	def display(self):
``		 print(self.name)
`d = dog()
`d.display("ak")

output is "ak".

# Constructor

Constructor usually used to initialize attributes to class members (class methods). 
**__ init __ ()** - init method is called constructor. 

**Types of constructor:**

Default constructor - only reference object self will be initialized.
Parameterized constructor - more than one argument will be initialized.

# Destructor

Destructor are called when objects gets destroyed. __ del __ () is the destructor. called when all instance of classes are deleted. 

let's take an class classed dog
d = dog()
d.method()
del d - object is deleted now __ del __ () - method will be called and display the message within it.

if not an object is deleted means destructor method will be called after the end of program.
# Encapsulation

Encapsulation prevents the unwanted usage of class attributes. using encapsulation class attributes can be declared private and protected, protected attribute means that attribute can be accessed within and its sub classes only. private attribute means attribute can be only accessed within the class.

Even if we change the value of protected class member in child class wont change the value in parent class.

class parent:
	def __ init __ (self):
		self. _ a = 10

class derived(parent):
	parent(). __ init __ (self)
	print(self. _ a)
	self. _ a = 20
	print(self. _ a)
	
p = parent()
d = derived()

d. _ a # output is 10
d. _ a # output is 20, after update the value. 

p. _ a # output is 10, parent class attribute wont change even if it updated in child class.

protected member: _ A (single underscore)
private member:  __ A (double underscore)

private and protected members are called access specifiers. 
# Abstraction

Basic definition is showing essential details and hiding the implementation is knows as abstraction.
Abstract class considered as blue print for other classes used to ensure that certain methods are used by subclasses. By default python doesn't support abstraction. ABC (Abstract base class) module will be used for abstraction, abstract method will be used as decorator. 
**@abstractmethod**.

from abc import ABC, abstractmethod
class Animal(ABC):
	@abstractmethod
	def  move(self):
		pass
class Dog(Animal):
	def move(self):
		return "Hello world"
can't access method move in Animal class because it defined as @abstractmethod.



# Inheritance

Members of one class can be accessed to another class via inheritance. 
A class will be created and attributes will be assigned (this class is called parent class).
Another class will be created and the parent class will be passed as parameter in this class.
This class is called child class.

Class parent:
		 constructor:
		 method creation

Class child(parent):
		 constructor:
		 super(). __ init __ (parent class variables) # no need to pass self while calling super class
		 method creation
### Types:

Unlike java python can do multiple inheritance.

Single inheritance - A child class inherits from only one parent class.

Multiple inheritance - A child class inherits from multiple parent class.
	 class p1:
     class p2:
     class child(p1,p2):

Multilevel inheritance - Parent class will be inherited by child class then child class will be inherited by another class.

	 class p1:
     class p2(p1):
     class child(p2):

Hierarchical inheritance - a class will be inherited by more than one child class.
Hybrid inheritance - involves more than one form of inheritance.

In heritance a parent attribute can be made to private by adding double underscore( _ ).
class A:
    def __ init __ (self):
         self.a = 10
         self. __ b = 20
class B(A):
	def  __ init __ (self):
		super() . __ init __ (self)
bb = B()
b.a
bb. __ b	
# Polymorphism

Same function being used for different use cases, differ by number of arguments and data types.
one class method name can be used for another class without inherit anything, (only the name of method). but we need to create separate objects for each class in order to access the methods. By inheriting we can modify the parent class method in child class.

class Animal:
    def speak(self):
        raise NotImplementedError("Subclass must implement this method")

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"
d = [Dog(), Cat()]
for i in d:
	print(i.speak())

Output - Woof !
		Meow!

# Method overloading

Two or more methods having same name but different parameters and data types. Only the latest function can be accessed (means if a method is modified the modified version can be accessed not the previous one).

To overcome method overloading declare parameters to none.
Efficient one - using multipledispatch

from multipledispatch import dispatch
@dispatch(int, int)
def product(a,b):
	print(a+b)

@dispatch(int, int, int)
def product(a, b, c):
	print(a+b+c)

# Method overriding

When a child class overrides a method of parent class is known as method overriding.
class parent:
	def method(self):
		return "parent"
class child(parent):
	def method(self):
		return "Child"
c = child()
c.method()
output - Child


