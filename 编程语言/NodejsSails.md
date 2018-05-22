
# sails

	npm install sails -g		//安装

	sails new test-project		//创建

	cd test-project

	sails lift				//开启
	webstorm run app.js		// webstorm 编辑器运行

	
	api/controllers ：控制层，该层是Http请求的入口。Sails官方建议该层只处理请求的转发和页面的渲染，具体的逻辑实现应该交给Service层。
	api/models：模型层，在Sails中，对于Model采用的是充血模型，除了可以在模型中定于属性之外，还可以定义包含逻辑处理的函数。在Sails中，所有Model都可以全局性访问。
	api/policies：过滤层，该层在Controller层之前对Http请求做处理，在这一层中，可以定于一些规则来过滤Http请求，比如身份认证什么的。
	api/responses：http响应的方法都放这里，例如服务器错误、请求错误、404错误等，定义在responses文件夹里面的方法，都会赋值到controller层的req对象中。
	api/services：服务层，该层包含逻辑处理的方法，在Sails中，所有Service都可以全局性访问。
	
	assets/
	资源文件夹，在Sails启动的时候，会启动某一个Grunt任务，把assets文件夹里的内容或压缩或编译或复制到根目录下的.tmp目录，这是前端可以直接通过路由访问的资源，HTML、JS、CSS以及图片等静态资源都放在这里了。


	/api/responsers 中添加自定义的响应
	waterline //可以跨多个数据库而几乎没有感知
		


	//sails 中文文档
	https://github.com/linxiaowu66/sails-docs-zh-cn/tree/master/concepts


# sails  controller and action
	
	控制器里面可以定义好几个action，控制器文件名为ZswCT1Controller
	路由绑定规则为'GET /zsw2': {action: 'ZswCT1/bye'}, //文件名前面的部分+/+action


	//增加控制器 
 	**注意，必须是驼峰， 首字母大写 **
	sails generate controller Comment create destroy tag like
	Sails将会生成api/controllers/CommentController.js
	里面有后面的4个函数定义,就是action


	// 单独增加action
	** 注意，action不能用驼峰， 不要用下划线，不要用数字， 要用目录**
	sails generate action 


# sails routes自定义路由

	config/routes.js  //手动增加路由

	'GET /contact':         { view:   'pages/contact' },			//view
	'GET /dashboard/zsw_1': {action: 'ZswCT2/hello1'},				//controller 的action
    'GET /hello': 'ZswCT2.hello2',									//同上, 有几种写法, 加不加Controller都可以
  	'GET /zswAction': {action: 'zsw-action'},						// action
	'GET /bar/go': 'foo/go-action'									//同上 ,有几种写法




# sails blueprint隐式路由

	RESTful routes
	比如一个POST请求到/user将会创建一个新的用户

	Shortcut routes
	比如，/user/create?name=joe快捷方式创建一个新的用户

	上面两个需要绑定model和controller, 下面的有controller就可以
	** 注意， 需要在config里面设置blueprint.js打开action: true， 才会开启自动action映射**
	如果你有一个FooController.js文件并带有一个bar方法，那么blueprint会自动创建一条/foo/bar的路由


	/Controller/Action		// 这是controller的隐式路由
	/Action					// 这是直接定义的Action的


# sails view 页面

	
	// 增加页面 
	** 注意，文件名必须是小写， 不能用驼峰，不能用数字，不能用下划线， 要用目录 **
	sails generate page zswp
    //增加一个页面，会在view\pages,api\controllers,assets\styles\pages\***.less , assets\js\pages\***.page.js增加4个文件
	
	
	
		

# 页面

	1. 用view下面的模板copy一个文件出来，改名zsw1
	2. 新增一个action， 设置success: {viewTemplatePath: 'pages/zsw1',},




# ejs （html模板）

	ejs 有 3 种常用标签：
	<% code %>：运行 JavaScript 代码，不输出
	<%= code %>：显示转义后的 HTML内容
	<%- code %>：显示原始 HTML 内容


	<% '脚本' 标签，用于流程控制，无输出。
	<%_ 删除其前面的空格符
	<%= 输出数据到模板（输出是转义 HTML 标签）
	<%- 输出非转义的数据到模板
	<%# 注释标签，不执行、不输出内容
	<%% 输出字符串 '<%'

	%> 一般结束标签
	-%> 删除紧随其后的换行符
	_%> 将结束标签后面的空格符删除



	<%- include('header') %>    // 拆分模板组件，模板可复用，减少重复代码