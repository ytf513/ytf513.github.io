---
layout: post
title: Python Class特性摘要及@property使用
category: Python
tags: Python
keywords: Python
description: 
---

与静态语言（java等）相比，python的类使用比较灵活，除了继承、封装、多态之外，还有很多特性：

* 实例的属性可随时添加、更改（但可通过__slots__限制）；类的属性也可通过实例对象访问 
* 支持多重继承
* 可以定制类的内置方法，改变类的行为模式。比如添加类的__iter__方法，实现迭代器的功能
* @property和元类：动态改变类的功能

本节主要介绍@property使用 

```python

#!/usr/bin/env python
#-*- coding:utf-8 -*-

__author__="Alex Yean"
__date__='2015-10-22'

'@property的使用'

print "绑定属性时我们直接调用，虽然写起来简单，但是没办法做校验。为了限制该漏洞，可以用get/set方法"

class Student(object):
    def __init__(self,score=15):
        self.__score=score

    def get_score(self):
        return self.__score

    def set_score(self,score):
        if not isinstance(score,int):
            raise ValueError("score is not integer!")
        elif score<0 or score>100:
            raise ValueError("score is not in 1-100!")
        else:
            self.__score=score

a=Student()
print '__score属性的值a.get_score():',a.get_score()
a.set_score(30)
print '__score属性的值a.get_score():',a.get_score()

print "*"*40
#@property
class StudentN(object):
    @property
    def score(self):
        return self.__score
    @score.setter
    def score(self,score):
        if not isinstance(score,int):
            raise ValueError("score is not integer!")
        elif score<0 or score>100:
            raise ValueError("score is not in 1-100!")
        else:
            self.__score=score

b=StudentN()
b.score=5
print b.score

```
@property装饰器就是把函数score变为类的属性，可以避免直接修改属性的问题，隐藏内部变量。

除了装饰器之外，也可以用属性来设置。
area = property(___get_area, ___set_area,doc="""Gets or sets the area of the square.""")"

除了getter/setter之外，还可以设置deleter。

---
写于2015-12-23

选自《[廖雪峰的官方网站][1]》

[1]: http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386820062641f3bcc60a4b164f8d91df476445697b9e000
