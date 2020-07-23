# Kafka

	Kafka是一个分布式的发布 - 订阅消息传递系统和一个强大的队列，可以处理大量的数据，并使您能够将消息从一个端点传递到另一个端点。


# 应用 

	Kafka建立在ZooKeeper同步服务之上。 它与Apache Storm和Spark完美集成，用于实时流数据分析。
 	Kafka速度非常快，每秒执行200万次写入。


# Topics - 

	属于特定类别的消息流被称为主题(Topics)，数据存储在主题中。主题分为多个分区。

# Partition - 

	主题可能有很多分区,Producer发送消息到broker时，会根据Paritition机制选择将其存储到哪一个Partition。如果Partition机制设置合理，所有消息可以均匀分布到不同的Partition里，这样就实现了负载均衡。如果一个Topic对应一个文件，那这个文件所在的机器I/O将会成为这个Topic的性能瓶颈，而有了Partition后，不同的消息可以并行写入不同broker的不同Partition里，极大的提高了吞吐率。可以在$KAFKA_HOME/config/server.properties中通过配置项num.partitions来指定新建Topic的默认Partition数量，也可在创建Topic时通过参数指定，同时也可以在Topic创建之后通过Kafka提供的工具修改。

# Brokers

	经纪人(Brokers)是引用服务器，负责维护公布的数据。Kafka集群中的一台或多台服务器统称为broker。

# Kafka Cluster

	Kafka拥有多个经纪人称为Kafka集群。

# Producers - 

	生产者(Producer)是一个或多个Kafka主题的发布者。

# Consumers - 

	消费者从经纪人那里读取数据。 多个消费者可以组成消费者组。
	
# 消费组

	在高并发方面，可以使用多个台服务器放在同一个消费组中，就可以保证所有的消费者拉取的消费不会重复并且完整，这样就可以提高消费者的执行效率。
	启动消费者的时候 –consumer-property group.id=group1  


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



# 安装
	
	tar -zxf kafka_2.11.0.9.0.0 tar.gz
	config\server.properties 配置文件，改log地址
	bin/kafka-server-start.sh config/server.properties  启动服务器
	bin/kafka-server-stop.sh config/server.properties  停止服务器
	

	创建主题
	bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic Hello-Kafka

	获取主题列表
	bin/kafka-topics.sh --list --zookeeper localhost:2181

	删除主题
	bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic topic_name

	启动生产者
	bin/kafka-console-producer.sh --broker-list localhost:9092 --topic Hello-Kafka

	启动消费者
	bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic Hello-zsw --from-beginning


# 多节点

	复制多个server.properties文件
	修改broker.id分别为0，1，2

	listeners=PLAINTEXT://:9092
	advertised.listeners=PLAINTEXT://172.16.140.110:9092   
	修改多个节点，多个log地址

	启动多个节点kafka用不同的配置文件
	
	创建主题
	bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 -partitions 1 --topic Hello-zswc
	
	查看主题
	bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic Hello-zswc -cation

	启动生产者
	bin/kafka-console-producer.sh --broker-list localhost:9092 --topic Hello-zswc

	启动消费者
	bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic Hello-zswc





# 数据清理

	Kafka提供两种策略删除旧数据。一是基于时间，二是基于Partition文件大小。
    例如可以通过配置$KAFKA_HOME/config/server.properties，让Kafka删除一周前的数据，也可在Partition文件超过1GB时删除旧数据



# 