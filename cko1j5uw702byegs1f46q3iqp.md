## Python - List Vs Tuple Memory Management

This article is going to be a short read, we will focus on how memory is managed in Python for objects like `list` and `tuple` and what can be the key takeaways.

Let's get started!

---

### List

Python list as we all know is a mutable dynamic array that behaves like a linked list as well. Let's look at some code for creating and updating a list:

```python
# ./list_1.py

l = [1,2,3]     # A new list gets created
print('Initial List', l)

l.append(4)     # Updating list using in-built append method
print('Append 4, List updated to', l)

l.pop()         # Pop last item
print('Pop, List updated to', l)

l += [5, 6]     # Updating list by adding a new list to given list
print('Add new list, List updated to', l)
```

Following will be the output:

```bash
Initial List [1, 2, 3]
Append 4, List updated to [1, 2, 3, 4]
Pop, List updated to [1, 2, 3]
Add new list, List updated to [1, 2, 3, 5, 6]
>>>
```

Now let's see what happens in memory when we run the above script, here we will be using `sys` to help us out on viewing system-related information:

```python
# ./list_2.py

import sys
l = [1,2,3]     # A new list gets created
print('Initial List', l)
print('Initial List Address', id(l))
print('Initial List Memory', sys.getsizeof(l))

l.append(4)     # Updating list using in-built append method
print('Append 4, List updated to', l)
print('Append 4, List Address', id(l))
print('Append 4, List Memory', sys.getsizeof(l))

l.pop()         # Pop last item
print('Pop, List updated to', l)
print('Pop, List Address', id(l))
print('Pop, List Memory', sys.getsizeof(l))

l += [5, 6]     # Updating list by adding a new list to given list
print('Add new list, List updated to', l)
print('Add new list, List Address', id(l))
print('Add new list, List Memory', sys.getsizeof(l))
```

Let's look at the output first:

```bash
Initial List [1, 2, 3]
Initial List Address 139688582615624
Initial List Memory 88
Append 4, List updated to [1, 2, 3, 4]
Append 4, List Address 139688582615624
Append 4, List Memory 120
Pop, List updated to [1, 2, 3]
Pop, List Address 139688582615624
Pop, List Memory 120
Add new list, List updated to [1, 2, 3, 5, 6]
Add new list, List Address 139688582615624
Add new list, List Memory 120
>>>
```

Following points we can find out after looking at the output:

- Initially, when the list got created, it had a memory of `88` bytes, with 3 elements.
- Later on, after appending an element `4` to the list, the memory changes to `120` bytes, meaning more memory blocks got linked to list `l`.
- Even after popping out the last element the created blocks memory remains the same and still attached to list `l`. And when we add another list with 2 more elements to the given list `l`, we see that occupied memory is still the same `120` bytes. Hence, we can conclude that it is behaving more like a dynamic array, which updates the size of the list to contain more elements at once to avoid repetitive callbacks (to create and attach new memory address) at every insertion of the new element.
- We also notice that the list address remains the same, even if we do append, pop or add a new list to it (as long as we don't assign it to a new variable). This advocates the nature of the mutability of python lists (it means, more or less, that at the same address we are able to update values or extend it further).

Now, let's look at the tuples.

### Tuple

Python tuple as we all know are immutable and do not extend in the memory further after the initial declaration. Now, let's look at the above same scenario but for tuples:

```python
# ./tuple_1.py

import sys
t = (1,2,3)     # A new tuple gets created
print('Initial Tuple', t)
print('Initial Tuple Address', id(t))
print('Initial Tuple Memory', sys.getsizeof(t))

t += (5, 6,)     # Updating tuple by adding a new tuple to given tuple
print('Add new tuple, Tuple updated to', t)
print('Add new tuple, Tuple Address', id(t))
print('Add new tuple, Tuple Memory', sys.getsizeof(t))
```

Output:

```bash
Initial Tuple (1, 2, 3)
Initial Tuple Address 140452527817280
Initial Tuple Memory 72
Add new tuple, Tuple updated to (1, 2, 3, 5, 6)
Add new tuple, Tuple Address 140452528572728
Add new tuple, Tuple Memory 88
>>>
```

Following points we notice after looking at the output:

- Since, tuples are immutable, once created cannot be updated unless a new tuple gets added to the previous one, resulting in the creation of a new tuple.
- Once a tuple gets created, its allocated memory will not be changed.
- Updating a tuple after adding another tuple to it, updates the address of the resulting tuple, this advocated its immutability property.
- We can see it allocates `72` bytes for 3 values and `88` for 6 values, it does not allocate the unnecessary amount of memory, only what is required is allocated.

Let's look at some miscellaneous points.

### MISC

What happens when we create an empty list and empty tuple?

```python
# ./misc.py

import sys

t1 = ()
t2 = ()

l1 = []
l2 = []

print('List l1 address', id(l1))
print('List l2 address', id(l2))
print('List l1 memory', sys.getsizeof(l1))
print('List l2 memory', sys.getsizeof(l2))

print('List t1 address', id(t1))
print('List t2 address', id(t2))
print('List t1 memory', sys.getsizeof(t1))
print('List t2 memory', sys.getsizeof(t2))
```

What did we get?

```bash
List l1 address 139766851756616
List l2 address 139766851761800
List l1 memory 64
List l2 memory 64
List t1 address 139766871547976
List t2 address 139766871547976
List t1 memory 48
List t2 memory 48
>>>
```

What did we find?

- Creating 2 empty lists have the same amount of memory allocated, whereas the address of both lists is different. It makes sense because, list address will have to act as mutable and cannot be the same at a given time, which means 2 different lists will be different unless they are the same (not in value but in reference point of view).
- Creating 2 empty tuples have the same amount of memory allocated and will point to the same address initially. It makes sense because of its immutability property. Consider integer `1` value in python that is immutable and always point to the same address unless changed to some other integer. Similarly, the initial empty tuple will always point to the same address unless changed to some other tuple.

---

Well, that's it from me.

We explored quite a few points on how memory is allocated and how it could be managed in Python.

To know more about memory management, I encourage you to explore their code available on python's [repo](https://github.com/python/cpython).

Feeling it's difficult to go through the source code of python? Don't worry, we can always use available `sys` module methods and other functions like `id` to develop an understanding of what could be happening behind the scenes.

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏