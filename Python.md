# 包管理

	python的包在Lib/site-packages目录下面， 自己的目录copy给别人就可以了


# 字符串也是数组

	s = 'Python'
	s[-1]='n'
	s[1:4]='yth'
	s[3:-1]='ho'

# 字符串操作

	s.split()		# 字符串按照空格分隔
	' '.join(s)		# 组成字符串, 作用是将s这个list用空格来区分每个数组中的item，最后组成一个string
	s.upper()		# 大写
	s.title()		# 大写首字母

<font color=#A52A2A size=2>字符串支持 +（连接字符串） 和 *（乘法，重复字符串）</font>

<font color=#A52A2A size=2>如果你不想让反斜杠发生转义，可以在字符串前面添加一个r，表示原始字符串：</font>

	>>> print('C:\some\name')
	C:\some
	ame
	>>> print(r'C:\some\name')
	C:\some\name

单引号和双引号都是字符串， 单引号转义的时候用的多一些， 三引号用在多行字符串

	u"字符串"	# 表示unicode的编码格式
	r"字符串"	# 表示原始不需要转义的
	b"字符串"	# 代表的就是bytes 


# 字符串的替换

	print "%s ,%s, %s"%(3,4,5)

	str = 'test{0},{1}'
	str = str.format("place0", "place1")


# 数组操作

	list[::-1][:3]
	list[-3:][::-1]
	list[::-1]		# 是将列表反过来，一种是先反过来，然后取前三位；一种是先取后三位，再反过来。
	list[-3:]		# 是取list的从后面数3个元素

	list.append(obj)	# 添加到末尾
	list.insert(1,'web')	# 插入元素到指定位置

	list.remove(8)	# 把8这个元素删掉
	list.pop(0)		# 把0位置上的元素删掉
	del(list[0])	# 同上

	list.extend(list2)	# 合并
	list.index(obj)		# 返回元素的位置

	list.reverse()		#反向
	list.sort([func])	# func可选，排序

	# 利用enumerate()函数，可以在每次循环中同时得到下标和元素：
	for (index,char) in enumerate(S): 
		print index print char

	len(list)		# 获取列表长度
	max(list)
	min(list)
	list(seq)		# 元组变列表


# 正则表达式

	# 删除非数字的字符串 
	num = re.sub(r'\D', "", phone)


# 集合

set() set和list可以互相转换， set的速度比list快非常多

	list(set(list1))   去掉重复的元素

# 字典
	dict.get(key, default=None)
	key -- 这是要搜索在字典中的键。
	default -- 这是要返回键不存在的的情况下默认值。

	# 对字典进行遍历
	for k,v in dict.iteritems():


# 类型

	利用isinstance函数，来判断一个对象是否是一个已知的类型。 
	数字变为字符串 str(4)
	字符串变为数字 string.atoi(s,[，base]) //base为进制基数
	浮点数转换 string.atof(s)
	字符转数字 int(str)

	除法根据前面的类型定义来计算结果的类型的 
	1/2 = 0  # 根据1取整	# 这是python2
	1/2 = 0.5	#这是python3

	在编写sql语句的时候，如果日期转换用%就会报错，所以要用%%

---



 

# 函数式编程

**filter:**

	filter(function, sequence)：
	str = ['a', 'b','c', 'd']
	def fun1(s): return s if s != 'a' else None
	ret = filter(fun1, str)
	print ret
	## ['b', 'c', 'd']

对sequence中的item依次执行function(item)，

将执行结果为True的item组成一个List/String/Tuple（取决于sequence的类型）返回。

可以看作是过滤函数。 

---
**map:**

	map(function, sequence) 
	str = ['a', 'b','c', 'd'] 
	def fun2(s): return s + ".txt"
	ret = map(fun2, str)
	print ret
	## ['a.txt', 'b.txt', 'c.txt', 'd.txt']

对sequence中的item依次执行function(item)，见执行结果组成一个List返回：

map也支持多个sequence，这就要求function也支持相应数量的参数输入：

	def add(x, y): return x+y 
	 print map(add, range(10), range(10)) 
	##[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

---
**reduce:**

	reduce(function, sequence, starting_value)：def add1(x,y): return x + y 
	print reduce(add1, range(1, 100)) 
	print reduce(add1, range(1, 100), 20)
	## 4950 （注：1+2+...+99）
	## 4970 （注：1+2+...+99+20）

对sequence中的item顺序迭代调用function，如果有starting_value，还可以作为初始值调用，例如可以用来对List求和： 

---

**lambda：**

	g = lambda s: s + ".fsh" 
	print g("haha") 
	print (lambda x: x * 2) (3)
	## haha.fsh 
	## 6

这是Python支持一种有趣的语法，它允许你快速定义单行的最小函数，类似与C语言中的宏，这些叫做lambda的函数.

---




# 随机数

	random.randint
	print random.randint(12,20)#生成的随机数n:12<=n<=20

# 日期的转化

	row_day = datetime.datetime.strptime(str(row_date),'%Y-%m-%d')  #将date转换为str，在由str转换为datetime
	(create_time-row_day).days


# 获取命令行参数

	if __name__ == "__main__":
	   main(sys.argv[1:])


# import 
	
	import自定义的目录时候，2.7版本需要在目录下创建__init__.py文件


# 2.7版本要注意

	coding = utf-8 必须写在第一行

Python2的写法用的是

    def __unicode__(self):
        return self.name


而python3中写法是

    def __str__(self):
        return self.name
	
# 2.7字符串转化

	unicodestring = u"Hello world" 
	# 将Unicode转化为普通Python字符串："encode"  
	utf8string = unicodestring.encode("utf-8")  
	asciistring = unicodestring.encode("ascii")  
	isostring = unicodestring.encode("ISO-8859-1")  
	utf16string = unicodestring.encode("utf-16")  
	# 将普通Python字符串转化为Unicode："decode"  
	plainstring1 = unicode(utf8string, "utf-8")  
	plainstring2 = unicode(asciistring, "ascii")  
	plainstring3 = unicode(isostring, "ISO-8859-1")  
	plainstring4 = unicode(utf16string, "utf-16")  
	assert plainstring1 == plainstring2 == plainstring3 == plainstring4



# 面向对象


	class Person:
		def __init__(self, name):
			self.name = name

类的用法， 类中_是私有方法, __是私有变量


cls是class的缩写




	# 类的普通方法可以通过self访问实例属性
	def normalMethod(self, name):
	# 类方法,可以通过cls访问类属性
	@classmethod
	def classMethod(cls, name):
	# 静态方法,不可以访问类属性
	@staticmethod
	def staticMethod(name):

# 文件处理，注意python2和python3的区别

	# python可以优雅的处理文件，with来自动关闭文件，不需要写close
	with open('1.txt','r') as f:	# python2
		tt = f.read()
	
	with open('1.txt','r', encoding='utf-8') as f:  # python3	
		tt = f.read()


	line.replace(old_str, new_str)		#行字符串替换
	
	
	
	# 写入文件的时候要注意字符编码，2.7对宽字符处理不好， 所以尽量用3.6版本吧
	str = unicode(str,'utf-8')
	f.write(str.encode("utf-8"))




---

# 兼容python2 和python3

	建立2个名字类似的文件，	一个python2，一个python3， 启动的时候也是分别启动，那个平台启动对应的py
	安装python3的目录下面python.exe改名为python3.exe
	大部分代码在调用str = unicode(str, "utf-8")的改为调用自定义接口函数zsw_python2_3_unicode_str(str)
	接口里面会定义平台不同使用的函数 ，也是分开的文件， 在启动的时候， import进去的


# struct

	python中的struct主要是用来处理C结构数据的，读入时先转换为Python的字符串类型，然后再转换为Python的结构化类型，比如元组(tuple)啥的~。一般输入的渠道来源于文件或者网络的二进制流。

	import struct
	# native byteorder
	buffer = struct.pack("ihb", 1, 2, 3)
	print repr(buffer)
	print struct.unpack("ihb", buffer)
	# data from a sequence, network byteorder
	data = [1, 2, 3]
	buffer = struct.pack("!ihb", *data)		//网络字节序
	print repr(buffer)
	print struct.unpack("!ihb", buffer)

# byte

	文件和网络经常读取数据流，读出到byte数组之后， 可以通过byte[:10]对数组进行分割， 然后struct进行转换和处理


----

# gevent

	gevent	基于事件的非阻塞网络io高性能的Python并发框架	http://www.gevent.org/contents.html
	gevent  是一个网络库：libevent是一个事件分发引擎，greenlet提供了轻量级线程的支持
	gevent的特点总结是：事件驱动+协程+非阻塞IO，事件驱动值得是libvent对epool的封装，来基于事件的方式处理IO。
	
# python GIL 全局锁
	
	GIL导致python性能很差， 所以尽量用multiprocess替代Thread， 但是缺点是多进程不能共享变量， 导致操作复杂
	
# Twisted 
	
	严格遵循类继承结构的组织，非常像java
	Twisted提供了很多协议的实现，过于复杂
	Twisted是异步编程模型，后来出现了协程，使用起来更加方便快捷
	
# firefly引擎

	采用Twisted， gevent开发的引擎，很久不维护
	
---	
	
	
	