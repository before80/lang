+++
title = "C 属性： unsequenced, reproducible (C23 起)"
date = 2025-04-13T11:27:37+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/unsequenced](https://zh.cppreference.com/w/c/language/attributes/unsequenced)

向编译器提供函数访问对象的信息，使其可以推导函数调用的某些性质。

## 语法

| `[[` `unsequenced` `]]` <br />`[[` `__unsequenced__` `]]`   | (1)  |      |
| ----------------------------------------------------------- | ---- | ---- |
| `[[` `reproducible` `]]` <br />`[[` `__reproducible__` `]]` | (2)  |      |

1) 指示函数[无作用]({{< ref "/c/language/declarations/attributes/unsequenced#.E6.97.A0.E4.BD.9C.E7.94.A8" >}})、[幂等]({{< ref "/c/language/declarations/attributes/unsequenced#.E5.B9.82.E7.AD.89" >}})、[无状态]({{< ref "/c/language/declarations/attributes/unsequenced#.E6.97.A0.E7.8A.B6.E6.80.81" >}})且[无关联]({{< ref "/c/language/declarations/attributes/unsequenced#.E6.97.A0.E5.85.B3.E8.81.94" >}})。
2) 指示函数无作用且幂等

## 解释

​	这些属性适用于函数声明符或者具有函数类型的类型说明符。相应属性是函数类型的性质。

### 无作用

​	如果函数调用过程中编入序列的任何存储操作，都是对某对象的同步于此次调用的修改，则该调用的执行是无作用的；如果这种存储操作还是可观察的，则对该对象的所有访问必须都基于函数的一个唯一指针形参进行。

### 幂等

​	对于某个求值 *E*，若 *E* 的第二次求值可以紧跟第一次求值编入序列而不改变结果值（如果有）或执行的可观察状态，则它是幂等的。

### 无状态

​	如果函数 *F* 或其所调用的任何函数中，具有静态或线程[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的任意对象的定义均为 `const` 但无 `volatile` 限定，则 *F* 是无状态的。

#### 无关联

​	对于函数 *F*，如果 *F* 的调用中可以通过并非该调用的形参的左值而观察到任何对象 *X*，而在同一次程序执行中所有对 *F* 的调用中，对 *X* 的所有访问都观察到相同的值，则 *F* 无关联；或者如果访问是通过某个指针形参进行，则应当有一个唯一的这种指针形参 *P*，使得对 *X* 的任何访问都应当是基于 *P* 的左值访问。

​	对象 *X* 由函数调用所观察的条件是：二者均同步，*X* 并非局部与此次调用，*X* 的生存期开始于函数调用之前，且此次调用中有对 *X* 的访问被排入序列；此次调用前所存储的 *X* 的最新值（如果有），被称为此次调用所观察到的 *X* 的值。

## 注解

​	这些属性为编译器优化的目的而存在。

​	如果函数可重现，则可将先后多次调用当做一次调用。

​	如果函数无顺序，则可将先后多次调用当做一次调用，且这些调用可以并行化并任意重排。
