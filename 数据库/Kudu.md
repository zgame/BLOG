# Kudu

	支持快速分析的新型Hadoop存储系统, 是Cloudera开源的新型列式存储系统

	Kudu是对HDFS和HBase功能上的补充，能提供快速的分析和实时计算能力，并且充分利用CPU和I/O资源，支持数据原地修改，支持简单的、可扩展的数据模型。

# 基本框架

	类似于BigTable，Kudu的表是由很多数据子集构成的，表被水平拆分成多个Tablets.
	Kudu增删改操作都放在内存中的buffer，然后才merge到持久化的列式存储中。

# 优化

	HDFS + HBase这样的混合架构复杂， 在使用Kudu以后，Kudu作为统一的数据仓库，可以同时支持离线分析和实时交互分析。

	Kudu提供一个介于HDFS和HBase的性能特点之间的一个系统，在随机读写和批量扫描之间找到一个平衡点，


# 数据存储

	和HBase不同的是，Kudu没有借助于HDFS存储实际数据，而是自己直接在本地磁盘上管理分片数据，包括数据的Replication机制，kudu的Tablet server直接管理Master分片和Slave分片，自己通过raft协议解决一致性问题等，多个Slave可以同时提供数据读取服务，相对于HBase依托HDFS进行Region数据的管理方式，自主性会强一些，不过比如Tablet节点崩溃，数据的迁移拷贝工作等，也需要Kudu自己完成。


