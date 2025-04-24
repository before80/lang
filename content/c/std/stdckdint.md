
+++
title = "<stdckdint.h>"
date = 2025-04-24T20:14:16+08:00
weight = 180
type = "docs"
description = "实施带检查整数算术的宏"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏



### __STDC_VERSION_STDCKDINT_H__

原址：

作用：

备注：






## 函数



### ckd_add

原址：[https://zh.cppreference.com/w/c/numeric/ckd_add](https://zh.cppreference.com/w/c/numeric/ckd_add)

作用：checked addition operation on two integers(type-generic function macro)

备注：
```c
// 在标头 <stdckdint.h> 定义
#define ckd_add(result, a, b) /* 由实现定义 */
// 暴露的接口：

bool ckd_add(type1* result, type2 a, type3 b);// (C23 起)
```

​	计算加法 `x + y` 并将结果存储于 `*result`。进行加法如同两个操作数都表示为具有无限范围的有符号整数类型，随后将结果从这个整数类型转换为 `type1` 一样。如果赋给 `*result` 的值正确表示运算的数学结果，就返回 `false`。否则返回 `true`。这种情况下，赋给 `*result` 的值是运算的数学结果根据 `*result` 的宽度回绕所得。

**参数**

| a, b   | -    | 整数           |
| ------ | ---- | -------------- |
| result | -    | 存储结果的地址 |

**返回值**

​	如果赋给 `*result` 的值正确表示加法的数学结果则为 `false`，否则为 `true`。

**注解**

​	`type2` 和 `type3` 应当是并非“普通”`char`、`bool`、[位精确整数类型](https://zh.cppreference.com/w/c/language/arithmetic_types)或者[枚举类型](https://zh.cppreference.com/w/c/language/enum)之外的任何整数类型，且二者可以相同。`*result` 应当是并非“普通”`char`、`bool`、位精确整数类型或者枚举类型之外的任何整数类型的可修改左值。

​	建议实现在 `type2` 或 `type3` 不是适当整数类型，或当 `*result` 不是适当整数类型的可修改左值时给出诊断消息。

**示例**

> 本节未完成
>
> 原因：暂无示例

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.20.1 The ckd_ checked integer operation macros （第 311 页）

**参阅**

| [ckd_sub (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_sub) | 两个整数的带检查减法运算 (泛型函数宏) |
| ------------------------------------------------------------ | ------------------------------------- |
| [ckd_mul (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_mul) | 两个整数的带检查乘法运算 (泛型函数宏) |
| **ckd_add** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/ckd_add)** |                                       |





### ckd_mul

原址：[https://zh.cppreference.com/w/c/numeric/ckd_mul](https://zh.cppreference.com/w/c/numeric/ckd_mul)

作用：checked multiplication operation on two integers(type-generic function macro)

备注：
```c
// 在标头 <stdckdint.h> 定义
#define ckd_mul(result, a, b) /* 由实现定义 */
// 暴露的接口：

bool ckd_mul(type1* result, type2 a, type3 b);// (C23 起)
```

​	计算乘法 `x × y` 并将结果存储于 `*result`。进行乘法如同两个操作数都表示为具有无限范围的有符号整数类型，随后将结果从这个整数类型转换为 `type1` 一样。如果赋给 `*result` 的值正确表示运算的数学结果，就返回 `false`。否则返回 `true`。这种情况下，赋给 `*result` 的值是运算的数学结果根据 `*result` 的宽度回绕所得。

**参数**

| a, b   | -    | 整数           |
| ------ | ---- | -------------- |
| result | -    | 存储结果的地址 |

**返回值**

​	如果赋给 `*result` 的值正确表示乘法的数学结果则为 `false`，否则为 `true`。

**注解**

​	`type2` 和 `type3` 应当是并非“普通”`char`、`bool`、[位精确整数类型](https://zh.cppreference.com/w/c/language/arithmetic_types)或者[枚举类型](https://zh.cppreference.com/w/c/language/enum)之外的任何整数类型，且二者可以相同。`*result` 应当是并非“普通”`char`、`bool`、位精确整数类型或者枚举类型之外的任何整数类型的可修改左值。

​	建议实现在 `type2` 或 `type3` 不是适当整数类型，或当 `*result` 不是适当整数类型的可修改左值时给出诊断消息。

**示例**

> 本节未完成
>
> 原因：暂无示例

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.20.1 The ckd_ checked integer operation macros （第 311 页）

**参阅**

| [ckd_add (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_add) | 两个整数的带检查加法运算 (泛型函数宏) |
| ------------------------------------------------------------ | ------------------------------------- |
| [ckd_sub (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_sub) | 两个整数的带检查减法运算 (泛型函数宏) |
| **ckd_mul** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/ckd_mul)** |                                       |





### ckd_sub

原址：[https://zh.cppreference.com/w/c/numeric/ckd_sub](https://zh.cppreference.com/w/c/numeric/ckd_sub)

作用：checked subtraction operation on two integers(type-generic function macro)

备注：
```c
// 在标头 <stdckdint.h> 定义
#define ckd_sub(result, a, b) /* 由实现定义 */
// 暴露的接口：

bool ckd_sub(type1* result, type2 a, type3 b);// (C23 起)
```

​	计算减法 `x - y` 并将结果存储于 `*result`。进行减法如同两个操作数都表示为具有无限范围的有符号整数类型，随后将结果从这个整数类型转换为 `type1` 一样。如果赋给 `*result` 的值正确表示运算的数学结果，就返回 `false`。否则返回 `true`。这种情况下，赋给 `*result` 的值是运算的数学结果根据 `*result` 的宽度回绕所得。

**参数**

| a, b   | -    | 整数           |
| ------ | ---- | -------------- |
| result | -    | 存储结果的地址 |

**返回值**

​	如果赋给 `*result` 的值正确表示减法的数学结果则为 `false`，否则为 `true`。

**注解**

​	`type2` 和 `type3` 应当是并非“普通”`char`、`bool`、[位精确整数类型](https://zh.cppreference.com/w/c/language/arithmetic_types)或者[枚举类型](https://zh.cppreference.com/w/c/language/enum)之外的任何整数类型，且二者可以相同。`*result` 应当是并非“普通”`char`、`bool`、位精确整数类型或者枚举类型之外的任何整数类型的可修改左值。

​	建议实现在 `type2` 或 `type3` 不是适当整数类型，或当 `*result` 不是适当整数类型的可修改左值时给出诊断消息。

**示例**

> 本节未完成
>
> 原因：暂无示例

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.20.1 The ckd_ checked integer operation macros （第 311 页）

**参阅**

| [ckd_add (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_add) | 两个整数的带检查加法运算 (泛型函数宏) |
| ------------------------------------------------------------ | ------------------------------------- |
| [ckd_mul (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_mul) | 两个整数的带检查乘法运算 (泛型函数宏) |
| **ckd_sub** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/ckd_sub)** |                                       |





