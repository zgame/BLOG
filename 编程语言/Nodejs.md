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


# undefined

	typeof(exp) == "undefined"

# 转换

	Number(str)

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


	package.json文件记录项目的配置信息， 在部署的时候，运行npm install 即可安装依赖， 自动下载node_modules内容



# yarn

	新一代npm包管理器，npm install yarn -g
	yarn config set registry https://registry.npm.taobao.org

	yarn install  安装依赖包
	yarn start
	yarn run dev


# promise 把异步的语法， 写成同步处理语法

	http://liubin.org/promises-book/        教程电子书

	var promise = getAsyncPromise("fileA.txt"); 
	promise.then(function(result){
	    // 获取文件内容成功时的处理
	}).catch(function(error){
	    // 获取文件内容失败时的处理
	});


