+++
title = "动态内存扩展"
date = 2025-04-15T19:32:03+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/experimental/dynamic](https://zh.cppreference.com/w/c/experimental/dynamic)

​	对 C 库的扩展部分 II ：动态分配函数 (Extensions to the C Library Part II: Dynamic Allocation Functions) ， ISO/IEC TR 24731-2:2010 ，为 C 标准库定义下列新组件：

| __STDC_ALLOC_LIB__<br />                                   | 指遵从性等级的 long 类型常量 (宏常量)                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [fmemopen (动态内存 TR)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/dynamic/fmemopen&action=edit&redlink=1) | 把固定大小的内存缓冲区作为 I/O 流打开 (函数)                 |
| [open_memstream (动态内存 TR)<br />open_wmemstream (动态内存 TR)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/dynamic/open_memstream&action=edit&redlink=1) | 把动态改变大小的内存缓冲区作为 I/O 流打开 (函数)             |
| [asprintf (动态内存 TR)<br />aswprintf (动态内存 TR)<br />vasprintf<br />vaswprintf<br />](https://zh.cppreference.com/w/c/experimental/dynamic/asprintf) | [sprintf](https://zh.cppreference.com/w/c/io/fprintf) 等的变体，写入自动分配的缓冲区并返回指向它的指针 (函数) |
| [getline (动态内存 TR)<br />getwline (动态内存 TR)<br />getdelim<br />getwdelim<br />](https://zh.cppreference.com/w/c/experimental/dynamic/getline) | 从流读入至动态改变大小的缓冲区，直到分隔符/行尾 (函数)       |
| 在标头 `<string.h>` 定义                                   |                                                              |
| [strdup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strdup) | 分配字符串的副本 (函数)                                      |
| [strndup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strndup) | 分配字符串副本，至多到指定的大小 (函数)                      |

​	此库扩展亦引入赋值分配字符 `m` ，用于 [fscanf](https://zh.cppreference.com/w/c/io/fscanf) 和 [fwscanf](https://zh.cppreference.com/w/c/io/fwscanf) 函数族中的 `%s` 、 `%[` 及 `%c` 转换说明符。

## 注解

​	函数 `fmemopen` 、 `open_memstream` 、 `open_wmemstream` 、 `getdelim` 、 `getline` 、 `strdup` 、 `strndup` 及对 `fscanf` 的扩展于 [POSIX (ISO/IEC 9945:2003)](http://pubs.opengroup.org/onlinepubs/9699919799/) 可用。

​	函数 `asprintf` 及 `vasprintf` 于 Linux 标准基础 (Linux Standard Base) (ISO/IEC IS 23360:2006) 可用。