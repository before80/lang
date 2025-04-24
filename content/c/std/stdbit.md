
+++
title = "<stdbit.h> (C23)"
date = 2025-04-24T18:40:59+08:00
weight = 160
type = "docs"
description = "处理各类型的字节和位表示的宏"
isCJKLanguage = true
draft = false

+++

## 类型



### stdc_bit_ceil

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_ceil&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_ceil&action=edit&redlink=1)

作用：查找不小于给定值的最小 2 的整数次幂(泛型函数宏)

备注：





### stdc_bit_floor

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_floor&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_floor&action=edit&redlink=1)

作用：查找不大于给定值的最大 2 的整数次幂(泛型函数宏)

备注：





### stdc_bit_width

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_width&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_width&action=edit&redlink=1)

作用：查找表示给定值所需要的最小位数(泛型函数宏)

备注：





### stdc_count_ones

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_ones&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_ones&action=edit&redlink=1)

作用：计算在无符号整数中为 `1` 的位的数量(泛型函数宏)

备注：





### stdc_count_zeros

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_zeros&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_zeros&action=edit&redlink=1)

作用：计算在无符号整数中为 `​0​` 的位的数量(泛型函数宏)

备注：





### stdc_first_leading_one

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_one&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_one&action=edit&redlink=1)

作用：从最高有效位开始，查找第一个为 `1` 的位的位置(泛型函数宏)

备注：





### stdc_first_leading_zero

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_zero&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_zero&action=edit&redlink=1)

作用：从最高有效位开始，查找第一个为 `​0​` 的位的位置(泛型函数宏)

备注：





### stdc_first_trailing_zero

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailing_zero&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailing_zero&action=edit&redlink=1)

作用：从最低有效位开始，查找第一个为 `​0​` 的位的位置(泛型函数宏)

备注：





### stdc_first_trailinging_zero

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailinging_zero&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailinging_zero&action=edit&redlink=1)

作用：从最低有效位开始，查找第一个为 `1` 的位的位置(泛型函数宏)

备注：





### stdc_leading_ones

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_leading_ones&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_leading_ones&action=edit&redlink=1)

作用：从最高有效位开始，计算连续为 `1` 的位的个数(泛型函数宏)

备注：





### stdc_leading_zeros

原址：[https://zh.cppreference.com/w/c/numeric/bit/stdc_leading_zeros](https://zh.cppreference.com/w/c/numeric/bit/stdc_leading_zeros)

作用：从最高有效位开始，计算连续为 `​0​` 的位的个数(泛型函数宏)

备注：
```c
// 在标头 <stdbit.h> 定义
unsigned int stdc_leading_zeros_uc( unsigned char value ) [[unsequenced]];// (1)(C23 起)
unsigned int stdc_leading_zeros_us( unsigned short value ) [[unsequenced]];// (2)(C23 起)
unsigned int stdc_leading_zeros_ui( unsigned int value ) [[unsequenced]];// (3)(C23 起)
unsigned int stdc_leading_zeros_ul( unsigned long int value ) [[unsequenced]];// (4)(C23 起)
unsigned int stdc_leading_zeros_ull( unsigned long long int value ) [[unsequenced]];// (5)(C23 起)
#define stdc_leading_zeros( value )
// 暴露的接口：

generic_return_type stdc_leading_zeros( generic_value_type value ) [[unsequenced]];// (6)(C23 起)
```

1-5) 返回 `value` 中从最高有效位开始的连续 `0` 位的个数。

6） 泛型函数（以 `generic_value_type` 实参标记），基于输入值的类型返回适当的值，要求类型为：

- 不包括 `bool` 的标准无符号整数类型；
- 扩充无符号整数类型；
- 或者，宽度与某个非 `bool` 标准或扩充整数类型匹配的位精确无符号整数类型。

`generic_return_type` 应当是足以表示计算结果的适当大小的无符号整数类型。

**参数**

| value | -    | 无符号整数 |
| ----- | ---- | ---------- |
|       |      |            |

**返回值**

​	`value` 中从最高有效位开始的连续 `0` 位的个数。

**示例**

```c
#include <limits.h>
#include <stdbit.h>
#include <stdint.h>
#include <stdio.h>
 
#define bits_num(value) (sizeof(value) * CHAR_BIT)
 
#define bin_impl(T, suffix) \
const char* bin_##suffix(T x) \
{ \
    static char buf[bits_num(x) * CHAR_BIT + 1]; \
    for (T i = 0, mask = ((T)1 << (bits_num(x) - 1)); mask; mask >>= 1) \
        buf[i++] = x & mask ? '1' : '0'; \
    buf[bits_num(x)] = '\0'; \
    return buf; \
}
 
bin_impl(uint8_t, u8)
bin_impl(uint16_t, u16)
bin_impl(uint32_t, u32)
bin_impl(uint64_t, u64)
 
#define bin(x) _Generic((x), \
    uint8_t: bin_u8, uint16_t: bin_u16, uint32_t: bin_u32, default: bin_u64)(x)
 
int main()
{
    puts("uint8_t:");
    for (uint8_t x = 0b11000000; ; x >>= 1)
    {
        printf("x = [%s], 前导零: %d\n", bin(x), stdc_leading_zeros(x));
        if (!x)
            break;
    }
 
    puts("uint16_t:");
    for (uint16_t x = 0b11000000; ; x >>= 1)
    {
        printf("x = [%s], 前导零: %d\n", bin(x), stdc_leading_zeros(x));
        if (!x)
            break;
    }
}
```

​	输出：

```txt
uint8_t:
x = [11000000], 前导零: 0
x = [01100000], 前导零: 1
x = [00110000], 前导零: 2
x = [00011000], 前导零: 3
x = [00001100], 前导零: 4
x = [00000110], 前导零: 5
x = [00000011], 前导零: 6
x = [00000001], 前导零: 7
x = [00000000], 前导零: 8
uint16_t:
x = [0000000011000000], 前导零: 8
x = [0000000001100000], 前导零: 9
x = [0000000000110000], 前导零: 10
x = [0000000000011000], 前导零: 11
x = [0000000000001100], 前导零: 12
x = [0000000000000110], 前导零: 13
x = [0000000000000011], 前导零: 14
x = [0000000000000001], 前导零: 15
x = [0000000000000000], 前导零: 16
```

**参阅**

| [stdc_first_leading_zero (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_zero&action=edit&redlink=1) | 从最高有效位开始，查找第一个为 `0` 的位的位置 (泛型函数宏) |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| [stdc_count_zeros (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_zeros&action=edit&redlink=1) | 计算在无符号整数中为 `0` 的位的数量 (泛型函数宏)           |
| [stdc_leading_ones (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_leading_ones&action=edit&redlink=1) | 从最高有效位开始，计算连续为 `1` 的位的个数 (泛型函数宏)   |
| **countl_zero** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/countl_zero)** |                                                            |





### stdc_trailing_ones

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_ones&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_ones&action=edit&redlink=1)

作用：从最低有效位开始，计算连续为 `1` 的位的个数(泛型函数宏)

备注：





### stdc_trailing_zeros

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_zeros&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_zeros&action=edit&redlink=1)

作用：从最低有效位开始，计算连续 `​0​` 位的个数(泛型函数宏)

备注：






## 枚举




## 宏



### __STDC_ENDIAN_BIG__

原址：[https://zh.cppreference.com/w/c/numeric/bit/endian](https://zh.cppreference.com/w/c/numeric/bit/endian)

作用：指示所有标量类型的端序  (宏常量)

备注：
```c
// 在标头 <stdbit.h> 定义
#define __STDC_ENDIAN_LITTLE__ /* 由实现定义 */// (1)(C23 起)
#define __STDC_ENDIAN_BIG__    /* 由实现定义 */// (2)(C23 起)
#define __STDC_ENDIAN_NATIVE__ /* 由实现定义 */// (3)(C23 起)
```

​	指示所有[标量类型](https://zh.cppreference.com/w/cpp/language/type)的[端序](https://en.wikipedia.org/wiki/Endianness#Overview)：

- 若所有标量类型均为小端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_LITTLE__`。
- 若所有标量类型均为大端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_BIG__`。
- 若平台不使用大端或小端，则`__STDC_ENDIAN_NATIVE__` 既不等于 `__STDC_ENDIAN_BIG__` 也不等于 `__STDC_ENDIAN_LITTLE__`。
- `__STDC_ENDIAN_BIG__` 和 `__STDC_ENDIAN_LITTLE__` 的整数常量表达式的值不同。

**示例**

```c
#include <stdbit.h>
#include <stdio.h>
 
int main()
{
    switch(__STDC_ENDIAN_NATIVE__)
    {
        case __STDC_ENDIAN_LITTLE__:
            printf("__STDC_ENDIAN_LITTLE__\n");
            break;
        case __STDC_ENDIAN_BIG__:
            printf("__STDC_ENDIAN_BIG__\n");
            break;
        default:
            printf("mixed-endian\n");
    }
    return __STDC_ENDIAN_NATIVE__;
}
```

​	可能的输出：

```txt
mixed-endian
```

**参阅**

**endian** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/endian)**





### __STDC_ENDIAN_LITTLE__

原址：[https://zh.cppreference.com/w/c/numeric/bit/endian](https://zh.cppreference.com/w/c/numeric/bit/endian)

作用：指示所有标量类型的端序  (宏常量)

备注：
```c
// 在标头 <stdbit.h> 定义
#define __STDC_ENDIAN_LITTLE__ /* 由实现定义 */// (1)(C23 起)
#define __STDC_ENDIAN_BIG__    /* 由实现定义 */// (2)(C23 起)
#define __STDC_ENDIAN_NATIVE__ /* 由实现定义 */// (3)(C23 起)
```

​	指示所有[标量类型](https://zh.cppreference.com/w/cpp/language/type)的[端序](https://en.wikipedia.org/wiki/Endianness#Overview)：

- 若所有标量类型均为小端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_LITTLE__`。
- 若所有标量类型均为大端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_BIG__`。
- 若平台不使用大端或小端，则`__STDC_ENDIAN_NATIVE__` 既不等于 `__STDC_ENDIAN_BIG__` 也不等于 `__STDC_ENDIAN_LITTLE__`。
- `__STDC_ENDIAN_BIG__` 和 `__STDC_ENDIAN_LITTLE__` 的整数常量表达式的值不同。

**示例**

```c
#include <stdbit.h>
#include <stdio.h>
 
int main()
{
    switch(__STDC_ENDIAN_NATIVE__)
    {
        case __STDC_ENDIAN_LITTLE__:
            printf("__STDC_ENDIAN_LITTLE__\n");
            break;
        case __STDC_ENDIAN_BIG__:
            printf("__STDC_ENDIAN_BIG__\n");
            break;
        default:
            printf("mixed-endian\n");
    }
    return __STDC_ENDIAN_NATIVE__;
}
```

​	可能的输出：

```txt
mixed-endian
```

**参阅**

**endian** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/endian)**





### __STDC_ENDIAN_NATIVE__

原址：[https://zh.cppreference.com/w/c/numeric/bit/endian](https://zh.cppreference.com/w/c/numeric/bit/endian)

作用：指示所有标量类型的端序  (宏常量)

备注：
```c
// 在标头 <stdbit.h> 定义
#define __STDC_ENDIAN_LITTLE__ /* 由实现定义 */// (1)(C23 起)
#define __STDC_ENDIAN_BIG__    /* 由实现定义 */// (2)(C23 起)
#define __STDC_ENDIAN_NATIVE__ /* 由实现定义 */// (3)(C23 起)
```

​	指示所有[标量类型](https://zh.cppreference.com/w/cpp/language/type)的[端序](https://en.wikipedia.org/wiki/Endianness#Overview)：

- 若所有标量类型均为小端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_LITTLE__`。
- 若所有标量类型均为大端，则 `__STDC_ENDIAN_NATIVE__` 等于 `__STDC_ENDIAN_BIG__`。
- 若平台不使用大端或小端，则`__STDC_ENDIAN_NATIVE__` 既不等于 `__STDC_ENDIAN_BIG__` 也不等于 `__STDC_ENDIAN_LITTLE__`。
- `__STDC_ENDIAN_BIG__` 和 `__STDC_ENDIAN_LITTLE__` 的整数常量表达式的值不同。

**示例**

```c
#include <stdbit.h>
#include <stdio.h>
 
int main()
{
    switch(__STDC_ENDIAN_NATIVE__)
    {
        case __STDC_ENDIAN_LITTLE__:
            printf("__STDC_ENDIAN_LITTLE__\n");
            break;
        case __STDC_ENDIAN_BIG__:
            printf("__STDC_ENDIAN_BIG__\n");
            break;
        default:
            printf("mixed-endian\n");
    }
    return __STDC_ENDIAN_NATIVE__;
}
```

​	可能的输出：

```txt
mixed-endian
```

**参阅**

**endian** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/endian)**





### __STDC_VERSION_STDBIT_H__

原址：

作用：

备注：






## 函数



### stdc_bit_ceil_uc

原址：

作用：

备注：





### stdc_bit_ceil_ui

原址：

作用：

备注：





### stdc_bit_ceil_ul

原址：

作用：

备注：





### stdc_bit_ceil_ull

原址：

作用：

备注：





### stdc_bit_ceil_us

原址：

作用：

备注：





### stdc_bit_floor_uc

原址：

作用：

备注：





### stdc_bit_floor_ui

原址：

作用：

备注：





### stdc_bit_floor_ul

原址：

作用：

备注：





### stdc_bit_floor_ull

原址：

作用：

备注：





### stdc_bit_floor_us

原址：

作用：

备注：





### stdc_bit_width_uc

原址：

作用：

备注：





### stdc_bit_width_ui

原址：

作用：

备注：





### stdc_bit_width_ul

原址：

作用：

备注：





### stdc_bit_width_ull

原址：

作用：

备注：





### stdc_bit_width_us

原址：

作用：

备注：





### stdc_count_ones_uc

原址：

作用：

备注：





### stdc_count_ones_ui

原址：

作用：

备注：





### stdc_count_ones_ul

原址：

作用：

备注：





### stdc_count_ones_ull

原址：

作用：

备注：





### stdc_count_ones_us

原址：

作用：

备注：





### stdc_count_zeros_uc

原址：

作用：

备注：





### stdc_count_zeros_ui

原址：

作用：

备注：





### stdc_count_zeros_ul

原址：

作用：

备注：





### stdc_count_zeros_ull

原址：

作用：

备注：





### stdc_count_zeros_us

原址：

作用：

备注：





### stdc_first_leading_one_uc

原址：

作用：

备注：





### stdc_first_leading_one_ui

原址：

作用：

备注：





### stdc_first_leading_one_ul

原址：

作用：

备注：





### stdc_first_leading_one_ull

原址：

作用：

备注：





### stdc_first_leading_one_us

原址：

作用：

备注：





### stdc_first_leading_zero_uc

原址：

作用：

备注：





### stdc_first_leading_zero_ui

原址：

作用：

备注：





### stdc_first_leading_zero_ul

原址：

作用：

备注：





### stdc_first_leading_zero_ull

原址：

作用：

备注：





### stdc_first_leading_zero_us

原址：

作用：

备注：





### stdc_first_trailing_one_uc

原址：

作用：

备注：





### stdc_first_trailing_one_ui

原址：

作用：

备注：





### stdc_first_trailing_one_ul

原址：

作用：

备注：





### stdc_first_trailing_one_ull

原址：

作用：

备注：





### stdc_first_trailing_one_us

原址：

作用：

备注：





### stdc_first_trailing_zero_uc

原址：

作用：

备注：





### stdc_first_trailing_zero_ui

原址：

作用：

备注：





### stdc_first_trailing_zero_ul

原址：

作用：

备注：





### stdc_first_trailing_zero_ull

原址：

作用：

备注：





### stdc_first_trailing_zero_us

原址：

作用：

备注：





### stdc_has_single_bit

原址：[https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_has_single_bit&action=edit&redlink=1](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_has_single_bit&action=edit&redlink=1)

作用：检查整数是否是 2 的整数次幂(泛型函数宏)

备注：





### stdc_has_single_bit_uc

原址：

作用：

备注：





### stdc_has_single_bit_ui

原址：

作用：

备注：





### stdc_has_single_bit_ul

原址：

作用：

备注：





### stdc_has_single_bit_ull

原址：

作用：

备注：





### stdc_has_single_bit_us

原址：

作用：

备注：





### stdc_leading_ones_uc

原址：

作用：

备注：





### stdc_leading_ones_ui

原址：

作用：

备注：





### stdc_leading_ones_ul

原址：

作用：

备注：





### stdc_leading_ones_ull

原址：

作用：

备注：





### stdc_leading_ones_us

原址：

作用：

备注：





### stdc_leading_zeros_uc

原址：

作用：

备注：





### stdc_leading_zeros_ui

原址：

作用：

备注：





### stdc_leading_zeros_ul

原址：

作用：

备注：





### stdc_leading_zeros_ull

原址：

作用：

备注：





### stdc_leading_zeros_us

原址：

作用：

备注：





### stdc_rotate_left_uc

原址：

作用：

备注：





### stdc_rotate_left_ui

原址：

作用：

备注：





### stdc_rotate_left_ul

原址：

作用：

备注：





### stdc_rotate_left_ull

原址：

作用：

备注：





### stdc_rotate_left_us

原址：

作用：

备注：





### stdc_rotate_right_uc

原址：

作用：

备注：





### stdc_rotate_right_ui

原址：

作用：

备注：





### stdc_rotate_right_ul

原址：

作用：

备注：





### stdc_rotate_right_ull

原址：

作用：

备注：





### stdc_rotate_right_us

原址：

作用：

备注：





### stdc_trailing_ones_uc

原址：

作用：

备注：





### stdc_trailing_ones_ui

原址：

作用：

备注：





### stdc_trailing_ones_ul

原址：

作用：

备注：





### stdc_trailing_ones_ull

原址：

作用：

备注：





### stdc_trailing_ones_us

原址：

作用：

备注：





### stdc_trailing_zeros_uc

原址：

作用：

备注：





### stdc_trailing_zeros_ui

原址：

作用：

备注：





### stdc_trailing_zeros_ul

原址：

作用：

备注：





### stdc_trailing_zeros_ull

原址：

作用：

备注：





### stdc_trailing_zeros_us

原址：

作用：

备注：






