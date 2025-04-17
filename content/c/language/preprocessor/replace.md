+++
title = "替换文本宏"
date = 2025-04-12T12:05:04+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor/replace](https://zh.cppreference.com/w/c/preprocessor/replace)

​	预处理器支持文本宏替换及类函数文本宏替换。

## 语法

| `#define` *标识符* *替换列表* ﻿(可选)         | (1)  |          |
| -------------------------------------------- | ---- | -------- |
| `#define` *标识符*`( 形参 )` *替换列表*      | (2)  |          |
| `#define` *标识符*`( 形参, ... )` *替换列表* | (3)  | (C99 起) |
| `#define` *标识符*`( ... )` *替换列表*       | (4)  | (C99 起) |
| `#undef `*标识符*                            | (5)  |          |

## 解释

### #define 指令

​	`#define` 指令定义*标识符* ﻿为宏，即它们指示编译器将后继出现的所有*标识符* ﻿均替换为*替换列表* ﻿，可以可选地附加地处理。若已定义该标识符为任何类型的宏，除非定义相同，否则程序非良构。

### 仿对象宏

​	仿对象宏将所定义的*标识符* ﻿的每次出现替换为*替换列表*。`#define` 指令的版本 (1) 行为恰为如此。

### 仿函数宏

​	仿函数宏将所定义的*标识符* ﻿的每次出现替换为*替换列表* ﻿，其额外接受一定数量的实参，它们会替换*替换列表* ﻿中任何*形参* ﻿的对应出现。

​	仿函数宏的调用语法与函数调用语法相似：每个宏名实例后跟一个作为下个预处理记号的 (，引入被*替换列表* ﻿所替换的记号序列，序列由匹配的 ) 记号终止，跳过中间已匹配的左右括号对。

​	实参数量必须与宏定义的（*形参列表*）中的实参数量相同，否则程序为非良构。若标识符不在函数记号中，即它自身不后随括号，则决不替换它。

`#define` 指令的版本 (2) 定义简单的仿函数宏。

`#define` 指令的版本 (3) 定义有可变数量实参的仿函数宏。能用 `__VA_ARGS__` 标识符访问额外实参，然后该标识符被实参替换。

`#define` 指令的版本 (4) 定义有可变数量实参的仿函数宏，但没有常规参数。只能用 `__VA_ARGS__` 标识符访问实参，然后该标识符被实参替换。

​	版本 (3,4)中，*替换列表* ﻿可包含标记序列 `__VA_OPT__ ( 内容 )`。标记序列在`__VA_ARGS__` 非空时，将替换为*内容* ﻿，否则将展开为空。(C23 起)

```c
#define F(...) f(0 __VA_OPT__(,) __VA_ARGS__)
F(a, b, c) // 替换为 f(0, a, b, c)
F()        // 替换为 f(0)
 
#define G(X, ...) f(0, X __VA_OPT__(,) __VA_ARGS__)
G(a, b, c) // 替换为 f(0, a, b, c)
G(a, )     // 替换为 f(0, a)
G(a)       // 替换为 f(0, a)
 
#define SDEF(sname, ...) S sname __VA_OPT__(= { __VA_ARGS__ })
SDEF(foo);       // 替换为 S foo;
SDEF(bar, 1, 2); // 替换为 S bar = { 1, 2 };
```

> 注意
>
> ​	若仿函数宏的实参包含逗号，且未为匹配的左右括号对所保护（例如 `macro(array[x = y, x + 1])` 或 [atomic_store](http://zh.cppreference.com/w/c/atomic/atomic_store) (p, (struct S){ a, b });），则将逗号转译为宏实参分隔符，这导致编译失败，原因为实参数量不合。

## `#` 与 `##` 运算符

​	在仿函数宏中，*替换列表* ﻿中标识符前的 `#` 运算符对标识符做形参替换，并将结果环绕在引号中，等效地创建一个字符串字面量。而且，预处理器会添加反斜杠，以转义环绕内嵌字符串字面量的引号，若存在，并按需在字符串中双写反斜杠。它移除所有前导和尾随空白符，且将任何文本中部的空白符序列（但非内嵌字符串字面量中的）缩减成单个空格。此运算被称作“字符串化”。若字符串化的结果不是合法字符串字面量，则行为未定义。

​	`#` 出现在 `__VA_ARGS__` 之前时，将整个展开后的 __VA_ARGS__ 放入引号：(C99 起)

```c
#define showlist(...) puts(#__VA_ARGS__)
showlist();            // 展开成 puts("")
showlist(1, "x", int); // 展开成 puts("1, \"x\", int")
```

​	*替换列表* ﻿中任意两个相继标识符间的 `##` 运算符对二个标识符进行参数替换，然后将结果连接起来。此运算被称作“连接”或“记号粘贴”。只可以粘贴有一同组成合法记号的记号：组成较长标识符的标识符、组成数字的数位或组成 `+=` 的运算符 `+` 与 `=`。不能通过粘贴 `/` 与 `*` 创建注释，因为注释在考虑宏替换前已被移除。若连接的结果不是合法记号，则行为未定义。

> 注意
>
> ​	一些编译器提供允许 ## 出现在逗号后和 __VA_ARGS__ 前的扩展，在此情况下 ## 在 __VA_ARGS__ 非空时无效，但在 __VA_ARGS__ 为空时移除逗号：这使得可以定义如 `fprintf (stderr, format, ##__VA_ARGS__)` 的宏。

​	标准没有规定 `#` 与 `##` 操作符的求值顺序。

## `#undef` 指令

​	`#undef` 指令解除定义*标识符* ﻿，即它取消先前 `#define` 对*标识符* ﻿的定义。若标识符无与之关联的宏，则忽略此指令。

### 预定义宏

​	下列宏名称在任意翻译单元中均被预定义：

| `__STDC__`                                                   | 展开成整数常量 1。此宏是用以指示遵从标准的实现 (宏常量)      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `__STDC_VERSION__`(C95)                                      | 展开成 `long` 类型的整数常量，其值随着 C 标准的每个版本递增：`199409L` (C95) <br />`199901L` (C99)<br />`201112L` (C11)<br />`201710L` (C17)<br />`202311L` (C23) (宏常量) |
| `__STDC_HOSTED__`(C99)                                       | 若实现有宿主（在操作系统下运行），则展开成整数常量 1，若为自立的（不在操作系统中运行）则展开成 0 (宏常量) |
| `__FILE__`                                                   | 展开成当前文件名，为字符串字面量，可用 [`#line`]({{< ref "/c/language/preprocessor/line" >}}) 指令更改 (宏常量) |
| `__LINE__`                                                   | 展开成源文件行号，为整数常量，可用 [`#line`]({{< ref "/c/language/preprocessor/line" >}}) 指令更改 (宏常量) |
| `__DATE__`                                                   | 展开成翻译的日期，格式为 "Mmm dd yyyy" 的字符串字面量。月份名如同以 [asctime](https://zh.cppreference.com/w/c/chrono/asctime) 生成，而若月之日期小于 `10` 则 "dd" 的首字符为空格 (宏常量) |
| `__TIME__`                                                   | 展开成翻译的时间，格式为 "hh:mm:ss" 的字符串字面量，如同 [asctime](http://zh.cppreference.com/w/c/chrono/asctime)() 所生成 (宏常量) |
| `__STDC_UTF_16__`(C23)                                       | 扩展为 1 以指出 `char16_t` 使用 UTF-16 编码 (宏常量)         |
| `__STDC_UTF_32__`(C23)                                       | 扩展为 1 以指出 `char32_t` 使用 UTF-32 编码 (宏常量)         |
| `__STDC_EMBED_NOT_FOUND__` `__STDC_EMBED_FOUND__` `__STDC_EMBED_EMPTY__`(C23) | 分别扩展为 `0`、`1` 和 `2` (宏常量)                          |

​	实现可能预定义下列额外宏名：

| `__STDC_ISO_10646__`(C99)         | 若 `wchar_t` 使用 Unicode，则展开成形式为 `yyyymmL` 的整数常量，日期指示受支持的 Unicode 最近版本 (宏常量) |
| --------------------------------- | ------------------------------------------------------------ |
| `__STDC_IEC_559__`(C99)           | 若支持 IEC 60559 则展开成 `1` (弃用)(C23 起) (宏常量)        |
| `__STDC_IEC_559_COMPLEX__`(C99)   | 若支持 IEC 60559 复数算术则展开成 `1` (弃用)(C23 起) (宏常量) |
| `__STDC_UTF_16__`(C11)            | 若 `char16_t` 使用 UTF-16 则展开成 1 (宏常量)                |
| `__STDC_UTF_32__`(C11)            | 若 `char32_t` 使用 UTF-32 则展开成 `1` (宏常量)              |
| `__STDC_MB_MIGHT_NEQ_WC__`(C99)   | 若 `'x' == L'x'` 可能对基础字符集的成员为 false 则展开成 `1`，例如在基于 EBCDIC 的，`wchar_t` 使用 Unicode 的系统上 (宏常量) |
| `__STDC_ANALYZABLE__`(C11)        | 若支持[可分析性]({{< ref "/c/language/misc/analyzability" >}})则展开成 1 (宏常量) |
| `__STDC_LIB_EXT1__`(C11)          | 若支持[边界检查接口](https://zh.cppreference.com/w/c/error)则展开成整数常量 `201112L` (宏常量) |
| `__STDC_NO_ATOMICS__`(C11)        | 若不支持[原子]({{< ref "/c/language/declarations/atomic" >}})类型和[原子操作库](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)则展开成 `1` (宏常量) |
| `__STDC_NO_COMPLEX__`(C11)        | 若不支持[复数类型]({{< ref "/c/language/basic_concepts/arithmetic_types#.E5.A4.8D.E6.B5.AE.E7.82.B9.E6.95.B0.E7.B1.BB.E5.9E.8B" >}})和[复数运算库](https://zh.cppreference.com/w/c/numeric/complex)则展开成 `1` (宏常量) |
| `__STDC_NO_THREADS__`(C11)        | 若不支持[多线程](https://zh.cppreference.com/w/c/thread)则展开成 `1` (宏常量) |
| `__STDC_NO_VLA__`(C11)            | 若不支持自动存储期的(C23 起)[非常量长度数组]({{< ref "/c/language/declarations/array#.E9.9D.9E.E5.B8.B8.E9.87.8F.E9.95.BF.E5.BA.A6.E6.95.B0.E7.BB.84" >}})及可变修改类型(C23 前)则展开成 1 (宏常量) |
| `__STDC_IEC_60559_BFP__`(C23)     | 若支持 IEC 60559 二进制浮点数算术则展开成 `202311L` (宏常量) |
| `__STDC_IEC_60559_DFP__`(C23)     | 若支持 IEC 60559 十进制浮点数算术则展开成 `202311L` (宏常量) |
| `__STDC_IEC_60559_COMPLEX__`(C23) | 若支持 IEC 60559 复数算术则展开成 `202311L` (宏常量)         |
| `__STDC_IEC_60559_TYPES__`(C23)   | 若支持 IEC 60559 互换可扩展类型则展开成 `202311L` (宏常量)   |

​	这些宏的值（除了 `__FILE__` 和 `__LINE__`）在整个翻译单元中保持常量。尝试重定义或解除定义这些宏导致未定义行为。

​	预定义变量 __func__（细节见[函数定义]({{< ref "/c/language/functions/function_definition#func" >}})）不是预处理器宏，尽管有时与 `__FILE__` 及 `__LINE__` 一同使用它，例如通过 [assert](https://zh.cppreference.com/w/c/error/assert)。(C99 起)

## 示例

```c
#include <stdio.h>
 
// 制造函数工厂并使用之
#define FUNCTION(name, a) int fun_##name(int x) { return (a) * x; }
 
FUNCTION(quadruple, 4)
FUNCTION(double, 2)
 
#undef FUNCTION
#define FUNCTION 34
#define OUTPUT(a) puts( #a )
 
int main(void)
{
    printf("quadruple(13): %d\n", fun_quadruple(13) );
    printf("double(21): %d\n", fun_double(21) );
    printf("%d\n", FUNCTION);
    OUTPUT(million);               // 注意缺少引号
}
```

输出：

```txt
quadruple(13): 52
double(21): 42
34
million
```

## 缺陷报告

下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                                  | 正确行为                                |
| ------------------------------------------------------------ | ------ | --------------------------------------------- | --------------------------------------- |
| [DR 321](https://www.open-std.org/jtc1/sc22/wg14/www/docs/dr_321.htm) | C99    | 不明确 L'x' == 'x' 是否在基本字符集中始终成立 | 为该目的添加了 __STDC_MB_MIGHT_NEQ_WC__ |

