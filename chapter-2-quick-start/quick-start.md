# Kafka Streams 快速开始

 > 本篇讲述如何利用Kafka Streams library，构建简单的Java 应用来进行端到端的kafka数据流计算

# 环境及版本

| Software   | Version   |
| ---------- |-----------|
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

## 搭建单节点Kafka集群

[请参考此篇文章-Kafka集群搭建]()

## 创建Topic

## 发送测试数据

## WordCount程序

- WordCount架构图



> 与批处理程序不同（Hadoop MapReduce），Kafka Streams 处理的是一个无穷、无边界的数据流，数据会一直不断的经过Kafka Streams，保证7x24小时的运行。

```java
```

> Kafka Streams程序和正常的Java程序一样启动、停止、性能参数等

[完整Demo]()

## 消费Topic

## 关闭Kafka集群
