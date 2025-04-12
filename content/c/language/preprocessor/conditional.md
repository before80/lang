+++
title = "条件包含"
date = 2025-04-12T11:58:52+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor/conditional](https://zh.cppreference.com/w/c/preprocessor/conditional)

​	预处理器支持有条件地编译源文件的某些部分。这一行为由 `#if`、`#else`、`#elif`、`#ifdef`、`#ifndef`、`#elifdef`、`#elifndef`(C23 起) 与 `#endif` 指令所控制。

## 语法

| `#if` *表达式*                |
| ----------------------------- |
| `#ifdef` *标识符*             |
| `#ifndef` *标识符*            |
| `#elif` *表达式*              |
| `#elifdef` *标识符* (C23 起)  |
| `#elifndef` *标识符* (C23 起) |
| `#else`                       |
| `#endif`                      |

## 解释

​	条件预处理块由 `#if`、`#ifdef` 或 `#ifndef` 指令开始，然后可选地包含任意多个 `#elif`、`#elifdef` 或 `#elifndef`(C23 起) 指令，接下来是最多一个可选的 `#else` 指令，并以 `#endif` 指令结束。嵌套的条件预处理块会被单独处理。

​	各个 `#if`、`#ifdef`、`#ifndef`、`#elif`、`#elifdef`、`#elifndef`(C23 起) 和 `#else` 指令所控制的代码块在第一个不属于内部嵌套的条件预处理块的 `#elif`、`#elifdef`、`#elifndef`(C23 起)、`#else` 或 `#endif` 指令处结束。

​	`#if`、`#ifdef` 和 `#ifndef` 指令测试其所指定的条件（见下文），如果条件求值为真，则编译其控制的代码块。此时后续的 `#else`、`#elifdef`、`#elifndef`(C23 起) 和 `#elif` 指令将被忽略。否则，如果所指定的条件求值为假，则跳过其所控制的代码块，然后处理后续的 `#else`、`#elifdef`、`#elifndef`(C23 起) 或 `#elif` 指令（如果存在）。若后续指令为 `#else`，则 `#else` 指令所控制的代码块将会无条件地进行编译。否则，`#elif`、`#elifdef` 或 `#elifndef`(C23 起) 指令按照与 `#if` 指令相同的方式执行：即测试条件是否满足，并根据其结果决定编译或跳过其所控制的代码块，并在后一种情况下继续处理后续的 `#elif`、`#elifdef`、`#elifndef`(C23 起) 和 `#else` 指令。条件预处理块以 `#endif` 指令结束。

## 条件的求值

#### `#if`, `#elif`

​	*表达式* 是常量表达式，仅使用[常量](https://zh.cppreference.com/w/c/language/expressions#.E5.B8.B8.E9.87.8F.E5.8F.8A.E5.AD.97.E9.9D.A2.E9.87.8F)和用 [`#define`](https://zh.cppreference.com/w/c/preprocessor/replace) 指令定义的标识符。任何非字面量，未以 [`#define`](https://zh.cppreference.com/w/c/preprocessor/replace) 指令定义的标识符，均求值为 0，但 true 求值为 1(C23 起)。

​	表达式可以含有形式为 `defined` *标识符* 或 `defined (`*标识符*`)` 的一元运算符，若用 [`#define`](https://zh.cppreference.com/w/c/preprocessor/replace) 指令定义了该 *标识符*，则返回 1，否则返回 0。这种语境中，__has_include、__has_embed 和 __has_c_attribute 被当做如同它们是已定义宏的名字。(C23 起)若 *表达式* 求值为非零值，则包含该控制代码块并跳过其他。若所用的任何标识符不是常量，则用 0 替换它。

​	预处理器语境中，`__has_c_attribute` 表达式检测给定属性记号是否受支持及其受支持版本。见[属性测试](https://zh.cppreference.com/w/c/language/attributes#.E5.B1.9E.E6.80.A7.E6.B5.8B.E8.AF.95)。(C23 起)

> 注
>
> ​	[DR 412](https://open-std.org/JTC1/SC22/WG14/www/docs/dr_412.htm) 前，“`#if *cond1*` ... `#elif *cond2*`”和“`#if *cond1*` ... `#else`”后面跟着“`#if *cond3*`”是不同的，因为当 `*cond1*` 为真时第二个 `#if` 将被跳过，且 `*cond3*` 并不需要是良构的，而 `#elif` 中的 `*cond2*` 则必须是合法的表达式。[DR 412](https://open-std.org/JTC1/SC22/WG14/www/docs/dr_412.htm) 开始，引领跳过的代码块的 `#elif` 也被跳过。

## 组合指令

​	检查标识符是否[被定义为宏名](https://zh.cppreference.com/w/c/preprocessor/replace)。

“`#ifdef` *标识符*”与“`#if defined` *标识符*”实质上等价。

“`#ifndef` *标识符*”与“`#if !defined` *标识符*”实质上等价。

“`#elifdef` *标识符*”与“`#elif defined` *标识符*”实质上等价。(C23 起)

“`#elifndef` *标识符*”与“`#elif !defined` *标识符*”实质上等价。(C23 起)

## 注解

​	`#elifdef` 与 `#elifndef` 指令于 C23 标准化，不过实现可以将它们作为遵从的扩展向后移植到旧语言模式。

## 示例

```c
#define ABCD 2
#include <stdio.h>
 
int main(void)
{
 
#ifdef ABCD
    printf("1: yes\n");
#else
    printf("1: no\n");
#endif
 
#ifndef ABCD
    printf("2: no1\n");
#elif ABCD == 2
    printf("2: yes\n");
#else
    printf("2: no2\n");
#endif
 
#if !defined(DCBA) && (ABCD < 2 * 4 - 3)
    printf("3: yes\n");
#endif
 
// C23 指令 #elifdef/#elifndef
#ifdef CPU
    printf("4: no1\n");
#elifdef GPU
    printf("4: no2\n");
#elifndef RAM
    printf("4: yes\n"); // C23 模式中得到选择， C23 之前模式中可能得到选择
#else
    printf("4: no3\n"); // C23 之前模式中可能得到选择
#endif
}
```

可能的输出：

```txt
1: yes
2: yes
3: yes
4: yes
```

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                      | 正确行为           |
| ------------------------------------------------------------ | ------ | --------------------------------- | ------------------ |
| [DR 412](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_412) | C++14  | 要求失败的 `#elif` 中的表达式合法 | 跳过失败的 `#elif` |

## 参阅

​	**条件包含**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/preprocessor/conditional)**