+++
title = "实验性 C 特性"
date = 2025-04-15T19:29:35+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/experimental](https://zh.cppreference.com/w/c/experimental)

​	C 标准委员会为未来的标准化出版C语言及库的实验性扩展。

​	注意：2012以前，此类出版使用 TR （ technical report ，技术报告）格式。自 2012 起 ISO 程序改用 TS （ technical specification ，技术规范）格式。

|                ISO 编号                |              名称               |                             状态                             |                             链接                             |
| :------------------------------------: | :-----------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|  ISO/IEC TR​	19769:2004  |      支持新字符类型的扩展       | 出版（ [ISO 商店](https://www.iso.org/standard/33907.html)）​	最终草案： [n1040](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1040.pdf) (2003-11-07) **✔**并入 C11 。 |                                                              |
| ISO/IEC TR​	24731-1:2007 |          边界检查接口           | 出版（ [ISO 商店](https://www.iso.org/standard/38841.html)）​	最终草案： [n1225](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1225.pdf) (2007-03-28) **✔**并入 C11 。 |                                                              |
|  ISO/IEC TR​	18037:2008  |     支持嵌入式处理器的扩展      | 出版（ [ISO 商店](https://www.iso.org/standard/51126.html)）​	最终草案：[n1169](https://www.open-std.org/jtc1/SC22/wg14/www/docs/n1169.pdf) (2006-04-04) |                                                              |
|  ISO/IEC TR​	24732:2009  |    支持十进制浮点算术的扩展     | 出版（ [ISO 商店](https://www.iso.org/standard/38842.html)）​	最终草案： [N1312](https://open-std.org/JTC1/SC22/WG14/www/docs/n1312.pdf) (2008-05-16) 为 TS 18661-2:2015 所代替 |                                                              |
|   ISO/IEC​	24747:2009    |     支持特殊数学函数的扩展      | 出版（ [ISO 商店](https://www.iso.org/standard/38857.html)）​	草案：[n1182](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1182.pdf) (2006-08-02) |                                                              |
| ISO/IEC TR​	24731-2:2010 |     支持动态分配函数的扩展      | 出版于 2010-11-24 （ [ISO 商店](https://www.iso.org/standard/51678.html)）​	草案： [n1248](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1248.pdf) (2007-08-15) | [dynamic](https://zh.cppreference.com/w/c/experimental/dynamic) |
|  ISO/IEC TS​	17961:2013  |          安全编码规则           | 出版于 2013-11-15 （[ISO 商店](https://www.iso.org/standard/61134.html)）​	草案： [n1624](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1624.pdf) (2012-06-26) TC1 出版于 2016-08-09 （ [ISO 商店](https://www.iso.org/standard/72086.html)） |                                                              |
| ISO/IEC TS​	18661-1:2014 |    浮点扩展：二进制浮点算术     | 出版于 2014-07-21 （ [ISO 商店](https://www.iso.org/standard/63146.html)）​	草案： [n1778](https://www.open-std.org/JTC1/sc22/wg14/www/docs/n1778.pdf) (2013-11-05)​	C2x 草案： [n2314](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2314.pdf) (2018-11-12)​	**✔**并入 C23 。 | [fpext1](https://zh.cppreference.com/w/c/experimental/fpext1) |
| ISO/IEC TS​	18661-2:2015 |    浮点扩展：十进制浮点算术     | 出版于 2015-02-11 ，修订于 2015-05-18 （ [ISO 商店](https://www.iso.org/standard/68882.html)）​	C2x 草案： [n2341](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2341.pdf) (2019-02-26)​	**✔**并入 C23 。 |                                                              |
| ISO/IEC TS​	18661-3:2015 |    浮点扩展：交流及扩展类型     | 出版于 2015-10-06 （ [ISO ISO 商店](https://www.iso.org/standard/65615.html)）。草案： [n1945](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1945.pdf) (2015-06-10) 。​	C2x 草案： [n2601](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2601.pdf) (2020-10-15)​	**✔**并入 C23 。 |                                                              |
| ISO/IEC TS​	18661-4:2015 |       浮点扩展：补充函数        | 出版于 2015-10-06 （ [ISO 商店](https://www.iso.org/standard/65616.html)）。草案： [n1950](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1950.pdf) (2015-06-10) 。​	C2x 草案： [n2401](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2401.pdf) (2019-06-23)​	**✔**部分并入 C23 。 | [fpext4](https://zh.cppreference.com/w/c/experimental/fpext4) |
| ISO/IEC TS​	18661-5:2016 |       浮点扩展：补充属性        | 出版于 2016-08-11 （ [ISO 商店](https://www.iso.org/standard/65617.html)）​	草案： [n2004](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2004.pdf) (2016-03-07) |                                                              |
| ISO/IEC TR​	24772-3:2020 |     编程语言 C 的脆弱性描述     | 出版于 2020-05-20 （ [ISO 商店](https://www.iso.org/standard/71093.html)）。草案： [n2169](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2169.pdf) (2017-04-07) |                                                              |
|                                        |          事务性内存 TS          | 早期草案： [n1961](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n1961.pdf) (2015-09-23) |                                                              |
|  ISO/IEC TS​	17961:xxxx  |       安全编码规则部分 2        |       早期开发，预计发布于 2023 ，可能作为 IS 而非 TS        |                                                              |
|           ISO/IEC CD TS 6010           |   C 的具备来源的内存对象模型    | 草案： [N3226](https://open-std.org/JTC1/SC22/WG14/www/docs/n3226.pdf) (2024-03-24) |                                                              |
|   ISO/IEC TS​	21938-1    | 并行扩展部分 1 ：基于线程的并行 | 早期草案： [n2170](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2170.pdf) (2017-09-21) **×**（废弃） |                                                              |
|                                        | 并行扩展部分 2 ：基于向量的并行 | 早期部分草案： [n2081](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2081.htm) (2016-09-15) **×**（废弃） |                                                              |

## 参阅

​	**实验性 C++ 特性**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/experimental)**
