------------------------python UI���� tkinter---------------------------------------------------

�ο��ĵ�
http://effbot.org/tkinterbook/
https://blog.csdn.net/wuxiushu/article/details/52516652


--------------------------------------------------------------------------------------------------

# coding=utf-8
from Tkinter import *
root = Tk()

# -----���label---------------------------------------------------------
labelHello = tk.Label(top, text = "label...", height = 5, width = 20, fg = "blue").pack()


#-----���list�б�---------------------------------------------


movie = ['CSS', 'jQuery', 'Bootstrap']
listb2 = Listbox(root, listvariable=StringVar(value=list_a))
	# selectmode�е�ѡ����ѡ�������ƶ���֧��shift��ctr��
listb2 .bind("<Double-Button-1>", callback)		
# ����listbox��������˫���¼��� callback�ǻص�������Ҫ�ر�ע�⣬����ʹ�õ�����һ��Ҫ˫���ſ��Ե���ȷ��
 def printcurList(event):
        print(list_all.curselection()[0])	# ע�������eventҪ��


# �Ӻ��濪ʼ��ӣ���Ϊ�Ƕ��У���������ǰ���������
# ����һ�ֲ���forѭ���ķ�ʽ���������������listvariable=StringVar(value=list_a)
for item in movie:
    listb2.insert(END, item)			




listb2.pack()

# -----��list���scroll---------------------------------------------------------
  sl = Scrollbar(root)						#����scroll
    sl.config(command=listb.yview)			# ���ø�list�Ĺ�ϵ
    sl.grid(row=1, column=2, sticky=W+N+S)		# ����λ�ã����йؼ���sticky  W�������䣬N+S�Ǵ�ֱ��������
listb.config(yscrollcommand=sl.set)


#------���button���Զ����¼��������Ҫ�����������������ɣ�����������----------------------------------
def callback():
	print 'callback'
quit = Button(root, text='Quit',  command=callback).pack()

# ---Menubutton	�˵���ť���¼����ش�����--------------------------------------------------
    def menu_button_fuc(index):
        mbutton.config(text=list1[int(index)])			# �ѵ�ǰѡ��İ�ť������ʾ����

    mbutton = Menubutton(root, text='Food', relief=RAISED)		# ����
    picks = Menu(mbutton)					# �Ӱ�ť
    mbutton.config(menu=picks)
    mbutton.grid(row=8, column=1)				#λ��
    list1 = ["a", "b", "c"]
    for (index,value) in enumerate(list1):			# ����б�Ԫ��
        picks.add_command(label=value, command=lambda index=index: menu_button_fuc(index))   



# ---Message��----------
Message(root, text=str(input1.get())).grid(row=6, column=0)
��ʾһ�ı�������label���ڲ����������ܹ��Զ��ص����ı��������Ŀ�Ȼ���ʡ�

#--------messagebox��ʾ��-----------------------------------
import tkinter.messagebox as msgbox	#ע�����Ҫ����import�����ſ���
msgbox.showinfo('Message', '��ϲ��')		(Python2��ΪtkMessagebox)


#-------grid�����Ű�---------------------------------------------------

ע�⣺���ʹ��grid�Ļ��� �Ͳ���ʹ��pack��
b1.grid(row=3,column=4, padx=10, pady=10)	���ڵ����У�������
mm1.grid(row=0,column=1)		���ڵ�0�У���һ��

grid(row=0,column=1,columnspan=4, sticky=W+E+N+S)	����3�У� һ������ܿ�Ŀؼ��������Ƕ��뷽ʽ��������

#---------Menu�˵������--------------------------
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
# --------�ļ�ѡ���--------------------------------------------
import tkinter.filedialog as fd
	my_file_types = [('Python files', '*.py'), ('All files', '*')]
        open1 = fd.Open(root, filetypes=my_file_types)
        str1 = open1.show()			#�����������ļ���ȫ·��
        Message(root, text=str1).grid(row=7, column=0)

#---------spinbox�����--------------------------
input1 = Spinbox(root, from_=0, to=100)    ֻ������0-100������
input1 = Spinbox(values=(1, 2, 4, 8))      ֻ�����⼸������֮����ת
input1.get()			ͨ��get����ȡֵ�����ֵ���������������
#-------------Entry�ı������---------------------------------------------------------------
input2 = Entry(root)
input2.get()				ͨ��get����ȡ�ı������Ա�����룬֧����֤�����ֻ��
#----------------------------------------------------------------------------
root.mainloop()
