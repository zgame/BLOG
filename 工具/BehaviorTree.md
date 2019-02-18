https://github.com/donnki/bttree


# 如果出现打不开的情况， 删掉C:\Users\soonyo\AppData\Roaming\b3editor目录


# Behavior3 Editor

	安装bower
	npm install -g bower
	npm install -g gulp

	安装依赖
	npm install
	bower install

	运行
	gulp serve

	127.0.0.1:8000

	编译桌面版本
	gulp dist


# binder
	
	进行条件判断，action事件的回调函数的绑定


# BTSequence顺序执行(前一个状态为结束才行)

	顺序执行，每个tick只执行一个子分支， 
	binder绑定函数返回true代表当前分支运行结束，下次进入下一个子分支, 否则就一直在当前分子
	如果子分支不满足进入条件，则不执行子分支，下次进入下一个子分支

# BTPrioritySelector 优先执行

	有一个满足条件就返回


# BTParallel并行与节点（要注意有一个失败全失败）

	并行节点，有一个子节点失败，就返回(return false的每次都运行)
	shouldEndWhenOneEnd 有一个节点结束，就结束(return true的每次都运行)


# BTParallelFlexible 并行或节点

	并行节点，全部执行成功的子节点
	只要其中一个子结点评估成功，则BTParallelFlexible评估成功
	当所有子结点返回Ended时，BTParallelFlexible返回Ended


# RunAction

	行为，可以设置前提条件和行为绑定函数

# BTWaitAction

	等待时间， 一般是作为顺序执行的子节点存在，作为一定的时间延迟


# BTCondition 条件判断节点

	设定assertFunc，就是用来做判断的函数
	一般用法是用在顺序执行的首位，用来判断是否满足一定条件


# 使用

	BTSequence顺序执行和 BTPrioritySelector优先执行都是执行一个子分支
	并行是可能执行多个字分支


# 步骤

	1.首先确定是单一执行分支，还是多个执行分支，就是子分支是否能够并行执行
	2.确定是否有先后顺序，如果是基于条件的用优先
	3.并行不要一死全死的话，用松散并行
	4.注意普通并行的shouldEndWhenOneEnd需要注意