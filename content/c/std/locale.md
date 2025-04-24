
+++
title = "<locale.h>"
date = 2025-04-24T18:06:28+08:00
weight = 90
type = "docs"
description = "本地化工具"
isCJKLanguage = true
draft = false

+++

## 类型



### lconv

原址：[https://zh.cppreference.com/w/c/locale/lconv](https://zh.cppreference.com/w/c/locale/lconv)

作用：localeconv 所返回的格式化细节  (结构体)

备注：
```c
// 在标头 <locale.h> 定义
struct lconv;
```

​	`struct lconv` 含有 C 本地环境定义的数值和货币格式化规则。此结构体的对象可由 [localeconv](https://zh.cppreference.com/w/c/locale/localeconv) 获得。`std::lconv` 的成员为 `char` 类型和 `char*` 类型的值。除了 `decimal_point`，每个 `char*` 成员都可以指向空字符（即为空 C 字符串）。`char` 类型成员均为非负数，而且若任一者在当前 C 本地环境中不可用，则为 [CHAR_MAX](https://zh.cppreference.com/w/c/types/limits)。

### 成员对象

#### 非货币数值格式化参数

| char* decimal_point<br /> | 用作小数点的字符 (公开成员对象)               |
| --------------------------- | --------------------------------------------- |
| char* thousands_sep<br /> | 用于在小数点前分隔数位组的字符 (公开成员对象) |
| char* grouping<br />      | 字符串，其元素指示数位组的大小 (公开成员对象) |

#### 货币数值格式化参数

| char* mon_decimal_point<br /> | 用作小数点的字符 (公开成员对象)               |
| ------------------------------- | --------------------------------------------- |
| char* mon_thousands_sep<br /> | 用于在小数点前分隔数位组的字符 (公开成员对象) |
| char* mon_grouping<br />      | 字符串，其元素指示数位组的大小 (公开成员对象) |
| char* positive_sign<br />     | 用于指示非负货币量的字符串 (公开成员对象)     |
| char* negative_sign<br />     | 用于指示负货币量的字符串 (公开成员对象)       |

#### 本地货币数值格式化参数

| char* currency_symbol<br /> | 当前 C 本地环境中用于通货的符号 (公开成员对象)               |
| ----------------------------- | ------------------------------------------------------------ |
| char frac_digits<br />      | 货币量中小数点后显示的位数 (公开成员对象)                    |
| char p_cs_precedes<br />    | 若 `currency_symbol` 置于非负值前则为 `1`，于其后则为 `0` (公开成员对象) |
| char n_cs_precedes<br />    | 若 `currency_symbol` 置于负值前则为 `1`，于其后则为 `0` (公开成员对象) |
| char p_sep_by_space<br />   | 指示 `currency_symbol`、`positive_sign` 及非负货币值的分隔 (公开成员对象) |
| char n_sep_by_space<br />   | 指示 `currency_symbol`、`positive_sign` 及负货币值的分隔 (公开成员对象) |
| char p_sign_posn<br />      | 指示非负货币值中 `positive_sign` 的位置 (公开成员对象)       |
| char n_sign_posn<br />      | 指示负货币值中 `negative_sign` 的位置 (公开成员对象)         |

#### 国际货币数值格式化参数

| char* int_curr_symbol<br />         | 当前 C 本地环境中用作国际通货名的字符串 (公开成员对象)       |
| ------------------------------------- | ------------------------------------------------------------ |
| char int_frac_digits<br />          | 国际货币量中小数点后显示的位数 (公开成员对象)                |
| char int_p_cs_precedes (C99)<br />  | 若 `currency_symbol` 置于非负值前则为 `1`，于其后则为 `0` (公开成员对象) |
| char int_n_cs_precedes (C99)<br />  | 若 `currency_symbol` 置于负值前则为 `1`，于其后则为 `0` (公开成员对象) |
| char int_p_sep_by_space (C99)<br /> | 指示 `int_curr_symbol`、`positive_sign` 及非负国际货币值的分隔 (公开成员对象) |
| char int_n_sep_by_space (C99)<br /> | 指示 `int_curr_symbol`、`positive_sign` 及负国际货币值的分隔 (公开成员对象) |
| char int_p_sign_posn (C99)<br />    | 指示非负国际货币值中 `positive_sign` 的位置 (公开成员对象)   |
| char int_n_sign_posn (C99)<br />    | 指示负国际货币值中 `positive_sign` 的位置 (公开成员对象)     |

​	按照数值判读 `grouping` 和 `mon_grouping` 所指向的 C 字符串。遇到终止 `'\0'` 时，假设剩下的数位重复采用最后见到的值。若遇到 [CHAR_MAX](https://zh.cppreference.com/w/c/types/limits)，则不再将数位分组。典型的三位一组的分组是 `"**\003**"`。

​	`p_sep_by_space`、`n_sep_by_space`、`int_p_sep_by_space`、`int_n_sep_by_space` 的值判读如下：

| `0`  | 通货符号和值间无空格分隔         |
| ---- | -------------------------------- |
| `1`  | 符号紧贴通货符号，值为空格所分隔 |
| `2`  | 符号紧贴值，通货符号为空格所分隔 |

​	`p_sign_posn`、`n_sign_posn`、`int_p_sign_posn`、`int_n_sign_posn` 的值判读如下：

| `0`  | 以围绕值和通货符号的括号表示正负号 |
| ---- | ---------------------------------- |
| `1`  | 正负号在值与通货符号前             |
| `2`  | 正负号在值与通货符号后             |
| `3`  | 正负号在通货符号前                 |
| `4`  | 正负号在通货符号后                 |

**示例**

```c
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    setlocale(LC_ALL, "ja_JP.UTF-8");
    struct lconv* lc = localeconv();
    printf("Japanese currency symbol: %s(%s)\n", lc->currency_symbol, lc->int_curr_symbol);
}
```

​	可能的输出：

```txt
Japanese currency symbol: ￥(JPY)
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/2 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/2 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/2 Localization <locale.h> （第 223 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/2 Localization <locale.h> （第 204 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [localeconv<br />](https://zh.cppreference.com/w/c/locale/localeconv) | 查询当前本地环境的数值及货币格式化细节 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| **lconv** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/lconv)** |                                               |






## 枚举




## 宏



### LC_ALL

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### LC_COLLATE

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### LC_CTYPE

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### LC_MONETARY

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### LC_NUMERIC

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### LC_TIME

原址：[https://zh.cppreference.com/w/c/locale/LC_categories](https://zh.cppreference.com/w/c/locale/LC_categories)

作用：setlocale 所用的本地环境类别  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
#define LC_ALL      /* 由实现定义 */
#define LC_COLLATE  /* 由实现定义 */
#define LC_CTYPE    /* 由实现定义 */
#define LC_MONETARY /* 由实现定义 */
#define LC_NUMERIC  /* 由实现定义 */
#define LC_TIME     /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，适合用作 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的首个实参。

| 常量          | 解释                              |
| ------------- | --------------------------------- |
| `LC_ALL`      | 选择整个 C 本地环境               |
| `LC_COLLATE`  | 选择 C 本地环境中的校排类别       |
| `LC_CTYPE`    | 选择 C 本地环境中的字符分类类别   |
| `LC_MONETARY` | 选择 C 本地环境中的货币格式化类别 |
| `LC_NUMERIC`  | 选择 C 本地环境中的数值格式化类别 |
| `LC_TIME`     | 选择 C 本地环境中的时间格式化类别 |

​	`<locale.h>` 中可以定义附加宏常量，名称以 `LC_` 后随至少一个大写字母开始。例如， POSIX 规范要求 `LC_MESSAGES`（此外还控制 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)）， ISO/IEC 30112:2014（[2014 方案](https://www.open-std.org/JTC1/SC35/WG5/docs/30112d10.pdf)）额外定义 `LC_IDENTIFICATION`、`LC_XLITERATE`、`LC_NAME`、`LC_ADDRESS`、`LC_TELEPHONE`、`LC_PAPER`、`LC_MEASUREMENT` 和 `LC_KEYBOARD`，它们均为 GNU C 库所支持（除了 `LC_XLITERATE`）。

**注解**

#### glibc 中的本地环境类别

​	glibc 除了 C 标准要求的 5 个类别外，还额外支持 7 个类别，以及一个默认项：

| glibc 本地环境类别常量 | 解释                                                  |
| ---------------------- | ----------------------------------------------------- |
| `LC_ADDRESS`           | 选择 C 本地环境中的邮政地址格式类别                   |
| `LC_IDENTIFICATION`    | 选择 C 本地环境中的类别版本与状态                     |
| `LC_KEYBOARD`          | 选择 C 本地环境中的键盘鉴别类别                       |
| `LC_MEASUREMENT`       | 选择 C 本地环境中的度量系统信息类别                   |
| `LC_NAME`              | 选择 C 本地环境中的人名书写格式类别                   |
| `LC_PAPER`             | 选择 C 本地环境中的纸张格式类别                       |
| `LC_TELEPHONE`         | 选择 C 本地环境中的电话号码格式（和其他电话信息）类别 |
| `LANG`                 | 选择尚未指定的类别                                    |

​	其中 `LC_ALL` 的优先级高于所有特定类别，而每个特定类别都优先于 `LANG` 。具体而言：

1. 若设置 `LC_ALL` 为 `"zh_CN.UTF-8"` ，则不论 `LC_*` 和 `LANG` 原为何值，每个分类都会被设为 `"zh_CN.UTF-8"` 。
2. 若未设置 `LC_ALL` ，而专门设置 `LANG` 为 `"zh_CN.UTF-8"` ，并设置某 `LC_*` 为`"en_US.UTF-8"` ，则其所对应的本地环境类别被设为 `"en_US.UTF-8"` 。
3. 若未设置 `LC_ALL` 和某些类别的 `LC_*` ，并设置 `LANG` 为 `"zh_CN.UTF-8"` ，则这些 `LC_*` 所对应的本地环境被设为 `"zh_CN.UTF-8"` 。

​	所以，对于不同的目的，应该用不同方式设置本地环境：

- 例如，若需要纯中文的系统，则可调用 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LC_ALL, "zh_CN.UTF-8")` 或 `[setlocale](http://zh.cppreference.com/w/c/locale/setlocale)(LANG, "zh_CN.UTF-8")` 。可以但没必要设置二次。
- 若只需要输入中文的环境，而其他界面信息和格式为英文，则可使用

```
setlocale(LC_CTYPE, "zh_CN.UTF-8");
setlocale(LANG, "en_US.UTF-8");
```

- 若有特殊的本地环境定制需求，例如使用中文 GBK 字符集、用 ISO-8859-1 字符集的大英数字系统、用 ISO-8859-15 字符集的德国度量系统……，则应逐一设置 `LC_*` ：

```
setlocale(LC_TYPE, "zh_CN.GBK/GBK");
setlocale(LC_NUMERIC, "en_GB.ISO-8859-1");
setlocale(LC_MESUREMENT, "de_DE.ISO-8859-15@euro");
// 以及其他类别
```

- 若只需要应用默认 `"C"` （ `"POSIX"` 为其别名）本地环境，则无需任何设置代码。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.UTF-8"); // C 本地环境将为启用 UTF-8 的英文
    setlocale(LC_NUMERIC, "de_DE.utf8"); // 小数点将为德文
    setlocale(LC_TIME, "ja_JP.utf8");    // 日期/时间格式将为日文
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"数值: %.2f\n日期: %Ls\n", 3.14, str);
}
```

​	输出：

```txt
数值: 3,14
日期: 金曜日 2023年09月15日 20時04分14秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11/3 Localization <locale.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11/3 Localization <locale.h> （第 224 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11/3 Localization <locale.h> （第 205 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4 LOCALIZATION <locale.h>

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数) |
| ------------------------------------------------------------ | -------------------------------- |
| **本地环境类别**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/LC_categories)** |                                  |





### NULL

原址：[https://zh.cppreference.com/w/c/types/NULL](https://zh.cppreference.com/w/c/types/NULL)

作用：实现定义的空指针常量  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
// 在标头 <stddef.h> 定义
// 在标头 <stdio.h> 定义
// 在标头 <stdlib.h> 定义
// 在标头 <string.h> 定义
// 在标头 <time.h> 定义
// 在标头 <wchar.h> 定义
#define NULL /* 由实现定义 */
```

​	宏 `NULL` 是实现定义的空指针常量，可为

- 值为 `0` 的整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F)
- [转换为](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2) `void*` 的值为 `0` 的整数常量表达式



- 预定义常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr)

(C23 起)



​	空指针常量能[转换](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2)为任何指针类型；转换结果是该类型的空指针值。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/stddef.h.html) `NULL` 被定义为转换为 `void*` 的值为 `0` 的整数常量表达式。

**可能的实现**

```c
// 兼容 C++： #define NULL 0 // 不兼容 C++： #define NULL (10*2 - 20) #define NULL ((void*)0) // C23 起（与 C++11 及之后兼容） #define NULL nullptr
```

**示例**

```c
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 任何类型的指针均能设为 NULL
    int* p = NULL;
    struct S *s = NULL;
    void(*f)(int, double) = NULL;
    printf("%p %p %p\n", (void*)p, (void*)s, (void*)(long)f);
 
    // 多数返回指针的函数用空指针指示错误
    char *ptr = malloc(0xFULL);
    if (ptr == NULL)
        printf("Out of memory");
    else
        printf("ptr = %#" PRIxPTR"\n", (uintptr_t)ptr);
    free(ptr);
}
```

​	可能的输出：

```txt
(nil) (nil) (nil)
ptr = 0xc001cafe
```

**参阅**

| [nullptr_t (C23)<br />](https://zh.cppreference.com/w/c/types/nullptr_t) | 预定义空指针常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr) 的类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **NULL** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/NULL)** |                                                              |






## 函数



### localeconv

原址：[https://zh.cppreference.com/w/c/locale/localeconv](https://zh.cppreference.com/w/c/locale/localeconv)

作用：查询当前本地环境的数值及货币格式化细节  (函数)

备注：
```c
// 在标头 <locale.h> 定义
struct lconv *localeconv(void);
```

​	`localeconv` 函数获得指向 `struct `[lconv](https://zh.cppreference.com/w/c/locale/lconv) 类型的静态对象的指针，该对象表示当前 C 本地环境的数值和货币格式化规则。

**参数**

​	（无）

**返回值**

​	指向当前 `struct `[lconv](https://zh.cppreference.com/w/c/locale/lconv) 对象的指针。

**注解**

​	通过返回的指针修改对象是未定义行为。

​	`localeconv` 修改静态对象，从不同线程调用它而不进行同步是未定义行为。

**示例**

```c
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    setlocale(LC_MONETARY, "en_IN.utf8");
    struct lconv *lc = localeconv();
    printf("本地货币符号: %s\n", lc->currency_symbol);
    printf("国际货币符号: %s\n", lc->int_curr_symbol);
}
```

​	输出：

```txt
本地货币符号: ₹
国际货币符号: INR
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11.2.1 The localeconv function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11.2.1 The localeconv function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11.2.1 The localeconv function （第 225-230 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11.2.1 The localeconv function （第 206-211 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4.2.1 The localeconv function

**参阅**

| [setlocale<br />](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------ |
| [lconv<br />](https://zh.cppreference.com/w/c/locale/lconv) | **localeconv** 所返回的格式化细节 (结构体) |
| **localeconv** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/localeconv)** |                                            |





### setlocale

原址：[https://zh.cppreference.com/w/c/locale/setlocale](https://zh.cppreference.com/w/c/locale/setlocale)

作用：获取和设置当前 C 本地环境  (函数)

备注：
```c
// 在标头 <locale.h> 定义
char* setlocale( int category, const char* locale );
```

​	`setlocale` 函数安装指定的系统本地环境或其一部分，作为新的 C 本地环境。修改保持效果，并影响所有关乎本地环境的 C 库函数执行，到下次调用 `setlocale` 为止。若 `locale` 为空指针，则 `setlocale` 查询当前 C 本地环境而不修改它。

**参数**

| category | -    | 本地环境类别标识符，[`LC_xxx`](https://zh.cppreference.com/w/c/locale/LC_categories) 宏之一。可为 0。 |
| -------- | ---- | ------------------------------------------------------------ |
| locale   | -    | 特定于系统的本地环境标识符。对于操作系统的环境支持字段为命令行“locale -a”的合法列出内容值，对于用户偏好的本地环境为 `""`，对于最小本地环境为 `"C"`。 |

**返回值**

​	指向窄空终止字符串的指针，它表示应用更改后的 C 本地环境，若存在。或在失败时为空指针。

​	程序中可以于后来，以其所返回字符串的副本和该调用中所用的类别值一起，调用 `setlocale` 来恢复本地环境到此调用结束时的状态。

**注解**

​	程序启动过程中，运行任何用户代码前都会执行 `setlocale([LC_ALL](http://zh.cppreference.com/w/c/locale/LC_categories), "C");` 的等价代码。

​	虽然返回类型为 `char*`，但修改其所指向的字符是未定义行为。

​	因为 `setlocale` 会修改全局状态，并影响依赖本地环境的函数的执行，故而一个线程调用它，同时另一个线程执行任何下列函数是未定义行为：[fprintf](https://zh.cppreference.com/w/c/io/fprintf)、[isprint](https://zh.cppreference.com/w/c/string/byte/isprint)、[iswdigit](https://zh.cppreference.com/w/c/string/wide/iswdigit)、[localeconv](https://zh.cppreference.com/w/c/locale/localeconv)、[tolower](https://zh.cppreference.com/w/c/string/byte/tolower)、[fscanf](https://zh.cppreference.com/w/c/io/fscanf)、[ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct)、[iswgraph](https://zh.cppreference.com/w/c/string/wide/iswgraph)、[mblen](https://zh.cppreference.com/w/c/string/multibyte/mblen)、[toupper](https://zh.cppreference.com/w/c/string/byte/toupper)、[isalnum](https://zh.cppreference.com/w/c/string/byte/isalnum)、[isspace](https://zh.cppreference.com/w/c/string/byte/isspace)、[iswlower](https://zh.cppreference.com/w/c/string/wide/iswlower)、[mbstowcs](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs)、[towlower](https://zh.cppreference.com/w/c/string/wide/towlower)、[isalpha](https://zh.cppreference.com/w/c/string/byte/isalpha)、[isupper](https://zh.cppreference.com/w/c/string/byte/isupper)、[iswprint](https://zh.cppreference.com/w/c/string/wide/iswprint)、[mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc)、[towupper](https://zh.cppreference.com/w/c/string/wide/towupper)、[isblank](https://zh.cppreference.com/w/c/string/byte/isblank)、[iswalnum](https://zh.cppreference.com/w/c/string/wide/iswalnum)、[iswpunct](https://zh.cppreference.com/w/c/string/wide/iswpunct)、`setlocale`、[wcscoll](https://zh.cppreference.com/w/c/string/wide/wcscoll)、[iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl)、[iswalpha](https://zh.cppreference.com/w/c/string/wide/iswalpha)、[iswspace](https://zh.cppreference.com/w/c/string/wide/iswspace)、[strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll)、[wcstod](https://zh.cppreference.com/w/c/string/wide/wcstof)、[isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit)、[iswblank](https://zh.cppreference.com/w/c/string/wide/iswblank)、[iswupper](https://zh.cppreference.com/w/c/string/wide/iswupper)、[strerror](https://zh.cppreference.com/w/c/string/byte/strerror)、[wcstombs](https://zh.cppreference.com/w/c/string/multibyte/wcstombs)、[isgraph](https://zh.cppreference.com/w/c/string/byte/isgraph)、[iswcntrl](https://zh.cppreference.com/w/c/string/wide/iswcntrl)、[iswxdigit](https://zh.cppreference.com/w/c/string/wide/iswxdigit)、[strtod](https://zh.cppreference.com/w/c/string/byte/strtof)、[wcsxfrm](https://zh.cppreference.com/w/c/string/wide/wcsxfrm)、[islower](https://zh.cppreference.com/w/c/string/byte/islower)、[iswctype](https://zh.cppreference.com/w/c/string/wide/iswctype)、[isxdigit](https://zh.cppreference.com/w/c/string/byte/isxdigit)。

​	POSIX 亦定义名为 "POSIX" 的本地环境，它始终可访问，并严格等价于默认的最小 "C" 本地环境。

​	POSIX 亦指定后继的 `setlocale` 调用可以使返回的指针无效，而不仅是被指向的字符串内容。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <time.h>
#include <wchar.h>
 
int main(void)
{
    // C 本地环境将为启用 UTF-8 的英文；
    // 小数点将为德文
    // 日期和时间格式将为日文
    setlocale(LC_ALL, "en_US.UTF-8");
    setlocale(LC_NUMERIC, "de_DE.utf8");
    setlocale(LC_TIME, "ja_JP.utf8");
 
    wchar_t str[100];
    time_t t = time(NULL);
    wcsftime(str, 100, L"%A %c", localtime(&t));
    wprintf(L"Number: %.2f\nDate: %ls\n", 3.14, str);
}
```

​	可能的输出：

```txt
Number: 3,14
Date: 月曜日 2017年09月25日 13時00分15秒
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.11.1.1 The setlocale function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.11.1.1 The setlocale function （第 163-164 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.11.1.1 The setlocale function （第 224-225 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.11.1.1 The setlocale function （第 205-206 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.4.1.1 The setlocale function

**参阅**

| [LC_ALL<br />LC_COLLATE<br />LC_CTYPE<br />LC_MONETARY<br />LC_NUMERIC<br />LC_TIME<br />](https://zh.cppreference.com/w/c/locale/LC_categories) | **setlocale** 所用的本地环境类别 (宏常量) |
| ------------------------------------------------------------ | ----------------------------------------- |
| **setlocale** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/locale/setlocale)** |                                           |

**外部链接**

| 1.   | [Windows 本地环境名字列表](https://ss64.com/locale.html)。  |
| ---- | ----------------------------------------------------------- |
| 2.   | [Linux 本地环境名字列表](https://lh.2xlibre.net/locales/)。 |






