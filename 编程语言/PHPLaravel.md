

# Laravel

	composer global require "laravel/installer"		//安装    

	laravel new blog		//创建项目

	php artisan serve		//启动

	artisan  phpscript  arguments填serve  // webstorm运行

	

# 路由

	/routes/web.php
	
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
	
	 // 路由指定	
	 return view('greeting', ['name' => 'James']);

	/resources/views/welcome.blade.php
	

# blade

	Blade 是 Laravel 提供的一个既简单又强大的模板引擎。


---


# 例子


	Route::get('/search','Home\zswController@zswget');

	namespace App\Http\Controllers\Home;

	public function zswget(Request $request){
        $name=$request->input('user');
        $idx=$request->input('id');

        //echo "user:", $name,"    id:" , $idx;

        $array = [];
        array_push($array,$name);
        array_push($array,$idx);

        //print_r($array);

        return response()->json($array);