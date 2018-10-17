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

	* 这里需要注意： windows下面用gcc，需要用mingw， 需要下载64位的版本，否则32位版本不兼容golang

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

	import "C"   //必须加
	需要导出的函数前面增加export+函数名
	//export hello

	编译:
	go build -ldflags "-s -w" -buildmode=c-shared -o exportgo.dll dllmake.go


# dll golang 调用

	// 如果是C C++制作的dll， windows下面要用mingw64位的版本才可以

	调用1:
	DllTestDef := syscall.MustLoadDLL("libcppmakedll.dll")
	add := DllTestDef.MustFindProc("hello")
	ret, _, err := add.Call()

	调用2：
	lib := syscall.NewLazyDLL("libcppmakedll.dll")//exportgo  libcppmakedll
	add := lib.NewProc("hello")
	ret, _, err := add.Call()

