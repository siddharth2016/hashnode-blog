---
title: "Diving into Docker: A Comprehensive Guide for Beginners"
seoDescription: "Learn Docker. Docker basics for beginners. Docker in 9 steps. Kubernetes and Docker Swarm. Containerize Spring Boot App."
datePublished: Tue Sep 05 2023 14:42:25 GMT+0000 (Coordinated Universal Time)
cuid: clm6f6dcu000009jw7fny56x8
slug: diving-into-docker-a-comprehensive-guide-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693924772547/88f89474-06b5-4933-bbfe-c930e11b1387.png
tags: docker, java, kubernetes, containers, springboot

---

Docker has revolutionized the way we build, ship, and run applications. It's a containerization platform that enables developers to package applications and their dependencies into isolated containers. These containers can run consistently across different environments, from development to production, making it easier to manage and scale applications.

In this article, we will try to understand its basics while diving deep enough so that you will be able to start working with Docker as a software engineering professional.

---

## Installing Docker

Before we dive into Docker, we need to install it on our system. Docker provides installation packages for various operating systems, including Windows, macOS, and Linux. You can download the appropriate package for your OS from the official Docker [website](https://docs.docker.com/engine/install/).

Once Docker is installed, open a terminal or command prompt and run the following command to verify the installation:

```bash
docker --version
```

If you see the Docker version information like the below image, you're ready to move on to the next steps.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693923810337/c96baee7-9f87-4adc-ad5f-303d5bc81820.png align="left")

## Running Your First Docker Container

Let's start by running a simple Docker container. Docker containers are instances of Docker images, which are pre-packaged, portable environments. We'll use the official Docker image for the "hello-world" application.

Open your terminal and run the following command:

```bash
docker run hello-world
```

Docker will download the "hello-world" image if it's not already available and run it. You'll see a message indicating that your installation appears to be working correctly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693923837031/c2d7a170-f534-4b4d-b274-b824c5075867.png align="left")

In the above image, you'll see that since `hello-world` Docker image was not present locally, Docker downloaded it and displayed additional information on what happened behind the scenes.

> Note: See `Docker daemon`, search for this on the internet, doing so, you will get to learn about the internals of Docker as a bonus.

## Understanding Docker Images

Docker images are the building blocks of containers. They contain everything needed to run an application, including the code, runtime, libraries, and system tools. Images are stored in a Docker registry, which is like a repository for Docker images.

You can search for Docker images on the [Docker Hub](https://hub.docker.com/) (Docker Registry) or create your own custom images. Let's create a simple Java application and package it into a Docker image.

> Note: For some developers, this may seem like a lot of information. Try to code along with the article at your own pace and whenever in doubt, just search it over the internet!

```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Docker!");
    }
}
```

To create a Docker image for this Java application, create a `Dockerfile` in the same directory with the following content:

> Note: To create a Dockerfile, if you are a terminal enthusiast then you can do something like `touch Dockerfile`. Make sure you are in the same directory as `HelloWorld.java` file.

```Dockerfile
# Use an official Java runtime as a parent image
FROM openjdk:8-jdk

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Compile the Java code
RUN javac HelloWorld.java

# Run the application
CMD ["java", "HelloWorld"]
```

Now, build the Docker image using the `docker build` command:

```bash
docker build -t hello-java .
```

The `-t` flag allows you to tag the image with a name ("hello-java" in this case). You can replace "hello-java" with any name you prefer.

> Note: I have added comments in `Dockerfile` itself, it is pretty straight forward, just give it some time and you'll understand it easily. Note the `COPY` command, you need to copy the files inside your `Dockerfile`. When you use `docker build .`, then the current directory files are available to you as context but they are not inside image.

## Running Your Custom Docker Image

Now that we have created a custom Docker image, let's run it as a container:

```bash
docker run hello-java
```

The "Hello, Docker!" message is printed in the terminal, indicating that the Java application is running inside the Docker container.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693924104117/c52c960f-efc7-43b3-be7b-7dc4b3f666b1.png align="center")

## Docker Containers Are Stateless

One important concept to understand is that Docker containers are stateless by default. This means that any changes made inside a container are ephemeral and do not persist after the container exits. To demonstrate this, let's modify our Java application to accept user input and see how the container behaves.

```java
// HelloWorld.java (Updated)
import java.util.Scanner;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = scanner.nextLine();
        System.out.println("Hello, " + name + "!");
    }
}
```

Now, rebuild the Docker image and run it again:

```bash
docker build -t hello-java .
docker run -it hello-java
```

You'll notice that the container stops after taking user input and displaying the message. This is because containers are designed to be disposable and do not retain state between runs.

You can see the result below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693924134885/66891ba7-edc9-42b3-a8dc-65dce59c4f8a.png align="left")

## Docker Volumes for Data Persistence

To persist data between container runs, you can use Docker volumes. Volumes are a way to share data between the host system and containers or between containers. Let's modify our Java application to write user input to a file and use a Docker volume to persist the data.

```java
// HelloWorld.java (Updated)
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = scanner.nextLine();

        try {
            FileWriter writer = new FileWriter("/app/output.txt");
            writer.write("Hello, " + name + "!");
            writer.close();
            System.out.println("Data written to output.txt");
        } catch (IOException e) {
            System.err.println("Error writing to file: " + e.getMessage());
        }
    }
}
```

Rebuild the Docker image and run it, this time with a Docker volume:

```bash
docker build -t hello-java .
docker run -it -v $(pwd)/data:/app/data hello-java
```

The `-v` flag is used to mount a host directory (`./data`) as a volume inside the container. Now, the data is written to `output.txt` will be persisted on your host system in the `./data` directory.

That's a lot of information! Let's move on to something more fun.

## Dockerizing a Java Web Application

Docker is not limited to running simple command-line applications. It can also containerize web applications. Let's take a Java-based web application as an example. We'll use Spring Boot, a popular Java framework, to create a simple REST API.

**Example Java Web Application (HelloAPI.java):**

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class HelloAPI {
    @GetMapping("/")
    public String hello() {
        return "Hello, Dockerized API!";
    }

    public static void main(String[] args) {
        SpringApplication.run(HelloAPI.class, args);
    }
}
```

To Dockerize this application, create a Dockerfile similar to the one we used earlier but with a few modifications:

**Dockerfile for Java Web Application:**

```Dockerfile
# Use an official OpenJDK runtime as a parent image
FROM openjdk:8-jdk

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Build the Java application
RUN ./mvnw package -DskipTests

# Expose port 8080 for the Spring Boot application
EXPOSE 8080

# Run the Spring Boot application
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]
```

Now, build the Docker image for your Java web application using the same `docker build` command as before:

```bash
docker build -t hello-api .
```

Once the image is built, you can run a container from it, and your Spring Boot application will be accessible at `http://localhost:8080` in your web browser.

## Docker Registry and Pushing Images

So far, we've been working with local Docker images. You can use Docker registries to share your Docker images with others or deploy them to remote servers. Docker Hub is a popular public registry, but you can also set up your private registry.

To push your custom Docker image to Docker Hub, follow these steps:

1. Log in to Docker Hub using the `docker login` command.
    

```bash
docker login
```

1. Tag your image with your Docker Hub username and repository name.
    

```bash
docker tag hello-java <your-docker-hub-username>/hello-java
```

1. Push the image to Docker Hub.
    

```bash
docker push <your-docker-hub-username>/hello-java
```

Now, your custom Docker image is available on Docker Hub and can be pulled by others.

## Container Orchestration with Docker Swarm and Kubernetes

Docker can be used for container orchestration, which manages multiple containers across a cluster of machines. Two popular tools for container orchestration are Docker Swarm and Kubernetes.

* **Docker Swarm**: Docker Swarm is a built-in orchestration solution for Docker. It allows you to create and manage a swarm of Docker nodes (machines) and deploy services to them. Docker Swarm is easy to set up and is suitable for smaller deployments.
    
* **Kubernetes**: Kubernetes is a powerful and widely adopted container orchestration platform. It provides advanced features for managing containerized applications at scale. Kubernetes has a steeper learning curve than Docker Swarm but offers more flexibility and scalability.
    

To get started with Docker Swarm or Kubernetes, you can refer to their official documentation and tutorials.

## Takeaways

Docker is a powerful tool that simplifies application development, deployment, and scaling by using containers. In this article, we've covered the essential steps to get started with Docker, with these fundamental concepts and practical examples, you can begin harnessing the full potential of Docker for your Java development projects. Docker's ability to create consistent and isolated environments will streamline your development process and make your applications more portable and maintainable. Happy Dockerizing!

---

* Make sure to follow me to get regular updates or subscribe so that you never miss my upcoming articles, ranging from [Data Structures & Algorithms](series/data-structure-algorithms) to more fun topics like [Computer Vision](series/computer-vision).
    
* Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)
    
* Starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)
    
* Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)
    

Till next time!

Namaste 🙏