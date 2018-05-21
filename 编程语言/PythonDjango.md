# run

	python manage.py runserver 0.0.0.0:8000
	http://127.0.0.1:8000/

	html-----------------------------
	<h1>{{ hello }}</h1>

	view------------------------------
	context          = {}
    context['hello'] = 'Hello World!'
    return render(request, 'hello.html', context)


# 路由urls	



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
    

---


