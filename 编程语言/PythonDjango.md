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
    

	
