+++
title = "offsetof"
date = 2025-04-14T15:54:58+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/offsetof](https://zh.cppreference.com/w/c/types/offsetof)

| 在标头 `<stddef.h>` 定义                          |      |      |
| ------------------------------------------------- | ---- | ---- |
| `#define offsetof(type, member) /* 由实现定义 */` |      |      |

​	宏 **offsetof** 展开成 [size_t]({{< ref "/c/types/size_t" >}}) 类型的[整数常量表达式]({{< ref "/c/language/expressions/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})，其值为从指定类型对象起始到其指定子对象的偏移，若填充存在则包含之。

​	给定拥有静态存储期的 `type` 类型对象 `o`，`&(o.member)` 应当为地址常量表达式并指向 `o` 的子对象。否则行为未定义。

​	若在 `type` 中指定的类型含有不在匹配的括号中的逗号，则行为未定义。(C23 起)

## 注解

​	若将 `offsetof` 应用到位域成员，则行为未定义，因为不能取位域的地址。

​	不限制 `member` 为直接成员。它能指代给定成员的子对象，例如数组成员的元素。

​	尽管 C23 中指定在 `offsetof` 中指定含有不带括号的逗号的新类型为未定义行为，这种用法在较早模式的实现中通常不支持：`offsetof(struct Foo { int a, b; }, a)` 通常不能编译。

​	[`typeof`](https://zh.cppreference.com/w/c/language/typeof) 能用于避免在新类型定义中的逗号的坏效果，例如 `offsetof(typeof(struct { int i, j; }), i)` 为良定义。(C23 起)

## 示例

```c
#include <stdio.h>
#include <stddef.h>
 
struct S {
    char c;
    double d;
};
 
int main(void)
{
    printf("the first element is at offset %zu\n", offsetof(struct S, c));
    printf("the double is at offset %zu\n", offsetof(struct S, d));
}
```

​	可能的输出：

```txt
the first element is at offset 0
the double is at offset 8
```

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为             | 正确行为                 |
| ------------------------------------------------------------ | ------ | ------------------------ | ------------------------ |
| [DR 496](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_496) | C89    | 仅提及结构体与结构体成员 | 亦支持联合体与其他子对象 |

## 参阅

| [size_t]({{< ref "/c/types/size_t" >}})       | [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 运算符返回的无符号整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **offsetof** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/offsetof)** |                                                              |
