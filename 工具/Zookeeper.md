# zookeeper
	
	Apache ZooKeeper是由集群（节点组）使用的一种服务，用于在自身之间协调，并通过稳健的同步技术维护共享数据。ZooKeeper本身是一个分布式应用程序，为写入分布式应用程序提供服务。
	

# leader

	如果我们有三个节点而一个节点故障，那么我们有大多数，因此，这是最低要求。ZooKeeper集合在实际生产环境中必须至少有三个节点。


# zookeeper cli

	ZooKeeper命令行界面（CLI）用于与ZooKeeper集合进行交互以进行开发。它有助于调试和解决不同的选项。


# api

	ZooKeeper有一个绑定Java和C的官方API。Zookeeper社区为大多数语言（.NET，python等）提供非官方API。

	连接到ZooKeeper集合。ZooKeeper集合为客户端分配会话ID。
	定期向服务器发送心跳。否则，ZooKeeper集合将过期会话ID，客户端需要重新连接。
	只要会话ID处于活动状态，就可以获取/设置znode。
	所有任务完成后，断开与ZooKeeper集合的连接。如果客户端长时间不活动，则ZooKeeper集合将自动断开客户端。

# hbase

	HBase遵循主从架构，HBase主控制所有从机。从机称为区域服务器。HBase分布式应用程序安装取决于运行的ZooKeeper集群。