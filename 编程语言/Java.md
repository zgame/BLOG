# 变量

	局部变量：在方法、构造方法或者语句块中定义的变量被称为局部变量。变量声明和初始化都是在方法中，方法结束后，变量就会自动销毁。
	成员变量：成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。
	类变量：类变量也声明在类中，方法体之外，但必须声明为static类型。



# 常量

	final double PI = 3.1415927;

# 访问限制

	默认的，也称为default，无修饰符就是默认权限，也叫包访问权限，只能被同一包内类访问
	私有的，以private修饰符指定，子类都不可见。
	共有的，以public修饰符指定，对所有类可见。
	受保护的，以protected修饰符指定，对同一包内的类和所有子类可见。

# 抽象类：

	抽象类不能用来实例化对象，声明抽象类的唯一目的是为了将来对该类进行扩充。

# 抽象方法

	抽象方法是一种没有任何实现的方法，该方法的的具体实现由子类提供。

# synchronized修饰符

	synchronized关键字声明的方法同一时间只能被一个线程访问。

# transient修饰符

	序列化的对象包含被transient修饰的实例变量时，java虚拟机(JVM)跳过该特定的变量。
	该修饰符包含在定义变量的语句中，用来预处理类和变量的数据类型。

#volatile修饰符

	volatile修饰的成员变量在每次被线程访问时，都强迫从共享内存中重读该成员变量的值。而且，当成员变量发生变化时，强迫线程将变化值回写到共享内存。这样在任何时刻，两个不同的线程总是看到某个成员变量的同一个值。一个volatile对象引用可能是null。

# for循环

	 for(int x : numbers ){
         System.out.print( x );
         System.out.print(",");
      }

	break主要用在循环语句或者switch语句中，用来跳出整个语句块。
	continue适用于任何循环控制结构中。作用是让程序立刻跳转到下一次循环的迭代。

# 常用类
	Number, Character, String, Stringbuffer, StringBuilder

	和String类不同的是，StringBuffer和StringBuilder类的对象能够被多次的修改，并且不产生新的未使用对象。
	StringBuilder类在Java 5中被提出，它和StringBuffer之间的最大不同在于StringBuilder的方法不是线程安全的（线程安全就是多线程访问时，采用了加锁机制，当一个线程访问该类的某个数据时，进行保护，其他线程不能进行访问直到该线程读取完，其他线程才可使用。不会出现数据不一致或者数据污染。线程不安全就是不提供数据访问保护，有可能出现多个线程先后更改数据造成所得到的数据是脏数据）。
	由于StringBuilder相较于StringBuffer有速度优势，所以多数情况下建议使用StringBuilder类。然而在应用程序要求线程安全的情况下，则必须使用StringBuffer类。

# finalize() 方法

	Java允许定义这样的方法，它在对象被垃圾收集器析构(回收)之前调用，这个方法叫做finalize( )，它用来清除回收对象。
	例如，你可以使用finalize()来确保一个对象打开的文件被关闭了。
	在finalize()方法里，你必须指定在对象销毁时候要执行的操作。

# 重载(Overload)

	重载(overloading) 是在一个类里面，方法名字相同，而参数不同。返回类型呢？可以相同也可以不同。
	每个重载的方法（或者构造函数）都必须有一个独一无二的参数类型列表。


# 重写(Override)

	重写是子类对父类的允许访问的方法的实现过程进行重新编写！返回值和形参都不能改变。即外壳不变，核心重写！

# Java 多态

	多态是同一个行为具有多个不同表现形式或形态的能力。
	多态性是对象多种表现形式的体现。因为多重继承，所以多态.

# 接口

	接口（英文：Interface），在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。
	接口并不是类，编写接口的方式和类很相似，但是它们属于不同的概念。类描述对象的属性和方法。接口则包含类要实现的方法。
	除非实现接口的类是抽象类，否则该类要定义接口中的所有方法。
	接口无法被实例化，但是可以被实现。一个实现接口的类，必须实现接口内所描述的所有方法，否则就必须声明为抽象类。另外，在Java中，接口类型可用来声明一个变量，他们可以成为一个空指针，或是被绑定在一个以此接口实现的对象。

# 数据结构

	枚举（Enumeration）
	位集合（BitSet）
	向量（Vector）	和传统数组非常相似，但是Vector的大小能根据需要动态的变化。
	栈（Stack）实现了一个后进先出（LIFO）的数据结构。
	字典（Dictionary）Dictionary类已经过时了。在实际开发中，你可以实现Map接口来获取键/值的存储功能。
	哈希表（Hashtable）
	属性（Properties）

# Collection接口

	LinkedList继承于 AbstractSequentialList，实现了一个链表。
	ArrayList通过继承AbstractList，实现动态数组。
	HashSet继承了AbstractSet，并且使用一个哈希表。
	TreeSet继承于AbstractSet，使用元素的自然顺序对元素进行排序.
	HashMap 继承了HashMap，并且使用一个哈希表。
	TreeMap 继承了AbstractMap，并且使用一颗树。

# 基本数据类型

	byte，short，int，long，float，double，boolean，char


# Integer类
	
	1、Integer是int的包装类，int则是java的一种基本数据类型 
	2、Integer变量必须实例化后才能使用，而int变量不需要 
	3、Integer实际是对象的引用，当new一个Integer时，实际上是生成一个指针指向此对象；而int则是直接存储数据值 
	4、Integer的默认值是null，int的默认值是0

	Integer wrapperi = new Integer(0);		//转interger
	int i = wrapperi.intValue();			//转int

# String

	 String s = "zsw ok";   // 注意String是不可变的
	 String s1 = s.toUpperCase();   // 要将字符串做变化， 都是通过返回新的字符串来实现的

# Stack Queue 栈（先进后出）和队列（先进先出）

	Stack<Integer> ss = new Stack<Integer>();
        ss.push(8);
        ss.pop();
 	Queue<String> ss2 = new LinkedList<String>();
        ss2.offer("ssssss3");
        ss2.poll();


# 数组array,不可变

	dataType[] arrayRefVar = new dataType[arraySize];
	dataType[] arrayRefVar = {value0, value1, ..., valuek};
	
	//binarySearch 二分法查找，数组必须有序，且存在此数组中，否则返回负数下标
	int binarySearch = Arrays.binarySearch(arr, 3);
	
# ++
	
	array[i++]  ==    	array[i]; i++;  //等价


# 可变数组vector , arraylist

	Vector类中的方法是同步的(线程安全)，而ArrayList中的方法不同步。
	Vector<Integer> vv = new Vector<Integer>();
       vv.add(1);
 	   vv.remove(1);
	ArrayList<Integer> aa = new ArrayList<>();
        aa.add(3);
        aa.remove(new Integer(1));


# map

        Map mm = new HashMap();
        mm.put(1,"ss");
        mm.put(2,"ss2");
        mm.remove(2);
        System.out.println(mm);

# 链表LinkedList

        LinkedList<String> ll = new LinkedList<String>();
        ll.add("1");
        ll.add("2");
        ll.add("3");
        ll.remove("1");    // remove（index）也可以
	 	ll.addFirst("-1");
        System.out.println(ll);



# 序列化对象，反序列化对象

	DeserializeDemo程序实例了反序列化
	ObjectOutputStream 类用来序列化一个对象


# 创建线程的三种方式的对比

	1. 采用实现 Runnable、Callable 接口的方式创建多线程时，线程类只是实现了 Runnable 接口或 Callable 接口，还可以继承其他类。
	2. 使用继承 Thread 类的方式创建多线程时，编写简单，如果需要访问当前线程，则无需使用 Thread.currentThread() 方法，直接使用 this 即可获得当前线程。



# 线程同步器

	A.  semaphore:信号量。用于表示共享资源数量。用acquire()获取资源，用release()释放资源。
	B.  CyclicBarrier  线程到达屏障后等待，当一组线程都到达屏障后才一起恢复执行
	C. CountDownLatch  初始时给定一个值，每次调用countDown值减1，当值为0时阻塞的线程恢复执行


# 知识点

	int溢出， 注意10亿以上要用long，否则会变负数，abs也不行
	1/0 运行时异常报错，  1.0/0.0 是infinity无穷大
	-14%3 = -2   14%-3=2 ， 跟前面的保持一致
	println('a')  //显示a     
	println('a'+'b') // 显示195
	println("a"+'b') // 显示ab

