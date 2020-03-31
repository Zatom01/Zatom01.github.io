---
layout: post
title:      "Understanding Instance methods and Class methods"
date:       2020-03-31 00:45:00 -0400
permalink:  understanding_instance_methods_and_class_methods
---



Methods that work only on the instance or objects that we create are called instance methods whereas class methods are defined on the class and are not tied to an instance.
Let’s jump to our example below:

1.  Class Dog
1.  
1.      def bark
1.        puts “Woof! Woof !”
1.      end  
1.  end

Which method do you think this is? This is an example of an instance method. To make our dog “Fido” bark, we have to first create an object of Dog class by Fido = Dog .new. Then we can call the method by Fido.bark instead of Dog.bark where the latter is wrong.
So, what does a Class method look like? Let’s take a look at the example below:
 
1.  Class Dog
1.      def self.bark
1.          puts “Woof! Woof!”
1.      end
1.  end

Now, this method can be called directly on the Class itself by Dog.bark which will print “Woof! Woof!. Here, self is referring to the class itself which is “Dog”. In this example, other class methods could be “self.all” which would track all the Dog objects we create, “self.clear” which would reset our class variable responsible for storing all of our Dog objects, etc.

In conclusion, we can tell the difference between instance and class methods by looking at how they are declared. Class methods will have an additional syntax of ‘self ‘ in front of the method name. Class methods can be called just on the Class itself whereas, for the Instance method to work, we have to first create an instance of the class and then call our method on that instance only.
