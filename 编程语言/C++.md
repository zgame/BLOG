# 关于内存控制

	用malloc或new申请内存之后，应该立即检查指针值是否为NULL。防止使用指针值为NULL的内存。
	不要忘记为数组和动态内存赋初值。防止将未被初始化的内存作为右值使用。
	避免数组或指针的下标越界，特别要当心发生“多1”或者“少1”操作。
	动态内存的申请与释放必须配对，防止内存泄漏。
	用free或delete释放了内存之后，立即将指针设置为NULL，防止产生“野指针”。


  	calloc申请内存空间后，会自动初始化内存空间为 0，但是malloc不会进行初始化，其内存空间存储的是一些随机数据。
	realloc动态分配一个长度为size的内存空间，并把内存空间的首地址赋值给ptr，把ptr内存空间调整为size。    申请的内存空间不会进行初始化。
	new是动态分配内存的运算符，自动计算需要分配的空间，在分配类类型的内存空间时，同时调用类的构造函数，对内存空间进行初始化，即完成类的初始化工作。动态分配内置类型是否自动初始化取决于变量定义的位置，在函数体外定义的变量都初始化为0，在函数体内定义的内置类型变量都不进行初始化。
	
	Obj *objects = new Obj[100]; // 创建100个动态对象
	delete []objects; // 正确的用法
	
	auto_ptr 智能指针 不用delete

	将析构函数定义为私有， 那么无法通过new来创建对象

---
# 定义
	指针常量 & 常量指针 const 离谁近，就修饰谁
	
	函数指针：指向函数的指针变量。
	指针函数：带指针的函数，也就是返回指针的函数。
	
	typedef不是简单的替换，要看成一种新的命名
	
	explicit 只对构造函数起作用，用来抑制隐式转换

---
# 字符串

	char * s = “sdsdsd”； //	指针指向字符串时，字符串是常量，存储在常量区，而指针存储在栈区，不能对其操作修改。


	char,TCHAR,WCHAR的不同之处
	CHAR实施上就是unsigned char,WCHAR为宽字符，而TCHAR根据是否支持unicode而不同。 
	
	CString myStr(L"test string");  
	L""表示宽字符 
	TEXT("")  变为宽字符unicode
	
	// 字符串分割函数
	AfxExtractSubString( strTmp, (LPCTSTR)strFullString, 0, '-');//strTmp的内容为abcd

	inet_addr的功能是将一个ip地址字符串转换成一个整数值

	GetBuffer，MFC函数，这个函数是为一个CString对象重新获取其内部字符缓冲区的指针，返回的LPTSTR为非const的，从而允许直接修改CString中的内容。


	ZeroMemory // 内存地址清零




# MFC

	InitCommonControlsex 如果一个运行在 Windows XP 上的应用程序清单指定要使用 ComCtl32.dll 版本 6 或更高版本来启用可视化方式

	AfxSocketInit()MFC中的函数 AfxSocketInit() 包装了函数 WSAStartup(), 在支持WinSock的应用程序的初始化函数IninInstance()中调用AfxSocketInit()进行初始化, 程序则不必调用WSACleanUp()

	AfxInitRichEdit2() 调用此函数加载 RICHED20.DLL，并初始化 2.0 版的 rich edit 控件。

	WSAStartup，即WSA(Windows Sockets Asynchronous，Windows异步套接字)的启动命令。

	AfxEnableControlContainer()函数是允许应用程序作为控件容器来使用

	利用GetPrivateProfileString读取配置文件(.ini)
	GetPrivateProfileString("NETWORK", "LocalHost", "", add, sizeof(add), "e:\\test.ini");  

# 编译

	速度慢可以用联合编译工具incredibuild
	


# 调试

	应用程序报错可以，调试->附件到进程进行查看


# socket

	如果称某个系统所采用的字节序为主机字节序，则它可能是小端模式的，也可能是大端模式的。 
	而端口号和IP地址都是以网络字节序存储的，不是主机字节序，网络字节序都是大端模式。 
	要把主机字节序和网络字节序相互对应起来，需要对这两个字节存储优先顺序进行相互转化。 
	这里用到四个函数：htons(),ntohs(),htonl()和ntohl(). 
	这四个地址分别实现网络字节序和主机字节序的转化，这里的h代表host,n代表network，s代表short，l代表long。 

	htonl 表示 host to network long ，用于将主机 unsigned int 型数据转换成网络字节顺序； 
	htons 表示 host to network short ，用于将主机 unsigned short 型数据转换成网络字节顺序； 
	ntohl、ntohs 的功能分别与 htonl、htons 相反。


# 输出

	std::cout << "Hello, World!" << std::endl;
	printf("");
	%d 十进制有符号整数
	%u 十进制无符号整数
	%f 浮点数
	%s 字符串
	%c 单个字符
	%p 指针的值
	%e 指数形式的浮点数
	%x, %X 无符号以十六进制表示的整数
	%o 无符号以八进制表示的整数
	%g 把输出的值按照%e或者%f类型中输出长度较小的方式输出
	%p 输出地址符
	%lu 32位无符号整数
	%llu 64位无符号整数


# 引用

	定义h头文件， #include "dir/***.h" 引用自己目录的，  
	而#include <iostream> //尖括号代表系统的


# 取反~
	
	~0 = -1   // 全是0，取反，全是1


# 内存对齐的3大规则:

	对于结构体的各个成员，第一个成员的偏移量是0，排列在后面的成员其当前偏移量必须是当前成员类型的整数倍
	结构体内所有数据成员各自内存对齐后，结构体本身还要进行一次内存对齐，保证整个结构体占用内存大小是结构体内最大数据成员的最小整数倍
	如程序中有#pragma pack(n)预编译指令，则所有成员对齐以n字节为准(即偏移量是n的整数倍)，不再考虑当前类型以及最大结构体内类型

	在64位系统下，地址占64位, 即指针占64位，8个字节
	
# 精度

	由于计算机二进制表示浮点数有精度的问题，0.0(浮点double)实际上不是0，而是非常接近零的小数

# 宏定义

	宏定义是直接替换， 注意，没有括号的


# ++
	
	++i ，先自增再返回，  i++， 先返回再自增，  ++i速度快


# 柔性数组

	char data[0];请去百度  柔性数组,它只能放在结构体末尾,是
	申明一个长度为0的数组，就可以使得这个结构体是可变长的。对于编译器来说，此时长度为0的数组并不占用空间，因为数组名本身不占空间，它只是一个偏移量， 数组名这个符号本身代 表了一个不可修改的地址常量 （注意：数组名永远都不会是指针！ ），但对于这个数组的大小，我们可以进行动态分配 请仔细理解后半部分，对于编译器而言，数组名仅仅是一个符号，它不会占用任何空间，它在结构体中，只是代表了一个偏移量，代表一个不可修改的地址常量！
	 对于0长数组的这个特点，很容易构造出变成结构体，如缓冲区，数据包等等：
	注意:构造缓冲区就是方便管理内存缓冲区,减少内存碎片化,它的作用不是标志结构体结束,而是扩展
	柔性数组是C99的扩展，简而言之就是一个在struct结构里的标识占位符（不占结构struct的空间）

# 函数隐藏

	基类定义，子类重复定义，但是还没有virtual修饰，就隐藏了， 采用基类的函数定义， 如果有virtual，那么就用子类的
	隐藏触发的结果:指针对成员的函数调用取决于指针类型


# STL 容器（Containers）
	
	//string
	#include <string>
	string s2 = s1; //拷贝初始化，深拷贝字符串
	string s8 = s3 + s6;//将两个字符串合并成一个


	//vector
	vector<int> v1;
	v1.push_back(i);
	v5.pop_back(); //删除最后一个元素
	v5.insert(v5.begin()+1,9); //在第二个位置插入新元素
	
	//set 红黑树实现，自动排序
	set跟vector差不多，它跟vector的唯一区别就是，set里面的元素是有序的且唯一的，只要你往set里添加元素，它就会自动排序，而且，如果你添加的元素set里面本来就存在，那么这次添加操作就不执行。

	//list
	list<int> l1{ 1,2,3,4,5,5,6,7,7 };
	l1.sort();

	//map 红黑树实现，自动排序
	map<string, int> m1; //<>里的第一个参数表示key的类型,第二个参数表示value的类型
    m1["Kobe"] = 100;

	//优先队列：使用最大堆实现，用 vector 存储。

	
# STL 算法（Algorithms）




# STL 迭代器（iterators）

	string str("hi sysu");
	for (string::iterator it = str.begin(); it != str.end(); it++)
	{
	    cout << *it << endl;
	}


#内联函数inline：
	引入内联函数的目的是为了解决程序中函数调用的效率问题，这么说吧，程序在编译器编译的时候，编译器将程序中出现的内联函数的调用表达式用内联函数的函数体进行替换，而对于其他的函数，都是在运行时候才被替代。这其实就是个空间代价换时间的i节省。所以内联函数一般都是1-5行的小函数。在使用内联函数时要留神：
	
	1.在内联函数内不允许使用循环语句和开关语句；
	2.内联函数的定义必须出现在内联函数第一次调用之前；
	3.类结构中所在的类说明内部定义的函数是内联函数。

