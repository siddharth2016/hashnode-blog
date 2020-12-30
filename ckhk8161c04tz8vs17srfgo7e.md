## Delegating OOPs

**Delegation**

One of the pillars of OOP, it help objects to interact with each other. But, there is a dichotomy in delegation, it can be achieved following 2 different strategies.

One is Composition and other is Inheritance. But, why we tend to use inheritance more often than composition in our regular design solutions ?

Inheritance can result in clash between same names with different meaning, if not dealt with properly or we may need to remove some methods from parent class which will result in unnecessary polluting of child class.

Composition can have too many methods from container class to be contained or we may be composing instances, but creating many class methods so that the container can access them.

There may be pitfalls to both strategies, but we should look at how we can reduce maintenance hours for a particular project.

To get a scalable model, we can look at following points before designing our project:

⚡ Visibility of class methods</br>
⚡ Control over classes</br>
⚡ Relationship between classes</br>
⚡ Entities in classes

Your thoughts on Inheritance and Composition ? What are the factors you take into account before proceeding ? Which one do you prefer or use regularly ?

Just starting you Open Source Journey ? Don't forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Till next time !

Namaste 🙏