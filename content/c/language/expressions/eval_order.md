+++
title = "求值顺序"
date = 2025-04-12T16:45:19+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/eval_order](https://zh.cppreference.com/w/c/language/eval_order)

​	除下列标出者，任意 C 运算符的运算数求值顺序，包括函数调用表达式的函数参数求值顺序，及任何表达式的子表达式求值顺序都是未指定的。编译器会以任意顺序对其求值，而且在同一表达式被再度求值时可选用另一种顺序。

​	C 中没有从左到右或从右到左求值的概念，不要将其与运算符的从左到右或从右到左结合性混淆：表达式 `f1() + f2() + f3()` 因为 `operator+` 的从左到右结合性而被分析成 `(f1() + f2()) + f3()`，但运行时对 `f3()` 的函数调用可以最先、最后，或在 f1() 与 f2() 之间求值。

## 定义

### 求值

​	对于每个表达式或子表达式，编译器会进行两种求值（两者都是可选的）：

- *值计算* ﻿（value computation）：计算表达式所返回的值。这可以涉及到确定对象身份（[左值求值](https://zh.cppreference.com/w/c/language/value_category)）或读取之前赋给对象的值（右值求值）
- *副效应* ﻿（side effect）：访问（读或写）以 [`volatile`](https://zh.cppreference.com/w/c/language/volatile) 左值指代的对象、修改（写）对象、原子同步(C11 起)、修改文件、修改浮点环境（若支持）或调用进行上述操作的函数。

​	若表达式不产生副效应，且编译器能确定其值不被使用，则表达式[可以不求值](https://zh.cppreference.com/w/c/language/as_if)。

### 定序

​	*先序于*（sequenced before）是一种同一线程内求值的非对称、传递性、对偶关系（若引入原子类型和内存屏障，则它可以扩展到线程间）。

- 若在子表达式 `E1` 和 `E2` 间存在*序列点（[sequence point](https://en.wikipedia.org/wiki/Sequence_point)）*，则 `E1` 的值计算和副效应都*先序于* `E2` 的所有值计算和副效应
- 若求值 A 先序于求值 B，则求值 A 将在求值 B 开始前完成。(C11 起)
- 若求值 A 不先序于求值 B，且求值 B 先序于求值 A，则求值 B 将在求值 A 开始前完成。(C11 起)
- 若求值 A 不先序于求值 B，且求值 B 不先序于求值 A，则存在二种可能：(C11 起)
  - 求值 A 与 B 是无顺序（unsequenced）的：它们可以以任意顺序进行，并且可以重叠（在执行的单一线程中，编译器可以交错地写入构成 A 与 B 的 CPU 指令）
  - 求值 A 与 B 是非确定顺序（indeterminably-sequenced）的：它们可以以任意顺序进行，但不可重叠：要么是 A 将在 B 之前完成，要么是 B 在 A 之前完成。顺序可以在相同表达式的下次求值前相反。

## 规则

1) 在所有函数参数和函数指代器的求值后，实际调用函数前，有一个序列点。
2) 在下例二元运算符的第一（左）运算数求值后，第二（右）运算数求值前，有一个序列点：`&&`（逻辑与）、`||`（逻辑或），及 `,`（逗号）。
3) 在条件运算符 `?:` 的第一（左）运算数求值后，第二或第三运算数（无论何者被求值）前，有一个序列点。
4) 在完整表达式（非子表达式的表达式：典型的是以分号为结尾者或 `if/switch/while/do` 的[控制语句](https://zh.cppreference.com/w/c/language/statements)）的求值后，下个完整表达式前，有一个序列点。
5) 在完整声明器的结尾，有一个序列点。(C99 起)
6) 在紧接库函数返回前，有一个序列点。(C99 起)
7) 在格式化 I/O 中，关联到每个转换指定符的动作后，有一个序列点（特别是 [scanf](https://zh.cppreference.com/w/c/io/fscanf) 写入同一变量的不同域， [printf](https://zh.cppreference.com/w/c/io/fprintf) 读取并以多于一次使用 `%n` 修改同一变量是良构的）。(C99 起)
8) 在每次通过库函数 [qsort](https://zh.cppreference.com/w/c/algorithm/qsort) 和 [bsearch](https://zh.cppreference.com/w/c/algorithm/bsearch) 调用比较函数前和紧随其后有序列点，在 [qsort](https://zh.cppreference.com/w/c/algorithm/qsort) 调用比较函数和移动对象之间也有序列点。(C99 起)
9) 属于运算符的运算数的值计算（但非副效应）先序于运算符的值计算（但非其副效应）。(C11 起)
10) 直接赋值运算符与所有复合赋值运算符的副效应（修改左参数）后序于左右参数的值计算（但非其副效应）。(C11 起)
11) 后自增和后自减运算符的值计算先序于其副效应。(C11 起)
12) 既非先序于亦非后序于另一函数调用的函数调用是非确定顺序的（构成不同函数调用的 CPU 指令不可能交错，即使函数被内联）。(C11 起)
13) 在[初始化器](https://zh.cppreference.com/w/c/language/initialization)列表表达式中，所有求值都是非确定顺序的14) 考虑到非确定顺序的函数调用，复合赋值运算符，及自增减运算符的前后缀形式都是单独求值。(C11 起)

## 未定义行为

1) 若对一个标量对象的副效应与另一个对同一标量对象的副效应相对无顺序，则[行为未定义](https://zh.cppreference.com/w/c/language/behavior#UB_.E4.B8.8E.E4.BC.98.E5.8C.96)。

```c
i = ++i + i++; // 未定义行为
i = i++ + 1; // 未定义行为
f(++i, ++i); // 未定义行为
f(i = -1, i = -1); // 未定义行为
```

2) 若一个标量对象上的副效应与另一个使用同一标量对象之值的值计算相对无顺序，则行为未定义。

```c
f(i, i++); // 未定义行为
a[i] = i++; // 未定义行为
```

3) 只要至少一个子表达式的排序容许这种无顺序副效应，就应用上述规则。

## 参阅

[运算符优先级](https://zh.cppreference.com/w/c/language/operator_precedence)，定义自源代码表示构建表达式的方式。

**求值顺序**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/eval_order)**