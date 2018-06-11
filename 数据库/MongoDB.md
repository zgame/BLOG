
# 安装和设置

	安装完成以后， 建目录MongoDB\Server\3.4\data\db
	使用--dbpath选项为mongod.exe指定数据文件的路径
	如果不使用 --dbpath 指定数据存储的目录，那么 MongoDB 默认使用的是 “C:\data\db“ 目录

	

# 启动

	mongod.exe --dbpath "D:\Program Files\MongoDB\Server\3.4\data\db"

	客户端
	mongo.exe


# 命令

	show dbs
	use  ***     // 有就切换， 没有就创建
	db				// 查看当前选择的数据库是哪一个
	db.dropDatabase()	//删除当前的数据库


# 查询

	// 插入数据到集合中， 如果没有集合，就创建该集合
	db.COLLECTION_NAME.insert({"name":"zsw"})
	show collections    		//集合列表
	db.COLLECTION_NAME.drop()  	//删除集合
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
	db.mycol.save({"_id" : ObjectId(5983548781331adf45ec7), "title":"Yiibai Yiibai New Topic", "by":"Yiibai Yiibai"   })


# 删除

	db.mycol.remove({'title':'MongoDB Overview'}，1)

# 显示

	db.mycol.find({},{"title":1,_id:0})			//把id列给隐藏掉
	db.mycol.find({},{"title":1,_id:0}).limit(2)		//限制只取2列
	db.COLLECTION_NAME.find().sort({KEY:1})				//1用于升序，而-1是用于降序。

	

# 索引

	db.mycol.ensureIndex({"title":1})		//创建title的索引，1用于升序，而-1是用于降序。
	db.mycol.ensureIndex({"title":1,"description":-1})   // 多字段索引


# 聚合

 	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : 1}}}])
	// 按照by_user， 统计数量

