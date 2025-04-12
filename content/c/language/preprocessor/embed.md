+++
title = "二进制资源包含 "
date = 2025-04-12T14:34:44+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor/embed](https://zh.cppreference.com/w/c/preprocessor/embed)

​	`#embed` 是用于在构建中包含（二进制）资源的预处理器指令，其中的资源被定义为从翻译环境中可以访问的数据来源。

## 语法

| `#embed <` *h-字符序列* `>` *嵌入形参序列* ﻿(可选) *换行*     | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `#embed "` *q-字符序列* `"` *嵌入形参序列* ﻿(可选) *换行*     | (2)  |      |
| `#embed` *预处理记号序列* *换行*                             | (3)  |      |
| `__has_embed` `(` `"` *q-字符序列* `"` *嵌入参数序列* ﻿(可选) `)` <br />`__has_embed` `(` `<` *h-字符序列* `>` *嵌入参数序列* ﻿(可选) `)` | (4)  |      |
| `__has_embed` `(` *字符字面量* *预处理平衡记号序列* ﻿(可选) `)` <br />`__has_embed` `(` `<` *h-预处理记号序列* `>` *预处理平衡记号序列* ﻿(可选) `)` | (5)  |      |

1) 搜索由 *h-字符序列* 所唯一标定的资源，并将该指令替换为对应于该资源数据的整数的逗号分隔列表。
2) 搜索由 *q-字符序列* 所标定的资源，并将该指令替换为对应于该资源数据的整数的逗号分隔列表。可能回退为 (1)。
3) 若 (1) 和 (2) 均未匹配，则对 *预处理记号序列* 进行替换。替换后，该指令再次尝试与 (1) 或 (2) 匹配。
4) 检查是否有可用于嵌入的资源，无论它是否为空或无论实现是否支持所传递参数。
5) 若 (4) 未匹配，则对 *h-预处理记号序列* 和 *预处理平衡记号序列* 进行替换。替换后，该指令再次尝试与 (4) 匹配。

| *换行*               | -    | 换行字符                                                     |
| -------------------- | ---- | ------------------------------------------------------------ |
| *h-字符序列*         | -    | 一个或更多 *h-字符* 的序列，出现以下任何字符导致未定义行为：<br />字符 `'`<br />字符 `"`<br />字符 `\` <br />字符序列 `//`<br />字符序列 `*/` |
| *h-字符*             | -    | [源字符集](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_5)中除了换行和 > 的任意成员 |
| *q-字符序列*         | -    | 一个或更多 *q-字符* 的序列，出现以下任何字符导致未定义行为：<br />字符 `'`<br />字符 `\` <br />字符序列 `//` <br />字符序列 `*/` |
| *q-字符*             | -    | [源字符集](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_5)中除了换行和 `"` 的任意成员 |
| *预处理记号序列*     | -    | 一个或更多[预处理记号](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_3)的序列 |
| *字符串字面量*       | -    | [字符串字面量](https://zh.cppreference.com/w/c/language/string_literal) |
| *h-预处理记号序列*   | -    | 一个或更多除了 > 外的[预处理记号](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_3)的序列 |
| *嵌入参数序列*       | -    | 一个或多个 *预处理参数* 的序列。注意，不同于 *属性列表*，这个序列并非逗号分隔。 |
| *预处理参数*         | -    | *属性记号*（见 [属性](https://zh.cppreference.com/w/c/language/attributes)），但由预处理记号而非记号组成。 |
| *预处理平衡记号序列* | -    | *平衡记号序列*（见 [属性](https://zh.cppreference.com/w/c/language/attributes)），但由预处理记号而非记号组成。 |

## 解释

1) 以由实现定义的方式搜索由 *h-字符序列* 所标定的资源。
2) 以由实现定义的方式搜索由 *q-字符序列* 所标定的资源。对于 (1,2)，各实现通常使用与该实现用于[源文件包含](https://zh.cppreference.com/w/c/preprocessor/include)相似但不同的一组由实现定义的搜索路径。出现于标准中一个示例中的语言构造 `__has_embed(__FILE__ ...` 说明，至少在 (2) 的情况中，当前文件所在的目录预期会被搜索。
3) 指令中处于 `embed` 之后的各预处理记号，与普通文本一样处理（亦即，当前被定义为宏的各个标识符均被替换为其预处理记号替换列表）。经全部替换后所得的指令应当与之前两个形式之一相匹配。预处理记号对 `<` 和 `>` 或者一对 `"` 字符之间的预处理记号序列，将其合并为一个头文件名预处理记号的方法是由实现定义的。
4) 对由 *h-字符序列* 或 *q-字符序列* 所标定的资源进行的搜索，如同该预处理记号序列是 (3) 中的 *预处理记号序列* 一样进行，但不进行进一步的宏展开。如果这条指令无法满足 #embed 指令的语法规定，则程序非良构。如果资源搜索成功，该资源非空，且所有参数均受支持，则 __has__embed 表达式求值为 `__STDC_EMBED_FOUND__`，如果该资源为空且所有参数均受支持，则为 `__STDC_EMBED_EMPTY__` ，而如果搜索失败或有任一参数不受实现支持，则为 `__STDC_EMBED_NOT_FOUND__`。
5) 仅当 (4) 无法匹配时才考虑这种形式，这种情况下各预处理记号按普通文本一样处理。

​	若未能找到资源或有参数之一不受实现支持，则程序非良构。

​	`__has_embed` 可在 [`#if`](https://zh.cppreference.com/w/c/preprocessor/conditional) 和 [`#elif`](https://zh.cppreference.com/w/c/preprocessor/conditional) 的表达式中展开。它被 [`#ifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #ifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #elifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #elifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional) 和 [`defined`](https://zh.cppreference.com/w/c/preprocessor/conditional) 当做已定义宏，但不能用在别处。

​	资源具有*实现的资源宽度*，它是由实现定义的所定位资源的位大小。其*资源宽度*，为由实现定义的资源宽度，除非由 `limit` 参数所修改。若资源宽度为 0，则认为该资源为空。*嵌入元素宽度* 等于 [CHAR_BIT](http://zh.cppreference.com/w/c/types/limits)，除非由某个由实现定义的参数所修改。资源宽度必须可被嵌入元素宽度整除。

​	`#embed` 指令展开为上述由整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)构成的列表。列表中每个整数常量表达式的记号组，与列表中前一个整数常量表达式的记号组之间，以逗号分隔。这个序列不会以逗号开头或结束。若整数常量表达式的列表为空，则记号序列为空。该指令被替换为其展开，并根据给出的某些特定嵌入参数，带有额外的或者替换的记号序列。

​	扩展序列中的各整数常量表达式的值，由该资源的数据以实现定义的映射所决定。各个整数常量表达式的取值范围为 \\([0, 2^{嵌入元素宽度})\\)。如果：

1. 整数常量表达式列表用于初始化数组，其元素类型与 `unsigned char` 兼容，或于 `char` 可持有负值时与 `char` 兼容，并且
2. 嵌入元素宽度等于 [CHAR_BIT](http://zh.cppreference.com/w/c/types/limits)，

则所初始化的元素数组的内容如同在翻译时间将该资源的二进制数据以 [fread](https://zh.cppreference.com/w/c/io/fread) 读入到数组中一样。

​	鼓励各实现关注翻译时的位序和字节序，以及执行时的位序和字节序，以更加恰当地给出指令中的资源二进制数据。这样会尽可能做到，如果翻译时通过 #embed 指令所引用的资源与通过执行时的方法所访问的相同，那么通过如 [fread](https://zh.cppreference.com/w/c/io/fread) 或类似方式读到连续存储中的数据，与由 #embed 指令展开的内容初始化的字符类型的数组，将会逐位比较相等。

## 参数

​	标准定义了参数 `limit`、`prefix`、`suffix` 和 `if_empty`。指令中出现的任何其他参数都必为实现定义的，否则程序非良构。由实现定义的嵌入参数可能改变指令的语义。

### limit

| `limit(` *常量表达式* `)`     | (1)  |
| ----------------------------- | ---- |
| `__limit__(` *常量表达式* `)` | (2)  |

​	嵌入参数 `limit` 在嵌入参数序列中最多可出现一次。它必须带有实参，必须为整数（预处理器）[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，求值为非负数，且不包含记号 defined。资源宽度被设为该整数常量表达式与嵌入元素宽度的乘积和实现的资源宽度的最小值。

### suffix

| `suffix(` *预处理平衡记号序列* ﻿(可选) `)`     | (1)  |
| --------------------------------------------- | ---- |
| `__suffix__(` *预处理平衡记号序列* ﻿(可选) `)` | (2)  |

​	嵌入参数 `suffix` 在嵌入参数序列中最多可出现一次。它必须带有（可能为空的）实参子句。如果资源非空，则该参数子句的内容被置于紧跟该指令的展开之后。否则，它没有效果。

### prefix

| `prefix(` *预处理平衡记号序列* ﻿(可选) `)`     | (1)  |
| --------------------------------------------- | ---- |
| `__prefix__(` *预处理平衡记号序列* ﻿(可选) `)` | (2)  |

​	嵌入参数 `prefix` 在嵌入参数序列中最多可出现一次。它必须带有（可能为空的）实参子句。如果资源非空，则该参数子句的内容被置于紧接该指令的展开之前。否则，它没有效果。

### if_empty

| `if_empty(` *预处理平衡记号序列* ﻿(可选) `)`     | (1)  |
| ----------------------------------------------- | ---- |
| `__if_empty__(` *预处理平衡记号序列* ﻿(可选) `)` | (2)  |

​	嵌入参数 `if_empty` 在嵌入参数序列中最多可出现一次。它必须带有（可能为空的）实参子句。如果资源为空，则以该参数子句的内容替换该指令。否则，它没有效果。

## 示例

```c
#include <stdint.h>
#include <stdio.h>
 
const uint8_t image_data[] =
{
#embed "image.png"
};
 
const char message[] =
{
#embed "message.txt" if_empty('M', 'i', 's', 's', 'i', 'n', 'g', '\n')
,'\0' // 空终结符
};
 
void dump(const uint8_t arr[], size_t size)
{
    for (size_t i = 0; i != size; ++i)
        printf("%02X%c", arr[i], (i + 1) % 16 ? ' ' : '\n');
    puts("");
}
 
int main()
{
    puts("image_data[]:");
    dump(image_data, sizeof image_data);
    puts("message[]:");
    dump((const uint8_t*)message, sizeof message);
}
```

​	可能的输出：

```txt
image_data[]:
89 50 4E 47 0D 0A 1A 0A 00 00 00 0D 49 48 44 52
00 00 00 01 00 00 00 01 01 03 00 00 00 25 DB 56
...
message[]:
4D 69 73 73 69 6E 67 0A 00
```

## 参阅

资源包含 (C++26 起)的 [C++ 文档](https://zh.cppreference.com/w/cpp/preprocessor/embed)