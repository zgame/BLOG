# c dll vs制作 

	建dll的win32工程

	tdll.h
	extern "C" _declspec(dllexport)//导出
	void hello();
	
	
	tdll.c
	extern "C" _declspec(dllexport)//导出
	#include <stdio.h>
	#include "tdll.h"
	void hello(){
	 printf("Hello, World zzzzzz!\n");
	}


# c dll vs调用


	建普通win32工程

	copy tdll.h
	
	#include "tdll.h"
	
	int _tmain(int argc, _TCHAR* argv[])
	{
		hello();
		return 0;	
	}

	设置lib目录：
	项目属性- 连接器 - 常规  -附加库目录 ，指定lib文件目录； 或者把h，lib，dll都copy到exe的目录下面

	设置lib文件名：
	项目属性- 连机器- 输入- 附加依赖项，  增加lib的文件名 
	


# dll clion制作

	library.h	
	#define IO_XXX_DLL __declspec(export)
	
	extern "C" {
	IO_XXX_DLL void hello(void);
	}
	
	library.cpp
	IO_XXX_DLL void hello(void) {
	
	}


# dll clion 调用

	library.h
	#define IO_XXX_DLL __declspec(import)

	extern "C"
	{
	IO_XXX_DLL void hello(void);
	} 

	1. 显示调用dll
	main.h
	HINSTANCE handle = LoadLibrary("C:\\Users\\Administrator\\CLionProjects\\cppusedll\\cmake-build-debug\\libcppmakedll.dll");
    typedef void (*pointer)(void);
    pointer f;
    f = (pointer)GetProcAddress(handle, "hello");
    f();
    FreeLibrary(handle);


	2. 编译时候加入
	cmakelists.txt
	#add_library(cppmakedll SHARED library.cpp)
	add_executable(cppusedll main.cpp)
	target_link_libraries(cppusedll C:\\Users\\Administrator\\CLionProjects\\cppusedll\\cmake-build-debug\\libcppmakedll.dll )


# dll golang制作

