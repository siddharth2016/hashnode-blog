---
title: "Scala For Beginners - Crash Course - Part 5"
seoDescription: "Scala programming, learn about collections, map, flatMap and filter in this Scala for beginners crash course and where to go from here."
datePublished: Mon Sep 13 2021 11:26:58 GMT+0000 (Coordinated Universal Time)
cuid: cktik9zhr01c0nos1hmqv3rgw
slug: scala-for-beginners-crash-course-part-5
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1631529339828/ysmHxIuv8.png
tags: tutorial, programming, scala, beginners, functional-programming

---

Welcome to the 5<sup>th</sup> and last part of the Scala beginners crash course, here we will go through the concepts like collections, sequences and map, flatmap, filter in the Scala programming language. This will be a short article, so if you need much more in-depth information you can check out the recommended books at the end of this article.

It will be a no-nonsense, to the point kind of article (like [part 1](scala-for-beginners-crash-course-part-1), [part 2](scala-for-beginners-crash-course-part-2), [part 3](scala-for-beginners-crash-course-part-3) and [part 4](scala-for-beginners-crash-course-part-4)) with all the necessary links wherever needed.

Without any further ado, let's get started.

---

### Before We Start

Before we start coding out, first create a new object in the `crashcourse` package (please go through [part 1](scala-for-beginners-crash-course-part-1) for more information on creating packages and objects).

Let's name it `Collections` like below:

![collections.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531346691/e6CNxW3S3.png)

Now, we can start coding out the examples on this Scala application.

### Collections

Scala offers 2 sets of collections, one is mutable and the other one is immutable. Scala by default works with immutable collection objects.

But, we can import mutable collection objects whenever needed like:

```java
import scala.collection.mutable
```

Also, if we want we can see all immutable collection objects in package `scala.collections.immutable`.

Following are some of the immutable collection objects provided in scala:

* [HashSet](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/HashSet.html)
* [SortedSet](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/SortedSet.html)
* [Vector](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/Vector.html)
* [StringLike](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/StringLike.html)
* [Range](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/Range.html)
* [List](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/List.html)
* [Stream](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/Stream.html)
* [Stack](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/Stack.html)
* [Queue](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/Queue.html)
* [HasMap](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/HashMap.html)
* [SortedMap](https://www.scala-lang.org/api/2.12.2/scala/collection/immutable/SortedMap.html)

Similar collection objects are available in the mutable set. This [link](https://www.scala-lang.org/api/2.12.2/scala/collection/mutable/index.html) has all the mutable collection objects set.

The commonality between mutable and immutable collection objects is that both extends trait [Traversable](https://www.scala-lang.org/api/2.12.2/scala/collection/Traversable.html). It is a base trait for all collections and offers a great variety of methods.

Some of these collection objects are often sequenced in nature. Let's discuss sequences now.

### Sequences

Sequences in scala are a general interface for data structures that have a well-defined order and can be indexed.

These support various operations like:

* `apply`, `iterator`, `length`, `reverse` for indexing and iterating.
* Concatenation, appending, prepending.
* A lot of others - grouping, sorting, zipping, searching and slicing.

Let's see how to define a sequence:

![sequence.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531369496/8rbrbjIYW.png)

Output:

![sequence2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531388160/8067-fcPJ.png)

`Range` is one of the sequences available, we can define a `Range` like this:

![range.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531407959/iaYGwXKJ4.png)

Output:

![range2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531425930/J_O_pCi5I.png)

There is another type of sequence, `LinearSeq` which is an immutable linked list with the following properties:

* Accessing head, tail and using methods like `isEmpty` are fast and takes `O(1)` time.
* Most other operations like `length` or `reverse` takes `O(n)` time.

Arrays in scala are equivalent to java arrays, these can be manually constructed with predefined lengths. These can be mutated, have fast indexing and are interoperable with java's arrays.

![array.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531440888/_h4W3tUUF.png)

Vectors are also present in scala, these are the default implementation for immutable sequences taking constant time for indexed based read/write, with fast append/prepend, shows good performance for large size vectors and are implemented using a fixed branched trie data structure.

![vector.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531455900/knizLYOg-.png)

Tuples are finite ordered kinds of lists that can contain a maximum of 22 elements. A tuple value data type is defined similarly to a function like `TupleN[...]`.

![tuple.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531475585/fR2ZmAxRN.png)

There is one more collection object, `Map`, which is a key->value pair data structure present in scala. Following are some ways to manipulate a map:

![map.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531488699/EIud6p632.png)

Output:

![map2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531499216/dHUHeRySj.png)

More on Scala collections can be found [here](https://docs.scala-lang.org/overviews/collections/overview.html) or you can check the books provided in the last section for the more detailed in-depth working of collections.

### map, flatMap, filter and for

Finally, on the most important part of functional programming, that would become the daily need of a Scala programmer. I wanted to include these in the previous [part](scala-for-beginners-crash-course-part-4) but to show how these work I needed to show collections in scala first, now that we know enough about collections, let's move on to these functions.

> Note: For the sake of examples, I will be showing these operations on the `List` sequence, you can try these on other collections as well.

First, define our list collection like this:

![list.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531520453/GABMEV5EE.png)

What is the `map` method? It allows a certain function to be applied to all the elements present in the given sequence and evaluates to a sequence of updated values.

What is the `filter` method? It filters out the elements which do not meet a certain criterion defined as another function and evaluates to a sequence of filtered values.

What is the `flatMap` method? This is identical to the `map` method, but the only difference is that in `flatMap` the inner grouping of an item is removed and a sequence is generated. So, if `flatMap` is applied to a list then the generated output will be a list of lists, changing the inner grouping of integer elements to a list and later flattening it.

What is the `for` loop in scala? Yeah, you read it right 'What is' and not 'How to', in scala, writing a `for` loop is just a fancy way of writing a coupled `map` and `flatMap` methods. A `for` loop in scala can be written as:

![mapfilter.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531539746/H2GaxC-s3.png)

Output:

![mapfilter2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631531550914/FvTwmpzad.png)

These are some important methods to remember while coding out in scala.

### Wrap Up

Well, that wraps up part 5 and the end of this crash course.

I hope it was something worth it for you as a reader and made you a scala enthusiast at the end of this course.

You can pick up any of the below books to master the art of programming in scala:

* [Scala For The Impatient](https://amzn.to/3C4rZ8a)
* [Scala Programming Projects](https://amzn.to/3tAluXH)
* [Functional Programming in Scala](https://amzn.to/3hnZYAw)
* [Programming Scala](https://amzn.to/3k66Lk1)

To keep in touch, you can follow me on here or subscribe to get the updates of the new blogs that I will write in the future or follow me on [Twitter](https://twitter.com/chandrajidev) where I share my thoughts not only on programming but also on personal finance.

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏