# lua protobuf protoc-gen-lua

	pb.c
	pb.go	//自己写的

# 概念

	用c或者go，写module，然后注册到lua中，让lua可以调用c或者go的函数

# 主要流程文件

	protobuf.lua
	encoder.lua
	decoder.lua


# 为了调试方便，增加一个显示byte数组的函数

	C++

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


	Go
	func ZswLuaShowBytesToString(L *lua.LState) int  {
		str := L.ToString(1)
	
		fmt.Printf("*******************************************************************************ZswLuaShowBytesToString: %v \n", []byte(str))
		return 0
	}
	

# go protobuf生成byte数组

	************************ok******************
	int32 zswnameb = 1;		// proto file
	Zswnameb:1,			    // byte数组为 [8 1] 
	Zswnameb:23333,			// byte数组为 [8 165 182 1]
	Zswnameb:189,			// byte数组为 [8 189 1]
	Zswnameb:-1,			// [8 255 255 255 255 255 255 255 255 255 1]
	Zswnameb:-189,			//[8 195 254 255 255 255 255 255 255 255 1]
	Zswnameb = -2147483648  //[8 128 128 128 128 248 255 255 255 255 1]
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
	double zswnameb =  55  // [9 0 0 0 0 0 128 75 64]
	

	














	string zswnameb2 = 2;	 // proto file
	Zswnameb2:"1",			// byte数组为 [18 1 49]


# protoc-gen-lua c 生成byte数组

	要注意，protoc-gen-lua c生成的跟go显示的不一样的 
	Zswnameb:189,			// byte数组为 [8 67 1]
	
	


# 上限

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



