+++
title = "自增/自减运算符"
date = 2025-04-12T21:17:07+08:00
weight = 200
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_incdec](https://zh.cppreference.com/w/c/language/operator_incdec)

​	自增/自减运算符是使对象的值增加/减少 1 的一元运算符。

​	它们能拥有后缀形式：

| *表达式* `++` |
| ------------- |
| *表达式* `--` |

​	还有前缀形式：

| `++` *表达式* |
| ------------- |
| `--` *表达式* |

​	前缀和后缀自增或自减的操作数 *表达式* 必须为[整数类型]({{< ref "/c/language/basic_concepts/type" >}})（包含 `_Bool` 和枚举）、实浮点数类型或指针类型的[可修改左值]({{< ref "/c/language/expressions/value_category" >}})。它可被 cvr 限定、无限定或为[原子的]({{< ref "/c/language/declarations/atomic" >}})。

​	后缀自增和自减运算符的结果是 *表达式* 的值。

​	前缀自增运算符的结果是将值 `1` 加到 *表达式* 的值的结果：表达式 `++e` 等价于 `e += 1`。前缀自减运算符的结果从 *表达式* 减去值 `1` 的结果：表达式 `--e` 等价于 `e -= 1`。

​	自增运算符发动向操作数加以相应类型的值 `1` 的副效应。自减运算符发动从操作数减去相应类型的值 `1` 的副效应。同其他副效应，这些操作在下个[序列点]({{< ref "/c/language/expressions/eval_order" >}})或那之前完成。

```c
int a = 1;
int b = a++; // 存储 1+a （即 2）到 a
             // 返回 a 的旧值（即 1）
             // 此行后，b == 1 而 a == 2
a = 1;
int c = ++a; // 存储 1+a （即 2）到 a
             // 返回 1+a （即 2）
             // 此行后，c == 2 而 a == 2
```

​	任何[原子对象]({{< ref "/c/language/declarations/atomic" >}})上的后缀自增或后缀自减运算符，是拥有 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 内存顺序的原子读改写操作。(C11 起)

​	指针算术上的限制，还有应用于操作数的隐式转换见[算术运算符]({{< ref "/c/language/expressions/operator_arithmetic" >}})。

## 注意

​	因为涉及副效应，必须谨慎地使用自增和自减运算符，以避免违背[定序规则]({{< ref "/c/language/expressions/eval_order" >}})所致的未定义行为。

​	自增/自减运算符不对复数或虚数类型定义：加/减实数 1 的通常定义对虚数会无效，而使之对虚数加/减 `i` 但对复数加/减 `1`，会使得处理 `0+yi` 和 `yi` 的方式有别。

​	不同于 C++（和 C 的某些实现），自增/自减运算符自身决非左值：`&++a` 是非法的。

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int a = 1;
    int b = 1;
 
    printf("original values: a == %d, b == %d\n", a, b);
    printf("result of postfix operators: a++ == %d, b-- == %d\n", a++, b--);
    printf("after postfix operators applied: a == %d, b == %d\n", a, b);
    printf("\n");
 
    // 重置 a 与 b 。
    a = 1;
    b = 1;
 
    printf("original values: a == %d, b == %d\n", a, b);
    printf("result of prefix operators: ++a == %d, --b == %d\n", ++a, --b);
    printf("after prefix operators applied: a == %d, b == %d\n", a, b);
}
```

输出：

```txt
original values: a == 1, b == 1
result of postfix operators: a++ == 1, b-- == 1
after postfix operators applied: a == 2, b == 0
 
original values: a == 1, b == 1
result of prefix operators: ++a == 2, --b == 0
after prefix operators applied: a == 2, b == 0
```

## 参阅

自增/自减运算符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_incdec)
