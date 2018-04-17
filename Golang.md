# Web框架

### Revel

	不推荐使用

### Beego

	国人开发
	一个使用 Go 的思维来帮助您构建并开发 Go 应用程序的开源框架
	https://beego.me/

### martini

	比较简单，不复杂
	https://github.com/codegangsta/martini 


---

# 游戏框架

### goworld

	GoWorld通过进程替换来实现游戏逻辑的热更新
	https://github.com/xiaonanln/goworld
	


### leaf

	https://github.com/name5566/leaf

---

#  语法

### 入门  

	package main
	//GoLand编辑器会自动引入包，不需要手动填写
	import "fmt"	
	func main(){
		fmt.Println("dddddddddddddd")
	}

	package 别名：
	// 为fmt起别名为fmt2
	import fmt2 "fmt"

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

### 输出

	fmt.Println("dddddddddddddd", "fffffff","33333")	//输出字符串连接
	fmt.Println("d",":",balance)						//字符串连接带变量
	fmt.Printf("sdfsdf --:%s", ss)						//输出格式化
	fmt.Println("")										//换行


### 变量声明和赋值

	
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

	var balance [10] float32
	numbers := [6]int{1, 2, 3, 5} 
	var balance = []float32{1000.0, 2.0, 3.4, 7.0, 50.0}	//[]或者[...]都可以

	//初始化二维数组
	a = [3][4]int{  
	 {0, 1, 2, 3} ,   /*  第一行索引为 0 */
	 {4, 5, 6, 7} ,   /*  第二行索引为 1 */
	 {8, 9, 10, 11}   /*  第三行索引为 2 */
	}

# 切片

	var identifier []type
	var slice1 []type = make([]type, len)	// len 是数组的长度并且也是切片的初始长度。
	slice1 := make([]type, len)		//简写为

	numbers[1:4]	//从索引1(包含) 到索引4(不包含)
	numbers[:3]		//从前面 到索引3(不包含)
	numbers[4:]		//从索引4(包含) 到最后

	numbers = append(numbers, 999)		//append 追加一个数组的元素
	copy(numbers1,numbers)				// copy切片


### map

	/* 声明变量，默认 map 是 nil */
	var map_variable map[key_data_type]value_data_type
	/* 使用 make 函数 */
	map_variable := make(map[key_data_type]value_data_type)


	var countryCapitalMap map[string]string
	/* 创建集合 */
	countryCapitalMap = make(map[string]string)

	/* map 插入 key-value 对，各个国家对应的首都 */
	countryCapitalMap["France"] = "Paris"
	

	countryCapitalMap["France"]					//使用
	delete(countryCapitalMap,"France")			//删除


### 运算符

	&	返回变量存储地址	&a; 将给出变量的实际地址。
	*	指针变量。	*a; 是一个指针变量
	**	指向指针的指针	
	&&	逻辑 AND 运算符。 如果两边的操作数都是 True，则条件 True，否则为 False。	(A && B) 为 False
	||	逻辑 OR 运算符。 如果两边的操作数有一个 True，则条件 True，否则为 False。	(A || B) 为 True
	!	逻辑 NOT 运算符。 如果条件为 True，则逻辑 NOT 条件 False，否则为 True。	!(A && B) 为 True

### 循环

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


### 函数私有和公共

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


### 方法 (类的成员函数)

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

### 结构体 （类的成员变量）

	type Books struct {
	   title string
	   author string
	   subject string
	   book_id int
	}
	
	var Book1 Books        /* 声明 Book1 为 Books 类型 */
	Book1.title = "Go 语言"

### 接口

	type Phone interface {
    call()
	}
	
	type NokiaPhone struct {
	}
	
	func (nokiaPhone NokiaPhone) call() {
	    fmt.Println("I am Nokia, I can call you!")
	}
	
	type IPhone struct {
	}
	
	func (iPhone IPhone) call() {
	    fmt.Println("I am iPhone, I can call you!")
	}
	
	func main() {
    var phone Phone

    phone = new(NokiaPhone)
    phone.call()

    phone = new(IPhone)
    phone.call()

	}


### 错误处理

	func Sqrt(f float64) (float64, error) {
	if f < 0 {
		return 0, errors.New("出错了，不能小于0")
	}
		// 实现
		return f*f, nil
	}


	fmt.Println(Sqrt(-9))		//输出： 0 出错了，不能小于0


### 文件外函数引用

	多个文件组成的项目，直接调用即可，编译的时候一起编译	//go run test.go main.go test2.go
	程序只能有一个main入口点, 多文件的函数名不能重名


### 反射

		