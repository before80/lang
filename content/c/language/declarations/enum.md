+++
title = "枚举"
date = 2025-04-13T10:27:54+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/enum](https://zh.cppreference.com/w/c/language/enum)

​	*枚举类型* ﻿是独立的[类型](https://zh.cppreference.com/w/c/language/types)，其值为包含所有其显示命名的常量（*枚举常量*）的*底层类型* ﻿的值。

## 语法

​	枚举类型在[声明文法]({{< ref "/c/language/declarations" >}})中以跟随的*枚举说明符* ﻿作为*类型说明符* ﻿声明：

| `enum` *属性声明符序列* ﻿(可选) *标识符* ﻿(可选) `{` *枚举项列表* `}` | (1)  |          |
| ------------------------------------------------------------ | ---- | -------- |
| `enum` *属性声明符序列* ﻿(可选) *标识符* ﻿(可选) `:` *类型* `{` *枚举项列表* `}` | (2)  | (C23 起) |

1) 声明没有固定底层类型的枚举。
2) 声明固定底层类型为*类型* ﻿的枚举。

​	其中*枚举项列表* ﻿是*枚举项* ﻿的逗号分隔列表（允许尾随的逗号）(C99 起)，每个*枚举项* ﻿拥有形式：

| *枚举常量* *属性声明符序列* ﻿(可选)                  | (1)  |      |
| --------------------------------------------------- | ---- | ---- |
| *枚举常量* *属性声明符序列* ﻿(可选) `=` *常量表达式* | (2)  |      |

​	其中

| *标识符*, *枚举常量* | -    | 由此声明引入的标识符                                         |
| -------------------- | ---- | ------------------------------------------------------------ |
| *常量表达式*         | -    | [整数常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})，其值可以以 int 类型的值表示。(C23 前)若枚举具有固定底层类型，则其可以表示为*类型* ﻿的值(C23 起) |
| *属性声明符序列*     | -    | (C23)可选的[属性列表]({{< ref "/c/language/declarations/attributes" >}})，若出现在 `enum` 后则应用到整个枚举，若出现在*枚举常量* ﻿ 后则应用到*枚举项* |

​	与[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})一样，引入枚举类型和一或多个枚举常量的声明亦可声明一或多个该类型的对象，或从该类型派生的类型的对象。

```c
enum color_t {RED, GREEN, BLUE} c = RED, *cp = &c;
// 引入类型 enum color_t
// 整数常量 RED 、 GREEN 、 BLUE 
// 对象 c 拥有类型 enum color_t
// 对象 cp 的类型为指向 enum color_t 的指针
```

## 解释

​	每个出现于枚举说明符体中的*枚举常量* ﻿会成为 int 类型的(C23 前)[整数常量]({{< ref "/c/language/expressions/constant_expression" >}})，并处于包围它的作用域中，而且在凡要求整数常量处可用（例如，作为 case 标号或非 VLA 数组大小）。

在处理枚举项列表中的每个枚举常量过程中，枚举常量的类型应当为：(C23 起)

- 之前声明的类型，若此为相同枚举常量的重声明；或者，
- 对于带有固定底层类型的枚举，则为枚举所用类型；或者，
- int，若枚举项列表中没有更早的枚举常量且没有提供定义的整数常量表达式的明确 =；或者，
- int，若给出了明确的 = 且整数常量表达式的值可以表示为 int；或者，
- 整数常量表达式的类型，若给出了明确的 = 并且整数常量表达式的值无法表示为 int；或者，
- 最后一个没寄出来的值加上 1 的值的类型。如果这种整数常量表达式对于前一个枚举常量加 1 的值会发生溢出或回绕，则其类型为以下之一：
  - 适当大小的有符号整数类型（不包括位精确有符号整数类型），有能力表示前一个枚举常量加 1 的值；或者
  - 适当大小的无符号整数类型（不包括位精确无符号整数类型），有能力表示前一个枚举常量加 1 的值。

​	当被加的前一个枚举常量为有符号整数类型时，选用有符号整数类型。当被加的前一个枚举常量为无符号整数类型时，选用无符号整数类型。如果不存在前述可以表示新值的合适的有符号整数类型，则该枚举没有有能力表示其所有值的类型。

```c
enum color { RED, GREEN, BLUE } r = RED;
switch(r)
{
case RED:
    puts("red");
    break;
case GREEN:
    puts("green");
    break;
case BLUE:
    puts("blue");
    break;
}
```

​	若*枚举常量* ﻿后随*= 常量表达式* ﻿，则其值为该常量表达式的值。若*枚举常量* ﻿没有后随*=常量表达式* ﻿ ，则其值是比同一枚举中前一枚举项的值大一的值。首个枚举项（若它不用 `= 常量表达式`）的值是零。

```c
enum Foo { A, B, C = 10, D, E = 1, F, G = F + C};
// A=0, B=1, C=10, D=11, E=1, F=2, G=12
```

​	若使用*标识符* ﻿，则其自身成为标签[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})中枚举类型的名称，且需要使用关键词 `enum` （除非 `typedef` 到通常命名空间）。

```c
enum color { RED, GREEN, BLUE };
enum color r = RED; // OK
// color x = GREEN; // 错误： color 不在通常命名空间中
typedef enum color color_t;
color_t x = GREEN; // OK
```

​	每个无固定底层类型的(C23 起)枚举类型与如下之一[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)：`char`、有符号整数类型或无符号整数类型（不包括 `bool` 和位精确整数类型）(C23 起)。对于任何枚举类型，哪一个类型是兼容的是实现定义的，但无论是那种类型，都必须有足以表示该枚举中所有枚举项的值。对于所有具有固定底层类型的枚举，枚举的类型均与枚举的底层类型兼容。(C23 起)

​	没有固定底层类型的枚举类型，在其完成处枚举成员的类型为：(C23 起)

- 如果枚举的所有值均可表示为一个 `int` 则为 `int`；否则，
- 所枚举的类型。

​	所有枚举均有底层类型。可以通过用 *enum-类型说明符* 显式指定底层类型，并作为其固定底层类型。如果未显示指定，则其底层类型为枚举的兼容类型，它为有符号或无符号的整数类型或 `char`。(C23 起)

​	枚举类型是整数类型，从而可以用于任何其他整数类型能用之处，包括[隐式转换]({{< ref "/c/language/expressions/conversion" >}})和[算术运算符]({{< ref "/c/language/expressions/operator_arithmetic" >}})。

```c
enum { ONE = 1, TWO } e;
long n = ONE; // 提升
double d = ONE; // 转换
e = 1.2; // 转换，e 现在是 ONE
e = e + 1; // e 现在是 TWO
```

## 注解

​	不同于 [struct]({{< ref "/c/language/declarations/struct" >}}) 或 [union]({{< ref "/c/language/declarations/union" >}}) ， C 中没有 enum 的前置声明：

```
enum Color; // 错误：C 中无 enum 的前置声明
enum Color { RED, GREEN, BLUE };
```

​	枚举允许以比 `#define` 更加便利和结构化的方式生成具名常量；它们可见于调试器，遵循作用域规则，并且参与类型系统。

```c
#define TEN 10
struct S { int x : TEN; }; // OK
```

或

```c
enum { TEN = 10 };
struct S { int x : TEN; }; // 也 OK
```

自 C23 起也可用 [constexpr](https://zh.cppreference.com/w/c/language/constexpr) 来达成相同目的：

```c
constexpr int TEN = 10;
struct S { int x : TEN; }; // 也 OK
```

​	另外，由于 C 中[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})不建立其作用域，可以在前者的成员说明中引入枚举类型及其枚举常量，而之后其作用域与前者相同。

```c
struct Element
{
    int z;
    enum State { SOLID, LIQUID, GAS, PLASMA } state;
} oxygen = { 8, GAS };
// 类型 enum State 与其枚举常量于此保持可见，例如
void foo(void) {
    enum State e = LIQUID; // OK
    printf("%d %d %d ", e, oxygen.state, PLASMA); // 打印 1 2 3
}
```

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    enum TV { FOX = 11, CNN = 25, ESPN = 15, HBO = 22, MAX = 30, NBC = 32 };
 
    printf("List of cable stations:\n");
    printf(" FOX: \t%2d\n", FOX);
    printf(" HBO: \t%2d\n", HBO);
    printf(" MAX: \t%2d\n", MAX);
}
```

输出：

```txt
List of cable stations:
  FOX:   11
  HBO:   22
  MAX:   30
```

## 关键词

[`enum`](https://zh.cppreference.com/w/c/keyword/enum)

## 参阅

枚举声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/enum)
