#python UI开发 tkinter的试用

----------

**参考文档**

[http://effbot.org/tkinterbook/](http://effbot.org/tkinterbook/)


----------


    # coding=utf-8
    from Tkinter import *
    root = Tk()

# 添加label

    labelHello = tk.Label(top, text = "label...", height = 5, width = 20, fg = "blue").pack()



# 添加list列表

    movie = ['CSS', 'jQuery', 'Bootstrap']
    listb2 = Listbox(root, listvariable=StringVar(value=list_a))    	

<font color=#A52A2A size=2>SELECTMODE有单选，多选，可以移动，支持SHIFT和CTR键</font>

    listb2 .bind("<Double-Button-1>", callback)		
    def printcurList(event):
    	print(list_all.curselection()[0])		# 注意这里的event要有

<font color=#A52A2A size=2>这是listbox绑定鼠标左键双击事件， callback是回调函数，要特别注意，不能使用单击，一定要双击才可以等于确定</font>

    # 从后面开始添加，因为是队列，所以正好前面的在上面
    # 另外一种不用for循环的方式，就是上面的例子listvariable=StringVar(value=list_a)
    for item in movie:
    	listb2.insert(END, item)			
    listb2.pack()

# 给list配合scroll
    sl = Scrollbar(root)						# 定义scroll
    sl.config(command=listb.yview)				# 设置跟list的关系
    sl.grid(row=1, column=2, sticky=W+N+S)		# 定义位置，还有关键的sticky  W是左侧对其，N+S是垂直方向拉长
    listb.config(yscrollcommand=sl.set)			# 定义scroll跟list的反馈


# 添加button和自定义事件，如果需要参数用匿名函数即可，看下面例子
    def callback():
    	print 'callback'
    quit = Button(root, text='Quit',  command=callback).pack()

# Menubutton	菜单按钮和事件返回带参数
    def menu_button_fuc(index):
    	mbutton.config(text=list1[int(index)])					# 把当前选择的按钮名字显示出来
    
    mbutton = Menubutton(root, text='Food', relief=RAISED)		# 定义
    picks = Menu(mbutton)										# 子按钮
    mbutton.config(menu=picks)
    mbutton.grid(row=8, column=1)								# 定义位置
    list1 = ["a", "b", "c"]
    for (index,value) in enumerate(list1):						# 添加列表元素
    	picks.add_command(label=value, command=lambda value=value: menu_button_fuc(index))   


<font color=#A52A2A size=2>绑定菜单按钮的事件，并通过匿名函数返回参数，这里需要比较注意一点，绑定的匿名函数不能用index，因为删除掉一个按钮之后，index会变化， 导致绑定事件的变化， 所以，每删掉一个menubutton，都要把后面的重置一下index，因为index变了
</font>

# Message：
    Message(root, text=str(input1.get())).grid(row=6, column=0)
<font color=#A52A2A size=2>显示一文本。类似label窗口部件，但是能够自动地调整文本到给定的宽度或比率。</font>

# messagebox提示框
    import tkinter.messagebox as msgbox					# 注意这个要单独import进来才可以
    msgbox.showinfo('Message', '恭喜！')				  # Python2中为tkMessagebox


# grid网格化排版

<font color=#A52A2A size=2>注意：如果使用grid的话， 就不能使用pack了</font>

    b1.grid(row=3,column=4, padx=10, pady=10)		# 放在第三行，第四列
    mm1.grid(row=0,column=1)						# 放在第0行，第一列
    grid(row=0,column=1,columnspan=4, sticky=W+E+N+S)	# 跨了3列， 一个横向很宽的控件，后面是对齐方式，带拉伸

# Menu菜单栏添加
    def hello():
        print("hello!")

    # create a pulldown menu, and add it to the menu bar
    filemenu = Menu(menubar, tearoff=0)
    filemenu.add_command(label="Open", command=hello)
    filemenu.add_command(label="Save", command=hello)
    filemenu.add_separator()
    filemenu.add_command(label="Exit", command=root.quit)
    menubar.add_cascade(label="File", menu=filemenu)

    # create more pulldown menus
    editmenu = Menu(menubar, tearoff=0)
    editmenu.add_command(label="Cut", command=hello)
    editmenu.add_command(label="Copy", command=hello)
    editmenu.add_command(label="Paste", command=hello)
    menubar.add_cascade(label="Edit", menu=editmenu)

    helpmenu = Menu(menubar, tearoff=0)
    helpmenu.add_command(label="About", command=hello)
    menubar.add_cascade(label="Help", menu=helpmenu)

    # display the menu
    root.config(menu=menubar)
# 文件选择框
    import tkinter.filedialog as fd
    my_file_types = [('Python files', '*.py'), ('All files', '*')]
    open1 = fd.Open(root, filetypes=my_file_types)
    str1 = open1.show()								#这里就是输出文件的全路径
    Message(root, text=str1).grid(row=7, column=0)

# spinbox输入框
    input1 = Spinbox(root, from_=0, to=100)		# 只能输入0-100的数字
    input1 = Spinbox(values=(1, 2, 4, 8))  		# 只能在这几个数字之间跳转
    input1.get()								# 通过get来获取值，这个值可以是任意的数字
	# python2 ：input.get().encode("utf-8")   python3: input:get()
	input1.insert(0, 50)		# 设置初始值
	input1.delete(0,END)		# 清空输入框
	
# Entry文本输入框
    input2 = Entry(root)
    input2.get()				# 通过get来获取文本，可以变成密码，支持验证，变成只读
	# python2 ：input.get().encode("utf-8")   python3: input:get()
	input1.insert(0,"sss")		# 设置初始值
	input1.delete(0,END)		# 清空输入框

# Frame排版

	frame = Frame(root)
	frame.grid(row=0,column=1,columnspan=4, sticky=W+E+N+S)
	# 其他的控件绑定到frame上面， 界面就很固定了


# 最后mainloop
    root.mainloop()
