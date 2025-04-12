+++
title = "转换运算符"
date = 2025-04-12T21:31:05+08:00
weight = 240
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/cast](https://zh.cppreference.com/w/c/language/cast)

进行显式类型转换。

## 语法

| `(` *类型名* `)` *表达式* |      |      |
| ------------------------- | ---- | ---- |

其中

| *类型名* | -    | void 类型或任何[标量类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB) |
| -------- | ---- | ------------------------------------------------------------ |
| *表达式* | -    | 任何[标量类型](https://zh.cppreference.com/w/c/language/type#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)[表达式](https://zh.cppreference.com/w/c/language/expressions)（除非 *类型名*是 void，此情况下它可以是任何表达式） |

## 解释

若 *类型名* 是 void，则 *表达式* 为其副效应求值，并舍弃其返回值，与单独将 *表达式* 用作[表达式语句](https://zh.cppreference.com/w/c/language/statements#.E8.A1.A8.E8.BE.BE.E5.BC.8F.E8.AF.AD.E5.8F.A5)时相同。

否则，若 *类型名* 恰是 *表达式* 的类型，则不做任何事（除非若 *表达式* 拥有浮点数类型，且它表示大于其范围和精度的值——见后述）。

否则，转换 *表达式* 的值为由 *类型名* 所指名的类型，如下：

允许每种[如同赋值的隐式转换](https://zh.cppreference.com/w/c/language/conversion)。

除了隐式转换之外，还允许下列转换规则：

- 任何整数类型能被转换为任何指针类型。但不包括如 [NULL](https://zh.cppreference.com/w/c/types/NULL) 这样的空指针常量（[它们不需要转换](https://zh.cppreference.com/w/c/language/conversion)），结果是实现定义的，可能对齐不准确，可能不指向所引用类型的对象，而且可能是一个[陷阱表示](https://zh.cppreference.com/w/c/language/object)。
- 任何指针类型可以被转换为任何整数类型。结果是实现定义的，即使空指针值也是如此（它们不必得到零值）。若结果不能被表示成目标类型，则行为未定义（无符号整数在从指针转换的情况下不实现模算术）。
- 任何指向对象的指针能被转换为指向任何其他对象类型的指针。若其值未为目标类型正确对齐，则行为未定义。否则，若其值转换回原类型，则它与原值比较相等。若指向对象指针被转换为指向任何字符类型的指针，则结果指向对象的最低字节，且能自增到目标类型的 sizeof （换言之，可用于检验[对象表示](https://zh.cppreference.com/w/c/language/object)，或通过 [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy) 或 [memmove](https://zh.cppreference.com/w/c/string/byte/memmove) 进行复制）。
- 任何指向函数的指针能被转换为指向任何其他函数类型的指针。若将结果指针转换回原类型，则它与原值比较相等。若将转换所得指针用作函数调用，则行为未定义（除非函数类型[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)）。
- 在（指向对象或指向函数的）指针间转换时，若原值是其类型的空指针值，则结果是目标类型的正确空指针值。

在任何场合（执行隐式转换和同类型转换时）中，若 *表达式* 与 *类型名* 是浮点数类型，且 *表达式* 表示大于其类型所指示的范围和精度（见 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) ），则剥除范围和精度以匹配目标类型。

转换表达式的[值类别](https://zh.cppreference.com/w/c/language/value_category)始终是非左值。

## 注解

因为 [`const`](https://zh.cppreference.com/w/c/language/const)、[`volatile`](https://zh.cppreference.com/w/c/language/volatile)、[`restrict`](https://zh.cppreference.com/w/c/language/restrict) 及 [`_Atomic`](https://zh.cppreference.com/w/c/language/atomic) 限定符仅对[左值](https://zh.cppreference.com/w/c/language/value_category)有效，向 cvr 限定或原子类型的转换严格等价于向其对应无限定类型的转换。

转换为 void 在令编译器关于未使用结果的警告沉默时有用。

不允许不列于此的转换。特别是，

- 没有指针和浮点数类型间的转换
- 没有指向函数指针和指向对象指针（含 void*）间的转换

| 若实现提供 [intptr_t](https://zh.cppreference.com/w/c/types/integer) 与/或 [uintptr_t](https://zh.cppreference.com/w/c/types/integer)，则从指向对象类型（包括 *cv* void）的指针转换为这些类型始终良定义。然而这对于函数指针并不保证。 | (C99 起) |
| ------------------------------------------------------------ | -------- |
|                                                              |          |

注意函数指针与对象指针间的转换被许多编译器作为扩展接受，并且为 [POSIX `dlsym()` 函数](https://pubs.opengroup.org/onlinepubs/9699919799/functions/dlsym.html)的一些用法所期待。

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    // 检验对象表示是转换的合法使用
    double d = 3.14;
    printf("The double %.2f(%a) is: ", d, d);
    for(size_t n = 0; n < sizeof d; ++n)
        printf("0x%02x ", ((unsigned char*)&d)[n]);
 
    // edge cases
    struct S {int x;} s;
//    (struct S)s; // 错误；非标量类型
                   // 尽管转换到相同类型什么都不做
    (void)s; // 转换任何类型为 void 都 OK
}
```

可能的输出：

```txt
The double 3.14(0x1.91eb851eb851fp+1) is: 0x1f 0x85 0xeb 0x51 0xb8 0x1e 0x09 0x40
```

## 参阅

**显式类型转换**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/explicit_cast)**