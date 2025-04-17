+++
title = "结构体声明"
date = 2025-04-13T10:31:52+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/struct](https://zh.cppreference.com/w/c/language/struct)

​	结构体是一种由一序列的成员组成的类型，成员的存储以顺序分配于内存中（与联合体相反，联合体是由一个序列的成员组成的类型，成员存储在内存中重叠）。

​	结构体的[类型说明符]({{< ref "/c/language/declarations" >}})与[联合体（`union`）]({{< ref "/c/language/declarations/union" >}})类型说明符相同，只是所用的关键词有别。

## 语法

| `struct` *属性说明符序列* ﻿(可选) *名字* ﻿(可选) `{` *结构体声明列表* `}` | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `struct` *属性说明符序列* ﻿(可选) *名字*                      | (2)  |      |

1) 结构体定义：引入一个新类型 `struct` *名字* ﻿并定义其含义
2) 若仅在其自身的行使用，如在 `struct` *名字* ﻿`;` 中，*声明* ﻿但不定义 struct `名字`（见下方前置声明）。在其他语境中，命名先前声明的结构体，并且不允许*属性说明符序列* ﻿。

| *名字*           | -    | 正在定义的结构体名称                                         |
| ---------------- | ---- | ------------------------------------------------------------ |
| *结构体声明列表* | -    | 任意数量的变量声明、[位域]({{< ref "/c/language/declarations/bit_field" >}})声明和[静态断言](https://zh.cppreference.com/w/c/language/static_assert)声明。不允许不完整类型的成员和函数类型的成员（除了下面描述的柔性数组成员） |
| *属性说明符序列* | -    | (C23)[属性]({{< ref "/c/language/declarations/attributes" >}})的可选列表，应用到结构体类型 |

## 解释

​	在结构体对象内，其成员的地址（及位域分配单元的地址）按照成员定义的顺序递增。可以把指向结构体的指针转换为指向其首成员（或者若首成员为位域，则指向其分配单元）的指针。类似地，能转换指向结构体首成员的指针为指向整个结构体的指针。在任意两个成员间和最后的成员后可能存在无名的填充字节，但首成员前不会有。结构体的大小至少与其成员的大小之和一样大。

​	若结构体定义了至少一个具名成员，则可以额外声明拥有不完整的数组类型的最后一个成员，称为柔性数组成员。访问柔性数组成员的元素时（在以柔性数组成员名作为 `.` 或 `->` 的右侧运算数的表达式中），结构体表现得如同该数组成员拥有为此结构体对象分配的内存的除结构体其他成员占用的以外的部分，即额外分配的存储。若未分配额外存储，则它表现为如同有 1 个元素的数组，但若访问该元素，或产生指向该元素后一位置指针，则行为未定义。初始化、赋值运算符会忽略柔性数组成员。sizeof 含有柔性数组成员的结构体的结果是除去柔性数组成员以外的结构体的大小，但是含有柔性数组成员的结构体除去柔性数组成员的部分可能比不含柔性数组成员的结构体有更多的尾部填充字节。拥有柔性数组成员的结构体（或拥有可能递归的有柔性数组成员的结构体成员的联合体）不能作为数组元素，或其他结构体的成员出现。(C99 起)

```c
struct s { int n; double d[]; }; // s.d 是柔性数组元素 
 
struct s t1 = { 0 };          // OK：d 如同为 double d[1]，但访问是 UB
struct s t2 = { 1, { 4.2 } }; // 错误：初始化忽略柔性数组
 
// 若 sizeof (double) == 8
struct s *s1 = malloc(sizeof (struct s) + 64); // 如同 d 为 double d[8]
struct s *s2 = malloc(sizeof (struct s) + 40); // 如同 d 为 double d[5]
 
s1 = malloc(sizeof (struct s) + 10); // 现在如同 d 为 double d[1]
double *dp = &(s1->d[0]);    // OK
*dp = 42;                    // OK
s1->d[1]++;                  // 未定义行为，不能将超出的两字节作为 double 访问。
 
s2 = malloc(sizeof (struct s) + 6);  // 同上，但访问为 UB，因为缺少
                                     // 两个字节作为完整的 double
dp = &(s2->d[0]);            //  OK，获取地址没问题
*dp = 42;                    //  未定义行为
 
*s1 = *s2; // 只复制 s.n，没有任何 s.d 的元素
           // 除了 sizeof (struct s) 中捕获的元素
```

​	类似联合体，类型为不带*名字* ﻿的结构体的无名结构体成员被称作*匿名结构体*。每个匿名结构体的成员被认为是外围结构体或联合体的成员。若外围结构体或联合体亦为匿名，则递归应用此规则。(C11 起)

```c
struct v {
   union { // 匿名联合体
      struct { int i, j; }; // 匿名结构体
      struct { long k, l; } w;
   };
   int m;
} v1;
 
v1.i = 2;   // 合法
v1.k = 3;   // 非法：内层结构体非匿名
v1.w.k = 5; // 合法
```

​	类似联合体，若不以任何具名成员定义结构体（包含经由匿名嵌套结构体或联合体获得的成员），则程序行为未定义。

## 前置声明

下列形式的声明：

​	`struct` *属性说明符序列* ﻿(可选) *名字* ﻿`;`

​	隐藏任何先前在标签命名空间中声明的*名字* ﻿的含义，并在当前作用域中声明*名字* ﻿为新的结构体名，可以在之后定义该结构体。在定义出现之前，此结构体名拥有[不完整类型](https://zh.cppreference.com/w/c/language/types#.E4.B8.8D.E5.AE.8C.E6.95.B4.E7.B1.BB.E5.9E.8B)。

​	这允许结构体彼此引用：

```c
struct y;
struct x { struct y *p; /* ... */ };
struct y { struct x *q; /* ... */ };
```

​	注意，亦可只用在另一声明中使用 struct 标签引入新的结构体名，但若先前声明的拥有同名的结构体存在于标签[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})中，则标签会指代该名称

```c
struct s* p = NULL; // 标签命名一个位置结构体，声明它
struct s { int a; }; // p 所指向的结构体的定义
void g(void)
{
    struct s; // 新的局部 struct s 的前置声明
              // 它隐藏全局 struct s 直至此块结束
    struct s *p;  // 指向局部 struct s 的指针
                  // 若无上面的前置声明，则它会指向文件作用域的 s
    struct s { char* p; }; // 局部 struct s 的定义
}
```

## 关键词

[`struct`]({{< ref "/c/language/keyword/struct" >}})

## 注解

​	涉及结构体初始化式的规则，见[结构体初始化]({{< ref "/c/language/initialization/struct_initialization" >}})。

​	因为不允许不完整类型的成员，而且结构体类型在其定义结束前不完整，故结构体不能拥有其自身类型的成员。指向其自身类型的指针成员是允许的，而且这通常用于实现链表或树的节点。

​	因为结构体声明不建立[作用域]({{< ref "/c/language/basic_concepts/scope" >}})，故在*结构体声明列表* ﻿中引入的嵌套类型、枚举及枚举项会在定义结构体的外围作用域可见。

## 示例

```c
#include <stddef.h>
#include <stdio.h>
 
int main(void)
{
    // 声明结构体类型
    struct car
    {
        char *make;
        int year;
    };
    // 声明并初始化之前声明的结构体类型的对象
    struct car c = {.year = 1923, .make = "Nash"};
    printf("Car: %d %s\n", c.year, c.make);
 
    // 声明结构体类型、该类型的对象和指向它的指针
    struct spaceship
    {
        char *model;
        int max_speed;
    } ship = {"T-65 X-wing starfighter", 1050},
    *pship = &ship;
    printf("Spaceship: %s. Max speed: %d km/h\n\n", ship.model, ship.max_speed);
 
    // 地址以定义顺序递增，可能插入填充字节
    struct A {char a; double b; char c;};
    printf(
        "Offset of char a = %zu\n"
        "Offset of double b = %zu\n"
        "Offset of char c = %zu\n"
        "Size of struct A = %zu\n\n",
        offsetof(struct A, a),
        offsetof(struct A, b),
        offsetof(struct A, c),
        sizeof(struct A)
    );
    struct B {char a; char b; double c;};
    printf(
        "Offset of char a = %zu\n"
        "Offset of char b = %zu\n"
        "Offset of double c = %zu\n"
        "Size of struct B = %zu\n\n",
        offsetof(struct B, a),
        offsetof(struct B, b),
        offsetof(struct B, c),
        sizeof(struct B)
    );
 
    // 能转换指向结构体的指针为指向其首成员的指针，反之亦然
    char* pmake = (char *)pship;
    pship = (struct spaceship *)pmake;
}
```

可能的输出：

```c
Car: 1923 Nash
Spaceship: T-65 X-wing starfighter. Max speed: 1050 km/h
 
Offset of char a = 0
Offset of double b = 8
Offset of char c = 16
Size of struct A = 24
 
Offset of char a = 0
Offset of char b = 1
Offset of double c = 8
Size of struct B = 16
```

## 参阅

- [结构体及联合体成员访问]({{< ref "/c/language/expressions/operator_member_access" >}})
- [位域]({{< ref "/c/language/declarations/bit_field" >}})
- [结构体初始化]({{< ref "/c/language/initialization/struct_initialization" >}})

类声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/class)
