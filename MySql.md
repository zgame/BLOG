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

