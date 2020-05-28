# 表的操作
    CREATE	创建一个新的表，表的视图，或者在数据库中的对象
    ALTER	修改现有的数据库对象，例如一个表
    DROP	删除整个表，数据库中的表或其他对象或视图

---

# 范式

	第一范式(1NF)：定义所需要的数据项，因为它们成为在表中的列。放在一个表中的相关的数据项。
	确保有数据没有重复的组。
	确保有一个主键。
	第二范式指出，它应满足所有1NF的规则，必须有任意列不依赖主键关系：
	表满足以下条件时就是第三范式：所有非主字段都是依赖于主键



---

# 通配符

	百分号 (%)	匹配一个或多个字符。需要注意的是MS Access使用星号(*)通配符代替百分号(%)通配符。
	下划线 (_)	匹配一个字符。请注意，MS Access使用一个问号(？)而不是下划线(_)来匹配任何一个字符。

---

# 设定

	SET ROWCOUNT @Count   使命令的处理在响应指定的行数之后停止处理命令, 可以用来做分页
	
	DECLARE： 定义变量，变量第一个字母是“@”
	SET：设置变量
	IF NOT EXISTS：如果不存在数据，执行BEGIN-END模块中的语句
	GO：批解释信号，告诉编辑器代码已结束。

	ISNULL(@xx, 0)	如果为NULL那么用0填充
	
	set @addr = '初始值'  变量赋值
	
	select @@identity	在插入结束之后把自增加的值返回
	select @@rowcount	结束之后把影响多少行返回
	
	SET NOCOUNT ON 不返回受影响的行数
	在pyodbc开发中，如果需要insert之后返回自增加的值， 那么exec前面要加上SET NOCOUNT ON， 这样才能返回这个返回值
	
	SET IDENTITY_INSERT dbo.UserDB ON   关闭自增加

---

# 字符类型

	CHAR，NCHAR 定长，速度快，占空间大，需处理
	VARCHAR，NVARCHAR，TEXT 不定长，空间小，速度慢，无需处理
	NCHAR、NVARCHAR、NTEXT处理Unicode码

# 字符串拼接

	concat('','')

---


# 字符转换

	CONVERT(VARCHAR(24),GETDATE(),113)   按照不同的编号格式比如113， 转换日期为字符串
	
	CAST(10.6496 AS int)
	select CAST(123.4 as int)   -- 123
	select CONVERT(int, 123.4)  -- 123 

---


# 创建表

	-- 判断要创建的表名是否存在 
	if exists(select * from dbo.sysobjects where id = object_id(N'dbo.AaWhiteIPList') 
		print 'exists'
	else
		begin
			create table AaWhiteIPList(
				ip varchar(15) not null default '',
				comments varchar(100) null
		end

	
# select

	DISTINCT 	去重
	as 			别名用法
	TOP(1)		返回最上面的一行数据
	count(*)	返回行数
	select * from dbo.accounts where UserID like %zsw%   查找包含zsw字段的
	select id=identity(int,1,1) ,name into #regtemp11 from table(nolock)	copy表到临时表，并新增一列列名为id的自增加列

 
# order by

	排序 
	desc 倒序

# update

	update dbo.gamestoreinfo set androidcount = '40',pay='1' where uid = '2003'   更新数据

# insert

	insert into dbo.AaWhiteIPList (ip,comments) values ('127.0.0.1','')

# delete

	DELETE FROM runoob_tbl WHERE runoob_id=3;





# 存储过程和函数

	区别很小， 存储过程可以返回多个参数， 函数限制比较多
	Alter procedure dbo.GetWhiteList
	as
	begin
		...
	end



# 存在就更新，不存在就插入，经常用于更新游戏房间的状态

   if not exists (select 1 from t where id = 1)
      insert into t(id, update_time) values(1, getdate())
   else
      update t set update_time = getdate() where id = 1
