# Hadoop WordCount Project

This project implements a simple WordCount application using Apache Hadoop. The WordCount program reads a text file, processes it in parallel across multiple nodes in a Hadoop cluster, and counts the occurrences of each word in the input file.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Running the Application](#running-the-application)
- [Docker Setup Instructions](#Docker-Setup-Instructions)

## Features

- Distributed processing of large text files
- Count the frequency of words
- Built with Java and Apache Hadoop

## Technologies Used

- Java 8
- Apache Hadoop 2.7.2
- Maven for project management

## Getting Started

To get started with this project, you will need to have Docker and Hadoop set up in your local environment.

### Prerequisites

- Docker installed
- Basic understanding of Hadoop and MapReduce

### Clone the Repository

```bash
git clone https://github.com/abderrahmane-stack/Hadoop-WordCount.git
```

## Running the Application

### Build the Project
Make sure to build your project using Maven:
```bash
mvn clean install
```
Run the WordCount Job: Start your Hadoop cluster and run the WordCount job:

```bash
hadoop jar wordcount-1.jar tp1.WordCount input output
```
View the Output: Check the results of the WordCount job:

```bash
hadoop fs -cat output/part-r-00000
```
## Docker Setup Instructions

1. **Download the Docker image uploaded on DockerHub:**
   ```bash
   docker pull liliasfaxi/spark-hadoop:hv-2.7.2
   ```
2. **Create the three containers from the downloaded image:**
   To do this: 2.1. Create a network that will connect the three containers:

```bash
docker network create --driver=bridge hadoop
```
2.2. Create and run the three containers 
```bash
docker run -itd --net=hadoop -p 50070:50070 -p 8088:8088  -p 16010:16010 \
--name hadoop-master --hostname hadoop-master \
liliasfaxi/spark-hadoop:hv-2.7.2

docker run -itd -p 8040:8042 --net=hadoop \
--name hadoop-slave1 --hostname hadoop-slave1 \
liliasfaxi/spark-hadoop:hv-2.7.2

docker run -itd -p 8041:8042 --net=hadoop \
--name hadoop-slave2 --hostname hadoop-slave2 \
liliasfaxi/spark-hadoop:hv-2.7.2
```
