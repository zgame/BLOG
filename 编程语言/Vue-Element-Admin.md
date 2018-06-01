# element UI
	
	大部分都是el-的控件名字

	this.$message('这是一条消息提示');

	// 确认框
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

	寻找所有父级，直到找到要找的父组件，并在其身上触发指定事件


# 




















 