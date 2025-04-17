+++
title = "属性说明符序列(C23 起)"
date = 2025-04-13T11:13:45+08:00
weight = 160
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes](https://zh.cppreference.com/w/c/language/attributes)

​	对类型、对象、表达式等引入实现定义的属性。

## 语法

​	正式而言，语法是

| `[[` *属性列表* `]]` |      | (C23 起) |
| -------------------- | ---- | -------- |

​	其中*属性列表* ﻿是零个或多个*属性记号* ﻿的逗号分隔列表

| *标准属性*                                         | (1)  |      |
| -------------------------------------------------- | ---- | ---- |
| *属性前缀* `::` *标识符*                           | (2)  |      |
| *标准属性* `(` *实参列表* ﻿(可选) `)`               | (3)  |      |
| *属性前缀* `::` *标识符* `(` *实参列表* ﻿(可选) `)` | (4)  |      |

​	其中*属性前缀* ﻿是一个*标识符* ﻿而*实参列表* ﻿为一系列记号，其中圆括号、方括号和花括号均平衡成对（*平衡记号序列*）。

1) 标准属性，例如 `[[fallthrough]]`
2) 有命名空间的属性，例如 `[[gnu::unused]]`
3) 有实参的标准属性，例如 `[[deprecated("reason")]]`
4) 有命名空间和实参列表的属性，例如 `[[gnu::nonnull(1)]]`

## 解释

​	属性为各种由实现定义的语言扩展（例如 GNU 与 IBM 的语言扩展 `__attribute__((...))`，微软的语言扩展 `__declspec()` 等）提供了统一化的语法。

​	属性可用在 C 程序中的几乎所有位置，而且可应用于几乎所有事物：类型、变量、函数、名字、代码块、整个翻译单元，不过每个特定的属性都仅在实现所容许之处有效：`[[expect_true]]` 可能是只能与 if，而非与类声明一同使用的属性，`[[omp::parallel()]]` 可能是应用到代码块或 for 循环，而非到类型 `int` 等的属性。（请注意这两个属性只是虚构的例子，有关标准与一些非标准属性，见下文）

​	在声明中，属性可以同时出现在整个声明之前，以及紧跟在被声明实体的名字之后，这些情况下它们被组合起来。大多数其他情形中，属性应用于直接位于其之前的实体。

​	两个连续的左方括号记号（`[[`）只能出现于引入属性说明符之处，或在属性实参之内。

​	除了以下所列出的标准属性之外，实现还可能支持任意拥有由实现定义的行为的非标准属性。所有实现所未知的属性均被忽略，且不产生错误。

每个*标准属性* ﻿均为标准化保留。即每个非标准属性均由实现提供的*属性前缀* ﻿冠以前缀，例如 `[[gnu::may_alias]]` 与 `[[clang::no_sanitize]]`。

### 标准属性

​	C 标准仅定义下列属性。每个名字形如 `attr` 的标准属性亦能拼写成 `__attr__` 而其含义不变。

| `[[deprecated]]`(C23)<br />`[[deprecated("原因")]]`(C23){{{notes}}} | 指定以此属性声明的名字或实体，允许使用，但因某个*原因* ﻿而不鼓励使用 (属性指示符) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `[[fallthrough]]`(C23)                                       | 指定从前一个 case 标号发生直落是有意的，且不应被会警告直落的编译器进行诊断 (属性指示符) |
| `[[nodiscard]]`(C23)<br />`[[nodiscard("原因")]]`(C23){{{notes}}} | 鼓励编译器在返回值被丢弃时发出警告 (属性指示符)              |
| `[[maybe_unused]]`(C23)                                      | 抑制编译器对未使用实体的警告，如果有 (属性指示符)            |
| `[[noreturn]]`(C23)<br />`[[_Noreturn]]`(C23)(弃用){{{notes}}} | 指定函数不会返回 (属性指示符)                                |
| `[[unsequenced]]`(C23)                                       | 指定函数无状态、无副作用、幂等且无依赖 (属性指示符)          |
| `[[reproducible]]`(C23)                                      | 指定函数无副作用且为幂等 (属性指示符)                        |

### 属性测试

​	`__has_c_attribute(` *属性记号* `)`

​	检查*属性记号* ﻿所指名的属性记号的存在。

​	对于标准属性，它将展开成该属性被添加到工作草案中时的年份和月份（见下表），特定于厂商的属性则以某个非零整数常量确定。

​	在 [`#if`]({{< ref "/c/language/preprocessor/conditional" >}}) 与 [`#elif`]({{< ref "/c/language/preprocessor/conditional" >}}) 的表达式中可以展开 `__has_c_attribute`。 [`#ifdef`]({{< ref "/c/language/preprocessor/conditional" >}})、[` #ifndef`]({{< ref "/c/language/preprocessor/conditional" >}}) 和 [`defined`]({{< ref "/c/language/preprocessor/conditional" >}}) 把它当做已定义的宏处理，但不能在别处使用它。

|       *属性记号*       |              属性              |   值    | 标准  |
| :--------------------: | :----------------------------: | :-----: | :---: |
|      `deprecated`      |        `[[deprecated]]`        | 201904L | (C23) |
|     `fallthrough`      |       `[[fallthrough]]`        | 201904L | (C23) |
|     `maybe_unused`     |       `[[maybe_unused]]`       | 201904L | (C23) |
|      `nodiscard`       |        `[[nodiscard]]`         | 202003L | (C23) |
| `noreturn` `_Noreturn` | `[[noreturn]]` `[[_Noreturn]]` | 202202L | (C23) |
|     `unsequenced`      |       `[[unsequenced]]`        | 202207L | (C23) |
|     `reproducible`     |       `[[reproducible]]`       | 202207L | (C23) |

## 示例

```c
[[gnu::hot]] [[gnu::const]] [[nodiscard]]
int f(void); // 以三个属性声明 f
 
[[gnu::const, gnu::hot, nodiscard]]
int f(void); // 同上，但使用了包含三个属性的
             // 单个属性说明符
 
int f(void) { return 0; }
 
int main(void)
{
}
```

## 参阅

属性说明符序列的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes)

## 外部链接

| [GCC 中的属性](https://gcc.gnu.org/onlinedocs/gcc/Attribute-Syntax.html#Attribute-Syntax) | 1.   |
| ------------------------------------------------------------ | ---- |
| [Clang 中的属性](https://clang.llvm.org/docs/AttributeReference.html) | 2.   |
