

# 基础

	-- 注释

	local tbl1 = {}		-- 定义局部变量
	
	-- 可以多变量赋值 ，下面就可以进行两个值的交换
	x, y = y, x                     -- swap 'x' for 'y'


# 类型转换

	tonumber() tostring()	
	

# 表

	-- 定义表 
	a = {}			
	a["key"] = "value"		
	key = 10
	a[key] = 22
	a[key] = a[key] + 11

	-- 语法糖
	a["key"] 也可以写成 a.key


	-- 在末尾插入
	table.insert(fruits,"mango")
	
	-- 在索引为 2 的键处插入
	table.insert(fruits,2,"grapes")
	
	-- 删除最后一个
	table.remove(fruits)
	table.remove(fruits,1)	-- 删除1位置上的

	-- 删除数组或者哈希都可以用
	tt[**] = nil
	
	
	table.sort(fruits)

	-- 返回表的长度
	#table  -- 这里要特别注意，#是找1开始的，如果没有1就找不到，顺序找，不连续也不行


	-- dumptable 打印table的函数，自己写的函数，可以打印table的内容


	-- table.concat 返回 table 连接后的字符串
	fruits = {"banana","orange","apple"}			--bananaorangeapple
	print("连接后的字符串 ",table.concat(fruits))
	print("连接后的字符串 ",table.concat(fruits,", "))
	print("连接后的字符串 ",table.concat(fruits,", ", 2,3))


# 条件判断

	-- and or not	

	if   ***	then
	elseif ** then
	else 
	end	


# 循环

	a3 = {}
	for i = 1, 10 do	(1,2,3...9,10)
	    a3[i] = i
	end

	--打印数组a的所有值  
	for i,v in ipairs(a) 
		do print(v) 
	end  

	--打印哈希表的所有键值
	for k, v in pairs(a) do
	    print(k .. " : " .. v)
	end


	--不同于其他语言的数组把 0 作为数组的初始索引，在 Lua 里表的默认初始索引一般以 1 开始。


# 函数

	-- 函数里面定义的全局变量， 也是全局变量， 所以一定要用local
	
	-- 函数可以被赋值成一个变量， 也可以作为参数传递到另外的函数中

	-- 多返回值跟python，golang一样

	-- 可变参
	function average(...)
	   result = 0
	   local arg={...}
	   for i,v in ipairs(arg) do
	      result = result + v
	   end
	   print("总共传入 " .. #arg .. " 个数")
	   return result/#arg
	end

	-- 函数结束要有end

	
# 字符串

	-- 字符串连接  ..
	-- 字符串长度 # 

	string.format("the value is:%d",4)
	the value is:4


	tostrng(x) --x为数字 如：10
	tonumber(x) --x为字符串 如： “10”

	..链接两个字符串
	string.len(arg)


# model 模块

	-- 文件名为 module.lua
	-- 定义一个名为 module 的模块
	module = {}
	 
	-- 定义一个常量
	module.constant = "这是一个常量"
	 
	-- 定义一个函数
	function module.func1()						--外部可以调用该函数
	    io.write("这是一个公有函数！\n")
	end
	 
	local function func2()					--本地私有函数，外部无法调用
	    print("这是一个私有函数！")
	end
	 
	 
	return module 
	
	--- 其他模块调用
	local m = require("module")
	 
	print(m.constant)
	 
	m.func3()


	--- module调用系统函数
	在module里 如果一个module里 可以把module(...)改成module(...,package.seeall) 
	或者在module之前执行 local string = string
	要注意： local string = string 调用系统的函数必须在module(...)前面



# 类


	Shape = {area = 0}

	
	function Shape:new (o,side)			-- 基础类方法 new
	  o = o or {}
	  setmetatable(o, self)
	  self.__index = self
	  side = side or 0
	  self.area = side*side;
	  return o
	end

	
	function Shape:printArea ()			-- 基础类方法 printArea
	  print("面积为 ",self.area)
	end
	
	
	myshape = Shape:new(nil,10)		-- 创建对象
	myshape:printArea()
	

	Square = Shape:new()		-- 派生类
	function Square:new (o,side)
	  o = o or Shape:new(o,side)
	  setmetatable(o, self)
	  self.__index = self
	  return o
	end
	
	
	function Square:printArea ()		-- 派生类方法 printArea
	  print("正方形面积为 ",self.area)
	end
	
	
	mysquare = Square:new(nil,10)		-- 创建派生类对象
	mysquare:printArea()
	



# 命名规范



	1．所有lua文件命名时使用小写字母、下划线
	2．类名、变量名尽可能使用有意义的英文，类名使用帕斯卡命名法，变量名使用骆驼式命名法 
	3．常量、消息号定义时用大写，单词间 _ 分割  eg:KIND_PET_FOOD
	4．枚举值定义时 加前缀 enum_ 
	5. 函数名使用骆驼式命名法



# 错误提示和堆栈

	Lua提供了xpcall来实现这个功能，xpcall接受两个参数：调用函数、错误处理函数。当错误发生时，Lua会在栈释放以前调用错误处理函数，因此可以使用debug库收集错误相关信息。有两个常用的debug处理函数：debug.debug和debug.traceback，前者给出Lua的提示符，你可以自己动手察看错误发生时的情况；后者通过traceback创建更多的错误信息，也是控制台解释器用来构建错误信息的函数。你可以在任何时候调用debug.traceback获取当前运行的traceback信息：
	
	
	xpcall(main, function(err)
	    print(err)
	    print(debug.traceback())
	end)



# 引用路径

	--方法1 只加载想要的目录
	package.path = "../myLuaTest/myLuaCode/?.lua;"
	--方法2 增加目录
	package.path = "../myLuaTest/myLuaCode/?.lua;"..package.path
	print(package.path);



# metatable

	lua首先查找表，找不到就找元表， 判断元表有没有__index
	__index可以是一个表，也可以是一个函数

	__newindex 元方法用来对表更新，__index则用来对表访问 。
	__call 元方法在 Lua 调用一个值时调用。
	__tostring 元方法用于修改表的输出行为

	

# 获取时间，秒数

	print(os.time())
	print(os.time({year =2916, month = 11, day =23, hour =17, min =17, sec = 00}))


# 随机数

	math.randomseed(os.time())
	math.random(3)  -- [1,3]
