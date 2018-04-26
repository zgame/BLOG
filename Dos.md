# bat
	
	@echo off	
	echo  -- 创建快捷方式
	::创建快捷方式
	set tp="%cd%\Debug.url"
	echo [internetshortcut]>> %tp%
	echo URL="E:\libs">>%tp%
	echo IconIndex=4>>%tp%
	echo IconFile=%SystemRoot%\system32\SHELL32.dll>>%tp%

	启动exe
	start LogService.exe
	ping -n 2 127.0.0.1 > nul
	start CenterServer.exe
	ping -n 2 127.0.0.1 > nul

	关闭exe
	set "d=%cd:\=\\%\\"
	@Wmic Process Where "Name='GameServer.exe' And ExecutablePath='%d%GameServer.exe'" Call Terminate