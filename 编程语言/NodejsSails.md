
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
	sails generate page zsw/zswp
    //增加一个页面，会在view\pages,api\controllers,assets\styles\pages\***.less , assets\js\pages\***.page.js增加4个文件
	
	
	
# models		

	sails generate model student

	attributes: {
    id: {
      type: 'number',
      required: true,
      unique: true,
      example: '1',
      autoIncrement: true,
      columnName: 'id'
    },
    name: {
      type: 'string',
      required: true,
      maxLength: 45,
      example: 'name',
      columnName: 'name'
    },
    age: {
      type: 'number',
      required: true,
      example: '22',
      columnName: 'age'
    },

	
	// 修改config下面datastore文件， 还有config/env/production文件
	adapter: 'sails-mysql',
    url: 'mysql://zsw1:zsw123@localhost:3306/zsw_db',

	// 修改config/models.js
	去掉createAt,updateAt等默认列

	// 安装依赖
	npm install sails-mysql --save
	npm install --save waterline
	npm install --save-dev sails-disk

	// action才能访问数据库
	var ss = await Student.find({ age: { '>=': 0 } });
    for (var x of ss){
      sails.log.info(""+x.id);
      sails.log.info(""+x.name);
      sails.log.info(""+x.age);
    }

	
	
	



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



# component ajax-form ajax-button

	
	具体看下面的ejs模板例子
	




# 例子
	// 生成4个page页面
	sails generate page zsw/zswp

	// routes-------------------路由--------------------------
 	'GET /signup':             { action: 'entrance/view-signup' },

	// view-action------------- 用处不大-----------------------------------
	api/controller/entrance/view-zswp.js
	viewTemplatePath: 'pages/zsw/zswp',   // 返回绑定的ejs
	
	// vue js-------------------vue的数据和函数----------------------------
	assets/js/pages/zswp.page.js文件定义vue的js代码
	定义data，methodes，用于绑定vue的数据和事件

		 data: {
		    // Main syncing/loading state for this page.
		    syncing: false,
		
		    // Form data
		    formData: { /* … */ },
		
		    // For tracking client-side validation errors in our form.
		    // > Has property set to `true` for each invalid property in `formData`.
		    formErrors: { /* … */ },
		
		    // Server error state for the form
		    cloudError: '',
		
		    // Success state when form has been submitted
		    cloudSuccess: false,
		
		    //…
		    zsw_open: true,
		    zsw_list:[
		      { message: 'Foo' },
		      { message: 'Bar' },
		      { message: 'Bar2' },
		    ],
		    zsw_map:{sss:222},
		    zsw_list_add:[],
		  },


		------------------------------------

		  methods: {
		    //…
		    zsw_method : function () {
		      this.zsw_map['sss'] --;
		      this.zsw_list_add.push(this.zsw_map['sss']);
		    },
		
		
		    submittedForm: async function() {
		      this.syncing = true;
		      window.location = '/';			//成功之后跳转到页面
		    },
		
		    handleParsingForm: function() {			//进行输入的客户端校验工作
		      // Clear out any pre-existing error messages.
		      this.formErrors = {};
		      var argins = this.formData;
		
		      // Validate email:
		      if(!argins.emailAddress) {
		        this.formErrors.emailAddress = true;
		      }
		   
		      if (Object.keys(this.formErrors).length > 0) {
		        return;
		      }
		
		      return argins;
		    },
		  }

	// views data-------------------html模板----------------------------
	view/pages/signup.ejs里面编写html模板，使用vue语法显示数据，绑定事件

	// views methodes
	<div id="zswp" v-cloak>		//一定要注意这个id
	<ajax-form action="zswpcb" :syncing.sync="syncing" :cloud-error.sync="cloudError" @submitted="submittedForm()" :handle-parsing="handleParsingForm">
	<ajax-button :syncing="syncing" class="btn-dark btn-lg btn-block">Sign in</ajax-button>

	// 生成1个action, 里面编写上面ajax-form对应的action函数
	sails generate action zsw/zswpcb

	 inputs: {
	    emailAddress: {
	      required: true,
	      type: 'string',
	      description: 'A return email address where we can respond.',
	      example: 'hermione@hogwarts.edu'
	    },},

	  exits: {
	    success: {
	      description: 'zsw successfully ',
	      extendedDescription:  'zswp callback'
	    },
	  },
	
	
	  fn: async function (inputs, exits) {
	
	    sails.log.info(inputs.emailAddress);
	    sails.log.info('ffffffffffff');
	    
	    return exits.success();
	  }


	// 调用服务器处理action路由 --------------客户端的事件------------------------
  	'PUT   /api/v1/zsw/zswpcb':             { action: 'zsw/zswpcb' },

	
	// 生成 cloud-sdk
	sails run rebuild-cloud-sdk



# model User

	friends: { collection: 'User', description: 'All of the other users this user can share things with.' },


# 点击按钮打开modal弹窗

 
	<div id="friends" v-cloak>
	  <div class="container">
		<button class="btn btn-outline-primary" @click="clickInviteButton()">Invite friends</button>	//调用vuejs不用ajax

	assets/js

	virtualPages: true,
	  html5HistoryMode: 'history',
	  virtualPagesRegExp: new RegExp(/^\/friends\/?([^\/]+)?/),


	  clickInviteButton: function() {
      // Open the modal.
      this.goto('/friends/new');
    },

  	'GET /friends/:virtualPageSlug?':   { action: 'friends/view-friends' },     // config/rout设定虚拟路由

# modal弹窗里面


	 <modal v-if="virtualPageSlug === 'new'" v-cloak key="new" @close="closeAddFriendsModal()">
	 <div class="modal-header">
      <h5 class="modal-title">Invite friends</h5>
      <button type="button" class="close" data-dismiss="modal" aria-label="Close">
        <span>&times;</span>									  // X的关闭按钮			
      </button>
     </div>

	<div class="modal-body">
 	<span class="add-more-button" @click="clickAddMoreButton()"><span class="fa fa-plus text-info mr-1"></span> Add more</span> // + 加一行的按钮

	<button data-dismiss="modal" class="btn btn-outline-secondary mr-1">Cancel</button>   //取消按钮
	<div class="modal-footer flex-row-reverse justify-content-start">	

	
# 数据处理流程vue js

		// vue 直接通过me来获取列表
		 <tr v-for="friend in me.friends">    
	
		// 想增加数据的时候，通过vue js文件中预定义的data来操作
		<div class="form-group" v-for="(friend, index) in addFriendsFormData.friends">

		// 增加好友点击提交--------------------------------------------------------------
 		 <ajax-form action="addFriends" :syncing.sync="syncing" :cloud-error.sync="cloudError" :handle-parsing="handleParsingAddFriendsForm" @submitted="submittedAddFriendsForm()">
		vue js文件中定义的submittedAddFriendsForm函数， 可以获取自己data中this.addFriendsFormData的数据
	  
	  var invitedFriends = _.filter(this.addFriendsFormData.friends, (friend)=>{
        return friend.fullName !== '' && friend.emailAddress !== '';
      });
	  this.me.outboundFriendRequests = this.me.outboundFriendRequests.concat(invitedFriends);
      this.$forceUpdate();




		// 删除好友  ---------有确认框------------------------------------
	<button class="btn btn-sm btn-outline-danger" @click="clickRemoveFriend(friend.id)">Remove friend</button>

    clickRemoveFriend: function(friendId) {
      this.selectedFriend = _.find(this.me.friends, {id: friendId});
      console.log('selectedFriend',this.selectedFriend);

      // Open the modal.
      this.confirmRemoveFriendModalOpen = true;
    },

	<modal v-if="confirmRemoveFriendModalOpen && selectedFriend" v-cloak key="remove" @close="closeRemoveFriendModal()">
	 <button data-dismiss="modal" class="btn btn-outline-secondary mr-1">Nevermind</button>
	 closeRemoveFriendModal: function() {   //关闭或取消确认框
	      this.selectedFriend = undefined;
	      this.confirmRemoveFriendModalOpen = false;
	      this.cloudError = '';
	    },
				

		// 删除好友确认框，指定了action，还有后面的vue js
		<ajax-form action="removeFriend" :syncing.sync="syncing" :cloud-error.sync="cloudError" :handle-parsing="handleParsingRemoveFriendForm" @submitted="submittedRemoveFriendForm($event)">
		
		// 删除好友 vue js
		handleParsingRemoveFriendForm: function() {
	      return {
	        id: this.selectedFriend.id
	      };
	    },
		submittedRemoveFriendForm: function() {
	      // Remove this user from our friends list.
	      _.remove(this.me.friends, {id: this.selectedFriend.id});
	
	      // Close the modal.
	      this.selectedFriend = undefined;
	      this.confirmRemoveFriendModalOpen = false;
	      this.cloudError = '';
	    },
		


		// 同意加好友------没有确认框-----------------------------------------------------
		 <button :disabled="syncing" class="btn btn-sm btn-outline-primary" @click="clickApproveFriend(potentialFriend.id)">Confirm</button>
		 // Prevent double-posting
	      if(this.syncing) {
	        return;
	      }
	      this.syncing = true;

		 await Cloud.approveFriend.with({ id: userId });   // 调用cloud 绑定的action

	      // Add this user to our approved friends list.
	      var approvedFriend =_.find(this.me.inboundFriendRequests, {id: userId});
	      this.me.friends.unshift({
	        id: approvedFriend.id,
	        fullName: approvedFriend.fullName,
	        emailAddress: approvedFriend.emailAddress
	      });
	      // Remove this user from our friends list.
	      _.remove(this.me.inboundFriendRequests, {id: userId});
	      // Clear loading state
	      this.syncing = false;
		-------------------------------------------------------------------------------



# action	

	