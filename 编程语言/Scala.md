# 变量

	不可变常量val
	变量 var
	延迟val变量计算一次，第一次访问变量。只有vals可以是惰性变量。


# 数据类型

	val x = !false 
	val x = "X" 
	println(s"Book Title is ${ bookTitle}" ); // 字符串插值
	val x: Byte = 30 	// 指定数字类型


# 范围

	var v = 1 to 10        // (1 to  10) 
    v = 1 until 10        //  (1 to 9) 
     val v1 = 1 to 10 by 3   // step by 3

# 元组

	元组是具有相同或不同类型的两个或更多个值的有序容器。
	然而，与列表和数组不同，没有办法迭代元组中的元素。
	它的目的只是作为一个多个值的容器。

# for循环

	 for (book<-books)
	 for (i <- 1 to 10) 
	for (breed <- dogBreeds 
       if breed.contains("D") 
     )
	for {
        book <- books
        bookVal = book.toUpperCase()
    }
	// 生成新的集合
	 val filteredBreeds = for { 
       breed <- dogBreeds 
       if breed.contains("T") &&  !breed.startsWith("Y") 
     } yield breed


# 模式匹配

	  for (m <- anyList) {
        m match {
            case i: Int => println("Integer: " + i)
            case s: String => println("String: " + s)
            case f: Double => println("Double: " + f)
            case other => println("other: " + other)
        }
     } 

# 函数

	object Main {
	  def main(args: Array[String]) {
	      def add(x: Int, y: Int): Int = { x + y } 
	      
	      println(add(5, 5) );
	  }
	}

# 函数式编程

	
	函数体可以放在变量里面，可以作为参数或者返回值


# 类

	class Rectangle(val width:Double,val height:Double) extends Shape {
   		override def area:Double = width*height
	}


# 单例

	object Car {
	   def drive {
	      println("drive car")
	   }
	}

# 接口	Scala Traits

	Traits就像Java中的接口，它也可以包含代码。
	在Scala中，当一个类从trait继承时，它实现trait的接口，并继承trait中包含的所有代码。
	在Scala中，traits可以继承类。

