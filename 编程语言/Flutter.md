# Flutter 

	Flutter是Google一个新的用于构建跨平台的手机App的SDK。写一份代码，在Android 和iOS平台上都可以运行，并且性能与构建思路几乎最接近原生开发的框架。


# 优点


	Dart是一个静态语言，这也是相对于js的一个优势。
	
	Flutter的路由传值非常方便，push一个路由，会返回一个Future对象（也就是Promise对象），使用await或者.then就可以在目标路由pop，回到当前页面时收到返回值。

	Flutter支持单例模式，单例模式的实现也非常简单。

# 跨平台技术

	h5 没有flutter效率好，而且不能使用原生的一些功能
	java + 原生渲染	快应用，Weex（不是很好）,React Native


#  设置编译环境，用国内镜像

	1. 修改flutter sdk 里 flutter.gradle，参考路径：C:\flutter_windows_1.17.1-stable\flutter\packages\flutter_tools\gradle

	buildscript {
	    repositories {
	        //google()
	        //jcenter()
	        maven { url 'https://maven.aliyun.com/repository/google' }
	        maven { url 'https://maven.aliyun.com/repository/jcenter' }
	        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
		}


	2. 同样也要修改项目build.gradle，注意这里2个地方都要修改


# 设置模拟器

	android studio tools -> 设置sdk manager 和avd manager

	
# flutter web

	flutter config --enable-web
	flutter create .
	flutter run -d chrome


# 
