# localhost(127.0.0.0)

	回送地址，只能本地访问，不能对外


# 0.0.0.0

	表示所有ip地址

# ip 

	本地固定ip	




# token

	令牌，是用户身份的验证方式。一般有加密解密方式和过期时间


# session

	会话，代表服务器与浏览器的一次会话过程，这个过程是连续的，也可以时断时续。

# cookie

	储存在用户本地终端上的数据，服务器生成，发送给浏览器，下次请求统一网站给服务器。


# session与token

	作为身份认证，token安全行比session好；


# token与cookie

	Cookie是不允许垮域访问的，但是token是支持的， 前提是传输的用户认证信息通过HTTP头传输；


# post

	form 为key，value形式的

