+++
title = "typedef 声明"
date = 2025-04-13T11:09:30+08:00
weight = 140
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/typedef](https://zh.cppreference.com/w/c/language/typedef)

​	*`typedef` 声明* ﻿提供一种声明标识符为类型别名的方式，以用于替换可能复杂的[类型名](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E5.90.8D)。

​	关键词 typedef 在[声明]({{< ref "/c/language/declarations" >}})中处于[存储类说明符]({{< ref "/c/language/declarations/storage_duration" >}})的文法位置，只是它对存储和链接无影响：

```c
typedef int int_t; // 声明 int_t 为类型 int 之别名
typedef char char_t, *char_p, (*fp)(void); // 声明 char_t 为类型 char 之别名
                                           // char_p 为 char* 之别名
                                           // fp 为 char(*)(void) 之别名
```

## 解释

​	若一个[声明]({{< ref "/c/language/declarations" >}})以 typedef 为存储类说明符，则其中每个声明符都会定义一个标识符为说明类型的别名。因为一个声明中仅允许一个存储类说明符，`typedef` 声明不能为 [`static` 或 `extern`]({{< ref "/c/language/declarations/storage_duration" >}})。

​	`typedef` 声明不引入另一种类型，它只会建立既存类型的同义词，故而 typedef 名与其所别名引用的类型[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)。`typedef` 名与如枚举项、变量或函数这样的通常标识符共享[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})。

​	对 VLA 的 `typedef` 只能出现在块作用域内。与数组自身的声明不同，数组长度会在每次控制流经过 `typedef` 声明时求值：(C99 起)

```c
void copyt(int n)
{
    typedef int B[n]; // B 是 VLA，其长度为 n，现在求值
    n += 1;
    B a; // a 的长度是 +=1 前的 n
    int b[n]; // a 和 b 长度不同
    for (int i = 1; i < n; i++)
        a[i-1] = b[i];
}
```



## 注解

​	`typedef` 名可以是[不完整类型](https://zh.cppreference.com/w/c/language/types#.E4.B8.8D.E5.AE.8C.E6.95.B4.E7.B1.BB.E5.9E.8B)，它会照常变得完整：

```c
typedef int A[]; // A 是 int[]
A a = {1, 2}, b = {3,4,5}; // a 的类型是 int[2]，b 的类型是 int[3]
```

`typedef` 声明通常用于将名称从标签[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})注入到通常命名空间：

```c
typedef struct tnode tnode; // 通常命名空间的 tnode
                            // 为标签命名空间的 tnode 之别名
struct tnode {
    int count;
    tnode *left, *right; // 同 struct tnode *left, *right;
}; // 现在 tnode 也是完整类型
tnode s, *sp; // 同 struct tnode s, *sp;
```

​	它们可以完全避免使用标签命名空间：

```c
typedef struct { double hi, lo; } range;
range z, *zp;
```

​	`typedef` 名亦常用来简化复杂声明的语法：

```c
// 5 个函数指针的数组，函数返回指向 3 个 int 的数组的指针
int (*(*callbacks[5])(void))[3];
 
// 与 typedef 相同
typedef int arr_t[3]; // arr_t 是 3 个 int 的数组
typedef arr_t* (*fp)(void); // 指针指向的函数返回 arr_t*
fp callbacks[5];
```

​	库常常会将依赖系统或依赖配置的类型暴露成 `typedef` 名，以对用户或其他库组件提供统一接口：

```c
#if defined(_LP64)
typedef int     wchar_t;
#else
typedef long    wchar_t;
#endif
```

## 关键词

[`typedef`]({{< ref "/c/language/keyword/typedef" >}})

## 参阅

**`typedef` 声明**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/typedef)**
