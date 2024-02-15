# Object Oriented Programming in Ruby

## Inheritance
Inheritance is one of the solid fundamental characteristics of object-oriented programming. sometimes we might need certain features of a class to be replicated into another class. Instead of creating that attribute again, we can inherit the attribute from the other class. The class that is inherited from is called the base class and the class that is inheriting from the base class is called the derived class. Syntax :
```
class base
# internal data and methods
end
class derived < base
# internal data and methods
end
```
We use the < symbol for inheriting. So all the data and methods in the base class is passed on to the derived class. however this is only one way. That is to say that the information from the derived class is not inherited back to the base class this is better understood with an example so consider our primary example Vehicle Let us take class Vehicle as the base class and make two derived classes – car and bus. Example:
``` 
# Ruby program of Inheritance 
class Vehicle 
    def initialize(vehicle_name, vehicle_color) 
        @vehicle_name = vehicle_name 
        @vehicle_color = vehicle_color 
    end
    def description 
        puts 'This is a vehicle'
    end
end
  
class Car < Vehicle 
    def description 
        puts 'This is a car'
    end
  
end 
  
class Bus < Vehicle 
    def display_this 
        puts 'This is a bus'
    end
  
end  
  
# Creating objects 
object1 = Car.new('Nissan', 'red') 
object2 = Bus.new('Volvo', 'white') 
  
object1.description 
object2.description 
object2.display_this
```
## Output:
```
This is a car
This is a vehicle
This is a bus
```
In the above example, we have one base class – Vehicle and two derived classes – Car and Bus. Car and Bus inherit the attributes and methods of the class Vehicle consider the method ‘Description’ which is common to both Vehicle and Car, however their functionality is different. So when Car inherits the methods from Vehicle it has two methods called Description however these two methods are not the same, one is Car.Description while the other is Vehicle.Description. However for an object of type Car, if we call the Description method then the Car.Description method executes Hence we can say that Car.Description overrides Vehicle.Description. In the class Bus, we have only one Description method which we inherited from the Vehicle class so there is no overriding in this scenario. Derived classes can have their own data and variables and one such example is the method ‘display_this’. Remember, inheritance is not vice versa. So if we had an object of type Vehicle i.e object3 = Vehicle.new() then we cannot write object3.display_this inheritance is only one way. Now consider the case of the two Description methods, Car.description and Vehicle.Description. we say that for an object of type Car, the Car.Description method will execute but what if we wanted the other method-Vehicle.Description to execute. to do this we use the keyword super.
``` 
# Ruby program of inheritance 
class Vehicle 
    def initialize(vehicle_name, vehicle_color) 
        @vehicle_name = vehicle_name 
        @vehicle_color = vehicle_color 
    end
    def description 
        puts 'This is a vehicle'
    end
end
   
# Using inheritance 
class Car < Vehicle 
    def description 
        puts 'This is a car'
            super
    end
   
end
   
# Using inheritance 
class Bus < Vehicle 
    def display_this 
        puts 'This is a bus'
    end
   
end
  
# creating object 
object1 = Car.new('Nissan', 'red') 
object2 = Bus.new('Volvo', 'white') 
   
# Calling object 
object1.description 
object2.description 
object2.display_this
```
## Output:
```
This is a car
This is a vehicle
This is a vehicle
This is a bus
```
The difference in this example when compared to the previous one is that we use super in the Car.Description method. when we use super, the control goes back to the base class and then executes the base class method i.e Vehicle.Description instead of Car.Description. This is how we can override our derived class method to use our base class method instead.
Derived class attributes
Now suppose we want our derived class to have attributes of their own. We would still have to pass the variables for the base class as well as the derived class. then we use super to call the constructor of the base class and then we initialize the derived class attributes. Example :
```
# Ruby program of showing Derived class attributes 
class Vehicle 
    attr_accessor :vehicle_name
    attr_accessor :vehicle_color
    def initialize(vehicle_name, vehicle_color) 
        @vehicle_name = vehicle_name 
        @vehicle_color = vehicle_color 
    end
end
   
class Car < Vehicle 
     attr_accessor :car_model
  def initialize(vehicle_name, vehicle_color, car_model) 
  
        # Using super keyword 
        super(vehicle_name, vehicle_color) 
        @car_model = car_model 
    end
end
   
# creating object  
object = Car.new('Nissan', 'white', 'xyz') 
  
# calling object 
puts object.vehicle_name 
puts object.vehicle_color 
puts object.car_model
```
## Output:
```
Nissan
white
xyz
```
We introduced an attribute car_model in the derived class Car while creating the object we passed values for the base as well as derived class (Car) as the derived class has the attributes of the base class (Vehicle) as well. From the below statement, object = Car.new('Nissan', 'white', 'xyz') The control goes to the initialize method of Car, from there we use super to pass the Vehicle attributes to the initialize method of Vehicle i.e. super(vehicle_name, vehicle_color). The control then passed into the initialize method of vehicle and then returns to the place it was called. then the derived attributes are initialized i.e. @car_model = car_model Multiple Inheritance is not supported in Ruby since it often gets messy and very complicated. by Multiple inheritance, we mean that one class derives from many base classes. this is supported by languages such as C++ but it is often seen as an over complication. we do have a work-around for this however. Mixins usually help curb this deficiency.
Public and Private
By default all our attributes and methods are public if we describe all our methods as public, it allows our methods to be accessed outside the class we use private when we have methods that we do not want to give access outside the class only the object is given access to use the methods internally from other public methods.
```
# Ruby program of Public and Private method 
class Vehicle 
    def initialize(vehicle_name, vehicle_color) 
        @vehicle_name = vehicle_name 
        @vehicle_color = vehicle_color 
    end
    
  # Using public method 
    public 
    def display 
        greeting 
        puts 'Your car details are: '
        puts @vehicle_name
        puts @vehicle_color
    end
    
   # Using Private method 
    private 
    def greeting 
        puts 'Hello, user'
    end
end
  
# Creating object 
object = Vehicle.new('Nissan', 'white') 
  
# Calling object 
object.display
```
## Output:
```
Hello, user
Your car details are: 
Nissan
white
```
By default all our methods are public so if we want one of our methods to be private then we should mention it with the keyword private Likewise we can mention a method as public using the keyword as public If we use one of the keywords private or public, then until we mention them again, it will remain in public or private till the end of the class definition.
## Modules
Modules are like blocks of code that contains methods and even constants while coding, we might have a lot of tools we wish to use however this might clutter up the whole program. So we put these in modules and only use the modules when we wish to use the methods and constants inside they are similar to classes with the exception that we cannot create objects from modules. Module syntax :
```
module ModuleName
    #methods and constants
end
```
Modules are written with CapitalizedCamelCase, which is just capitalizing the first letter of every word in the module name with no spaces. Module Example
```
module ConstantsAndMethods
    CONST_ONE = 10
    CONST_TWO = 20
    
    def method1
         puts ‘This belongs to ConstantsAndMethods’
    end
end
```
We created a module called ConstantsAndMethods we have two constants. Constants should be written in caps and underscores between words and we have a method called method1. to use the data and methods within a module we use the keyword require. and then we can use the scope resolution operator to access the constants and methods.
```
require ‘ConstantsAndMethods’

puts ConstantsAndMethods::CONST_ONE
```
Continuing with our introduction to modules, we’ll now learn about mixins.
## Mixins
Mixins are our cross-over between modules and classes and is how we curb over the issue that Ruby does not allow multiple inheritance. we can have our modules constants and methods included in our classes with the keyword include. Example :
``` 
# Ruby program of using mixins 
module Greeting 
    def display 
        puts 'Hello'
    end
end
    
class Greetuser 
    include Greeting 
      attr_reader :name
    def initialize(name) 
        @name = name 
    end
end
    
# Creating object 
object = Greetuser.new('User_name') 
  
# Calling object 
object.display 
puts object.name 
```
## Output:
```
Hello
User_name
```
We have a module Greeting and a class Greetuser. as we can see in this line object.display we are using the object of class Greetuser to use the module method display. We can do this because of the include we did within the class i.e. include Greeting.
## Extend Mixins
We can use extend in place of instead the difference is that extend incorporates the module at the class level So the class itself can use the module methods as opposed to objects. Example:
``` 
# Ruby program of extending mixins 
module Greeting 
    def display 
        puts 'Hello'
    end
end
  
# Using extend keyword   
class Greetuser 
    extend Greeting 
  attr_reader :name
    def initialize(name) 
        @name = name 
    end
end
    
# Creating object 
object = Greetuser.new('User_name') 
  
# Calling object 
Greetuser.display 
puts object.name 
```
## Output:
```
Hello
User_name
```
In the previous example we replaced include with extend. So now it’s actually part of the class. hence we can use the method of the module using the class name Greetuser.display
