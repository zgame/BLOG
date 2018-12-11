
# express框架

	$ npm install express --save

	用了 --save 选项， 它还会更新 package.json 文件
	


	var server = app.listen(8081, function () {
	
	  var host = server.address().address
	  var port = server.address().port
	
	  console.log("应用实例，访问地址为 http://%s:%s", host, port)
	
	})



# 路由


	var express = require('express');
	var app = express();
	
	app.get('/', function (req, res) {			//这里的目录地址，代表着路由,django里面的urls
	   res.send('Hello World');
	})


	app.get('/users/:name', function (req, res) {   //这里的路由:代表着参数
	  res.send('hello, ' + req.params.name)
	})


 	res.render('page-login', { title: 'Express', list:[1,2,3,4,5] });

	// 加载中间件 ， next是进行下一个中间件的处理
	app.use(function (req, res, next) {
	  console.log('1')
	  next()
	})



# 请求和响应

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



# cookie
	
	
	var cookieParser = require('cookie-parser')
	
	var app = express()
	app.use(cookieParser())




# 运行

	set DEBUG=myapp & npm start   // windows 启动express服务器

	或者直接用webstorm创建一个nodejs+express app，然后run bin/www



# 目录结构

	//public目录下面放css, js等外部文件
	<link rel="stylesheet" href="/css/normalize.css">

	

# jade （html模板）

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





# 输出

	var debug = require('debug')('exp:server');
	debug('Listening on ' + bind);



# request

	let user = req.query.user;			//获取get请求参数
    let idx = req.query.id;

 	let user_name = req.body.username;		// post请求
    let pwd = req.body.password;


    console.log("user:",user);
    console.log("id:",idx);

    let re = [];
    re.push(user);
    re.push(idx);


# response

	let str_json = JSON.stringify(re, null, 4);     //使用四个空格缩进
    res.send(str_json);




# 前后端分离，跨域设置

	// app.js
	let allowCrossDomain = function (req, res, next) {
	    res.header('Access-Control-Allow-Origin', 'http://localhost:8080'); //必须重新设置，把origin的域加上去
	    res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
	    res.header('Access-Control-Allow-Headers', 'x-custom');
	    res.header('Access-Control-Allow-Credentials', 'true');//和客户端对应，必须设置以后，才能接收cookie.
	    next();
	};
	app.use(allowCrossDomain);


# mysql 

	npm install mysql --save

	//建model目录，db.js--------------------------------
	let mysql = require('mysql');
	let db = {}
	
	//插入操作，注意使用异步返回查询结果
	db.insert = function (connection, sql, paras, callback) {
	    connection.query(sql, paras, function (error, results, fields) {
	        if (error) throw error;
	        callback(results.insertId);//返回插入的id
	    });
	}
	
	//关闭数据库
	db.close = function (connection) {
	    //关闭连接
	    connection.end(function (err) {
	        if (err) {
	            return;
	        } else {
	            console.log('关闭连接');
	        }
	    });
	}
	
	//获取数据库连接
	db.connection = function () {
	    //数据库配置
	    let connection = mysql.createConnection({
	        host: 'localhost',
	        user: 'zsw1',
	        password: 'zsw123',
	        database: 'zsw_db',
	        port: 3306
	    });
	    //数据库连接
	    connection.connect(function (err) {
	        if (err) {
	            console.log(err);
	            return;
	        }
	    });
	    return connection;
	}
	module.exports = db;


	//action-----------------------------------
	let db = require('../model/db');
	let connection = db.connection();
    let  sql = 'SELECT * FROM student';
    connection.query(sql,function (err, result) {
        if (err) {
            console.log('[SELECT  ERROR] - ', err.message);
            return;
        }
        let str_json = JSON.stringify(result, null, 4);     //使用四个空格缩进
        res.send(str_json);
    });


# redis

	let redis = require('redis')
	let dbRedis = {}
	
	
	dbRedis.connection = function () {
	    let client = redis.createClient(6379, '172.16.140.123')
	    client.auth('Soonyo123',function () {
	    // console.log("pwd ok")
	    })
	
	    return client
	}
	
	
	dbRedis.hset = function(client,dir,key,value){
	    client.hset(dir,key,value)
	}
	
	dbRedis.hget = function(client,dir,key){
	    client.hget(dir,key, function(err, value){
	        console.log("value:      ",value)
	    })
	
	    client.keys('All*',function (err,value){		//这是获取keys
	        console.log("keys:      ",value)
	    })
	}
	
	
	
	module.exports = dbRedis;