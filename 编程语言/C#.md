# using

	java是import ， C#是using


# 常量

	const double pi = 3.14159; // 常量声明

# for

	foreach (int element in fibarray)

# 访问修饰符

	Internal 访问修饰符
	Internal 访问说明符允许一个类将其成员变量和成员函数暴露给当前程序中的其他函数和对象。换句话说，带有 internal 访问修饰符的任何成员可以被定义在该成员所定义的应用程序内的任何类或方法访问。

	

# 引用ref

	 public void swap(ref int x, ref int y)
 	 n.swap(ref a, ref b);

# 数组

	double[] balance = new double[10];

# 动态数组（ArrayList）

	

# 结构

	类和结构有以下几个基本的不同点：
	类是引用类型，结构是值类型。
	结构不支持继承。
	结构不能声明默认的构造函数。
	结构可定义构造函数，但不能定义析构函数。但是，您不能为结构定义默认的构造函数。默认的构造函数是自动定义的，且不能被改变。

# abstract抽象类和虚方法

	子类必须实现抽象方法
 	public override int area ()

	当有一个定义在类中的函数需要在继承类中实现时，可以使用虚方法。虚方法是使用关键字 virtual 声明的。虚方法可以在不同的继承类中有不同的实现。对虚方法的调用是在运行时发生的。

# 