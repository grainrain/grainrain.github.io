---
title: Python学习-Day1
date: 2019-11-20 09:17:04
categories: 
           - Python
tags:
           - Python
           - Python3
---

> 1.变量介绍  
> 2.字符编码  
> 3.用户输入  
> 4.模块初识  
> 5. .pyc是什么？  
> 6.数据类型初识  
> 7.数据运算  
> 8.表达式if ...else语句  
> 9.表达式for 循环  
> 10.break and continue   

## 一、变量介绍

### 定义规则
+ 变量名只能是 字母、数字或下划线的任意组合
+ 变量名的第一个字符不能是数字
+ 以下关键字不能声明为变量名

```python
['and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'exec', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'not', 'or', 'pass', 'print', 'raise', 'return', 'try', 'while', 'with', 'yield']
```
### 变量赋值
```python
ame = "Benjamin"
name2 = name
print(name,name2)
name = "Jack"
print("What is the value of name2 now?")
```

## 二、字符编码
python解释器在加载中py文件会对.py文件内容进行编码（默认ascill）

ASCII（American Standard Code for Information Interchange，美国标准信息交换代码）是基于拉丁字母的一套电脑编码系统，主要用于显示现代英语和其他西欧语言，其最多只能用 8 位来表示（一个字节），即：2**8 = 256-1，所以，ASCII码最多只能表示 255 个符号。
![](http://ningyylin.top/image/python/ASCII.jpg)

### 关于中文
为了处理汉字，程序员设计了用于简体中文的GB2312和用于繁体中文的big5。

GB2312(1980年)一共收录了7445个字符，包括6763个汉字和682个其它符号。汉字区的内码范围高字节从B0-F7，低字节从A1-FE，占用的码位是72*94=6768。其中有5个空位是D7FA-D7FE。

GB2312 支持的汉字太少。1995年的汉字扩展规范GBK1.0收录了21886个符号，它分为汉字区和图形符号区。汉字区包括21003个字符。2000年的 GB18030是取代GBK1.0的正式国家标准。该标准收录了27484个汉字，同时还收录了藏文、蒙文、维吾尔文等主要的少数民族文字。现在的PC平台必须支持GB18030，对嵌入式产品暂不作要求。所以手机、MP3一般只支持GB2312。

从ASCII、GB2312、GBK 到GB18030，这些编码方法是向下兼容的，即同一个字符在这些方案中总是有相同的编码，后面的标准支持更多的字符。在这些编码中，英文和中文可以统一地处理。区分中文编码的方法是高字节的最高位不为0。按照程序员的称呼，GB2312、GBK到GB18030都属于双字节字符集 (DBCS)。

有的中文Windows的缺省内码还是GBK，可以通过GB18030升级包升级到GB18030。不过GB18030相对GBK增加的字符，普通人是很难用到的，通常我们还是用GBK指代中文Windows内码。


## 三、用户输入
```python
#!/usr/bin/env python
#_*_coding:utf-8_*_
 
 
#name = raw_input("What is your name?") #only on python 2.x
name = input("What is your name?")
print("Hello " + name )
```

输入密码时，如果想要不可见，需要利用getpass 模块中的 getpass方法，即：
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
  
import getpass
  
# 将用户输入的内容赋值给 name 变量
pwd = getpass.getpass("请输入密码：")
  
# 打印输入的内容
print(pwd)
```

## 四、模块知识
Python有非常丰富和强大的标准库和第三方库

+ sys
```python
!/usr/bin/env python
# -*- coding: utf-8 -*-
 
import sys
 
print(sys.argv)
 
 
#输出
$ python test.py helo world
['test.py', 'helo', 'world']  #把执行脚本时传递的参数获取到了

```

+ os
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
 
import os
 
os.system("df -h") #调用系统命令

```
+ python tab补全模块(自定义)

这里不展开，可以Google or Baidu

## 五、.pyc是什么？
Python是一门先编译后解释的语言

当python程序运行时，编译的结果则是保存在位于内存中的PyCodeObject中，当Python程序运行结束时，Python解释器则将PyCodeObject写回到pyc文件中。

当python程序第二次运行时，首先程序会在硬盘中寻找pyc文件，如果找到，则直接载入，否则就重复上面的过程。

所以我们应该这样来定位PyCodeObject和pyc文件，pyc文件其实是PyCodeObject的一种持久化保存方式

## 六、数据类型初识

### 1、数字
int（整型）

　　在32位机器上，整数的位数为32位，取值范围为-2**31～2**31-1，即-2147483648～2147483647
　　在64位系统上，整数的位数为64位，取值范围为-2**63～2**63-1，即-9223372036854775808～9223372036854775807
long（长整型）
　　跟C语言不同，Python的长整数没有指定位宽，即：Python没有限制长整数数值的大小，但实际上由于机器内存有限，我们使用的长整数数值不可能无限大。
　　注意，自从Python2.2起，如果整数发生溢出，Python会自动将整数数据转换为长整数，所以如今在长整数数据后面不加字母L也不会导致严重后果了。
float（浮点型）
　　浮点数用来处理实数，即带有小数的数字。类似于C语言中的double类型，占8个字节（64位），其中52位表示底，11位表示指数，剩下的一位表示符号。
complex（复数）
　　复数由实数部分和虚数部分组成，一般形式为x＋yj，其中的x是复数的实数部分，y是复数的虚数部分，这里的x和y都是实数。
注：Python中存在小数字池：-5 ～ 257

### 2、布尔值
真或假
1 或 0
### 3、字符串
python中的字符串在C语言中体现为是一个字符数组，每次创建字符串时候需要在内存中开辟一块连续的空，并且一旦需要修改字符串的话，就需要再次开辟空间，+号每出现一次就会在内从中重新开辟一块空间。
字符串格式化输出
```python
name = "Benjamin"
print "i am %s " % name
  
#输出: i am Benjamin
```
字符串常用功能：
+ 移除空白
+ 分割
+ 长度
+ 索引
+ 切片

### 4、列表
```python
name_list = ['Benjamin', 'seven', 'eric']
或
name_list ＝ list(['Benjamin', 'seven', 'eric'])
```
基本操作：

+ 索引
+ 切片
+ 追加
+ 删除
+ 长度
+ 切片
+ 循环
+ 包含

### 5、元组(不可变列表)
```python
ages = (11, 22, 33, 44, 55)
或
ages = tuple((11, 22, 33, 44, 55))
```

### 6、字典（无序）

```python
person = {"name": "Benjamin", 'age': 18}
或
person = dict({"name": "Benjamin", 'age': 18})
```

## 六、数据运算

算数运算：
![](http://ningyylin.top/image/python/arithmetic_operation.png)

比较运算：
![](http://ningyylin.top/image/python/comparison_operation.png)

赋值运算：
![](http://ningyylin.top/image/python/assignment_operation.jpg)

逻辑运算：
![](http://ningyylin.top/image/python/logical_operation.png)

位运算：
![](http://ningyylin.top/image/python/bit_operation.png)

```python
#!/usr/bin/python
  
a = 60            # 60 = 0011 1100
b = 13            # 13 = 0000 1101
c = 0
  
c = a & b;        # 12 = 0000 1100
print "Line 1 - Value of c is ", c
  
c = a | b;        # 61 = 0011 1101
print "Line 2 - Value of c is ", c
  
c = a ^ b;        # 49 = 0011 0001 #相同为0，不同为1
print "Line 3 - Value of c is ", c
  
c = ~a;           # -61 = 1100 0011
print "Line 4 - Value of c is ", c
  
c = a << 2;       # 240 = 1111 0000
print "Line 5 - Value of c is ", c
  
c = a >> 2;       # 15 = 0000 1111
print "Line 6 - Value of c is ", c

# 按位取反运算规则(按位取反再加1) 
```

运算符优先级：
![](http://ningyylin.top/image/python/operator_precedence.png)

## 七、表达式if  else
```python
# 验证用户名和密码
#     如果错误，则输出用户名或密码错误
#     如果成功，则输出 欢迎，XXX!
 
 
#!/usr/bin/env python
# -*- coding: encoding -*-
  
import getpass
  
  
name = raw_input('请输入用户名：')
pwd = getpass.getpass('请输入密码：')
  
if name == "alex" and pwd == "cmd":
    print("欢迎，alex！")
else:
    print("用户名和密码错误")

```
## 八、表达式for 循环 
```python
#_*_coding:utf-8_*_
 
for i in range(10):
    print("loop:", i )
```

## 九、while loop 

```python
#_*_coding:utf-8_*_
 
count = 0
while True:
    print("dead loop...",count)
    count +=1
```