

# Laravel

	composer global require laravel/installer		//安装    

	C:\Users\zhushiwei\AppData\Roaming\Composer\vendor\bin 加入到系统path中

	laravel new blog		//创建项目

	php artisan serve		//启动

	artisan  phpscript  arguments填serve  // webstorm运行

	

# 路由

	/routes/web.php
	
	Route::get('/', function()
	{
	    return 'Hello World';
	});

	
	注意：
	Laravel 8路由配置方式：
	use App\Http\Controllers\UserController;
	
	Route::get('/users', [UserController::class, 'index']); 

# 中间件

	app/Http/Middleware

# 控制器

	命令行生成一个控制器
	php artisan make:controller ArticleController

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

# 输出

	dd($outt);		//可以用dd来显示到浏览器上面， 但是会停止运行

	print_r($outt);		// 不会停止运行，推荐使用
    print_r("\n");

	echo		也是会输出到浏览器上


---


# get


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


# post

	任何指向 web 中 POST, PUT 或 DELETE 路由的 HTML 表单请求都应该包含一个 CSRF 令牌(CSRF token)，否则，这个请求将会被拒绝。


# 跨域

	//新建中间件
	php artisan make:middleware CrossHttp

	\app\Http\Middleware\CrossHttp.php
	 public function handle($request, Closure $next) {
        $response = $next($request);
        $response->header('Access-Control-Allow-Origin', '*');
        $response->header('Access-Control-Allow-Headers', 'Origin, Content-Type, Cookie, Accept');
        $response->header('Access-Control-Allow-Methods', 'GET, POST, PATCH, PUT, OPTIONS');
        // $response->header('Access-Control-Allow-Credentials', 'true');
        return $response;
    }


	// 加入到kernel.php 中	


# mysql

	config/database.php  配置数据库

	记住，重要，完事之后，还要配置根目录下面的.env文件
	DB_CONNECTION=mysql
	DB_HOST=127.0.0.1
	DB_PORT=3306
	DB_DATABASE=by_statis_db
	DB_USERNAME=zsw1
	DB_PASSWORD=zsw123

	
	 $users = DB::select("select * from user where name = ?",['zsw']);
     print_r($users);


# 修改端口

	serve --port=5000


# 跨站请求伪造（CSRF）



# 配置参数

	.env增加参数ALI_APP_ID=2016110200785785
	获取env('ALI_APP_ID', ''),
	