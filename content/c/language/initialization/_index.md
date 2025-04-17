+++
title = "初始化"
date = 2025-04-13T09:46:21+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/initialization](https://zh.cppreference.com/w/c/language/initialization)

​	对象[声明]({{< ref "/c/language/declarations" >}})可以通过名为*初始化* ﻿的步骤提供其初始值。

​	对于每个[声明符]({{< ref "/c/language/declarations" >}})，若不省略初始化式，则它可以是下列之一：

| `= 表达式`           | (1)  |          |
| -------------------- | ---- | -------- |
| `= { 初始化式列表 }` | (2)  |          |
| `= { }`              | (3)  | (C23 起) |

其中*初始化式列表* ﻿是非空的逗号分隔*初始化式* ﻿列表（尾逗号可选），这里每个初始化式拥有三种可能形式之一：

| *表达式*                | (1)  |          |
| ----------------------- | ---- | -------- |
| `{ 初始化器列表 }`      | (2)  |          |
| `{` `}`                 | (3)  | (C23 起) |
| `指派符列表 = 初始化式` | (4)  | (C99 起) |

​	其中*指派符列表* ﻿是形式为 `[ 常量表达式 ]` 的数组指派符的列表，或形式为 `.` *标识符* ﻿的结构体/联合体指派符的列表；见[数组初始化]({{< ref "/c/language/initialization/array_initialization" >}})和[结构体初始化]({{< ref "/c/language/initialization/struct_initialization" >}})。(C99 起)

> 注意 (C99 起)
>
> ​	除了初始化器，花括号环绕的*初始化器列表* ﻿亦可出现于[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})中，它是有下列形式的表达式：
>
> `( 类型 ) { 初始化器列表 }`
>
> `( 类型 ) { }` (C23 起)  



## 解释

​	初始化式指定存储于一个对象中的初始值。

### 显式初始化

​	若提供了初始化式，对于

- 标量类型初始化，见[标量初始化]({{< ref "/c/language/initialization/scalar_initialization" >}})。
- 数组类型初始化，见[数组初始化]({{< ref "/c/language/initialization/array_initialization" >}})。
- 结构体及联合体类型初始化，见[结构体初始化]({{< ref "/c/language/initialization/struct_initialization" >}})。

### 隐式初始化

​	若未提供初始化式：

- 拥有自动[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象将被初始化为不确定值（可能是[陷阱表示]({{< ref "/c/language/basic_concepts/object" >}})）
- 拥有静态及线程局域[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象被空初始化。

### 空初始化

​	若显式以初始化式 `= {}` 初始化对象，则它被空初始化。(C23 起)

​	一些情况下，若未显式初始化对象，则它被空初始化，即：

- 指针被初始化成其类型的空指针值
- 整数类型对象被初始化成无符号的零
- 浮点类型对象被初始化成正零
- 数组的所有元素、结构体的所有成员及联合体的首个成员递归地空初始化，外加将所有填充位初始化为零

（在空指针值和浮点零拥有全零位表示的平台上，静态对象的这种初始化形式普遍以将其分配到程序映像的 .bss 段来实现）



## 注解

​	在初始化静态或线程局域[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象时，每个初始化式中的*表达式* ﻿都必须是[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})或[字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})。

​	初始化式不能用于不完整类型的对象、VLA 及拥有链接的块作用域对象。

​	函数形参的初值如同用从[函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})实参赋值，而非初始化一样建立。

​	若将不确定值用作任何标准库调用的实参，则行为未定义。另外，任意牵涉到不确定值的表达式的值是不确定值（例如 int n;，n 可能与自身比较不相等，并且它在后续读取中的值可能出现更改）。

​	C 中没有对应于 C++ [值初始化](https://zh.cppreference.com/w/cpp/language/value_initialization)的专用语言构造；不过，可以代之以 = {0}（或复合字面量中的 (T){0}）(C99 起)，因为 C 标准不允许空结构体、空联合体或零长度的数组。(C23 前)

​	可以用空初始化式 = {}（或复合字面量中的 (T){}）来达成与 C++ 的[值初始化](https://zh.cppreference.com/w/cpp/language/value_initialization)相同的语义。(C23 起)

## 示例

```c
#include <stdlib.h>
int a[2]; //初始化a为{0, 0}
int main(void)
{
    int i;          // 初始化 i 为不确定值
    static int j;   // 初始化 j 为 0
    int k = 1;      // 初始化 k 为 1
 
    // 初始化 int x[3] 为 1,3,5
    // 初始化 int* p 为 &x[0]
    int x[] = { 1, 3, 5 }, *p = x;
 
    // 初始化 w （二个结构体的数组）为
    // { { {1,0,0}, 0}, { {2,0,0}, 0} }
    struct {int a[3], b;} w[] = {[0].a = {1}, [1].a[0] = 2};
 
    // 函数调用表达式可用于局部变量初始化
    char* ptr = malloc(10);
    free(ptr);
 
//  错误：拥有静态存储期的对象要求常量初始化器
//  static char* ptr = malloc(10);
 
//  错误：不能初始化 VLA
//  int vla[n] = {0};
}
```

## 参阅

**初始化**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/initialization)**
