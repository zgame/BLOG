#HTML标签

	<html>	定义 HTML 文档
	<body>	定义文档的主体
	<br>	这是一个换行标签
	<hr> 标签在 HTML 页面中创建水平线。
	<!-- 这是一个注释 -->

	
	<h1>这是一个标题</h1>
	<p>这是一个段落。</p>
	<a href="http://www.w3cschool.cn">这是一个链接</a>
	<img src="w3cschool.png" width="104" height="142">

### HTML head 元素	

	<head>	定义了文档的信息
	<title>	定义了文档的标题
	<base>	定义了页面链接标签的默认链接地址
	<link>	定义了一个文档和外部资源之间的关系
	<meta>	定义了HTML文档中的元数据
	<script>	定义了客户端的脚本文件
	<style>	定义了HTML文档的样式文件

### HTML 表格标签

	<table>	定义表格
	<th>	定义表格的表头
	<tr>	定义表格的行
	<td>	定义表格单元
	<caption>	定义表格标题
	<colgroup>	定义表格列的组
	<col>	定义用于表格列的属性
	<thead>	定义表格的页眉
	<tbody>	定义表格的主体
	<tfoot>	定义表格的页脚

### HTML 列表标签

	<ol>	定义有序列表
	<ul>	定义无序列表
	<li>	定义列表项
	<dl>	定义列表
	<dt>	自定义列表项目
	<dd>	定义自定义列表的描述

### HTML  布局标签

	<div>	定义了文档的区域，块级 (block-level)
	<span>	用来组合文档中的行内元素， 内联元素(inline)


### HTML 表单标签（New : HTML5新标签）

	<form>	定义供用户输入的表单
	<input>	定义输入域
	<textarea>	定义文本域 (一个多行的输入控件)
	<label>	定义了 <input> 元素的标签，一般为输入标题
	<fieldset>	定义了一组相关的表单元素，并使用外框包含起来
	<legend>	定义了 <fieldset> 元素的标题
	<select>	定义了下拉选项列表
	<optgroup>	定义选项组
	<option>	定义下拉列表中的选项
	<button>	定义一个点击按钮
	<datalist>New	指定一个预先定义的输入控件选项列表
	<keygen>New	定义了表单的密钥对生成器字段
	<output>New	定义一个计算结果

### 文本格式化（Formatting）

	<b>粗体文本</b>
	<code>计算机代码</code>
	<em>强调文本</em>
	<i>斜体文本</i>
	<kbd>键盘输入</kbd> 
	<pre>预格式化文本</pre>
	<small>更小的文本</small>
	<strong>重要的文本</strong>
	 
	<abbr> （缩写）
	<address> （联系信息）
	<bdo> （文字方向）
	<blockquote> （从另一个源引用的部分）
	<cite> （工作的名称）
	<del> （删除的文本）
	<ins> （插入的文本）
	<sub> （下标文本）
	<sup> （上标文本）

---

# CSS

### id

	<p id="para1">Hello World!!!</p>
	<style>
	#para1
	{
		text-align:center;
		color:red;
	} 
	</style>

### class

	<h1 class="center">标题居中</h1>
	<style>
	.center
	{
		text-align:center;
	}
	</style>

---

# jQuary

### jQuary选择器和事件

	# 用户点击按钮后，所有 <p> 元素都隐藏：
	$(document).ready(function(){ 
	 $("button").click(function(){ 
	   $("p").hide(); 
	 }); 
	});

	# 当用户点击按钮后，有 id="test" 属性的元素将被隐藏：
	$(document).ready(function(){ 
	 $("button").click(function(){ 
	   $("#test").hide(); 
	 }); 
	});

	# 用户点击按钮后所有带有 class="test" 属性的元素都隐藏：
	$(document).ready(function(){ 
	 $("button").click(function(){ 
	    $(".test").hide(); 
	 }); 
	});



### jQuary 遍历

	$(document).ready(function(){
	  $("span").parent();
	});

### jQuary Ajax

	<script src="//libs.baidu.com/jquery/1.10.2/jquery.min.js">
	</script>
	<script>
	$(document).ready(function(){
	  $("button").click(function(){
	    $.post("/statics/demosource/demo_test_post.php",
	    {
	      name:"W3Cschool",
	      url:"http://www.w3cschool.cn"
	    },
	    function(data,status){
	      alert("数据: " + data + "状态: " + status);
	    });
	  });
	});
	</script>


---

# Ajax

### responseText

	<script>
	function loadXMLDoc()
	{
	var xmlhttp;
	if (window.XMLHttpRequest)
	  {// code for IE7+, Firefox, Chrome, Opera, Safari
	  xmlhttp=new XMLHttpRequest();
	  }
	else
	  {// code for IE6, IE5
	  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
	  }
	xmlhttp.onreadystatechange=function()
	  {
	  if (xmlhttp.readyState==4 && xmlhttp.status==200)
	    {
	    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
	    }
	  }
	xmlhttp.open("POST","/statics/demosource/demo_post2.php",true);
	xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
	xmlhttp.send("fname=Henry&lname=Ford");
	}
	</script>
	</head>
	<body>
	
	<h2>AJAX</h2>
	<button type="button" onclick="loadXMLDoc()">Request data</button>
	<div id="myDiv"></div>




### responseXML 属性	

	xmlDoc=xmlhttp.responseXML;
	txt="";
	x=xmlDoc.getElementsByTagName("ARTIST");
	for (i=0;i<x.length;i++)
	  {
	  txt=txt + x[i].childNodes[0].nodeValue + "<br>";
	  }
	document.getElementById("myDiv").innerHTML=txt;

---

# UI框架

### Bootstrap

	没有主题，使用Bootstrap的系统，基本都是一个死样子。
	它API简洁优雅，社区火爆到不行，你需要任何东西，随便Google，分分钟找几十个插件。 所有组件全自动化绑定，根本不用关心JS，让你省心到爆。

### Foundation

	Foundation是严格的“移动优先”, 仅包含几个通用的组件,网页开发又因其功能不足，多数都不会选择。

### Semantic

	Semantic每一个组件都需要手动调用JS代码

### AmazeUI
	
	速度慢，没有社区，小众

### easy UI

	不美观

### QuickUI

	www.uileader.com ，北京的公司， 收费的

### Metronic

	收费的，界面十分精美
	淘宝有一个卖的

### H+
	
	收费

### Admin LTE

	下载：https://github.com/almasaeed2010/AdminLTE （目前star 11652+）
	预览: http://almsaeedstudio.com/preview/
	官网：Free Bootstrap Admin Template
	整体感觉与Metronic类似、功能强大，UI精致，被许多公司使用。免费的

### INSPINIA

	收费的

---

# MVC 框架

### react
	
	算是View层，虚拟DOM，性能很快.不允许你使用双向数据绑定，这会使你在处理表单数据和可编辑的表格时有很多痛苦。

### Angular

	学习起来费劲，包含整个MVC结构，支持双向数据绑定。

### VUE

	vue.js的特性如下：
	vue.js属于轻量级的框架；
	vue.js的数据时双向绑定的；
	vue.js中指令和组件分得更清晰；
	vue.js能够异步批量DOM更新；
	vue.js具有可扩展性，让用户可以在多个组件中复用共同的特性。


---

# 后端框架

### Nginx + Uwsgi

### Python + Django

### Python + Flask

### Node.js

### PHP

### Ruby on Rails

