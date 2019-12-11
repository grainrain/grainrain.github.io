---
title: Python学习-Day4
date: 2019-11-23 09:17:04
categories: 
           - Python
tags:
           - Python
           - Python3
---

> 1.递归
> 2.装饰器
> 3.迭代器与生成器


## 一、递归

### 特点
递归算法特点：
(1) 递归就是在过程或函数里调用自身。
(2) 在使用递归策略时，必须有一个明确的递归结束条件，称为递归出口。
(3) 递归算法解题通常显得很简洁，但递归算法解题的运行效率较低。所以一般不提倡用递归算法设计程序。
(4) 在递归调用的过程当中系统为每一层的返回点、局部量等开辟了栈来存储。递归次数过多容易造成栈溢出等。所以一般不提倡用递归算法设计程序。
### 示例

```python
def calc(n):
    print(n)
    if int(n / 2) > 0:
        return calc(int(n / 2))
    print("-> ",n)
calc(10)

```

## 二、装饰器

### 定义
**本质是函数，（装饰其他函数）就是为其他函数添加附加功能**
### 原则
+ 1.不能修改被装饰的函数源代码  
+ 2.不能修改被装饰的函数调用方式

### 实现装饰器
+ **1.函数即“变量”**
+ 2.高阶函数  
 *a:把一个函数名当做实参传给另外一个函数（不修改被装饰函数源代码的情况下为其添加功能）  
 b:返回值中包含函数名(不修改函数的调用方式)*
 ```python



+ 3.嵌套函数

 **高阶函数+嵌套函数->装饰器**


 #示例
def timer(func): # timer(test1) func =test1
    def wrapper(*args,**kwargs):
        start_time = time.time()
        func(*args,**kwargs)   #run test1
        stop_time = time.time()
        print("the func run time is %s " % (stop_time - start_time))
    return  wrapper

@timer #test1 = timer(test1)
def test1():
    time.sleep(3)
    print('in the test1')
@timer
def test2(name,age):
    time.sleep(3)
    print('test2',name,age)

test1()
test2('lin',22)
```

## 三、迭代器与生成器


### 生成器
通过列表生成式，我们可以直接创建一个列表。但是列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。
所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器

创建L和g的区别仅在于最外层的[]和()，L是一个list，而g是一个generator。
```python
#普通循环
[i*2 for i in range(10)]

#生成器
(i*2 for i in range(10000000000))
```

生成器只有在调用时才会生成相应的数据
只记录当前的位置
只有一个__next__()方法


```python
#通过函数创建一个生成器
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield  b
        a, b = b, a + b
        n = n + 1
    return 'done'

f = fib(100) #生成器

print(f.__next__())
print(f.__next__())
print(f.__next__())
```

捕获异常处理
```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'


g = fib(6)
while True:
    try:
        x = next(g)
        print('g:', x)
    except StopIteration as e:
        print('Generator return value:', e.value)
        break

```

通过yield实现在单线程的情况下实现并发运算的效果　
```python
#_*_coding:utf-8_*_
__author__ = 'Alex Li'

import time
def consumer(name):
    print("%s 准备吃包子啦!" %name)
    while True:
       baozi = yield

       print("包子[%s]来了,被[%s]吃了!" %(baozi,name))


def producer(name):
    c = consumer('A')
    c2 = consumer('B')
    c.__next__()
    c2.__next__()
    print("老子开始准备做包子啦!")
    for i in range(10):
        time.sleep(1)
        print("做了2个包子!")
        c.send(i)
        c2.send(i)

producer("alex")

#通过生成器实现协程并行运算
```
### 迭代器
*可以被next()函数调用并不断返回下一个值的对象称为迭代器：Iterator*
可以使用isinstance()判断一个对象是否是Iterable对象：
可以直接作用于for循环的数据类型有以下几种：
+ 集合数据类型，如list、tuple、dict、set、str等；
+ 是generator，包括生成器和带yield的generator function。


```python
for x in [1, 2, 3, 4, 5]:
    pass
```

```python
# 首先获得Iterator对象:
it = iter([1, 2, 3, 4, 5])
# 循环:
while True:
    try:
        # 获得下一个值:
        x = next(it)
    except StopIteration:
        # 遇到StopIteration就退出循环
        break
```

生成器都是Iterator对象，但list、dict、str虽然是Iterable，却不是Iterator。

把list、dict、str等Iterable变成Iterator可以使用iter()函数：
```python
>>> isinstance(iter([]), Iterator)
True
>>> isinstance(iter('abc'), Iterator)
True
```

