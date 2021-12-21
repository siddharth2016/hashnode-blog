## Scala For Beginners - Crash Course - Part 1

Welcome to this scala beginners crash course, here we will go through the basic syntax of scala programming language and some of the nuances available just for scala developers!

It will be a no-nonsense, to the point kind of article with all necessary links wherever needed.

Without further ado, let's get started.

### What Is Scala?

Scala is a programming language just like any other that is available out there but with a lot of sweetness and awesome features that opens our world to functional programming with easy to understand syntax, running on JVM under the hood, having all functionality that Java language offers with popularity ranging from being used in major FinTech companies to FAANG companies and as one of the major language for data engineering applications.

Need to know more about what is Scala, visit [here](https://www.scala-lang.org/).

### How To Install Scala?

Well, there are a couple of ways, in which the shortest and easy to follow is:

1. Install IntelliJ IDE from JetBrains. Check [here](https://www.jetbrains.com/idea/download/).
2. Select `IntelliJ IDEA | Preferences` for macOS ( Ctrl+Alt+S ) or `File | Settings` for Windows and Linux.
3. Select `Plugins` on the left pane.
4. Search for `Scala`, install the plugin and restart IDE.
5. Now, after it restarts, select `New Project` and then `Scala` -> `IDEA` project, click `Next`, set project name and your project folder are ready with necessary scala features.

> ![install_scala.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697251647/lECjG6zCA.png)
> Installing Scala

> ![setup_project.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697268678/dtXJwQfg8.png)
> Creating a New Project

> ![project_name.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697291997/GWDVd0_-X.png)
> Set Suitable Project Name


### How To Start Working With Scala?

After successful installation and creating a scala project, you would be seeing a nice project structure with the `src` folder.

We will create a package, inside that package we will continue our work. [What is a package?](https://docs.oracle.com/javase/tutorial/java/concepts/package.html)

To create a package, right-click on the `src` folder and select `New | Package` type, then fill in a name, whatever you like, for our case, let's name it `crashcourse`.

> ![create_package.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697312670/NxpfJgmX3.png)
> Create New Package

Now, right-click the `crashcourse` then `New | Scala`, here we are creating a scala object (we will discuss what scala object is in a minute). Let's name it `BeginnersCrashCourse`. It will create a standard template of scala object like below:

> ![object_creation.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697340573/3icKtWx0Z.png)
> Select Scala Class

> ![select_object.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621697358744/E9Gci-BRM.png)
> Select Scala Object

Well, now we have all we need to get started with some code!

### What Is An Object?

Before moving to object, if you notice the created template have `package crashcourse` at the top, it means that whatever code we are going to write below this, will belong to this package and can be accessed by any code file within the same package or can be imported using `import crashcourse._` in some other package. [How to do imports in scala?](https://docs.scala-lang.org/tour/packages-and-imports.html)

Now, what is an object in scala?

The object is a class that has exactly one instance, it means it already is an instance with a defined class structure. What is the defined class structure for an object type? It is everything we write inside scala object.

Scala objects are singleton, which means if we say we have an object named `BeginnersCrashCourse` then it is an instance that is a singleton in nature and whenever I am accessing it in the same executing program then its behaviour is going to be the same at every place, containing same values, methods or functions.

Treat an object as something that has static class level functionality.

How to write an object? Simple, just use the `object` keyword before writing an object, like below:

```scala
package crashcourse

object BeginnersCrashCourse extends App {

}
```

What is `extends App`? We extend `App` level functionality to a scala object whenever we want it to be able to run something inside it. It is like saying, we have a prebuilt `public static void main(String[] args)` whenever we extend it.

The above code is equivalent to:

```scala
package crashcourse

object BeginnersCrashCourse {
  def main(args: Array[String]): Unit = {
    
  }
}
```

Just to avoid writing the `main` method we can simply extend `App` to an object.

It is called a Scala Application if the main object (here `BeginnersCrashCourse`) extends `App` and is executable in nature. The main code goes inside an object that has `App` level functionality. Make sure you have a single main application while creating a service. Each service will have its main application to execute scala code.

Need more on scala objects, visit [here](https://docs.scala-lang.org/tour/singleton-objects.html).

### Expressions, Types, Vars, Vals, Def, Print and Codeblocks

How to create a variable in scala?

Well, there are 2 ways in which we can create a variable in scala:

```scala
package crashcourse

object BeginnersCrashCourse extends App {
  var var1 = 1  //Mutable
  val var2 = 2  //Immutable
}
```

> Writing comments in Scala is the same as Java.

The key difference between the 2 variables is that `var1` is mutable and `var2` is immutable and in functional programming, we will prefer to use immutable values.

`val` - values and `var` - variables, the name suggest itself that `val` will be a definite value whereas `var` are variables.

We can also use the semicolon `;` at end of each line, but they are not needed. We can also define types to the variables, but for the above case, the compiler does this work for us, although it is best to explicitly define the type of each value we use in our code. So below code is similar to the above:

```scala
package crashcourse

object BeginnersCrashCourse extends App {
  var var1: Int = 1;  //Mutable
  val var2: Int = 2;  //Immutable
}
```

There are several data types available in scala, some of them are as below:

```scala
package crashcourse

object BeginnersCrashCourse extends App {
  var var1 = 1;  //Mutable
  val var2 = 2; //Immutable
  
  val bool: Boolean = true  //or false
  val chr: Char = 'a'   //Make sure you use single quotes for character type value
  val str: String = "String"    //And double quotes for a string type
  val int: Int = 123    //An int value
  val shrt: Short = 123   //A short value
  val lng: Long = 123     //A long value
  val lng2 = 123L   //Make sure to put L to let compiler know that it is of type Long
  val flt: Float = 123.0f   //Make sure to put f at the end of float values
  val dbl: Double = 123.0   //Otherwise compiler will infer it as a type of double
}
```

More on scala types, [here](https://docs.scala-lang.org/tour/unified-types.html).

Now, let's move on to defining methods in scala. It can be done so using the `def` keyword, methods can take arguments passed to them as parameters while calling them. We can define empty methods as well, those that take nothing.

Let's define some methods and call them:

```scala
package crashcourse

object BeginnersCrashCourse extends App {
  var var1 = 1;  //Mutable
  val var2 = 2; //Immutable

  val bool: Boolean = true  //or false
  val chr: Char = 'a'   //Make sure you use single quotes for character type value
  val str: String = "String"    //And double quotes for a string type
  val int: Int = 123    //A int value
  val shrt: Short = 123   //A short value
  val lng: Long = 123     //A long value
  val lng2 = 123L   //Make sure to put L to let compiler know that it is of type Long
  val flt: Float = 123.0f   //Make sure to put f at the end of float values
  val dbl: Double = 123.0   //Otherwise compiler will infer it as a type of double
  
  // Methods
  def greetings(name: String): String = "Hello " + name
  println(greetings("Siddharth"))
  
  def greetingsModified(name: String): Unit = println("Hello " + name)
  greetingsModified("Sid")
  
  def greetingsFromSystem: Unit = println("Hello, you are learning Scala!")
  greetingsFromSystem
}
```

There are a lot of things happening here, let's break it down for each method:

**1.** We define a method using the `def` keyword, our first method named `greetings` takes a single parameter named `name` which of type `String` and the method returns a value of type `String` denoted by `: String` after `greetings(name: String)`, and this method evaluates to `"Hello " + name` with replacing with whatever name value we pass. We can print it to the console using the `println` method that conveniently puts a new line after printing the passed value to the console.

> A little detour before we move on to the next methods.

* In scala everything we write gets evaluated to some value, those statements like `"Hello " + name` from above are called expressions. Everything in scala can be referred to as an expression, even assigning of values is called an expression evaluating in such a way that assign values to a given name.

* Any expression that does not evaluate anything but does something, like printing to console or assigning a value or storing data, then data type of that whole expression is called `Unit`. So, whenever we assign a value within a method, and that's the last thing that method evaluated to then it will be of type `Unit`. Anything that evaluates to `Unit` type is called side-effect in scala.

* We can use code blocks `{...}` instead of directly writing an expression for our methods. Methods are evaluated to the value returned by the last expression if it has a number of expressions. You can consider it to be the return value of the method but without needing to write `return` explicitly. [Why we should not use return in scala?](https://tpolecat.github.io/2014/05/09/return.html). A method code block would look something like this:

```scala
def methodWithCodeBlock(name: String): String = {
  "Hello " + name    //Evaluates to String type
}

//Below method evaluates to same value as above method while doing something else, like printing something
def methodWithSomethingElse(name: String): String = {
  println("Inside methodWithSomethingElse")   //Evaluates to Unit type
  "Hello " + name    //Evaluates to String type, hence the type of method as it is the last expression evaluating
}
```

> Now, the remaining methods can be understood well.

**2.** We define the second method `greetingsModified` that takes a parameter named `name` of type `String` but evaluates to `Unit` as all this method does is print the greeting to the console as a side-effect.

**3.** The last method we wrote `greetingsFromSystem` does not take any parameter and evaluates to `Unit` with the side-effect of printing to console. This is called a parameterless method, scala allows us to define such a method, awesome, right?

For each method call, the following is the output to the console (to run a scala application, right-click and run in IntelliJ):

```bash
Hello Siddharth
Hello Sid
Hello, you are learning Scala!
```

---

More on `println`, visit [here](https://www.geeksforgeeks.org/scala-console-println-printf-and-readline/).

More on `Unit` type and other such types, visit [here](https://www.geeksforgeeks.org/scala-null-null-nil-nothing-none-and-unit/).

More on codeblocks in scala, visit [here](https://www.includehelp.com/scala/code-blocks-in-scala.aspx).

More on methods in scala, visit [here](https://docs.scala-lang.org/overviews/scala-book/methods-first-look.html).

### Wrap Up

Well, that wraps up part 1 of this crash course.

In the next part we will be discussing classes, more on objects, companions, case classes and much more related to object-oriented programming in Scala.

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏