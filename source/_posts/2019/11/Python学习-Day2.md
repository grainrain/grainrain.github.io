---
title: Python学习-Day2
date: 2019-11-21 09:17:04
categories: 
           - Python
tags:
           - Python
           - Python3
---

> 1.列表、元组操作
> 2.字符串操作
> 3.字典操作
> 4.集合操作
> 5.文件操作
> 6.字符编码与转码 

## 一、列表、元组操作

### 列表
列表是最常用的数据类型之一，通过列表可以对数据实现最方便的存储、修改等操作
#### 切片
```python
>>> names = ["Benjamin","Tenglan","Eric","Rain","Tom","Amy"]
>>> names[1:4]  #取下标1至下标4之间的数字，包括1，不包括4
['Tenglan', 'Eric', 'Rain']
>>> names[1:-1] #取下标1至-1的值，不包括-1
['Tenglan', 'Eric', 'Rain', 'Tom']
>>> names[0:3] 
['Benjamin', 'Tenglan', 'Eric']
>>> names[:3] #如果是从头开始取，0可以忽略，跟上句效果一样
['Benjamin', 'Tenglan', 'Eric']
>>> names[3:] #如果想取最后一个，必须不能写-1，只能这么写
['Rain', 'Tom', 'Amy'] 
>>> names[3:-1] #这样-1就不会被包含了
['Rain', 'Tom']
>>> names[0::2] #后面的2是代表，每隔一个元素，就取一个
['Benjamin', 'Eric', 'Tom'] 
>>> names[::2] #和上句效果一样
['Benjamin', 'Eric', 'Tom']
```
#### 追加
```python
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', 'Tom', 'Amy']
>>> names.append("我是新来的")
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', 'Tom', 'Amy', '我是新来的']
```
#### 插入
```python
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', 'Tom', 'Amy', '我是新来的']
>>> names.insert(2,"强行从Eric前面插入")
>>> names
['Benjamin', 'Tenglan', '强行从Eric前面插入', 'Eric', 'Rain', 'Tom', 'Amy', '我是新来的']

>>> names.insert(5,"从eric后面插入试试新姿势")
>>> names
['Benjamin', 'Tenglan', '强行从Eric前面插入', 'Eric', 'Rain', '从eric后面插入试试新姿势', 'Tom', 'Amy', '我是新来的']
```

#### 修改
```python
>>> names
['Benjamin', 'Tenglan', '强行从Eric前面插入', 'Eric', 'Rain', '从eric后面插入试试新姿势', 'Tom', 'Amy', '我是新来的']
>>> names[2] = "该换人了"
>>> names
['Benjamin', 'Tenglan', '该换人了', 'Eric', 'Rain', '从eric后面插入试试新姿势', 'Tom', 'Amy', '我是新来的']
```
#### 删除
```python
>>> del names[2] 
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', '从eric后面插入试试新姿势', 'Tom', 'Amy', '我是新来的']
>>> del names[4]
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', 'Tom', 'Amy', '我是新来的']
>>> 
>>> names.remove("Eric") #删除指定元素
>>> names
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy', '我是新来的']
>>> names.pop() #删除列表最后一个值 
'我是新来的'
>>> names
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy']
```
#### 扩展
```python
>>> del names[2] 
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', '从eric后面插入试试新姿势', 'Tom', 'Amy', '我是新来的']
>>> del names[4]
>>> names
['Benjamin', 'Tenglan', 'Eric', 'Rain', 'Tom', 'Amy', '我是新来的']
>>> 
>>> names.remove("Eric") #删除指定元素
>>> names
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy', '我是新来的']
>>> names.pop() #删除列表最后一个值 
'我是新来的'
>>> names
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy']
```
#### 拷贝
```python
>>> names
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy', 1, 2, 3]

>>> name_copy = names.copy()
>>> name_copy
['Benjamin', 'Tenglan', 'Rain', 'Tom', 'Amy', 1, 2, 3]
```
#### 统计
```python
>>> names
['Benjamin', 'Tenglan', 'Amy', 'Tom', 'Amy', 1, 2, 3]
>>> names.count("Amy")
2
```
#### 排序&翻转
```python
>>> names
['Benjamin', 'Tenglan', 'Amy', 'Tom', 'Amy', 1, 2, 3]
>>> names.sort() #排序
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unorderable types: int() < str()   #3.0里不同数据类型不能放在一起排序了，擦
>>> names[-3] = '1'
>>> names[-2] = '2'
>>> names[-1] = '3'
>>> names
['Benjamin', 'Amy', 'Amy', 'Tenglan', 'Tom', '1', '2', '3']
>>> names.sort()
>>> names
['1', '2', '3', 'Benjamin', 'Amy', 'Amy', 'Tenglan', 'Tom']

>>> names.reverse() #反转
>>> names
['Tom', 'Tenglan', 'Amy', 'Amy', 'Benjamin', '3', '2', '1']
```
#### 获取下标
```python
>>> names
['Tom', 'Tenglan', 'Amy', 'Amy', 'Benjamin', '3', '2', '1']
>>> names.index("Amy")
2 #只返回找到的第一个下标
```

### 元祖
元组跟列表差不多，不同于列表，不能再修改，所以又叫只读列表
```python
names = ("nanjing","suzhou","wuxi")
```
元祖只有两个方法(count,index)

## 字符串操作
特性：不可修改　

```python
name = "my name is {name} and i am {year} old"

print(name.capitalize())
print(name.count("a"))
print(name.center(50,"-"))
print(name.endswith("ex"))
# print(name.expandtabs(tabsize=30))
print(name[name.find("name"):])

print(name.format(name='alex',year=30))

#字典
print(name.format_map({'name':'alex','year':12}))
print('ab123'.isalnum())
print('abAB'.isalpha())
print('12'.isdecimal())

print('1A'.isdigit())
#判断是否是一个合法的标识符
print('1A'.isidentifier())

print('33.2'.isnumeric()) #只有数字在里面


print('My name is '.istitle())
print('my name'.isprintable())

print('+'.join(["1","2","3"]))

print(name.ljust(50,'*'))
print(name.rjust(50,'-'))

#去除换行
print('\nAlex'.lstrip())
print('Alex\n'.rstrip())
print('\nAlex\n'.strip())
print('--------1--------')

#字符替换,用于密码
p = str.maketrans("adbcef","123456")
print("alex li".translate(p))

print('alex'.replace('a','M'))
print('--------2--------')
print('alex li is me'.rfind('m'))
print('1+2+3+4'.split('+'))
print('1+2\n3+4'.splitlines())
print('Alex'.swapcase())

print('lex li'.title())

print('lex li'.zfill(50))
```

## 字典操作

字典一种key - value 的数据类型，使用就像我们上学用的字典，通过笔划、字母来查对应页的详细内容
```python
info = {
    'stu1101': "TengLan Wu",
    'stu1102': "LongZe Luola",
    'stu1103': "XiaoZe Maliya",
}
```

+ dict是无序的
+ key必须是唯一的,可以去重

### 增加
```python
>>> info["stu1104"] = "苍井空"
>>> info
{'stu1102': 'LongZe Luola', 'stu1104': '苍井空', 'stu1103': 'XiaoZe Maliya', 'stu1101': 'TengLan Wu'}
```
### 修改
```python
>>> info['stu1101'] = "武藤兰"
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya', 'stu1101': '武藤兰'}
```
### 删除
```python
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya', 'stu1101': '武藤兰'}
>>> info.pop("stu1101") #标准删除姿势
'武藤兰'
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya'}
>>> del info['stu1103'] #换个姿势删除
>>> info
{'stu1102': 'LongZe Luola'}
>>> 
>>> 
>>> 
>>> info = {'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya'}
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya'} #随机删除
>>> info.popitem()
('stu1102', 'LongZe Luola')
>>> info
{'stu1103': 'XiaoZe Maliya'}

```
### 查找
```python
>>> info = {'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya'}
>>> 
>>> "stu1102" in info #标准用法
True
>>> info.get("stu1102")  #获取
'LongZe Luola'
>>> info["stu1102"] #同上，但是看下面
'LongZe Luola'
>>> info["stu1105"]  #如果一个key不存在，就报错，get不会，不存在只返回None
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'stu1105
```
### 多级字典嵌套及操作
```python
v_catalog = {
    "欧美":{
        "www.youporn.com": ["很多免费的,世界最大的","质量一般"],
        "www.pornhub.com": ["很多免费的,也很大","质量比yourporn高点"],
        "letmedothistoyou.com": ["多是自拍,高质量图片很多","资源不多,更新慢"],
        "x-art.com":["质量很高,真的很高","全部收费,屌比请绕过"]
    },
    "日韩":{
        "tokyo-hot":["质量怎样不清楚,个人已经不喜欢日韩范了","听说是收费的"]
    },
    "大陆":{
        "1024":["全部免费,真好,好人一生平安","服务器在国外,慢"]
    }
}

av_catalog["大陆"]["1024"][1] += ",可以用爬虫爬下来"
print(av_catalog["大陆"]["1024"])
#ouput 
['全部免费,真好,好人一生平安', '服务器在国外,慢,可以用爬虫爬下来']
```
### 其它
```python
#values
>>> info.values()
dict_values(['LongZe Luola', 'XiaoZe Maliya'])

#keys
>>> info.keys()
dict_keys(['stu1102', 'stu1103'])


#setdefault
>>> info.setdefault("stu1106","Alex")
'Alex'
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya', 'stu1106': 'Alex'}
>>> info.setdefault("stu1102","龙泽萝拉")
'LongZe Luola'
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya', 'stu1106': 'Alex'}


#update 
>>> info
{'stu1102': 'LongZe Luola', 'stu1103': 'XiaoZe Maliya', 'stu1106': 'Alex'}
>>> b = {1:2,3:4, "stu1102":"龙泽萝拉"}
>>> info.update(b)
>>> info
{'stu1102': '龙泽萝拉', 1: 2, 3: 4, 'stu1103': 'XiaoZe Maliya', 'stu1106': 'Alex'}

#items
info.items()
dict_items([('stu1102', '龙泽萝拉'), (1, 2), (3, 4), ('stu1103', 'XiaoZe Maliya'), ('stu1106', 'Alex')])


#通过一个列表生成默认dict,有个没办法解释的坑，少用吧这个
>>> dict.fromkeys([1,2,3],'testd')
{1: 'testd', 2: 'testd', 3: 'testd'}
```
### 循环
```python
#方法1
for key in info:
    print(key,info[key])

#方法2
for k,v in info.items(): #会先把dict转成list,数据里大时莫用
    print(k,v)

```
## 集合操作
集合是一个无序的，不重复的数据组合，它的主要作用如下：

+ 去重，把一个列表变成集合，就自动去重了
+ 关系测试，测试两组数据之前的交集、差集、并集等关系
常用操作
```python
list_1 = [1,4,5,7,3,6,7,9]
demp = [1,4,5,7,3,6,7,9]
list_1  = set(list_1)

list_2 = set([2,6,0,66,22,8,4])


print(list_1,list_2)
#交集
print(list_1.intersection(list_2))

#并集
print(list_1.union(list_2))
#差集
print(list_1.difference(list_2))
print(list_2.difference(list_1))

#子集
list_3 = set([1,3,7])
print(list_1.issubset(list_2))
print(list_1.issuperset(list_2))
print(list_3.issubset(list_1))

#对称差集
print(list_1.symmetric_difference(list_2))

#判断是否有交集,没有则为True
list_4 = set([5,6,8])
print(list_4.isdisjoint(list_3))
```

```python
list_1 = [1,4,5,7,3,6,7,9]
list_1 = set(list_1)
list_2 = set([2,6,0,66,22,8,4])
#交集
print(list_1 & list_2)

#并集
print(list_1 | list_2)

#差集 去掉共同的
print(list_1 - list_2)

#对称差集
print(list_1 ^ list_2)
```

## 文件操作
对文件操作流程
+ 1.打开文件，得到文件句柄并赋值给一个变量
+ 2.通过句柄对文件进行操作
+ 3.关闭文件 

打开文件的模式有：
+ r，只读模式（默认）。
+ w，只写模式。【不可读；不存在则创建；存在则删除内容；】
+ a，追加模式。【可读；   不存在则创建；存在则只追加内容；】

"+" 表示可以同时读写某个文件
+ r+，可读写文件。【可读；可写；可追加】
+ w+，写读
+ a+，同a

"U"表示在读取时，可以将 \r \n \r\n自动转换成 \n （与 r 或 r+ 模式同使用）
+ rU
+ r+U

"b"表示处理二进制文件（如：FTP发送上传ISO镜像文件，linux可忽略，windows处理二进制文件时需标注）
+ rb
+ wb
+ ab


```python
'''
f = open('lyrics','a',encoding='utf-8') #文件句柄

#a  = append
f.write("\nwhen I was young I listen to the radio\n")
data = f.read()
print('--read',data)

f.close()

'''

# for i in range(5):
#     print(f.readline())

'''
f = open('lyrics2','r',encoding='utf-8') #文件句柄
for line in  f.readlines():
    print(line.strip()) # strip去除空格和换行

#不建议使用,因为当文件非常大的时候,很容易造成内存的溢出
for index,line in enumerate(f.readlines()):
    # print(line.strip()) # strip去除空格和换行
    if index == 9 :
        print("------------------------------")
        print(line.strip())
'''
##逐行读文件,当文件的大小不可预测的时候
'''
count  = 0
for line in f:
    if count == 9:
        print("------------------------------")
        count += 1
    print(line)
    count +=1
'''

f = open('lyrics2','r',encoding='utf-8') #文件句柄
'''
#打印当前位置
print(f.tell())
#逐行读取
print(f.readline())
print(f.readline())
print(f.readline())

#打印当前位置
print(f.tell())
#回到指定位置
print(f.seek(0))

#再次读取
print(f.readline())
'''

#print(f.encoding)
#文件在操作系统中的编号
#print(f.fileno())
#print(f.readable())

# print(f.flush())

#print(dir(f.buffer))
```

为了避免打开文件后忘记关闭,可以通过管理上下文，即：
```python
  with open(linkServicceFile, 'r') as f:
  with open(pipeLineFileOut, "w") as dump_f:
```


## 字符编码与转码

+ 1.在python2默认编码是ASCII, python3里默认是unicode

+ 2.unicode 分为 utf-32(占4个字节),utf-16(占两个字节)，utf-8(占1-4个字节)， so utf-16就是现在最常用的unicode版本， 不过在文件里存的还是utf-8，因为utf8省空间

+ 3.在py3中encode,在转码的同时还会把string 变成bytes类型，decode在解码的同时还会把bytes变回string
```python
print(sys.getdefaultencoding())

msg = "我爱北京天安门"
#msg_gb2312 = msg.decode("utf-8").encode("gb2312")
msg_gb2312 = msg.encode("gb2312") #python3默认就是unicode,不用再decode,喜大普奔
gb2312_to_unicode = msg_gb2312.decode("gb2312")
gb2312_to_utf8 = msg_gb2312.decode("gb2312").encode("utf-8")

print(msg)
print(msg_gb2312)
print(gb2312_to_unicode)
print(gb2312_to_utf8)

```