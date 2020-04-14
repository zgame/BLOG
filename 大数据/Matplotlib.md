


	import numpy as np
	import matplotlib.pyplot as plt

	x = np.array([1,2,3,4,5,6,7,8])
	y = np.array([3,5,7,6,2,6,10,15])

	# 折线 1 x 2 y 3 color
	plt.plot(x,y,'r')				
	plt.plot(x,y,'g',lw=10)			# 4 line w

	# 柱状
	x = np.array([1,2,3,4,5,6,7,8])
	y = np.array([13,25,17,36,21,16,10,15])
	plt.bar(x,y,0.2,alpha=1,color='b')# 5 color 4 透明度 3 0.9
	plt.show()




	plt.figure() ：自定义画布大小
	plt.subplot() ：设置画布划分以及图像在画布上输出的位置


	plt.xticks(np.linspace(-1, 1, 5))：设置x轴刻度的表现方式
	plt.xlim((-1, 1))：设置x轴刻度的取值范围
	plt.xlabel(u'这是x轴',fontproperties='SimHei',fontsize=14)

	# 绘制散点图
	plt.scatter(x, y, s = 75, c = color, alpha = 0.5)
	# 绘制柱状图, 向上
	plt.bar(x, y1, facecolor = 'blue', edgecolor = 'white')

	# 绘制3D曲面
	ax.plot_surface(X, Y, Z, rstride = 1, cstride = 1, cmap = plt.get_cmap('rainbow'))
	# 绘制从3D曲面到底部的投影
	ax.contour(X, Y, Z, zdim = 'z', offset = -2, cmap = 'rainbow')

	