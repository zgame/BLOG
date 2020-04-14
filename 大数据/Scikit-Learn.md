
	Scikit-learn的基本功能主要被分为六大部分：
	分类，回归，聚类，数据降维，模型选择和数据预处理

	由于Scikit-learn本身不支持深度学习，也不支持GPU加速，
	因此这里对于MLP的实现并不适合于处理大规模问题。

# 分类

	sklearn.naive_bayes 朴素贝叶斯
	sklearn.svm支持向量机（SVM）
	sklearn.neighbors最近邻
	逻辑回归，随机森林，
	sklearn.tree决策树
	以及多层感知器（MLP）神经网络sklearn.neural_network


# 回归

	支持向量回归（SVR），脊回归，Lasso回归，弹性网络（Elastic Net），最小角回归（LARS ），贝叶斯回归，以及各种不同的鲁棒回归算法

# 聚类

	K-均值聚类，谱聚类，均值偏移，分层聚类，DBSCAN聚类

# 数据降维sklearn.decomposition

	主成分分析（PCA）、非负矩阵分解（NMF）或特征选择等降维技术来减少要考虑的随机变量的个数，其主要应用场景包括可视化处理和效率提升。

# 模型选择sklearn.model_selection

	是指对于给定参数和模型的比较、验证和选择，其主要目的是通过参数调整来提升精度。目前Scikit-learn实现的模块包括：格点搜索，
	model_selection.cross_validate交叉验证和各种针对预测误差评估的度量函数。

#  数据预处理sklearn.preprocessing
	
	是指数据的特征提取和归一化，是机器学习过程中的第一个也是最重要的一个环节。这里归一化是指将输入数据转换为具有零均值和单位权方差的新变量，但因为大多数时候都做不到精确等于零，因此会设置一个可接受的范围，一般都要求落在0-1之间。而特征提取是指将文本或图像数据转换为可用于机器学习的数字变量。


# sklearn.mixture 高斯混合
# sklearn.gaussian_process:高斯过程

# sklearn.linear_model 广义线性模型
	
	linear_model.LinearRegression 普通最小二乘线性回归	

# sklearn.metrics:指标

	metrics.get_scorer(得分)

# sklearn.datasets:数据集

# sklearn.decomposition矩阵分解,降维

	模块包括矩阵分解 算法,包括PCA、NMF或ICA。 大多数的算法 这个模块可以被视为降维技术。

# sklearn.covariance:协方差估计

# sklearn.cluster:聚类

	cluster.KMeans

