# unity 2018.3.0 Xlua 报错

	在build setting - player setting - api Compatibility level 选择.net 4.x 

# jetbrain rider emmylua 支持lua

	plugins - emmylua下载安装
	Setting - Editor - File Types 将 .lua.txt 加入到lua files  这样就可以直接像lua一样编写

# rider 支持unity

	plugins - unity
	安装之后rider支持unity联机调试，rider设置断点，然后debug， 再点击运行unity run即可中断


# 文件保存路径

	android Application.persistentDataPath   /storage/emulated/0/Android/data/package name/files
	windows Application.persistentDataPath:   C:\Users\username\AppData\LocalLow\company name\product name


# asset bundle

	asset bundle brower ：	unity官网提供的打包工具， 可以可视化的选择要打的包
	asset bundle manager：  unity官网提供的管理工具， 模拟模式可以本地模拟运行

	---------------------------模拟和真实加载bundle文件------------------------
	asset bundle manager 可以设置模拟模式用于开发，关闭模拟模式就是从网络下下载使用
	asset - assetbundles - simulation mode设置模拟模式用于开发的菜单路径


	---------------------------加载bundle文件------------------------
	LoadFromFile(Async)在Unity5.4以上支持streamingAsset目录加载资源
	var myLoadedAssetBundle = AssetBundle.LoadFromFile(Path.Combine(Application.streamingAssetsPath, "lua"));
    TextAsset prefab = myLoadedAssetBundle.LoadAsset<TextAsset>("assets/assetpackage/lua/test2.lua.txt");

	---------------------------web远程加载bundle文件---------------------------
	string uri = "http://118.89.188.193:8080/zswt/Android/lua";        
    UnityWebRequest request = UnityWebRequestAssetBundle.GetAssetBundle(uri, 0);
    yield return request.Send();
    AssetBundle bundle = DownloadHandlerAssetBundle.GetContent(request);
    Debug.Log(bundle.GetAllAssetNames()[0]);
    TextAsset cube = bundle.LoadAsset<TextAsset>("assets/resources/lua/test2.lua.txt");


	

# 版本对应

	unity2018 需要更新最新安卓sdk build tools 	android sdk9  android studio3.2.1


# unity设置

	


# 安卓权限

	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS" />
	
# gradle 错误

	Unable to start the daemon process.
	打开 gradle.properties 文件： 改成512M


	连接不上https://dl.google.com/dl/android/maven2/com/android/tools/build/gradle/3.2.0
	gradel.properties里面默认有一个代理服务器设置，自己有vpn需要关闭这个代理


# XLua加载bundle文件用Loader

	luaenv = new LuaEnv();
    luaenv.AddLoader(CustomLoader);
	luaenv.DoString("require 'Lua.main'");

	public static byte[] CustomLoader(ref string filepath)
    {
		// 进入游戏先缓存bundle到本地， 这里读取bundle文件， 最后返回文件的内容
 		return System.Text.Encoding.Default.GetBytes ( "这里就是文件读取的字符串" );
    }
	

# 
	
