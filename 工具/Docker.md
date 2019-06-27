# 国内镜像

	https://get.daocloud.io/




# ubuntu 安装

	curl -sSL https://get.docker.com/ | sh 


# 安装windows


	docker需要windows10， 如果不是， 那么用Docker Toolbox来安装
	http://get.daocloud.io/#install-docker-for-mac-windows
	下载Docker Toolbox
	https://get.daocloud.io/toolbox/

	安装之后，第一次进入是自动配置， 第二次进入就可以了


	
# 腾讯云安装

	http://bbs.qcloud.com/thread-2213-1-1.html


# 下载容器

	docker search ***	//搜索容器名字

	docker pull learn/tutorial   //下载容器	learn/tutorial	

	docker run learn/tutorial echo "hello word"  // 运行容器

	docker run learn/tutorial apt-get install -y ping   // 容器中安装新的应用

	docker ps -l		//获得容器的id

	docker commit 698 learn/ping		//无需拷贝完整的id，通常来讲最开始的三至四个字母即可区分

	docker run learn/ping ping www.google.com


	docker ps   // 运行的容器

	docker inspect id。。。   //用id查看容器的具体信息

	
# toolbox 设置镜像


	docker-machine ssh default
	sudo sed -i "s|EXTRA_ARGS='|EXTRA_ARGS='--registry-mirror=http://56768f80.m.daocloud.io  |g" /var/lib/boot2docker/profile
	exit
	docker-machine restart default


# win10 设置镜像

	setting

	registry-mirrors

	http://56768f80.m.daocloud.io


# 命令

	https://www.runoob.com/docker/docker-command-manual.html

	docker ps   // 运行的容器

	docker ps -a   //所有的容器

	docker run -it ubuntu       //attach到ubuntu里面了  

	exit      //退出到docker

	docker images   //列出所有的镜像

	docker rm  容器id前3-4即可       // 删除对应的容器
	
	docker rmi 镜像id前3-4即可		//删除对应id的镜像

	

# Centos 7 安装

	sudo yum install -y yum-utils device-mapper-persistent-data lvm2

	sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
	
	sudo yum makecache fast				//更新 yum 缓存：
	
	sudo yum -y install docker-ce    //安装 Docker-ce：

# Centos 7 运行

	http://www.runoob.com/docker/centos-docker-install.html
	
	sudo systemctl start docker

	docker run hello-world		//测试运行

	docker pull mysql

	docker run -p 3306:3306 --name mymysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.6

	docker run -p 3306:3306 --name mymysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.6
	




# docker run

	docker run -i -t centos /bin/bash     // docker启动交互式镜像
	docker run -i -t centos/zsw:62712 /bin/bash 

# docker 修改保存

	// 在运行的容器里面，安装软件等操作，然后
	[root@190647a938a1 /]# exit
	// exit docker
	// 提交修改到新的镜像里面去
	docker commit -m="zsw62611" --author="zsw" 190647a938a1 centos/zsw:62611

	// 运行新的镜像
	docker run -i -t centos/zsw:62611 /bin/bash


# docker 文件copy

	将主机/www/runoob目录拷贝到容器96f7f14e99ab的/www目录下。
	docker cp /www/runoob 96f7f14e99ab:/www/



# docker file

	