+++
title = "for 循环"
date = 2025-04-12T16:18:29+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/for](https://zh.cppreference.com/w/c/language/for)

执行循环。

用作 [while 循环](https://zh.cppreference.com/w/c/language/while)的简短等价版本。

## 语法

​	*属性说明符序列*(C23 起) (可选) `for` `(` *初始化子句* `;` *条件表达式* `;` *迭代表达式* `)` *循环语句*

## 解释

​	表现如下：

- *初始化子句* 可以为表达式或声明(C99 起)
  - 作为表达式的 *初始化子句* 在首次求值 *条件表达式* 前被求值一次，并舍弃其结果。
  - 作为声明的 *初始化子句* 在整个循环体内都处于作用域内，包括 *初始化子句* 的剩余部分、整个*条件表达式*、整个 *迭代表达式* 及整个*循环语句*。声明于此声明的变量只允许有 `auto` 和 `register` [存储类说明符](https://zh.cppreference.com/w/c/language/storage_duration)。(C99 起)

- *条件表达式* 在循环体前求值。若表达式的结果是零，则循环立即退出。
- *迭代表达式* 在循环体后求值，并舍弃其结果。求值 *迭代表达式* 后，将控制转移到 *条件表达式*。

​	*初始化子句*、*条件表达式* 和 *迭代表达式* 都是可选的。若忽略 *条件表达式*，则它被替换成非零的整数常量，这使得循环不终止：

```c
for(;;) {
   printf("endless loop!");
}
```

​	*循环语句* 不是可选的，但它可以是空语句：

```c
for(int n = 0; n < 10; ++n, printf("%d\n", n))
    ; // 空语句
```

​	若需要在某些点终止循环的执行，则可在 *循环语句* 中的任何位置使用 [break 语句](https://zh.cppreference.com/w/c/language/break)。

​	*循环语句* 内任何位置使用的 [continue 语句](https://zh.cppreference.com/w/c/language/continue)会将控制转移到*迭代表达式*。

​	若无限循环在其 *条件表达式*、*迭代表达式* 或 *循环语句* 的任何部分无可观测行为（I/O、volatile 访问、原子或同步操作），则拥有这种循环的程序有未定义行为。这允许编译器优化掉整个不可观测循环，而无需证明他们会结束。仅有的例外是 *条件表达式* 被忽略或为常量表达式的循环：`for(;;)` 始终是无限循环。

​	同所有选择和迭代语句，for 语句建立[块作用域](https://zh.cppreference.com/w/c/language/scope)：任何于 *初始化子句*、*条件表达式* 或 *迭代表达式* 中引入的标识符在 *循环语句* 后离开作用域。(C99 起)

​	*属性说明符序列* 是[属性](https://zh.cppreference.com/w/c/language/attributes)的可选序列，应用到 `for` 语句。(C23 起)

## 关键词

[`for`](https://zh.cppreference.com/w/c/keyword/for)

## 注解

​	用作 *循环语句* 的表达式语句建立其自身的，异于 *初始化子句* 作用域的块作用域，不同于 C++：

```c
for (int i = 0; ; ) {
    long i = 1;   // C 中合法， C++ 中非法
    // ...
}
```

​	可以用 [goto](https://zh.cppreference.com/w/c/language/goto) 进入循环体，以此方式进入循环时，不执行 *初始化子句* 和 *条件表达式*。（若控制抵达循环体尾，则可能出现包括执行 *条件表达式* 的重复。）

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
enum { SIZE = 8 };
int main(void)
{
    int array[SIZE];
    for(size_t i = 0 ; i < SIZE; ++i)
        array [i] = rand() % 2;
    printf("Array filled!\n");
    for (size_t i = 0; i < SIZE; ++i)
        printf("%d ", array[i]);
    putchar('\n');
}
```

​	可能的输出：

```txt
Array filled!
1 0 1 1 1 1 0 0
```

## 参阅

**`for` 循环**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/for)**