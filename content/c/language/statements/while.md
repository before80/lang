+++
title = "while 循环"
date = 2025-04-12T16:10:45+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/while](https://zh.cppreference.com/w/c/language/while)

​	重复执行 *语句*，直到 *表达式* 的值变得比较等于零。此测试在每次迭代前发生。

## 语法

​	属性说明符序列(可选) `while (` 表达式  `)` 语句

| *表达式*         | -    | 任何[标量类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)的[表达式]({{< ref "/c/language/expressions" >}})。在每次迭代前求值此表达式，而若它与零比较相等，则退出循环。 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *语句*           | -    | 任何[语句]({{< ref "/c/language/statements" >}})，常为一条复合语句，它被用作循环体 |
| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到循环语句 |

## 解释

​	`while` 导致重复执行 *语句*（亦称为*循环体*），直至 *表达式*（亦称为*控制表达式*）与零比较相等。不管是正常进入循环体还是以 [goto]({{< ref "/c/language/statements/goto" >}}) 进入 *语句* 内部，都会发生重复。

​	*表达式*的求值在每次执行 *语句* 前发生（除非用 goto 进入）。若需要在每次循环体后求值控制表达式，可以用 [do-while 循环]({{< ref "/c/language/statements/do" >}})。

​	若循环的执行需要在某些点终止，则能以 [break 语句]({{< ref "/c/language/statements/break" >}})为作终止语句。

​	若循环的执行需要从循环体的结尾继续，则能以 [continue 语句]({{< ref "/c/language/statements/continue" >}})为快捷方式。

​	若无限循环在其 *语句* 或 *表达式* 的任何部分无可观测行为（I/O、volatile 访问、原子或同步操作），则拥有这种循环的程序有未定义行为。这允许编译器优化掉整个不可观测循环，而无需证明他们会结束。仅有的例外是 *表达式* 为常量表达式的循环：`while(true)` 始终是无限循环。

​	同所有选择和迭代语句，while 语句建立[块作用域]({{< ref "/c/language/basic_concepts/scope" >}})：任何于 *表达式* 中引入的标识符在语句后离开作用域。(C99 起)

## 注解

​	常以布尔和指针表达式为循环控制表达式。布尔值 `false` 和任何指针类型的空指针值与零比较相等。

## 关键词

[`while`]({{< ref "/c/language/keyword/while" >}})

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
enum { SIZE = 8 };
int main(void)
{
    // 平凡示例
    int array[SIZE], n = 0;
    while(n < SIZE) array[n++] = rand() % 2;
    puts("Array filled!");
    n = 0;
    while(n < SIZE) printf("%d ", array[n++]);
    printf("\n");
 
    // 经典的 strcpy() 实现
    // （从 src 复制空终止字符串到 dst）
    char src[]="Hello, world", dst[sizeof src], *p=dst, *q=src;
    while((*p++ = *q++)) // 用双括号（这严格上并不必要）
                         // 抑制警告，确保这有意为
                         // 赋值（而非比较），
                         // 其结果被用作真值
        ; // 空语句
    puts(dst);
}
```

​	输出：

```txt
Array filled!
1 0 1 1 1 1 0 0 
Hello, world
```

## 参阅

**`while` 循环**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/while)**
