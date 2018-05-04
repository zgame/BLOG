# 下载地址

	https://github.com/google/protobuf/releases
	
	下载proc编译器
	设置环境变量


# 编辑工具

	eclipse有专门的插件可以用来高亮编辑


###编译

	cd 到文件目录
	protoc -I=./ --python_out=./ books.proto


# 调用

###proto文件定义
	
	protobuf-3.5.1\examples\addressbook.proto


###python调用

	def PromptForAddress(person):
	  person.id = 20
	  person.name = "333"
	  person.email = 'sdfsdfsdf'
	
	  phone_number = person.phones.add()
	  phone_number.number = '5555555555'
	  phone_number.type = bk.Person.WORK

	address_book = bk.AddressBook()
	PromptForAddress(address_book.people.add())
	
	sss = address_book.SerializeToString()
	print(sss)
	
	newbook = bk.AddressBook()
	newbook.ParseFromString(sss)
	print(newbook)
	print(newbook.people.id)

### 输出

	# 转化成string的传输的
	b'\n"\n\x03333\x10\x14\x1a\tsdfsdfsdf"\x0e\n\n5555555555\x10\x02'

	# 传输数据转化回来
	people {
	  name: "333"
	  id: 20
	  email: "sdfsdfsdf"
	  phones {
	    number: "5555555555"
	    type: WORK
	  }
	}



# golang

	先下载编译工具
	go get -u github.com/golang/protobuf/protoc-gen-go

	会在GOPATH/bin目录下面新建一个exe文件
	设置GOPATH/bin目录添加为系统path

	cd到proto文件目录下面，然后再编译：protoc --go_out=. *.proto




# proto2 proto3

	syntax = "proto3";			//proto3必须用这个起头
	proto3不用optional
	proto3 不支持 //中文注释在单行里面
