# bat 开服，关服
	
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




# bat 打包

	@echo off
	@color E
	setlocal enabledelayedexpansion
	
	set /p tp = 请输入打包类型(1:内网 2：外网)
	if not defined tp goto :eof
	if %tp% neq 1 if %tp% neq 2 goto :eof
	
	echo 正在更新最新版本。。。
	svn up ./
	
	echo 开始编译。。。
	BuildConsole Server/Server.sln /prj="*" /build /OpenMonitor /cfg="Release_Unicode|Win32"	
	
	IF %ERRORLEVEL% NEQ 0 (pause&goto :eof)
	
	echo 开始打包。。。
	
	：：取版本号
	for /f "tokens=4 delims= " %%i in ('svn info ./ ^| find /i "Last Changed Rev:" ') do set version = %%i
	
	::取打包文件名
	
	for /f "delims= " %%i in ("%cd%") do set fdir=%%~nxi
	
	if %tp% equ 1 (set fpath=内网_!fdir!_RELEASE) else (set fpath=外网_!fdir!_RELEASE)
	
	::copy文件
	xcopy /s /y 运行\Release\Unicode\*.pdb			.\%fpath%\Unicode_pdb\
	xcopy /s /y 发布组件\服务器组件\Release\Unicode\*  .\%fpath%\Unicode\
	xcopy /s /y Server\所有游戏\BY\BY\*				.\%fpath%\Unicode\BY\
	
	::打包zip
	set rarPath=!fpath!_[@!version!]_
	"D:\winrar.exe" u -r -m5 -y -afzip -agYYYYMMDDHHMM %rarPath%.rar   .\%fpath%


# powershell

	开始菜单， powershell，点右键以管理员身份运行

	可以批量删除系统补丁



# 删除文件夹

	rd /s /q  E:\GitHub\Unity3DCode\test1\

# copy 文件和文件夹


	xcopy /s /y E:\unityProject\test1\Assets\AssetPackage\Lua  E:\GitHub\Unity3DCode\test1\Lua\
	xcopy /s /y E:\unityProject\test1\Assets\script  E:\GitHub\Unity3DCode\test1\script\
	xcopy /s /y E:\unityProject\test1\Assets\AssetPackage\UI\prefab  E:\GitHub\Unity3DCode\test1\prefab\


# 文件重命名

	ren *.lua.txt *.
	:ren *.lua *.lua.txt
	

# 注释

	rem  或者 :

# cmd命令太长分成多行的写法

	cmd脚本中实现的同样功能的连接符是^
	ec^
	ho hello world


# 合并

	copy /b 1.jpg + 2.rar 3.jpg 



# 获取系统时间

	for /f %%i in ('powershell -c "Get-Date -uformat '%%Y%%m%%d'"') do (
    set "Today=%%i"
	)
	go build  -o portia_shop_%Today%.exe


# 启动多个可执行程序

	start "" portia_shop_%Today%.exe -https=1
	start "" portia_shop_%Today%.exe -https=0