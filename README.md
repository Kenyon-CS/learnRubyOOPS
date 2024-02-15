# Learn Ruby OOPS
Activity to learn Ruby OOPS

## Object-Oriented Programming in Ruby
When we say object-oriented programming, we mean that our code is centered on objects. Objects are real-life instances that are classified into various types. Let’s take an example to understand this better. If we consider a rose as an object, then the class of the rose will be flower. A class is like the blue-print of an object and describes the attributes and behavior of an object. the attributes of a flower could be the color, fragrance or even whether it has thorns. these features are part of the class and each instance of the class i.e. each object of the class would share these attributes. though the value of the attribute may vary among different objects. take for an example – a lily. So if the color of the petals of the rose object is red then for the lily it could be white. this is the basis of object oriented programming where we can take real life situations and make different instances from it. Now let’s see on how we can define a class in Ruby Class’s Syntax:
```
class classname
end
```
## Implementing OOP concepts with Ruby
Ruby supports the OOP paradigm by allowing the creation of classes and its objects. Like we said before, objects are the instances of a class and a class is like the blueprints for the object. A class lists out the attributes and defines the behavior for the object while the object is the real world representation. A class has two parts to it – data and methods So now that we have a class Language Let’s define the attributes as 1) LanguageName 2) TopicName Now we have our data but we need a way to access them. This is where our methods come in. class Methods are methods defined in the class that are used to access the various data in our class. For Implementing into code, we use a constructor, that takes in values of the attributes and assigns them to the space stored for the particular object.
## Constructor’s Syntax :
```
def initialize(x, y)
    @x = x
    @y = y
end
```
The initialize function is defined within the class and its syntax is just like an ordinary function. It can take any amount of arguments. The @ symbol represents the object’s actual attributes.
## Examples:
```
class Language
    def initialize(language_name, topic_name)
        @language_name = language_name
        @topic_name = topic_name
    end
end
```
To create an instance of a class, we use a familiar function, which we might have used earlier for making hashes or arrays. We use the new function. Syntax :
```
object_name  = Class_name.new()
```
If we have any parameters, it is usually passed in the parenthesis of new, just like in ordinary methods. Examples:
``` 
class Language 
    def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
    end
end
  
object1 = Language.new('Ruby','method') 
```
So we have an object named as object1. We use the Language.new() to create a new instance, this calls the initialize function. So the object1.language_name is Ruby. And object1.topic_name is method Let’s create a second object as well Examples:
```
class Language 
    def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
    end
end

object1 = Language.new('Ruby','method') 
object2 = Language.new('Scala','string') 
```
So the object2.language_name is Scala And object2.topic_name is string.
## Access Methods
Now that we have defined our class and created objects, we need to be able to change or view the attributes of our object. This is where the second part of our class comes in – Methods. Class methods are much like our regular methods defined within a class. We use methods to change the value of some of our attributes and to view the values as well. To call the method for a particular method we have to mention the object_name.method_name. This is better understood with an example. Examples:
```
# Ruby program to understand the concept of  
# Access Method 
class Language 
    def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
    end
     
    # Defining Methods 
    def return_name 
        return @language_name
    end
    def return_topic 
        return @topic_name
    end
end
  
# Creating objects 
object1 = Language.new('Ruby','method') 
object2 = Language.new('Scala','string') 
puts 'Language name for object1: ' + object1.return_name 
puts 'Topic Name for object1: ' + object1.return_topic 
  
puts 'Language name for object2: ' + object2.return_name 
puts 'Topic Name for object2: ' + object2.return_topic 
```
## Output :
```
Language name for object1: Ruby
Topic Name for object1: method
Language name for object2: Scala
Topic Name for object2: string
```
We have created two objects in the above example. object1.return_name calls the method return_name for object1, this returns the result ‘Ruby’. If we call object2.return_topic, it calls the method return_topic for object2 This returns the result ‘method’ to the puts statement. Normally in ruby, methods return the last computer result of the method so we do not have to explicitly write return. So instead of writing below code
```
def return_name
    return @vehicle_name
end
```
We can write code as below.
```
def return_name
    @vehicle_name
end
```
## Variable Scope
When we say variable scope we mean under which areas a certain variable can be used. The scope can be global or local When we say global we mean that throughout our code, we can use the global variable anywhere To define global variables we use the ‘$’ symbol. Examples:
``` 
# Ruby program to understand the concept of  
# Variable Scope 
class Language 
  
    # Creating global variable 
    $reader = 'ABCD'
    def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
    end
     
    # Defining Methods 
    def return_name 
        return @language_name
    end
    def return_topic 
        return @topic_name
    end
end
  
# Creating objects 
object1 = Language.new('Ruby','method') 
object2 = Language.new('Scala','string') 
puts 'Language name for object1: ' + object1.return_name 
puts 'Topic Name for object1: ' + object1.return_topic 
  
puts 'Language name for object2: ' + object2.return_name 
puts 'Topic Name for object2: ' + object2.return_topic 
  
# Printing global variable 
puts 'The reader is '+ $reader
```
## Output :
```
Language name for object1: Ruby
Topic Name for object1: method
Language name for object2: Scala
Topic Name for object2: string
The reader is ABCD
```
In the above example, we declared a global variable Since this variable is global we can use it anywhere in the program. $reader responsible for ABCD. Let’s we tried this with one of the instance variables object1.language_name. This would have given an error because this variable is of local scope i.e. within the class only. so we need to use access methods or use attr_reader which explained below.
## Modifying attributes
Let’s understand it with example. Examples:
``` 
# Ruby program to understand the concept of  
# Modifying attributes 
class Language 
  def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
    end
  
  # Defining Method 
    def return_name 
        return @language_name
    end
    def return_topic 
        return @topic_name
    end
    def modify_topic(value) 
        @topic_name = value 
    end
end
  
# Creating object 
object = Language.new('Ruby','method')  
puts 'Language name for object: '+object.return_name 
puts 'Topic name is '+object.return_topic 
  
# Modifying attribute 
object.modify_topic('string') 
puts 'New Topic Name is '+object.return_topic 
```
## Output :
```
Language name for object: Ruby
Topic name is method
New Topic Name is string
```
In the above example, we see a new method modify_topic. This method is used to change the value of the attribute topic_name. Since the attributes cannot be accessed directly outside the function, we resort to using methods to access them. As we can see in the example, we pass the new topic as an argument to the modify_topic method. Within the method, the object’s topic attribute is reset to the new topic.
## Class Variables
Class variables are different from instance variables in the sense that they belong to the class and not the object. For instance variables like language_name and topic_name, we have one copy for each object but for class variables, one copy is shared among all the objects typically, the variable belongs to the class, not the instances of the class but it can still be accessed by the instances of the class. Class variables are usually identified using ‘@@’. The syntax is @@class_variable = 0. It can have a default value and that could be anything ranging from a string to an integer. Example :
``` 
# Ruby program to understand the concept of  
# Class Variables 
class Language 
    $reader = 'ABCD'
  
    # Creating class variable 
    @@count = 0
    def initialize(language_name, topic_name) 
        @language_name = language_name 
        @topic_name = topic_name 
        @@count  += 1
    end
  
    # Defining method 
    def return_name 
        @language_name
    end
    def return_topic 
        @topic_name
    end
      
    # Returning class variable 
    def  return_count 
        @@count
    end
end
  
# Creating object 
object1 = Language.new('Ruby', 'method')  
object2 = Language.new('Scala', 'string') 
puts 'Language name for object1: '+object1.return_name 
puts 'Topic name for object1: '+object1.return_topic 
  
puts 'Language name for object2: '+object2.return_name 
puts 'Topic name for object2: '+object2.return_topic 
  
puts 'The reader is '+ $reader 
  
puts 'The number of objects created is ' + object1.return_count.to_s 
puts 'The number of objects created is ' + object2.return_count.to_s 
```
Output :
```
Language name for object1: Ruby
Topic name for object1: method
Language name for object2: Scala
Topic name for object2: string
The reader is ABCD
The number of objects created is 2
The number of objects created is 2
```
In the above example, we have used a class variable count to keep track of the number of objects being created this is one of the most common usages of class variables in the above example, we initialize count with to 0. We also add a function to the return the value as and when called. every time an object is being created, the initialize method is called each time the initialize function is called, count gets incremented by one i.e. @@count += 1 regardless of whether we call the return_count method using object1 or object2, it prints out the same result. like instance variables, it’s scope is only within the class and cannot be accessed directly outside the class we use .to_s to convert the number into a string. Instead of access methods In the previous examples, we’ve introduced methods to return the attributes. We have an easier work-around for that. This is where attr_reader, attr_writer, attr_accessor comes into play consider the next slice of code. Example :
``` 
# Ruby program to understand the concept of  
# Modifying attributes 
class Language 
        attr_reader :language_name
        attr_writer :topic_name
        attr_reader :topic_name
  
    def initialize(language_name, topic_name) 
            @language_name = language_name 
            @topic_name = topic_name 
    end
      
end
      
object = Language.new('Ruby', 'method')  
puts 'The name of the language is ' + object.language_name 
puts 'The topic of the language is ' + object.topic_name 
  
# changing the topic name 
object.topic_name = 'array'
puts 'The new topic of the language is ' + object.topic_name 
```
Output :
```
The name of the language is Ruby
The topic of the language is method
The new topic of the language is array
```
Whether you're preparing for your first job interview or aiming to upskill in this ever-evolving tech landscape, GeeksforGeeks Courses are your key to success. We provide top-quality content at affordable prices, all geared towards accelerating your growth in a time-bound manner. Join the millions we've already empowered, and we're here to do the same for you. Don't miss out - check it out now!
