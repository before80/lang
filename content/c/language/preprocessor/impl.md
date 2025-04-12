+++
title = "实现定义的行为控制"
date = 2025-04-12T12:26:40+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

> 原文：[https://zh.cppreference.com/w/cpp/preprocessor/impl](https://zh.cppreference.com/w/cpp/preprocessor/impl)

​	实现定义的行为受 #pragma 指令控制。

## 语法

|                               |      |            |
| ----------------------------- | ---- | ---------- |
| `#pragma` *语用形参*          | (1)  |            |
| `_Pragma(` *字符串字面量* `)` | (2)  | (C++11 起) |

1) 具有由实现定义的行为方式。
2) 从 *字符串字面量* 移除 `L` 前缀（如果存在），外层引号，及前导/尾随空白符，将每个 \" 替换为 "、将每个 \\ 替换为 \，然后将结果记号化（像[翻译阶段 3](https://zh.cppreference.com/w/cpp/language/translation_phases#.E9.98.B6.E6.AE.B5_3) 中一样），再如同将结果作为 (1) 中的输入来使用。

## 解释

​	语用指令控制编译器的特定于实现的行为，如禁用编译器警告或更改对齐要求。无法识别的语用会被忽略。

### 非标准语用

​	ISO C++ 语言标准并不要求编译器支持任何语用。不过，多种实现都支持几种非标准的语用：

#### `#pragma STDC`

ISO C 语言标准要求 C 编译器支持下列三种语用，一些 C++ 编译器供应商在它们的 C++ 前端中以不同的程度支持它们：

|                                        |      |      |
| -------------------------------------- | ---- | ---- |
| `#pragma STDC FENV_ACCESS `*实参*      | (1)  |      |
| `#pragma STDC FP_CONTRACT `*实参*      | (2)  |      |
| `#pragma STDC CX_LIMITED_RANGE `*实参* | (3)  |      |

​	其中 *实参* 是 `ON`、`OFF` 和 `DEFAULT` 之一。

1. 如果设为 `ON`，就会告知编译器程序将访问或修改[浮点环境](https://zh.cppreference.com/w/c/numeric/fenv)，这意味着可能推翻标志测试和模式更改（例如，全局共用子表达式删除，代码移动，及常量折叠）的优化将被禁用。默认值由实现定义，通常是 `OFF`。

2. 允许浮点表达式的*缩略（contracting）*行为，即一种优化，表达式严格按书面求值时可被观察到的一些舍入错误和浮点异常将被忽略。例如，允许 (x * y) + z 使用单条融合乘加 CPU 指令实现。默认值由实现定义，通常是 `ON`。

3. 告知编译器，复数的乘法、除法和绝对值可以使用简化的数学公式 \\((x+iy)×(u+iv) =  (xu-yv)+i(yu+xv) \\)，      

   \\((x+iy)  \over  (u+iv)  =  {(xu+yv)+i(yu-xv)}  \over  (u^2 + v^2)\\)，和 \\(|x+iy| = \sqrt{x^2 + y^2}\\)，而不考虑中间溢出的可能性。换言之，程序员保证传递给这些函数的值范围是受限的。默认值为 `OFF`。

​	上述三种语用只能在所有外部声明之外，或在所有显式声明或复合语句中的所有语句之前出现，否则程序的行为未定义。

\\({x+iy}  \over  {u+iv}  =  {(xu+yv)+i(yu-xv)}  \over  (u^2 + v^2)\\)

> 注意
>
> \\({x+iy}  \over  {u+iv}  =  {(xu+yv)+i(yu-xv)}  \over  (u^2  +  v^2)\\)
>
> ​	不支持这些语用的编译器可能会提供等价的编译时选项，例如 gcc 的 `-fcx-limited-range` 和 `-ffp-contract`。

#### `#pragma once`

​	`#pragma once` 是受到[绝大多数现代编译器](https://en.wikipedia.org/wiki/Pragma_once#Portability)支持的非标准语用。当某个头文件中包含它时，指示编译器只对其分析一次，即使它在同一源文件中（直接或间接）被包含了多次也是如此。

​	阻止同一头文件的多次包含的标准方式是使用[包含防护](https://en.wikipedia.org/wiki/Include_guard)：

```c
#ifndef LIBRARY_FILENAME_H
#define LIBRARY_FILENAME_H
// 头文件的内容
#endif /* LIBRARY_FILENAME_H */
```

​	从而在任何翻译单元中，该头文件除首次以外被包含时都被排除出编译。所有现代编译器都记录头文件使用了包含防护的事实，只要该防护仍有定义，再遇到该头文件时就不再分析它。（例子见 [gcc](https://gcc.gnu.org/onlinedocs/cpp/Once-Only-Headers.html) ）

​	使用 `#pragma once` 时，同一个头文件可以变为

```c
#pragma once
// 头文件的内容
```

​	不同于头文件防护，这条 pragma 使得，不会错误地在多个文件中使用相同的宏名。另一方面，因为带 #pragma once 的文件是基于其文件系统层次的身份所排除的，所以若头文件在项目中多处出现，则不可避免地再次包含它。

#### `#pragma pack`

​	此语用族控制后继定义的类和联合体的最大对齐。

|                            |      |
| -------------------------- | ---- |
| `#pragma pack(实参)`       | (1)  |
| `#pragma pack()`           | (2)  |
| `#pragma pack(push)`       | (3)  |
| `#pragma pack(push, 实参)` | (4)  |
| `#pragma pack(pop)`        | (5)  |

​	其中 *实参* 实参是小的 2 的幂，指定以字节计的新对齐。

1) 设置当前对齐为值 *实参*。
2) 设置当前对齐为默认值（由命令行选项指定）。
3) 推入当前对齐的值到内部栈。
4) 推入当前对齐的值到内部栈然后设置当前对齐为值 *实参*。
5) 从内部栈弹出顶条目然后设置（恢复）当前对齐为该值。

​	`#pragma pack` 可以指定类的对齐，然而它不能使类过对齐。

参阅 [GCC](https://gcc.gnu.org/onlinedocs/gcc/Structure-Layout-Pragmas.html) 与 [MSVC](https://docs.microsoft.com/en-us/cpp/preprocessor/pack) 的特定细节。

> 本节未完成 
>
> 原因：解释此语用在数据成员的效果还有使用它们的优势与劣势。参考源：[Stack Overflow](https://stackoverflow.com/questions/3318410/pragma-pack-effect)

> 本节未完成 
>
> 原因：暂无示例

## 参阅

​	实现定义行为控制的 [C 文档](https://zh.cppreference.com/w/c/preprocessor/impl)

## 外部链接

| 1.   | [Visual Studio 的 C++ 语用](https://docs.microsoft.com/en-us/cpp/preprocessor/pragma-directives-and-the-pragma-keyword) |
| ---- | ------------------------------------------------------------ |
| 2.   | GCC 接受的 [语用](https://gcc.gnu.org/onlinedocs/gcc/Pragmas.html) |
| 3.   | IBM AIX XL C 16.1 的[各条语用描述](https://www.ibm.com/support/knowledgecenter/en/SSGH3R_16.1.0/com.ibm.xlcpp161.aix.doc/compiler_ref/pragma_descriptions.html)及[标准语用](https://www.ibm.com/support/knowledgecenter/en/SSGH3R_16.1.0/com.ibm.xlcpp161.aix.doc/language_ref/std_pragmas.html) |
| 4.   | Sun Studio 11 C++ 用户指南中的 [附录 B 语用](http://download.oracle.com/docs/cd/E19422-01/819-3690/Pragmas_App.html#73499) |
| 5.   | [Intel C++ 编译器语用](https://software.intel.com/content/www/us/en/develop/documentation/cpp-compiler-developer-guide-and-reference/top/compiler-reference/pragmas.html) |
| 6.   | HP aCC A.06.25 的[发行注记（包括语用）](https://h20565.www2.hpe.com/hpsc/doc/public/display?sp4ts.oid=4268164&docLocale=en_US&docId=emr_na-c02653979) |