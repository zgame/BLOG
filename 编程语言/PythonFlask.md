# python中处理数据内容之后， 传递给模板进行渲染
	
	模板默认是jinja2


# 调试模式

	如果你启用了调试支持，服务器会在代码修改后自动重新载入
	app.run(debug=True)

# 路由变量

	@app.route('/post/<int:post_id>')			#	int 类型的变量post_id


# 构造 URL

	


# 路由请求方法

	@app.route('/login', methods=['GET', 'POST'])


# 模板渲染

	from flask import Flask, render_template
	return render_template('hello.html', name=name)
	
	<!doctype html>
	<title>Hello from Flask</title>
	{% if name %}
	  <h1>Hello {{ name }}!</h1>
	{% else %}
	  <h1>Hello World!</h1>
	{% endif %}

	模板可以重用

	



# cookies


# session 

	
# 信号

# get

	@app.route('/login', methods=['POST', 'GET'])
	def login():
	    if request.method == 'GET':
	        user = request.args.get('user')
	        idx = request.args.get('id')

# response

	 return Response(json.dumps(data), mimetype='text/plain')


# 前后端分离，跨域

	//新建一个python文件cross_domain
	from functools import wraps
	from flask import make_response
	
	def allow_cross_domain(fun):
	    @wraps(fun)
	    def wrapper_fun(*args, **kwargs):
	        rst = make_response(fun(*args, **kwargs))
	        rst.headers['Access-Control-Allow-Origin'] = '*'
	        rst.headers['Access-Control-Allow-Methods'] = 'PUT,GET,POST,DELETE'
	        allow_headers = "Referer,Accept,Origin,User-Agent"
	        rst.headers['Access-Control-Allow-Headers'] = allow_headers
	        return rst
	    return wrapper_fun


	//路由的时候，调用装饰器
	@app.route('/login', methods=['POST', 'GET'])
	@allow_cross_domain
	def login_route():


# mysql数据库


	//app.py程序入口点

	from flask import Flask
	from flaskext.mysql import MySQL
	
	mysql = MySQL()
	app = Flask(__name__)
	app.config['MYSQL_DATABASE_USER'] = 'zsw1'
	app.config['MYSQL_DATABASE_PASSWORD'] = 'zsw123'
	app.config['MYSQL_DATABASE_DB'] = 'zsw_db'
	app.config['MYSQL_DATABASE_HOST'] = '127.0.0.1'
	mysql.init_app(app)


	// action里面获取数据库数据
	cursor = mysql.connect().cursor()
    cursor.execute("SELECT * from student where true")
    data = cursor.fetchall()
    # data = cursor.fetchone()


# pycharm 数据库工具

	view - tool window - database
	可以在pycharm里面进行sql语句的调试，测试，输出