+++
title = "逻辑运算符"
date = 2025-04-12T20:47:16+08:00
weight = 160
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_logical](https://zh.cppreference.com/w/c/language/operator_logical)

​	逻辑运算符对其操作数应用标准布尔代数运算。

| 运算符 | 运算符名 |   示例   |      结果       |
| :----: | :------: | :------: | :-------------: |
|  `!`   |  逻辑非  |   `!a`   |   a 的逻辑非    |
|  `&&`  |  逻辑与  | `a && b` | a 与 b 的逻辑与 |
|  `||`  |  逻辑或  | `a || b` | a 与 b 的逻辑或 |

## 逻辑非

​	逻辑非表达式的形式为：

`!` *表达式*

​	其中

| *表达式* | -    | 任何[标量类型]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB" >}})的表达式 |
| -------- | ---- | ------------------------------------------------------------ |

​	逻辑非运算符拥有 `int` 类型。若 *expression* 求值为不等于零的整数则其值为 0。若 *expression* 求值为等于零的整数则其值为 1。（故 `!E` 与 (`0==E`) 相同）

```c
#include <stdbool.h>
#include <stdio.h>
#include <ctype.h>
int main(void)
{
    bool b = !(2+2 == 4); // 非 true
    printf("!(2+2==4) = %s\n", b ? "true" : "false");
 
    int n = isspace('a'); // 若 'a' 是空格则为非零，否则为零
    int x = !!n; // "bang-bang"，常用的 C 手法，映射标量为 [0,1]
                 // （所有非零值变为 1 ）
    char *a[2] = {"non-space", "space"};
    puts(a[x]); // 现在能安全地以 x 为 2 个字符串的数组的下标
}
```

​	输出：

```txt
!(2+2==4) = false
non-space
```

## 逻辑与

​	逻辑与表达式的形式为：

*lhs* `&&` *rhs*

​	其中

| *lhs* | -    | 任何标量类型的表达式                                 |
| ----- | ---- | ---------------------------------------------------- |
| *rhs* | -    | 任何标量类型的表达式，仅若 *lhs* 比较不等于 0 才求值 |

​	逻辑与运算符拥有 int 类型，若 *lhs* 与 *rhs* 都比较不等于零则值为 1。否则值为 0（若 *lhs* 或 *rhs* 之一或两者比较等于零）。

​	在 *lhs* 的求值后有[序列点]({{< ref "/c/language/expressions/eval_order" >}})。若 *lhs* 的结果比较等于零，则完全不求值 *rhs*（是谓*短路求值*）。

```c
#include <stdbool.h>
#include <stdio.h>
int main(void)
{
    bool b = 2+2==4 && 2*2==4; // b == true
 
    1 > 2 && puts("this won't print");
 
    char *p = "abc";
    if(p && *p) // 常用的 C 手法：若 p 非空 *且* 若 p 不指向字符串尾
    {           // （注意拜短路求值所赐，这不会试图解引用空指针）
    // ...      // ……然后做一些字符串处理
    }
}
```

## 逻辑或

​	逻辑或表达式的形式为：

*lhs* `||` *rhs*

​	其中

| *lhs* | -    | 任何标量类型的表达式                               |
| ----- | ---- | -------------------------------------------------- |
| *rhs* | -    | 任何标量类型的表达式，仅若 *lhs* 比较等于 0 才求值 |

​	逻辑或运算符拥有 int 类型，而若 *lhs* 或 *rhs* 比较不等于零则值为 1。否则其值为 0（若 *lhs* 与 *rhs* 都比较等于零）。

​	在 *lhs* 的求值后有[序列点]({{< ref "/c/language/expressions/eval_order" >}})。若 *lhs* 的结果比较不等于零，则完全不求值 *rhs*（是谓*短路求值*）。

```c
#include <stdbool.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
int main(void)
{
    bool b = 2+2 == 4 || 2+2 == 5; // true
    printf("true or false = %s\n", b ? "true" : "false");
 
    // 逻辑或能像 perl 的 "or die" 一样使用，只要 rhs 拥有标量类型
    fopen("test.txt", "r") || printf("could not open test.txt: %s\n", strerror(errno));
}
```

​	可能的输出：

```txt
true or false = true
could not open test.txt: No such file or directory
```

## 参阅

逻辑运算符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_logical)
