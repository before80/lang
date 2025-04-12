+++
title = "if 语句"
date = 2025-04-12T15:09:01+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/if](https://zh.cppreference.com/w/c/language/if)

​	有条件地执行代码。

​	用于仅若某条件为真才执行代码的场合。

## 语法

| *属性说明符序列*(可选) `if (` *表达式* `)` *语句真*          | (1)  |
| ------------------------------------------------------------ | ---- |
| *属性说明符序列*(可选) `if (` *表达式* `)` *语句真* `else` *语句假* | (2)  |

| *属性说明符序列* | -    | (C23)可选的[属性](https://zh.cppreference.com/w/c/language/attributes)列表，应用到 `if` 语句 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *表达式*         | -    | 任何标量类型[表达式](https://zh.cppreference.com/w/c/language/expressions) |
| *语句真*         | -    | 任何[语句](https://zh.cppreference.com/w/c/language/statements)（常为复合语句），若 *表达式* 比较不等于 0 则执行 |
| *语句假*         | -    | 任何[语句](https://zh.cppreference.com/w/c/language/statements)（常为复合语句），若 *表达式* 比较等于 0 则执行 |

## 解释

​	*表达式* 必须为任何[标量类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)的表达式。

​	若 *表达式* 与整数零比较不相等，则执行 *语句真* 。

​	形式 (2) 中，若 *表达式* 与整数零比较相等，则执行 *语句假* 。

​	同所有选择和迭代语句，整个 if 语句拥有其自身的块作用域：(C99 起)

```c
enum {a, b};
int different(void)
{
    if (sizeof(enum {b, a}) != sizeof(int))
        return a; // a == 1
    return b; // C 89中 b == 0 ， C99 中 b == 1
}
```



## 注解

​	`else` 始终与最接近的前接 `if` 相关联（换言之，若 *语句真* 也是 if 语句，则内层 if 必须也含有 `else` 部分）：

```
int j = 1;
if (i > 1)
   if(j > 2)
       printf("%d > 1 and %d > 2\n", i, j);
    else // 此 else 是 if(j>2) 的一部分，不是 if(i>1) 的部分 
       printf("%d > 1 and %d <= 2\n", i, j);
```

​	若通过 [goto](https://zh.cppreference.com/w/c/language/goto) 进入 *语句真* ，则不执行 *语句假* 。

## 关键词

[`if`](https://zh.cppreference.com/w/c/keyword/if), [`else`](https://zh.cppreference.com/w/c/keyword/else)

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    int i = 2;
    if (i > 2) {
        printf("first is true\n");
    } else {
        printf("first is false\n");
    }
 
    i = 3;
    if (i == 3) printf("i == 3\n");
 
    if (i != 3) printf("i != 3 is true\n");
    else        printf("i != 3 is false\n");
}
```

输出：

```txt
first is false
i == 3
i != 3 is false
```

## 参阅

`if` 语句的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/if)