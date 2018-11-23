# 查看系统版本

	cat /etc/centos-release

# 系统内存

	free -m

# 硬盘

	df -hl

# cpu

	cat /proc/cpuinfo

#  32位还是64位

 	getconf LONG_BIT

# htop
	
	CentOS7 安装
	yum install epel-release -y
	yum install htop -y

# yum search
	
	yum search netstat

# netstat

	-t 			 tcp
	-p			程序

	netstat -at  列出所有tcp端口
	netstat -pt  tcp的程序

# 本机ip

	ip address

# 安装go

	下载包https://golang.org/dl/
	解压包到 /usr/local目录下
	tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz

	将 /usr/local/go/bin 目录添加至PATH环境变量：
	export PATH=$PATH:/usr/local/go/bin

	
# 查看系统路径

	echo $PATH

# /etc/profile    设置goPath

	export GOROOT=/usr/local/go
	export GOBIN=$GOROOT/bin
	export PATH=$PATH:$GOBIN
	export GOPATH=/opt/goPath

	source /etc/profile  运行



# redis

	下载包，解压，编译，设置配置文件
	init.d里面增加开机自动启动redisd(utils/redis_init_script改名)


	ps -aux | grep redis查看redis进程

	service redisd start
	service redisd stop

	// 如果关闭出问题，process is already running or crashed
	rm -rf /var/run/redis_6379.pid

	设置里面绑定ip， 然后设置密码

# 开放端口

	firewall-cmd --query-port=6379/tcp 	// 查看端口是否开放

	firewall-cmd --add-port=6379/tcp	// 开放端口


# 编译运行

	编译
	go build -o filename

	运行
	./filename


# 关机

	shutdown -h 0
	shutdown -r now 重启