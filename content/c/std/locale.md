+++
title = "<locale.h>"
date = 2025-04-16T14:23:19+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型

## 宏

函数







### NULL

原址：[https://zh.cppreference.com/w/c/types/NULL](https://zh.cppreference.com/w/c/types/NULL)

```c
#define NULL /* 由实现定义 */
```

​	宏 `NULL` 是实现定义的空指针常量，可为

- 值为 0 的整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F)
- [转换为](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2) void* 的值为 0 的整数常量表达式
- 预定义常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr)(C23 起)

​	空指针常量能[转换](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2)为任何指针类型；转换结果是该类型的空指针值。

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

