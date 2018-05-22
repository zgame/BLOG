

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


