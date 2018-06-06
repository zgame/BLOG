# element UI
	
	大部分都是el-的控件名字

	this.$message('这是一条消息提示');

	// 二次确认框
	methods: {			
      open2() {
        this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });          
        });
      }
    }


	// 通知框， 在右上角
 	this.$notify({
          title: '成功',
          message: '这是一条成功的提示消息',
          type: 'success'
        });


	// 可以设定数值的开关
	<el-switch v-model="dlgData.edit" active-color="#13ce66" inactive-color="#ff4949" active-value="1" inactive-value="0"></el-switch>


	// 开关的初始状态设定
	this.dlgData.dashboard = '1'	//开启

---

# Admin目录结构

	/api			action连接后端请求, 常用***
	/components		自定义组件
	/router			路由设定, 常用***
	/store			model数据层，常用***
	/utils			增加一个axios拦截器中间件
	/views			各个页面, 常用***
	permission.js




# utils

	request.js
	1. 创建axios实例，默认请求后端路径为config里面的配置BASE_API
	2. request拦截器，增加请求token
	3. response拦截器，code = 20000 为成功标识，
	   code = 50008 非法token，code = 50012 其他客户端登录了
	   code = 50014 token过期了，message为错误信息


# api

	// axios 连接后端请求数据用
	export function getInfo(token) {
	  return request({
	    url: '/user/info',
	    method: 'get',
	    params: { token }
	  })
	}


# store

	/modules/app.js		 侧边栏的大小调整记录cookies
	/modules/user.js	 登录之后设置token
	index.js			 定义全局的store



# dispatch

	寻找所有父级，直到找到要找的父组件，并在其身上触发指定事件action
	action就是在store/modules下面定义的action

# mutation
	
	vuex的状态变化只能通过mutation
	state.sidebar.opened = false

# action

	commit('TOGGLE_SIDEBAR')		//提交mutation


# router

	index.js里面增加一个路由，侧边栏会自动出现这个选项，后面会增加带权限验证的路由


# view

	form 表单页面	       	
	layout 布局不用动
	table 表格				// 启动就请求create		
	login					// 输入验证，




# 数据例子

	  "code": 20000,
	  "data": {
	    "items": [
	      {
	        "id": "54000020040629841X",
	        "title": "Yprmmwrmdf tksutufjw shh meigkut grqgjbxtq wygsp opcdexjvfq hvwdt swlqaono hvhndwuxiu disedjwb.",
	        "status": "draft",
	        "author": "name",
	        "display_time": "2008-08-07 08:01:02",
	        "pageviews": 3156
	      },


# 登录

	/views/login/index.vue   登录界面vue，先登录，获得token，然后getinfo

	通过this.$store.dispatch('Login', this.loginForm).then(() => {调用module层
	/store/modules/user.js   登录之后保存name，token等信息
	
	module层调用api层
	/api/login.js			 请求服务器登录的协议格式
	
	
# 权限

	/router/index.js 
	export const asyncRouterMap = []   // 这里增加带权限的路由，设置可以不可以访问
	meta: { title: '表单', icon: 'form', roles: ['admin','view'] },
	
	
	store/index.js
	import permission from './modules/permission'  // 针对权限进行的一些计算
	在modules里面增加permission

	store/getter.js
	permission_routers: state => state.permission.routers,
    addRouters: state => state.permission.addRouters,

	/views/layout/componets/Sidebar/index.vue 
	采用permission_routers，将权限路由显示出来

	

# 显示时间格式

	 <span>{{scope.row.login_time | parseTime('{y}-{m}-{d} {h}:{i}')}}</span>
	


# get,post

	method: 'post',
    data: { id, username, pwd, dashboard, statis, edit }		// data是用于post

	method: 'get',
    params: { username, pwd, dashboard, statis, edit }			// params是地址带参数，用于get


# form 

	<el-dialog :title="textMap[dialogStatus]" :visible.sync="dialogFormVisible">
      <el-form :rules="rules" ref="dataForm" :model="dlgData" label-position="left" label-width="90px" style='width: 300px; margin-left:50px;'>


        <el-form-item label="账号" >
          <el-input v-model="dlgData.username"></el-input>
        </el-form-item>
 	  </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">{{$t('table.cancel')}}</el-button>
        <el-button v-if="dialogStatus=='create'" type="primary" @click="AddUserAction">{{$t('table.confirm')}}</el-button>
        <el-button v-else type="primary" @click="EditUserAction">{{$t('table.confirm')}}</el-button>
      </div>
    </el-dialog>



# 表单验证


	<el-form :rules="rules" ref="dataForm" :model="dlgData"   	//设置rules

	<el-form-item label="账号" prop="username">			//设置prop
          <el-input v-model="dlgData.username"></el-input>
        </el-form-item>

	 rules: {
          username: [{ required: true, message: '必须有名字', trigger: 'change' }, { min: 5, max: 9, message: '长度在 5 到 9 个字符', trigger: 'blur' }],
          // timestamp: [{ type: 'date', required: true, message: 'timestamp is required', trigger: 'change' }],
          pwd: [{ required: true, message: '必须有密码', trigger: 'blur' }]
        }
	 
	this.$refs['dataForm'].validate((valid) => {
          if (valid) {
	}
	})



#  编辑数据

	this.dlgData.dashboard = '' + row.is_dashboard
	// 要注意前面部分是vue的变量， row是数据库的字段名
	// 开关默认开启是'1'

# 表格

	   <div class="app-container">
          <el-table :data="list" v-loading.body="listLoading" element-loading-text="Loading" border fit highlight-current-row  stripe>	//  stripe是带间隔颜色的标志
            <el-table-column align="center" label='ID' width="50">
              <template slot-scope="scope">
                {{scope.row.id}}
              </template>
            </el-table-column>
		   <el-table-column label="操作" align="center">
              <template slot-scope="scope">
                <el-button size="mini" type="primary" @click="addUser(scope.$index, scope.row)">新增</el-button>
                <el-button size="mini" @click="editUser(scope.$index, scope.row)">编辑</el-button>
                <el-button size="mini" type="danger" @click="deleteUser(scope.$index, scope.row)">删除</el-button>
              </template>
            </el-table-column>
          </el-table>
        </div>


# 表格搜索和过滤





# 数据库的嵌套





# 收入显示













 