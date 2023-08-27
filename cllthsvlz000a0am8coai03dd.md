---
title: "Stable and Unstable Sorting: Why Stability Matters?"
seoDescription: "Stable and Unstable Sorting Algorithms. Why Stability Matters? With Code Examples in Python and Java."
datePublished: Sun Aug 27 2023 13:34:54 GMT+0000 (Coordinated Universal Time)
cuid: cllthsvlz000a0am8coai03dd
slug: stable-and-unstable-sorting-why-stability-matters
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693142972829/300977bf-054f-4552-9ddd-b5b2158ac959.png
tags: algorithms, java, python, design, data-structures

---

Sorting is a fundamental operation in computer science and one that is used in solving some of the most common real-world problems. It involves arranging a collection of elements in a specific order, often in ascending or descending order. However, not all sorting algorithms are created equal!

Some sorting algorithms ensure that the relative order of **equal elements** remains unchanged after sorting, while others make no such guarantee. This distinction gives rise to the concepts of *stable* and *unstable* sorting algorithms. These categories may seem subtle, but they can have significant implications for various applications.

> Note: Equality of elements will depend on their data types, for primary types - their face values - and for secondary types i.e. objects - their custom-defined comparable methods - will act as the equality differentiator.

In this article, we will delve into the significance of stable and unstable sorting, exploring their differences and discussing scenarios where their distinctions matter.

## Understanding Stable and Unstable Sorting

Stability in sorting algorithms refers to the preservation of the relative order of elements with equal keys. In other words, if two elements have equal keys, and one appears before the other in the original sequence, a stable sorting algorithm will maintain that order in the sorted output. On the other hand, an unstable sorting algorithm makes no such promise. When two elements have equal keys, their relative positions in the sorted output may not match their original relative positions.

To illustrate this concept, consider a scenario where you have a list of student records, each containing a name and a score. You want to sort the records first by score in ascending order and then by name. A stable sorting algorithm will ensure that if two students have the same score, their names will remain in the same order as in the initial list. An unstable sorting algorithm, however, might rearrange the names of these students, leading to a different order.

Let's delve into some code examples to showcase stable and unstable sorting algorithms!

## Code Example In Python

Consider the following example in Python using the `sorted()` function, which employs a stable sorting algorithm:

```python
data = [(3, "apple"), (1, "banana"), (3, "orange"), (2, "grape")]

sorted_data = sorted(data)

print(sorted_data)
```

The output will be:

```plaintext
[(1, 'banana'), (2, 'grape'), (3, 'apple'), (3, 'orange')]
```

Notice that the two elements with the key `3` appear in the same order as they did in the original list.

> Note: `sorted` function when not given any `key` will take the first element of the inner tuples to perform the sorting in ascending order by default.

> Note: Python internally uses different sorting algorithms to perform sorting. In certain scenarios, its interpreter could use the quick sort algorithm which would result in an unstable sort. Read more about why the quick sort is unstable [here](https://saturncloud.io/blog/understanding-quicksort-algorithm-stability/).

## Code Examples In Java

### Stable Sorting

Java provides a built-in sorting method using the `Arrays` class, which uses a stable sorting algorithm. Here's how you can use it:

```java
import java.util.Arrays;
import java.util.Comparator;

class Student {
    String name;
    int score;

    public Student(String name, int score) {
        this.name = name;
        this.score = score;
    }
}

public class StableSortingExample {
    public static void main(String[] args) {
        Student[] students = {
            new Student("Alice", 85),
            new Student("Bob", 90),
            new Student("Carol", 85),
            new Student("David", 78)
        };

        // First, sort by score, then by name
        Arrays.sort(students, Comparator.comparingInt((Student s) -> s.score)
                                       .thenComparing(s -> s.name));

        for (Student student : students) {
            System.out.println(student.name + ": " + student.score);
        }
    }
}
```

The output will be:

```plaintext
David: 78
Alice: 85
Carol: 85
Bob: 90
```

In this example, the `Arrays.sort` method first sorts the students by their scores. Since both Alice and Carol have the same score, their original order is preserved due to the stability of the sorting algorithm.

### Unstable Sorting

To demonstrate an unstable sorting algorithm, we can use the `Collections` class, which provides a method to sort lists:

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class UnstableSortingExample {
    public static void main(String[] args) {
        List<Student> students = new ArrayList<>();
        students.add(new Student("Alice", 85));
        students.add(new Student("Bob", 90));
        students.add(new Student("Carol", 85));
        students.add(new Student("David", 78));

        // Sort by score using an unstable sorting algorithm
        Collections.sort(students, Comparator.comparingInt((Student s) -> s.score));

        for (Student student : students) {
            System.out.println(student.name + ": " + student.score);
        }
    }
}
```

The output could be:

```plaintext
David: 78
Carol: 85
Alice: 85
Bob: 90
```

In this example, the `Collections.sort` method sorts the students by their scores. However, unlike the stable sorting example, the original order of students with the same score (e.g., Alice and Carol) **might not be preserved** in the sorted output.

## Why Stability Matters

The stability of sorting algorithms might seem like a subtle distinction, but it can have significant implications in various applications.

Consider a situation where you have a dataset of individuals of the same age, and you want to sort them by their names. A stable sorting algorithm would ensure that if two people share the same age, their names remain in the same order as they were initially. This could be essential, especially when dealing with historical data or maintaining user preferences.

Here are a few scenarios where stability matters:

1. **Multi-level Sorting:** In cases where you need to sort data by multiple criteria, using a stable sorting algorithm ensures that the order of previous sorts is maintained. This is particularly useful in scenarios like the student records example shown earlier in the article.
    
2. **Preserving Initial Order:** Stable sorting is crucial when dealing with data that already has a meaningful order. For instance, when sorting log entries by timestamp, you'd want to maintain the original order of entries that occurred at the same time.
    
3. **Algorithm Composition:** Stable sorting is often used as a building block in more complex algorithms. If intermediate steps require sorted data, the stability of the sorting algorithm can impact the correctness of the overall process.
    

> Note: An unstable sorting algorithm might be more efficient in terms of time or memory usage. Algorithms like Quicksort and Heapsort are often unstable, but they can offer better performance in certain scenarios. For instance, if stability is not a concern and you're dealing with large datasets, an unstable sorting algorithm might be preferred due to its speed and memory efficiency.

## Takeaway

1. Sorting is not just about arranging elements; it's about maintaining the integrity of the data and respecting the original order when necessary. Stable and unstable sorting algorithms provide different approaches to achieving this goal.
    
2. When maintaining the initial order of equal elements is vital, a stable sorting algorithm is the way to go. However, if performance is a priority and stability is not a concern, an unstable sorting algorithm might offer better efficiency.
    
3. At last, it all comes down to an individual choice and the problem a developer is trying to solve. As a developer, understanding stable and unstable sorting empowers you to choose the right sorting algorithm for the task at hand, ensuring the accuracy and reliability of your applications.
    

---

* Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Data Structures & Algorithms](series/data-structure-algorithms) to more fun topics like [Computer Vision](series/computer-vision).
    
* Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)
    
* Starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)
    
* Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)
    

Till next time!

Namaste 🙏