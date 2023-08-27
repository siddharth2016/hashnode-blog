---
title: "Scala For Beginners - Crash Course - Part 3"
seoTitle: "Functional Programming in Scala, Scala For Beginners"
seoDescription: "Learn the basics of functional programming in scala in this beginners course. Learn higher-order, curries and anonymous functions in scala."
datePublished: Thu Sep 02 2021 09:56:18 GMT+0000 (Coordinated Universal Time)
cuid: ckt2r70n50e362is1cpm94ngx
slug: scala-for-beginners-crash-course-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1630575902470/ffLvQm1yq.png
tags: tutorial, programming-blogs, programming, scala, functional-programming

---

Welcome to the 3<sup>rd</sup> part of the scala beginners crash course, here we will go through the functional way of scala programming language and concepts like higher-order functions, curries and anonymous functions!

It will be a no-nonsense, to the point kind of article (like [part 1](scala-for-beginners-crash-course-part-1) and [part 2](scala-for-beginners-crash-course-part-2)) with all necessary links wherever needed.

Without further ado, let's get started.

---

### What Is Functional Programming?

The below is an excerpt from the **Functional Programming in Scala** book.

Functional programming (FP) is based on a simple premise with far-reaching implications: we construct our programs using only pure functions, in other words, functions that have no side effects. What are the side effects? A function has a side effect if it does something other than simply return a result, for example:

* Modifying a variable.
* Modifying a data structure in place.
* Setting a field on an object.
* Throwing an exception or halting with an error.
* Printing to the console or reading user input.
* Reading from or writing to a file.
* Drawing on the screen.

We discussed side-effects also in [part 1](scala-for-beginners-crash-course-part-1).

> Note: Functional programming is a restriction on how we write programs, but not on what programs we can express.

### Before We Start

Before we start coding out, first create a new object in the `crashcourse` package (please go through [part 1](scala-for-beginners-crash-course-part-1) for more information on creating packages and objects).

Let's name it `FunctionalProgramming` like below:

![functionalprog.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630575945646/OC1gaLVh2.png)

Now, we can start coding out examples on this scala application.

### Creating Functions In Scala

Before moving on to create functions in scala, please keep in mind that scala works on JVM and for JVM it needs classes/objects to work with, hence everything in scala will be an object, even the functions are objects.

> Note: Due to scala's syntactic sugar, we can still write functions in a more functional fashion.

Let's create a function in scala:

![function1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630575959941/pcZ5h_BWX.png)

Scala has a collection of functions namely `Function1` to `Function22`, which can be used out-of-the-box without any issues.

A function like `Function1[String, Int]` represents that it will take `String` as an input and evaluates to `Int` as an output. This function definition will be written in its `apply` method, as `Function1` is an object and we need to override its `apply` method to make it callable.

A simple syntactic sugar for a function like `Function2[Int, Int, Int]` would be `(Int, Int) => Int`, which is more functional while reading the code.

![function2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630575972248/l-jeLp22Hj.png)

We should also note that while working in IntelliJ, it tells us that the given `Function1[String, Int]` can be converted to its respective syntactic sugar, we can do so by hovering over the yellow line and simply clicking `Replace FunctionN[A1, A1, ..., AN, R] with (A1, A1, ..., AN) => R`.

![function1yellow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630575985895/CLRREEfBc.png)

Converted to syntactic sugar:

![function1syntax.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630575997793/1s4T2rLe-.png)

Important points to note:

* All scala functions are objects, that is, instances of `Function1`, `Function2` and so on.
* JVM was designed for object-oriented programming, but using it for scala function we need something like objects (like `Function1`) to instantiate them.
* Functions are traits with maximum parameters to be 22.

### Anonymous Functions

The anonymous function is something we saw in the previous example of `Function2[Int, Int, Int]` syntactic sugar.

So, the below expression:

![anonfunc.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576036088/edN80uOpx.png)

can be written as:

![anonfunc2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576046885/Pqc562saY.png)

or as:

![anonfunc3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576059186/SLHmwCK82r.png)

Anonymous functions are just another way of writing functions as supported by scala's compiler, behind the scenes everything is the same.

More ways in which we can write anonymous functions:

![anonfunc4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576079593/k_WNsN_7p.png)

> Note: An anonymous function is also known as a function literal. A function that does not contain a name is known as an anonymous function in general.

### Higher-Order Functions and Curries

Higher-order functions have at least one of the following properties:

1. Takes one or more functions as parameters.
2. Returns a function as a result.

In scala, a general higher-order function declaration can look like this:

![hof.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576093034/_ocWhLD0h.png)

These are called Higher-Order Functions, which essentially takes one or more functions as input and/or returns a function as output.

Moving on to curries, currying means transforming a function that takes multiple arguments into a chain of calls to functions, each of which takes one argument. Each function returns another function that takes the subsequent argument.

A simple curry can be like this:

![curry.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576108908/ZoNJdX16A.png)

Functions with multiple parameter list also act as curries:

![curry2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630576119542/o5ECg8pcP.png)

### Wrap Up

Well, that wraps up part 3 of this crash course.

I highly recommend you to go through the books below to get a better and deeper understanding of functional programming:

<a href="https://www.amazon.in/Functional-Thinking-Paradigm-Over-Syntax-ebook/dp/B00LEX6SP8?crid=2I35UGEUXLTHJ&dchild=1&keywords=functional+thinking&qid=1630574749&sprefix=functional+think%2Caps%2C317&sr=8-1&linkCode=li2&tag=chandrajidev-21&linkId=576c0c2c9e91856ea455b7baa167cbe1&language=en_IN&ref_=as_li_ss_il" target="_blank"><img border="0" src="//ws-in.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=B00LEX6SP8&Format=_SL160_&ID=AsinImage&MarketPlace=IN&ServiceVersion=20070822&WS=1&tag=chandrajidev-21&language=en_IN" ></a><img src="https://ir-in.amazon-adsystem.com/e/ir?t=chandrajidev-21&language=en_IN&l=li2&o=31&a=B00LEX6SP8" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="https://www.amazon.in/Grokking-Simplicity-software-functional-thinking-ebook/dp/B09781TWFL?dchild=1&keywords=functional+thinking&qid=1630574798&sr=8-2&linkCode=li2&tag=chandrajidev-21&linkId=54fce22f0619670582a2391a0daf4e0b&language=en_IN&ref_=as_li_ss_il" target="_blank"><img border="0" src="//ws-in.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=B09781TWFL&Format=_SL160_&ID=AsinImage&MarketPlace=IN&ServiceVersion=20070822&WS=1&tag=chandrajidev-21&language=en_IN" ></a><img src="https://ir-in.amazon-adsystem.com/e/ir?t=chandrajidev-21&language=en_IN&l=li2&o=31&a=B09781TWFL" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="https://www.amazon.in/Functional-Programming-Scala-Paul-Chiusano/dp/1617290653?crid=24RA56XW8MZX1&dchild=1&keywords=functional+programming+in+scala&qid=1630574828&sprefix=functional+prog%2Caps%2C322&sr=8-1&linkCode=li2&tag=chandrajidev-21&linkId=8928ebdaa8126f751f76a0612beeac4f&language=en_IN&ref_=as_li_ss_il" target="_blank"><img border="0" src="//ws-in.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=1617290653&Format=_SL160_&ID=AsinImage&MarketPlace=IN&ServiceVersion=20070822&WS=1&tag=chandrajidev-21&language=en_IN" ></a><img src="https://ir-in.amazon-adsystem.com/e/ir?t=chandrajidev-21&language=en_IN&l=li2&o=31&a=1617290653" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

In the next part, we will discuss some topics specific to scala, like options, handling errors in a unique style and pattern matching (the most awesome thing in scala).

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏
