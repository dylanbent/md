title: python copy 模块
date: 2015-06-10 13:48:26
categories: python
tags: [python, 标准库,]
---
程序中常常需要复制一个对象, 按思路应该是这样的
```python
a = [1, 2, 3]
b = a

# [1, 2, 3]
print b 
```
已经复制好了，但是现在得改变一下第一个元素的值把它改成5
```python
b[0] = 5 

# [5, 2, 3]
print b 

# [5, 2, 3]
print a 
```
我改变了`b`的第一个元素的值，但是`a`的值也改变了，这是因为python中的`=`是引用.`a和b`指向的是相同的列表，所以改变列表会出现以上的结果.
<!--more-->
解决方法是切片操作
```python
a = [1, 2, 3]
b = a[:]
b[0] = 4

# [1, 2, 3]
# [4, 2, 3]
print a
print b
```
但是在嵌套列表的时候呢，试一试
```python
a = [[1,2,3], 4, 5]
b = a[:]
b[1] = 0 

# [[1,2,3], 4, 5]
# [[1,2,3], 0, 5]
print a
print b
```
恩！没什么问题，在试一试嵌套列表元素
```python
a = [[1,2,3], 4, 5]
b = a[:]
b[0][0] = 5

# [[5,2,3], 4, 5]
# [[5,2,3], 4, 5]
print a
print b
b = a[:]
```
`a`的值还是改变了，切片复制只对该对象进行拷贝不会对子元素进行拷贝

### copy 模块
<hr>
`copy`模块提供了对对象的拷贝，分为浅拷贝和深拷贝

**copy.copy(x)**
>浅拷贝跟切片复制是相同的效果。只会对该对象进行复制。

**copy.deepcopy(x)**
>深拷贝会循环拷贝其子模块里的内容

```python
import copy

a = [[1,2,3], 4, 5]
b = copy.deepcopy(a)
b[0][0] = 9

# [[1,2,3], 4, 5]
# [[9,2,3], 4, 5]
print a
print b
```