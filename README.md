# kafka-setup
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

## Step 3.1 Download Kafka

## Step 3.2 Extract the tar file

## Step 3.3 Start Server

## Step 3.4 Stop Server







