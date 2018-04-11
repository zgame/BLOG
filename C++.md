用malloc或new申请内存之后，应该立即检查指针值是否为NULL。防止使用指针值为NULL的内存。
不要忘记为数组和动态内存赋初值。防止将未被初始化的内存作为右值使用。
避免数组或指针的下标越界，特别要当心发生“多1”或者“少1”操作。
动态内存的申请与释放必须配对，防止内存泄漏。
用free或delete释放了内存之后，立即将指针设置为NULL，防止产生“野指针”。


Obj *objects = new Obj[100]; // 创建100个动态对象
delete []objects; // 正确的用法

auto_ptr 只能指针 不用delete

指针常量 & 常量指针 const 离谁近，就修饰谁

函数指针：指向函数的指针变量。
指针函数：带指针的函数，也就是返回指针的函数。

typedef不是简单的替换，要看成一种新的命名

explicit 只对构造函数起作用，用来抑制隐式转换


char,TCHAR,WCHAR的不同之处
CHAR实施上就是unsigned char,WCHAR为宽字符，而TCHAR根据是否支持unicode而不同。 

CString myStr(L"test string");   L""表示宽字符 ， TEXT("")












