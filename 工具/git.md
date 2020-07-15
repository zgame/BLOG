# 自动修改换行符

	Unix/Linux使用的是LF，Mac后期也采用了LF，但Windows一直使用CRLF【回车(CR, ASCII 13, \r) 换行(LF, ASCII 10, \n)】作为换行符

	禁用git的自动换行功能： 
	在本地路径C:\ Users\ [用户名] \ .gitconfig下修改git配置[core]，如果没有就直接添加上去：

	[core]
	autocrlf = false


# 认证

	git config --list 查看配置和认证

	git config [--global] user.name "[name]"
	git config [--global] user.email "[email address]"