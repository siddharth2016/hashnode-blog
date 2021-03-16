## Python Asterisks

Asterisk, we all know is a little star symbol (*), used in programming languages for multiplication and other tasks like pointer declaration!

In Python, there is no pointer concept, but still, asterisks carry some amazing abilities to ease the life of a programmer.

In this article, we are going to see some of the most used use-cases of the asterisk symbol!

Then, let's get started 😎

---

### Multiplication and Exponentiation

Asterisk symbol most common use case is for accomplishing multiplication tasks (that we all know) and in python, it provides yet another much-needed task of exponentiation with the help of using 2 asterisks instead of 1 (amazing, right !).

```python

a = 2*4     # 8
b = 2**3    # 8, exponentiation

```

### Unpacking Iterable Objects

Asterisks can be used to unpack a list or any iterable data type. Simple, just put an asterisk in front of the variable that contains iterable needed to be unpacked and voila, you get your unpacked data!

```python

alist = [1, 2, 3]
blist = [4, 5, 6]
ctuple = (7, 8, 9)

combined = alist + blist + list(ctuple)     # tedious, less pythonic

unpacked = [*alist, *blist, *ctuple]        # hmm, cool, right ? more pythonic

```

We can use this kind of unpacking to assign some values to a variable. For example, we need the first element of the list in a variable and all other elements in another variable, then something like this will do the trick:

```python

a = [1, 2, 3, 4]

b, *c = a       # b = 1 and c = [2, 3, 4]

```

### Restrict Functions to Keyword Only Arguments

Asterisks in python can be used to restrict a function so that it can take only keyword arguments, but how? let's look at an example below:

```python

def someFunc(*, firstarg, secondarg):
    pass

someFunc(1, 2)      # Raises Exception - TypeError: someFunc takes 0 positional arguments, but 2 were given

someFunc(firstarg=1, secondarg=3)   # Works like magic !

```

To restrict the function to take keyword arguments only, place an asterisk symbol before the arguments you want to be restricted.

```python

def someFunc(zerotharg, *, firstarg, secondarg):
    pass

# Here, zerotharg is a positional argument (which we can use as a keyword also, but not restricted to it) and firstarg and secondarg (after the asterisk) are keyword-only (restricted) arguments.

```

### Unpack Multiple Arguments

Using an asterisk to get multiple arguments in a function is no less than magic in itself. Even, we can get multiple keyword arguments, that's insane!

```python

def someFunc(*args, **kwargs):
    pass

```

`*args` will take multiple positional arguments, unpacking them as a tuple (can be accessed using indices) and `**kwargs` will take multiple keyword arguments, unpacking them as a dictionary (can be accessed as a dict key-value).


---

That's it from me!

I hope you enjoyed reading the article and if you have reached to this point, then what are you waiting for, hit follow button, share this with your friends and let others know the beauty of the python programming language!

---

Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏