# Kafka Streams 快速开始

| Software   | Version   |
| ---------- |-----------|
| JDK        | 1.8+      | 
| Kafka      | 0.10.2.1  |
| Zookeeper  |           |

 > 本篇讲述如何利用Kafka Streams library，构建简单的Java 应用来进行端到端的kafka数据流计算

#  WordCount Demo Application 

> 本节的目的是利用Kafka Streams 从零构建一个WordCount词频统计的流式计算Demo，步骤如下：

- 搭建单节点Kafka集群
- 利用脚本工具创建topic，并且发送测试数据
- 利用Kafka Streams library编写WordCount程序处理测试数据
- 利用脚本工具消费经过处理的数据，以便检查数据处理结构是否正确
- 关闭Kafka 集群