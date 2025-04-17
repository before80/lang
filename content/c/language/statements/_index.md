+++
title = "语句"
date = 2025-04-12T15:02:09+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/statements](https://zh.cppreference.com/w/c/language/statements)

​	语句是带顺序执行的 C 程序段。任何函数体都是一条复合语句，继而为语句或声明的序列：

```c
int main(void)
{ // 复合语句的开始
    int n = 1; // 声明（非语句）
    n = n+1; // 表达式语句
    printf("n = %d\n", n); // 表达式语句
    return 0; // 返回语句
} // 复合语句之结尾，函数体之结尾
```


​	语句有五种类型：

1) [复合语句]({{< ref "/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5" >}})
2) [表达式语句]({{< ref "/c/language/statements#.E8.A1.A8.E8.BE.BE.E5.BC.8F.E8.AF.AD.E5.8F.A5" >}})
3) [选择语句]({{< ref "/c/language/statements#.E9.80.89.E6.8B.A9.E8.AF.AD.E5.8F.A5" >}})
4) [循环语句]({{< ref "/c/language/statements#.E5.BE.AA.E7.8E.AF.E8.AF.AD.E5.8F.A5" >}})
5) [跳转语句]({{< ref "/c/language/statements#.E8.B7.B3.E8.BD.AC.E8.AF.AD.E5.8F.A5" >}})

​	[属性说明符序列]({{< ref "/c/language/declarations/attributes" >}}) (*属性说明符序列*) 能应用到无标号语句，该情况下（除了表达式语句）属性应用到相应的语句。(C23 起)

## 标号

​	任何语句都能*有标号*，通过在语句自身前提供一个跟随冒号的名称。

| *属性说明符序列*(可选)(C23 起) *标识符* `:`            | (1)  |
| ------------------------------------------------------ | ---- |
| *属性说明符序列*(可选)(C23 起) `case` *常量表达式* `:` | (2)  |
| *属性说明符序列*(可选)(C23 起) `default` `:`           | (3)  |

1) [goto]({{< ref "/c/language/statements/goto" >}}) 语句的目标。
2) [switch]({{< ref "/c/language/statements/switch" >}}) 语句的 `case` 标号。
3) [switch]({{< ref "/c/language/statements/switch" >}}) 语句的默认标号。

​	任何语句（但非声明）可以前附任意数量的*标号*，每个都声明一个*标识符* ﻿为标号名，标号名必须在闭合的函数中唯一（换言之，标号名拥有[函数作用域]({{< ref "/c/language/basic_concepts/scope" >}})）。

​	标号声明自身没有效果，不会以任何方式变更控制流，或修改跟随其后的语句的行为。

​	标号应当后随语句。(C23 前)

​	标号可以不带其后随语句出现。若标号单独出现在块中，则表现为如同它后随一条[空语句]({{< ref "/c/language/statements#.E8.A1.A8.E8.BE.BE.E5.BC.8F.E8.AF.AD.E5.8F.A5" >}})。可选的 [*属性说明符序列*]({{< ref "/c/language/declarations/attributes" >}}) 应用到标号。(C23 起)

## 复合语句

​	复合语句，或称*块*，是花括号所包围的语句与声明的序列。

| `{` *语句* `|` *声明*...(可选) `}`                           | (C23 前) |
| ------------------------------------------------------------ | -------- |
| *属性说明符序列*(可选) `{` *无标号语句* `|` *标号* `|` *声明*...(可选) `}` | (C23 起) |

​	复合语句允许将一组声明和语句组合入一个单元，并将其任何在期待单个语句的场所使用（例如在 [if]({{< ref "/c/language/statements/if" >}}) 语句或循环语句中）：

```c
if (expr) // if 语句的开始
{ // 开始块
  int n = 1; // 声明
  printf("%d\n", n); // 表达式语句
} // 块结尾，if 语句结尾
```

​	每个复合语句引入其自身的[块作用域]({{< ref "/c/language/basic_concepts/scope" >}})。

​	拥有自动[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的变量的初始化式，及 VLA 声明符在每次控制流经过这些声明时按顺序执行，就像它们是语句一样：

```c
int main(void)
{ // 块的开始
  { // 块的开始
       puts("hello"); // 表达式语句
       int n = printf("abc\n"); // 声明，打印 "abc\n"，将 4 存入 n
       int a[n*printf("1\n")]; // 声明，打印 "1\n"，分配 8*sizeof(int)
       printf("%zu\n", sizeof(a)); // 表达式语句
  } // 块结束，n 与 a 的作用域结束
  int n = 7; // n 可以重新使用
}
```

## 表达式语句

​	表达式后跟分号即是一条语句。

| *表达式*(可选) `;`            | (1)  |          |
| ----------------------------- | ---- | -------- |
| *属性说明符序列* *表达式* `;` | (2)  | (C23 起) |

​	典型的 C 程序中大多数语句是表达式语句，例如赋值或函数调用。

​	无表达式的表达式语句被称作*空语句*。它通常用于给 [for]({{< ref "/c/language/statements/for" >}}) 或 [while]({{< ref "/c/language/statements/while" >}}) 循环提供空循环体。它亦能用于在复合语句尾部或声明之前携带一个标号：

```c
puts("hello"); // 表达式语句
char *s;
while (*s++ != '\0')
    ; // 空语句
```

​	可选的 [*属性声明符序列*]({{< ref "/c/language/declarations/attributes" >}}) 应用到表达式。后随 `;` 的*属性说明符序列* ﻿不构成表达式。它替而构成[属性声明]({{< ref "/c/language/declarations" >}})。(C23 起)

## 选择语句

​	选择语句根据表达式的值，选择数条语句之一执行。

| *属性说明符序列*(可选)(C23 起) `if` `(` *表达式* `)` *语句*  | (1)  |
| ------------------------------------------------------------ | ---- |
| *属性说明符序列*(可选)(C23 起) `if` `(` *表达式* `)` *语句* `else` *语句* | (2)  |
| *属性说明符序列*(可选)(C23 起) `switch` `(` *表达式* `)` *语句* | (3)  |

1) [if]({{< ref "/c/language/statements/if" >}}) 语句
2) [if]({{< ref "/c/language/statements/if" >}}) 语句带 `else` 子句
3) [switch]({{< ref "/c/language/statements/switch" >}}) 语句

## 循环语句

​	循环语句重复执行一条语句。

| *属性说明符序列*(可选)(C23 起) `while` `(` *表达式* `)` *语句* | (1)  |
| ------------------------------------------------------------ | ---- |
| *属性说明符序列*(可选)(C23 起) `do` *语句* `while` `(` *表达式* `)` `;` | (2)  |
| *属性说明符序列*(可选)(C23 起) `for` `(` *初始化子句* `;` *表达式*(可选) `;` *表达式*(可选) `)` *语句* | (3)  |

1) [while]({{< ref "/c/language/statements/while" >}}) 循环
2) [do-while]({{< ref "/c/language/statements/do" >}}) 循环
3) [for]({{< ref "/c/language/statements/for" >}}) 循环

## 跳转语句

​	跳转语句无条件地转移控制流。

| *属性说明符序列*(可选)(C23 起) `break ;`                | (1)  |
| ------------------------------------------------------- | ---- |
| *属性说明符序列*(可选)(C23 起) `continue ;`             | (2)  |
| *属性说明符序列*(可选)(C23 起) `return 表达式 (可选) ;` | (3)  |
| *attr-spec-seq*(可选)(C23 起) `goto identifier;`        | (4)  |

1) [break]({{< ref "/c/language/statements/break" >}}) 语句
2) [continue]({{< ref "/c/language/statements/continue" >}}) 语句
3) [return]({{< ref "/c/language/statements/return" >}}) 语句带可选的表达式
4) [goto]({{< ref "/c/language/statements/goto" >}}) 语句

## 参阅

​	语句的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/statements)
