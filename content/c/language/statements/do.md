+++
title = "do-while 循环"
date = 2025-04-12T16:13:15+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/do](https://zh.cppreference.com/w/c/language/do)

​	重复执行 *语句* ，直到条件 *表达式* 的值变为假。此测试在每次迭代后发生。

## 语法

​	属性说明符序列(可选) `do` *语句* `while (` *表达式* `)` `;`

| *表达式*         | -    | 任何[标量类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)的[表达式]({{< ref "/c/language/expressions" >}})。此表达式在每次迭代后求值，而且若它与零比较相等，则退出循环。 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *语句*           | -    | 任何[语句]({{< ref "/c/language/statements" >}})，常为一条复合语句，作为循环体 |
| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到循环语句 |

## 解释

​	`do-while` 语句导致重复执行 *语句* （亦称为*循环体*），直至 *表达式* （亦称为*控制表达式*）与 0 比较相等。不管是正常进入循环体还是以 [goto]({{< ref "/c/language/statements/goto" >}}) 进入 *语句* 内部，都会发生重复。

​	在每次执行 *语句* 后对 *表达式* 求值（无论是正常进入还是用 goto ）。若需要在循环体前求值控制表达式，则可以使用 [while 循环]({{< ref "/c/language/statements/while" >}})或 [for 循环]({{< ref "/c/language/statements/for" >}})。

​	若循环的执行需要在某点终止，则能以 [break 语句]({{< ref "/c/language/statements/break" >}})为终止语句。

​	若循环的执行需要从循环体的结尾继续，则能以 [continue 语句]({{< ref "/c/language/statements/continue" >}})为快捷方式。

​	若无限循环在其 *语句* 或 *表达式* 的任何部分无可观测行为（I/O、volatile 访问、原子或同步操作），则拥有这种循环的程序有未定义行为。这允许编译器优化掉整个不可观测循环，而无需证明他们会结束。仅有的例外是 *表达式* 为常量表达式的循环：`do {...} while(true);` 始终是无限循环。

​	同所有选择和迭代语句， do-while 语句建立[块作用域]({{< ref "/c/language/basic_concepts/scope" >}})：任何于 *表达式* 中引入的标识符在语句后离开作用域。(C99 起)

## 注解

​	通常以布尔和指针表达式为控制表达式。布尔值 `false` 和任何指针类型的空指针值与零比较相等。

## 关键词

[`do`]({{< ref "/c/language/keyword/do" >}}), [`while`]({{< ref "/c/language/keyword/while" >}})

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
enum { SIZE = 8 };
int main(void)
{
    // 平凡示例
    int array[SIZE], n = 0;
    do array[n++] = rand() % 2; // 循环体是单条表达式语句
    while(n < SIZE);
    puts("Array filled!");
    n = 0;
    do { // 循环体是复合语句
        printf("%d ", array[n]);
        ++n;
    } while (n < SIZE);
    printf("\n");
 
    // 来自 K&R itoa() 的循环。使用了 do-while 循环
    // 因为始终至少要生成一位
    int num = 1234, i=0;
    char s[10];
    do s[i++] = num % 10 + '0'; // 以反转顺序到下个数位
    while ((num /= 10) > 0);
    s[i] = '\0';
    puts(s);
}
```

​	可能的输出：

```txt
Array filled!
1 0 1 1 1 1 0 0
4321
```

## 参阅

`do`-`while` 循环的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/do)
