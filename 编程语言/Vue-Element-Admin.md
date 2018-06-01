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

	/api
	/components
	/router
	/store
	/utils
	/views
	main.js
	permission.js





# utils

	request.js
	1. 创建axios实例，默认请求后端路径为config里面的配置BASE_API
	2. request拦截器，增加请求token
	3. response拦截器，code = 20000 为成功标识，
	   code = 50008 非法token，code = 50012 其他客户端登录了
	   code = 50014 token过期了，message为错误信息





















 