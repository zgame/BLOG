
# 语法 

	必须在首行添加 # -*- coding: UTF-8 -*-,告诉解释器使用utf-8来解析源码。

	a + b 被解释为 a+b （这是一个局部变量）
	a  +b 被解释为 a(+b) （这是一个方法调用）


	BEGIN {			//声明 code 会在程序运行之前被调用。
 	  code
	}
	
	END {		//声明 code 会在程序的结尾被调用。
	   code
	}

	# 注释   
	=begin
	多行注释。
	=end


# 字符串

	字符串连接+


# 输出


	puts 'That\'s right';

	puts "#{name+",ok"}" 		# 自动换行

	print("ffff"，key，value， "\n")			# 不带换行,要自己加\n
	


# 数组

	通过赋值操作插入、删除、替换元素
	通过+，－号进行合并和删除元素，且集合做为新集合出现
	通过<<号向原数据追加元素
	通过*号重复数组元素
	通过｜和&符号做并集和交集操作（注意顺序）


	ary.each do |i|
    	puts i
	end

		




# 哈希表

	hsh = colors = { "red" => 0xf00, "green" => 0x0f0, "blue" => 0x00f }
	hsh.each do |key, value|
	    print key, " is ", value, "\n"
	end


# 范围

	(10..15).each do |n|
   		print n, ' '
	end




# 类

	全局变量总是以美元符号（$）开始
	实例变量在变量名之前放置符号（@）
	类变量在变量名之前放置符号（@@）。
	大写字母开头：常数（Constant）。

	cust1 = Customer. new

	成员函数 方法名总是以小写字母开头



# if

	if x > 2
	   puts "x 大于 2"
	elsif x <= 2 and x!=0
	   puts "x 是 1"
	else
	   puts "无法得知 x 的值"
	end


	case $age
	when 0 .. 2
	    puts "婴儿"
	when 3 .. 6
	    puts "小孩"
	when 13 .. 18
	    puts "少年"
	else
	    puts "其他年龄段的"
	end



# 方法

	def sample (*test)		# 可变参数



# 块

	一个程序可以包含多个 BEGIN{} 程序开始的时候执行 和 END{} 块 程序结束时候执行

	可以使用 yield 语句来调用块。


# 模块

	模块不能实例化
	模块没有子类
	模块只能被另一个模块定义

	require filename		# 调用其他rb文件

	include modulename
	