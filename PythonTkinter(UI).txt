------------------------python UI开发 tkinter---------------------------------------------------

参考文档
http://effbot.org/tkinterbook/
https://blog.csdn.net/wuxiushu/article/details/52516652


--------------------------------------------------------------------------------------------------

# coding=utf-8
from Tkinter import *
root = Tk()

# -----添加label---------------------------------------------------------
labelHello = tk.Label(top, text = "label...", height = 5, width = 20, fg = "blue").pack()


#-----添加list列表---------------------------------------------


movie = ['CSS', 'jQuery', 'Bootstrap']
listb2 = Listbox(root, listvariable=StringVar(value=list_a))
	# selectmode有单选，多选，可以移动，支持shift和ctr键
listb2 .bind("<Double-Button-1>", callback)		
# 这是listbox绑定鼠标左键双击事件， callback是回调函数，要特别注意，不能使用单击，一定要双击才可以等于确定
 def printcurList(event):
        print(list_all.curselection()[0])	# 注意这里的event要有


# 从后面开始添加，因为是队列，所以正好前面的在上面
# 另外一种不用for循环的方式，就是上面的例子listvariable=StringVar(value=list_a)
for item in movie:
    listb2.insert(END, item)			




listb2.pack()

# -----给list配合scroll---------------------------------------------------------
  sl = Scrollbar(root)						#定义scroll
    sl.config(command=listb.yview)			# 设置跟list的关系
    sl.grid(row=1, column=2, sticky=W+N+S)		# 定义位置，还有关键的sticky  W是左侧对其，N+S是垂直方向拉长
listb.config(yscrollcommand=sl.set)


#------添加button和自定义事件，如果需要参数用匿名函数即可，看下面例子----------------------------------
def callback():
	print 'callback'
quit = Button(root, text='Quit',  command=callback).pack()

# ---Menubutton	菜单按钮和事件返回带参数--------------------------------------------------
    def menu_button_fuc(index):
        mbutton.config(text=list1[int(index)])			# 把当前选择的按钮名字显示出来

    mbutton = Menubutton(root, text='Food', relief=RAISED)		# 定义
    picks = Menu(mbutton)					# 子按钮
    mbutton.config(menu=picks)
    mbutton.grid(row=8, column=1)				#位置
    list1 = ["a", "b", "c"]
    for (index,value) in enumerate(list1):			# 添加列表元素
        picks.add_command(label=value, command=lambda index=index: menu_button_fuc(index))   



# ---Message：----------
Message(root, text=str(input1.get())).grid(row=6, column=0)
显示一文本。类似label窗口部件，但是能够自动地调整文本到给定的宽度或比率。

#--------messagebox提示框-----------------------------------
import tkinter.messagebox as msgbox	#注意这个要单独import进来才可以
msgbox.showinfo('Message', '恭喜！')		(Python2中为tkMessagebox)


#-------grid网格化排版---------------------------------------------------

注意：如果使用grid的话， 就不能使用pack了
b1.grid(row=3,column=4, padx=10, pady=10)	放在第三行，第四列
mm1.grid(row=0,column=1)		放在第0行，第一列

grid(row=0,column=1,columnspan=4, sticky=W+E+N+S)	夸了3列， 一个横向很宽的控件，后面是对齐方式，带拉伸

#---------Menu菜单栏添加--------------------------
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
# --------文件选择框--------------------------------------------
import tkinter.filedialog as fd
	my_file_types = [('Python files', '*.py'), ('All files', '*')]
        open1 = fd.Open(root, filetypes=my_file_types)
        str1 = open1.show()			#这里就是输出文件的全路径
        Message(root, text=str1).grid(row=7, column=0)

#---------spinbox输入框--------------------------
input1 = Spinbox(root, from_=0, to=100)    只能输入0-100的数字
input1 = Spinbox(values=(1, 2, 4, 8))      只能在这几个数字之间跳转
input1.get()			通过get来获取值，这个值可以是任意的数字
#-------------Entry文本输入框---------------------------------------------------------------
input2 = Entry(root)
input2.get()				通过get来获取文本，可以变成密码，支持验证，变成只读
#----------------------------------------------------------------------------
root.mainloop()
