# HOW TO Quickly Setup Kafka on your MAC OS and get it to work
Quickly setting up Kafka on your local box

# Step 1 : Verify Java installation

```bash
navkar$ java -version
java version "1.8.0_131"
Java(TM) SE Runtime Environment (build 1.8.0_131-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)
```
If you don't have the correct version of Java, continue with the next steps.

## Step 1.1 Download JDK tar file

The version is JDK 8u 131 and the file is 'jdk-8u131-linux-x64.tar.gz'.

Assuming that the tar file is located in `Downloads` directory

```bash
navkar$ cd ~/Downloads
```

## Step 1.2 Extract files

```bash
navkar$ sudo mkdir /opt/jdk
navkar$ cd /opt/jdk
navkar$ tar -zxf ~/Downloads/jdk-8u131-linux-x64.tar.gz
```

## Step 1.3 Set JAVA HOME

Add the following commands to ~/.bashrc file.

NOTE: Please use your due deligence on this, since they vary for every setup.

```bash
export JAVA_HOME=/usr/jdk/xxx
export PATH=$PATH:$JAVA_HOME/bin
```
# Step 2 : Setup Zookeeper

## Step 2.1 Download Zookeeper

Download the tar file from http://zookeeper.apache.org/releases.html

## Step 2.2 Extract tar file

```bash
navkar$ cd /opt
navkar$ tar -zxf ~/Downloads/zookeeper-3.4.10.tar.gz
navkar$ cd zookeeper-3.4.10
navkar$ mkdir data
```

## Step 2.3 Create configuration file

Create configuration file named 'conf/zoo.cfg' using the command vi 'conf/zoo.cfg'.


```bash
navkar$ cd /opt/zookeeper-3.4.10/conf
navkar$ pwd
/opt/zookeeper-3.4.10/conf
navkar$ cat zoo.cfg 
tickTime=2000
dataDir=/opt/zookeeper-3.4.10/data
clientPort=2181
initLimit=5
syncLimit=2
```

## Step 2.4 Start Zookeeper Server 

```bash
navkar$ sudo bin/zkServer.sh start
Password:
ZooKeeper JMX enabled by default
Using config: /opt/zookeeper-3.4.10/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED
navkar$ jps
3626 Jps
```

## Step 2.5 Start CLI to talk to Zookeeper Server

```bash
navkar$ pwd
/opt/zookeeper-3.4.10
navkar$ bin/zkCli.sh
Connecting to localhost:2181
2017-05-18 10:11:54,912 [myid:] - INFO  [main:Environment@100] - Client environment:zookeeper.version=3.4.10-39d3a4f269333c922ed3db283be479f9deacaa0f, built on 03/23/2017 10:13 GMT
2017-05-18 10:11:54,917 [myid:] - INFO  [main:Environment@100] - Client environment:host.name=172.16.2.50
2017-05-18 10:11:54,918 [myid:] - INFO  [main:Environment@100] - Client environment:java.version=1.8.0_131
2017-05-18 10:11:54,920 [myid:] - INFO  [main:Environment@100] - Client environment:java.vendor=Oracle Corporation
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:java.home=/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home/jre
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:java.class.path=/opt/zookeeper-3.4.10/bin/../build/classes:/opt/zookeeper-3.4.10/bin/../build/lib/*.jar:/opt/zookeeper-3.4.10/bin/../lib/slf4j-log4j12-1.6.1.jar:/opt/zookeeper-3.4.10/bin/../lib/slf4j-api-1.6.1.jar:/opt/zookeeper-3.4.10/bin/../lib/netty-3.10.5.Final.jar:/opt/zookeeper-3.4.10/bin/../lib/log4j-1.2.16.jar:/opt/zookeeper-3.4.10/bin/../lib/jline-0.9.94.jar:/opt/zookeeper-3.4.10/bin/../zookeeper-3.4.10.jar:/opt/zookeeper-3.4.10/bin/../src/java/lib/*.jar:/opt/zookeeper-3.4.10/bin/../conf:
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:java.library.path=/Users/navkar/Library/Java/Extensions:/Library/Java/Extensions:/Network/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:.
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:java.io.tmpdir=/var/folders/r3/95_6x1tx0q5fzhc3vm8hqp900000gn/T/
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:java.compiler=<NA>
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:os.name=Mac OS X
2017-05-18 10:11:54,921 [myid:] - INFO  [main:Environment@100] - Client environment:os.arch=x86_64
2017-05-18 10:11:54,922 [myid:] - INFO  [main:Environment@100] - Client environment:os.version=10.12.4
2017-05-18 10:11:54,922 [myid:] - INFO  [main:Environment@100] - Client environment:user.name=navkar
2017-05-18 10:11:54,922 [myid:] - INFO  [main:Environment@100] - Client environment:user.home=/Users/navkar
2017-05-18 10:11:54,922 [myid:] - INFO  [main:Environment@100] - Client environment:user.dir=/opt/zookeeper-3.4.10
2017-05-18 10:11:54,923 [myid:] - INFO  [main:ZooKeeper@438] - Initiating client connection, connectString=localhost:2181 sessionTimeout=30000 watcher=org.apache.zookeeper.ZooKeeperMain$MyWatcher@446cdf90
Welcome to ZooKeeper!
2017-05-18 10:11:54,949 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@1032] - Opening socket connection to server localhost/0:0:0:0:0:0:0:1:2181. Will not attempt to authenticate using SASL (unknown error)
JLine support is enabled
2017-05-18 10:11:55,039 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@876] - Socket connection established to localhost/0:0:0:0:0:0:0:1:2181, initiating session
2017-05-18 10:11:55,050 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@1299] - Session establishment complete on server localhost/0:0:0:0:0:0:0:1:2181, sessionid = 0x15c1c518ae90009, negotiated timeout = 30000

WATCHER::

WatchedEvent state:SyncConnected type:None path:null
[zk: localhost:2181(CONNECTED) 0] 
```

## Step 2.6 Stop Zookeeper 

```bash
navkar$ pwd
/opt/zookeeper-3.4.10
navkar$ bin/zkServer.sh stop
```

# Step 3 : Apache Kafka Setup

Lets install Kafka on the localbox

## Step 3.1 Download Kafka

File : kafka_2.12-0.10.2.1.tgz

## Step 3.2 Extract the tar file

```bash
navkar$ cd /opt
navkar$ tar -zxf ~/Downloads/kafka_2.12-0.10.2.1.tgz
navkar$ cd kafka_2.12-0.10.2.1
```

## Step 3.3 Start Server

```bash
navkar$ bin/kaka-server-start.sh config/server.properties
```

## Step 3.4 Stop Server

```bash
navkar$ bin/kaka-server-stop.sh config/server.properties
```

# Step 4 : Getting everything to work together

## Step 4.1 Start Zookeeper

```bash
navkar$ sudo bin/zookeeper-server-start.sh config/zookeeper.properties
```

## Step 4.2 Start Kafka broker

```bash
navkar$ sudo bin/kafka-server-start.sh config/server.properties
```

## Step 4.3 Creating a Kafka Topic

```bash
navkar$ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic outgoing-messages
Created topic "outgoing-messages".
```

## Step 4.4 Getting a List of topics

```bash
navkar$ bin/kafka-topics.sh --list --zookeeper localhost:2181
outgoing-messages
welcome
```

## Step 4.5 Start producer to send messages

This command will create a CLI for sending messages through command line. Every line is interpreted as a message.

```bash
navkar$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic welcome
```

## Step 4.6 Start consumer to receive messages

This command will create a CLI for receiving messages through command line.

```bash
navkar$ bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic welcome --from-beginning 
Using the ConsoleConsumer with old consumer is deprecated and will be removed in a future major release. Consider using the new consumer by passing [bootstrap-server] instead of [zookeeper].
```
## Step 4.7 Java Process Status (JPS) command

```bash
navkar$ pwd
/opt/zookeeper-3.4.10
navkar$ jps
7025 Jps
6278 ConsoleConsumer
5018 ConsoleProducer
navkar$ jps -v
6278 ConsoleConsumer -Xmx512M -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:InitiatingHeapOccupancyPercent=35 -XX:+DisableExplicitGC -Djava.awt.headless=true -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Dkafka.logs.dir=/opt/kafka_2.12-0.10.2.1/bin/../logs -Dlog4j.configuration=file:/opt/kafka_2.12-0.10.2.1/bin/../config/tools-log4j.properties
7047 Jps -Dapplication.home=/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home -Xms8m
5018 ConsoleProducer -Xmx512M -XX:+UseG1GC -XX:MaxGCPauseMillis=20 -XX:InitiatingHeapOccupancyPercent=35 -XX:+DisableExplicitGC -Djava.awt.headless=true -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Dkafka.logs.dir=/opt/kafka_2.12-0.10.2.1/bin/../logs -Dlog4j.configuration=file:/opt/kafka_2.12-0.10.2.1/bin/../config/tools-log4j.properties

```







