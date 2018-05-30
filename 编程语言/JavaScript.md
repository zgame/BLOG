# 语法

	<script>
    alert("我的第一个 JavaScript");
	</script>

	<script src="myScript.js"></script>   // 调用外部的js文件

	voteable=(age<18)?"年龄太小":"年龄已达到";    //三元

# 输出

	console.log(c); 


# 属性

	attr.isId	如果属性是 ID 类型，则 isId 属性返回 true，否则返回 false。
	attr.name	返回属性名称
	attr.value	设置或者返回属性值
	
	nodemap.item()	返回节点列表中处于指定索引号的节点。
	nodemap.length	返回节点列表的节点数目。
	
	attr.firstChild	属性没有子节点
	attr.hasAttributes()	属性没有属性
	attr.hasChildNodes	属性没有子节点
	attr.parentNode	你用来访问属性的 HTML 元素



# 事件



	<button type="button" onclick="alert('欢迎!')">点我!</button>
	<button onclick="myFunction()">Click me</button>

	onsubmit	表单提交时触发


	addEventListener()	允许在目标事件中注册监听事件(IE8= attachEvent())	2
	dispatchEvent()	允许发送事件到监听器上 (IE8 =fireEvent())	2
	removeEventListener()	运行一次注册在事件目标上的监听事件(IE8 =detachEvent())

	handleEvent()	把任意对象注册为事件处理程序


# 元素对象

	element.addEventListener()	向指定元素添加事件句柄
	element.appendChild()	为元素添加一个新的子元素
	element.attributes	返回一个元素的属性数组
	element.childNodes	返回元素的一个子节点的数组

	element.firstChild	返回元素的第一个子节点
	element.hasAttribute()	如果元素中存在指定的属性返回 true，否则返回false。
	element.innerHTML	设置或者返回元素的内容。
	element.nodeName	返回元素的标记名（大写）
	element.removeChild()	删除一个子元素
	element.toString()	一个元素转换成字符串	



# document



	document.addEventListener()	向文档添加句柄
	document.createAttribute()	创建一个属性节点
	document.domain	返回当前文档的域名。

	document.getElementById()	返回对拥有指定 id 的第一个对象的引用。
	getElementsByName
	getElementsByTagName

	document.write()	向文档写 HTML 表达式 或 JavaScript 代码。



# 数组

	var cars = ["Saab", "Volvo", "BMW"];
	var  obj = new Array();
	var obj = new Array(size);

	length
	splice

	concat()	连接两个或更多的数组，并返回结果。
	every()	检测数组元素的每个元素是否都符合条件。
	filter()	检测数组元素，并返回符合条件所有元素的数组。
	indexOf()	搜索数组中的元素，并返回它所在的位置。
	join()	把数组的所有元素放入一个字符串。
	pop()	删除数组的最后一个元素并返回删除的元素。
	push()	向数组的末尾添加一个或更多元素，并返回新的长度。
	slice()	选取数组的的一部分，并返回一个新数组。
	toString()	把数组转换为字符串，并返回结果。
	unshift()	向数组的开头添加一个或更多元素，并返回新的长度。


# json

	var obj = JSON.parse(text);		//将一个JSON字符串转换为 JavaScript对象。

	//用于将 JavaScript 值转换为 JSON 字符串。
	let str_json = JSON.stringify(re, null, 4);     //使用四个空格缩进


# 对象

	{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}



# string

	.length	字符串的长度
	concat()	连接两个或更多字符串，并返回新的字符串。
	fromCharCode()	将 Unicode 编码转为字符。
	search()	查找与正则表达式相匹配的值。
	slice()	提取字符串的片断，并在新的字符串中返回被提取的部分。
	split()	把字符串分割为字符串数组。
	substr()	从起始索引号提取字符串中指定数目的字符。
	substring()	提取字符串中两个指定的索引号之间的字符。

	支持str+int的输出格式

	string(123)
	(123).toString()		//转成字符串

	Number("3.14")  		//字符串转数字
	parseInt()

	d = new Date(); 		//时间转数字
	Number(d)   
	getTime()  


# 全局函数


	escape()	对字符串进行编码。
	eval()	计算 JavaScript 字符串，并把它作为脚本代码来执行。
	isFinite()	检查某个值是否为有穷大的数。
	isNaN()	检查某个值是否是数字。
	Number()	把对象的值转换为数字。
	parseFloat()	解析一个字符串并返回一个浮点数。
	parseInt()	解析一个字符串并返回一个整数。
	String()	把对象的值转换为字符串。


# for

	for (x in person) 
	{
		 console.log(person[i]);
	}

	for(let value of Arr){
	    console.log(value);
	}  


# 函数

	for (i = 1; i < arguments.length; i++)   //可变参


	for (let i = 0; i < 5; ++i) 		
	// let 和var 的区别 ，  let是区块作用域，  var是局部变量
	// ES6新增了let命令，用来声明变量。它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效。
	

	


# es6 

	http://www.runoob.com/w3cnote/es6-concise-tutorial.html


# =>

	var getPrice = function() {
	  return 4.55;
	};
	 
	// Implementation with Arrow Function
	var getPrice = () => 4.55;


# map weakmap

	WeakMap 就是一个 Map，只不过它的所有 key 都是弱引用，意思就是 WeakMap 中的东西垃圾回收时不考虑，使用它不用担心内存泄漏问题。



# Set 和 WeakSet

	类似于 WeakMap，WeakSet 对象可以让你在一个集合中保存对象的弱引用，在 WeakSet 中的对象只允许出现一次

#  迭代器

	var arr = [11,12,13];
	var itr = arr[Symbol.iterator]();
	 
	itr.next(); // { value: 11, done: false }
	itr.next(); // { value: 12, done: false }
	itr.next(); // { value: 13, done: false }
	 
	itr.next(); // { value: undefined, done: true }

# Promises

	ES6 对 Promise 有了原生的支持，一个 Promise 是一个等待被异步执行的对象，当它执行完成后，其状态会变成 resolved 或者rejected。
	var p = new Promise(function(resolve, reject) {  
	  if (/* condition */) {
	    // fulfilled successfully
	    resolve(/* value */);  
	  } else {
	    // error, rejected
	    reject(/* reason */);  
	  }
	});
	每一个 Promise 都有一个 .then 方法，这个方法接受两个参数，第一个是处理 resolved 状态的回调，一个是处理 rejected 状态的回调：
	p.then((val) => console.log("Promise Resolved", val),
	       (err) => console.log("Promise Rejected", err));