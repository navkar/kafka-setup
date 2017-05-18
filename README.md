# kafka-setup
Quickly setting up Kafka on your local box

# Step 1 :  Verify Java installation

```bash
navkar$ java -version
java version "1.8.0_131"
Java(TM) SE Runtime Environment (build 1.8.0_131-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)
```
If you don't have the correct version of Java, continue with the next steps.

## Step 1.1 Download JDK tar file

The version is JDK 8u 131 and the file is 'jdk-8u131-linux-x64.tar.gz'
Assuming that the tar file is located in Downloads directory

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

Add the following commands to ~/.bashrc file
NOTE: Please use your due deligence on this, since they vary for every setup

```bash
export JAVA_HOME=/usr/jdk/xxx
export PATH=$PATH:$JAVA_HOME/bin
```

