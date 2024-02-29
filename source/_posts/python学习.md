---
title: python学习
date: 2024-02-08 12:11:12
tags: [python]
categories: 学习笔记
---

# python基础

## 1.字面量

>写在代码里固定的值

1. 数字

2. 字符串

3. 列表 （list)

   >有序的可变序列 

4. 元组(tuple)

   >有序的不可变的python数据集合

5. 集合(set)

   >无序不重复集合

6. 字典（dictionary)

   >无序 key-value集合

```python
mylist=[1,2,3]
# 列表while进行循环
index =0
while index<len(mylist):
    a = mylist[index]
    index += 1
# 列表for进行循环
for i in mylist:
    a = mylist[i]
```



## 2.注释

```python
# #号表示单行注释 一般#号后面空格在写注释

"""
三个双引号
表示多行注释
"""
```

## 3.变量

>能存储计算结果或表示值的抽象概念
>
>变量没有类型  变量存储的数据是有类型的

```python
# 定义一个变量 记录 钱包余额
money = 50

# 通过print语句，输出变量记录内容
# java用+ python用逗号会有空格 也可以用加号
print("钱包还有" , 50)

# 买了一个冰淇淋，花费十元
money = money -10
print("买了冰淇淋花费10元，还剩余：",money,"元") 
```

### 查看数据类型

```python
123
# 用变量接受123的类型 int
int_type =type(123)
```

### 数据转换类型

```python
# 将数字转换成字符串
num_str = str(11)
print(type(num_str),num_str)

# 将字符串转换成数字
num = int("11")
print(type(num),num)
nun = flat("11.8")

```

## 4.标识符

>变量的名字 方法的名字 类的名字
>
>用户在编程所使用的一系列的名字

命名规则：

1. 只能用英文，数字，下划线，不能以数字开头！！
2. 大小写敏感 （java也区分大小写）
3. 不可使用关键字

命名规范：

1. python多个单词之间用下划线
2. java用驼峰

## 5.运算符

1. 整除为 //
2. 指数为 **
3. 取模为 %=

## 6.字符串的三种定义

```python
# 单引号定义法
name = '单引号定义'

# 双引号定义法
name = "双引号定义"

# 三引号定义法
# 不用变量接收的话 三个引号代表注释
name = """三引号定义"""
```

## 7.字符串格式化

>字符串拼接是不能直接拼接非字符串的变量，如数字
>
>这时候就需要字符串格式化
>
>1. %s 字符串
>2. %d 整数
>3. %f  浮点数

```python
name = "zjaaa"
message = "学习Python的是： %s"  %name
#  如果有多个变量占位
id = 1
message = "我是%s,我在学习目前排名第%s的python" %(name,id)
```

### 可以用辅助符号m.n控制数据宽度和精度

```python
# 如果假如数字为11 因为宽度设成了5.所以得前面补三个空格
%5d
# 表述宽度为7，精度为2 假设数字为11.345
%7.2f
# 格式化的数字为 【空格】【空格】11.35

#也可以只设置精度 假如数字为11.342
%.1f
# 数字为11.3
```

### 字符串格式化方法2

```python
name = "zjaaaa"
date = "2024-02-08"
# f:format 格式化标记
print(f"我是{name},今天是{date},我正在学习python")
```

### 表达式格式化

>表达式: 1.有具体结果 2.代码片段

```python
print("1*1 的结果是: %d" %(1*1))

print(f"1*2的结果是：{1*2}")
```

## 8.数据输入

```python
name = input("请告诉我你是谁？")
print("我知道了，你是: %s"%name)
```

>input 默认接收到的是字符串 
>
>想要别的类型记得转换一下！

## 9.布尔类型以及比较运算符

```python
# python的True以及False都要大写

## 比较运算符 
num1 =10
num2 =15
print(f"num1 == num2 的结果为{num1 == num2}")
print(f"num1 > num2的结果为{num1>num2}")

# if 条件语句后面有冒号 
# 条件成立前面有四个空格
# else也要顶格写 后面有冒号！
if age >= 18:
    print('我已经成年了')
else:
    print("我还没成年")

# elif为条件判断
height =int(input("请输入你的身高：(cm)"))
vip_level = int(input("请输入你的vip等级(1-5)"))

if height<120:
    print("身高小于120cm，可以免费游玩")
elif vip_lever >3:
    print("vip级别大于3，可以免费游玩")
else:
    print('不好意思，条件都不满足，需要买票10元')
    
#简单的一个猜数字游戏
num = 5
if int(input("请输入一个数字")) ==num:
    print("恭喜你第一次就猜对了")
elif int(input("猜错了，请再猜一次")) ==num:
    print("猜对了")
elif int(input("猜错了，最后再猜一次")) ==num:
    print("恭喜你最后一次机会猜对了")
else:
    print("sorry,三次机会都没有猜对")
```

## 10. while循环

```python
i =0;
while i<100:
    print(f"我在学习python第{i+1}遍")
    i+=1
```

### while嵌套循环

```python
# 给定一个条件 向小美表白100天 每天送十朵玫瑰花 
i = 1
while i<=100:
    print("今天是第%s天,准备表白..."%i)
    j =1
    while j<=10:       
        print('送给小美第%s朵花'%j)
        j += 1
    print('小美，我喜欢你')
    i+=1
print(f"坚持到第{i-1}天，表白成功！")                   
```

## 11. for 循环

```python
name ='zjaaa'
for x in name:
    print(x)
```

### range序列

>一般用于搭配for循环使用

```python
# 语法1 range(num) 
range(10) #num为10 取0-9 
# 语法2 range(num1,num2)
range(1,100) # 取1-99
# 语法3 range(num1,num2,step)
range(1,10,2) # 取 1 3 5 7 9

# 搭配for循环使用
for x in range(10):
    print(x)
```

### continue

跳过本次循环

### break

终止循环

### 循环发工资小案例

```python
import random

jiangjin=10000
for i in range(1,21):
    if jiangjin == 0:
        break;
    else:
    jixiao=random.randint(1,10)
    if jixiao<5:
        print(f"员工i，绩效分{jixiao},不发工资，下一位")
        continue
    else:
        jiangjin=jiangjin-1000
        print(f"向员工{i}发放工资1000元,奖金还剩{jiangjin}元")
```

## 12.函数

```python
#函数定义
"""
def 函数名(传入参数):
    函数体
    return 返回值
"""
# 如果函数没返回值则返回none none为假
def add(x,y):
    """
    Add two numbers
    :param x: 
    :param y: 
    :return: 
    """
    return x+y
```

## 13. list列表

列表可以倒着索引 右边第一个索引为-1 

1. 可以容纳多个元素
2. 数据是有序存储的
3. 允许重复数据存在
4. 可以修改
5. 可以容纳不同类型元素

### list常用方法

>定义在class里面的称为方法   定义在外面的称为函数

 ```python
 mylist = ["java","python","c"]
 mylist = list
 # 查找元素在列表内的下标索引
 index =mylist.index("java") # index==0
 # 修改下标索引值
 mylist[2] = "php"
 # 在指定位置插入新元素
 mylist.insert(1,"best")
 # 在尾部添加元素
 mylist.append("c#")
 # 在列表尾部添加一批新元素
 mylist2 = [1,2,3]
 mylist.extend(mylist2)
 # 删除指定索引的元素 (第一种)
 mylist.del(2)
 # 删除指定索引的元素， 这种能接受到返回值
 element =mylist.pop(2)
 # 删除某元素在列表的第一个匹配项
 mylist.remove("java")
 # 清空列表
 mylist.clear()
 # 统计列表某元素的数量
 count = mylist.count("java")
 # 统计列表的全部元素数量
 count = len(mylist)
 ```

## 14.元组

>有序，任意数量元素，允许重复元数，不可修改

```python
# 定义元组
mytuple = tuple
mytuple = ()
mytuple=(1,2,3)

#定义单个元素的元组 需要有逗号！！
mytuple=(1,)
# 元组的嵌套
mutuple = ((1,2,3),(1,2,3))

#元组的操作
mytuple = (1,2,3)
# 查找元素索引
index = mytuple.indxe(1)
# 查找某个元素在元组里的数量
num = mutuple.count(2)
# 统计元组元素的数量
num =len(mytuple)

# 遍历元组
# while循环
index = 0
while index < len(mytuple):
    a = mytuple[index]
# for循环
for i in mytuple:
    a = mytuple[i]
```

## 15.字符串

>只可以存储字符串 长度任意 支持下标索引 不可以修改

```python
my_str ="hello world"
# 通过下标索引取值
value = my_str[0]
value = my_str[-1]
# 查找元素索引
my_str.index("world")
# 字符串的替换 替换次数参数（不加则为全部替换
new_my_str =my_str.replace("world","zjaaa"，1)
# split方法 有两个参数 第一个参数分隔符 第二个参数分割几次 -1 或者不填都默认分割到不能再分
my_str = "hello python java c++"
new_str_list = my_str.split(" ",2)
# strip方法
# 不传参数 去除首尾空格
my_str = " hello "
new_mystr = my_str.strip()
# 传参数 去除首位指定参数 传的参数 按每个字符进行比对
my_str="12hello21"
new_mystr=my_str.strip("12")
# 统计字符串在字符串的出现次数
count =my_str.count("hello")
# 统计字符串的长度
num = len(my_str)
```

## 16.序列切片

列表，元组，字符串都是序列

```python
# 语法 序列[起始索引：结束索引：步长] 步长为负数表示反向取
my_list = [0,1,2,3,4,5,6]
result = my_list[1:4] # 得到结果 [1,2,3]
my_list[::-1]# 倒着取
```

## 17. set集合

>可以容纳多个数据
>
>可以容纳不同类型数据
>
>数据是无序存储的
>
>不允许重复数据存在
>
>可以修改
>
>支持for循环

```python
# 定义集合
my_set = set()
my_set ={1,2,3}

# 集合方法
# 添加新元素
my_set.add("python")
# 移除新元素
my_set.remove("python")
# 随机删除一个元素并取出
value = my_set.pop()
# 清空集合
my_set.clear()
# 取两个集合的差集 调用者有的,被调用者没的 
set1={1,2,3}
set2={1,5,6}
set3 = set1.difference(set2) # set3结果为{2,3}
# 消除两个集合相同的元素
set1 ={1,2,3}
set2={1,5,6}
set1.difference_update(set2) # set1结果 {2,3}
# 两个集合合并
set3 =set1.union(set2) #结果去重合并
# 统计集合元素数量
num = len(set1)
# 集合的遍历
# 集合不支持下标索引，不能用while循环
# 可以用for循环
for i in set1:
    a = i
```

## 18.字典

>注意的是 字典是无序的 取出来想排序记得对keys做sort

```python
# 定义字典
my_dict= {"王丽"：99,"周杰"：88，"林俊":77}
# 定义空字典
my_dict ={}
my_dict = dict()
# 从字典中基于key获取value
score = my_dict["王丽"]
# 新字典
my_dict["张鑫"] =66
# 添加 或 更新元素
my_dcit["周杰"] = 33
# 删除元素
score = my_dict.pop("周杰")
# 清空元素
my_dict.clear()
# 获取全部的key
keys = my_dict.keys
# 遍历字典
for key in keys:
    print(f"key为{key}")
    print(f"value为{value}")
# for循环
for key in my_dict:
    print(f"key为{key}")
    print(f"value为{value}")
# 统计字典元素数量
num =len(my_dict)
```

## 19.容器通用方法

```python
# len元素个数
len(list)
# max最大元素
max(list)
# 容器转列表
list(mylist)
# 容器转元组
tuple(mytuple)
# 容器转字符串
str(mystr)
# 容易转集合
set(myset)
# 进行容器的排序
# 不加reverse升序排列
# 加reverse True表示降序排
sorted_list = sorted(mylist，reverse=False) 
# mylist.sort(key=,reverse=)
# 有两个参数 key 要求传入函数 一般直接用lambda
# reverse True降序 False 升序
# 没有返回值 直接改变
mylist,sort(key =lambda element: element[1],reverse = True)
# 如果要反转排序
sorted(mylist,reverse=True)
```

## 20.函数进阶

```python
# 函数返回多个返回值
def test_return():
    return 1,2,3

x,y,z = test_reeturn()
print(x)
print(y)
print(z)

# 函数传参方式
def user_info(name,age,gender):
    print(f"姓名是{name},年龄是{age},性别是{女}")
# 位置参数
user_info("小明",20,"男")
# 关键字参数
user_info(name="小王"，geder="女”,age="18")
# 缺省参数
def user_info(name,age,gender="女 "):
    print(f"姓名是{name},年龄是{age},性别是{女}")
          
# 可变参数
def user_info(*args):
          print(args)
user_info(1,2,3)
def user_info(**kwags):
          print(kwags)
user_info(name='小王',age=11,gender='男孩')
# 函数作为参数传递
def test_func(compute):
          result= compute(1,2)
          print(result)
# lambda 
test_func(lambda x,y:x+y)          
```

## 21.文件

### 1.打开文件

```python
open(name,mode,encoding)
# name打开目标文件名的字符串
# mode设置打开文件的模式
#只读r 
#写入w 文件存在 ，原有内容删除。更新文件内容 文件不存在 创造文件 
#追加a 文件存在，追加内容 文件不存在 创造文件
# encoding编码格式 这个是关键字传参 encoding=
open("D:/测试.txt","r",encoding="utf-8")
```

### 2.读入文件

```python
f = open("D:/测试.txt","r",encoding="utf-8")
f.read(参数为字符数，不带参数则表示读全部)
# 读取全部行
f.readlines()
# 读取一行
f.readline()
# for循环读取文件行
for line in f:
    print(line)
f.close()
# with open语法操作文件 执行完代码块会自动调用close方法
with open("D:/测试.txt","r",encoding="utf-8") as f:
    for line in f:
        print(line)
```

```python
#打开文件 以读取模式打开
f = open("D:/word.txt","r",encoding="utf-8")
count =0
for line in f:
    #去除开头和结尾的空格以及换行符
    line =line.strip()
    words = line.split(" ")
    for word in words:
        if word == "hello":
            count+=1
print(f"出现的次数为{count}")
f.close()
```

### 3.写入文件

```python
#写入文件是先写入内存 最后写入硬盘
#如果想及时进硬盘 应该用flush()方法
f = open("G:/test.txt","w",encoding="utf-8")
f.write("hello world")
f.flush()
```

## 22.异常

```python
# 捕获异常
# 这里可能出现异常
try:
    result=10 /0
# 出现异常以这种方式解决    
except:
    result=10/1
    
## 捕获指定的异常
try:
    print(未命名的name)
except NameError as e:
    print("出现了变量未定义的异常")
    
# 捕获所有异常
try:
    f = open("D:/123.txt","r")
except Exception as e:
    print("出现异常了")
# 没有异常做的代码块    
else:
    print("这里是没有异常做的事")
# 无论有没有异常都会执行    
finally：

```

## 23.模块

```python
# 引入一个模块
import time
# 引入模块里的一个功能
# 不需要time.sleep 只需要sleep
from time import sleep
# 导入模块里的所有功能
from time import * 
# 给模块起别名
from time as t
from time import sleep as t

```

### 自定义模块

```python
# 文件名 my_module.py
def test(a,b):
    print(a,b)
# 测试代码写这里 模块导入不会触发
if __name__ == '__main__':    

#设置导全部包的函数    
__all__ = ['file_util'] 
```

## 24. python包

>多个模块的文件夹
>
>里面含下面这个文件

```python
__init.py__
```

### 自己写一个python包

```python
创建一个python包
my_utils
里面含三个python文件
__init__.py 包需要的必备py
file_util.py
str_util.py
```

```python
# __init__.py
```

```python
# file_util.py
"""
Created on Mon Jul 17 14:
用于 处理文件相关工具
@author: zjaaa
"""


def read_file(filename):
    f = None
    try:
        f = open(filename, "r", encoding="utf-8")
        content = f.read()
        print(f'程序输出如下:\n读取的文件为:{filename}\n读的内容为:\n{content}')
    except Exception as e:
        print(f"程序出现异常了,原因为{e}")
    finally:
        if None:
            f.close()

def append_file(filename, content):
    f = open(filename, "a", encoding="utf-8")
    f.write(content)
    f.write("\n")
    f.close()

```

```python
# str_util.py
"""
Created on Mon Jul 22 14:
@author: zjaaa
用于 处理字符串的工具
"""

def str_reverse(str):
    """
    用于反转字符串
    :param 输入一个字符串
    :return:字符串反转的结果
    """
    return str[::-1]
def substr(s,x,y):
    """
    用于截取字符串
    :param s:输入的字符串
    :param x:开头的索引
    :param y:结尾的索引
    :return:截取的字符
    """
    return s[x:y+1]
if __name__ == '__main__':
    str = '大家好我叫zaaa，我学习的是python包的学习'
    print(str_reverse(str))
    prin
```



## 25. json

```python
import json
data=[{"name":"张三","age":16},{"name":"李四","age":20}]
# 将python数据转换成json数据
data = json.dumps(data)
# 不想让json数据变成ascii码
data = json.dumps(data,ensure_ascii=Fa)
# 将json数据转换成python数据
data =json.loads(data)
```

# python面向对象

## 1.类

>类包含属性和行为 一般用于描述现实世界事务

```python
class Student:
    name = None
    def sayHi(self):
        print(f"Hello大家好,我是{self.name}")

    def sayHi2(self,msg):
        print(f"hello大家好，我是{self.name},{msg}")

stu = Student()
stu.name= "小明"
stu.sayHi()
stu.sayHi2("很高兴认识大家")
```

## 2.构造方法

```python
class Student:
    ## 可以省略定义成员变量  直接在init方法里定义
    def __init__(self,name,age,tel):
        self.name = name
        self.age = age
        self.tel = tel
stu = Student('John',18,13221213456)
print(stu.name)
print(stu.age)
print(stu.tel)
```

## 3.魔术方法

```
__方法__
```

>如上面所示的都叫做魔术方法

### 常见方法

重写字符串方法

```python
class Student:
    # 将返回象打印结果 默认为内存地址
    def __str__(self):
        return "想打印打印什么，一般重写字符串"
  
```

lt 小于 大于比较方法

```python
class Student:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        # 返回值 true或false
        # lt 只能用于小于和大于 不能用于等于
    def __lt__(self,other):
        return self.age < other.age
```

le 小于等于 大于等于 比较方法

```python
class Stduent:
    def __init__(self,name,age):
        self.name = name
        self.age= age
        # 用于小于等于 以及 大于等于
    def __le__(self,other):
        return self.age<= other.age
```

eq 等于 比较方法

```python
class Student:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __eq__(self,other):
        self.age == other.age
```

## 4.封装

将现实世界的事务在类中描述为属性和方法即为封装

私有方法和成员都是以两个下划线开头

类对象无法访问私有成员

类的其他成员可以访问私有成员

```python
# 私有成员变量和方法都以两个下划线开头__
class Phone:
    __current_voltage = None
    
    def __keep_single_core(self):
        print("让cpu单核运行")
        
    def call_by_5g(self):
        if self.current_vlotage >=1:
            print("5g通话已开启")
        else:
            self.__keep_single_core()
            print("电量不足，无法使用5g通话，已设置单核运行")
```

```python
class Phone:
    __is5g_enable = False
    def __check_5g(self):
        if self.__is5g_enable:
            print("5g开启")
        else:
            print("5g关闭，使用4g")
    def call_by_5g(self):
        self.__check_5g()
        print("正在通话中")
p = Phone()
p.call_by_5g()
```

    ## 5.继承

```python
# 单继承
class 类名(父类名):

class Phone:
    IMEI = None
    producer ="apple"
    def call_by_4g(self):
        print('4g通话')
class Phone2022(Phone):
    def call_by_5g(self):
         print('2022新功能：5g通话')
# 多继承
class Myphone(RemoteControl,Phone,NFCReader):
    # pass 表示 不写新方法新成员 
    pass

# 多继承优先级 从左至右 优先级逐渐递减
```

### 复写 父类方法属性

直接在子类重写属性和方法就好了  

#### 使用被子类重写的父类方法和变量

```python
通过 父类名.成员方法(self)

通过 super().方法

父类名.成员变量

super().成员变量


```

## 6.类型注解

>标记变量类型
>
>类型注解仅仅是提示性的 不会影响程序运行

```python
# 基础数据类型注解
var_1: int =10
var_2: str ="zjaaa"
var_3: bool = True
# 类对象类型注解
class Student:
    pass
stu: Student = Student()
# 基础容器类型注解
my_list: list=[1,2,3]
my_tuple: tuple=(1,2,3)
my_dict: dict={"zjaaa"：666}
# 容器类型详细注解
my_list: list[int] =[1,2,3]
my_tuple: tuple[int,str,bool]=(1,"zjaaa"，True)
my_dict: dict[str,int] = {"itheima":666}  
    
# 在注释中进行注解
var_1 = 111 # type: int
var_2 = josn.loads('{"name"："zhangsan"}') # type: dict[str,str]

# 函数方法形参进行注解
def add(x: int,y: int):
    return x + y
# 对返回值进行类型注解
def func(data: list) -> list:
    return data

# Union类型 定义联合类型注解
from typing import Union
my_list: list[Union[int,str]] = [1,2,"zjaaa"]

def func(data: Union[int,str]) -> Union[int,str]:
    pass
```

## 6.多态

>同一个行为 使用不同的对象 获取不同的状态
>
>抽象类 为 包含抽象方法的类
>
>抽象方法 为 没有具体实现的方法 （pass）
>
>抽象类的作用
>
>用于提供标准 便于子类做具体实现
>
>

```python
class AC:
    def cool_wind(self):
        """制冷"""
        pass

    def hot_wind(self):
        """制热"""
        pass

    def swing_l_r(self):
        """左右摆风"""
        pass


class Midea_AC(AC):
    def cool_wind(self):
        print("美的吹冷风")

    def hot_wind(self):
        print('美的吹热风')

    def swing_l_r(self):
        print("美的左右摇摆")


class GREE_AC(AC):
    def cool_wind(self):
        print("格力吹冷风")

    def hot_wind(self):
        print("格力吹热风")

    def swing_l_r(self):
        print('格力左右摇摆')


def make_cool(ac: AC):
    ac.cool_wind()


midea_ac = Midea_AC()
gree_ac = GREE_AC()
make_cool(midea_ac)
make_cool(gree_ac)

```

## 7. python使用mysql

>pip install pymysql

创建表

```python
from pymysql import Connection
# 获取mysql的连接对象
conn = Connection(
    host= "localhost",
    port=3306,
    user="root",
    password="root"
)
# 执行非查询sql
# 获取游标对象
cursor = conn.cursor()
# 选择数据库
conn.select_db("test")
# 执行sql
cursor.execute("create table test_pymysql(id int)")
# 关闭连接
conn.close()


```

查询数据

```python
from pymysql import Connection
# 获取mysql的连接对象
conn = Connection(
    host= "localhost",
    port=3306,
    user="root",
    password="root"
)
# 执行查询sql
# 获取游标对象
cursor = conn.cursor()
# 选择数据库
conn.select_db("test")
# 执行sql
cursor.execute("select * from dakatime")
rs = cursor.fetchall()
for i in rs:
    print(i)
conn.close()
```

插入数据

发现一般默认建表引擎都不是innodb

如果事务没生效可以看看建表引擎 

```python
from pymysql import Connection
# 获取mysql的连接对象
conn = Connection(
    host= "localhost",
    port=3306,
    user="root",
    password="root",
    # 设置事务 一般会默认false 
    autocommit=False
)
# 执行插入sql
cursor = conn.cursor()
# 选择数据库
conn.select_db("test")
# 执行sql
cursor.execute("insert into test_pymysql values (3)")
## 提交事务
conn.commit()
conn.close()
```

## 8.闭包

记得用nonlocal修改属性

## 9.装饰器

```python
def outer(func):
    def inner():
        print('我睡觉了')
        func()
        print('我起床了')
    return inner
@outer # 直接把这个函数当参数传入@后面的函数
def sleep():
    print('睡眠中')
# 如果没写@增强方法 一般的执行操作
fn = outer(sleep)
fn()
# 写了@增强方法的执行操作
fn()
```

## 10.多线程

```python
import threading

# target 指定函数任务 args 指定元组传参 kwargs指定字典传参
def sing(msg):
    while(True):
        print(f'我在唱{msg}')
sing_thread= threading.thread(target=sing,args=('两只老虎',))
s
```



# 第三方包的使用以及记录

## pyechars图例库的使用

```python
from pyecharts.charts import Line
from pyecharts.options import TitleOpts, LegendOpts, ToolboxOpts, VisualMapOpts

# 创建一个折线图对象
line = Line()
# 给折线图添加x坐标
line.add_xaxis(["中国","美国","英国"])
# 给折线图添加y坐标
line.add_yaxis("GDP",[30,20,10])
# 设置全局配置项
line.set_global_opts(
    # 展示标题 设置离左边居中 离下面百分之一距离
    title_opts=TitleOpts(title="GDP展示",pos_left="center",pos_bottom="1%"),
    # 设置图例
    legend_opts=LegendOpts(is_show=True),
    # 设置工具箱
    toolbox_opts=ToolboxOpts(is_show=True),
    # 设置视觉映射
    visualmap_opts=VisualMapOpts(is_show=True)
)

line.render()

```

### 1.折线图使用

```python
import json

from pyecharts.charts import Line
from pyecharts.options import TitleOpts, ToolboxOpts, LabelOpts


def get_country_trend_data(file_str):
    """
    获取国家的trend值
    :param file_str:填入数据路径
    :return: 返回trend值
    """
    with open(file_str,"r",encoding='utf-8') as f:
        country_data = f.read()
        country_data = country_data.split('(',1)[1]
        country_data = country_data[:-2]
        country_dict = json.loads(country_data)
        return country_dict['data'][0]['trend']
def get_country_x_data(trend_value):
    """
    获取天数
    :param trend_value: 填入trend值
    :return: 返回x坐标
    """
    return trend_value['updateDate'][:314]
def get_country_y_data(trend_value):
    """
    获取每天感染人数
    :param trend_value:  填入trend值
    :return:  返回y坐标
    """
    return trend_value['list'][0]['data'][:314]
# 获取三国 trend数据
us_trend_data = get_country_trend_data('G:/美国.txt')
jp_trend_data = get_country_trend_data('G:/日本.txt')
in_trend_data = get_country_trend_data('G:/印度.txt')
# 获取一年日期
x_data = get_country_x_data(us_trend_data)
# 获取三国 感染人数
us_y_data = get_country_y_data(us_trend_data)
jp_y_data = get_country_y_data(jp_trend_data)
in_y_data = get_country_y_data(in_trend_data)
# 生成分析图
line = Line()
line.add_xaxis(x_data)
line.add_yaxis('美国确诊人数',us_y_data,label_opts=LabelOpts(is_show=False))
line.add_yaxis('日本确诊人数',jp_y_data,label_opts=LabelOpts(is_show=False))
line.add_yaxis('印度确诊人数',in_y_data,label_opts=LabelOpts(is_show=False))
line.set_global_opts(
    title_opts=TitleOpts(title="国家感染分析图"),
    toolbox_opts=ToolboxOpts(is_show=True)
)
line.render()

```



### 2.地图的使用

```python
import json

from pyecharts.charts import Map
from pyecharts.options import TitleOpts, VisualMapOpts

province_data = None
province_data_list = list()
with open("G:/疫情.txt",'r',encoding='utf8') as f:
    province_data = f.read()
    # 转换成字典一定不要忘！ str可没字典的字符串索引
    province_data = json.loads(province_data)
    province_data = province_data['areaTree'][0]['children']
    for data in province_data:
        province_data_list.append((f"{data['name']}省",data['total']['confirm']))

map = Map()
map.add('各省份确诊人数',province_data_list,'china')
map.set_global_opts(
    title_opts=TitleOpts(title="全国确诊图",pos_left='center',pos_bottom='1%'),
    visualmap_opts= VisualMapOpts(
        is_show=True,  # 是否显示
        is_piecewise=True, # 是否分段
        pieces=[
            {'min':1,'max':99,'label':'1-99人','color':'#CCFFFF'},
            {'min':100,"max":999,'label':"100-999人",'color':'#FFFF99'},
            {'min':1000,'max':4999,'label':'1000-4999人','color':'#FF9966'},
            {'min':5000,'max':9999,'label':'5000-9999人','color':'#FF6666'},
            {'min':10000,'max':99999,'label':'10000-99999人','color':'#CC3333'},
            {'min':100000,'label':'100000+','color':'#990033'}
        ]
    )
)
map.render('全国确诊地图.html') # 控制生成文件名

```

### 3.柱状图的使用

#### 简单柱状图

```python
from pyecharts.charts import Bar

bar = Bar()
bar.add_xaxis(['中国','美国','英国'])
bar.add_yaxis("GDP对比",[35,60,25])
bar.reversal_axis() # 把坐标系反转
bar.render('简单的柱状图生成.html')
```

#### 1960-2019全球经济前十柱状图

```python
from pyecharts.charts import Bar,Timeline
from pyecharts.options import LabelOpts,TitleOpts
from pyecharts.globals import ThemeType

# 设置主题
timeline = Timeline({'theme': ThemeType.LIGHT})
country_gdp_dict = {}
with open('G:/1960-2019全球GDP数据.csv', 'r', encoding='gbk') as f:
    all_data = f.readlines()
    all_data.pop(0)
    for i in all_data:
        data = i.split(',')
        year = data[0]
        country = data[1]
        # 把科学计数法E用浮点数转换成数字
        gdp = float(data[2])
        # 如果有 列表 则添加数据 如果 报错 无列表 则 初始化列表 再添加
        try:
            country_gdp_dict[year].append([country, gdp])
        except KeyError:
            country_gdp_dict[year] = []
            country_gdp_dict[year].append([country, gdp])
# 把字典的keys排序一下 sorted默认升序排
sorted_year = sorted(country_gdp_dict.keys())
for year in sorted_year:
    # 把一年里的国家按GDP排名 进行排序
    country_gdp_dict[year].sort(key=lambda element: element[1], reverse=True)
    year_data = country_gdp_dict[year][:10]
    x_data = []
    y_data = []
    # 对每个国家进行遍历
    for country_gdp in year_data:
        x_data.append(country_gdp[0])
        y_data.append(country_gdp[1] / 100000000)
    bar = Bar()
    # 把世界第一排上面 默认是排下面
    x_data.reverse()
    y_data.reverse()
    bar.add_xaxis(x_data)
    # 把标记放右边
    bar.add_yaxis('GDP(亿)',y_data,label_opts=LabelOpts(position='right'))
    # 把直的柱状图变成横的
    bar.reversal_axis()
    bar.set_global_opts(
        title_opts=TitleOpts(title=f'{year}年GDP全球前十数据')
    )
    timeline.add(bar,str(year))
# 设置一下自动播放配置项
timeline.add_schema(
    play_interval=1000,
    is_timeline_show=True,
    is_auto_play=True,
    is_loop_play=False
)
timeline.render("1960-2019全世界dgp前十国家动态对比.html")
```

