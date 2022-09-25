### Presentation Video

https://web.microsoftstream.com/video/7652ca2f-760f-4355-8b03-a8b0c0274cb5



# cs523
Spark Streaming project
# Setup and Installation

### Requirments

install Virtual Box and you can use any linux operating system, in this example i used lubuntu

- install java
``` bash
sudo apt install openjdk-8-jdk -y
```

## Installing Kafka

#### Download and extract

``` bash
wget http://apache.claz.org/kafka/2.2.0/kafka_2.12-2.2.0.tgz
tar -xvf kafka_2.12-2.2.0.tgz
```

#### Running Kafka & Zookeeper

Start zookeeper

```bash
~$ bin/zookeeper-server-start.sh config/zookeeper.properties
```

then start Kafka broker
```bash
bin/kafka-server-start.sh config/server.properties
```

and dont forget to create a new tpoic for kafka to use

list all tpoics 
```bash
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

create a new one
```bash
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic tweets
```

finally install the kafka package for python
```bash
pip3 install kakfa-python 
```

## Install hadoop

```bash
wget https://archive.apache.org/dist/hadoop/common/hadoop-2.8.5/hadoop-2.8.5.tar.gz
tar -xvf hadoop-2.8.5.tar.gz
```

install ssh

```bash
apt install openssh-server openssh-client
```

start hadoop cluster

```bash
hdfs namenode -format
start-dfs.sh
```

test it

```bash
hadoop fs -ls /
```

## Install Hive

```bash
wget http://archive.apache.org/dist/hive/hive-2.3.5/apache-hive-2.3.5-bin.tar.gz
tar -xvf apache-hive-2.3.5-bin.tar.gz
```

test it 
```bash
hive --version
```


create database

```bash
schematool -initSchema -dbType derby
```

start the meta store

```bash
hive --services metastore
```


## install spark

download from a webbrowser

https://spark.apache.org/downloads.html

```bash
tar -xvf Downloads/spark-2.4.3-bin-hadoop2.7.tgz
```

install scala

```bash
sudo apt install scala -y
```

install python lib

```bash
pip3 install pyspark
```

try it

```bash
pyspark
```


## Runnnning the scripts file

running the stream script

```bash
./fake_tweet_stream.py
```

running the transformer script

```bash
spark-submit --jars spark-streaming-kafka-0-8-assembly_2.11-2.4.3.jar transformer.py
```

