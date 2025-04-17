+++
title = "switch 语句"
date = 2025-04-12T15:11:50+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/switch](https://zh.cppreference.com/w/c/language/switch)

​	按照整数实参的值执行代码。

​	在需要按照整数值执行多个分支中的一个或数个之处使用。

## 语法

属性说明符序列(可选) `switch (` *表达式* `)` *语句*

| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到 `switch` 语句 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *表达式*         | -    | 任何[整数类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)（`char`、有符号或无符号整数，或枚举）的[表达式]({{< ref "/c/language/expressions" >}}) |
| *语句*           | -    | 任何[语句]({{< ref "/c/language/statements" >}})（典型为复合语句）。允许在 *语句* 中有 `case:` 和 `default:` 标号，而 `break;` 语句拥有特殊含义。 |

| `case` *常量表达式* `:` *语句*                              | (1)  | (C23 前) |
| ----------------------------------------------------------- | ---- | -------- |
| *属性说明符序列*(可选) `case` *常量表达式* `:` *语句*(可选) | (1)  | (C23 起) |
| `default` `:` *语句*                                        | (2)  | (C23 前) |
| *属性说明符序列*(可选) `default` `:` *语句*(可选)           | (2)  | (C23 起) |

| *常量表达式*     | -    | 任何整数[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}}) |
| ---------------- | ---- | ------------------------------------------------------------ |
| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到标号 |

## 解释

​	switch 语句体可拥有任意数量的 `case:` 标号，只要所有 *常量表达式* 的值（在[转换]({{< ref "/c/language/expressions/conversion" >}})到 *表达式* 的[提升后类型]({{< ref "/c/language/expressions/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87" >}})后）各不相同。至多可以存在一个 `default:` 标号（尽管嵌套的 switch 语句可使用其自身的 `default:` 标号，或拥有常量等于外围 switch 所用的 `case:` 的标号）。

​	若 *表达式* 求值为等于一个 *常量表达式* 在转换到 *表达式* 的提升类型后的值，则转移控制到标号为该 *常量表达式* 的语句。

​	若 *表达式* 求值为不匹配任何 `case:` 标号的值，且存在 `default:` 标号，则转移控制到标号为 `default:` 的语句。

​	若 *表达式* 求值为不匹配任何 `case:` 标号的值，且不存在 `default:` 标号，则不执行 switch 体的任何部分。

​	在 *语句* 中的任何位置遇到 [break]({{< ref "/c/language/statements/break" >}}) 语句时，跳出语句体：

```c
switch(1) {
    case 1 : puts("1"); // 打印“1”
    case 2 : puts("2"); // 然后打印“2”（“继续”）
}
```

```c
switch(1) {
    case 1 : puts("1"); // 打印“1”
             break;     // 并退出 switch
    case 2 : puts("2");
             break;
}
```

​	同所有选择和迭代语句，switch 语句建立[块作用域]({{< ref "/c/language/basic_concepts/scope" >}})：任何 *表达式* 的标识符在 *语句* 后离开作用域。若 `case:` 或 `default:` 标号在 VLA 或另一拥有可变修改类型的标识符的作用域内，则整个 switch 语句都必须在其作用域内（换言之，VLA 必须在整个 switch 前或最后的标号后声明）：(C99 起)

```c
switch (expr)
{
        int i = 4; // 非 VLA；声明于此 OK
        f(i); // 决不调用
//      int a[i]; // 错误：VLA 不能声明于此
    case 0:
        i = 17;
    default:;
        int a[i]; // 在此声明 VLA OK
        printf("%d\n", i); // 若 expr == 0 则打印 17，否则打印不确定值
}
```

## 关键词

​	[`switch`]({{< ref "/c/language/keyword/switch" >}}), [`case`]({{< ref "/c/language/keyword/case" >}}), [`default`]({{< ref "/c/language/keyword/default" >}})

## 示例

```c
#include <stdio.h>
 
void func(int x)
{
   printf("func(%d): ", x);
   switch(x)
   {
      case 1: printf("case 1, ");
      case 2: printf("case 2, ");
      case 3: printf("case 3.\n"); break;
      case 4: printf("case 4, ");
      case 5:
      case 6: printf("case 5 or case 6, ");
      default: printf("default.\n");
   }
}
 
int main(void)
{
   for(int i = 1; i < 9; ++i) func(i);
}
```

​	输出：

```txt
func(1): case 1, case 2, case 3.
func(2): case 2, case 3.
func(3): case 3.
func(4): case 4, case 5 or case 6, default.
func(5): case 5 or case 6, default.
func(6): case 5 or case 6, default.
func(7): default.
func(8): default.
```

## 参阅

**`switch` 语句**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/switch)**
