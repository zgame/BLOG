# Web框架

### Express

	1）Express的学习曲线并不陡峭，可以很快上手；
	2）Express 有非常庞大的社区，和组织良好的文档，新手可以很容易得到所需要的一切。


### Sail

	Sail.js 既给开发者提供了一个优秀的 MVC 框架，也提供了一定的灵活性，让开发者可以自主选择前端开发方式和后端的数据库。
	除了传统的HTTP RESTful外还同时支持websocket - 同一个请求协议既可以通过Ajax发送, 也可以通过websocket发送, 这一点让人赞赏.
	相当于针对典型应用框架所需组件在Express基础上的集成封装, 
	优点: 开箱即用的全功能Express增强框架, 内置支持websocket 
	缺点:(据说)ORM性能不好


### KOA

	KOA 框架本身非常小，只打包了一些必要的功能，但是它本身通过良好的模块化组织，让开发人员可以按照自己的想法来实现一个扩展性非常好的应用。

### Meteor

	Meteor 框架是 Node.js 上最出色的全栈框架。项目在 GitHub 上有 28K+ 的赞，拥有大量的自定义包，庞大的社区支持，非常好的教程和文档。
	在这个领域 Meteor 毫无疑问是王者，你可以用它构建纯 Javascript 的实时 Web 和 手机应用。
	一个完全统一前后台开发的一站式框架, 从后台数据库到前端view全部包含在内, 特别适合于重度依赖websocket的SPA(单页面应用)开发, 国外流行的Asana就是完全采用Meteor框架开发.
	优点:一站式解决方案, 前后台一体开发, 强大的websocket + mongoDB支持 
	缺点:自由度不够, 和传统的Web框架概念差异较大.


### Derby.js

	也是一个全栈框架。它运行在 Nodejs + mongo + Redis 的上层

### Socket Stream

	它更适合做单页 web 应用，多用户游戏，聊天客户端，网络应用，交易平台以及所有的需要将数据从服务端实时推送到客户端的应用。
	服务端和客户端使用 JSON 来传输数据，比较理想的是使用 websockets 在服务端事件发生时自动将数据推送到客户端，

### Mean

	Mean 是 Mongo DB，Express，Angular 和 Node.js 捆绑在一起的组合。基本上说只要有它，你就拥有了数据库层，服务器端和网页前端的整套工具，足以开发所有类型的现代网络应用。

### Hapi

	Hapi 是为数不多的不依赖于 Express 的 node.js 框架


---
---
---


# 回调函数

	var fs = require("fs");

	fs.readFile('input.txt', function (err, data) {
	    if (err) return console.error(err);
	    console.log(data.toString());
	});
	
	console.log("程序执行结束!");


# 事件

	var EventEmitter = require('events').EventEmitter; 
	var event = new EventEmitter(); 
	event.on('some_event', function() { 		//绑定
    console.log('some_event occured.'); 
	}); 

    event.emit('some_event'); 			//触发

# buffer

	var buf = new Buffer(10);
	buf.length;
	buf.slice([start[, end]])   //缓冲区裁剪
	Buffer.concat(list[, totalLength])
	buf.toJSON()
	buf.toString([encoding[,start[,end]]])
	buf.write(string[, offset[, length]][, encoding])


# 模块文件

	var hello = require('./hello');
	hello.world();      //调用其他文件中的函数


	function Hello() { 
	 var name; 
	    this.setName = function(thyName) { 
	       name = thyName; 
	  }; 
	   this.sayHello = function() { 
	     console.log('Hello ' + name); 
	  }; 
	}; 
	module.exports = Hello;				//直接把类写成一个文件

# 路由

	var http = require("http");
	var url = require("url");

    var pathname = url.parse(request.url).pathname;


# 输出

	console.log(util.inspect(obj));      //把obj转换成string，方便调试



# NPM

	npm install express -g  //全局安装， 包在电脑任意一个文件夹都可以被引用
	如果没有用到-g，那么就会安装到命令行所显示的文件夹里。

	npm list -g        //全局包安装路径


# express框架

	$ npm install express --save

	var express = require('express');
	var app = express();
	
	app.get('/', function (req, res) {			//这里的目录地址，代表着路由,django里面的urls
	   res.send('Hello World');
	})
	
	var server = app.listen(8081, function () {
	
	  var host = server.address().address
	  var port = server.address().port
	
	  console.log("应用实例，访问地址为 http://%s:%s", host, port)
	
	})



	Request 对象 - request对象表示HTTP请求，包含了请求查询字符串，参数，内容，HTTP头部等属性。常见属性有：
	req.app：当callback为外部文件时，用req.app访问express的实例
	req.baseUrl：获取路由当前安装的URL路径
	req.body / req.cookies：获得「请求主体」/ Cookies
	req.fresh / req.stale：判断请求是否还「新鲜」
	req.hostname / req.ip：获取主机名和IP地址
	req.originalUrl：获取原始请求URL
	req.params：获取路由的parameters
	req.path：获取请求路径
	req.protocol：获取协议类型
	req.query：获取URL的查询参数串
	req.route：获取当前匹配的路由
	req.subdomains：获取子域名
	req.accpets（）：检查请求的Accept头的请求类型
	req.acceptsCharsets / req.acceptsEncodings / req.acceptsLanguages
	req.get（）：获取指定的HTTP请求头
	req.is（）：判断请求头Content-Type的MIME类型

	Response 对象 - response对象表示HTTP响应，即在接收到请求时向客户端发送的HTTP响应数据。常见属性有：
	res.app：同req.app一样
	res.append（）：追加指定HTTP头
	res.set（）在res.append（）后将重置之前设置的头
	res.cookie（name，value [，option]）：设置Cookie
	opition: domain / expires / httpOnly / maxAge / path / secure / signed
	res.clearCookie（）：清除Cookie
	res.download（）：传送指定路径的文件
	res.get（）：返回指定的HTTP头
	res.json（）：传送JSON响应
	res.jsonp（）：传送JSONP响应
	res.location（）：只设置响应的Location HTTP头，不设置状态码或者close response
	res.redirect（）：设置响应的Location HTTP头，并且设置状态码302
	res.send（）：传送HTTP响应
	res.sendFile（path [，options] [，fn]）：传送指定路径的文件 -会自动根据文件extension设定Content-Type
	res.set（）：设置HTTP头，传入object可以一次设置多个头
	res.status（）：设置HTTP状态码
	res.type（）：设置Content-Type的MIME类型


	
	
	var cookieParser = require('cookie-parser')
	
	var app = express()
	app.use(cookieParser())


	set DEBUG=myapp & npm start   // windows 启动express服务器

	或者直接用webstorm创建一个nodejs+express app，然后run bin/www





	

# jade

	http://jade-lang.com/reference/attributes	//手册

	node 模板引擎，动态加载，改完不用重启服务器，是精简的html

	// html格式
	div(id="content", class='main')
	    a(href='http://csdn.net', title='csdn主页'， target='_blank') 软件联盟
	    form(action="/login")
	        button(type="submit", value="提交")

	// 普通注释，会输出到渲染后生成的HTML页面

	---------------------------------------------------
	// 添加javascript代码
	script.
    console.log("Hello world!");
    setTiemout(function() {
        window.location.href = "http://csdn.net"
    }, 1000);

    console.log("Good bye!");
	---------------------------------------------------
	// ID，class简写
	div#content
    p.lead.center
        | Pandora_galen
        #side-bar.pull-right  // 没有标签名，默认为“div”
        span.contact.span4
            a(href="/contact") contact me
	---------------------------------------------------
	



	each value, key in languages
        p= key + ":" + value
	--------------------------------------------------- 
	

# sails

	npm install sails -g		//安装

	sails new test-project		//创建

	cd test-project

	sails lift				//开启
	webstorm run app.js

	
	api/controllers ：控制层，该层是Http请求的入口。Sails官方建议该层只处理请求的转发和页面的渲染，具体的逻辑实现应该交给Service层。
	api/models：模型层，在Sails中，对于Model采用的是充血模型，除了可以在模型中定于属性之外，还可以定义包含逻辑处理的函数。在Sails中，所有Model都可以全局性访问。
	api/policies：过滤层，该层在Controller层之前对Http请求做处理，在这一层中，可以定于一些规则来过滤Http请求，比如身份认证什么的。
	api/responses：http响应的方法都放这里，例如服务器错误、请求错误、404错误等，定义在responses文件夹里面的方法，都会赋值到controller层的req对象中。
	api/services：服务层，该层包含逻辑处理的方法，在Sails中，所有Service都可以全局性访问。
	
	assets/
	资源文件夹，在Sails启动的时候，会启动某一个Grunt任务，把assets文件夹里的内容或压缩或编译或复制到根目录下的.tmp目录，这是前端可以直接通过路由访问的资源，HTML、JS、CSS以及图片等静态资源都放在这里了。
		