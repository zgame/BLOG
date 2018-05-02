# ubuntu


	第一步：安装 PostgreSQL, phpPgAdmin 和 Apache2
	sudo apt-get -y install postgresql postgresql-contrib phppgadmin

  	apt-get install apache2
	apt-get install php5
	apt-get install php5-pgsql
	apt-get install php5-gd

	第二步：配置 PostgreSQL 用户
	sudo su
	su - postgres			//用postgres登录
	psql			//登录数据库

	\password		//修改密码

	\q  			// 退出
	exit			// 退出到linux

	第三步：配置Apache2
	/etc/apache2/conf-available/phppgadmin.conf
	/etc/phppgadmin/apache.conf
	#allow from 127.0.0.0/255.0.0.0 ::1/128
    allow from all     取消这行注释，运行所有ip访问
	注释掉#Require local，添加allow from all

	第四步：配置 phpPgAdmin
	编辑文件 /etc/phppgadmin/config.inc.php 
	找到 $conf[‘extra_login_security’] = true; 修改为false。

	sudo service postgresql restart
	sudo service apache2 restart
	
	http://115.159.43.11/phppgadmin/  这样就可以远程来登录和编辑数据库了
	



# windows版本

	安装后，可以用pgadmin来进行可视化管理， 也支持命令行
	\l		//列出所有数据库

	可以创建模式schema,  模式下面是table， 调用的时候用 schema.table

	INSERT INTO zsw_schema.zsw_table(
            id, age, school)
    VALUES (1, 20, 'xxxxx');

	\c database   // use database 进入数据库
	\dt     // show tables  列出所有表

	
	