## Python De-Prioritise Performance ?

Python deprioritize the performance use-case, so does the developers using Python !
Although, there is one group that suffers because of this, the one that uses computing on data, the data scientists !!

But due to easy adaptability of learning/implementing python programmes, it gives no other choice to them but to learn python (mostly because of their non-programming background).

Hence, it becomes necessary to look out for options to have more performance oriented way to use python.

Here comes numerical programming libraries like numpy, scipy, tensorflow etc.

As per Brain Kihoon Lee, the magic for their enhanced performance lies in their PyObject use case.

“A NumPy array can hold many raw data within a single PyObject box, provided that all of those data are of the same type (int32, float32, etc.). By doing this, NumPy amortizes the cost of boxing over multiple data”

Such a simple yet complex strategy numpy adopted to increase performance by 30X !!

Many more interesting things are discussed in article titled “Data-oriented Programming in Python” by Brain Kihoon Lee.

One such thing is about pointer latency and how it affects the performance of Python code.

Link to article:

[Data Oriented Python](https://www.moderndescartes.com/essays/data_oriented_python/)

Did you like the article ? What are your views on it ?

---

Just starting you Open Source Journey ? Don't forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Till next time !

Namaste 🙏