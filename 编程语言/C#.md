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

# 字典

	Dictionary<int,string>myDictionary=newDictionary<int,string>();
	
	myDictionary.Add(1,"C#");
	myDictionary.Add(2,"C++");
	if(myDictionary.ContainsKey(1))
	{
	Console.WriteLine("Key:{0},Value:{1}","1", myDictionary[1]);
	 }
	
	foreach(KeyValuePair<int,string>kvp in myDictionary)
	...{
	Console.WriteLine("Key = {0}, Value = {1}",kvp.Key, kvp.Value);
	}
	Dictionary<int,string>.ValueCollection valueCol=myDictionary.Values;
	foreach(stringvalueinvalueCol)
	...{
	Console.WriteLine("Value = {0}", value);
	}
	myDictionary.Remove(1);


# 特性（Attribute）

	是用于在运行时传递程序中各种元素（比如类、方法、结构、枚举、组件等）的行为信息的声明性标签。您可以通过使用特性向程序添加声明性信息。一个声明性标签是通过放置在它所应用的元素前面的方括号（[ ]）来描述的。
	特性（Attribute）用于添加元数据，如编译器指令和注释、描述、方法、类等其他信息。.Net 框架提供了两种类型的特性：预定义特性和自定义特性。

# 反射（Reflection）

	反射（Reflection） 对象用于在运行时获取类型信息。该类位于 System.Reflection 命名空间中，可访问一个正在运行的程序的元数据。
	System.Reflection 命名空间包含了允许您获取有关应用程序信息及向应用程序动态添加类型、值和对象的类。

# 属性（Property）

	属性（Property） 是类（class）、结构（structure）和接口（interface）的命名（named）成员。类或结构中的成员变量或方法称为 域（Field）。属性（Property）是域（Field）的扩展，且可使用相同的语法来访问。它们使用 访问器（accessors） 让私有域的值可被读写或操作。
	属性（Property）不会确定存储位置。相反，它们具有可读写或计算它们值的 访问器（accessors）。
	例如，有一个名为 Student 的类，带有 age、name 和 code 的私有域。我们不能在类的范围以外直接访问这些域，但是我们可以拥有访问这些私有域的属性。
	访问器（Accessors）
	
	属性（Property）的访问器（accessor）包含有助于获取（读取或计算）或设置（写入）属性的可执行语句。访问器（accessor）声明可包含一个 get 访问器、一个 set 访问器，或者同时包含二者。

# 索引器（Indexer）

	索引器（Indexer） 允许一个对象可以像数组一样被索引。当您为类定义一个索引器时，该类的行为就会像一个 虚拟数组（virtual array） 一样。您可以使用数组访问运算符（[ ]）来访问该类的实例。


	 publis string this[int index]		// 索引器没有名字		类型可以是int，string等类型
	  {
	    get
	    {
	      string temp;
	      if(index>=0 && index<size)
	      {
	        temp = nameList[index];
	      }
	      else
	      {
	        temp = "";
	      }
	      return temp;
	    }
	    set
	    {
	      if(index>=0 && index<size)
	      {
	        nameList[index] = value;
	      }
	    }
	  }

# 委托（Delegate）

	C# 中的委托（Delegate）类似于 C 或 C++ 中函数的指针。委托（Delegate） 是存有对某个方法的引用的一种引用类型变量。引用可在运行时被改变。
	委托（Delegate）特别用于实现事件和回调方法。所有的委托（Delegate）都派生自 System.Delegate 类。
	delegate int NumberChanger(int n);
  	// 创建委托实例
         NumberChanger nc;
         NumberChanger nc1 = new NumberChanger(AddNum);		//参数是一个返回值int的函数
         NumberChanger nc2 = new NumberChanger(MultNum);	//参数是一个返回值int的函数
         nc = nc1;
         nc += nc2;
         // 调用多播
         nc(5);


# 事件（Event）

	事件（Event） 基本上说是一个用户操作，如按键、点击、鼠标移动等等，或者是一些出现，如系统生成的通知。应用程序需要在事件发生时响应事件。例如，中断。事件是用于进程间通信。

	通过事件使用委托
	事件在类中声明且生成，且通过使用同一个类或其他类中的委托与事件处理程序关联。包含事件的类用于发布事件。这被称为 发布器（publisher） 类。其他接受该事件的类被称为 订阅器（subscriber） 类。事件使用 发布-订阅（publisher-subscriber） 模型。

	public delegate void NumManipulationHandler();
    public event NumManipulationHandler ChangeNum;
	EventTest e = new EventTest(); /* 实例化对象,第一次没有触发事件 */
    e.ChangeNum += new EventTest.NumManipulationHandler( printf ); /* 注册 */  这样在调用ChangeNum的时候也会调用prinf



#  集合

	动态数组（ArrayList）
	哈希表（Hashtable）
	排序列表（SortedList）
	堆栈（Stack）
	队列（Queue）
	点阵列（BitArray）

# 泛型（Generic）

	<T>


# 面向对象

	三个基本元素：1封装 2继承 3多态
	五个基本原则： 
	1单一职责原则， 一个类，最好只做一件事 
	2开放封闭原则，软件的功能应该是可扩展的，而尽可能的不修改。
	3Liskov替换原则，子类必须能够替换基类
	4依赖倒置原则，依赖于抽象，不能依赖具体
	5接口隔离原则，使用多个小的专门的接口，执行专门的功能


