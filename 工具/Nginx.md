# serverlist的ngnix配置 #

	/etc/nginx/nginx.conf	ngnix配置
	
	server {
			listen 80 default_server;
			server_name _;
			access_log off;
		}
	server{
	listen  8080;
	server_name 182.254.220.194;
	root /opt/Bundle/ClientGameBundle;
	}
	server{
	listen 8086;
	server_name 182.254.220.194;
	root /opt/Bundle/GamePacket;
	}




---

# website nginx设置 #

	/etc/nginx/nginx.conf	ngnix配置
	server {
			listen 80 default_server;
			server_name _;
			access_log off;
			root /opt/website;
		}
	
	server{
	                listen  8080;
	                server_name 182.254.220.194;
	                root /opt/Bundle/ClientGameBundle;
	        }



---

# 多站点配置 #


	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
	
	server {
		listen 80 default_server;
		server_name _;
		access_log off;
		root /opt/website;
	}
	server{
                listen  8080;
                server_name 182.254.220.194;
                root /opt/Bundle/ClientGameBundle;
        }
	server{
                listen  8081;
                server_name 182.254.220.194;
                root /opt/Bundle/ClientGameBundle;
        }


---
# uwsgi #

	upstream GameServer {
	    server unix:///tmp/game_pikaqiu.sock;
	}
	
	server {
	    listen    8083;
	    server_name    GameServer;
	    charset    utf-8;
	    client_max_body_size    1M;    
	
	    #path
	    location / {
	        uwsgi_pass    GameServer;		#这里标注uwsgi转发
	        include    /etc/nginx/uwsgi_params;
	        #access_log /opt/GameServer/logs/access.log;
	    	#error_log /opt/GameServer/logs/error.log crit;
	    	access_log /dev/null;
	        error_log /dev/null;
	    }
	}



# 命令

	ps -ef | grep nginx
	service nginx -s  reload

	目录到nginx下面
	./nginx -s  reload


# windows版本

	直接解压到目录下
	cd 到nginx的目录下，再敲命令
	
	start nginx （不要多次运行）
	
	tasklist /fi "imagename eq nginx.exe" （查看进程）

	nginx -s  reload

	nginx -s  quit
	



# apache配置

	把require local修改为Require all granted


# apache tomcat

	apache是web服务器,Tomcat是应用（java）服务器，它只是一个servlet(jsp也翻译成servlet)容器，可以认为是apache的扩展，但是可以独立于apache运行。  