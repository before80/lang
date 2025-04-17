+++
title = "C 的历史"
date = 2025-04-13T14:07:08+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/history](https://zh.cppreference.com/w/c/language/history)

## 早期 C

- 1969：基于 BCPL 创建 B 语言，以替代 PDP-7 汇编器作为 Unix 的系统编程语言
  - 增加运算符 `++`、`--`、复合赋值，保持为与 BCPL 类似的无类型语言

- 1971：将 B 移植到 PDP-11 时，创建了 NB 语言（“new B”，即新的 B 语言）
  - 支持类型（`int`、`char`、数组和指针），数组到指针转换，编译为机器码

- 1972：语言更名为 C
  - `struct`、运算符 `&&` 及 `||`、预处理器、可移植 I/O

- 1973：以 C 重写 Unix
  - `unsigned`、`long`、`union`、枚举、增强类型安全性

- 1978：《The C Programming Language》，第1版

## 标准 C

- 1983：ANSI 建立 X3J11 委员会
- 1988：《The C Programming Language》，第2版
- 1989：**C89**，ANSI C 标准出版
  1. 代码化的既存实践
  2. 新特性：`volatile`、`enum`、`signed`、`void`、本地环境
  3. 来自 C++：`const`、函数原型

- 1990：**C90**，ANSI C 标准被采纳为 ISO/IEC 9899-1990
- 1994：技术勘误 1（ISO/IEC 9899:1990/Cor.1:1994）
  - [44 个小更改](https://open-std.org/JTC1/SC22/WG14/www/docs/tc1.htm)

- 1995：**C95**（ISO/IEC 9899:1990/Amd.1:1995）（[在线商店](http://infostore.saiglobal.com/store/Details.aspx?DocN=isoc000767513)）
  1. 极大扩充了宽和多字节字符支持（[`<wctype.h>`]({{< ref "/c/header/wctype" >}})、[`<wchar.h>`]({{< ref "/c/header/wchar" >}})、对流 I/O 的添加和更改等）
  2. 双标符、[`<iso646.h>`]({{< ref "/c/header/iso646" >}})

- 1996：技术勘误 2（ISO/IEC 9899:1990/Cor.2:1996）
  - [24 个小更改](https://open-std.org/JTC1/SC22/WG14/www/docs/tc2.htm)

- 1999：**C99**（ISO/IEC 9899:1999）
  1. 新特性：`bool`、`long long`、[`<stdint.h>`]({{< ref "/c/header/stdint" >}})、[`<inttypes.h>`]({{< ref "/c/header/inttypes" >}})、`restrict`、复合字面量、变长度数组、灵活数组成员、指派初始化器、[`<fenv.h>`]({{< ref "/c/header/fenv" >}})、变参数宏、复数、`__func__`、十六进制浮点格式（`%a`）、{lc|lconv}} 的货币格式化、[isblank](https://zh.cppreference.com/w/c/string/byte/isblank)、窄与宽字符串字面量的连接、枚举的尾逗号、类函数宏的空实参、`STDC_*` 语用、`va_copy`、[tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 的空返回、[setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 中的空指针、[printf](https://zh.cppreference.com/w/c/io/fprintf) 的 `hh` 与 `ll` 长度指定符、[snprintf](https://zh.cppreference.com/w/c/io/fprintf)、[_Exit](https://zh.cppreference.com/w/c/program/_Exit)、[`<tgmath.h>`]({{< ref "/c/header/tgmath" >}})、仿 POSIX [strftime](https://zh.cppreference.com/w/c/chrono/strftime) 说明符
  2. 来自 C++：`inline`、混合声明与代码、`for` 循环的初始化子句中的声明、`//` 注释、源代码中的通用字符名
  3. 移除隐式函数声明和隐式 `int`

- 2001：技术勘误 1（ISO/IEC 9899:1999/Cor.1:2001(E)）
  - [修正 11 个缺陷](https://open-std.org/JTC1/SC22/WG14/www/docs/9899tc1/)

- 2004：技术勘误 2（ISO/IEC 9899:1999/Cor.2:2004(E)）
- 2004：Unicode TR（ISO/IEC TR 19769:2004）（[ISO商店](http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=33907)）（[2013-11-07 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1040.pdf)）
- 2007：技术勘误 3（ISO/IEC 9899:1999/Cor.3:2007(E)）（[2007-09-07草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf)）
  - 弃用 [gets](https://zh.cppreference.com/w/c/io/gets)

- 2007：边界检查接口 TR（ISO/IEC TR 24731-1:2007）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=38841)）（[2007-03-28 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1225.pdf)）
- 2008：嵌入式 TR（ISO/IEC TR 18037:2008）（[ISO商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=51126)）（[2003-09-24 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1021.pdf)）
- 2009：十进制浮点数 TR（ISO/IEC TR 24732:2009）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=38842)）（[2007-07-05 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1241.pdf)）
- 2009：特殊数学函数 TR（ISO/IEC TR 24747:2009）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=38857)）（[2006-08-02 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1182.pdf)）
- 2010：动态分配函数 TR（ISO/IEC TR 24731-2:2010）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=51678)）（[2007-08-15 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1248.pdf)）
- 2011：**C11**（ISO/IEC 9899:2011）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=57853)）（[ANSI 商店](http://webstore.ansi.org/RecordDetail.aspx?sku=INCITS%2fISO%2fIEC+9899-2012#.UGCvLIHyaHM)）（[2011-04-12 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)）
  1. 具线程的内存模型、[`<stdatomic.h>`]({{< ref "/c/header/stdatomic" >}})、[`<threads.h>`]({{< ref "/c/header/threads" >}})、泛型函数、`alignas/alignof`、 `noreturn`、`static_assert`、可分析性扩展、对复数和虚数类型的扩展、匿名结构体与联合体、独占文件打开模式、 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)
  2. 移除 [gets](https://zh.cppreference.com/w/c/io/gets)
  3. 来自边界检查接口 TR：边界检查接口
  4. 来自 Unicode TR：`char16_t`、`char32_t`，及 [`<uchar.h>`]({{< ref "/c/header/uchar" >}})

- 2012：技术勘误 1（ISO/IEC 9899:2011/Cor 1:2012）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=61717)）
  - 修正 [DR 411](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_411)

- 2013：安全代码规则 TS（ISO/IEC TS 17961:2013）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=61134)）（[2012-12-26](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1624.pdf) 草案）
- 2014：FP TS 部分 1：二进制浮点算术（ISO/IEC TS 18661-1:2014）（[ISO 商店](http://www.iso.org/iso/catalogue_detail.htm?csnumber=63146)）（[2013 草案](http://www.open-std.org/JTC1/sc22/wg14/www/docs/n1778.pdf)）
  1. 提供对 C11 的更改（主要对附录 F），以覆盖所有基本要求及一些 IEC 60559:2011 的推荐（C11 构建于 IEC 60559:1989）

- 2015：FP TS 部分 2：十进制浮点算术（ISO/IEC TS 18661-2:2015）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_ics/catalogue_detail_ics.htm?csnumber=68882)) ([2015 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1912.pdf)）
  1. 提供对 C11 的更改，以支持所有要求，加上一些 IEC 60559:2011 对十进制浮点算术的基本推荐。它替代了 ISO/IEC TR 24732:2009。

- 2015：FP TS 部分 3：交换及扩展类型（ISO/IEC TS 18661-3:2015）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=65615)）（[2015 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1945.pdf)）
  1. 提供对 C11 的更改，以支持 IEC 60559:2011 对扩展浮点格式及交换格式的推荐，包括算术和非算术。

- 2015：FP TS 部分 4：补充的函数（ISO/IEC TS 18661-4:2015）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=65616)）（[2015 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1950.pdf)）
  1. 提供对 C11 的更改，以支持所有 IEC 60559:2011 推荐的数学运算，包括 π 单位的三角函数、平方根倒数、复利等。

- 2016：FP TS 部分 5：补充的属性（ISO/IEC TS 18661-5:2016）（[ISO 商店](http://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.htm?csnumber=65617)）（[2016 草案](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2004.pdf)）
  1. 提供对 C11 的更改，以支持所有 IEC 60559:2011 推荐的补充属性（求值模型、异常处理、可再现性等）

- 2018: **C17**（ISO/IEC 9899:2018）（[最终草案](https://files.lhmouse.com/standards/ISO C N2176.pdf)）。

  - [主条目：C17](https://zh.cppreference.com/w/c/17)

  - |              C17 中修正的缺陷报告（ 54 个缺陷）              |
    | :----------------------------------------------------------: |
    | [DR 400](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_400)[DR 401](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_401)[DR 402](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_402)[DR 403](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_403)[DR 404](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_404)[DR 405](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_405)[DR 406](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_406)[DR 407](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_407)[DR 410](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_410)[DR 412](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_412)[DR 414](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_414)[DR 415](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_415)[DR 416](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_416)[DR 417](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_417)[DR 419](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_419)[DR 423](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_423)[DR 426](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_426)[DR 428](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_428)[DR 429](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_429)[DR 430](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_430)[DR 431](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_431)[DR 433](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_433)[DR 434](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_434)[DR 436](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_436)[DR 437](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_437)[DR 438](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_438)[DR 439](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_439)[DR 441](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_441)[DR 444](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_444)[DR 445](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_445)[DR 447](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_447)[DR 448](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_448)[DR 450](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_450)[DR 452](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_452)[DR 453](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_453)[DR 457](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_457)[DR 458](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_458)[DR 459](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_459)[DR 460](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_460)[DR 462](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_462)[DR 464](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_464)[DR 465](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_465)[DR 468](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_468)[DR 470](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_470)[DR 471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_471)[DR 472](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_472)[DR 473](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_473)[DR 475](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_475)[DR 477](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_477)[DR 480](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_480)[DR 481](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_481)[DR 485](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_485)[DR 487](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_487)[DR 491](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2244.htm#dr_491) |



- 2023 **C23** (ISO/IEC 9899:2024)。C23 是 C 标准的当前修订版。

  - [主条目：C23](https://zh.cppreference.com/w/c/23)

  - |              C23 中修正的缺陷报告（？ 个缺陷）               |
    | :----------------------------------------------------------: |
    | [DR 440](https://open-std.org/JTC1/SC22/WG14/www/docs/n2379.htm)[DR 432](https://open-std.org/JTC1/SC22/WG14/www/docs/n2326.htm)[DR 467](https://open-std.org/JTC1/SC22/WG14/www/docs/n2326.htm)[DR 476](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_476)[DR 482](https://open-std.org/JTC1/SC22/WG14/www/docs/n2324.htm)[DR 488](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_488)[DR 489](https://open-std.org/JTC1/SC22/WG14/www/docs/n2713.htm)[DR 494](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_494)[DR 496](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_496)[DR 497](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_497)[DR 499](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_499) |



## 未来发展

- 并行 TS（草案 [n2017](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2017.pdf) 2016-03-10）
- 事务性内存 TS（草案 [n1961](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1961.pdf) 2015-09-23）
- **C**（最新草案 [n3467](https://open-std.org/JTC1/SC22/WG14/www/docs/n3467.pdf) 2025-02-09）

1. 未赋予 DR 状态的问题列表：（[N2556](https://open-std.org/JTC1/SC22/WG14/www/docs/n2556.pdf) 2020-08-02）

[主条目：C29](https://zh.cppreference.com/mwiki/index.php?title=c/29&action=edit&redlink=1)?

下个主要 C 语言标准修订版

## 参阅

**C++ 的历史**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/history)**

## 外部链接

| 1.   | [C 语言的发展](https://www.bell-labs.com/usr/dmr/www/chist.html)，作者 Dennis M. Ritchie |
| ---- | ------------------------------------------------------------ |
| 2.   | [C99 标准基本原理](https://www.open-std.org/jtc1/sc22/wg14/www/C99RationaleV5.10.pdf) |
