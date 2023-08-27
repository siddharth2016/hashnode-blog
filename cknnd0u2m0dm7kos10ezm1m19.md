---
title: "Orange: The No-Code Tool for Machine Learning"
seoDescription: "This article introduces Orange, a visual programming software package. Let's see a simple demo of how we can use Orange to do machine learning tasks."
datePublished: Sun Apr 18 2021 16:04:31 GMT+0000 (Coordinated Universal Time)
cuid: cknnd0u2m0dm7kos10ezm1m19
slug: orange-the-no-code-tool-for-machine-learning
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1618761120714/uV4vgHWVP.png
tags: artificial-intelligence, python, tools, data-science, machine-learning

---

The demand for machine learning engineers and data scientists has increased exponentially over the years. This is justified because machine learning is being applied in almost every field to solve real-world problems.

There are very good programming languages like Python and R to acquire the skills required for machine learning engineers and data scientists. But people need to spend a good amount of time learning these programming languages before practising data analysis techniques.

Machine learning engineers and data scientists need to apply different visualisation techniques to understand the data and test different models to get accurate results. In this situation, having a GUI based tool that needs minimum programming can lead to good productivity.

This article introduces Orange, a visual programming software package released under GPL, and focused on components for data visualisation, machine learning, data mining, and analysis of data.

It features a visual programming front-end for explorative rapid qualitative data analysis and interactive data visualisation. The developers of Orange at the University of Ljubljana in Slovenia built the core components in C++ with wrappers in Python, which are available on GitHub. Orange is available for Mac, Linux and Windows users.

Let's see a simple demo of how we can use Orange to do machine learning tasks. Following steps are carried on MacOS, but they remain the same for Linux and Windows.

---

### Prerequisites - All You Need

We are going to work in a virtual environment for this demo (considering we have python already installed, if not please check [this](https://realpython.com/installing-python/)). To create this environment follow the below steps in the terminal (make sure you are in a project folder and not in Desktop or Documents, just to avoid any other issues it might create):

```python
~ % mkdir orange_proj
~ % cd orange_proj
orange_proj ~ % python3 -m venv venv
```

This creates a virtual environment in our working directory `orange_proj` if we notice there is a folder created named `venv` in the directory.

To activate this `venv`, we can do the following in the terminal:

```shell
orange_proj ~ % source venv/bin/activate
(venv) orange_proj ~ %
```

`(venv)` prefix in terminal means that this environment is active for us to do the work. Now, nothing outside of it will be affected and libraries will only be installed in this environment.

So moving on, first we upgrade the pip, setuptools and wheel packages in python's virtual environment (to avoid any unwanted errors).

```shell
(venv) orange_proj ~ % pip install --upgrade pip setuptools wheel
```

When you run the above command, it upgrades pip, setuptools and wheel in one go. Let's install Orange now.

```shell
(venv) orange_proj ~ % pip install orange3
```

After you hit enter on that, you should have orange installed in your virtual environment, if you faced any issues/errors please reach out to me in the comments.

Let's move on to the fun part now!

---

### Starting Orange

Now, in the same virtual environment where we just installed Orange, we will type the following to launch Orange GUI.

```shell
(venv) orange_proj ~ % orange-canvas
```

After you hit enter it should open something like this:

![orange1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761157337/uTnxN61Kh.png)

It offers a very simple GUI and is divided into 3 sections - categories, widgets and canvas. By default Orange comes with 5 categories called Data, Visualize, Model, Evaluate and Unsupervised.

To perform any kind of task with Orange, we need to construct a workflow by dragging widgets onto the canvas from the respective categories and connecting them by drawing a line from the transmitting widget to the receiving widget. These lines can be connected through an arc on sides of these widgets, the left arc represents the input and the right arc represents the output from that widget.

Let's build a classifier using Orange.

### Load Dataset in Orange

Open Orange and drag the `File` widget icon under the `Data` category and place it on canvas wherever you want.

![orange2.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761188080/IaD1RWZ3U.gif)

Data category widgets offer multiple options to load the data into Orange. It is not possible to introduce all those options in this article (better to take that as a learning activity after completing this article).

Double click on the `File` widget on canvas to load the dataset.

![orange3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761209338/-QeDGd21n.png)

We are going to work with the basic, most loved dataset, Iris Dataset, that is by default selected, but if it is not then you can manually select it. The Iris dataset contains 150 samples with 5 features. Any feature can be skipped by clicking on the role and selecting skip. We can make any feature act as a target variable for predictions. Here, we make `Species` a target. Now simply close the window without worrying about anything else!

### Explore Dataset in Orange

![orange4.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1618764205794/JHQ8OPey9.gif)

Now select and drag the `Data Table` widget from the `Data` category into the canvas and connect it with the `File` widget. Double click `Data Table` to view the spreadsheet output of the Iris dataset.

![orange5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761264599/CtWxEppHL.png)

Let's plot a scatter plot for this dataset. Drag the `Scatter Plot` widget from the `Visualize` category, place it on the canvas and connect it with the `File` widget. Double click on the `Scatter Plot` widget to get the samples plotted on the graph. 

![orange6.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1618764223654/0AFLpzOVw.gif)

### Training And Testing Set in Orange

Machine learning classifiers take known samples (training data) and predict the output for any new unknown sample. At the outset, the machine learning classifier looks like a black box that takes some input sample and predicts the corresponding output label.

So let's prepare the training dataset for Iris data. Of the 150 samples, we will take 147 as training samples and 3 as testing data. To achieve that do the following:

1. Double click on the `Data Table` on the canvas and select all the samples from the spreadsheet (Ctrl + A or Cmd + A).
2. Now, hold the `Ctrl` or `Cmd` key and deselect rows `50th`, `100th` and `150th`. If you see at the bottom of the spreadsheet you will know that we have 147 rows selected out of 150, this will act as our training dataset. This would look something like this:

![orange7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761325315/UMYy6nkdp.png)

3. Now, leave it open and go back to the canvas. Drag another `Data Table` from the `Data` category and put it on the canvas and connect it with `File`. The new data table would be automatically be named as `Data Table (1)`, leave it as it is.

![orange8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761349701/mUgk-rEl9.png)

4. Double click `Data Table (1)` and you would be able to see a new spreadsheet of the Iris dataset. Now, here we will select our testing data. Select only those rows that we left for training, rows `50th`, `100th` and `150th`. If you see at the bottom of the spreadsheet you will know that we have 3 rows selected out of 150 rows. This will look something like this:

![orange9.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761366071/KzheX0L_y.png)

5. Leave it open and move back to the canvas. Now we will do the model training and predictions on our training and testing dataset respectively.

### Training and Predictions in Orange

Make sure we are on canvas window, with 2 data table spreadsheets open in the background (what we just did above).

Follow the below steps to perform training and prediction on the Iris dataset:

1. Select and drag the `SVM` widget from the `Model` category to the canvas.
2. Connect the `Data Table` output to the `SVM` widget. It would look something like this.

![orange10.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761413183/UALCdCui7.png)

3. Next, drag and drop `Predictions` from the `Evaluate` category to the canvas.
4. Connect the `SVM` output/right arc to `Predictions` input/left arc. It would look something like this:

![orange11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761439580/gXzJZWHFj.png)

5. Connect the `Data Table (1)` widget (our testing sample) to the `Predictions` widget. Double click on the `Predictions` widget and you will see how our training model did on the test dataset (on 3 rows that we selected).

![orange12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761455945/wcMvyIsyB.png)

Now, let's add 1 more model to the existing diagram and see how we can compare the results of 2 different models.

### Comparing Results of Models in Orange

Follow the below steps to compare several models at once:

1. Drag and drop the `KNN` widget from the `Model` category to the canvas and connect the `Data Table` widget with its input arc and connect to the `Predictions` widget from its output arc. 

![orange13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761483126/kTRwqSmvZ.png)

2. Well, that's it, now we have 2 models connected to `Data Table` (training set) and both pointing to the `Predictions`. Double click `Predictions` widget and we can see and compare outputs of 2 models on the same dataset.

![orange14.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761501691/dDiWeJ9bf.png)

3. Additionally we can also include a confusion matrix. Drag and drop the `Confusion Matrix` widget from the `Evaluate` category and connect the `Predictions` output arc to its input arc.

![orange15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761524966/3qTWJ5IgJ.png)

4. Double click on the `Confusion Matrix` widget to see and compare the results of `SVM` and `KNN` widget models.

![orange16.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618761551326/eLnIxGtd3.png)

### What Can Be Done From Here?

Well, these were the most basics of operations you can do to achieve a functional machine learning model and analyse the dataset. You can add more models and evaluate different widgets from the `Evaluate` category.

Using the Orange tool, you can easily apply different machine learning classifiers to the dataset and make a comparative study to find out the best classifier for the given dataset.

Orange can be used for unsupervised learning, image analytics, time series analysis, data mining, bioinformatics, etc.

Go and try your hands on different functionalities it offers and how it can reduce the task of writing code to no-code for simple yet complex machine learning tasks.

Explore their official documentation for more tutorials and see how it fits your needs. Visit [here](https://orange3.readthedocs.io/projects/orange-development/en/latest/tutorial.html).

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Need inspiration or a different perspective on the Python projects or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏