## Python - Useful Tips for Beginners

Python ranked as the number 1 programming language as per PYPL - Popularity of Programming Language. Python is easy to learn, without putting too much pressure on the learner, it helps to get started with programming in the most friendly way possible with the use of concise and easy to read plain English like syntax, with powers like - dynamically typed variables, single-click execution with no worry about compiling code first - using it as your first language to do just anything and everything out there is definitely the right choice!

Here, we are going to discuss some of the tricks/tips that a beginner python learner should know and can get benefits out of that in his/her daily work routine.

Let's get started!

---

### Assignment

Python allows a significant improvement to the assignments of variables. One can simply assign several variables with each variable assigned in a single line using the `=` operator.

```python
# Assign variable, 1 line at a time.

a = 1
b = 2
c = 3
```

But, little did we know, python allows developers to save space and write less and be more pythonic! We can do multiple assignments, yes that too in a single line.

```python
# Assign variables, all of them in a single line.

a, b, c = 1, 2, 3
print(a, b, c)      # Output: 1 2 3
```

A single value can be assigned to multiple variables in a single line.

```python
# Assign variables to a single value in a single line.

a = b = c = 1
print(a, b, c)      # Output: 1 1 1
```

This is possible because of something called tuple unpacking (not an advanced topic, you will learn that in tuples, if not already, try this [link](https://www.guru99.com/python-tuples-tutorial-comparing-deleting-slicing-keys-unpacking.html)).

We can simply assign multiple values to a variable and it will pack it as a tuple.

```python
# Assign multiple values to a single variable

x = 1, 2, 3, 4  # Treat it as a tuple
print(x)        # Output: (1, 2, 3, 4)
```

### Swapping

Well, what we learn in traditional programming languages is that swapping a variable's value to another variable requires the usage of an extra variable, say, `temp` or with the usage of some more complex concepts like pointers.

But, as python says - We don't do that here!

There is an awesome way to that:

```python
# Swap variables

a, b = 2, 5
print(a, b)     # Output: 2 5

a, b = b, a
print(a, b)     # Output: 5 2
```

Again, behind the scenes working is similar to tuple unpacking.

### List to String to List

Let's look at some awesome 1 liners for converting a list to string and vice-versa.

```python
# Convert list to string and string to list

a = ['a', 'b', 'c']
aString = "".join(a)
print(aString)      # Output: abc

aAgain = list(aString)
print(aAgain)       # Output: ['a', 'b', 'c']
```

### Some More List

A list of strings can be printed out in a single line, without using a loop.

```python
# Print a list of a string with a single print()

a = ["Hello", "Python", "World"]
print(*a, sep=',')      # Ouput: Hello,Python,World
```

The little `*` symbol is used here to unpack the list. It can be used to unpack other iterable type objects as well. Look at the end of this article for more info on asterisks.

Get a list of unique elements. You can do this with loops or with lambdas, but there is a 1 liner again for this.

```python
# Get a list of unique items.

a = [1, 2, 3, 4, 1, 1, 3, 4, 2, 5, 5]
print(list(set(a)))     # Output: [1, 2, 3, 4, 5]
```

Here, `set()` function creates a set of unique elements first and then outer `list()` return a generated list.

In case you need to create a list with repetitive values, the easiest way is to do the following:

```python
# A list with repetitive values

a = [1, 2, 3] * 6
print(a)    # Output: [1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
```

### Operators

You must have heard about the `_` (underscore) character, but did you know that it can be used as an operator as well?

Yes, we can use `_` as an interactive operator, more of a temporary variable used commonly for loops, when we are not concerned about the values on which looping is done.

```python
# Underscore operator usage
# When you do this in REPL
>>> a = 2
>>> b = 3
>>> a * b
6
>>> _
6
>>>
```

With for loop construct, we can do something like this:

```python
# Underscore to help developers to ignore values on which loop is done.

for _ in range(10):
    # Do something here that does not depends on range(10) values.
```

Let's move to the next operator tip.

Python allows the chaining of multiple comparison operators, without using a logical operator on that.

```python
# Chaining of comparison operators

a = 5
print(1 < a < 10)   # Output: True, otherwise in other languages like C, it would be - 1<a && a<10
```

Next is the ternary operator. Like many other programming languages, Python also has a facility that gives the effect of a ternary operator (technically it's not an operator, but more of a single-line conditional statement).

```python
# Python's way of the ternary operation

a = 5
print("Five" if a==5 else "Not Five")   # Ouput: Five
```

Here, it checks for the condition if `a` is `5` or not, if it was not `5` then the value after `else` would be printed.

### Miscellaneous

Now, let's wrap this up with some miscellaneous tips that a beginner can use.

A function can return multiple values. It uses the tuple unpacking concept to return multiple values at once.

```python
# A function can return multiple values.

def someFunc():
    a, b, c = 1, 2, 3
    # Do something here with a, b, c
    return a, b, c

d, e, f = someFunc()
print(d, e, f)      # Output: 1 2 3
```

We can have a simplified `if` constructs.

```python
# Simplified IF statements

a = [1, 2, 3]
i = int(input())

# Complex IF
if i == 1 or i == 2 or i == 3:
    # Do something

# Simplified IF
if I in a:
    # Do something
```

We can do single line reversal of string, i.e, reverse of a string.

```python
# Reverse a string.

s = "Hello Python World"
print(s[::-1])      # Output: dlroW nohtyP olleH
```

---

Well, that's it from me.

There are more nuances to the tricks python offers, this blog may not be enough for all of those, but still, these were some of the important tips/tricks that a python developer should know.

I have published some blog articles where I have tried to lay out more such nuances, please go through them to get a better understanding of asterisks and other things python has to offer.

[Python Asterisks](https://blog.codekaro.info/python-asterisks)

[Let's Talk Python - Some of the Unknown 👤](https://blog.codekaro.info/lets-talk-python-some-of-the-unknown)

---

Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Need inspiration or a different perspective on the Python projects or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏