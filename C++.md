# 关于内存控制

	用malloc或new申请内存之后，应该立即检查指针值是否为NULL。防止使用指针值为NULL的内存。
	不要忘记为数组和动态内存赋初值。防止将未被初始化的内存作为右值使用。
	避免数组或指针的下标越界，特别要当心发生“多1”或者“少1”操作。
	动态内存的申请与释放必须配对，防止内存泄漏。
	用free或delete释放了内存之后，立即将指针设置为NULL，防止产生“野指针”。
	
	Obj *objects = new Obj[100]; // 创建100个动态对象
	delete []objects; // 正确的用法
	
	auto_ptr 智能指针 不用delete

---
# 定义
	指针常量 & 常量指针 const 离谁近，就修饰谁
	
	函数指针：指向函数的指针变量。
	指针函数：带指针的函数，也就是返回指针的函数。
	
	typedef不是简单的替换，要看成一种新的命名
	
	explicit 只对构造函数起作用，用来抑制隐式转换

---
# 字符串
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


# socket

	如果称某个系统所采用的字节序为主机字节序，则它可能是小端模式的，也可能是大端模式的。 
	而端口号和IP地址都是以网络字节序存储的，不是主机字节序，网络字节序都是大端模式。 
	要把主机字节序和网络字节序相互对应起来，需要对这两个字节存储优先顺序进行相互转化。 
	这里用到四个函数：htons(),ntohs(),htonl()和ntohl(). 
	这四个地址分别实现网络字节序和主机字节序的转化，这里的h代表host,n代表network，s代表short，l代表long。 

	htonl 表示 host to network long ，用于将主机 unsigned int 型数据转换成网络字节顺序； 
	htons 表示 host to network short ，用于将主机 unsigned short 型数据转换成网络字节顺序； 
	ntohl、ntohs 的功能分别与 htonl、htons 相反。



	








