---
title: C++友元(Friend)小结
date: 2017-02-15
tag:
  - C++
category: C++
---

相对`Java`而言，友元是C++中特有的一种元素，再加上`《C++ Primer》`也并没有太详细的例子，所以刚接触这个概念的时候懵了很久，即是自己总结一下，也希望能帮到大家，下面来讲讲友元的用法和一些注意的地方。

操作：
1. 在`MyFriend`类中，将`Father`类定义成友元
1. 写一个`Son`类继承自`Father`类
1. 在`Father`类和`Son`类的构造函数中分别创建`MyFriend`对象，并定义其内部的三个变量
1. 在`MyFriend`类的构造函数中创建`Father`对象，并定义其内部的三个变量

结果：
1. `Father`类中创建的`MyFriend`对象允许直接访问`MyFriend`类中所有变量
1. Son类中创建的`MyFriend`对象只允许直接访问`MyFriend`类中`Public`变量
1. 由第二点可知，友元关系无法继承
1. `MyFriend`类中创建的`Father`对象只允许直接访问`Father`类中的`Public`变量
1. 由第四点可知，友元关系是单向的，即A为B友元，B并不是A的友元，需要另外单独定义

```c++
///////////////////
// MyFriend.h
///////////////////

#include "Father.h"  
  
class MyFriend{  
    friend class Quote; //友元类直接这样定义就OK了  
public:  
    MyFriend(){  
        Father *p = new Father();  
        p->var1 = 1;  
        p->var2 = 1;  
        p->var3 = 1;  
    }  
    int var1;  
protected:  
    int var2;  
private:  
    int var3;  
};
```

```c++
///////////////////
// Father.h
///////////////////

#include "MyFriend.h"  
  
class Father{  
public:  
   Father(){  
        MyFriend *p = new MyFriend();  
        p->var1 = 1;  
        p->var2 = 1;  
        p->var3 = 1;  
    };  
    int var1;  
protected:  
    int var2;  
private:  
    int var3;  
}
```

```c++
///////////////////
// Son.h
///////////////////

#include "MyFriend.h"  
  
class Son : Father{  
   Son(){  
        MyFriend *p = new MyFriend();  
        p->var1 = 1;  
        p->var2 = 1;  
        p->var3 = 1;  
    };  
}  
```