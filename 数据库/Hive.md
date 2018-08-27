# Hive

	安装要先安装java，hadoop，
	访问Hadoop的默认端口号为50070.使用以下网址，以获取浏览器Hadoop服务。
	http://localhost:50070/

	访问集群中的所有应用程序的默认端口号为8088。使用以下URL访问该服务。
	http://localhost:8088/

	下载并安装Apache Derby


# 应用
	
	Hive是一种建立在Hadoop文件系统上的数据仓库架构，并对存储在HDFS中的数据进行分析和管理；它可以将结构化的数据文件映射为一张数据库表，并提供完整的 SQL 查询功能，可以将 SQL 语句转换为 MapReduce 任务进行运行，通过自己的 SQL 去查询分析需要的内容

	Hive 的最佳使用场合是大数据集的批处理作业，例如，网络日志分析

# 类型

	1整形
	 整型数据可以指定使用整型数据类型，INT。当数据范围超过INT的范围，需要使用BIGINT，如果数据范围比INT小，使用SMALLINT。 TINYINT比SMALLINT小。
	2 字符串类型
	3 时间戳
	4 日期
	5 小数点
	6 联合类型
	7 文字
	8 浮点
	9 十进制
	10 NULL
	11 数组
	12 映射
	13 结构体

# 操作

	hive> CREATE DATABASE [IF NOT EXISTS] userdb;
	hive> DROP DATABASE IF EXISTS userdb;


	hive> CREATE TABLE IF NOT EXISTS employee ( eid int, name String,
	> salary String, destination String)
	> COMMENT ‘Employee details’
	> ROW FORMAT DELIMITED
	> FIELDS TERMINATED BY ‘\t’
	> LINES TERMINATED BY ‘\n’
	> STORED AS TEXTFILE;


#分区

	用分区，很容易对数据进行部分查询。

# 支持视图和索引


# HiveQL

	hive> SELECT * FROM employee WHERE salary>30000;
	hive> SELECT Id, Name, Dept FROM employee ORDER BY DEPT;	
	hive> SELECT Dept,count(*) FROM employee GROUP BY DEPT;

# 支持join

	JOIN
	LEFT OUTER JOIN
	RIGHT OUTER JOIN
	FULL OUTER JOIN