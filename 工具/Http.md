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



# https

	Apache、Nginx等，使用OpenSSL提供的密码库，生成PEM、KEY、CRT等格式的证书文件。

	CSR 是Certificate Signing Request的缩写，即证书签名申请，这不是证书，这是要求CA给证书签名的一种正是申请，该申请包含申请证书的实体的公钥及该实体店某些信息。该数据将成为证书的一部分。CSR始终使用它携带的公钥所对应的私钥进行签名。
	PEM - Privacy Enhanced Mail,打开看文本格式,以"-----BEGIN..."开头, "-----END..."结尾,内容是BASE64编码



	csr证书转换成crt
	openssl x509 -req -days 1800 -in /usr/local/cert_req.csr -signkey /usr/local/private.key -out /usr/local/server_cert.crt

	pem 转成crt
	openssl x509 -outform der -in full_chain.pem -out server.crt


# 免费证书申请

	https://certmall.trustauth.cn/Free/

	https://freessl.org/apply?domains=portia_shop.patheagames.com&product=letsencrypt02&from=
	提交csr，然后在dns设置网站给到的参数， 验证通过后点击下载证书pem

	查看pem的内容
 	openssl x509 -in full_chain.pem -text -noout	

	pem文件结尾不能有其它回车，空格等多余字符


	pem证书要跟私钥key文件配对

	
# 证书的类型

	http://blog.chinassl.net/tag/pem

	