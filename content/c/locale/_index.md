+++
title = "本地化支持"
date = 2025-04-15T19:23:53+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/locale](https://zh.cppreference.com/w/c/locale)

| 在标头 `<locale.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数)                             |
| [localeconv<br />](https://zh.cppreference.com/w/c/locale/localeconv) | 查询当前本地环境的数值及货币格式化细节 (函数)                |
| [lconv<br />](https://zh.cppreference.com/w/c/locale/lconv)  | [localeconv](https://zh.cppreference.com/w/c/locale/localeconv) 所返回的格式化细节 (结构体) |

## 本地环境类别

| [LC_ALL<br />LC_COLLATE<br />LC_CTYPE<br />LC_MONETARY<br />LC_NUMERIC<br />LC_TIME<br />](https://zh.cppreference.com/w/c/locale/LC_categories) | [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 所用的本地环境类别 (宏常量) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

## 参阅

**本地化库**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale)**