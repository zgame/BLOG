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
	
      FDelegatezzz f = ReadBundles.luaenv.Global.Get<FDelegatezzz>("GoCallLuaNetWorkReceive");
      f(1, 1, "", "");



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

	transform:GetChild(i)	-- 获取第几个子物体
	transform:SetSiblingIndex(i)	--设定在所有子物体中的排序


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
	
	MySerpent = require("serpent")
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

	DOMove()			-- 绝对坐标
	DOLocalMoveX()		-- 相对坐标


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
	GetComponent(typeof(CS.UISprite)).spriteName = ""

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


# 刚体约束

	m_Rigidbody.constraints = RigidbodyConstraints.None;
	m_Rigidbody.constraints = RigidbodyConstraints.FreezePositionZ | RigidbodyConstraints.FreezeRotationZ;


# log view 

	https://github.com/aliessmael/Unity-Logs-Viewer
	导入unity包， 菜单点击Reporter->Create
	Edit -> Project Settings 设置 Scrip execution order 里面优先级为最高级，即可使用
	画一个圆圈， 就会进入log界面， 可以缩放，就有关闭按钮


# xlua生成代码报错

	需要把xlua的黑名单，加入到我们自己定义的XLuaCustormExport文件里面去
	 BlackList = new List<List<string>>()
	  {
	     new List<string>(){"UnityEngine.Light", "shadowRadius"},
	     new List<string>(){"UnityEngine.Light", "shadowAngle"},
	  };

# -------------------------------------------------------------------------------

# GI 实时全局光照

	Shrine Arch-viz Demo 官方示例
	实时GI = 静态光照图Lightmaps、灯光探针Light Probes、反射探针Reflection Probes

# Unity PostProcess 后处理

	Anti-aliasing	FXAA：开销较低的一种抗锯齿方案
					TAA对画质的改善较好，满足静态、动态的画面边缘平滑处理
	Dithering		使用8-bit dithering像素点抖动技术，消除色阶。

	HDRP Volume Profile
	1) Ambient Occlusion 环境光影响，环境光吸收
	2) Auto Exposure 自动曝光用于调整图像的亮度范围
	3) Bloom 明亮区域扩散出来的柔光效果
	4) Chromatic Aberration 色差效果，模拟相机镜头的颜色偏移
	5) Color Grading 画面的色调
	6) Depth of Field 景深
	7) Grain 颗粒效果
	8) Lens Distortion 镜头扭曲
	9）Motion Blur 运动模糊
	10）Screen Space Reflections屏幕空间反射是一种伪反射效果，模拟潮湿的地板或水坑的表面反射
	11）Vignette 暗角效果 

# IL2CPP

	将mono转换成ILVM， 编译成C++代码之后，体积会变小，性能提升一倍

# 正向渲染和延迟渲染，可编程渲染SRP

	延迟渲染主要包含了两个Pass：
	
	第一个Pass用于渲染G缓冲，在这个Pass中，不进行光照计算，仅仅计算哪些片元是可见的，如果一个片元是可见的，就把它的相关信息（漫反射颜色、高光反射颜色、法线、自发光和深度等信息）存储到G缓冲区中。对于每一个物体，这个Pass仅会执行一次。
	第二个Pass用于计算真正的光照模型。该Pass会使用上一个Pass渲染的数据来计算最终的光照颜色，再存储到帧缓冲中。
	
	延迟渲染可以用来加快渲染真实的光线计算，但是不允许我们渲染半透明物体，且没有抗锯齿，依赖显卡支持， 主要是光源越多，优势越好。
	一般说来，如果我们的游戏有大量的实时光照、阴影和反射并允许在高端硬件上，延迟渲染(Deferred Rendering)是更好的选择。如果我们的游戏允许在低端硬件，并且并没有用到上面的特性，就应该旋转正向渲染(Forward Rendering)。

# 渲染的步骤rendering pipeline

	中央处理器器(CPU)，决定哪些对象需要渲染以及要怎么渲染。
	CPU发送指令给图像处理器(GPU)。
	GPU根据CPU指令进行渲染。

	渲染管道(the rendering pipeline)

	渲染一帧，CPU需要完成以下工作： 
	1.CPU检测场景中的每一个物件，决定它是否需要被渲染。一个object只有达成某些特定的条件才能被渲染。例如，object的包围盒的一部分必须在摄像机的视锥体中。一个object被裁剪后也不会被渲染。
	2.CPU收集每一个需要渲染的的object的信息，并将它们按顺序生成名为 draw calls 的命令。一个 draw call 包含了一个模型和如何渲染这个模型的信息。例如，使用哪一张贴图。在特定的情况下，使用同一种设置的objects将被合并成一个draw call。将不同的objects合并成一个draw call 被叫做合批(batching)。 CPU为每一个draw call创建个一个名为batch的数据包，数据包可能还会包含一些除了drawcalls的额外数据，但是这些一般和性能问题关系不大，所以在这里暂不讨论。

	
	为每一个drawcall,CPU将做如下工作： 
	1.CPU将发送一个命令给GPU,告诉GPU改变某些被称为渲染状态( render state )的变量。这个命令变为称为( SetPass call )。一个SetPass call告诉GPU，下一个模型将使用什么设置来渲染。只有当下一个模型所需要的render state和前一个模型不应的时候，SetPass Call才会被发送。
	2.CPU发送draw call给GPU。GPU使用最近的一次SetPass call设置的渲染状态，渲染draw call中的模型。
	3.在某些情况下，一个 batch 可能有多个 pass。pass是shader代码中的一个片段。一个新的pass需要改变渲染状态。对batch中的每一个pass,CPU需要发送一个新的SetPass call和draw call。

	GPU进行如下工作： 
	1.GPU按顺序处理CPU发送过来的任务。
	2.如果当前任务是SetPass call,GPU更新render state。
	3.如果当期任务是Draw call,GPU渲染模型。这一步在shader code中分为不同的阶段。由于比较复杂，这篇文件中不更深入的讲解。但是我们有必要知道的是，shader代码中名为vertex shader的部分告诉GPU处理模型的顶点，名为fragment shader的部分告诉GPU处理像素。
	4.一直重复上面的操作直到所有的CPU请求被处理。


	在Unity渲染过程中，有三种不同的线程：主线程、渲染线程、工作线程。主线程承担游戏的大部分CPU任务，包括一些渲染任务。渲染线程专门用来给GPU发送渲染指令。工作线程主要用来剔除或模型蒙皮。


# 加强渲染效率

	降低需要渲染的objects的数量是降低batches和SetPass calls最简单的方法
	1.用摄像机的 Layer Cull Distance属性。它针对不同layers的物体，可以设置不同的剔除距离。
	2.遮挡剔除(occlusion culling)。
	
	降低objects的渲染次数 
	少用动态光，用烘焙，少用反射探针.

	合并Objects 
	1. 使用同一个材质球，使用同样的材质球设置(贴图，shader和shader参数)
	2. 静态合批(Static batching) 将那些不会移动的满足条件的objects合并成一个批次
	3. 动态合批(Dynamic batching)
	4. GPU instancing使用将大量相同的objects高效合批的技术，如果我们的游戏需要同时渲染大量相同的模型，这些技术将非常有用。
	
	在模型导入设置中，如果我们不勾选import animations选择，导入时Unity会使用MeshRender代替SkinnedMeshRenderer。

	如果存储带宽是主要问题，我们应该降低贴图的内存使用，压缩或者降低贴图质量

	
#  Universal Render Pipeline通用渲染管线（LWRP）

	URP是一种预置的可编程渲染管线。可以实现快速的渲染而不需要shader技术。URP使用简化的基于物理的光照和材质。
	
# HDRP
	
	HDRP不支持opengl

# 深度贴图

	深度贴图类似于灰度图像，每个像素值表示的是传感器距离物体的实际距离。

# 渲染管线流程

	1）几何变换和光照使用的顶点着色器处理
	2）裁剪和深度测试
	3）去采样，去计算颜色以及雾化处理等使用的片段着色器
	4）光栅化处理
	5）绘制半透明和全透明物体
	6）混合

	
# Shader 

	1. 属性，外部可以调节的参数，括号里面是外部显示的名字
	Properties {
	_Color ("Main Color", Color) = (1,1,1,0.5)
	_SpecColor ("Spec Color", Color) = (1,1,1,1)
	_Emission ("Emmisive Color", Color) = (0,0,0,0)
	_Shininess ("Shininess", Range (0.01, 1)) = 0.7
	_MainTex ("Base (RGB)", 2D) = "white" { }
    }

	2. subShader shader可包含多个子着色器 (SubShaders) Unity 渲染着色器时，将仔细查看所有子着色器，然后使用硬件支持的一个子着色器。
	
	3. pass 每个子着色器是一个通道集合。每个通道的对象几何图像需要渲染，因此必须至少有一个通道。顶点光照 (VertexLit) 着色器只有一个通道 .
	4. 使用 Material 块将属性值绑定至固定功能照明材质设置。
	5. 命令 Lighting On可打开标准顶点照明
	6. SeparateSpecular On 可将单独的颜色用于高亮点。
	7. SetTexture 定义我们需要使用的纹理以及如何在渲染中混合、组合和应用这些纹理。
	8. Combine 命令执行此任务，此命令可指定此纹理与其他纹理或颜色混合的方式。
	9. Fallback 命令指出当用户图形硬件上没有运行当前着色器中的任何子着色器 (SubShaders) 时，应该使用哪种着色器。
	10. 命令 UsePass 可以使用其他着色器中定义的通道可快速构建子着色器。


	float、half、fixed (精度分别是高，中，低)
	

# CG 

	CGPROGRAM
		#pragma vertex name 说明给定函数的顶点程序包含的代码（此处为 vert）。
		#pragma fragment name 说明给定函数的片段程序包含的代码（此处为 frag）。
		#include "UnityCG.cginc"
		struct v2f {		//定义一个“顶点至片段”结构,从顶点传递至片段程序的信息
		float4 pos :SV_POSITION;
		float3 color :COLOR0;
		};		//传递位置和颜色参数

		v2f vert (appdata_base v)
		{
		v2f o;
		o.pos = mul (UNITY_MATRIX_MVP, v.vertex);
		o.color = v.normal * 0.5 + 0.5;
		return o;		//顶点程序计算出颜色并只在片段程序中输出
		}
		
		half4 frag (v2f i) :COLOR
		{
		//法线组件位于 -1..1 范围之间，但颜色位于 0..1 范围之间，所以我们微调并微移上述代码中的法线
		return half4 (i.color, 1);//只输出计算的颜色和 1 作为 alpha 组件
		}	
	ENDCG

# GLSL


# HLSL 


# 表面着色器 Surface Shader

	用它来编写光照着色器比用低级的顶点/像素着色器程序容易得多

	struct SurfaceOutput {
	    half3 Albedo;			表面反射率
	    half3 Normal;			法线
	    half3 Emission;			发射量
	    half Specular;			高光
	    half Gloss;				光泽
	    half Alpha;				透明
	};

	void myvert (inout appdata_full v, out Input data)
	void vert (inout appdata_full v, out Input o) 
	void mycolor (Input IN, SurfaceOutput o, inout fixed4 color)
	void surf (Input IN, inout SurfaceOutput o)


