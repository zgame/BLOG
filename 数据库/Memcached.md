

# 安装 


	sudo apt-get install libevent libevent-deve          自动下载安装（Ubuntu/Debian）
	yum install libevent libevent-deve                      自动下载安装（Redhat/Fedora/Centos）

	sudo apt-get install memcached				//Ubuntu/Debian
	yum install memcached						//Redhat/Fedora/Centos


	ps aux | grep memcached
	telnet 127.0.0.1 11211


# 保存

	set key 0 900 9 		//900秒失效时间	 key = 9
	memcached 
	STORED 

	get key 
	VALUE key 0 9
	memcached
	END 


# 基本废弃了，用redis更方便，更强大


#Memcached乐观锁

	Memcached提供了2个命令 gets + cas。gets取出数据的时候，同时返回版本号；修改之后, cas回去的时候，会比较该版本号和服务器上最新的版本号。如果不等，则cas失败。