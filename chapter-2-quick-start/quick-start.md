# Kafka Streams 快速入门

 > 本篇讲述如何利用Kafka Streams library，构建简单的Java 应用来进行端到端的kafka数据流计算

# 环境及版本

| Software   | Version   |
| ---------- |-----------|
| JDK        | 1.8+      |
| Kafka      | 0.10.2.1  |
| Zookeeper  |           |

> Oracle Java JRE or JDK >= 1.7 

#  WordCount Demo Application 

> 本节的目的是利用Kafka Streams 从零构建一个WordCount词频统计的流式计算Demo，步骤如下：

- 搭建单节点Kafka集群
- 利用脚本工具创建topic，并且发送测试数据（同样可以通过Java Client编写Producer程序实现）
- 利用Kafka Streams library编写WordCount程序处理测试数据
- 利用脚本工具消费经过处理的数据，以便检查数据处理结构是否正确（同样可以通过Java Client编写Consumer程序实现）
- 关闭Kafka 集群

## 一、搭建单节点Kafka集群

[请参考此篇文章-Kafka集群搭建]()

## 二、创建Topic

> Kafka 自带工具：./kafka_2.11-0.10.2.1/bin 

```shell

// Create the input topic for producer, named wordcount-input

./bin/kafka-topics.sh --create \
          --zookeeper localhost:2181 \
          --replication-factor 1 \
          --partitions 1 \
          --topic wordcount-input

Created topic "wordcount-input".

// Create the output topic for consumer, named wordcount-output

./bin/kafka-topics.sh --create \
          --zookeeper localhost:2181 \
          --replication-factor 1 \
          --partitions 1 \
          --topic wordcount-output

Created topic "wordcount-output".
```

- --zookeeper 为zookeeper地址
- --replication-factor 为副本数
- --partitions 为分区数

## 三、发送测试数据

> 利用脚本向wordcount-input topic发送数据

```shell

./kafka-console-producer.sh --broker-list 192.168.1.112:9092 --topic wordcount-input

// 一行一行输入以下内容
hello world
hello world
kafka streams test
kafka streams test
```

## 四、WordCount（词频统计Demo）

- WordCount整体架构图

![WordCount整体架构图](https://github.com/imperio-wxm/kafka-streams-documents/blob/64eb084c4c0efddf0d614e48b4bf2ab6c481784a/pictures/WordCount%E6%9E%B6%E6%9E%84%E5%9B%BE.png?raw=true)

> 与批处理程序不同（Hadoop MapReduce），Kafka Streams 处理的是一个无穷、无边界的数据流，数据会一直不断的经过Kafka Streams，保证7x24小时的运行。

```java
```

> Kafka Streams程序和正常的Java程序一样启动、停止

[完整Demo]()

## 五、消费Topic

> 利用脚本从wordcount-output topic读取数据

```shell

./kafka-console-consumer.sh --bootstrap-server 192.168.1.112:9092 --topic wordcount-output --from-beginning --formatter kafka.tools.DefaultMessageFormatter  --property print.key=true
```

## 六、关闭Kafka集群
