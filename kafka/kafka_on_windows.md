# Set up Kafka on a Windows Machine

Refer to this page for quick start: [https://kafka.apache.org/quickstart](https://kafka.apache.org/quickstart). Although this tutorial is for Linux machines, but the steps are the same for Windows machines.

## Install Kafka

Requirements:
- Java
- Zookeeper (you can install it from Kafka)

1. First download the latest version of [Kafka](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.6.0/kafka_2.13-2.6.0.tgz). Make sure you download the <span style="color:green">binary files</span>, __NOT__ the source files. Then unzip the files and move to the folder you want, e.g. C: Drive.

2. Change Zookeeper and Kafka configurations. Assume unzipped Kafka files are in C Drive:
    - Go to your Kafka installation directory: `C:\kafka_{version_number}\`
    - Open `config\zookeeper.properties`
    - Find and edit `dataDir=/tmp/zookeeper` to `C:/kafka_{version_number}/zookeeper`. You can customize the path as long as it's a valid path on your machine.
    - Open `config\server.properties`
    - Find and edit `log.dirs=/tmp/kafka-logs` to `log.dirs=C:/kafka_{version_number}/kafka-logs`. You can customize this path too.

3. Now you're ready to go.


## How to use Kafka

1. Start Zookeeper server. Open a command prompt. Navigate to the installation folder: `C:\kafka_{version_number}\`
```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

2. Start Kafka server. Open another command prompt. Navigate to the installation folder:
```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

3. Create a topic. Open a new command prompt. Navigate to the bin folder: `C:\kafka_{version_number}\bin\windows`
```
kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
```
- List topics:
```
kafka-topics.bat --list --zookeeper localhost:2181
```
- Describe a topic:
```
kafka-topics.bat --describe --zookeeper localhost:2181 --topic [Topic Name]
```
- Delete a topic:
```
kafka-run-class.bat kafka.admin.TopicCommand --delete --topic [topic_to_delete] --zookeeper localhost:2181
```

4. Start a Kafka producer. Open a new command prompt. Navigate to the bin folder:
```
kafka-console-producer.bat --broker-list localhost:9092 --topic test
```

5. Start a Kafka consumer. Open a new command prompt. Navigate to the bin folder:
```
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test
```

Now you can send messages from the producer. The consumer will automatically receive the published messages.


__NOTE__:
1. You can terminate the Kafka server and Zookeeper server using `CTRL + C` 
2. If it's on a linux machine, we the `*.sh` scripts in the `bin` folder directly. The steps are exactly the same.




