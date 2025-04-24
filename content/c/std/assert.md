
+++
title = "<assert.h>"
date = 2025-04-24T19:11:42+08:00
weight = 0
type = "docs"
description = "条件编译宏，将参数与零比较"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏



### assert

原址：[https://zh.cppreference.com/w/c/error/assert](https://zh.cppreference.com/w/c/error/assert)

作用：若用户指定的条件非`true`，则异常终止程序。可以在发行版本禁用。  (宏函数)

备注：
```c
// 在标头 <assert.h> 定义
#ifdef NDEBUG
#define assert(condition) ((void)0)
#else
#define assert(condition) /*implementation defined*/

#endif// (C23 前)
#ifdef NDEBUG
#define assert(...) ((void)0)
#else
#define assert(...) /*implementation defined*/

#endif// (C23 起)
```

​	宏 `assert` 的定义依赖于另一个宏 `NDEBUG`，它并非由标准库定义。

​	若在源代码中包含 [`<assert.h>`](https://zh.cppreference.com/w/c/header/assert) 之处 `NDEBUG` 被定义为宏名，则 `assert` 不做任何事。

​	若 `NDEBUG` 未定义，则 `assert` 检查其实参(C23 前)从 `__VA_ARGS__` 组合成的表达式(C23 起)（必须拥有标量类型，否则行为未定义）与零比较是否相等。若相等，则 `assert` 在标准错误输出上输出特定于实现的诊断信息，并调用 [abort](http://zh.cppreference.com/w/c/program/abort)()。要求诊断信息必须包含表达式的文本，以及[预定义变量](https://zh.cppreference.com/w/c/language/function_definition) `__func__` 与(C99 起)[预定义宏](https://zh.cppreference.com/w/c/preprocessor/replace) `__FILE__` 和 `__LINE__` 的值。

**参数**

| condition | -    | 标量类型的表达式 |
| --------- | ---- | ---------------- |
|           |      |                  |

**返回值**

​	（无）

**注解**

​	没有用于向 `assert` 错误添加额外消息的标准化接口。一种可移植的包含它的方式是使用[逗号运算符](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)，或者与字符串字面量一起使用 `&&`：

```
assert(("There are five lights", 2 + 2 == 5));
assert(2 + 2 == 5 && "There are five lights");
```

​	`assert` 在 [Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/assert-macro-assert-wassert) 中的实现不遵从 C99 以及后续标准版本，因为其底层函数（`_wassert`）不接收 `__func__` 或等价的替代品。

​	虽然 C23 中 `assert` 的更改（[N2829](https://open-std.org/JTC1/SC22/WG14/www/docs/n2829.htm)）不是正式的缺陷报告，C 委员会[推荐](https://www.open-std.org/jtc1/sc22/wg14/www/previous.html)实现将该更改向后移植到旧模式。

**示例**

```c
#include <stdio.h>
// 反注释可禁用 assert()
// #define NDEBUG
#include <assert.h>
#include <math.h>
 
#define TEST(...) __VA_ARGS__
 
int main(void)
{
    double x = -1.0;
    assert(x >= 0.0);
    printf("sqrt(x) = %f\n", sqrt(x));
 
    assert(TEST(x >= 0.0));
 
    return 0;
}
```

​	可能的输出：

```txt
--- 未定义 NDEBUG 时的输出：---
a.out: main.cpp:10: main: Assertion `x >= 0.0' failed.
 
--- 定义 NDEBUG 时的输出：---
sqrt(x) = -nan
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.2.2.1 The assert macro （第 196 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.2.1.1 The assert macro （第 135 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.2.1.1 The assert macro （第 186-187 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.2.1.1 The assert macro （第 169 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.2.1.1 The assert macro

**参阅**

| [abort<br />](https://zh.cppreference.com/w/c/program/abort) | 引发非正常的程序终止（不清理） (函数) |
| ------------------------------------------------------------ | ------------------------------------- |
| **assert** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/error/assert)** |                                       |






## 函数




