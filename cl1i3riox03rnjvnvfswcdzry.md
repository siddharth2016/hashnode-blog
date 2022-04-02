## Python Programmer to a Java Developer: Things I Learned

So, a couple of months back I started learning [Java Programming Language](https://en.wikipedia.org/wiki/Java_(programming_language) for a project at my organisation. Initially, like most of us, I felt intimidated by Java. For almost every time, as far as I can remember, I never looked at Java as my choice of language to complete any task at hand. It felt distant and very difficult to understand just because of one `System.out.println`.

But, any way I took, which looked daunting at first, the task of learning Java! And I am not going to lie, Java is the most user-friendly programming language for anyone who works with [Object Oriented Programming](https://en.wikipedia.org/wiki/Object-oriented_programming) almost every day. Heck, if you love [Functional Programming](https://en.wikipedia.org/wiki/Functional_programming), Java got you covered (but I am a little biased towards [Scala Programming Language](https://en.wikipedia.org/wiki/Scala_(programming_language)).

Being a Python Developer since college and now learning Java, I wanted to highlight some of the many things that I learned during this transition, which might help you decide whether you should go ahead and over that intimidation to learn Java or not.

---

### Don't Be Afraid Of Java Hello World Program

I have seen people disliking Java immediately after seeing the code of [Hello World](https://www.javatpoint.com/simple-program-of-java) written in Java (I was one of them). They start comparing it with Python's syntax of [Hello World](https://www.python-ds.com/python-hello-world) program and get intimidated and leave before even trying to understand why its syntax is like that.

So, Java is almost a complete Object-Oriented Programming (OOP) language and as we all know, in OOP we deal with classes/objects and when we talk about classes or objects, we need to understand that the code written might be big but it is guaranteed to be human-readable and understandable and highly manageable.

If you don't know, almost everything that Python offers is actually an object of some type behind the scenes. It is abstracting it all out so that we write less code and can focus on delivering fast. But, it comes at a cost of speed (which now with many enhancements is improving).

>Note: You can start learning Scala to write less code and be as fast as Java [here](series/scala).

So, before starting to learn Java, you should know that classes will be defined, objects will be created, methods will be called and all will be in accordance with OOP, and you will learn OOP either as a beginner or as a professional from the get-go through Java.

Don't be afraid of that Hello World program anymore.

### Java Works With Primitive Data Types

Java is not 100% OOP language in nature, it also works with [primitive data types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html).

Well, after learning that the Java Hello World program deals with OOP concepts and now getting to know that Java is not 100% OOP language, I felt relieved, because you know, C++ works with primitive data types and even though Python is dynamically typed, behind the scenes it works with primitive data types, then it means that learning curve would be same for anyone learning a new programming language.

But, Java aims to be 100% OOP language and to cover primitive data types, it offers wrappers around primitive types. So, for each primitive type, there is a corresponding class we can rather use.

```java
int i = 0;
// is same as
Integer i = 0;
```

Taking the above example, `int` is a primitive data type and `Integer` is a wrapper class around it.

Then, how can it directly assign an `Integer` type variable to a primitive value when we know that it is a wrapper class? It is accomplished using autoboxing. Similarly, we can directly use the `Integer` type value or any other wrapper class value using unboxing whenever needed within the program.

Both autoboxing and unboxing are done by JVM behind the scenes and can also be done explicitly, so you do not need to worry about it much. Also, this article is not intended to help you learn [auto/unboxing](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html), but it's better to know the inner workings and I would recommend you to check the link provided.

### A Lot Of Similarities

After spending a lot of time learning Java, I figured that it is not much different from Python when it comes to programming language concepts. As they say, learning another programming language is easy when you know one already.

- Python provides conditional statements so does Java.
- Python has looping constructs like `for` and `while`, and so does Java. Only they differ in syntax.
- Python provides exception handling using `try-catch` and so does Java.
- Python can be used for OOP, guess what, Java is OOP.
- Python can be used for functional programming, and so does Java.
- Python provides `list`, `set` and `dict` and Java have `ArrayList`, `HashSet` and `HashMap`.
- Python is used for competitive programming (CP), and Java is 2nd most used programming language for CP after C++.
- A big community of developers to help each other out.

So, with all these similarities we can be less worried about learning Java.

### Not Everything Is Similar

Even though Java and Python are a lot similar in many concepts, there are some things that Java differs on and these are some of them:

- Java have [access modifiers](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html). `public`, `private`, `protected` and `package-private`.
- Java works with [interfaces](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html). Java defines interfaces to provide the ability of a `can` relationship between classes, similar to what an [abstract class](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html) defines, `is a` relationship.
- Inner classes in Java are handled very differently than in Python.
- `static` members in a class can be defined. Although, Python have `@classmethod` and `@staticmethod`, but as Zen of Python says, we are all adults here!
- Generic classes. One step closer to being dynamically typed classes!
- 2 IO packages, [java.io](https://docs.oracle.com/javase/tutorial/essential/io/streams.html) and [java.nio](https://docs.oracle.com/javase/tutorial/essential/io/fileio.html). `java.io` has similarities to traditional input/output programmes that we are used to. But, `java.nio` is something else completely. It uses channels/buffers and sometimes selectors to perform the reading/writing of data.
- `Serializable` interface, helps when we need to output classes to streams.
- It provides the `java.sql` package as an out of the box library to directly connect with databases in a very OOP way using [JDBC](https://docs.oracle.com/javase/tutorial/jdbc/basics/index.html) drivers.

There are many more dissimilarities, but now we get a general idea that both Python and Java are similar and dissimilar on many points giving different advantages.

### An Ocean Of Opportunities

When Java gets used with frameworks like [spring](https://spring.io/), it becomes a beast of a language, providing almost all the capabilities that we need in general to develop fully functional end-to-end applications.

I am still learning a lot in the Java tech space and will continue to do so, you can also start learning it or any other technology that you feel intimated by and you will soon realize that it's not that difficult and easy to apply in your daily dev tasks.

At the end of this article I just want to say that - when you stop learning and experimenting, you start ignoring those opportunities that lie in front of you.

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala) to [Java](series/java).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏