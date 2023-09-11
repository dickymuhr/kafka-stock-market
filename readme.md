# Kafka Stock Market Project
Project based on Darshil Parmar Youtube Video [Stock Market Real-Time Data Analysis Using Kafka](https://www.youtube.com/watch?v=KerNf0NANMo)

What is Kafka? Learn here [Kafka Visualizaiton](https://softwaremill.com/kafka-visualisation/)
# Architechture

![Alt text](architechture.jpg "Architechture")
Image from [here](https://github.com/darshilparmar/stock-market-kafka-data-engineering-project)
# Steps
1. [Installing Kafka on AWS EC2](#installing-kafka-on-aws-ec2)

# Installing Kafka on AWS EC2
1. Launch new AWS EC2 instance
Named it "kafka-stock-market-project". Choose Ubuntu AMI. Don't forget to create key pair and save it 
3. Login with SSH client
Go to folder where you save .pem file. Then change the permision to read-only
```
    chmod 400 kafka-stock-market-project.pem
```
Then login with SSH, change ec2-instance with your own instance
```
    ssh -i "kafka-stock-market-project.pem" ec2-instance
```
4. Download Apache Kafka
Check latest kafka version [here](https://kafka.apache.org/downloads)
```
    wget https://downloads.apache.org/kafka/3.5.1/kafka_2.13-3.5.1.tgz
    tar -xvf kafka_2.13-3.5.1.tgz
```
5. Install Java
```
    sudo apt-get update
    sudo apt-get install openjdk-8-jdk
    java -version
```
6. Start Zookeeper
```
    cd kafka_2.13-3.5.1
    bin/zookeeper-server-start.sh config/zookeeper.properties
```
7. Start Kafka
Open new terminal (since the first one running Zookeeper), then also login with SSH. Increase the memory first (because we only use one instance)
```
    cd kafka_2.13-3.5.1
    export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
    bin/kafka-server-start.sh config/server.properties
```