+++
title = "goto 语句"
date = 2025-04-12T16:28:02+08:00
weight = 100
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/goto](https://zh.cppreference.com/w/c/language/goto)

​	将控制无条件转移到所欲位置。

​	在无法用约定的构造将控制转移到所欲位置时使用。

## 语法

​	*属性说明符序列*(可选) `goto` *标号* `;`

| *标号*           | -    | `goto` 语句的目标[标号](https://zh.cppreference.com/w/c/language/statements#.E6.A0.87.E5.8F.B7) |
| ---------------- | ---- | ------------------------------------------------------------ |
| *属性说明符序列* | -    | (C23)可选的[属性](https://zh.cppreference.com/w/c/language/attributes)列表，应用到 `goto` 语句 |

## 解释

​	`goto` 语句导致无条件跳转（控制的转移）到前附具名 *标号* （必须与 goto 语句出现于同一函数中）的语句，除非此跳转会进入[非常量长度数组（VLA）](https://zh.cppreference.com/w/c/language/array)或另一[可变修改（VM）类型](https://zh.cppreference.com/w/c/language/declarations)的作用域(C99 起)。

​	*标号* 是一个后随冒号（`:`）和一条语句(C23 前)的标识符。标号是仅有的拥有*函数作用域*的标识符：能在其所出现于的函数中的任何位置使用它们（在 goto 语句中）。任何语句前可以有多个标号。

(C99 起)

```c
goto lab1; // OK：进入常规变量的作用域
    int n = 5;
lab1:; // 注意未初始化 n，如同以 int n; 声明
 
//   goto lab2;   // 错误：进入二个 VM 类型的作用域
     double a[n]; // VLA
     int (*p)[n]; // VM 指针
lab2:
```

​	若 `goto` 离开 VLA 的作用域，则 VLA 会被解分配（而且可能会被再分配，若再度执行其初始化）：

```c
{
   int n = 1;
label:;
   int a[n]; // 重分配 10 次，每次拥有不同的大小
   if (n++ < 10) goto label; // 离开 VM 的作用域
}
```



## 关键词

​	[`goto`](https://zh.cppreference.com/w/c/keyword/goto)

## 注解

​	因为声明不是语句，在声明前的标号必须使用空语句（紧随冒号后的分号）。同样的规则适用于块结尾前的标号。(C23 前)

​	C++ 在 `goto` 语句上加上了另外的限制，不过允许标号在声明（它们在 C++ 中是语句）前。

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    // goto 可用于简单地离开多层循环
    for (int x = 0; x < 3; x++) {
        for (int y = 0; y < 3; y++) {
            printf("(%d;%d)\n",x,y);
            if (x + y >= 3) goto endloop;
        }
    }
endloop:;
}
```

输出：

```txt
(0;0)
(0;1)
(0;2)
(1;0)
(1;1)
(1;2)
```

## 参阅

**`goto` 语句**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/goto)**