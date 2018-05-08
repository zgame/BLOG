# 学用if语句：

	=IF(OR(B2="",B2=" "),$AA$8,IF(B2="○",$AA$7, IF(B2="△",$AA$9,IF(B2="X",$AA$10))))
	注释：
	or（条件1，条件2）
	if（条件1，符合，不符合）
	嵌套if（条件1，符合，if（条件2，符合，不符合））

# 技巧

	点击公式格子的右下角可以拖拽复制
	如果采用固定引用，那么采用$bb$10的格式
	如果是公式计算出来的数值，那么copy到文本里面，然后再copy回去，就成最后的数值了



# 获取随机整数范围
	
	=RANDBETWEEN(0,31)


# 锁定某些数据不让人修改

	右键选择所有单元格解除锁定， 然后选择要锁定的格子，选择锁定
	然后“审阅”-》“保护工作表”，只勾选未锁定的单元格，然后设置密码就可以了


# 引用别的表的数据

	=工作表1!a1
	注释：工作表后面接!即可引用该工作表的数据了


# 如何查找对应数据

	=vlookup("c",a2:b6,2,true)
	注释：
	查找a2到b6范围内的数据 ，有符合“c”的，返回符合条件行的第2列数据，
	false是完全匹配
	注意， 如果是匹配字符串的话， 一定要匹配的原始表，第一列是字符串

---

	CONCATENATE(TEXT(A4,"0"),"S") 合并字符串， 把数字转换成字符
	ROW()返回当前行号
	MOD(4，2) = 0 余数
	QUOTIENT(4,2) = 2  商的整数
	MID(text,start_num,num_chars)  截取字符串
	replace(old, startnum, num_chars, new_text)


---

	=IF(MOD(ROW(),2)=1,CONCATENATE(vlookup(QUOTIENT(ROW(),2),a2:b129,1,true),vlookup(QUOTIENT(ROW(),2),a2:b129,2,true),"|普通攻击"),CONCATENATE(vlookup(QUOTIENT(ROW(),2),a2:b129,1,true),vlookup(QUOTIENT(ROW(),2),a2:b129,2,true),"|技能攻击"))
	
	
	=IF(MOD(ROW(),2)=1,CONCATENATE("AQUOTIENT(ROW(),2)",B$(QUOTIENT(ROW(),2),"|普通攻击"),CONCATENATE(A2,B2,"|技能"))
	
	
	//下面是如果查到就查到，查不到用0
	=IF(ISERROR(VLOOKUP(A2,Sheet4!$A$1:$B$996,2,FALSE)),0,VLOOKUP(A2,Sheet4!$A$1:$B$996,2,FALSE))

