# Hadoop Word Count Example with Docker

This repository provides instructions on setting up and running a simple Hadoop word count example using Docker.

## Prerequisites

- Docker installed on your system.

## Docker Setup

Clone this repository to your local machine:

```bash
git clone https://github.com/your-username/hadoop-wordcount-docker.git
```
Navigate to the cloned repository:

```bash
cd hadoop-wordcount-docker
```
Build the Docker image:

```bash
Build the Docker image:
```

##Running the wordcount example

Start a Docker container from the image you built:

```bash
docker run -it --name hadoop-container hadoop-wordcount
```

Inside the container, switch to the 'hadoop' user:
```bash
su hadoop
```

Configurate SSH service
```bash
ssh-keygen -t rsa -P ""
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
service ssh start
```

Once SSH is set up, you can start HDFS and YARN:

```bash
$HADOOP_HOME/sbin/start-dfs.sh
$HADOOP_HOME/sbin/start-yarn.sh
```

Create an input file for the word count:

```bash
echo "Hello world, this is a simple word count example with Hadoop" > input.txt
```

Copy the input file to HDFS:

```bash
hdfs dfs -copyFromLocal input.txt /user/hadoop/input
```

Run the Hadoop word count job:

```bash
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.1.jar wordcount /user/hadoop/input /user/hadoop/output
```

View the word count results:

```bash
hdfs dfs -cat /user/hadoop/output/part-r-00000
```

Result:

<img width="473" alt="Capture" src="https://github.com/aybstain/hadoop-single-node/assets/103702856/56a074a8-09e3-468f-8f10-209168aafe0c">

## Custom Configuration

If you need to customize Hadoop configuration, you can modify the hdfs-site.xml and core-site.xml files in this repository.



