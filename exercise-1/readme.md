# 练习1 - 通过docker搭建kafka的开发环境

参考文章： [使用Docker快速搭建Kafka开发环境](https://www.jianshu.com/p/ac03f126980e)

1. 启动zookeeper和kafka

```bash
docker-compose up -d
```

2. 通过kafka cli练习kafka基本操作

2.1 创建一个topic

```bash
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic my_topic
```

2.2 启动producer并发送消息

```bash
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my_topic
This is a message
This is another message
```

2.3 启动consumer并接收消息

```bash
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my_topic --from-beginning
This is a message
This is another message
```

4. 停止并清除资源

```bash
docker-compose down
```