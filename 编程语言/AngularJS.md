# 引入

	<script src="http://apps.bdimg.com/libs/angular.js/1.4.6/angular.min.js"></script>

# 指令

	ng-app 指令定义一个 AngularJS 应用程序。
	ng-model 指令把元素值（比如输入域的值）绑定到应用程序。
	ng-bind 指令把应用程序数据绑定到 HTML 视图。		或者{{ expression }}
	ng-init 指令初始化应用程序数据。


# scope作用域
	
	scope 是一个 JavaScript 对象，带有属性和方法，这些属性和方法可以在视图和控制器中使用。
	$scope.name = "John Dow";
	$rootScope.lastname = "Refsnes";

# 控制器

	app.controller('myCtrl', function($scope) {
    	$scope.firstName = "John";
    	$scope.lastName = "Doe";
	});

# 过滤器

	currency	格式化数字为货币格式。
	filter	从数组项中选择一个子集。
	lowercase	格式化字符串为小写。
	orderBy	根据某个表达式排列数组。
	uppercase	格式化字符串为大写。

# 服务

	$location 服务，它可以返回当前页面的 URL 地址。
	$http 是 AngularJS 应用中最常用的服务。 服务向服务器发送请求，应用响应服务器传送过来的数据。
	AngularJS $timeout 服务对应了 JS window.setTimeout 函数。
	AngularJS $interval 服务对应了 JS window.setInterval 函数。
	

# 选择框

	ng-repeat 指令是通过数组来循环 HTML 代码来创建下拉列表，但 ng-options 指令更适合创建下拉列表，它有以下优势：
	使用 ng-options 的选项的一个对象， ng-repeat 是一个字符串。
	ng-repeat可以用于表格

# dom

	ng-disabled 指令绑定应用程序数据 "mySwitch" 到 HTML 的 disabled 属性。
	ng-show 指令隐藏或显示一个 HTML 元素。
	ng-click 指令定义了一个 AngularJS 单击事件。
	ng-hide 指令用于设置应用的一部分 不可见 。
	
---
---

# Angular2

	使用typeScript作为脚本语言。写成ts文件

	import {Component, View} from "angular2/core";

	//framework recognizes @Component annotation and knows that we are trying to create a new component
	@Component({
	   selector: 'my-app'
	})
	
	@View({
	  //this template value will be displayed in the browser
	  template: '<h2>Welcome to Tutorialspoint</h2>'
	})
	
	export class MyModulesClass { }


# 