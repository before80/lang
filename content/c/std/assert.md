+++
title = "<assert.h>"
date = 2025-04-14T23:18:36+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 宏










### assert

原址：[https://zh.cppreference.com/w/c/error/assert](https://zh.cppreference.com/w/c/error/assert)

```c
// (C23 前)
#ifdef NDEBUG
#define assert(condition) ((void)0)
#else
#define assert(condition) /*implementation defined*/
#endif

// (C23 起)
#ifdef NDEBUG
#define assert(...) ((void)0)
#else
#define assert(...) /*implementation defined*/
#endif

```

​	宏 `assert` 的定义依赖于另一个宏 NDEBUG，它并非由标准库定义。

​	若在源代码中包含 [`<assert.h>`]({{< ref "/c/header/assert" >}}) 之处 NDEBUG 被定义为宏名，则 `assert` 不做任何事。

​	若 NDEBUG 未定义，则 `assert` 检查其实参(C23 前)从 __VA_ARGS__ 组合成的表达式(C23 起)（必须拥有标量类型，否则行为未定义）与零比较是否相等。若相等，则 `assert` 在标准错误输出上输出特定于实现的诊断信息，并调用 [abort](http://zh.cppreference.com/w/c/program/abort)()。要求诊断信息必须包含表达式的文本，以及[预定义变量]({{< ref "/c/language/functions/function_definition" >}}) `__func__` 与(C99 起)[预定义宏]({{< ref "/c/language/preprocessor/replace" >}}) `__FILE__` 和 `__LINE__` 的值。

**参数**

| condition | -    | 标量类型的表达式 |
| --------- | ---- | ---------------- |

**返回值**

​	（无）

**注解**

​	没有用于向 `assert` 错误添加额外消息的标准化接口。一种可移植的包含它的方式是使用[逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})，或者与字符串字面量一起使用 `&&`：


```
assert(("There are five lights", 2 + 2 == 5));
assert(2 + 2 == 5 && "There are five lights");

```

​	`assert` 在 [Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/assert-macro-assert-wassert) 中的实现不遵从 C99 以及后续标准版本，因为其底层函数（`_wassert`）不接收 __func__ 或等价的替代品。

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

可能的输出：

```txt
--- 未定义 NDEBUG 时的输出：---
a.out: main.cpp:10: main: Assertion `x >= 0.0' failed.
 
--- 定义 NDEBUG 时的输出：---
sqrt(x) = -nan
```




### static_assert

原址：[https://zh.cppreference.com/w/c/error/static_assert](https://zh.cppreference.com/w/c/error/static_assert)

```c
#define static_assert _Static_assert // (C11 起) (C23 移除)

```

​	此便利宏展开成关键词 [`_Static_assert`]({{< ref "/c/language/keyword/_Static_assert" >}})。

**示例**

```c
#include <assert.h>
int main(void)
{
    static_assert(2 + 2 == 4, "2+2 isn't 4");   // 良构
 
    static_assert(sizeof(int) < sizeof(char),   // 编译时错误
                  "this program requires that int is less than char");
}

```

**注解**

​	自 C23 起，[`static_assert`]({{< ref "/c/language/declarations/_Static_assert" >}}) 自身即是关键词，可能亦为预定义宏，故 `<assert.h>` 不再提供它。

## 函数
