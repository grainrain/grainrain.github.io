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

#定义一个高阶函数
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

+ 3.嵌套函数


 **高阶函数+嵌套函数->装饰器**

## 三、迭代器与生成器
 

