+++
title = "break 语句"
date = 2025-04-12T16:21:52+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/break](https://zh.cppreference.com/w/c/language/break)

​	导致外围 [for]({{< ref "/c/language/statements/for" >}})、[while]({{< ref "/c/language/statements/while" >}}) 或 [do-while]({{< ref "/c/language/statements/do" >}}) 循环或 [switch 语句]({{< ref "/c/language/statements/switch" >}})终止。

​	在用条件表达式和条件语句终止循环显得笨拙时使用。

## 语法

​	*属性说明符序列* ﻿(可选) `break` `;`

| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到 `break` 语句 |
| ---------------- | ---- | ------------------------------------------------------------ |

​	只出现在循环体（[while]({{< ref "/c/language/statements/while" >}})、[do-while]({{< ref "/c/language/statements/do" >}})、[for]({{< ref "/c/language/statements/for" >}})）的 *语句* 内，或 [switch]({{< ref "/c/language/statements/switch" >}}) 的 *语句* 内。

## 解释

​	此语句后，控制被转移到紧随整个循环或 switch 之后的声明或语句，如同由 [goto]({{< ref "/c/language/statements/goto" >}}) 进行。

## 关键词

[`break`]({{< ref "/c/language/keyword/break" >}})

## 注解

​	`break` 语句不能用于打破多重嵌套循环。[`goto` 语句]({{< ref "/c/language/statements/goto" >}})可用于此目的。

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    int i = 2;
    switch (i)
    {
        case 1: printf("1");
        case 2: printf("2");   // i==2 ，故执行始于此 case 标号
        case 3: printf("3");
        case 4:
        case 5: printf("45");
                break;         // 导致后续的 case 终止
        case 6: printf("6");
    }
    printf("\n");
 
    // 比较来自这二个循环嵌套的输出
    for (int j = 0; j < 2; j++)
        for (int k = 0; k < 5; k++)
            printf("%d%d ", j,k);
 
    printf("\n");
 
    for (int j = 0; j < 2; j++)
    {
        for (int k = 0; k < 5; k++) { // 只有此循环会由 break 退出
            if (k == 2)
                break;
            printf("%d%d ", j,k);
        }
    }
}
```

输出：

```txt
2345
00 01 02 03 04 10 11 12 13 14 
00 01 10 11
```

## 参阅

​	[`fallthrough`]({{< ref "/c/language/declarations/attributes/fallthrough" >}})(C23) 指定从前一个 case 标号发生直落是有意的，且不应被会警告直落的编译器进行诊断 (属性指示符)

​	**`break` 语句**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/break)**
