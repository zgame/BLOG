# unity 2018.3.0 Xlua 报错

	在build setting - player setting - api Compatibility level 选择.net 4.x 

# jetbrain rider emmylua 支持lua

	plugins - emmylua下载安装
	Setting - Editor - File Types 将 .lua.txt 加入到lua files  这样就可以直接像lua一样编写

# rider 支持unity

	rider安装之后，还需要安装NDP471-KB4033342-x86-x64-AllOS-ENU，  .net4.7
	plugins - unity
	安装之后rider支持unity联机调试，rider设置断点，然后debug， 再点击运行unity run即可中断

# 版本对应

	unity2018 需要更新最新安卓sdk build tools 	android sdk9  android studio3.2.1

# 设置

	有unsafe代码的话，可以在player setting里面设置allow unsafe code

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

	---------------------------读取所有的依赖，自动加载依赖---------------------------
	var AndroidManifest = GetAssetBundle("Android");
    GlobalManifest = AndroidManifest.LoadAsset<AssetBundleManifest>("AssetBundleManifest");
	var dependenciesList = GlobalManifest.GetAllDependencies(fileName);
    if (dependenciesList.Length > 0)
       foreach (var VARIABLE in dependenciesList)    


	AssetBundle打包出来会丢失Shader。要把可能用到的Shader加入到Edit->Project Settings->Graphics->Always Included Shaders这个列表里。


# asset bundle 贴图丢失问题，需要添加额外的shader到setting里面

	将用到的Shader加到Editor->Project Settings -> Graphics Settings
	Always Included Shaders 的Shader列表里再进行打包即可。

	编辑里面andorid模式不行的，打包到手机ok的，所以编辑器用window模式


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

# lua增加第三方lua库

	可以直接用xlua作者自己githbu上面的封装dll， 封装了lua protocol,  覆盖plgins里面dll
	copy BuildInInit.cs是一些库的接口定义

	luaenv.AddBuildin("rapidjson", XLua.LuaDLL.Lua.LoadRapidJson);
    luaenv.AddBuildin("lpeg", XLua.LuaDLL.Lua.LoadLpeg);
    luaenv.AddBuildin("pb", XLua.LuaDLL.Lua.LoadLuaProfobuf);
    luaenv.AddBuildin("ffi", XLua.LuaDLL.Lua.LoadFFI);
        
    luaenv.DoString(@"require 'Lua/main'");

	
# lua调用C# 

	local ReadBundles = CS.ReadBundles		//ReadBundles是c#的class
	--print(ReadBundles:getsss())	// 调用ReadBundles的静态函数
	--print(ReadBundles.getsss())	// 调用ReadBundles的静态函数 ， : .都可以


	typeof(CS.Cinemachine.CinemachineVirtualCamera)	-- 调用cs的第三方库文件


# C#调用lua
	
	这里要注意一下，因为c# socket为异步回调多线程，所以要求线程安全， 不然会crash
	1.在Unity-player setting-Scripting Define Symbols 增加THREAD_SAFE
	2.然后调用代码写为：
	
	 [CSharpCallLua]
	    public delegate void FDelegatezzz(int a, int b, string c, string d);
	
	......
	#if THREAD_SAFE || HOTFIX_ENABLE
	            lock (ReadBundles.luaenv.luaEnvLock)
	#endif
	            {
	                FDelegatezzz f = ReadBundles.luaenv.Global.Get<FDelegatezzz>("GoCallLuaNetWorkReceive");
	                f(1, 1, "", "");
	            }
	.....



# lua操作UI

	local object = CS.UnityEngine.GameObject.Find('MainCanvas/DownLoadBundleFilePanel')  // 获取物体
	CS.UnityEngine.GameObject.Destroy (DownLoadBundleFilePanelObject)	 //销毁物体
	DownLoadBundleFilePanelObject:SetActive(false)			// 隐藏物体
	prefab:GetComponentInChildren(typeof(CS.UnityEngine.UI.Button)).onClick:AddListener(func) // 绑定按钮事件
	
	obj:GetComponent(typeof(CS.UnityEngine.RectTransform)).offsetMin = CS.UnityEngine.Vector2.zero;
    obj:GetComponent(typeof(CS.UnityEngine.RectTransform)).offsetMax = CS.UnityEngine.Vector2.zero;
    obj.transform.localScale = CS.UnityEngine.Vector3.one;
    obj.transform.localPosition = CS.UnityEngine.Vector3.zero
    obj:SetActive(true)



	self.Model.transform.localPosition = CS.UnityEngine.Vector3(0, 0, self.Model.transform.localPosition.z + 1);
 	self.Model.transform.localRotation = CS.UnityEngine.Quaternion.Euler(0, 180, 0);


	damageNumber:GetComponent(typeof(CS.UnityEngine.UI.Text)).text = ""..damage
	local mScreen= CS.UnityEngine.Camera.main:WorldToScreenPoint(parent.transform.position + CS.UnityEngine.Vector3(0,5,0))
    damageNumber:GetComponent(typeof(CS.UnityEngine.RectTransform)).position = mScreen


	local position = damageNumber:GetComponent(typeof(CS.UnityEngine.RectTransform)).position
    local tween = damageNumber.transform:DOMove(CS.UnityEngine.Vector3(position.x  , position.y  + 30 , position.z ),0.5)
    tween:SetEase(CS.DG.Tweening.Ease.OutQuad)       -- 设定移动方式

	hpSlider:GetComponentInChildren(typeof(CS.UnityEngine.UI.Slider)).value = parentCharacter.HP/ parentCharacter.MaxHP


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




#  对齐方式 layout

	canvas 设置成scale with screen size 

	首先注意，控件的周围要设置锚点（十字花），可以将锚点跟控件大小保持一致，这样可以缩放
	另外注意，left，right，top，bottom最好都置为0， 对齐
	
	大部分情况都是全屏进行缩放，文字也是，可以选择best fit来进行自动缩放
	Content Size Fitter		自动识别
	Layout Element		设定最大，最小
	Aspect Ratio Fitter 根据宽高，根据父物体


# scrollView的使用

	horizontal 横向
	vertical  纵向
	elastic   默认就选这个，正常滑动

	---ScrollView-ViewPort-Content增加下面2个控件--
	vertical Layout Group 纵向排列用的，child controls size Height可以让子控件的大小进行自动缩放
	Content Size Fitter	缩放用的，vertical fit选择preferred size，让列表可以识别里面子控件的数量而自动增加长度
	
	-----------Content增加Layout Element控件---------------------------
	preferred Height 设置子元素的合适尺寸



# json

	var localList =  (List<object>)MiniJSON.Json.Deserialize(localVersionText);
    foreach (var version in localList)
     {
        var value = (Dictionary<string, object>) version;
		}


# unity设定摄像机快捷键

	ctrl+shift+f


# animator controller 

	设置状态机，也可以设置子状态机，分支树

	如果一个动画有Conditions建议取消Has Exit Time，会出现无法及时触发的问题。
	Has Exit Time就是必须过度的时间，处于这个时间时，是不允许任何对动画的操作的。
	
	local animator2 = monster2:GetComponent(typeof(CS.UnityEngine.Animator))
	animator2:SetInteger("attack",1)    // 设定int参数值
	animator2:SetTrigger("attack")		// trigger

	local info = self.Animator:GetCurrentAnimatorStateInfo(0)
    if info:IsName("Attack")  then


# 调试


 	print(type(info))					-- 查看类型
    print(MySerpent.block(info))		-- 输出table



# 协程

	cs_coroutine.start(function()
        coroutine.yield(CS.UnityEngine.WaitForSeconds(0.2))     -- 这里用协程暂停0.2秒
		coroutine.yield(CS.UnityEngine.WaitForEndOfFrame())		--这里等待一帧



# DoTween 

	c# 映射文件Assets/Editor/XLuaCustormExport.cs  在里面编辑lua要用到的函数
	
	写好C#的映射文件之后，xlua生成代码
	local tween = tauren.Model.transform:DOMoveX(1,3)		-- 移动
	local tween = self.Model.transform:DOMove(CS.UnityEngine.Vector3(0, 0, self.Model.transform.localPosition.z + 2),0.5)						-- 第一个参数是目的地， 第二个参数是时间


    tween:SetEase(CS.DG.Tweening.Ease.Linear)	-- 设置移动方式为平均移动， 不然默认是缓冲

	https://blog.csdn.net/u013762848/article/details/82256276	ease的集中方式


# Cinemachine

	可以设定很多虚拟相机，进行不同情况下相机之间的切换
	可以切换，融合，设定轨迹，围绕，震动，触发控制等相机控制机制

	VirtualCamera 可以设置跟踪
	FreeLook  自由旋转查看，设置follow和look at， 然后可以设定上，中，下，三个圆环的大小和高度
	
	DollyTrack和DollyCart 自动旋转镜头  
	相机Auto Dolly开启，增加extension follow zoom, follow要跟着DollyCart,Aim设定Hard Look At
	DollyTrack设定几个点，然后设定looped圆圈循环
	DollyCart指定DollyTrack和移动速度

	clearShot 适合有遮挡的地方，会自动切换其他视角的相机



# 制作伤害数字效果

	一张0-9的数字图，将它的Texture Type 改为 Sprite(2D and UI)，Sprite Mode改为 Multiple，点击Apply保存后，打开 Sprite Editor 对字符图进行编辑，在Sprite Editor窗口下，点击左上角的Slice按钮就可以对当前图片进行自动切分。
	
	创建Material， 选择 GUI/Text Shader
	创建Custom Font ,选择材质， 然后填写图片切分的数据, 设置Ascii Start Offset为48(因为ascii码0是48，1是49)
	Uv x 0 y 0 w 0.1 H 1
	Vert x 0 y 0 w 40 H -59（这里用负数） 
	advance 40 间距
	

# NGUI

	c# 映射文件Assets/Editor/XLuaCustormExport.cs  在里面编辑lua要用到的函数
	写好C#的映射文件之后，xlua生成代码
	CS.UIEventListener.Get(***.gameObject).onClick = function() end


# OnTriggerEnter

	C# CallTriggerEnter.cs
	public class CallTriggerEnter : MonoBehaviour
	{
	    public Action<Collider> handler;
	    public void OnTriggerEnter(Collider other)
	    {
	        if (handler != null)
	            handler(other);
	    }
	}

	lua调用
	gameObject:AddComponent(typeof(CS.CallTriggerEnter)).handler = function(other) end


#
	