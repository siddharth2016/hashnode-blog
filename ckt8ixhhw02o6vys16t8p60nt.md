## Scala For Beginners - Crash Course - Part 4

Welcome to the 4<sup>th</sup> part of the scala beginners crash course, here we will go through the concepts like options, exception handling and pattern matching in the scala programming language. This will be a short article, so if you need much more in-depth information you can check out the recommended books at the end of this article.

It will be a no-nonsense, to the point kind of article (like [part 1](https://blog.codekaro.info/scala-for-beginners-crash-course-part-1), [part 2](https://blog.codekaro.info/scala-for-beginners-crash-course-part-2) and [part 3](https://blog.codekaro.info/scala-for-beginners-crash-course-part-3)) with all the necessary links wherever needed.

Without further ado, let's get started.

---

### Before We Start

Before we start coding out, first create a new object in the `crashcourse` package (please go through [part 1](https://blog.codekaro.info/scala-for-beginners-crash-course-part-1) for more information on creating packages and objects).

Let's name it `OptionErrorPattern` like below:

![optionerrorpattern.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925030021/nVd9E9gnC.png)

Now, we can start coding out examples on this scala application.

### Options

An option is a wrapper for a value that might be present or not.

As the name suggests it evaluates to an option of 2 values, either `Some` or `None`, when given an expression. In this way, when we are dealing with some unsafe APIs, we can always wrap that API calls within an `Option` object to keep our program safe and error-free that might otherwise result in a `Null` pointer kind of exception.

For example,

![option1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925018987/sB1uRqqay.png)

Output:

![option2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925042862/-nK_ZfcMc.png)

* `Some` wraps a concrete value.
* `None` is a singleton for absent values.
* It is better to use `Option` in APIs that we are creating.

### Handling Exceptions

In scala, exceptions are handled inside try-catch blocks, like below:

![trycatch1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925058053/hTqvEBrrBP.png)

Output:

![trycatch2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925069861/Esd5kD21N.png)

But, it comes with its drawbacks:

* Multiple/Nested try-catch blocks make the code hard to read/follow.
* We can not chain multiple operations prone to failure.

To overcome these limitations, scala introduced a `Try` object that can act as a wrapper to wrap an error-prone expression and evaluates to either a `Success` or a `Failure` as a result.

A `Try` is a wrapper for a computation that might fail or not. It wraps failed computations as `Failure` and successful computations as `Success`.

To use `Try`, `Success` and `Failure` objects, we have to import these first:

```java
import scala.util.{Try, Success, Failure}
```

So, the above method `someErrorProneFunc` can be used with `Try` as follows:

![try1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925084602/6lmVG7jIU.png)

Output:

![try2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925093846/jtYL6zcZR.png)

We can check if a `Try` is a `Success` or `Failure` using `isSuccess` or `isFailure` methods respectively.

We can use `Try` to handle exceptions for avoiding runtime crashes due to uncaught exceptions or just to avoid an endless amount of try-catch blocks.

### Pattern Matching

Pattern matching is a mechanism for checking a value against a pattern. A successful match can also deconstruct a value into its constituent parts. It is a more powerful version of the `switch` statement in Java and it can likewise be used in place of a series of if/else statements.

A match expression has a value, the `match` keyword, and at least one `case` clause.

For example,

![pattern1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925111421/1pCDtmdXV.png)

Output:

![pattern2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630925120830/nW6vRfMZ8.png)

Some important points to note on pattern matching:

* It is used to decompose values.
* Cases are matched in the order given.
* What if there was no case that matched the pattern, then it would result in `MatchError`.
* Pattern matching works really well with case classes.

### Wrap Up

Well, that wraps up part 4 of this crash course.

I know, it was a very short read, my motivation was to keep it short and simple and be able to provide ample impetus to you to explore it further. 

Take it as a challenge or homework, explore advanced pattern matching, how you can use `Option` in conjunction with `Try` (it can do wonders to the API you are working on) and in the comments, mention what you know about on these concepts.

You can check these books to get more insights on these topics:

* [Scala For The Impatient](https://amzn.to/3C4rZ8a)
* [Scala Programming Projects](https://amzn.to/3tAluXH)
* [Functional Programming in Scala](https://amzn.to/3hnZYAw)
* [Programming Scala](https://amzn.to/3k66Lk1)

In the next and last part of this crash course, we will discuss the collections available in scala and most important of all, the map, flatmap and filter methods in scala.

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](https://chandraji.dev/series/python) to [Computer Vision](https://chandraji.dev/series/computer-vision) to [Scala](https://chandraji.dev/series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏