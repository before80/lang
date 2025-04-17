+++
title = "内存模型"
date = 2025-04-11T23:35:02+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/memory_model](https://zh.cppreference.com/w/c/language/memory_model)

​	为 C 抽象机的目的，定义计算机内存存储的语义。

​	可用于 C 程序的数据存储（内存）是一个或多个连续*字节* ﻿的序列。内存中每个字节拥有唯一的*地址*。

## 字节

​	*字节* ﻿是内存的最小可寻址单元。它定义为一系列连续的位，足以保有任何*基础执行字符集*（要求 [96 个字符](https://zh.cppreference.com/w/c/language/translation_phases)是单字节）。C 支持大小为 8 位或更多的字节。

​	`char`、`unsigned char` 及 `signed char` [类型](https://zh.cppreference.com/w/c/language/types)的存储和[值表示]({{< ref "/c/language/basic_concepts/object" >}})都使用一个字节。字节的位数可以用 [CHAR_BIT]({{< ref "/c/types/limits" >}}) 访问。

​	对于用字节表示其他基础类型的（包含大端与小端内存布局），见[对象表示]({{< ref "/c/language/basic_concepts/object#.E5.AF.B9.E8.B1.A1.E8.A1.A8.E7.A4.BA" >}})。

## 内存位置

​	*内存位置* ﻿是

- 一个[标量类型](https://zh.cppreference.com/w/c/language/types#.E5.AF.B9.E8.B1.A1.E7.BB.84.E5.88.AB)（算术类型、指针类型、枚举类型）的对象
- 或非零长[位域]({{< ref "/c/language/declarations/bit_field" >}})的最大连续序列

```c
struct S
{
    char a;     // 内存位置 #1
    int b : 5;  // 内存位置 #2
    int c : 11, // 内存位置 #2（连续）
          : 0,
        d : 8;  // 内存位置 #3
    struct
    {
        int ee : 8; // 内存位置 #4
    } e;
} obj; // 对象“obj”由 4 个分离的内存位置组成
```

## 线程及数据竞争

​	执行的线程是一个程序中的控制流，它以调用顶层函数 [thrd_create](https://zh.cppreference.com/w/c/thread/thrd_create) 或其他方法起始。

​	任意线程可潜在地访问程序中的任意对象（拥有自动及线程局域[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象仍能通过指针被另一线程访问）。

​	执行的不同线程始终允许同时访问（读或修改）不同的*内存位置*，这没有冲突和同步要求（注意同时更新二个同一结构体内的非原子位域是不安全的，若所有声明于其间的成员亦为（非零长）位域，不管那些插入的位域大小是多少）。

​	一个表达式的[求值]({{< ref "/c/language/expressions/eval_order" >}})写入一个内存位置，而另一求值读取或修改同一内存位置时，我们称这两个表达式*冲突*。拥有两个冲突表达式的程序有*数据竞争* ﻿，除非

- 两个冲突求值是[原子操作]({{< ref "/c/language/declarations/atomic" >}})
- 一个冲突求值*先发生于* ﻿另一个（见 [memory_order](https://zh.cppreference.com/w/c/atomic/memory_order)）

​	若发生数据竞争，则程序行为未定义。

（特别是，[mtx_unlock](https://zh.cppreference.com/w/c/thread/mtx_unlock) 与另一线程的 [mtx_lock](https://zh.cppreference.com/w/c/thread/mtx_lock) *同步*，从而*先发生于* ﻿后者，这使得可以用互斥锁保证排除数据竞争）

本节未完成
原因：一或二个小示例

## 内存顺序

​	线程从一个内存位置读取值时，它可能看到初始值、被同一线程写入的值，或被其他线程写入的值。关于线程所做的写入对其他线程变得可见的顺序细节，见 [memory_order](https://zh.cppreference.com/w/c/atomic/memory_order)。

## 参阅

**内存模型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/memory_model)**
