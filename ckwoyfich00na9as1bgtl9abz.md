---
title: "Big Data Open Source Frameworks"
datePublished: Thu Dec 02 2021 12:48:55 GMT+0000 (Coordinated Universal Time)
cuid: ckwoyfich00na9as1bgtl9abz
slug: big-data-open-source-frameworks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1638445825326/h1sZBUeYa.png
tags: hadoop, big-data, opensource, spark, scala

---

Big Data is a term used to define large scale data sets that are too complex to be manipulated with basic DBMS. Handling Big Data requires sophisticated hardware and software technologies.

Just as open-source has been the primary reason for the Big Data revolution, so has it been at the forefront of developing tools to counter the challenges that we face with the data. And while there are hundreds of popular open-source projects that are focused on Big Data management, in this article, we shall focus on the top three that caught my attention.

We shall discuss the Hadoop framework, the Spark analytics engine and the Kafka framework.

---

### Is Big Data Hard To Handle?

- Almost 90% of the Big Data we produce today is unstructured and there are no predefined models that it adheres to. And there is no quick and easy way to access and analyse unstructured data.

- Not only is Big Data unstructured, but it is also extremely complex. This means traversing through it requires advanced algorithms that are being run on top of grade-A machinery and not everyone can afford that.

- We have multiple sources from which we accrue data and there are no clean ways to integrate disparate data from so many sources.

- With Big Data comes big mistakes. Storing massive and complex data in a secure manner is a really daunting challenge. It is also the need of the hour. Since the beginning of the pandemic, more people are stuck at home with their computers than ever before and cybercrime and data theft have gone up by 400%.

### Open Source Softwares

#### Hadoop

Developed by the Apache Foundation, Hadoop is a framework for Big Data management. It uses distributed systems architecture, which has the ability to store and easily access vast amounts of data.

While there are many different types of Big Data management solution software, what makes Hadoop stands out are 3 components, HDFS, MapReduce and YARN.

- HDFS (Hadoop Distributed File System)

The Hadoop Distributed File System (HDFS) is a powerful and dynamic tool that is efficient at handling Big Data. HDFS breaks down Big Data into blocks and the default size of each block is 128MB. This makes accessing data simple, as the HDFS only has to access the specific block of data that the user is searching for. HDFS is a resilient framework, thanks to its replication methodology. To maintain the accessibility of the data even when one of the distributed system blocks is down, HDFS replicates that block data in a three-fold fashion making it robust to avoid failures or inconsistency.

- MapReduce

Storing and accessing Big Data, with all its complications and difficulties, is still the easy part. The real fun begins when we try to process Big Data. MapReduce is exactly what it sounds like, it maps the data followed by reducing it. MapReduce takes the data as input and splits it into different parts. It then maps each individual component within each part. Then the data is shuffled and sorted into clusters of homogenous data. The data is then reduced by integrating homogenous data and assigning IDs, which give the smaller final output.

- YARN (Yet Another Resource Negotiator)

A Hadoop environment is constrained to the number of resources it has, namely, CPUs, memory units, storage space, etc. But since Hadoop is designed to be able to run multiple processes at the same time, a mechanism for allocating resources is necessary to make sure there are no deadlocks and every task is accomplished in its desired time period. Now, YARN comes into play, when a job requires the resources to run, the application manager sends a request to the node manager to allocate the physical resources. The node manager then sends the resources to the resource manager, which assigns the physical resource to the client process.

#### Spark

While HDFS, MapReduce and YARN are the three major defining components of Hadoop, the Hadoop ecosystem has more tools to offer when it comes to Big Data processing, one such tool is Apache Spark. Spark is one of the few tools in the industry that combines Big Data analytics tools with Machine Learning and AI. Spark is 100 times faster than MapReduce in processing data. Spark computations are done in memory itself, it has the ability to perform both batch processing real-time processing of data. Spark is also comparatively lightweight as most of it is written in [Scala](series/scala).

Following are the Spark components:

- Spark Core
- Spark SQL
- Spark Streaming
- Spark MLib
- Spark GraphX

#### Kafka

Apache Kafka is a framework implementation of a software bus using stream processing. If you break down an information transaction on the Internet, it's essentially nothing but an exchange of information between 2 systems which we sometimes call producers and consumers. Each transaction can be thought of as integration between producer and consumer. In order to simplify complex integrations, Kafka acts as a broker between producer and consumer, which can be well integrated with Hadoop and Spark.

Kafka consists of Brokers and a Zookeeper.

- Broker

A broker is a Kafka server that runs in a Kafka cluster. Each broker divides a unique transaction between the producer and consumer into a topic. Now, these topics within the broker are used to consume and broadcast the messages in an asynchronous fashion.

- Zookeeper

In order to define topics and keep a metadata record of all the topics defined in the cluster, Kafka uses Zookeeper which is a replicated distributed log with a file system API built on top. It keeps a record of all the topics within all the nodes and also keeps track of which nodes are down and which are up and running.

### Where To Go From Here?

The tools and frameworks discussed in this article are a high-level overview of the innovation and efforts taking place in the Big Data management industry. There are many more open source tools and frameworks that can be learned and used for Big Data management.

Google all the available resources and check which fits your Big Data management need to the point and become a Big Data Engineer one step at a time.

Books to check out more on Big Data Engineering:

- [Big Data Simplified](https://amzn.to/3DbHhYN)
- [Big Data Analytics, Introduction to Hadoop, Spark, and Machine-Learning](https://amzn.to/3phG2CF)
- [Big Data and Analytics](https://amzn.to/3rvFcoE)

---

- Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Python](series/python) to [Computer Vision](series/computer-vision) to [Scala](series/scala).

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏