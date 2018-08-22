# run

	python manage.py runserver 0.0.0.0:8000
	http://127.0.0.1:8000/

	html-----------------------------
	<h1>{{ hello }}</h1>

	view------------------------------
	from django.shortcuts import render
	def hello(request):
		context          = {}
	    context['hello'] = 'Hello World!'
	    return render(request, 'hello.html', context)


# 路由urls	

	url(r'^$', views.hello),


# locals()

	locals()返回一个包含当前作用域里面的所有变量和它们的值的字典。
	
	所以可以把views改写为
	
	    def current_datetime(request):
		    current_date = datetime.datetime.now()
		    return render_to_response('current_datetime.html', locals()) 
	
	这里要注意的是要把now重命名为current_date，因为模板需要的是这个变量名。
	
	在template是如下定义的：
	
	    <html>
	    <body>
	    <font color = "blue">It is is now {{ current_date }}.</font>
	    </body>
	    </html> 
    

# action

	<form class = 'button_one_line' action="/Tyranitar6/server/notice_del_confirm/" method="post" onsubmit="return checkForm()">
    	<input name="uid" type="hidden" value={{row.0}}>
        <button type="submit" class="btn btn-primary" >删除</button>
    </form>


	//路由绑定python的代码函数	notice_del_confirm
	urlpatterns += patterns('game_manager.views.server.notice',
           (r'^server/notice_del_confirm/$', 'notice_del_confirm'),
    

	
# request

	def echoz(request):
	    if request.method == 'GET':
	        user = request.GET.get('user')
        	idx = request.GET.get('id')

	   if request.method == 'POST':
		received_json_data = json.loads(request.body)
        user = received_json_data.get('username')
        idx = received_json_data.get('password', '')


# port 
	
	python manage.py runserver 8080		
	pycharm run里面设定端口


# response

	 return HttpResponse(json.dumps(data), content_type="text/plain")


# 前后端分离，跨域解决

	pip install django-cors-headers


	配置settings.py文件
	INSTALLED_APPS = [
	    ...
	    'corsheaders'，
	    ...
	 ] 
	
	MIDDLEWARE_CLASSES = (
	    ...
	    'corsheaders.middleware.CorsMiddleware',
	    'django.middleware.common.CommonMiddleware', # 注意顺序
	    ...
	)
	#跨域增加忽略
	CORS_ALLOW_CREDENTIALS = True
	CORS_ORIGIN_ALLOW_ALL = True
	CORS_ORIGIN_WHITELIST = (
	    '*'
	)
	
	CORS_ALLOW_METHODS = (
	    'DELETE',
	    'GET',
	    'OPTIONS',
	    'PATCH',
	    'POST',
	    'PUT',
	    'VIEW',
	)
	
	CORS_ALLOW_HEADERS = (
	    'XMLHttpRequest',
	    'X_FILENAME',
	    'accept-encoding',
	    'authorization',
	    'content-type',
	    'dnt',
	    'origin',
	    'user-agent',
	    'x-csrftoken',
	    'x-requested-with',
	    'Pragma',
	)




# mysql

	import pymysql
	
	def get_sql_data(sql):
	    # 打开数据库连接
	    # db = pymysql.connect("55a0ed1bee1a4.sh.cdb.myqcloud.com:6370", "root", "***", "test")
	    db = pymysql.connect("127.0.0.1", "zsw1", "zsw123", "by_statis_db")
	
	    # 使用 cursor() 方法创建一个游标对象 cursor
	    cursor = db.cursor()
	    # 使用 execute()  方法执行 SQL 查询
	    cursor.execute(sql)
	    # 使用 fetchone() 方法获取单条数据.
	    data = cursor.fetchone()
	
	    # print("Database version : %s " % data)
	    db.close()
	
	    return data

	在获取数据的地方直接调用即可
