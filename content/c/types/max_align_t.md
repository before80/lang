+++
title = "max_align_t"
date = 2025-04-14T15:53:41+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/max_align_t](https://zh.cppreference.com/w/c/types/max_align_t)

| 在标头 `<stddef.h>` 定义                |      |          |
| --------------------------------------- | ---- | -------- |
| `typedef /* 由实现定义 */ max_align_t;` |      | (C11 起) |

​	`max_align_t` 是对齐要求至少和其他任何一种标量类型一样严格（一样大）的类型。

## 注解

​	如 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 这样的分配函数所返回的指针是为任意对象对齐的，这表示它们至少和 `max_align_t` 一样严格。

## 示例

```c
#include <inttypes.h>
#include <stdalign.h>
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    size_t a = alignof(max_align_t);
    printf("max_align_t 的对齐是 %zu (%#zx)\n", a, a);
 
    void *p = malloc(123);
    printf("从 malloc(123) 获得的地址为 %#" PRIxPTR"\n",
            (uintptr_t)p);
    free(p);
}
```

可能的输出：

```txt
max_align_t 的对齐是 16 (0x10)
从 malloc(123) 获得的地址为 0x1fa67010
```



### 参阅

**max_align_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/max_align_t)**