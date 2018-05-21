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
	global $x,$y; 

	局部变量使用static之后，每次调用函数，变量会保留着函数前一次被调用时的值。

	define("GREETING", "Welcome to w3cschool.cn!");  // 常量的定义，php7可以定义常量数组

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

	echo $this->url . PHP_EOL;
	PHP_EOL 为换行符。

# 字符串

	echo $txt1 . " " . $txt2;        //字符串链接

	

# 数组

	$cars=array("Volvo","BMW","Toyota");
	支持数组的+，-运算
	

	$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43"); 	 // 关联数组， 哈希表

	sizeof()				//数组长度， 跟count一样
	count() 				//用于返回数组的长度
	range()				//创建一个包含指定范围的元素的数组
	current()	返回数组中的当前元素。
	pos()	current() 的别名。
	
	in_array()	检查数组中是否存在指定的值。
	list()	把数组中的值赋给一些数组变量。
	
	prev()	将数组的内部指针倒回一位。
	next()	将数组中的内部指针向前移动一位。
	
	array_values()	返回数组中所有的值。
	array_walk()	对数组中的每个成员应用用户函数。
	array_search()	在数组中搜索给定的值，如果成功则返回相应的键名。
	array_key_exists()	检查指定的键名是否存在于数组中。
	
	array_pop()	删除数组中的最后一个元素（出栈）。
	array_push()	将一个或多个元素插入数组的末尾（入栈）。
	
	$t = array_splice($arr, 1, 0, $arr2);   // 在1这个位置插入数组，  关键是0这个位置，表示替换几个
	array_splice($arr,1,1);  				// 把1这个位置的元素删除


	sort() - 对数组进行升序排列
	rsort() - 对数组进行降序排列
	asort() - 根据关联数组的值，对数组进行升序排列
	ksort() - 根据关联数组的键，对数组进行升序排列
	arsort() - 根据关联数组的值，对数组进行降序排列
	krsort() - 根据关联数组的键，对数组进行降序排列


# for循环

	for($x=0;$x<$arrlength;$x++)
	
	foreach (array_expression as $value)		//遍历数组

	foreach($age as $x=>$x_value)				// 遍历哈希表  



# 超级全局变量

	$GLOBALS
	$_SERVER	是一个包含了诸如头信息(header)、路径(path)、以及脚本位置(script locations)等等信息的数组。这个数组中的项目由 Web 服务器创建
	$_REQUEST   用于收集HTML表单提交的数据。
	$_POST		被广泛应用于收集表单数据，在HTML form标签的指定该属性："method="post"。
	$_GET
	$_FILES
	$_ENV
	$_COOKIE
	$_SESSION

# 函数多返回值

	可以返回数组

# 魔术常量

	__LINE__
	__FILE__
	__DIR__
	__FUNCTION__
	__CLASS__
	__TRAIT__
	__METHOD__
	__NAMESPACE__


# 类

	class phpClass {
	  var $var1;
	  var $var2 = "constant string";
	  
	  function myfunc ($arg1, $arg2) {			//默认为公有函数
		}
	}

	
	function __construct( $par1, $par2 ) {   //构造函数
	   $this->url = $par1;
	   $this->title = $par2;
	}

	function __destruct() { }		//析构函数
		
	class Child extends Parent{}    // 继承


 	public $public = 'Public';				//公有成员变量
    protected $protected = 'Protected';
    private $private = 'Private';

	$youj = new Site;
	变量 $this 代表自身的对象。


	interface iTemplate
	{
	    public function setVariable($name, $var);
	    public function getHtml($template);
	}
	
	// 实现接口
	class Template implements iTemplate

	abstract class AbstractClass		//抽象类
	{
	 // 强制要求子类定义这些方法
	    abstract protected function getValue();
	    abstract protected function prefixValue($prefix);
	}


	const constant = '常量值';
	echo  self::constant . PHP_EOL;

	public static $my_static = 'foo';

 	final public function moreTesting()   // 子类不能重写

	parent::__construct()			// 子类调用父类的构造方法


# 命名空间

	命名空间必须是程序脚本的第一条, 除非义源文件编码方式的 declare 语句




# composer

	直接下载安装到php的目录下即可https://getcomposer.org/download/



-----



# Laravel

	composer global require "laravel/installer"		//安装    

	laravel new blog		//创建项目

	php artisan serve		//启动

	

# 路由

	app/Http/routes.php
	
	Route::get('/', function()
	{
	    return 'Hello World';
	});

# 中间件

	app/Http/Middleware

# 控制器

	class UserController extends Controller {

# 请求

	$name = Request::input('name');

# 响应

	return response()->view('hello')->header('Content-Type', $type);

# view

	 return view('greeting', ['name' => 'James']);

# blade

	Blade 是 Laravel 提供的一个既简单又强大的模板引擎。


---



	