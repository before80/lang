+++
title = "C 属性： deprecated (C23 起)"
date = 2025-04-13T11:18:26+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/deprecated](https://zh.cppreference.com/w/c/language/attributes/deprecated)

​	指示声明有此属性的名字或实体被[弃用](https://en.wikipedia.org/wiki/Deprecation)，即允许但因故不鼓励使用。

## 语法

| `[[` `deprecated` `]]` `[[` `__deprecated__` `]]`            | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `[[` `deprecated` `(` *字符串字面量* `)` `]]` `[[` `__deprecated__` `(` *字符串字面量* `)` `]]` | (2)  |      |

| *字符串字面量* | -    | 能用于解释弃用的理由并/或提议代替用实体的文本 |
| -------------- | ---- | --------------------------------------------- |

## 解释

​	指示允许使用以此属性声明的名字或实体，但因某种原因不鼓励使用。编译器通常会对这些使用情况发出警告。若指定 *字符串字面量*，则通常将它包含于警告中。

​	下列名字或实体的声明中允许使用这个属性：

- [结构体](https://zh.cppreference.com/w/c/language/struct)/[联合体](https://zh.cppreference.com/w/c/language/union)：`struct [[deprecated]] S;`，
- [typedef 名](https://zh.cppreference.com/w/c/language/typedef)：`[[deprecated]] typedef S* PS;`，
- 对象：`[[deprecated]] int x;`，
- 结构体/联合体成员：`union U { [[deprecated]] int n; };`，
- [函数](https://zh.cppreference.com/w/c/language/function_definition)：`[[deprecated]] void f(void);`，
- [枚举](https://zh.cppreference.com/w/c/language/enum)：`enum [[deprecated]] E {};`，
- 枚举项：`enum { A [[deprecated]], B [[deprecated]] = 42 };`。

​	声明时未弃用的名字可被重声明为 `deprecated`。声明为 `deprecated` 的名字不能通过不带此属性地重声明而变为未弃用。

## 示例

```c
#include <stdio.h>
 
[[deprecated]]
void TriassicPeriod(void)
{
    puts("Triassic Period: [251.9 - 208.5] million years ago.");
}
 
[[deprecated("Use NeogenePeriod() instead.")]]
void JurassicPeriod(void)
{
    puts("Jurassic Period: [201.3 - 152.1] million years ago.");
}
 
[[deprecated("Use calcSomethingDifferently(int).")]]
int calcSomething(int x)
{
    return x * 2;
}
 
int main(void)
{
    TriassicPeriod();
    JurassicPeriod();
}
```

可能的输出：

```txt
Triassic Period: [251.9 - 208.5] million years ago.
Jurassic Period: [201.3 - 152.1] million years ago.
 
prog.c:23:5: warning: 'TriassicPeriod' is deprecated [-Wdeprecated-declarations]
    TriassicPeriod();
    ^
prog.c:3:3: note: 'TriassicPeriod' has been explicitly marked deprecated here
[[deprecated]]
  ^
prog.c:24:5: warning: 'JurassicPeriod' is deprecated: Use NeogenePeriod() instead. [-Wdeprecated-declarations]
    JurassicPeriod();
    ^
prog.c:9:3: note: 'JurassicPeriod' has been explicitly marked deprecated here
[[deprecated("Use NeogenePeriod() instead.")]]
  ^
2 warnings generated.
```

## 参阅

**deprecated** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/deprecated)**