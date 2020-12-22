# http压测工具jmeter windows版本

	下载地址：
	https://jmeter.apache.org/download_jmeter.cgi?Preferred=https%3A%2F%2Fmirror.bit.edu.cn%2Fapache%2F

	下载zip版本，解压缩到硬盘上

	配置系统路径：
	JMETER_HOME,值为你解压的jmeter安装路径
	配置classpath变量，%JMETER_HOME%\lib\ext\ApacheJMeter_core.jar;%JMETER_HOME%\lib\jorphan.jar;%JMETER_HOME%\lib/logkit-2.0.jar;


	运行：
	bin\jmeter.bat


# 压测

	新建线程组 -  
	线程组里面新建http请求 - 
	http请求右键新建监听 1. 结果树 2 聚合报告 3 图形
	  