+++
title = "联合体声明"
date = 2025-04-13T10:36:01+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/union](https://zh.cppreference.com/w/c/language/union)

​	联合体是由一序列的成员所组成的类型，各成员的存储重叠（与结构体相反，结构体是由一序列的成员所构成的类型，成员的存储以顺序分配）。在任一时刻，最多能在联合体中存储其一个成员的值。

​	联合体的[类型说明符]({{< ref "/c/language/declarations" >}})与 [`struct`]({{< ref "/c/language/declarations/struct" >}}) 类型说明符相同，只是所用的关键词有别。

## 语法

| `union` *属性声明符序列* ﻿(可选) *名字* ﻿(可选) `{` *结构体声明列表* `}` | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `union` *属性声明符序列* ﻿(可选) *名字*                       | (2)  |      |

| *名字*           | -    | 所定义的联合体的名称                                         |
| ---------------- | ---- | ------------------------------------------------------------ |
| *结构体声明列表* | -    | 任意数量的变量声明、[位域]({{< ref "/c/language/declarations/bit_field" >}})声明和[静态断言]({{< ref "/c/language/declarations/_Static_assert" >}})声明。不允许不完整类型的成员和函数类型的成员。 |
| *属性声明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到联合体类型，若这种形式不后随 `;`（即不是前置声明）则对于 (2) 不允许。 |

## 解释

​	联合体只大到足以保有其最大成员（亦可能添加额外的尾随填充字节）。其他成员被分配于与该最大成员一部分相同的字节中。

​	可以将指向联合体的指针转型为指向它每个成员的指针（若联合体拥有位域成员，则能转型指向联合体的指针为指向位域底层类型的指针）。类似地，指向结构体任何成员的指针都能被转型为指向整个结构体的指针。

​	若用于访问内容的联合体成员不同于上次用于存储值的成员，则转译被存储值的对象表示为新类型的对象表示（这被称为*类型双关*）。若新类型的大小大于上次写入的类型大小，则多出的字节内容是未指明的（而且可以是陷阱表示）。C99 TC3（DR 283）之前，此行为未定义，但一般都实现为这种方式。(C99 起)

​	类似结构体，类型为不带 *名字* 的联合体的无名联合体成员被称为*匿名联合体*。每个匿名联合体的成员被认为是外围结构体或联合体的成员并维持联合体布局不变。若外围结构体或联合体亦为匿名，则递归应用此规则。(C11 起)

```c
struct v {
   union // 匿名联合体
   {
      struct { int i, j; }; // 匿名结构体
      struct { long k, l; } w;
   };
   int m;
} v1;
 
v1.i = 2;   // 合法
v1.k = 3;   // 非法：内层结构体不是匿名的
v1.w.k = 5; // 合法
```

​	类似结构体，若不以任何具名成员（包含经由匿名嵌套结构体或联合体获得的成员）定义联合体，则程序行为未定义。

## 关键词

[`union`]({{< ref "/c/language/keyword/union" >}})

## 注解

​	关于结构体和联合体初始化的规则，见[结构体初始化]({{< ref "/c/language/initialization/struct_initialization" >}})。

## 示例

```c
#include <assert.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    union S
    {
        uint32_t u32;
        uint16_t u16[2];
        uint8_t  u8;
    } s = {0x12345678}; // s.u32 现为活跃成员
    printf("Union S has size %zu and holds %x\n", sizeof s, s.u32);
    s.u16[0] = 0x0011;  // s.u16 现为活跃成员
    // 从 s.u32 或 s.u8 的读取转译对象表示
//  printf("s.u8 is now %x\n", s.u8); // 未指定，典型结果是 11 或 00
//  printf("s.u32 is now %x\n", s.u32); // 未指定，典型结果是 12340011 或 00115678
 
    // 指向联合体所有成员的指针彼此间比较相等，也与指向联合体的指针比较相等
    assert((uint8_t*)&s == &s.u8);
 
    // 此联合体拥有尾随的 3 个填充字节
    union pad
    {
       char  c[5];   // 占据 5 字节
       float f;      // 占据 4 字节，隐含对齐 4
    } p = {.f = 1.23}; // 大小为 8 以满足 float 的对齐
    printf("size of union of char[5] and float is %zu\n", sizeof p);
}
```

可能的输出：

```txt
Union S has size 4 and holds 12345678
size of union of char[5] and float is 8
```

## 参阅

联合体声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/union)
