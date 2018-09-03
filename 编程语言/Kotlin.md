
# 运行基本的函数

	fun main(args: Array<String>) {
	    println(sum(2, 3))
	}
	
	// 参数默认值，返回值
	fun sum(a: Int=0, b: Int): Int {
	    return a + b
	}


# list

	val items = listOf("apple", "banana", "kiwi")
    



# for循环

	for (index in items.indices) 
	for (item in items)
	for ((k, v) in map) 
	for (i in 1..100) { ... }  // 闭区间: 包括100
	for (i in 1 until 100) { ... } // 半开区间: 不包括100
	for (x in 1..10 step 2) 


# 过滤

	val positives = list.filter { it > 0 }

	data?.let{
		...//如果不为空执行该语句块
	}


# 单例

	object Resource {
		val name = "Name"
	}