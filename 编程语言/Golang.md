# 进程、线程、协程的关系和区别：

	进程拥有自己独立的堆和栈，既不共享堆，亦不共享栈，进程由操作系统调度。
	线程拥有自己独立的栈和共享的堆，共享堆，不共享栈，线程亦由操作系统调度(标准线程是的)。
	协程和线程一样共享堆，不共享栈，协程由程序员在协程的代码里显示调度。

	1.栈区（stack）  —   由编译器自动分配释放，存放函数的参数值，局部变量的值等。其操作方式类似于数据结构中的栈。 
	2.堆区（heap）   —   一般由程序员分配释放，若程序员不释放，程序结束时可能由OS回  

	

# Web框架


### Beego

	国人开发
	一个使用 Go 的思维来帮助您构建并开发 Go 应用程序的开源框架
	https://beego.me/

# gin

	https://www.kancloud.cn/shuangdeyu/gin_book/949451

# fiber 
	https://github.com/gofiber/fiber



#  设定path

	设定好GOROOT和GOPATH到系统路径
	GOPATH是引入库文件的存放地点

	go env -w GO111MODULE=on
	go env -w GOPROXY=https://goproxy.io,direct

# ide环境设置
	1.将goland.vmoptions内JMV内存限制改成
	-Xmx4096m
	2.help ->edit custome properties 增加
	idea.max.intellisense.filesize=999999

# Modules

	在terminal里面输入 go mod init 项目名字，自动生成go.mod文件
	
	配置goland 环境增加  GOPROXY=https://goproxy.io 

	运行就会自动下载需要的插件
	
	自己的package目录引用“项目名/”即可


# init 包初始化

	init函数不能被其他函数调用，而是在main函数执行之前，自动被调用
  
# import

	package main
	
	import "fmt"	//GoLand编辑器会自动引入包，不需要手动填写
	func main(){
		fmt.Println("dddddddddddddd")
	}

	package 别名：
	
	import fmt2 "fmt"	// 为fmt起别名为fmt2

	import不同的包名的时候， 包名要跟目录名一样， 然后引用目录就可以了
	import (""./tutorial"")		tutorial目录下面是package tutorial的go代码

	package就是目录的名字，同一个目录下面的可以跨文件调用
	跨package调用，首先需要import“./目录”， 然后需要外部package的变量或者函数需要首字母大写


	"./"  同级目录
	"../" 上级目录
	如果是同一个package，想分不同的目录，直接import目录地址到本目录即可 . "./const"


# 入门

	// 常量定义
	const PI = 3.14
	// 全局变量的声明和赋值
	var name = "gopher"

	// 一般类型声明
	type newType int
	
	// 结构的声明
	type gopher struct{}
	
	// 接口的声明
	type golang interface{}

# 输出

	fmt.Println("dddddddddddddd", "fffffff","33333")	//输出字符串连接
	fmt.Println("d",":",balance)						//字符串连接带变量
	fmt.Printf("sdfsdf --:%s", ss)						//输出格式化
	fmt.Println("")										//换行
	fmt.Printf("%v\n", p) 					// {1 2}	打印数组，切片，结构体都可以
 	fmt.Printf("%T\n", p) 					// main.point 打印类型
	fmt.Printf("%b\n", p) 					// 二进制
	fmt.Printf("%d\n", p) 					// 十进制
	fmt.Printf("%x\n", p) 					// 十六进制
	fmt.Printf("%s\n", p) 					// 字符串
	fmt.Printf("%c\n", p) 					// char
	fmt.Printf("%f\n", p) 					// float




# 字符串string

	字符串定义，反引号``中间的是原始字符串

	int,err:=strconv.Atoi(string)  		//string到int  
	int64, err := strconv.ParseInt(string, 10, 64)  	//string到int64  
	string:=strconv.Itoa(int)  				//int到string 
	string:=strconv.FormatInt(int64,10)			//int64到string 


	#float到string
	s_score := fmt.Sprintf("%.3f", 0.03)

	string := strconv.FormatFloat(float32,'E',-1,32)
	string := strconv.FormatFloat(float64,'E',-1,64)
	// 'b' (-ddddp±ddd，二进制指数)
	// 'e' (-d.dddde±dd，十进制指数)
	// 'E' (-d.ddddE±dd，十进制指数)
	// 'f' (-ddd.dddd，没有指数)
	// 'g' ('e':大指数，'f':其它情况)
	// 'G' ('E':大指数，'f':其它情况)
	
	#string到float64
	float,err := strconv.ParseFloat(string,64)
	
	#string到float32
	float,err := strconv.ParseFloat(string,32)



	string -> int -> int32(int)			// string 到int32
	strconv.Itoa(int(i))				// int32 到string
	
	string(bytes)				// []byte -> string
	 []byte(str)			// string -> []byte

	strings.Contains(str, "!!")  //字符串包含，包含返回true
	strings.ContainsAny(str, "xx") // 任何一个unicode代码点在str中
	strings.ContainsRune(str, r)  // unicode代码点r在s中
 
	strings.ToUpper				//转大写
	strings.Split(s, ".")		//字符串分割
	strings.Replace(day1,"-","",-1)		// 替换
	str[0:5]			// 字符串子串
	strings.Join(list,"&")
	strings.Trim(str, cut)	// 字符串修剪，去掉前面和后面的cut字符


	enc := mahonia.NewDecoder("gb2312")		// 转换一下编码格式 decoder是解码 ， encoder是编码成**格式，默认utf-8
	output := enc.ConvertString(string(v.ServerName))


 	f2 := fmt.Sprintf("He%03s","1")  	//格式化


	str := "ff68b4ff"
	b, _ := hex.DecodeString(str)		//将16进制字符串转换成对应的byte数组
	encodedStr := hex.EncodeToString(b)		// 再转回来




# byte buffer 

	var b bytes.Buffer //直接定义一个 Buffer 变量，而不用初始化 
	b.Writer([]byte(“Hello “)) // 可以直接使用

	b1 := new(bytes.Buffer) //直接使用 new 初始化，可以直接使用 
	// 其它两种定义方式 
	bytes.NewBuffer(buf []byte) *Buffer 
	bytes.NewBufferString(s string) *Buffer
	
 	b1.String()
	b1.Bytes()

# interface{}类型强转

	value, ok ：= interface{}.(string)    //ok 是否成功，  value值
	interface{}.(int)


# 变量声明和赋值

	
	var a					// = 使用必须使用先var声明例如：
	a=100
	
	var b = 100				//或
	var c int = 100			//或
	d := 100				// := 是声明并赋值，并且系统自动推断类型，不需要var关键字
	
	//g, h := 123, "hello"  //这种不带声明格式的只能在函数体中出现


	a = "hello"
 	b = len(a)		
	unsafe.Sizeof(a)
	输出结果为：16
	字符串类型在 go 里是个结构, 包含指向底层数组的指针和长度,这两部分每部分都是 8 个字节，所以字符串类型大小为 16 个字节。

	//默认值
	int	0
	float32	0
	pointer	nil

# 常量

	显式类型定义： const b string = "abc"
	隐式类型定义： const b = "abc"

	第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：
	const (
	    a = iota
	    b
	    c
	)

	func main() {
	    const (
	            a = iota   //0
	            b          //1
	            c          //2
	            d = "ha"   //独立值，iota += 1
	            e          //"ha"   iota += 1
	            f = 100    //iota +=1
	            g          //100  iota +=1
	            h = iota   //7,恢复计数
	            i          //8
	    )
	    fmt.Println(a,b,c,d,e,f,g,h,i)
	}
	以上实例运行结果为：
	0 1 2 ha ha 100 100 7 8

# 数组
	Go 数组的长度不可改变
	var balance [10] float32
	numbers := [6]int{1, 2, 3, 5} 
	var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}	//[]或者[...]都可以

	bb := [...]int{2,3,4}
	fmt.Printf("%v",list2)

	//初始化二维数组
	var a = [3][4]int{  
	 {0, 1, 2, 3} ,   /*  第一行索引为 0 */
	 {4, 5, 6, 7} ,   /*  第二行索引为 1 */
	 {8, 9, 10, 11},   /*  第三行索引为 2 */
	}

	// 数组增加元素
	mylist := make([]int, 0, 10)
	mylist1 := []int{1, 2, 3}
	mylist = append(mylist, mylist1...) //加上'...'就可以追加一个数组， 否则只能追加一个元素

	// 数组排重
		var strMap map[int]string = make(map[int]string,0)
		for _,v:= range arrItem {
			strMap[v] = "true"
		}
		var shopList []int= make([]int,0)
		for k,_:=range strMap{
			shopList = append(shopList,k)
		}

# 可变参数

	arg ...interface{}
	func xx(arg...)		传递可变参数


# 切片

	var identifier []type
	var slice1 []type = make([]type, len)	// len 是数组的长度并且也是切片的初始长度。

	slice1 := make([]type, len)		//简写为

	numbers[1:4]	//从索引1(包含) 到索引4(不包含)
	numbers[:3]		//从前面 到索引3(不包含)
	numbers[4:]		//从索引4(包含) 到最后

	numbers = append(numbers, 999)		//append 追加一个数组的元素
	copy(numbers1,numbers)				// copy切片


	// 切片的删除函数，要自己写
	mw.model.ip=append(mw.model.ip[:i],mw.model.ip[i+1:]...)


	// 切片是可以作为可变参数传递进去的，但是要注意写法， 后面加...
	m.SetHeader("To", mTo...)		


# map

	map在使用前必须make

	
	var map_variable map[key_data_type]value_data_type			/* 声明变量，默认 map 是 nil */
	map_variable := make(map[key_data_type]value_data_type)			/* 使用 make 函数 */


	var countryCapitalMap map[string]string
	/* 创建集合 */
	countryCapitalMap = make(map[string]string)

	/* map 插入 key-value 对，各个国家对应的首都 */
	countryCapitalMap["France"] = "Paris"
	

	countryCapitalMap["France"]					//使用
	delete(countryCapitalMap,"France")			//删除


	* 要注意， 多线程的时候，map不是线程安全的
	GlobalVar.RWMutex.RLock()
	GlobalVar.RWMutex.RUnlock()	// 读锁
	luaUIDConnectMyServer[uid]	//读写都要加锁
	GlobalVar.RWMutex.Lock()
	GlobalVar.RWMutex.Unlock()   //写的锁
	
# json

	将一个Go语言中类似movies的
	结构体slice转为JSON的过程叫编组（marshaling）。MarshalIndent把json加入了格式的编排更好看

	type book struct {
		Id   int			//结构体的成员首字母一定要大写
		Name string			//结构体的成员首字母一定要大写
		Li   []int			//结构体的成员首字母一定要大写
	}

	var book1 book
	book1.Id = 31
	book1.Name = "SS"
	book1.Li = []int{1,2,3,4}

	data, err := json.MarshalIndent(book1, "", " ")
	if err != nil {
		log.Fatalf("JSON marshaling failed: %s", err)
	}
	fmt.Printf("%s\n", data)

	var book2 book
	if err := json.Unmarshal(data, &book2); err != nil {
		log.Fatalf("JSON unmarshaling failed: %s", err)
	}
	fmt.Println(book2) 


# switch

	switch i { 
	    case 0: 
	        fmt.Printf("0") 
	    case 4, 5, 6: 
	        fmt.Printf("4, 5, 6") 
	    default: 
	        fmt.Printf("Default") 
	} 


# 运算符

	&	返回变量存储地址	&a; 将给出变量的实际地址。
	*	指针变量。	*a; 是一个指针变量
	**	指向指针的指针	
	&&	逻辑 AND 运算符。 如果两边的操作数都是 True，则条件 True，否则为 False。	(A && B) 为 False
	||	逻辑 OR 运算符。 如果两边的操作数有一个 True，则条件 True，否则为 False。	(A || B) 为 True
	!	逻辑 NOT 运算符。 如果条件为 True，则逻辑 NOT 条件 False，否则为 True。	!(A && B) 为 True

# 循环

	import "fmt"func main() {
	   for i := 1; i <= 9; i++ { // i 控制行，以及计算的最大值
	      for j := 1; j <= i; j++ { // j 控制每行的计算个数
	         fmt.Printf("%d*%d=%d ", j, i, j*i)
	      }
	      fmt.Println("")
	   }
	}

	for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。格式如下：
	for key, value := range oldMap {
	    newMap[key] = value
	}


# 函数私有和公共(函数定义风格为驼峰， python为小写下划线)

	函数名首字母小写即为 private :
	func getId() {}
	函数名首字母大写即为 public :
	func Printf() {}

	// 多返回值的函数
	func swap(x, y string) (string, string) {
	   return y, x
	}

	/* 声明函数变量 */
	getSquareRoot := func(x float64) float64 {
		return math.Sqrt(x)
	}

	
	//闭包
	package main
	
	import "fmt"
	func main() {
	    add_func := add(1,2)
	    fmt.Print(add_func())
	    fmt.Print(add_func())
	    fmt.Print(add_func())
	}
	
	// 闭包使用方法
	func add(x1, x2 int) func()(int,int)  {
	    i := 0
	    return func() (int,int){
	        i++
	        return i,x1+x2
	    }
	}

	//可变参，参数数量可变
	func sum(vals...int) int {
	total := 0
	for _, val := range vals {
	total += val
	}
	return total
	}


# 方法 (类的成员函数)

	/* 定义结构体 */
	type Circle struct {
	  radius float64
	}
	
	func main() {
	  var c1 Circle
	  c1.radius = 10.00
	  fmt.Println("Area of Circle(c1) = ", c1.getArea())
	}
	
	//该 method 属于 Circle 类型对象中的方法
	func (c Circle) getArea() float64 {
	  //c.radius 即为 Circle 类型对象中的属性
	  return 3.14 * c.radius * c.radius
	}
# 结构体 	

###结构体的成员首字母一定要大写，否则没法用json输出
###结构体最好的输出方式就是json

	type Books struct {
	   title string		//结构体的成员首字母一定要大写
	   author string		//结构体的成员首字母一定要大写
	   subject string		//结构体的成员首字母一定要大写
	   book_id int			//结构体的成员首字母一定要大写
	}
	
	var Book1 Books        /* 声明 Book1 为 Books 类型 */
	Book1.title = "Go 语言"

	//使用new创建一个Student对象,结果为指针类型
	var s *Student = new(Student)


	//结构体的嵌入， 
	type Circle struct {
	Point		//匿名嵌入， 包含 X,Y
	Radius int
	}
	type Wheel struct {
	Circle		//匿名嵌入
	Spokes int
	}
	var w Wheel
	w.X = 8		//这样就不用写全路径了


	//结构体另外的定义方法
	w = Wheel{Circle{Point{8, 8}, 5}, 20}
	w = Wheel{
	Circle: Circle{
	Point: Point{X: 8, Y: 8},
	Radius: 5,
	},
	Spokes: 20, // NOTE: trailing comma necessary here (and at Radius)
	}



	// 构造函数
	func (tt *CommonTable) NewTable(uid uint64, gameid int) TableInterface{
		return &CommonTable{TableID:uid, GameID:gameid}
	}

	// 结构体的多态采用接口的设计， 创建构造函数返回接口， 然后接口再进行函数调用
	NewTable(uid uint64, gameid int)  TableInterface




# 接口 有点类似模板，泛型

	1. 接口作为参数传递的时候， 可以代表多种类型
		


	2. 接口可以作为相同函数多态的集合

	type Phone interface {		//定义接口
    call()
	}
	
	type NokiaPhone struct {	//定义结构1
	}
	
	func (nokiaPhone NokiaPhone) call() {
	    fmt.Println("I am Nokia, I can call you!")
	}
	
	type IPhone struct {		//定义结构2
	}
	
	func (iPhone IPhone) call() {
	    fmt.Println("I am iPhone, I can call you!")
	}
	
	func main() {
    var phone Phone				//声明接口

    phone = new(NokiaPhone)
    phone.call()

    phone = new(IPhone)
    phone.call()

	}

	


# 错误处理

	func Sqrt(f float64) (float64, error) {
	if f < 0 {
		return 0, errors.New("出错了，不能小于0")
	}
		// 实现
		return f*f, nil
	}


	fmt.Println(Sqrt(-9))		//输出： 0 出错了，不能小于0

## panic和recover

	虽然Go的panic机制类似于其他语言的异常，但panic的适用场景有一些不同。由于panic会引起程序的崩溃，因此panic一般用于严重错误
	当程序遇到panic的时候（当然，也可以正常的调用出现的异常情况），系统将跳过后面的代码，进入defer，如果defer函数中recover()，则返回捕获到的panic的值， 并且只挂掉当前goroutine， 而不是整个进程


# 文件外函数引用，运行，编译

	多个文件组成的项目，直接调用即可，编译的时候一起编译	//go run test.go main.go test2.go
	程序只能有一个main入口点, 多文件的函数名不能重名
	go build test.go main.go test2.go		//编译成exe

# 反射

	类型断言语法为：expression.(Type)

	TypeOf返回接口中保存的值的类型
	if reflect.TypeOf(x).Kind() == reflect.String


	获取变量的值：
	reflect.ValueOf(x).Int()
	reflect.ValueOf(x).Float() 
	reflect.ValueOf(x).String()
	reflect.ValueOf(x).Bool()

# 单元测试

	函数名Test... 文件名..._test ，编辑器直接运行，命令行go test

	GoConvey
	是一款针对Golang的测试框架，可以管理和运行测试用例，同时提供了丰富的断言函数，并支持很多 Web 界面特性。
	func TestAdd(t *testing.T) {
	    Convey("将两数相加", t, func() {
	        So(Add(1, 2), ShouldEqual, 3)
	    })
	}


# 并发

	go 创建一个goroutine
	runtime.GOMAXPROCS(runtime.NumCPU()) //设置cpu的核的数量，从而实现高并发
	

# Channel

	是Go中的一个核心类型，你可以把它看成一个管道，通过它并发核心单元就可以发送或者接收数据进行通讯(communication)。	

	ch := make(chan int)
	make(chan int, 100)				//信道缓冲
	ch <- v    // 发送值v到Channel ch中
	v := <-ch  // 从Channel ch中接收数据，并将数据赋值给v

	chan T          // 可以接收和发送类型为 T 的数据
	chan<- float64  // 只可以用来发送 float64 类型的数据
	<-chan int      // 只可以用来接收 int 类型的数据
	<-总是优先和最左边的类型结合。(The <- operator associates with the leftmost chan possible)
	chan<- chan int    // 等价 chan<- (chan int)
	chan<- <-chan int  // 等价 chan<- (<-chan int)
	<-chan <-chan int  // 等价 <-chan (<-chan int)
	chan (<-chan int)

	
	c := make(chan int)
	defer close(c)
	go func() { c <- 3 + 4 }()
	i := <-c
	fmt.Println(i)


	x, ok := <-ch
	x, ok = <-ch
	var x, ok = <-ch	//如果OK 是false，表明接收的x是产生的零值，这个channel被关闭了或者为空。

	信道如果没有缓冲， 那么如果里面有数据而没有取走的话， 就会阻塞等待数据取走，容易形成死锁

	for x := range naturals {
		squares <- x * x
	}	// 用range来遍历信道


# sync 同步

	mutex 互斥锁
	var mutex sync.Mutex
	mutex.Lock()
	mutex.Unlock()

	RWMutex 是读写锁，它更适合读多写少的情况，性能要高一些
	多个goroutine可以同时读，读锁只会阻止写；只能一个同时写，写锁会同时阻止读写
	Lock()加写锁，Unlock()解写锁，RLock()加读锁，RUnlock()解读锁


	WaitGroup总共有三个方法：Add(delta int),Done()相当于Add(-1),Wait()执行阻塞，直到所有的WaitGroup数量变成0
	WaitGroup的特点是Wait()可以用来阻塞直到队列中的所有任务都完成时才解除阻塞，而不需要sleep一个固定的时间来等待


	sync.Pool临时对象池pool，只适合临时对象，持久对象不行，他会自动回收
	sync.Once再多的协程也只执行一次就完事
	sync.Cond是⽤来控制某个条件下，goroutine进⼊等待时期，等待信号到来

	sync.map 
	sync.Map 有以下特性：
	无须初始化，直接声明即可。
	sync.Map 不能使用 map 的方式进行取值和设置等操作，而是使用 sync.Map 的方法进行调用，Store 表示存储，Load 表示获取，Delete 表示删除。range的用法比较特殊，参考map_test
	使用 Range 配合一个回调函数进行遍历操作，通过回调函数返回内部遍历出来的值，Range 参数中回调函数的返回值在需要继续迭代遍历时，返回 true，终止迭代遍历时，返回 false。
		

# context

	使用context可以使开发者方便的在这些goroutine里传递request相关的数据、取消goroutine的signal或timeout
	 ctx, _ := context.WithTimeout(context.Background(), timeout)		// 到时间自动停止
 	 ctx, cancel := context.WithCancel(context.Background())	// 通过函数cancel()通知

	select {
		case <-ctx.Done():
			return
		}



# os 系统

	Chdir	将当前工作目录更改为dir目录
	Getwd	获取当前目录
	Mkdir	创建一个新目录
	Chmod	更改文件的权限
	Environ 返回所有环境变量
	Setenv	设定环境变量
	Exit	退出
	Getpid	获取进程id
	Hostname获取主机名
	Remove	删除文件或者目录
	Rename	重命名
	SysUsage主要用来获取进程使用系统资源

# flag
	
	解析命令行参数
	-name=zsw -age=22 -married=false

	wsPort := flag.Int("WebSocketPort", 0, "")
	flag.Parse()
	WebSocketPort = *wsPort
	

# 关键字

	defer一般用于在函数结束时执行必要的处理工作。例如，关闭文件描述符，关闭网络连接等等。
	函数中可以定义多个defer，执行的时候按照先进后出的顺序。

	go:用于并行
	chan用于channel通讯
	select：用于选择不同类型的通讯

	map用于声明自定义类型


# select

	golang 的 select 就是监听 IO 操作，当 IO 操作发生时，触发相应的动作。 
	select {
	case SendStmt:
	  //statements
	case RecvStmt:
	  //statements
	default:
	  //statements
	}
	SendStmt : channelVariable <- value
	case e1 := <-ch1:        //如果ch1通道成功读取数据，则执行该case处理语句
	RecvStmt : variable <-channelVariable


# websocket

	https://github.com/golang/net	下载repository到gopath目录$GOPATH/src/golang.org/x/net下面
	https://github.com/golang-samples/websocket	下载例子

###server

	func echoHandler(ws *websocket.Conn) {
		msg := make([]byte, 512)
		n, err := ws.Read(msg)
		if err != nil {
			log.Fatal(err)
		}
		fmt.Printf("Receive: %s\n", msg[:n])
	
		m, err := ws.Write(msg[:n])
		if err != nil {
			log.Fatal(err)
		}
		fmt.Printf("Send: %s\n", msg[:m])
	}
	
	func main() {
		http.Handle("/echo", websocket.Handler(echoHandler))
		err := http.ListenAndServe(":8080", nil)
		if err != nil {
			panic("ListenAndServe: " + err.Error())
		}
	}

###client

	func main() {
	ws, err := websocket.Dial("ws://localhost:8080/echo", "", "http://11.com")
	if err != nil {
		log.Fatal(err)
	}

	message := []byte("hello, world ，中文!")
	_, err = ws.Write(message)
	if err != nil {
		log.Fatal(err)
	}
	fmt.Printf("Send: %s\n", message)

	var msg = make([]byte, 512)
	_, err = ws.Read(msg)
	if err != nil {
		log.Fatal(err)
	}
	fmt.Printf("Receive: %s\n", msg)
}




# socket

###server

	func main() {
		service := "172.16.140.63:8081"
		listener, err := net.Listen("tcp", service)
		checkError(err)
		for {
			conn, err := listener.Accept()
			if err != nil {
				continue
			}
			handlerClient(conn)
			go handler_timer(conn)
		}
	}
	func handler_timer(conn net.Conn)  {
		for {
			sInfo := "I am server, tick！"
			clientInfo := []byte(sInfo)
			_, err := conn.Write(clientInfo)
			fmt.Println("send:"+sInfo)
			checkError(err)
	
			time.Sleep(1*time.Second)
		}
	}
	
	func handlerClient(conn net.Conn) {
		//defer conn.Close()
	
		buf := make([]byte,1024) //定义一个切片的长度是1024。
		n,err :=conn.Read(buf)
		//result, err := ioutil.ReadAll(conn)
		checkError(err)
		fmt.Println("收到客户端消息："+string(buf[:n]))
	
		sInfo := "你已经连接服务器，你的消息是！"+string(buf[:n])
		clientInfo := []byte(sInfo)
		_,err = conn.Write(clientInfo)
		checkError(err)
	}
	
	func checkError(err error) {
		if err != nil {
			fmt.Fprintf(os.Stderr, "Fatal error: %s", err.Error())
			os.Exit(1)
		}
	}

###client

	func main() {
		service := "172.16.140.63:8081"
		conn, err := net.Dial("tcp", service)
		checkError(err)
	
		_, err = conn.Write([]byte("我是客户端!"))
		checkError(err)
	
		for{
			go handlerRead(conn)
			time.Sleep(1*time.Second)
		}
		//defer conn.Close()  //断开TCP链接。
	}
	
	func handlerRead(conn net.Conn) {
		buf := make([]byte,1024) //定义一个切片的长度是1024。
		n,err :=conn.Read(buf)
	
		if err != nil && err != io.EOF {  //io.EOF在网络编程中表示对端把链接关闭了。
			log.Fatal(err)
		}
		fmt.Println(string(buf[:n])) //将接受的内容都读取出来。
		fmt.Println("")
	}

# time

	//时间戳 UnixNano的精度很高 , Unix()精度只到秒比较低
	stamp := strconv.FormatInt(time.Now().UnixNano(),10)

	t1 := time.Now()	//2018-04-22 14:27:28.7273956 +0800 CST m=+0.005000301
	t2 := t1.Unix()	//1524378448
	t3 := t1.UnixNano()	//1524378448727395600
	t4 := t1.String()	//2018-04-22 14:27:28.7273956 +0800 CST m=+0.005000301
	t5 := time.Millisecond		//1ms
	t6 := time.Now().UnixNano() / int64(time.Millisecond)	//1524378448805
	t7 := t1.Year()		//2018
	t8 := t1.Format("2006-01-02 15:04:05")		//2018-04-22 14:32:05
	t9 := time.Date(2017,2,4,5,7,8,0,time.Local)	//2017-02-04 05:07:08 +0800 CST

	// 时间增加， 可以增加日期
	time.Now().Add(time.Second)
	startTime.AddDate(0,0,1)

	//时间比较
	time.Now().After(time.Now().Add(time.Second))


	// 字符串变时间
	startTime,err := time.ParseInLocation("2006-01-02", start, time.Local)

	// 字符串变日期
	


	//定时器
	ticker := time.NewTicker(time.Second)
	defer ticker.Stop()
	select {
		case t:= <-ticker.C:
			fmt.Println("",t)
		}
	

	// 时间戳转日期
	timeLayout := "2006-01-02 15:04:05"     
	dataTimeStr := time.Unix(时间戳, 0).Format(timeLayout) //设置时间戳 使用模板格式化为日期字符串


# protocol buffer

	安装protoc windows版本, github有release版本，下载然后设置bin到系统路径下

	先下载编译工具
	go get -u github.com/golang/protobuf/protoc-gen-go

	会在GOPATH/bin目录下面新建一个exe文件
	设置GOPATH/bin目录添加为系统path

	cd到proto文件目录下面，然后再编译：
	protoc --go_out=. *.proto

	注意： proto文件必须是utf-8格式， 否则会提示--go_out: protoc-gen-go: Plugin failed with status code 1.
	注意： proto文件不要import文件， 编译之后，运行会报循环引用的错误
		proto文件如果import其他proto文件，那么要修改一下编译好的go文件，把go的import “.”去掉，都改成同目录引用，然后冲突的命名要改一下，可以用1.2.3.4.5等

	注意： 如果proto文件引用了其他文件，可以在编译的时候把引用的文件加上protoc --go_out=. a.proto b.proto

	
	test := &t.AddressBook {
		People:[]* t.Person{
			{
				Name:"zsw",
				Id:20,
				Email:"emaildd1",
				Phones:[]*t.Person_PhoneNumber{
					{
						Number:"112",
						Type:t.Person_PhoneType(t.Person_WORK),
					},
					{
						Number:"119",
						Type:t.Person_PhoneType(t.Person_HOME),
					},
				},
			},
			{
				Name:"zsw2",
				Id:2,
				Email:"emaildd2",
				Phones:[]*t.Person_PhoneNumber{
					{
						Number: "112",
						Type:t.Person_WORK,
					},
				},
			},
		},
	}


	data, err := proto.Marshal(test)
	if err != nil {
		log.Fatal("marshaling error: ", err)
	}

	fmt.Printf("%v",data)
	fmt.Println("")
	
	newTest := &t.AddressBook{}
	err = proto.Unmarshal(data, newTest)
	if err != nil {
		log.Fatal("unmarshaling error: ", err)
	}
	data_j, err := json.MarshalIndent(newTest, "", " ")
	fmt.Printf("%s",data_j)
	fmt.Println("")

	


# UI

	https://github.com/lxn/walk
	安装
	go get github.com/lxn/walk	
	go get github.com/akavel/rsrc
	rsrc -manifest test.manifest -o rsrc.syso

	编辑和编译好manifest文件, 重命名test_ui.exe.manifest, 
	注意： rsrc.syso或者test_ui.exe.manifest是用来编译用的， 所以目录下面有一个build.bat，里面写着go build
	用goland编辑器的时候，在run设置里面不要设定运行文件，而是要选择运行设置，运行整个目录，就可以了，平时run的时候用Shift+f10


	------------------------控件--------------------------------

	walk.MsgBox(mw, "Value", value, walk.MsgBoxIconInformation)  //msgbox
	DataBinder		//struct结构跟控件输入绑定
	PushButton		//按钮
	Label			
	LineEdit		//单行输入
	DateEdit		// 日期选择
	ComboBox		//下拉
	Slider			// 滑动条
	RadioButtonGroupBox	//单选组合框
	NumberEdit		// 数字输入
	CheckBox		//单选
	VSpacer			// 空白
	TextEdit		// 文本输入
	Composite		// frame
	------------------------例子--------------------------------
	
	databinding	 	//弹出一个可以编辑很多控件的窗体，返回编辑数据
	dropfiles		// 文件拖拽
	externalwidgets //特殊控件点击事件
	filebrowers		// 文件夹和文件列表
	gradientcomposite  // 控件背景渐变颜色
	listbox			//列表选项，支持点击，双击
	settinglist		// 类似excel表格的数据显示
	logview			//日志文件的显示，带滚动条的编辑框
	notifyicon		//window通知栏上多一个图标
	tableView		// 功能强大的列表控件
	

	---------------------------布局------------------------------

	布局非常容易布局， 想横着占一行就用HSplitter
	平时就一直添加就是竖着增加了
	默认控件就是比较小，但是如果整体窗体过大，会平均分配
	如果想让某一个控件变大，设置Minsize就可以了

	HSplitter{			//横着布局		
	VSplitter{			// 竖着布局

	Layout: Grid{Columns: 2},
	Layout:  VBox{},			//竖着排
	Layout:  HBox{},			//横着排
	

	Layout: Grid{Columns: 8},			//最底层的格子
			Children: []Widget{			// 子物体
				Composite{				// frame，要建多个composite
					ColumnSpan:6,		// 占几个格子
					Layout: Grid{Columns:0},	//composite的布局方式
					Children: []Widget{			// composite的子控件

	//listbox
	i := mw.lb.CurrentIndex()
		if i>=0{					//每次获取玩index要判断一下，因为不选是-1
	mw.model.PublishItemsReset()	// listbox每次需要更新的时候，就用这个函数来刷新一下

	// tableview
	看源代码， 里面有新增，删除，更新对应的刷新事件

	--------------------------后台处理同步-----------------------------------

	// 开启协程运行TCP处理
	go startTcp()
	// 启动UI
	startUI()


# go get git

	https://github.com/golang/go/wiki/GoGetTools

# SQL数据库

	go get github.com/go-xorm/xorm
	go get -u github.com/go-sql-driver/mysql	//也需要同时安装对应的数据库支持

	//数据库连接
	//Engine, err := xorm.NewEngine("odbc", "driver={SQL Server};Server="+ServerIP+";Database="+Database+";uid="+uid+";pwd="+pwd+";")
	Engine, err := xorm.NewEngine("mysql", uid+":"+pwd+"@tcp("+ServerIP+")/"+Database+"?charset=utf8")

	Engine.ShowSQL(true)	//调试的时候一定要把sql给显示出来，才方便调试

	//表跟结构的映射
	//数据库表名：test_ip , 字段ip
	type Test_ip struct {				//结构名大写，注意 结构的item name也要大写才可以
		Ip string	`xorm:"varchar(40)"`		//这里是建表用的，注意``是数字1前面的符号		
	}
	err = Engine.Sync2(new(Test_ip))		//同步结构与表名，同步绑定的时候要注意上面结构的定义，首字母大写和备注

	// 这里尤其要注意名称映射规则
	//SnakeMapper 支持struct为驼峰式命名，表结构为下划线命名之间的转换，这个是默认的Maper； * 
	//SameMapper 支持结构体名称和对应的表名称以及结构体field名称与对应的表字段名称相同的命名； * 
	engine.SetMapper(core.SameMapper{})

	engine.IsTableExist(new(AaWhiteIPList))	//判断是否存在这个表
	engine.CreateTables(new(Aaa))		//创建一个Aaa表


	var test_ii Test_ip
	var test_iii []Test_ip
	Engine.Get(&test_ii)		//获取单条数据
	println(test_ii.Ip)
	
	Engine.Find(&test_iii)		//获取多条数据
	println(len(test_iii))
	println(test_iii[0].Ip)

	_,err = engine.Exec("update test_ip set ip = ? where ip = ?", "192.2.0.0", "192.1.0.0")  // 更新数据

	engine.Insert(&test_ii)  //插入单条，因为test_ii是单个结构，不是数组
	engine.Insert(&test_iii)  //插入多条，因为test_iii是结构数组
	
	engine.Query("delete  from test_ip")		// 删除全部


		

# ini配置文件

	go get github.com/go-ini/ini

	f, _ := ini.Load("Setting.ini")
	println(f.Section("author").Key("E-MAIL").Value())


# log

	file, err := os.OpenFile("test.log",os.O_CREATE|os.O_RDWR|os.O_APPEND, os.ModeAppend|os.ModePerm)
	logger := log.New(file, "", log.LstdFlags|log.Llongfile)

	logger.Println("logs...")

# log4go
	
	第三方log，含有log4go.json配置

# seelog 目前最好用的

	seelog， 用xml做配置， 在代码里面server里面有例子， 配置xml， 还可以支持发邮件提醒

# github.com/sirupsen/logrus


# bytes

	// 发送的时候组合成头数据
	bufferT := new(bytes.Buffer)
	binary.Write(bufferT,binary.LittleEndian,uint8(0))
	binary.Write(bufferT,binary.LittleEndian,uint8(2))
	binary.Write(bufferT,binary.LittleEndian,size)
	binary.Write(bufferT,binary.LittleEndian,maincmd)
	binary.Write(bufferT,binary.LittleEndian,childcmd)
	binary.Write(bufferT,binary.LittleEndian,uint16(0))
	return bufferT.Bytes()				//组合成[]byte

	// 接收的时候，读取头数据，变换成struct
	var hh TCPHeader					//struct结构
	buf1 := bytes.NewBuffer(msg[:10])		// 用收到的[]byte变换成bytes.buffer
	binary.Read(buf1,binary.LittleEndian,&hh)		//编程struct
	bufferSize := hh.PackSize

	// bytes 包用法
	http://www.cnblogs.com/golove/p/3287729.html


	// []byte 和 []byte 连接在一起
	bufferEnd := make([]byte,size+10)
	copy(bufferEnd, bufferT)
	copy(bufferEnd[len(bufferT):], data)

	// []byte 可以 append

	// []byte转float   float转[]byte 去看示例代码里面的byte部分
	// []byte 转int32 int64  去看示例代码里面byte部分


# ssh

	"golang.org/x/crypto/ssh"
	cmd := "cmd.exe /c \"cd d:/server && d:/zswzsw\""			// windows

# mail

	自己的代码仓库里面有例子
	https://github.com/go-gomail/gomail

# atomic 原子性比mutex锁更有效率

	函数atomic.LoadInt32接受一个*int32类型的指针值，并会返回该指针值指向的那个值
	有了“原子的”这个形容词就意味着，在这里读取value的值的同时，当前计算机中的任何CPU都不会进行其它的针对此值的读或写操作。
	这样的约束是受到底层硬件的支持的。
	tmp := atomic.LoadInt32(&num)
	num = atomic.AddInt32(&tmp, 1)


# 函数作为参数 ，并执行

	AddTask(f func())   // f为函数类型
	f.Value.(func())()	
	
	type TaskFunc func()   
	func (this TaskFunc) Exec() {
		this()
	}


# 高级用法

	type World struct {
		component.Base
		*nano.Group				// 有点像继承，可以用Group这里的方法
	}
	

	if err, ok := err.(net.Error); ok && err.Timeout() {}  // 检查timeout的方法


# random

	   rand.Seed(time.Now().UnixNano()) 	//利用当前时间的UNIX时间戳初始化rand包
       x := rand.Intn(100)


# md5

	w := md5.New()
	io.WriteString(w, str)   //将str写入到w中
	md5str2: = fmt.Sprintf("%x", w.Sum(nil))  //w.Sum(nil)将w的hash转成[]byte格式



# 文件内容

	b, err := ioutil.ReadFile("test.log")
    if err != nil {
        fmt.Print(err)
    }
    str := string(b)

# vet

	vet是一个优雅的工具，每个Go开发者都要知道并会使用它。它会做代码静态检查发现可能的bug或者可疑的构造。
	go tool vet false.go  //命令


# Lua

	gopher-lua

	go和lua互相调用，传递参数

	L := lua.NewState()
	defer L.Close()

	// Lua调用go函数声明--------------------------------------------------------------
	// 声明double函数为Lua的全局函数，绑定go函数Double
	L.SetGlobal("double", L.NewFunction(Double))

	// Lua调用的go函数
	func Double(L *lua.LState) int {
		lv := L.ToInt(1)             --第一个参数
		lv2 :=  L.ToInt(2)			--第二个参数
		str := L.ToString(3)
	
		L.Push(lua.LNumber(lv * lv2)) /* push result */
		L.Push(lua.LString(str+"  call "+strconv.Itoa(lv * lv2))) /* push result */
	
		return 1                     /* number of results */
	}

	
	// 执行lua文件---------------------------------------------------------------
	if err := L.DoFile("hello.lua"); err != nil {
		fmt.Println("---------------")
		fmt.Println(err.Error())
		fmt.Println("---------------")
	}

	// 这里是go调用lua的函数---------------------------------------------------------
	if err := L.CallByParam(lua.P{
		Fn: L.GetGlobal("Zsw2"),
		NRet: 1,					//这里是返回几个参数，数量
		Protect: true,
	}, lua.LNumber(2),lua.LNumber(2)); err != nil {
		fmt.Println("---------------")
		fmt.Println("",err.Error())
		fmt.Println("----------------")
	}
	ret := L.Get(-1) // returned value
	L.Pop(1)  // remove received value			// pop 1个参数，如果上面是2个参数，就是2
	fmt.Println("lua return: ",ret)


# dll

	go文件需要注意的地方：
	import "C"   //必须加
	需要导出的函数前面增加export+函数名
	//export hello

	注意事项：
	fmt.Println 不能用，会报错，可以用println
	return 需要是int


	编译:
	go build -ldflags "-s -w" -buildmode=c-shared -o exportgo.dll dllmake.go


	func IntPtr(n int) uintptr {
		return uintptr(n)
	}
	func StrPtr(s string) uintptr {
		p:=unsafe.Pointer(&s)
		return uintptr(p)
	}


	调用1:
	DllTestDef := syscall.MustLoadDLL("libcppmakedll.dll")
	add := DllTestDef.MustFindProc("hello")
	ret, _, err := add.Call()

	调用2：
	lib := syscall.NewLazyDLL("libcppmakedll.dll")//exportgo  libcppmakedll
	add := lib.NewProc("hello")
	ret, _, err := add.Call()

	调用3：
	DllTestDef, _ := syscall.LoadLibrary("exportgo.dll")
	defer syscall.FreeLibrary(DllTestDef)
	add, err := syscall.GetProcAddress(DllTestDef, "Sum")
	ret, _, err := syscall.Syscall(add,		2,		IntPtr(1),		IntPtr(27),		0)



# windos下编译linux

 	SET CGO_ENABLED=0 SET GOOS=linux SET GOARCH=amd64 go build test.go


# 查看进程信息pprof

	_ "net/http/pprof"			// 注意这里


	//远程获取pprof数据打开浏览器http://localhost:8080/debug/pprof/
	go func() {
		log.Println(http.ListenAndServe("localhost:8080", nil))
	}()


	安装graphviz  ，添加系统目录
	控制台输入go tool pprof http://localhost:8080/debug/pprof/profile    // cpu
	控制台输入go tool pprof http://localhost:8080/debug/pprof/heap      // heap



	如果执行命令的时候加上 --inuse_objects 可以查看每个函数分配的对象数；--alloc-space 查看分配的内存空间大小。
	命令时加上 --nodefration=0.05 参数，表示如果调用的子函数使用的 CPU、memory 不超过 5%，就忽略它，不要显示在图片中


	输入web命令是生成svg图标
	top命令是排序




# http

	func httpGet() {
	    resp, err :=   http.Get("http://www.01happy.com/demo/accept.php?id=1")
	    if err != nil {
	        // handle error
	    }
	
	    defer resp.Body.Close()
	    body, err := ioutil.ReadAll(resp.Body)
	    if err != nil {
	        // handle error
	    }
	
	    fmt.Println(string(body))
	}


# 函数指针， 回调函数

	func TimerMillisecondCheckUpdate(f func(), timer time.Duration)

	ztimer.TimerMillisecondCheckUpdate(func() {
		ztimer.CheckRunTimeCost(func() {
			LuaServer.QueueRun()
		}, "LuaServer.QueueRun")
	},  20)  //


# nsq

	类似kafka的高性能消息队列
	https://nsq.io/



# GUI框架

	https://github.com/fyne-io/fyne




	
# 并发检测

	并发安全可以用go run -race 来做数据的竞争检测，如果有问题，会有warning提示




# 正则表达式



# mongo db

	http://labix.org/mgo

	Bulk() 方法进行一次性批量操作
	

	// session的复用
	s := session.Copy()
    defer s.Close()
		

	// 登录认证
	dialInfo := &mgo.DialInfo{里面写具体信息}

	bson 类似json的格式
	

	err := Collection.Update(options,bson.M{"$set":updateO})
	err := Collection.Update(options,bson.M{"$inc":updateO})
	err := Collection.Update(options,bson.M{"$push":updateO})
	err := Collection.Update(options,bson.M{"$pull":updateO})

	c.Find(bson.M{"$or": []bson.M{bson.M{"name": "Jimmy Kuu"}, bson.M{"age": 31}}}).All(&users)