+++
title = "日期和时间工具"
date = 2025-04-15T19:18:25+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/chrono](https://zh.cppreference.com/w/c/chrono)

## 函数

### 时间操纵

| 在标头 `<time.h>` 定义                                     |                                                   |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [difftime<br />](https://zh.cppreference.com/w/c/chrono/difftime) | 计算时间差 (函数)                                 |
| [time<br />](https://zh.cppreference.com/w/c/chrono/time)  | 返回纪元开始经过的当前系统日历时间 (函数)         |
| [clock<br />](https://zh.cppreference.com/w/c/chrono/clock) | 返回未加工的程序启动时开始经过的处理器时间 (函数) |
| [timespec_get (C11)<br />](https://zh.cppreference.com/w/c/chrono/timespec_get) | 返回基于给定时间基底的日历时间 (函数)             |
| [timespec_getres (C23)<br />](https://zh.cppreference.com/w/c/chrono/timespec_getres) | 返回基于给定时间基底的日历时间的分辨率 (函数)     |

### 格式转换

| 在标头 `<time.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [asctime (C23 弃用)<br />asctime_s (C23 弃用)<br />](https://zh.cppreference.com/w/c/chrono/asctime) | 将 `struct tm` 对象转换成文本表示 (函数)                     |
| [ctime (C23 弃用)<br />ctime_s (C23 弃用)<br />](https://zh.cppreference.com/w/c/chrono/ctime) | 将 `struct time_t` 对象转换成文本表示 (函数)                 |
| [strftime<br />](https://zh.cppreference.com/w/c/chrono/strftime) | 将 `struct tm` 对象转换成自定义文本表示 (函数)               |
| 在标头 `<wchar.h>` 定义                                    |                                                              |
| [wcsftime (C95)<br />](https://zh.cppreference.com/w/c/chrono/wcsftime) | 将 `struct tm` 对象转换成自定义宽字符文本表示 (函数)         |
| 在标头 `<time.h>` 定义                                     |                                                              |
| [gmtime <br />gmtime_r (C23)<br />gmtime_s (C23)<br />](https://zh.cppreference.com/w/c/chrono/gmtime) | 将从纪元开始的时间转换成以协调世界时（UTC）表示的日历时间 (函数) |
| [localtime <br />localtime_r (C23)<br />localtime_s (C23)<br />](https://zh.cppreference.com/w/c/chrono/localtime) | 将从纪元开始的时间转换成以本地时间表示的日历时间 (函数)      |
| [mktime<br />](https://zh.cppreference.com/w/c/chrono/mktime) | 将日历时间转换成纪元开始经过的时间 (函数)                    |

## 常量

| 在标头 `<time.h>` 定义                                     |                               |
| ------------------------------------------------------------ | ----------------------------- |
| [CLOCKS_PER_SEC<br />](https://zh.cppreference.com/w/c/chrono/CLOCKS_PER_SEC) | 处理器每秒时钟滴答数 (宏常量) |

## 类型

| 在标头 `<time.h>` 定义                                     |                                      |
| ------------------------------------------------------------ | ------------------------------------ |
| [tm<br />](https://zh.cppreference.com/w/c/chrono/tm)      | 日历时间类型 (结构体)                |
| [time_t<br />](https://zh.cppreference.com/w/c/chrono/time_t) | 从纪元开始的日历时间类型 (typedef)   |
| [clock_t<br />](https://zh.cppreference.com/w/c/chrono/clock_t) | 从时点开始的处理器时间类型 (typedef) |
| [timespec (C11)<br />](https://zh.cppreference.com/w/c/chrono/timespec) | 单位为秒和纳秒的时间 (结构体)        |

## 参阅

​	**C 日期和时间工具**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/chrono/c)**
