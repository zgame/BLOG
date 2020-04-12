# Kafka

	Kafka是一个分布式的发布 - 订阅消息传递系统和一个强大的队列，可以处理大量的数据，并使您能够将消息从一个端点传递到另一个端点。


# 应用 

	Kafka建立在ZooKeeper同步服务之上。 它与Apache Storm和Spark完美集成，用于实时流数据分析。
 	Kafka速度非常快，每秒执行200万次写入。


# Topics - 

	属于特定类别的消息流被称为主题(Topics)，数据存储在主题中。主题分为多个分区。

# Partition - 

	主题可能有很多分区

# Brokers

	经纪人(Brokers)是引用服务器，负责维护公布的数据。Kafka集群中的一台或多台服务器统称为broker。

# Kafka Cluster

	Kafka拥有多个经纪人称为Kafka集群。

# Producers - 

	生产者(Producer)是一个或多个Kafka主题的发布者。

# Consumers - 

	消费者从经纪人那里读取数据。 多个消费者可以组成消费者组。
	

# Leader - 

	Leader是负责所有分区读写的节点。

# Follower - 

	遵循领导者(Leader)指示的节点称为追随者(Follower)。


# ZooKeeper -
 
	ZooKeeper用于管理和协调Kafka经纪人。

 
# golang结合

	https://blog.csdn.net/tflasd1157/article/details/81985722

# 跟storm的结合


# 跟spark的结合


