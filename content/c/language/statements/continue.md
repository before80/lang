+++
title = "continue 语句"
date = 2025-04-12T16:24:17+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/continue](https://zh.cppreference.com/w/c/language/continue)

​	导致跳过整个 [for](https://zh.cppreference.com/w/c/language/for)、 [while](https://zh.cppreference.com/w/c/language/while) 或 [do-while](https://zh.cppreference.com/w/c/language/do) 循环体的剩余部分。

​	在使用条件语句忽略循环剩余部分显得笨拙时使用。

## 语法

​	*属性说明符序列*(可选) `continue` `;`

| *属性说明符序列* | -    | (C23)可选的[属性](https://zh.cppreference.com/w/c/language/attributes)列表，应用到 `continue` 语句 |
| ---------------- | ---- | ------------------------------------------------------------ |

## 解释

​	`continue` 语句导致如同用 [goto](https://zh.cppreference.com/w/c/language/goto) 跳转到循环体的结尾（它仅能出现在 [for](https://zh.cppreference.com/w/c/language/for)、 [while](https://zh.cppreference.com/w/c/language/while) 及 [do-while](https://zh.cppreference.com/w/c/language/do) 的循环体内）。

​	对于 [while](https://zh.cppreference.com/w/c/language/while) 循环，它表现为

```c
while (/* ... */) {
   // ... 
   continue; // 表现为 goto contin;
   // ... 
   contin:;
}
```

​	对于 [do-while](https://zh.cppreference.com/w/c/language/do) 循环，它表现为：

```c
do {
    // ... 
    continue; // 表现为 goto contin;
    // ... 
    contin:;
} while (/* ... */);
```

​	对于 [for](https://zh.cppreference.com/w/c/language/for) 循环，它表现为：

```c
for (/* ... */) {
    // ... 
    continue; // 表现为 goto contin;
    // ... 
    contin:;
}
```

## 关键词

[`continue`](https://zh.cppreference.com/w/c/keyword/continue)

## 示例

```c
#include <stdio.h>
 
int main(void) 
{
    for (int i = 0; i < 10; i++) {
        if (i != 5) continue;
        printf("%d ", i);             // 每次 i != 5 时跳过此语句
    }
 
    printf("\n");
 
    for (int j = 0; j < 2; j++) {
        for (int k = 0; k < 5; k++) { // 只有此循环受 continue 影响
            if (k == 3) continue;
            printf("%d%d ", j, k);    // 每次 k == 3 时跳过此语句
        }
    }
}
```

输出：

```txt
5
00 01 02 04 10 11 12 14
```

## 参阅

**`continue` 语句**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/continue)**