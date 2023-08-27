---
title: "Scala For Beginners - Crash Course - Part 2"
seoTitle: "Scala Tutorial For Beginners - Crash Course"
seoDescription: "Scala tutorial for beginners, a crash course. Object-oriented programming using scala, learn about objects, case class, abstract class and traits."
datePublished: Tue Aug 31 2021 17:04:16 GMT+0000 (Coordinated Universal Time)
cuid: ckt0blohg074v54s16ko5e1so
slug: scala-for-beginners-crash-course-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1630427731200/vmXYNpyiq.png
tags: tutorial, programming-blogs, programming, scala, functional-programming

---

Welcome to the 2<sup>nd</sup> part of scala beginners crash course, here we will go through the object-oriented way of scala programming language and concepts like anonymous class, case classes and traits!

It will be a no-nonsense, to the point kind of article (like [part 1](scala-for-beginners-crash-course-part-1)) with all necessary links wherever needed.

Without further ado, let's get started.

---

### Before We Start

Before we start coding out, first create a new object in `crashcourse` package (please go through [part 1](scala-for-beginners-crash-course-part-1) for more information on creating packages and objects).

Let's name it `ClassAndObject` like below:

![classandobject.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428192859/oxQvO6f-0.png)

Now, we can start coding out examples on this scala application.

---

### Classes And Objects

In scala, to define a class we use the `class` keyword:

![classkeyword.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428208513/-YBKewovA.png)

We can directly use the `Student` class later in the program. That's it! that's how we can create a class in scala.

It is different from writing `object Student` as it is not instantiated right away, we have just defined it and are not using it anywhere. To instantiate a class we can use the `new` keyword.

![newkeyword.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428230819/rKcOjejYv.png)

A class can have parameters, like this:

![classargs.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428242656/aO-thvn6J.png)

> Note: Class parameters are not class fields, which means we can not use these parameters with instantiated objects.

To make class parameters as class fields, we have to use the `val` keyword along with the name of the parameter, like this:

![valclassargs.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428319579/tsxrdzViI.png)

We can use class parameters within the class code block by using the `this` keyword if value name conflict occurs, like below:

![usingthis.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428339539/wdMAz_16a.png)

If value name conflict does not occur, then the class method by default (implicitly) uses the `this` operator on class parameters values.

Some other important concepts:

* Overloading occurs with only different signature methods. More on overloading in scala [here](https://www.geeksforgeeks.org/method-overloading-in-scala/).
* Auxiliary constructor are generally used for default parameters. More on auxiliary constructor [here](https://www.geeksforgeeks.org/scala-auxiliary-constructor/).
* Instances are fixed, whenever we want to do something with the given class, say creating/updating something, then we would need to instantiate a new class, it is the clause of immutability, useful in functional programming.

Conceptually, scala does not provide class level functionality, like a static class. However, scala provides something called an `object`, using which we can obtain class level functionalities.

Scala objects are singleton instances by definition. We can create an object like the below code:

![object.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428399034/tswQeZPm90.png)

We can create an object with the same name as that of a class in the same scope, creating such an object/class is called companion object/class, known as companions.

Companions can be used to make a factory method in objects, that can help instantiate a class in a certain way. Using companions does not require using the `new` keyword to instantiate a scala class, we can define a method named `apply` within the object to handle instantiation.

We can create a companion like below:

![companion.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428637173/s90e0_FRe.png)

Well, that's about it on classes and objects in scala. You can check out official docs on scala classes [here](https://docs.scala-lang.org/tour/classes.html) and on objects [here](https://docs.scala-lang.org/tour/singleton-objects.html).

### Anonymous And Case Classes

To create an anonymous class we can directly define the class like this:

![anonclass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428653602/AuZMDeqQt.png)

Things to remember when creating an anonymous class:

* Pass proper parameters whenever required.
* Anonymous class declaration works for abstract as well as for non-abstract classes. It works for traits as well.
> Note: We will discuss abstract classes and traits in the next section.
* Useful for on-spot declaration in some scenarios.

Using the `case` keyword in front of the `class` keyword will make it a case class, like this:

![caseclass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428673599/WBzmt4Qjo.png)

Case classes promote class parameters to fields, it has a predefined `toString` method that evaluates to a representation that is understandable.

Equality and hashcodes are implemented out-of-the-box with a handy `copy` method to copy instances. Case classes come with their companion objects predefined.

Things to remember when creating a case class:

* Case class is a quick lightweight data structure with little boilerplate.
* Case classes are serializable and used with the Akka framework.
* Case classes have extractor patterns that can be used in pattern matching.
* Case objects are the same as case classes but don't get companion objects as they themselves are objects.

Well, that's about it on anonymous class and case class in scala.

### Inheritance, Abstract Class And Traits

Scala offers single level inheritance. Inheriting a class inherits public methods and protected methods can be used within the child class.

Inheritance example:

![inheritance.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428695980/LGFCROTuq.png)

Important notes on inheritance overriding:

* To override methods, use the `override` keyword. Override works for `val`, `var`, `def` or anything within in the class.
* To prevent override, we have to use the `final` keyword.
* Put a `final` keyword before `class` to altogether prevent the inheritance of a class.
* Use the `sealed` keyword to restrict inheritance in different scopes of the program.

Moving on to abstract classes in scala, we have to use the `abstract` keyword to make an abstract class and an abstract class cannot be instantiated, however, we can create an anonymous class using the `new` keyword and defining all the methods within that anonymous code block.

![abstractclass.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428722924/REIHImy5p.png)

Traits are similar to interfaces in java. They are also used to declare undefined or unimplemented methods. We have to use the `trait` keyword to define traits in scala.

![trait.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630428738822/-Gt2CDPkh.png)

Important points to note for abstract classes and traits in scala:

* Abstract class can have both abstract and non-abstract methods. It is the same for traits.
* Traits does not have constructor parameters.
* Classes can inherit multiple traits, but not multiple classes.
* Traits are used to define the behaviour of a class.
* Abstract class is the type of thing itself.

> Note: If you see `???` in abstract/trait methods, it means that method is not implemented and evaluates to `Nothing`.

Well, that's about it on inheritance, abstract class and traits in scala.

### External Links

Below are some of the external links you can go through to get a more in-depth understanding of object-oriented programming in scala.

* [Object Oriented Programming in Scala](https://www.baeldung.com/scala/oop-intro#:~:text=Scala%20is%20a%20hybrid%20between,encapsulation%2C%20inheritance%2C%20and%20polymorphism)
* [Scala Exercises](https://www.scala-exercises.org/scala_tutorial/object_oriented_programming)

### Wrap Up

Well, that wraps up part 2 of this crash course.

In the next part, we will discuss functions, HOFs, curries and much more related to functional programming in scala.

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏