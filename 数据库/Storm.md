
# Apache Storm vs Hadoop

	基本上Hadoop和Storm框架用于分析大数据。两者互补，在某些方面有所不同。Apache Storm执行除持久性之外的所有操作，而Hadoop在所有方面都很好，但滞后于实时计算。


# Spouts输入

	通常，Storm从原始数据源（如Twitter Streaming API，Apache Kafka队列，Kestrel队列等）接受输入数据。

# Bolts

	实现一个 bolt 时，通常需要实现 IRichBolt 接口.Bolts 对象由客户端机器创建，序列化为拓扑，并提交给集群中的主机。然后集群启动工人进程反序列化 bolt，调用 prepare****，最后开始处理元组。


# Nimbus（主节点）

	Nimbus是Storm集群的主节点。集群中的所有其他节点称为工作节点。主节点负责在所有工作节点之间分发数据，向工作节点分配任务和监视故障。

# Supervisor（工作节点）

	遵循指令的节点被称为Supervisors。Supervisor有多个工作进程，它管理工作进程以完成由nimbus分配的任务。

# Worker process（工作进程）

	工作进程将执行与特定拓扑相关的任务。工作进程不会自己运行任务，而是创建执行器并要求他们执行特定的任务。工作进程将有多个执行器。

# 开发语言

	除了java，还可以python等语言