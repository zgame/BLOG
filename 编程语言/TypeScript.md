# 特点

	强类型语法， Angular指定的开发语言


# 语法

	typeScript是javaScript的超集， 强类型

	let decLiteral: number = 6;     // 变量定义

	变量作用域， var比较宽松，整个函数作用域，容易形成bug， let比较严格，代码块作用域。

	

# 字符串

	${ expr }		//格式化字符串，用于输出


# 数组

	let list: number[] = [1, 2, 3];
	let list: Array<number> = [1, 2, 3];

# 元组

	let x: [string, number];


# 枚举

	enum Color {Red, Green, Blue}

# 任意值

	let notSure: any = 4;
	void类型像是与any类型相反，它表示没有任何类型
	never类型表示的是那些永不存在的值的类型

# 常量

	const numLivesForCat = 9;