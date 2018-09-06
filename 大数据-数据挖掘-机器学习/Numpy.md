# ndarray 基本数组

	# 多于一个维度  
	import numpy as np 
	a = np.array([[1,  2],  [3,  4]])  
	print a

# dtype 获取类型
 
	#int8，int16，int32，int64 可替换为等价的字符串 'i1'，'i2'，'i4'，以及其他。  

# shape , reshape 多维数组的形状

# asarray	用python数组生成ndarray

# arange linspace logspace	范围生成ndarray

# nditer 迭代器 

# 数组矩阵修改形状

	1.	reshape 不改变数据的条件下修改形状
	2.	flat 数组上的一维迭代器
	3.	flatten 返回折叠为一维的数组副本
	4.	ravel 返回连续的展开数组

# 数组矩阵翻转操作

	1.	transpose 翻转数组的维度
	2.	ndarray.T 和self.transpose()相同
	3.	rollaxis 向后滚动指定的轴
	4.	swapaxes 互换数组的两个轴

# 数组矩阵修改维度

	1.  broadcast 产生模仿广播的对象
	2.	broadcast_to 将数组广播到新形状
	3.	expand_dims 扩展数组的形状
	4.	squeeze 从数组的形状中删除单维条目

# 数组矩阵数组的连接

	1.	concatenate 沿着现存的轴连接数据序列
	2.	stack 沿着新轴连接数组序列
	3.	hstack 水平堆叠序列中的数组(列方向)
	4.	vstack 竖直堆叠序列中的数组(行方向)

# 数组矩阵数组分割

	1.	split 将一个数组分割为多个子数组
	2.	hsplit 将一个数组水平分割为多个子数组(按列)
	3.	vsplit 将一个数组竖直分割为多个子数组(按行)

# 数组矩阵添加/删除元素

	1.	resize 返回指定形状的新数组
	2.	append 将值添加到数组末尾
	3.	insert 沿指定轴将值插入到指定下标之前
	4.	delete 返回删掉某个轴的子数组的新数组
	5.	unique 寻找数组内的唯一元素

# 位操作

	1.	bitwise_and 对数组元素执行位与操作
	2.	bitwise_or 对数组元素执行位或操作
	3.	invert 计算位非
	4.	left_shift 向左移动二进制表示的位
	5.	right_shift 向右移动二进制表示的位

# 字符串函数

	1.	add() 返回两个str或Unicode数组的逐个字符串连接
	2.	multiply() 返回按元素多重连接后的字符串
	3.	center() 返回给定字符串的副本，其中元素位于特定字符串的中央
	4.	capitalize() 返回给定字符串的副本，其中只有第一个字符串大写
	5.	title() 返回字符串或 Unicode 的按元素标题转换版本
	6.	lower() 返回一个数组，其元素转换为小写
	7.	upper() 返回一个数组，其元素转换为大写
	8.	split() 返回字符串中的单词列表，并使用分隔符来分割
	9.	splitlines() 返回元素中的行列表，以换行符分割
	10.	strip() 返回数组副本，其中元素移除了开头或者结尾处的特定字符
	11.	join() 返回一个字符串，它是序列中字符串的连接
	12.	replace() 返回字符串的副本，其中所有子字符串的出现位置都被新字符串取代
	13.	decode() 按元素调用str.decode
	14.	encode() 按元素调用str.encode

# 数学

	numpy.around()
	numpy.floor()
	numpy.ceil()
	numpy.sin
	numpy.cos
	numpy.tan

# 矩阵算数

	add()
	subtract()
	multiply()
	divide()
	numpy.reciprocal()逐元素的倒数
	numpy.power()	幂
	numpy.mod()		除法余数

# 统计函数

	amin
	amax
	ptp  最大值和最小值的差距
	numpy.percentile()百分位数是统计中使用的度量，表示小于这个值得观察值占某个百分比。
	numpy.median()中值定义为将数据样本的上半部分与下半部分分开的值。
	numpy.mean()算术平均值是沿轴的元素的总和除以元素的数量。
	numpy.average()加权平均值是由每个分量乘以反映其重要性的因子得到的平均值。
	std 标准差
	var 方差

# 排序

	numpy.sort() 
	numpy.argsort()函数对输入数组沿给定轴执行间接排序，并使用指定排序类型返回数据的索引数组。
	numpy.lexsort()函数使用键序列执行间接排序。 键可以看作是电子表格中的一列。 
	numpy.argmax() 和 numpy.argmin()这两个函数分别沿给定轴返回最大和最小元素的索引。
	numpy.nonzero()函数返回输入数组中非零元素的索引。
	numpy.where()函数返回输入数组中满足给定条件的元素的索引。
	numpy.extract()函数返回满足任何条件的元素。
	
# 字节交换

	numpy.ndarray.byteswap()函数在两个表示：大端和小端之间切换。
	
# 副本和视图

	copy物理存储在另一个位置
	view相同内存内容的不同视图

# 矩阵库

	matlib.empty()	内容随机
	numpy.matlib.zeros()
	numpy.matlib.ones()
	numpy.matlib.eye()对角线元素为 1，其他位置为零
	numpy.matlib.identity()单位矩阵是主对角线元素都为 1 的方阵。
	numpy.matlib.rand()

# 线性代数

	1.	dot 两个数组的点积
	2.	vdot 两个向量的点积
	3.	inner 两个数组的内积
	4.	matmul 两个数组的矩阵积
	5.	determinant 数组的行列式
	6.	solve 求解线性矩阵方程
	7.	inv 寻找矩阵的乘法逆矩阵

# IO

	load()和save()函数处理 numPy 二进制文件(带npy扩展名)loadtxt()和savetxt()函数处理正常的文本文件

