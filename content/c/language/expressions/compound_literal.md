+++
title = "复合字面量 (C99 起)"
date = 2025-04-12T20:33:43+08:00
weight = 130
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/compound_literal](https://zh.cppreference.com/w/c/language/compound_literal)

​	就地构造一个指定类型的无名对象，在只需要一次数组、结构体或联合体变量时使用。

## 语法

| `(` *存储类说明符* ﻿(可选)(C23 起) *类型* `)` `{` *初始化式列表* `}` | (C99 起) |
| ------------------------------------------------------------ | -------- |
| `(` *存储类说明符* ﻿(可选)(C23 起) *类型* `)` `{` *初始化式列表* `,` `}` | (C99 起) |
| `(` *存储类说明符* ﻿(可选) *类型* `)` `{` `}`                 | (C23 起) |

​	其中

| *存储类说明符* | -    | (C23 起)[存储类说明符]({{< ref "/c/language/declarations/storage_duration" >}})的列表，只能包含 `constexpr`、`static`、`register` 或 [thread_local](http://zh.cppreference.com/w/c/thread/thread_local) |
| -------------- | ---- | ------------------------------------------------------------ |
| *类型*         | -    | 指定任何完整对象类型或未知大小的数组的[类型名](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E5.90.8D)，但不能是 VLA |
| *初始化式列表* | -    | 适合类型为 *类型* 的对象进行[初始化]({{< ref "/c/language/initialization" >}})的初始化式的列表 |

## 解释

​	复合字面量表达式构造一个 *类型* 所指定类型的无名对象，并根据 *初始化式列表* 予以初始化。接受[指派初始化器]({{< ref "/c/language/initialization" >}})。

​	复合字面量的类型是 *类型*（除非 *类型* 是未知大小的数组；如在[数组初始化]({{< ref "/c/language/initialization/array_initialization" >}})中一般从 *初始化器列表* 推导出其大小）。

​	复合字面量的值类别是[左值]({{< ref "/c/language/expressions/value_category" >}})（能取其地址）。

​	若复合字面量出现于文件作用域，则其求值所得的无名对象拥有静态[存储期]({{< ref "/c/language/declarations/storage_duration" >}})，若复合字面量出现于块作用域，则该对象拥有自动[存储期]({{< ref "/c/language/declarations/storage_duration" >}})（此情况下对象的[生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})结束于外围块的结尾）。(C23 前)

​	若复合字面量在函数体之外且在任何形参列表之外求值，则它与文件作用域关联；否则，它与其外围块相关联。存储类说明符序列（可能为空）、类型名和初始化式列表（如果有），依据这项关联，应当分别对于文件作用域或块作用域中的具有以下形式的虚构的对象定义而言是有效的说明符：(C23 起)

*存储类说明符序列* *类型* `typeof(` *类型* `)` *ID* `=` `{` *初始化器列表* `}` `;`

​	其中 *ID* 为对于整个程序唯一的标识符。复合字面量提供一个无名对象，其值、类型、存储类和其他性质如同以上定义语法所给出的一样；如果是自动存储期，则该无名对象的实例的生存期为其外围块的当前执行。如果存储类说明符序列包含除 `constexpr`、`static`、`register` 或 [thread_local](http://zh.cppreference.com/w/c/thread/thread_local) 之外的说明符，则其行为未定义。

## 注解

​	`const` 限定的字符或宽字符数组类型的复合字面量，可能会与[字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})共享存储。

```c
(const char []){"abc"} == "abc" // 可以为 1 或 0，未指定
```

​	每个复合字面量仅在其作用域内创建一个对象：

```c
#include <assert.h>
 
int main(void)
{
    struct S
    {
        int i;
    }
    *p = 0, *q;
    int j = 0;
again:
    q = p,
    p = &((struct S){ j++ }); // 创建 S 类型的无名对象，
                              // 将之初始化为 j 之前持有的值，
                              // 然后将此无名对象的地址赋给指针 p
    if (j < 2)
        goto again; // 注意：若使用循环，则其作用域会结束于此，
                    // 这会终止复合字面量的生存期，
                    // 遗留 p 为悬垂指针
    assert(p == q && q->i == 1);
}
```

​	因为复合字面量是无名的，一个复合字面量不能在自己的初始化器中引用自身（一个具名结构体可以包含指向其自身的指针）。

​	复合字面量的语法和[转型]({{< ref "/c/language/expressions/cast" >}})相似，其重要的区别是转型是非左值表达式，而复合字面量是左值。

## 示例

```c
#include <stdio.h>
 
int *p = (int[]){2, 4}; // 创建一个无名的 int[2] 类型静态存储数组
                        // 将数组初始化为值 {2, 4}
                        // 创建指向数组首元素的指针 p
const float *pc = (const float []){1e0, 1e1, 1e2}; // 只读复合字面量
 
struct point {double x,y;};
 
int main(void)
{
    int n = 2, *p = &n;
    p = (int [2]){*p}; // 创建一个无名的 int[2] 类型自动存储数组
                       // 初始化首个元素为之前 *p 所持有的值
                       // 初始化第二个元素为零
                       // 将首元素的地址存储到 p
 
    void drawline1(struct point from, struct point to);
    void drawline2(struct point *from, struct point *to);
    drawline1((struct point){.x=1, .y=1},  // 创建二个块作用域的结构体
              (struct point){.x=3, .y=4}); // 然后调用 drawline1，按值传递它们
    drawline2(&(struct point){.x=1, .y=1},  // 创建二个块作用域的结构体
              &(struct point){.x=3, .y=4}); // 然后调用 drawline2，传递它们的地址
}
 
void drawline1(struct point from, struct point to)
{
    printf("drawline1: `from` @ %p {%.2f, %.2f}, `to` @ %p {%.2f, %.2f}\n",
        (void*)&from, from.x, from.y, (void*)&to, to.x, to.y);
}
 
void drawline2(struct point *from, struct point *to)
{
    printf("drawline2: `from` @ %p {%.2f, %.2f}, `to` @ %p {%.2f, %.2f}\n",
        (void*)from, from->x, from->y, (void*)to, to->x, to->y);
}
```

​	可能的输出：

```txt
drawline1: `from` @ 0x7ffd24facea0 {1.00, 1.00}, `to` @ 0x7ffd24face90 {3.00, 4.00}
drawline2: `from` @ 0x7ffd24facec0 {1.00, 1.00}, `to` @ 0x7ffd24faced0 {3.00, 4.00}
```
