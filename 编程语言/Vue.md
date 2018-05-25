
# 比较


	Vue 是最容易上手，最具亲和度的。工具链方面最近刚发布了 vue-cli，1 分钟搞定 webpack 配置。轻量级框架。Vue 也支持双向绑定，默认为单向绑定
	Vue 由于采用依赖追踪，默认就是优化状态：动了多少数据，就触发多少更新，不多也不少。
	Vue.js 不使用 Virtual DOM 而是使用真实 DOM 作为模板，数据绑定到真实节点。Vue.js 的应用环境必须提供 DOM。Vue.js 有时性能会比 React 好**，而且几乎不用手工优化。


	React采用特殊的JSX语法，Vue.js在组件开发中也推崇编写.vue特殊文件格式，对文件内容都有一些约定，两者都需要编译后使用。
	React推崇的是函数式编程和单向数据流，React和Vue都可以配合Redux来管理状态数据。
	


	Angular 使用双向绑定即：界面的操作能实时反映到数据，数据的变更能实时展现到界面。
	Angular，当 watcher 越来越多时会变得越来越慢，因为作用域内的每一次变化，所有 watcher 都要重新计算。
	

	
	React 以 JavaScript 为中心，Angular 2 依然保留以 HTML 为中心。Angular 2 将 “JS” 嵌入 HTML。React 将 “HTML” 嵌入 JS。Angular 2 沿用了 Angular 1 试图让 HTML 更强大的方式。
	
	React 推荐的做法是 JSX + inline style，也就是把 HTML 和 CSS 全都整进 JavaScript 了。Vue 的默认 API 是以简单易上手为目标，但是进阶之后推荐的是使用 webpack + vue-loader 的单文件组件格式（template,script,style写在一个vue文件里作为一个组件）




# vue

	不支持ie8， 所以使用chrome浏览器

	https://vuejs.org/js/vue.js		//可以下载开发版本到本地
	<script src="vue.js"></script>		//调用开发版本vue

	<div id="app">
    {{ message }}									//
	</div>

	<!-- JavaScript 代码需要放在尾部（指定的HTML元素之后） -->
	<script>
	
	    new Vue({
	        el:'#app',							//el 参数，它是 DOM 元素中的 id
	        data: {
	            message:'Hello World!'				//data 用于定义属性
	        }
			methods: {							// methods 用于定义的函数
            details: function() {
                return  this.site + " sdsf！";
            }
        	}
	    });

	</script>


# vue-cli 命令行工具，生成一个项目结构

	$ cd my-project
	$ cnpm install
	$ cnpm run dev						//然后用cnpm启动

	也可以在webstorm里面配置npm的run项目

	 DONE  Compiled successfully in 4388ms


	build	项目构建(webpack)相关代码
	config	配置目录，包括端口号等。我们初学可以使用默认的。
	node_modules	npm 加载的项目依赖模块
	src	
	这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：
	assets: 放置一些图片，如logo等。
	components: 目录里面放了一个组件文件，可以不用。
	App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。
	main.js: 项目的核心文件。
	static	静态资源目录，如图片、字体等。
	test	初始测试目录，可删除
	.xxxx文件	这些是一些配置文件，包括语法配置，git配置等。
	index.html	首页入口文件，你可以添加一些 meta 信息或统计代码啥的。
	package.json	项目配置文件。
	README.md	项目的说明文档，markdown 格式


# 参数

		
	var data = { site: "菜鸟教程", url: "www.runoob.com", alexa: 10000}

	document.write(vm.$data === data) 			// 还提供了一些有用的实例属性与方法。它们都有前缀 $，以便与用户定义的属性区分开来
	vm.$data === data
	

# 模板

 	 <p>{{ message }}</p>（双大括号）的文本插值
	
	 <div v-html="message"></div>		//html代码

 	<div v-bind:class="{'class1': class1}">     //HTML 属性中的值应使用 v-bind 指令。
	<a :href="url"></a>			//缩写



	 <input v-model="message">        //在 input 输入框中我们可以使用 v-model 指令来实现双向数据绑定


	{{ message | capitalize }}		//过滤器
 	filters: {
    capitalize: function (value) {}}
	{{ message | filterA | filterB }}  //过滤器可以串联
	{{ message | filterA('arg1', arg2) }}   // 过滤器是 JavaScript 函数



# 循环

	<li v-for="value in object">


	<li v-for="(value, key) in object">
    {{ key }} : {{ value }}

	 <li v-for="(value, key, index) in object">
     {{ index }}. {{ key }} : {{ value }}


   <li v-for="n in 10">

# if

	<p v-if="seen">现在你看到我了</p>		//指令是带有 v- 前缀的特殊属性
	<div v-else-if="type === 'B'">
 	<div v-else>
	<h1 v-show="ok">Hello!</h1>			// ok: true , 也是根据条件判断
	

# computed vs methods

	可以说使用 computed 性能会更好，但是如果你不希望缓存，你可以使用 methods 属性。

 	computed: {
     site: {
      // getter
      get: function () {
        return this.name + ' ' + this.url
      },
      // setter
      set: function (newValue) {


# 监听事件

	watch : {
        kilometers:function(val) {
            this.kilometers = val;
            this.meters = val * 1000;
        },
        meters : function (val) {
            this.kilometers = val/ 1000;
            this.meters = val;
        }
    }
    });
    // $watch 是一个实例方法
    vm.$watch('kilometers', function (newValue, oldValue) {


# css样式绑定

	<div v-bind:class="{ active: isActive }"></div>


# 事件



	<a v-on:click="doSomething">			//它用于监听 DOM 事件
	<a @click="doSomething"></a>			//缩写

	app.greet()			//javascript直接调用


#	事件修饰符

	<!-- 阻止单击事件冒泡 -->
	<a v-on:click.stop="doThis"></a>
	<!-- 提交事件不再重载页面 -->
	<form v-on:submit.prevent="onSubmit"></form>
	<!-- 修饰符可以串联  -->
	<a v-on:click.stop.prevent="doThat"></a>
	<!-- 只有修饰符 -->
	<form v-on:submit.prevent></form>
	<!-- 添加事件侦听器时使用事件捕获模式 -->
	<div v-on:click.capture="doThis">...</div>
	<!-- 只当事件在该元素本身（而不是子元素）触发时触发回调 -->
	<div v-on:click.self="doThat">...</div>
	
	<!-- click 事件只能点击一次，2.1.4版本新增 -->
	<a v-on:click.once="doThis"></a>



# 表单

	<!-- 在 "change" 而不是 "input" 事件中更新 -->
	<input v-model.lazy="msg" >

	如果想自动将用户的输入值转为 Number 类型（如果原值的转换结果为 NaN 则返回原值），可以添加一个修饰符 number 给 <input v-model.number="age" type="number">

	如果要自动过滤用户输入的首尾空格，可以添加 trim 修饰符到 v-model 上过滤输入：
	<input v-model.trim="msg">


# 组件

	<div id="app">
    <runoob></runoob>
	</div>

	Vue.component('runoob', {
	  template: '<h1>自定义组件!</h1>'
	})


	局部组件
	var Child = {
	  template: '<h1>自定义组件!</h1>'
	}

	Vue.component('child', {
	  // 声明 props
	  props: ['message'],				//父子组件


	验证
	 props: {
    // 基础类型检测 （`null` 意思是任何类型都可以）
    propA: Number,
    // 多种类型
    propB: [String, Number],
    // 必传且是字符串


# 钩子函数

	bind: 只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化动作。
	inserted: 被绑定元素插入父节点时调用（父节点存在即可调用，不必存在于 document 中）。
	update: 被绑定元素所在的模板更新时调用，而不论绑定值是否变化。通过比较更新前后的绑定值，可以忽略不必要的模板更新（详细的钩子函数参数见下）。
	componentUpdated: 被绑定元素所在模板完成一次更新周期时调用。
	unbind: 只调用一次， 指令与元素解绑时调用。


	参数
	el: 指令所绑定的元素，可以用来直接操作 DOM 。
	binding: 一个对象，包含以下属性：
		name: 指令名，不包括 v- 前缀。
		value: 指令的绑定值， 例如： v-my-directive="1 + 1", value 的值是 2。
		oldValue: 指令绑定的前一个值，仅在 update 和 componentUpdated 钩子中可用。无论值是否改变都可用。
		expression: 绑定值的字符串形式。 例如 v-my-directive="1 + 1" ， expression 的值是 "1 + 1"。
		arg: 传给指令的参数。例如 v-my-directive:foo， arg 的值是 "foo"。
		modifiers: 一个包含修饰符的对象。 例如： v-my-directive.foo.bar, 修饰符对象 modifiers 的值是 { foo: true, bar: true }。
	vnode: Vue 编译生成的虚拟节点。
	oldVnode: 上一个虚拟节点，仅在 update 和 componentUpdated 钩子中可用。



# vue2-ajax-form
	
	https://www.npmjs.com/package/vue2-ajax-form
	npm install vue2-ajax-form --save

	<template>
	    <ajax-form :action="action" :method="method" :enctype="enctype" :responsetype="responsetype" :before="before" :error="error" :complete="complete" :progress="progress" :after="after">
	        <input name="username" type="text" />
	        <input value="submit" type="submit" />
	    </ajax-form>
	</template>
	<script>
	import ajaxForm from 'vue2-ajax-form'
	export default {
	    data() {
	        action: '/api', // ajax 请求地址 (必须)
	        method: 'POST', // ajax 请求方法 POST | GET (默认: POST)
	        enctype: 'multipart/form-data', // ajax 请求编码 application/x-www-form-urlencoded | multipart/form-data | text/plain (默认: multipart/form-data)
	        responsetype: 'json' // ajax 请求数据类型 blob | document | json | text (默认: json)
	    },
	    components: {
	        ajaxForm
	    },
	    methods: {
	        before() {
	            console.log('before')
	            // ajax请求前
	        },
	        error(err) {
	            console.log(err)
	            // ajax请求出现错误
	        },
	        complete(response) {
	            console.log(response)
	            // ajax请求完成
	        },
	        progress(percent) {
	            console.log(percent)
	            // ajax请求进度
	        },
	        after() {
	            console.log('after')
	            // ajax请求后, 请求未完成
	        },
	    }
	}
	</script>



# 例子

	<div id = "zswtest" v-cloak>
	  <p v-if = "zswp_open"> zswp open</p>			//label
	  <p v-if = "!zswp_open"> zswp close</p>

	<span>Message is: {{ zswp_open }}</span>         // 输入框
      <input type="text" v-model="zswp_open" placeholder="edit me">


 	<div class="form-group">			// 按钮
        <button class="btn-success" @click="zsw_meth">bt</button>
	  <a class="btn btn-info" href="/account/profile">Update my email</a>   //地址跳转的按钮,比如取消


	<p class= badge-info>zsw_map:{{ zsw_map}}</p>
    <p class= badge-info>zsw_map['sss']:{{ zsw_map['sss']}}</p>

	<ul id="example-1">
    <li v-for="item in zsw_list">		//列表
      {{ item.message }}
    </li>
  	</ul>

	


#  路由

	Vue.js 路由需要载入 vue-router 库


# vuex状态管理

	Getters：用来从 store 获取 Vue 组件数据。 
	Mutators：事件处理器用来驱动状态的变化。 
	Actions：可以给组件使用的函数，以此用来驱动事件处理器 mutations


# vue-resource

	请求API是按照REST风格设计的，它提供了7种请求API： 
	· get(url,[options]) 
	· head(url,[options]) 
	· delete(url,[options]) 
	· jsonp(url,[options]) 
	· post(url,[body], [options]) 
	· put(url, [body],[options]) 
	· patch(url,[body], [options])

# Axios插件

	上面的替代


# vuex状态管理

	虽然 Vuex 可以帮助我们管理共享状态，但也附带了更多的概念和框架。这需要对短期和长期效益进行权衡。

	如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。确实是如此——如果您的应用够简单，您最好不要使用 Vuex。一个简单的 global event bus 就足够您所需了。


# ESLint

	自动对齐的一个插件

# 文档生成工具

	swagger是一个REST APIs文档生成工具

 