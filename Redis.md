# 安装

	sudo apt-get update 
	sudo apt-get install redis-server



# 配置文件

	/etc/redis/redis.conf		//编辑文件
	requirepass zsw123	//设置密码
	bing 127.0.0.1
	
	CONFIG GET *	//命令行获取
	

# 安全

	比较安全的办法是采用绑定IP的方式来进行控制。
	bind 127.0.0.1    // 修改配置

	requirepass zsw123
	zsw123就是redis验证密码，设置密码以后发现可以登陆，但是无法执行命令了，因为要登录验证密码。

	auth zsw123	//客户端输入登录验证的命令，zsw123是自己设置的密码
	



# 启动，重启


	redis-server			//启动
	redis-cli			//客户端
	redis 127.0.0.1:6379> 			//显示进入客户端控制台

	ping		//测试

	sudo /etc/init.d/redis-server stop
	sudo /etc/init.d/redis-server start
	sudo /etc/init.d/redis-server restart



# 保存类型

	// 字符串-----------------------------
	set name "yiibai.com" 	
	get name

	//哈希表------------------------------------
	hset:设置hash field为指定值，如果key不存在，则先创建。
	hget:获取指定的hash field。
	hset user:001 name Tom
	hset user:001 age 28
	hget user:001 name

	//hmset:同时设置hash的多个字段。
	HMSET zsw:1 username w3cschool.cn password w3cschool.cn points 200
	HGETALL zsw:1

	keys *zsw*	//列出所有包含zsw的key
	keys ***    // list all

	//hdel:删除指定hash的field。
	hdel user:002 sex

	
	// 列表--------------------------------
	lpush list_name sdfsdf
	lrange list_name 0 10

	// set 集合--------------------------
	sadd set_name redis
	smembers redis

	//有序集合zset 和 set 一样也是string类型元素的集合,且不允许重复的成员。


	incr // 对存储在指定key的数值执行原子的加1操作。
	INCR mykey


# 备份和恢复

	save	
	/var/lib/redis/dump.rdb		//保存的文件


	重启redis server会自动从文件中恢复数据，所以每次关闭redis之前， 一定一定要save
	这里要注意，做备份的文件及时copy走， 因为恢复是自动的




# 分区（多个redis一起用）

	范围分区
	最简单的分区方式是按范围分区，就是映射一定范围的对象到特定的Redis实例。
	比如，ID从0到10000的用户会保存到实例R0，ID从10001到 20000的用户会保存到R1，以此类推。


	哈希分区
	另外一种分区方法是hash分区。这对任何key都适用，也无需是object_name:这种形式，像下面描述的一样简单：
	
	用一个hash函数将key转换为一个数字，比如使用crc32 hash函数。对key foobar执行crc32(foobar)会输出类似93024922的整数。
	对这个整数取模，将其转化为0-3之间的数字，就可以将这个整数映射到4个Redis实例中的一个了。93024922 % 4 = 2，就是说key foobar应该被存到R2实例中。注意：取模操作是取除的余数，通常在多种编程语言中用%操作符实现。	


# 管道技术

	Redis 管道技术可以在服务端未响应时，客户端可以继续向服务端发送请求，并最终一次性读取所有服务端的响应。


# 服务器命令

	比如info


# 事务

	类似存储过程
	multi
	....
	exec




# golang 开发

	https://github.com/gomodule/redigo
	
	// 例子
	https://godoc.org/github.com/gomodule/redigo/redis#pkg-examples

	n, err := conn.Do("APPEND", "key", "value")
	n, err = redis.String(c.Do("get", "key"))		//获取返回值


	c.Send("SET", "foo", "bar")
	c.Send("GET", "foo")
	c.Flush()
	c.Receive() // reply from SET
	v, err = c.Receive() // reply from GET


	c.Send("MULTI")
	c.Send("INCR", "foo")
	c.Send("INCR", "bar")
	r, err := c.Do("EXEC")
	fmt.Println(r) // prints [1, 1]


---

	func newPool(addr string) *redis.Pool {
	  return &redis.Pool{
	    MaxIdle: 3,
	    IdleTimeout: 240 * time.Second,
	    Dial: func () (redis.Conn, error) { return redis.Dial("tcp", addr) },
	  }
	}
	
	var (
	  pool *redis.Pool
	  redisServer = flag.String("redisServer", ":6379", "")
	)
	
	func main() {
	  flag.Parse()
	  pool = newPool(*redisServer)
	  ...
	}
	
	
	pool := &redis.Pool{
	  // Other pool configuration not shown in this example.
	  Dial: func () (redis.Conn, error) {
	    c, err := redis.Dial("tcp", server)
	    if err != nil {
	      return nil, err
	    }
	    if _, err := c.Do("AUTH", password); err != nil {
	      c.Close()
	      return nil, err
	    }
	    if _, err := c.Do("SELECT", db); err != nil {
	      c.Close()
	      return nil, err
	    }
	    return c, nil
	  },
	}








# windows版本redis

	https://github.com/MicrosoftArchive/redis/releases

	安装之后cmd
	redis-server.exe redis.windows.conf		//开启服务器
	
	redis-cli.exe -h 127.0.0.1 -p 6379 			//开启客户端

	