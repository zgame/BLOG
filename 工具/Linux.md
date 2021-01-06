---

# 命令

    tar czvf zgame.tar.gz zgame(目录)----------压缩	
    sz zgame.tar.gz(下载)--------------sz命令发送文件到本地：	
    rz 上传， 然后出对话框--------------rz命令本地上传文件到服务器：	
    cp -r 原 目标	----------------copy	
    rm  -r **	------------------删除	
    mv -r 原 目标	-------------------移动	
    sudo ln -s /opt/GameServer/apps/game_nginx.conf /etc/nginx/sites-enabled/game_nginx.conf	建立软连接	
    touch	创建一个文件
    nohup command > myout.file 2>&1 &		输出被重定向到myout.file文件中。
    直接不开后台模式就可以 看输出了
    start.sh去掉nohup 和结尾的& 就可以前台执行	
    ps -ef|grep svnserve 查看线程
    ifconfig -----------------------------看ip	
    关机shutdown -h 0
    休眠sudo echo mem > /sys/power/state
    查看哪些端口被打开  netstat -anp

---
# svn

	启动svn
	svnserve -d -r /home/svn
	
	关闭svn
	killall svnserve
	
	创建svn仓库
	sudo mkdir  repository
	sudo chown -R root:subversion repository
	sudo chown -R 777 repository
	sudo svnadmin create repository

---

# 权限

	sudo -s
	
	安装软件
	sudo apt-get  build-dep gcc
	
	sudo chmod -R 777 /usr/local/nginx/objs	-----------设置目录权限
	
	
	linux
	su 权限
	./stop.sh
	./start.sh
	/opt/sites/zgame/





-----

# 日志

	查看错误日志文件，代码中加入的：tail -n 1000 /opt/GameServer/logs/game_err.log
	-f 一直查看，正在发生的
	查看wsgi日志： sudo tail -n 1000 /opt/GameServer/logs/uwsgi.log
	
	ctrl+c 退出
	ctrl+z 后台暂停
	
	htop 查看进程，cpu，内存
	f4 加关键字
	f5 树形结构
	
	sudo kill -9  进程pid  杀死进程
	
	sh start_uwsgi.sh
	sh start_thread.sh
	
	sh stop_uwsgi.sh
	sh stop_thread.sh
	
	uwsgi调整works数量/etc/uwgsi/apps_enabled/game_wsgi.ini
	
	皮卡丘works = 40
	战舰works = 40
	测试服works = 4 
	
	
	netstat -nlpt  查看端口	
	
	开启日志服务
	sh /home/ubuntu/start_scribe_client.sh
	
	查看线程报错位置
	tail -f /opt/GameServer/logs/new_rekoo.out
	
	
	
	查看TCP连接数：	netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
	
	查看当前打开文件数： lsof |wc -l 
	
---

# 内存和硬盘

	free -m		--------------------------   	查看内存的状态
	dd 		----------------- 用指定大小的块拷贝一个文件，并在拷贝的同时进行指定的转换。
	df -hl		------------------             查看硬盘的状态 /dev/vda1


---

# 增加swap虚拟内存方法

	#cd /usr/
	#mkdir swap		创建目录
	#cd swap
	#dd if=/dev/zero of=swapfile bs=1G count=2	创建文件
	#mkswap swapfile	创建swap
	#swapon swapfile	激活swap
	/etc/fstab	添加/usr/swap/swapfile            swap                 swap       defaults 0 0 这里是增加开启自动启动
	

---

# 调试方法：

	1.winscp上传代码
	2.secureCrt重启服务器
	3.运行客户端unity
	4.查看uwsgi.log



---

# 项目相关

	修改model的文件名字后， 需要修改app/utils/model_define.py , 还需要修改apps/config/model.conf
	
	-----------------
	调试模式，看memcache
	sh shell.sh
	
	from apps.models.player_models import Player
	
	a = Player.get(玩家uid)
	
	a.debug()
	
	-----------------------------------
	调试模式，直接看输出
	
	直接不开后台模式就可以 看输出了
	start.sh去掉nohup 和结尾的& 就可以前台执行
	
	或者test.sh

	http://client-config.sh.1251506402.clb.myqcloud.com:8080/2.5.1115/Android/CRC.txt

-----------------------------------

# 日志服务器

	开启日志服务
	sh /home/ubuntu/start_scribe_client.sh
	
	保存的地址：
	/data/scribe/log_bak
	/home/ubuntu/data


---

	from apps.models.common import common_dat
	server_chat = common_dat.get_server_chat_model("ALLServerChat")
	chat_list_dat = server_chat.get_chat_list(refresh_time)
	server_chat.debug()
	generate_cache_key
	print chat_list_dat
	server_chat.put()
	
	from apps.utils import memcache
	cmem_url = '10.66.102.119:9101'
	chat_model = memcache.get_cmem_val(cmem_url, 'pkq_si|apps.models.user.User|1000000002')
	print chat_model
	
	
	
	
	from apps.models.user import User
	friend_user = User.get(1000000002)
	friend_user.debug()
	
	
	from apps.models.server_arena_rank import ServerArenaRank
	key = str('ServerArenaRank') + "|" #+ str(server_define.MERGE_SERVER_MAPPING[int(server_id)])
	_server_arena_rank_model = ServerArenaRank.get(key)
	_server_arena_rank_model.debug()
	
	
	
	zgame_pm2|apps.models.chat_list.ChatListDat|server_chat|ALLWorldChat数据为空
	
	'         apps.models.chat_list.ChatListDat'>----
	
	apps.models.server_arena_rank.ServerArenaRank
	
	
	from apps.models.notice import Notice
	_notice_box = Notice.get('game_notice|')
	_notice_box.debug()
	
	
	from apps.models.union_user import UnionUser
	_union_user_model = UnionUser.get(1000000092)
	_union_user_model.debug()
	
	
	
	
	from apps.models.common.server_arena.server_arena_rank import ServerArenaRank
	key = str(arena_rank) + "|" + str(server_define.MERGE_SERVER_MAPPING[int(server_id)])
	_server_arena_rank_model = ServerArenaRank.get(key)



----

	所有服务器列表数据都在zgame的mysql这个表中
	
	服务器列表8081 8084 8085 8086 8087可用，如果需要添加， 在腾讯云的负载均衡里面的serverlist里面添加

-----

# sdk的接入：


	serverlist里面制作回调，用来验签
	游戏服务器里面也需要制作回调，用来充值
	
	----------------------------------------------------------------------
	serverlist用来返回所有的服务器列表（mysql里面zgame的serverlist表），同时用来做所有渠道，所有游戏的登录验证和支付验证（主要是url跳转，platform是平台验证相关，还有验签）
	serverlist启动是start_uwsgi
	serverlist里面还有各个游戏的gm平台，启动是start84（端口号），端口是在负载均衡里面配置的
	
	gameserver配置的memcache和mysql地址在外面的一个目录下面（platform目录下面platform.conf,这里可以配置多个mysql的数据库地址，参考战舰.
	在platform.py里面定义了配置的读取，然后在config目录下面有storage.conf里面对应读取数据库的配置）
	gamesever的uwsgi要配置是否打印log，开启几个线程workers
	gameserver的thread是根据merge serverlist表里面有多少服务器，就有多少个线程







---

	-----------------安装pingpp--------------------------------------------------
	sudo pip install pingpp
	然后修改/usr/local/lib/python2.7/dist-packages/pingpp/api_requestor.py（因为platform名字冲突了）
	cd /usr/local/lib/python2.7/dist-packages/
	sudo chmod -R 777 pingpp
	
	
	        # for attr, func in [['lang_version', platform.python_version],
	        #                    ['platform', platform.platform],
	        #                    ['uname', lambda: ' '.join(platform.uname())]]:
	        zgame_str2 = "Linux VM-25-47-ubuntu 3.13.0-36-generic #63~precise1-Ubuntu SMP Thu Sep 4 22:28:20 UTC 2014 x86_64 x86_64"
	        for attr, func in [['lang_version', '2.7.13'],
	                           ['platform', 'Linux-3.13.0-36-generic-x86_64-with-debian-wheezy-sid'],
	                           ['uname', zgame_str2]]:
	            try:
	                val = func
	            except Exception as e:
	                val = "!! %s" % (e,)
	            ua[attr] = val


---

	---------------------更新python2.7-------------------------------------------------------------------------
	
	下载更新包，到windows，然后上传到opt目录下面， 然后在opt目录下面进行安装
	安装到/usr/local/python27，再链接上即可
	
	--------------------------修改hosts------------------------
	sudo vim /etc/hosts
	121.43.74.100	api.pingxx.com	pingpp
	sudo /etc/init.d/networking restart
	---------------------------------------------------------------




# ssh2
	Ubuntu默认是没有装ssh服务的，ssh分为客户端和服务器。
	Ubuntu安装ssh服务：sudo apt-get install openssh-server
	确认ssh服务是否启动：ps -e |grep ssh
	启动：sudo /etc/init.d/ssh start
	停止：sudo /etc/init.d/ssh stop
	ssh-server配置文件位于/ etc/ssh/sshd_config
	登录ssh：ssh tuns@ip tuns