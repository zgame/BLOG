# unity 2018.3.0 Xlua 报错

	在build setting - player setting - api Compatibility level 选择.net 4.x 

# jetbrain rider emmylua 支持lua

	plugins - emmylua下载安装
	Setting - Editor - File Types 将 .lua.txt 加入到lua files  这样就可以直接像lua一样编写

# rider 支持unity

	plugins - unity
	安装之后rider支持unity联机调试，rider设置断点，然后debug， 再点击运行unity run即可中断

# 版本对应

	unity2018 需要更新最新安卓sdk build tools 	android sdk9  android studio3.2.1

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


# ----------------------------------文件操作---------------------------------------------

# 文件保存路径
	Application.dataPath		Asset目录
	Application.streamingAssetsPath	streamingAssets
	Application.persistentDataPath  外部存储document保存文件尽量保存到这里，记得安卓要开放写sd卡权限

	IOS Application.persistentDataPath  /var/mobile/Containers/Data/Application/app sandbox/Documents
	android Application.persistentDataPath   /storage/emulated/0/Android/data/package name/files
	windows Application.persistentDataPath:   C:\Users\soonyo\AppData\LocalLow\zgame\test1

# 文件夹操作

	 var pathDir = Path.GetDirectoryName(localPath);  // 该函数从字符串中获取路径
        if (!Directory.Exists(pathDir))
        {
            Directory.CreateDirectory(pathDir);            
            Debug.Log(pathDir + "  目录被创建了");
        }


# 本地文件读写

	// 文件写入
	 FileInfo file= new FileInfo(localVersionPath);
            if(!file.Exists)
            {
                //如果不存在就创建文件
                var str=file.Create();
                str.Write(System.Text.Encoding.Default.GetBytes ( wwwlogin.text) , 0  , wwwlogin.text.Length);
                str.Close();
                str.Dispose();//文件流释放
            }
	// 文件读出
	var url = Application.dataPath + "/assetpackage/" + luaFileName + ".lua.txt";
	var localVersionText = File.ReadAllText(url);

# www获取web文件 

	//轻松获取文件内容
	string urlPath = "http://118.89.188.193:8080/zswt/Android/lua.manifest";
    WWW wwwlogin = new WWW(urlPath);
    yield return wwwlogin;
    if (wwwlogin.text != null){.......}

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


# ---------------------------------- XLua---------------------------------------------	

# XLua加载bundle文件用Loader

	luaenv = new LuaEnv();
    luaenv.AddLoader(CustomLoader);
	luaenv.DoString("require 'Lua.main'");

	public static byte[] CustomLoader(ref string filepath)
    {
		// 进入游戏先缓存bundle到本地， 这里读取bundle文件， 最后返回文件的内容
 		return System.Text.Encoding.Default.GetBytes ( "这里就是文件读取的字符串" );
    }
	
# lua调用C# 

	local ReadBundles = CS.ReadBundles		//ReadBundles是c#的class
	--print(ReadBundles:getsss())	// 调用ReadBundles的静态函数
	--print(ReadBundles.getsss())	// 调用ReadBundles的静态函数 ， : .都可以


# lua操作UI

	local object = CS.UnityEngine.GameObject.Find('MainCanvas/DownLoadBundleFilePanel')  // 获取物体
	CS.UnityEngine.GameObject.Destroy (DownLoadBundleFilePanelObject)	 //销毁物体




# ----------------------------------UI---------------------------------------------
# gameobject生成之后的初始化

		// 生成物体，然后放到父物体下面，然后设置对齐位置
		var obj = GameObject.Instantiate(prefab, GameObject.Find(parentDir).gameObject.transform, true);
        obj.GetComponent<RectTransform>().offsetMin = new Vector2(0.0f, 0.0f);
        obj.GetComponent<RectTransform>().offsetMax = new Vector2(0.0f, 0.0f);



# UI使用图集	

	// 打包成图集
	Editor->Project Settings -> Editor -> Sprite Packer -> Always Enabled(Legacy Sprite Packer)
	在UI图片的目录下，全选点击， Texture Type 为Sprite(2D and UI) ， 把要打在一起的图集命名一致即可
	菜单栏打开 Window -> 2D -> Sprite Packers
	图集保存在和Assets文件夹同级的目录，Libary/AtlasCache里面
	
	// 编辑图片九宫格
	菜单栏打开 Window -> 2D -> Sprite Editor 进行图片的边界设定, 是用来做九宫格的，直接选择图片的属性也可以编辑




#  对齐方式

	首先注意，控件的周围要设置锚点（十字花），可以将锚点跟控件大小保持一致，这样可以缩放
	另外注意，left，right，top，bottom最好都置为0， 对齐
	
	大部分情况都是全屏进行缩放，文字也是，可以选择best fit来进行自动缩放





# json

	var localList =  (List<object>)MiniJSON.Json.Deserialize(localVersionText);
    foreach (var version in localList)
     {
        var value = (Dictionary<string, object>) version;
		}