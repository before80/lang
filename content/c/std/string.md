+++
title = "<string.h>"
date = 2025-04-16T14:16:24+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型








### size_t

原址：[https://zh.cppreference.com/w/c/types/size_t]({{< ref "/c/types/size_t" >}})

```c
typedef /* 由实现定义 */ size_t;
```

​	`size_t` 是 [offsetof]({{< ref "/c/types/offsetof" >}})、[`<izeo>`]({{< ref "/c/language/expressions/sizeof" >}}) 和 `_Alignof`(C23 前)`alignof`(C23 起) 的结果的无符号整数类型，定义取决于[数据模型]({{< ref "/c/language/basic_concepts/arithmetic_types#.E6.95.B0.E6.8D.AE.E6.A8.A1.E5.9E.8B" >}})。

​	`size_t` 的位宽不小于 16。(C99 起)

**注解**

​	`size_t` 能存储理论上可行的任何类型（包括数组）对象的最大大小。

​	`size_t` 通常用于数组下标和循环计数。将如 unsigned int 的其他类型用作数组下标的的程序，可能譬如在 64 位系统上，当下标超过 [UINT_MAX]({{< ref "/c/types/limits" >}}) 时，或若其依赖 32 位模算术时失败。

**可能的实现**

```c
typedef typeof(sizeof(0)) size_t; // C23 起合法
```

**示例**



```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const size_t N = 101;
    int numbers[N];
    size_t sum = 0;
    for (size_t ndx = 0; ndx < N; ++ndx)
        sum += numbers[ndx] = ndx;
    size_t size = sizeof numbers;
    printf("sum = %zu\n", sum);
    printf("size = %zu\n", size);
    printf("SIZE_MAX = %zu\n", SIZE_MAX);
}
```

​	可能的输出：

```txt
sum = 5050
size = 400
SIZE_MAX = 18446744073709551615
```

## 宏








### NULL

原址：[https://zh.cppreference.com/w/c/types/NULL]({{< ref "/c/types/NULL" >}})

```c
#define NULL /* 由实现定义 */
```

​	宏 `NULL` 是实现定义的空指针常量，可为

- 值为 0 的整数[常量表达式]({{< ref "/c/language/expressions/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})
- [转换为]({{< ref "/c/language/expressions/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2" >}}) void* 的值为 0 的整数常量表达式
- 预定义常量 [`<ullpt>`]({{< ref "/c/language/expressions/nullptr" >}})(C23 起)

​	空指针常量能[转换]({{< ref "/c/language/expressions/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2" >}})为任何指针类型；转换结果是该类型的空指针值。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/stddef.h.html) `NULL` 被定义为转换为 void* 的值为 0 的整数常量表达式。

**可能的实现**

```C
// 兼容 C++： #define NULL 0 // 不兼容 C++： #define NULL (10*2 - 20) #define NULL ((void*)0) // C23 起（与 C++11 及之后兼容） #define NULL nullptr
```

**示例**



```c
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 任何类型的指针均能设为 NULL
    int* p = NULL;
    struct S *s = NULL;
    void(*f)(int, double) = NULL;
    printf("%p %p %p\n", (void*)p, (void*)s, (void*)(long)f);
 
    // 多数返回指针的函数用空指针指示错误
    char *ptr = malloc(0xFULL);
    if (ptr == NULL)
        printf("Out of memory");
    else
        printf("ptr = %#" PRIxPTR"\n", (uintptr_t)ptr);
    free(ptr);
}
```

​	可能的输出：

```txt
(nil) (nil) (nil)
ptr = 0xc001cafe
```

## 函数
