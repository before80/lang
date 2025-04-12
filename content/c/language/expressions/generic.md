+++
title = "泛型选择 (C11 起)"
date = 2025-04-12T17:18:41+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/generic](https://zh.cppreference.com/w/c/language/generic)

​	提供一种方式，基于控制表达式的类型，在编译时选择数个表达式之一。

## 语法

​	`_Generic` `(` *控制表达式* `,` *关联列表* `) ` (C11 起)

​	其中 *关联列表* 是关联的逗号分隔列表，每项关联的语法为：

| *类型名* `:` *表达式*  |
| ---------------------- |
| `default` `:` *表达式* |

​	其中

| *类型名*     | -    | 任何并非可变修改的完整[对象类型](https://zh.cppreference.com/w/c/language/types)（即既非 VLA 亦非指向 VLA 的指针）。 |
| ------------ | ---- | ------------------------------------------------------------ |
| *控制表达式* | -    | 任何表达式（除了[逗号运算符](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)），若不使用 `default` 关联，则其类型必须与 *类型名* 之一兼容 |
| *表达式*     | -    | 任何类型和值类别的表达式（除了[逗号运算符](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)） |

​	*关联列表* 中的任意二个 *类型名* 不能指定[兼容类型](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)。使用关键词 default 的关联只能有一个。若不使用 default，且无一 *类型名* 与控制表达式类型兼容，则程序无法编译。

## 解释

​	首先，*控制表达式* 的类型经历[左值转换](https://zh.cppreference.com/w/c/language/conversion#.E5.B7.A6.E5.80.BC.E8.BD.AC.E6.8D.A2)。只在类型域中进行转换：它舍弃顶层 cvr 限定符和原子属性，并应用数组到指针/函数到指针变换到控制表达式的类型，而不实例化任何副效应或计算任何值。

​	将转换后的类型与来自关联列表中的 *类型名* 比较。

若其类型与各关联之一的 *类型名* [兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，则泛型选择的类型、值及[值类别](https://zh.cppreference.com/w/c/language/value_category)就是出现于该 *类型名* 冒号后的表达式的类型、值及值类别。

若无一 *类型名* 的类型与 *控制表达式* 兼容，且提供了 default 关联，则泛型的类型、值及值类别就是出现于 `default :` 标号后的表达式的类型、值及值类别。

## 注解

​	决不求值 *控制表达式* 和未被选择的选项中的 *表达式*。

​	因为左值转换，"abc" 匹配 `char*` 而非 `char[4]`，`(int const){0}` 匹配 `int` 而非 `const int`。

​	泛型选择中的 *表达式* 允许任何[值类别](https://zh.cppreference.com/w/c/language/value_category)，含函数指代符及 void 表达式，而且若它受到选择，则泛型选择自身拥有相同的值类别。

​	C99 中引入的来自 [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) 的[泛型数学宏](https://zh.cppreference.com/w/c/numeric/tgmath)曾是通过编译器特定的行为实现的。 C11 所引入的泛型选择给予程序员写相似的类型依赖代码的能力。

​	泛型选择类似 C++ 中的重载（在编译时基于参数类型选择数个函数之一），但它在任意表达式之间选择。

## 关键词

[`_Generic`](https://zh.cppreference.com/w/c/keyword/_Generic), [`default`](https://zh.cppreference.com/w/c/keyword/default)

## 示例

```c
#include <math.h>
#include <stdio.h>
 
// tgmath.h 宏 cbrt 的可能实现
#define cbrt(X) _Generic((X),     \
              long double: cbrtl, \
                  default: cbrt,  \
                    float: cbrtf  \
              )(X)
 
int main(void)
{
    double x = 8.0;
    const float y = 3.375;
    printf("cbrt(8.0) = %f\n", cbrt(x));    // 选择默认的 cbrt
    printf("cbrtf(3.375) = %f\n", cbrt(y)); // 将 const float 转换成 float，
                                            // 然后选择 cbrtf
}
```

​	输出：

```txt
cbrt(8.0) = 2.000000
cbrtf(3.375) = 1.500000
```

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                     | 正确行为 |
| ------------------------------------------------------------ | ------ | -------------------------------- | -------- |
| [DR 481](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_481) | C11    | 未指定控制表达式是否经历左值转换 | 经历     |

## 参阅

**模板**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/templates)**