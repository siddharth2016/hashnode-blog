## Scala Vs Python Syntax Cheat Sheet

There are about 8 million Python developers around the world and it's also the top programming language people want to learn, but why is that? Why not any other language but Python? Let me tell you, Python offers a lean learning curve, with just 2-3 days of hands-on Python anyone can start developing applications (they might not be technically sound software initially), it's syntax is one of the easiest to learn due to its plain english like code, it offers flexibility from both domains either object-oriented or functional programming (not so much FP, but it has its benefits) and it is used in almost every field of software engineering.

The only drawback people face when working with Python is related to its speed of executing programs. But is there any other programming language as easy to understand and to get started to work with? Yep, there is, Scala comes to the rescue!

Python faces speed issues mainly due to its interpreted nature, whereas Scala is a compiled language that offers dynamic typing as well (close to 90%), many new features in Python like pattern matching are already present in Scala since the beginning, there are awesome syntactic sugars in Scala that allows us to write even less code when compared to Python and also Scala being a functional programming language does not shy away from object-oriented programming as it is run over JVM.

When it comes to the syntax of these programming languages, there are a lot of similar patterns and some differences as well, but overall they both offer a lean learning curve with endless opportunities in the software engineering world.

So, let's discuss those similarities and differences in the form of a cheat sheet, which not only helps in refreshing some concepts from Python/Scala but also acts as a guide to learn Python or Scala for someone coming from the Scala or Python background respectively.

This will be a to-the-point kind of article, with little to no explanation but with necessary links wherever needed.

So, let's get started!

---

### How To Import?

In Python importing a library can look like this:

```python
import math.*

# OR

import math.pow

# OR

from math import pow, sqrt

# OR

from math import sqrt as squareRoot
```

In Scala importing a library can look like this:

```java
import scala.math._

// OR

import scala.math.BigInt

// OR

import scala.math.{BigInt, BigDecimal}

// OR

import scala.math.{BigInt => BInt}
```

### How To Declare Variables?

Python offers dynamic typing so you don't need to declare variables beforehand like in C/C++, but you can just type out the variables and use them:

```python
some_variable = 10
```

Scala also offers dynamic typing to some extent and infer that type during compile time:

```java
val some_variable = 10  // infers it as Int type
```

### How To Define Conditionals?

In Python and Scala defining conditionals are more or less similar:

```python
v = 5
if v%2==1:
    print("Odd")
elif v==0:
    print("Zero")
else:
    print("Even")
```

In Scala:

```java
val v = 5
if (v%2==1) println("Odd")
else if (v==0) println("Zero")
else println("Even")
```

The important thing to note in conditionals is that in Python conditionals are referred to as statements whereas in Scala these are expressions that evaluates to something or nothing.

### How To Define Loops?

In Python a simple for-loop would look like this:

```python
for i in range(10):
    # do something here
```

The same for-loop in Scala would look like this:

```java
for {
    i <- 0 until 10
}   {
    // do something here
}
```

The difference in their respective working behind the scenes, in Scala, is the use of conjunction of `map` and `flatMap` methods whereas in Python it is simple iteration.

There is a `while` loop in Scala, but let's not discuss that, while coding in Scala it is not encouraged to use `while` loops.

[Why are while loops not recommended in Scala?](https://stackoverflow.com/questions/49552915/why-are-while-loops-not-recommended-in-scala#:~:text=The%20scala%20style%20checker%20says,%2Ddev.html%23org_scalastyle_scalariform_WhileChecker.)

### How To Write Methods?

In Python, we can simply use the `def` keyword to define functions, which are similar to methods in Scala.

```python
def some_method():
    # do something here
```

In Scala we can define a method like:

```java
def someMethod() = {
    // do something here
}
```

To define functions in Scala, we can use `Function` objects or their respective syntactic sugars. To know more about functions and functional programming in Scala, do check [this](https://blog.codekaro.info/scala-for-beginners-crash-course-part-3).

### How To Define Classes and Objects?

In Python, we can define a class using the `class` keyword, the same keyword can be used to define a class in Scala.

Whereas objects in Scala are singleton instances and similar to what we call static class in other programming languages.

A class however in Scala can be instantiated using the `new` keyword, whereas in Python calling the class directly creates an instance for that.

In Python:

```python
class Student:

    def __init__(self):
        # do something here

student = Student()     # creates an instance of class Student
```

In Scala:

```java
class Student

val student = new Student()     // creates an instance of class Student

// use Object keyword for singleton objects

Object Student

val aParticularStudent = Student
```

To know more about classes and objects in Scala, I recommend checking out [this](https://blog.codekaro.info/scala-for-beginners-crash-course-part-2) article.

### Miscellaneous

Scala offers 2 more advantages over Python, namely **traits** and **tail recursion**. 

Python does not offer tail recursive capabilities to its functions and suffers from stack overflow errors whenever functional programming goes wrong. To know more about why python does not offer tail recursion, you can read [this](https://neopythonic.blogspot.com/2009/04/tail-recursion-elimination.html) article. However, there is a work-around as described in [this](https://chrispenner.ca/posts/python-tail-recursion) article using decorators.

Similarly, Python does not have concepts like traits. A trait is used to describe the quality of a class, whereas in Python you would have to do multiple inheritances to get certain qualities or have to define certain methods within the class definition. Trait allows loose coupling.

How to define a trait in Scala?

```java
trait SomeQuality

class Student extends SomeQuality
```

### Wrap Up

Well, that wraps up this simple Scala Vs Python syntax cheat sheet.

What else would you add to this cheat sheet? Please let me know in the comments!

If you are looking to sharpen your coding skills in Python or Scala, then do consider buying these awesome books that go in-depth to let you understand the semantics of the language.

For Python:

* [Python - The Bible](https://amzn.to/3k4sVmN)
* [Python - The Complete Reference](https://amzn.to/3959lR9)
* [Automate The Boring Stuff With Python](https://amzn.to/3hxhjqJ)
* [Python Basics](https://amzn.to/3AcJgvc)

For Scala:

* [Scala For The Impatient](https://amzn.to/3C4rZ8a)
* [Scala Programming Projects](https://amzn.to/3tAluXH)
* [Functional Programming in Scala](https://amzn.to/3hnZYAw)
* [Programming Scala](https://amzn.to/3k66Lk1)

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](https://chandraji.dev/series/python) to [Computer Vision](https://chandraji.dev/series/computer-vision) to [Scala](https://chandraji.dev/series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏