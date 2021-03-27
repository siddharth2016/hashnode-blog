## Let's Talk Python - Some of the Unknown 👤

After working on and building things using python programming language for a while, I feel that there are some of the tricks or unknowns that this beast of a language contains and has to offer !

In this article I aim to highlight some of the unknowns that I work with from time to time and that I feel every python developer should know to get the most out of it.

Without any further ado, let's begin !

---

### Unknown 1 - NaN

Well, `NaN` itself is an unknown (Not-A-Number) when it comes to programming or mathematics, but what a python developer should focus on is the arithmetic operations on a `NaN` object (that is basically `math.nan`), they are bizarre !

Let's see this through an example below:

```python

someNaN = float("NaN")

someNaN == someNaN  # False

```

Well, you see python itself couldn't figure out the infamous `NaN` object. It considers as what it literally means - *Not-A-Number*, hence if something is not a numeric value (or can not be converted to a numeric), how come we can compare it (makes sense, right ?).

So, if there is a equality check where we need to filter out all `NaN` from a list or dictionary, how can we do that ? For this python provides us with `math.isnan`, so to check the `NaN` equality, always use `math.isnan`.

Although, you may not encounter `NaN` objects out of the blue as python is intelligent enough to not throw `NaN`, instead it raises expections like `ValueError` !

But, if you are doing data science and using numpy or pandas, be careful and check your code atleast twice to make sure you handle `NaN` objects.


### Unknown 2 - global, nonlocal

Ever encountered a situation where you needed to access out-of-scope variable and didn't know the right way to do it ?

Well, I have plenty of my share experiencing the exact same situation, where I had to refactor a lot of code just to access some out-of-the scope variables !

Let's see how can we access global variables first:

```python

someGlobalVar = True

def someFunc():
    return someGlobalVar

def someFunc2():
    someGlobalVar = False
    return someGlobalVar

def someFunc3():
    global someGlobalVar
    someGlobalVar = False
    return someGlobalVar


print(someFunc(), someGlobalVar)    # True, True
print(someFunc2(), someGlobalVar)   # False, True
print(someFunc3(), someGlobalVar)   # False, False

```

`someFunc` above deals with the global variable while returning `someGlobalVar`, without changing the actual global variable outside the scope it directly returns it with no change at all. Python treats it as global and not local to function's scope.

`someFunc2` changes the variable `someGlobalVar` resulting in python to think that some new local variable is created within the function and hence does not change global variable.

`someFunc3` uses `global` keyword to explicity say which varibale is going to be global within the function scope. Hence, after using global keyword, python knows that `someGlobalVar` is coming from outside scope and it needs to change that.

So, which approach to used while developing software ?

Well, to be honest, it is better to not use too many global variables, but only to define some constants that are never going to be changed during execution.

Still, to use global variables within local scopes of functions or classes, always use `global` keyword, even when you are not going to change the value, as explicit is better than implicit !

Same goes for `nonlocal` keyword, always specify nonlocal variables when creating closures that requires the same.

```python

def outer():
    val1 = True
    def inner():
        nonlocal val1
        if val1:
            # do some stuff

```

`nonlocal` keyword will look for the nearest/immediate outer variable, if not found it will move to next outer scope and so on...


### Unknown 3 - Mutable Objects

Ever tried to pass mutable objects like `list` or `dict` as default arguments to a function in python ?

If not, then you have been lucky, if yes, then you know the disaster it brings (sometimes this disaster can be a blessing in disguise, but not often !).

Never ever pass mutable objects as default function arguments (except for logging purpose) !

```python

def someFunc(a = []):
    a.append('Never Do This')
    return a

print(someFunc())   # ['Never Do This']
print(someFunc())   # ['Never Do This', 'Never Do This']
print(someFunc())   # ['Never Do This', 'Never Do This', 'Never Do This']

```

During execution, interpretor creates some space for variable `a` which is a mutable object `list` and when `someFunc` is called and appends some value to `a`, no new address is created but at the same address where `a` resides the value is added (since its mutable, value at same address can be changed), same thing happens during 2nd and 3rd call to `someFunc` resulting in getting a completely different list from what we wanted.

A better way to deal with this could be as follows (as most of the tutorials and stackoverflow answers pointed out):

```python

def someFunct(a = None):
    if not a:
        a = []

```

Doing this, creates a new address for list `a` everytime it is called, as each call when ends destory its contents and recreate it again during next call. But for default args, the are created once !


### Unknown 4 - Indexing List

Well, to access some part of the list/string in python, we immediately gets to indexing it ! But, how often do we index it using negative indices or using a method like `partition` (which returns a tuple of length 3, for string object) ?

Let's look at in which case negative index could be useful:

```python

a = [1, 2, 3]

print(a[::-1]) # reverse the list in 1 line

```

A case where negative index makes no sense:

```python

a = [1, 2, 3]

print(a[-0:]) # equivalent to a[:], creates copy of list, [1, 2, 3]

```

Well, not much here, but for me, I have seldom used negative indices to access elements, sometimes it feels like a trick to do a job and sometime it is hectic to manage negative indexed slice. More than often, just to access the last element I use negative index or to reverse a list !

---

That's it from me, I hope you learnt something new or refreshed some of the unknowns (that's what I like to call them 😁) !

If you were here as one of the followers, then I appreciate you reading this and if you are new here, then follow me for more upcoming on-the-go articles to freshen up your developer's brain 🧙‍♂️

Share it with your friends, python programming beginners or seasonal python professionals!

---

Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏