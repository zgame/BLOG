
# 目标：

	1.解决旧架构运维不方便问题。新架构采用研运一体DevOps设计，结合研发，运维，运营一体设计，网站后台监控及控制，高效管理，一键运维。
	2.解决旧架构数据库瓶颈问题。新架构采用redis缓存架构，解决掉关系型数据库的瓶颈问题。
	3.解决旧架构研发效率低问题。新架构采用go+lua研发，全脚本开发，结构清晰，文档齐全，调试方便。

# 计划：
	
	第一步：底层的搭建。 （1-2周） (已完成)
	实现go和lua的结合，互相调用，传递参数及返回值；
	lua业务逻辑的结构和调用关系设计
	lua的热更新实现
	lua热更新之后玩家数据保留
	支持socket连接
	支持websocket连接
	支持单独或者同时开启socket和websocket连接，也就是说同一个服务器可以支持不同客户端的不同连接方式同时在一起玩。
	计时器逻辑处理；
	实现高性能的go高并发网络处理及lua的对接；
	lua部分可以实现收发数据；
	消息收发protocol协议部分接入；
	日志部分处理；
	csv配置文件部分；
	数据库部分接口；
	
	缺点：因为使用lua，并且采用go的高并发架构，所以lua部分会占用内存多一些，具体看压测结果。

	中间插入： lua gen protobuf for go 这个功能模块需要自己来实现，花费1.5周时间(已完成)
	
	第二步：捕鱼的主要逻辑实现。（1-2周）(已完成)
	用捕鱼的protocol协议来实现游戏逻辑；
	游戏的管理模块实现；
	支持不同逻辑的小游戏管理；
	游戏桌子的管理模块实现，动态的分配和回收；
	玩家的登录流程；
	玩家进入游戏流程；
	玩家进入桌子，坐下，玩，离开等流程；
	进入场景生成鱼，捕鱼，捕鱼成功，发放奖励流程；


	中间插入：（正在进行，这块还真是麻烦） 
	开始处理多线程问题，由于使用高并发，多go协程处理各个玩家连接和主线程游戏逻辑之前如何通信，交换数据成为一个核心问题。
	
	多线程处理设计细节：
	单独多个计时器线程处理热更新，夜里12点计划任务，公共数据处理逻辑等
	主线程跑游戏管理器，游戏，桌子创建等，以后把每个桌子单独做成独立成处理线程（未尝试）
	每个玩家连接是单独的线程处理
	多线程之间保证线程安全的通讯机制：
	lua栈是主线程一个，每个玩家连接一个
	如果采用共有变量，必须保证线程安全，也就是同一个时间只能有一个线程去处理，不能多线程处理
	玩家连接数量非常多，跟主线程之间不能用全局变量，只能用channel
	但是这个channel如何设计，如何交换，交换数量类型，大小，待定
	下周开始做几个类型解决方案的尝试，看效果再定


	第三步：压测工具测试。（3-5天）
	用压测工具开始进行测试，主要包括网络上限，内存，cpu上限，延迟时间，卡顿情况测试。
	测试结果
	第一次测试内存不通过，消耗量太大，调整架构之后，压测1万人同时在线内存占用只有2个G，内存通过测试
	cpu上限， i3cpu可以带1000人，i5cpu可以带3500人，i7cpu可以带1万人， 达到预期，符合要求
	
	
	第四步：代码优化阶段。（1周）
	针对前期测试的情况，进行代码优化调整，完善细节处理。
	数据包的拆包，粘包及数据包校验的优化
	网络数据发送和接收的优化
	socket和websocket的服务器和压测客户端优化
	服务器的健壮性和稳定性的优化
	
	
	第五步：实现共有数据的处理。（1周）
	共有数据主要是玩家一起活动的数据，比如世界boss，工会活动，跨服活动，排行榜等。
	
	
	第六步：共有数据处理的压力测试（3-5天）
	这个要专门的写一个测试工具，集中测试大量访问下的承载情况，是否有数据不同步的情况，是否有死锁情况，是否有过载崩溃的情况。
	
	第七步：总结（1-2周）
	引擎架构说明；
	注意事项；
	测试用例；
	代码范例；
	编码规范；
	后台控制方法；
	运维部分说明，如何增减服务器，如何监控服务器状态，大小维护如何进行；
	数据存储部分的运维和备份；
	运维日志监控，收集，报警；


# 总结：

	反正总体目标就是让研发和运维运营变的更简单和轻松，总体研发技术难度不大，细节处理完美需要花点时间。

	上面就是大致的研发计划和大致的时间安排。 
	每当有关键步骤完成，我会通知大家，并告诉实现的情况，达到什么效果，遇到什么问题，怎么解决，大家可以了解项目进展情况， 也可以随时增加需求或者提出自己的看法。
	有新的需求或者变动的时候，时间会响应的变化， 另外如果我中途需要处理其他事情，时间节点就会顺延。
	有问题随时找我

