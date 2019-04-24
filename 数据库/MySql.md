# 安装

	Ubuntu上安装MySQL非常简单只需要几条命令就可以完成。

	sudo apt-get install mysql-server
	apt-get isntall mysql-client
	sudo apt-get install libmysqlclient-dev
	
	安装过程中会提示设置密码什么的，注意设置了不要忘了，安装完成之后可以使用如下命令来检查是否安装成功：
	sudo netstat -tap | grep mysql
	tcp        0      0 localhost:mysql         *:*                     LISTEN      19217/mysqld   

	
	mysql -u root -p		//登录
	show databases;			//显示所有数据库
	create database zsw_database;	//创建新的数据库
	use  zsw_database;			//切换进入数据库
	show tables;			//显示表

	create table zsw_table(			//创建表结构
		ip varchar(45) not null 
     )engine=innodb;
	
	


# 远程登录的允许

	在装有MySQL的机器上登录MySQL mysql -u root -p密码
	mysql>执行use mysql;
	mysql>执行update user set host = '%' where user = 'root';这一句执行完可能会报错，不用管它。
	mysql>执行FLUSH PRIVILEGES;

	在windows版本， 设置用户的limit to hosts matching 为%


# mysql.user 对用户权限的设置

	mysql> use mysql;   // 记住这里一定要用；

	SELECT host, user, authentication_string FROM user WHERE user = 'guest';
	
	
	// 用户的认证方式一直是caching_sha2_password
	// 客户端就一直认证不过去，客户端不支持
	// 所以执行命令：
	ALTER USER ‘root’@’localhost’ IDENTIFIED WITH mysql_native_password BY ‘root’; 
	// 然后再修改一下密码就可以了


# 正确的权限

	Authentication Type : Standard
	Limit to Hosts Matching: %
	Administrative Roles: 全选

	
#游标

	实际上是一种能从包括多条数据记录的结果集中每次提取一条记录的机制。游标充当指针的作用。尽管游标能遍历结果中的所有行，但他一次只指向一行。



# MySQL master-slave主从架构

	Slave从库数据变化只通过应用日志实现，一般不会主动产生写数据的情况，但可以提供对外数据读服务，这样通过增加几个slave从库，让只进行数据读取的业务到slave从库上查询，就都可以大大提高业务的读性能和吞吐量。

	在互联网行业中，非常多的数据读操作远高于数据写操作的业务场景，通过在master主节点写数据，在slave节点上读数据，进行这种读写分离的架构，可以很好地满足业务需求。

	
# MySQL MHA高可用架构

	在master-slave主从环境的基础上，将业务连接master的IP，有master主机的实际IP，变成虚拟的VIP或者域名。应用程序通过VIP访问数据库，进行数据读写，master出现问题就切换到slave

# MySQL水平扩展
	

	有一个Proxy代理层或者中间件层的一个database和一个table，通过代理层按照一定的规则映射和转换，转换成底层多台服务器上的多个database和多个table，这样就相当于多台服务器共同支撑一个业务，	用的比较多的是MyCAT中间件，
	mycat可以通过取模来存取数据


# MySQL + Inforbright/Greenplum 统计分析架构


	Inforbright数据仓库比较轻量级，与MySQL使用类似；Greenplum分布式MPP数据仓库可以支撑海量数据的统计分析，功能、性能、容量等也比Inforbright要更强一下，成本也更大一些。


# 横向扩展

	横向扩展需要数据复制，例如基本的 MySQL Replication 或是用于数据同步的 Percona XtraDB 群集。
	如果您需要更高级的扩展性，那么请考虑使用 MySQL 分片（sharding）。
	另外，您还需要确保连接到群集架构的应用程序可以找到它们所需的数据。这通常是通过诸如 ProxySQL 或 HAProxy 的一些代理服务器和负载平衡器来实现的。




# 行锁

	每次单条记录的update操作，会对分区表数目相同的行数进行上锁。


# 表锁

	另外，InnoDB表的行锁也不是绝对的，假如在执行一个SQL语句时MySQL不能确定要扫描的范围，InnoDB表同样会锁全表，例如update table set num=1 where name like “%aaa%”


	select count(*) 和order by 是最频繁的，大概能占了整个sql总语句的60%以上的操作，而这种操作Innodb其实也是会锁表的，很多人以为Innodb是行级锁，那个只是where对它主键是有效，非主键的都会锁全表的。



# 数据库监控

	数据库监控以开源软件为主，有天兔Lepus、Prometheus、Open-Falcon


# 分区

	mysql自带分区表，对你的应用是透明的，无需更改代码,但是sql语句是需要针对分区表做优化的，sql条件中要带上分区条件的列，从而使查询定位到少量的分区上，否则就会扫描全部分区


# 增加查询速度


	1. 设计合适的索引,基于主键的查找,上亿数据也是很快的;
	2. 反范式化设计,以空间换时间,避免join,有些join操作可以在用代码实现,没必要用数据库来实现;
	3. buffer,尽量让内存大于数据.


# sql开发优化


	不使用存储过程、触发器，自定义函数
	不使用全文索引
	不使用分区表
	针对OTLP业务尽量避免使用多表join和子查询
	不使用*,SELECT使用具体的列名：在发生列的增/删时，发生列名修改时，最大限度避免程序逻辑中没有修改导致的BUG，IN的元素个数300-500
	避免使用大事务，使用短小的事务：减少锁等待和竞争
	禁止使用%前缀模糊查询 where like ‘%xxx’
	禁止使用子查询，遇到使用子查询的情况，尽量使用join代替
	遇到分页查询，使用延迟关联解决：分页如果有大offset，可以先取Id，然后用主键id关联表会提高效率
	禁止并发执行count(*)，并发导致CPU飙高
	禁止使⽤order by rand()
	不使用负向查询，如 not in/like，使用in反向代替
	不要一次更新大量（大于30000条）数据，批量更新/删除
	SQL中使用到OR的改写为用 IN() （or的效率没有in的效率高）


# 合并表

	INSERT INTO 目标表 SELECT * FROM 来源表;


	merge合并表的要求
	1.合并的表使用的必须是MyISAM引擎
	2.表的结构必须一致，包括索引、字段类型、引擎和字符集

	假如我有一张用户表user，有50W条数据，现在要拆成二张表user1和user2，每张表25W条数据，
	INSERT INTO user1(user1.id,user1.name,user1.sex)SELECT (user.id,user.name,user.sex)FROM user where user.id <= 250000
	INSERT INTO user2(user2.id,user2.name,user2.sex)SELECT (user.id,user.name,user.sex)FROM user where user.id > 250000



	mysql> CREATE TABLE IF NOT EXISTS `user1` (  
	 ->   `id` int(11) NOT NULL AUTO_INCREMENT,  
	 ->   `name` varchar(50) DEFAULT NULL,  
	 ->   `sex` int(1) NOT NULL DEFAULT '0',  
	 ->   PRIMARY KEY (`id`)  
	 -> ) ENGINE=MyISAM  DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;  
	Query OK, 0 rows affected (0.05 sec)  
	  
	mysql> CREATE TABLE IF NOT EXISTS `user2` (  
	 ->   `id` int(11) NOT NULL AUTO_INCREMENT,  
	 ->   `name` varchar(50) DEFAULT NULL,  
	 ->   `sex` int(1) NOT NULL DEFAULT '0',  
	 ->   PRIMARY KEY (`id`)  
	 -> ) ENGINE=MyISAM  DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;  
	Query OK, 0 rows affected (0.01 sec)  
	  
	mysql> INSERT INTO `user1` (`name`, `sex`) VALUES('张映', 0);  
	Query OK, 1 row affected (0.00 sec)  
	  
	mysql> INSERT INTO `user2` (`name`, `sex`) VALUES('tank', 1);  
	Query OK, 1 row affected (0.00 sec)  
	  
	mysql> CREATE TABLE IF NOT EXISTS `alluser` (  
	 ->   `id` int(11) NOT NULL AUTO_INCREMENT,  
	 ->   `name` varchar(50) DEFAULT NULL,  
	 ->   `sex` int(1) NOT NULL DEFAULT '0',  
	 ->   INDEX(id)  
	 -> ) TYPE=MERGE UNION=(user1,user2) INSERT_METHOD=LAST AUTO_INCREMENT=1 ;  
	Query OK, 0 rows affected, 1 warning (0.00 sec)  
	  
	mysql> select id,name,sex from alluser;  
	+----+--------+-----+  
	| id | name   | sex |  
	+----+--------+-----+  
	|  1 | 张映 |   0 |  
	|  1 | tank   |   1 |  
	+----+--------+-----+  
	2 rows in set (0.00 sec)  
	  
	mysql> INSERT INTO `alluser` (`name`, `sex`) VALUES('tank2', 0);  
	Query OK, 1 row affected (0.00 sec)  
	  
	mysql> select id,name,sex from user2  
	 -> ;  
	+----+-------+-----+  
	| id | name  | sex |  
	+----+-------+-----+  
	|  1 | tank  |   1 |  
	|  2 | tank2 |   0 |  
	+----+-------+-----+  
	2 rows in set (0.00 sec)  



# MyISAM与InnoDB区别

	MyISAM类型不支持事务处理等高级处理，而InnoDB类型支持。MyISAM类型的表强调的是性能，其执行数度比InnoDB类型更快，但是不提供事务支持，而InnoDB提供事务支持以及外部键等高级数据库功能。


	两种类型最主要的差别就是Innodb 支持事务处理与外键和行级锁。而MyISAM不支持.所以MyISAM往往就容易被人认为只适合在小项目中使用。

	
# 保存时间戳

	保存时间戳可以设置字段 bigint(20)



# select by time


	SELECT * FROM player_charge_rmb where time between '2015-03-07 00:00:00' and '2015-04-07 00:00:00'

	
# select limit

	SELECT * FROM player_charge_rmb limit 75100,75400


# group 分组

	SELECT user_id,sum(rmb) FROM by_statis_db.player_charge_rmb where time between '2016-01-01' and '2016-11-01' group by user_id     // 按照user_id来进行分组统计单个uid的充值金额汇总

 

# 插入或者更新 
	
	insert into t3(xx,xx) on duplicate key update `xx`='XX';
	key是主键


# 锁

	insert语句对于主键来说，插入的行不管有没有存在，都会只有行锁。
	简单的select操作，属于快照读，不加锁
	如果没有索引，所以update会锁表，如果加了索引，就会锁行

# 多列索引

	索引可以建立单列，也可以建立多列索引，这个在多个条件查询的时候会一次性的查询出来
	建立索引index（part1,part2,part3）,相当于建立了 index(part1),index(part1,part2)和index（part1,part2,part3）三个索引。
	MySQL针对like语法必须如下格式才使用索引：SELECT * FROM t1 WHERE key_col LIKE 'ab%' ；



# 存在就更新，不存在就插入

	如果有主键的话，可以用duplicate 或者replace
	insert into table (player_id,award_type,num)  values(20001,0,1) on  DUPLICATE key update num=num+values(num)

	所以两者的区别只有一个，insert .. on deplicate udpate保留了所有字段的旧值，再覆盖然后一起insert进去，而replace没有保留旧值，直接删除再insert新值。
 	从底层执行效率上来讲，replace要比insert .. on deplicate update效率要高，但是在写replace的时候，字段要写全，防止老的字段数据被删除。


	如果没有主键，采用的是多个索引搜索， 那么组合成一个唯一主键即可

	其他方法就是用存储过程。麻烦。
	