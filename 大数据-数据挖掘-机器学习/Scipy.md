# 科学计算

	scipy.cluster	矢量量化 / K-均值
	scipy.constants	物理和数学常数
	scipy.fftpack	傅里叶变换
	scipy.integrate	积分程序
	scipy.interpolate	插值
	scipy.io	数据输入输出
	scipy.linalg	线性代数程序
	scipy.ndimage	n维图像包
	scipy.odr	正交距离回归
	scipy.optimize	优化
	scipy.signal	信号处理
	scipy.sparse	稀疏矩阵
	scipy.spatial	空间数据结构和算法
	scipy.special	任何特殊数学函数
	scipy.stats	统计


# scipy.special

	贝塞尔函数，如scipy.special.jn() (整数n阶贝塞尔函数)
	椭圆函数: scipy.special.ellipj() (雅可比椭圆函数，……)
	伽马函数：scipy.special.gamma()，还要注意scipy.special.gammaln,这个函数给出对数坐标的伽马函数，因此有更高的数值精度。

# scipy.linalg

	scipy.linalg.det()函数计算方阵的行列式
	scipy.linalg.svd()奇异值分解(SVD)

# scipy.fftpack

	scipy.fftpack.fftfreq()函数将生成取样频率，scipy.fftpack.fft()将计算快速傅里叶变换：
	scipy.fftpack.ifft函数计算滤波信号

# scipy.optimize
	
	scipy.optimize.fmin_bfgs() 梯度下降
	scipy.optimize.fminbound()限制范围
	scipy.optimize.fsolve()

# scipy.stats

	stats.ttest_ind
	stats.scoreatpercentile

# scipy.interpolate 插值

	scipy.interpolate.interp1d类会构建线性插值函数
	scipy.interpolate.linear_interp

# scipy.integrate 数值积分

	scipy.integrate.quad()

# scipy.signal

	scipy.signal.detrend()：移除信号的线性趋势
	scipy.signal.resample():使用FFT重采样n个点。
	中值滤波scipy.signal.medfilt()
	维纳滤波scipy.signal.wiener()

# scipy.ndimage

	ndimage.shift 
	ndimage.rotate 旋转
	scipy.ndimage.filters 滤镜