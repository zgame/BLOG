# 框架

	Laravel一直是PHP开发者最受欢迎的PHP框架。这是一个年轻的框架，但是拥有优雅的语法，可简单快速开发你的应用。它拥有大多数常见的功能，如：路由，身份验证，会话，队列和缓存。

	
	THinkPHP框架是一个快速、兼容而且简单的轻量级国产PHP开发框架

	
	CakePHP最大的缺点就是没有支持面向对象。


	Symfony一直是PHP开发者稳定使用的框架之一。它非常灵活并且功能强大。Symfony有很多可以复用的部分比如：安全、模板、转义、验证、表单配置等。

	Yii2一个基于DRY (Don’t Repeat Yourself) 理念的，拥有简洁编程逻辑的纯面向对象框架。Yii2中整合了jQuery还有一套完整的AJAX机制可以使得很好的扩展你的皮肤和主题功能。总的来说，Yii2框架对于前端转后端的开发者来说很友好。


# 集成开发环境

	wampserver  http://www.wampserver.com/

	配置环境教程（安装，配置，设置参数）
	https://www.w3cschool.cn/phpwmpsql/glrsxa.html


# mysql数据库管理界面

	http://localhost/phpmyadmin/
	root 密码空
	登陆之后修改mysql的密码

# apache

	可以修改apache的配置
	默认的www目录是C:\wamp64\www

# phpstorm

	setting里面配置languages &frameworks -> PHP 
	选择右边的interpreter 添加路径，添加C:\wamp64\bin\php\下面的php.exe

# 语法

	<?php        
	// PHP 代码        
	?>

	$txt="Hello world!"; 
	要在一个函数中访问一个全局变量，需要使用 global 关键字

	局部变量使用static之后，每次调用函数，变量会保留着函数前一次被调用时的值。

	define("GREETING", "Welcome to w3cschool.cn!");  // 常量的定义

	$username = $test ?: 'nobody'; echo $username, PHP_EOL; //三元运算

# 输出

	echo "Study PHP at $txt2";
	echo "My car is a {$cars[0]}";
	//echo可以输出一个或多个字符串
	echo "This", " string", " was", " made", " with multiple parameters.";

	$cars=array("Volvo","BMW","Toyota");
	print_r($cars);		//print_r - 可以输出复杂类型变量的值,如数组,对象

	printf("There are %u million bicycles in %s.",$number,$str);	// 格式化输出字符串
	var_dump() 函数返回变量的数据类型和值

# 字符串

	echo $txt1 . " " . $txt2;        //字符串链接

	

# 数组

	$cars=array("Volvo","BMW","Toyota");
	支持数组的+，-运算
	