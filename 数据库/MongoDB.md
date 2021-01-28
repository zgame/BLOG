# 下载

	http://dl.mongodb.org/dl/win32/x86_64


# windows安装和设置

	安装完成以后， 建目录MongoDB\Server\3.4\data\db
	使用--dbpath选项为mongod.exe指定数据文件的路径
	如果不使用 --dbpath 指定数据存储的目录，那么 MongoDB 默认使用的是 “C:\data\db“ 目录


# ubuntu安装

	sudo apt-get install -y mongodb

	启动和停止:
	sudo service mongodb stop 　　
	sudo service mongodb start

# 开放远程登录
	
	配置文件修改
	外围可以访问
	bindIp: 0.0.0.0

	开启登录认证	
	security:
	  authorization: enabled
	

# 客户端工具

	可以使用jetbrain datagrip
	或者https://nosqlbooster.com/downloads

	robot 3t可视化工具
	https://www.robomongo.org/
	

# 启动

	mongod.exe --dbpath "D:\Program Files\MongoDB\Server\3.4\data\db"

	客户端
	mongo.exe

# 权限

	用mongo客户端进入
	use admin
	db.auth("root", "root123" )
	

	show dbs
	use admin
	db.createUser({user:"patheaDev",pwd:"LncDnQaR502NWaFdCVXMeKacglgnf3",roles:[{role:"root",db:"admin"}]})
	db.createUser({user:"root",pwd:"root123",roles:[{role:"root",db:"admin"}]})
	db.createUser({user:"zsw",pwd:"zsw123",roles:[{role:"userAdminAnyDatabase",db:"admin"}]})

	关闭数据库，然后启动mongod.exe --dbpath "C:\Program Files\mongodb-win32-x86_64-windows-4.4.2\data\db" --auth


# 命令

	show dbs
	use  ***     // 有就切换， 没有就创建数据库
	
	db				// 查看当前选择的数据库是哪一个
	db.dropDatabase()	//删除当前的数据库

	db.createCollection("Package")		//创建集合
	show collections    		//集合列表
	db.COLLECTION_NAME.drop()  	//删除集合

# 查询

	// 插入数据到集合中， 如果没有集合，就创建该集合
	db.COLLECTION_NAME.insert({"name":"zsw"})
	

	db.mycol.find().pretty()	// 查询集合内容
	db.mycol.find({"by":"yiibai tutorials"}).pretty()		// by = 'yiibai tutorials'
	db.mycol.find({"likes":{$lte:50}}).pretty()				// likes <= 50
	db.mycol.find({"likes":{$gte:50}}).pretty()				// likes >= 50
	db.mycol.find({"likes":{$ne:50}}).pretty()				// likes != 50

	多个键通过","将它们分开, 等价于and
	db.mycol.find({"by":"yiibai tutorials","title": "MongoDB Overview"}).pretty()
	$or: [	     {key1: value1}, {key2:value2}      ]   // 或者的查询语句


# 更新

	update()方法将现有的文档中的值更新，而save()方法使用传递到save()方法的文档替换现有的文档。
	db.mycol.update({'title':'MongoDB Overview'},{$set:{'title':'New MongoDB Tutorial'}})
	$set:  这个是只更新更新的值，其他的不动

	db.mycol.save({"_id" : ObjectId(5983548781331adf45ec7), "title":"Yiibai Yiibai New Topic", "by":"Yiibai Yiibai"   })


# 删除

	db.mycol.remove({'title':'MongoDB Overview'}，1)

# 显示

	db.mycol.find({},{"title":1,_id:0})			//把id列给隐藏掉
	db.mycol.find({},{"title":1,_id:0}).limit(2)		//限制只取2列
	db.COLLECTION_NAME.find().sort({KEY:1})				//1用于升序，而-1是用于降序。

	

# 索引
	索引通常能够极大的提高查询的效率

	db.mycol.ensureIndex({"title":1})		//创建title的索引，1用于升序，而-1是用于降序。
	db.mycol.ensureIndex({"title":1,"description":-1})   // 多字段索引


# 聚合

	MongoDB 中聚合(aggregate)主要用于处理数据(诸如统计平均值，求和等)，并返回计算后的数据结果。
 	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : 1}}}])
	// 按照by_user， 统计数量



# 原子操作，可以解决并发问题

	$set	用来指定一个键并更新键值，若键不存在并创建。
	$inc	可以对文档的某个值为数字型（只能为满足要求的数字）的键进行增减的操作
	$push	把value追加到field里面去，field一定要是数组类型才行，如果field不存在，会新增一个数组类型加进去。
	$pull	从数组field内删除一个等于value值。
	$addToSet	增加一个值到数组内，而且只有当这个值不在数组内才增加。

