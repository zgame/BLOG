# 流数据处理

	Apache Flink是一个面向分布式数据流处理和批量数据处理的开源计算平台，它能够基于同一个Flink运行时（Flink Runtime），提供支持流处理和批处理两种类型应用的功能。现有的开源计算方案，会把流处理和批处理作为两种不同的应用类型，因为他们它们所提供的SLA是完全不相同的：流处理一般需要支持低延迟、Exactly-once保证，而批处理需要支持高吞吐、高效处理，所以在实现的时候通常是分别给出两套实现方法，或者通过一个独立的开源框架来实现其中每一种处理方案。例如，实现批处理的开源方案有MapReduce、Tez、Crunch、Spark，实现流处理的开源方案有Samza、Storm。




# web可视化控制台

	打开http://192.168.80.131:8081



# 对比

	Spark streaming 的本质还是一款基于 microbatch 计算的引擎。这种引擎一个天生的缺点就是每个 microbatch 的调度开销比较大，当我们要求越低的延迟时，额外的开销就越大。

	Kafka streaming 是从一个日志系统做起来的，它的设计目标是足够轻量，足够简洁易用。

	Storm 是一个没有批处理能力的数据流处理器，除此之外 Storm 只提供了非常底层的 API，用户需要自己实现很多复杂的逻辑。


# 批处理

	Flink 还提供了 SQL／tableAPI 这两个 API，为批和流在 query 层的统一又铺平了道路。因此 Flink 是最合适的批和流统一的引擎；


# libraries支持

	Libraries支持
	支持机器学习（FlinkML）
	支持图分析（Gelly）
	支持关系数据处理（Table）
	支持复杂事件处理（CEP）

# 基本架构
	
	Flink系统的架构与Spark类似，是一个基于Master-Slave风格的架构

# JobManager
	
	JobManager是Flink系统的协调者，它负责接收Flink Job，调度组成Job的多个Task的执行。同时，JobManager还负责收集Job的状态信息，并管理Flink集群中从节点TaskManager。


# TaskManager

	TaskManager也是一个Actor，它是实际负责执行计算的Worker，在其上执行Flink Job的一组Task。每个TaskManager负责管理其所在节点上的资源信息，如内存、磁盘、网络，在启动的时候将资源的状态向JobManager汇报。

