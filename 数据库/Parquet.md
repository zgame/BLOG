# parquet

	Parquet 是列式存储的一种文件类型
	
	Parquet仅仅是一种存储格式，它是语言、平台无关的，并且不需要和任何一种数据处理框架绑定，目前能够和Parquet适配的组件包括下面这些，可以看出基本上通常使用的查询引擎和计算框架都已适配，并且可以很方便的将其它序列化工具生成的数据转换成Parquet格式。
	
	查询引擎: Hive, Impala, Pig, Presto, Drill, Tajo, HAWQ, IBM Big SQL
	计算框架: MapReduce, Spark, Cascading, Crunch, Scalding, Kite
	数据模型: Avro, Thrift, Protocol Buffers, POJOs


