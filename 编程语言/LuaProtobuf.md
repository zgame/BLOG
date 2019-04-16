# lua protobuf protoc-gen-lua

	pb.c
	pb.go	//自己写的

# 概念

	用c或者go，写module，然后注册到lua中，让lua可以调用c或者go的函数

# 主要流程文件

	protobuf.lua
	encoder.lua
	decoder.lua
	pb.go


# 为了调试方便，增加一个显示byte数组的函数

	C++版本

	static int ZswShowLuaBuffer(lua_State *L)
	{
	    size_t len;
	    const char* buffer = luaL_checklstring(L, 1, &len);
	    int i=0;
	    for(i=0;i<len;i++)
	    {
	        printf("--------read_tag-----****[[[[[[ZswShowLuaBuffer]]]]]]]*****************------out----%x   \n",buffer[i]);
	    }
	}


	Go 版本
	func ZswLuaShowBytesToString(L *lua.LState) int  {
		str := L.ToString(1)
	
		fmt.Printf("*******************************************************************************ZswLuaShowBytesToString: %v \n", []byte(str))
		return 0
	}
	

# go protobuf生成byte数组

	************************ok******************
	注意上下限-2147483648 through 2147483647.
	int32 zswnameb = 1;		// proto file
	Zswnameb:1,			    // byte数组为 [8 1] 
	Zswnameb:23333,			// byte数组为 [8 165 182 1]
	Zswnameb:189,			// byte数组为 [8 189 1]
	Zswnameb:-1,			// [8 255 255 255 255 255 255 255 255 255 1]
	Zswnameb:-189,			//[8 195 254 255 255 255 255 255 255 255 1]
	Zswnameb = -2147483648  //[8 128 128 128 128 248 255 255 255 255 1]
	**********************OK********************
	uint32 zswnameb = 4294967295;   
	**********************OK********************
	bool zswnameb = true;   // [16 1]   
	bool zswnameb = false;  // [16 0]   
	*********************OK*********************
	float zswnameb = 1.0;   // [29 0 0 128 63]
	float zswnameb = -1.0;   // [29 0 0 128 191]
	float zswnameb = -9911.36;   // [29 113 221 26 198]
	*********************ok*********************
	double zswnameb =  55  // [9 0 0 0 0 0 128 75 64]
	*********************ok*********************
	一定要注意上下限 -562949953421312 through  562949953421312
	int64 zswnameb =  562949953421312
	int64 zswnameb =  -562949953421312
	*********************ok*********************
	一定要注意上限 1125899906842624
	uint64 zswnameb =  1125899906842624
	*********************ok*********************
	string ad5 = 8;		//person.ad5 = "sdf中文测试"
	sint32 ad6 = 9;			//person.ad6 = -2147483647
	sint64 ad7 = 10;		//person.ad7 = 562949953421312
	fixed32 ad8 = 11;		//person.ad8 = 2147483647
	fixed64 ad9 = 12;		//person.ad9 = 562949953421312
	bytes ad10 = 13;		//person.ad10 = string.char(112,113,114,115)
	
	
# proto 3
	
	不需要required optional


# repeated 用法

	-- 如果repeated是一个结构体
	local zzz = person.zz:add()
	zzz.name = "sdfsd这是"
	zzz.id = 21343

	-- 如果repeated是一个数字
	person.zz:append(123)

	
	
	

# go的数值上限，跟lua版本略有不同

	// int8 Range: -128 through 127.
	// int16  Range: -32768 through 32767.
	// int32 Range: -2147483648 through 2147483647.
	// int64 Range: -9223372036854775808 through 9223372036854775807.

	// uint8 Range: 0 through 255.
	// uint16 Range: 0 through 65535.
	// uint32 Range: 0 through 4294967295.
	// uint64 Range: 0 through 18446744073709551615.
	
	// float32 (float)   IEEE-754 32-bit floating-point numbers.
	// float64 (double)  IEEE-754 64-bit floating-point numbers.



# protobuf数据类型


	int32使用可变长编码方式。编码负数时不够高效——如果你的字段可能含有负数，那么请使用sint32。
	int64使用可变长编码方式。编码负数时不够高效——如果你的字段可能含有负数，那么请使用sint64。
	uint32
	uint64
	sint32使用可变长编码方式。有符号的整型值。编码时比通常的int32高效。
	sint64使用可变长编码方式。有符号的整型值。编码时比通常的int64高效。
	fixed32总是4个字节。如果数值总是比总是比228大的话，这个类型会比uint32高效。
	fixed64总是8个字节。如果数值总是比总是比256大的话，这个类型会比uint64高效。
	sfixed32总是4个字节。
	sfixed64总是8个字节。
	bool 
	string一个字符串必须是UTF-8编码或者7-bit ASCII编码的文本。
	bytes可能包含任意顺序的字节数据。