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


