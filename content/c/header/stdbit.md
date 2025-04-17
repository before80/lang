+++
title = "<stdbit.h>"
date = 2025-04-14T14:43:32+08:00
weight = 170
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdbit](https://zh.cppreference.com/w/c/header/stdbit)

​	此标头是[数值](https://zh.cppreference.com/w/c/numeric)库的一部分，特别是，它提供处理 C 对象的[字节序]({{< ref "/c/header/stdbit#.E5.AE.8F.E5.B8.B8.E9.87.8F" >}})和[字节与位表示]({{< ref "/c/header/stdbit#.E5.87.BD.E6.95.B0" >}})的宏和函数。

## 函数

| [stdc_leading_zeros (C23)<br />](https://zh.cppreference.com/w/c/numeric/bit/stdc_leading_zeros) | 从最高有效位开始，计算连续为 0 的位的个数 (泛型函数宏)   |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| [stdc_leading_ones (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_leading_ones&action=edit&redlink=1) | 从最高有效位开始，计算连续为 1 的位的个数 (泛型函数宏)   |
| [stdc_trailing_zeros (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_zeros&action=edit&redlink=1) | 从最低有效位开始，计算连续 0 位的个数 (泛型函数宏)       |
| [stdc_trailing_ones (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_trailing_ones&action=edit&redlink=1) | 从最低有效位开始，计算连续为 1 的位的个数 (泛型函数宏)   |
| [stdc_first_leading_zero (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_zero&action=edit&redlink=1) | 从最高有效位开始，查找第一个为 0 的位的位置 (泛型函数宏) |
| [stdc_first_leading_one (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_leading_one&action=edit&redlink=1) | 从最高有效位开始，查找第一个为 1 的位的位置 (泛型函数宏) |
| [stdc_first_trailing_zero (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailing_zero&action=edit&redlink=1) | 从最低有效位开始，查找第一个为 0 的位的位置 (泛型函数宏) |
| [stdc_first_trailinging_zero (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_first_trailinging_zero&action=edit&redlink=1) | 从最低有效位开始，查找第一个为 1 的位的位置 (泛型函数宏) |
| [stdc_count_zeros (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_zeros&action=edit&redlink=1) | 计算在无符号整数中为 0 的位的数量 (泛型函数宏)           |
| [stdc_count_ones (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_count_ones&action=edit&redlink=1) | 计算在无符号整数中为 1 的位的数量 (泛型函数宏)           |
| [stdc_has_single_bit (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_has_single_bit&action=edit&redlink=1) | 检查整数是否是 *2* 的整数次幂 (泛型函数宏)               |
| [stdc_bit_width (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_width&action=edit&redlink=1) | 查找表示给定值所需要的最小位数 (泛型函数宏)              |
| [stdc_bit_floor (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_floor&action=edit&redlink=1) | 查找不大于给定值的最大 *2* 的整数次幂 (泛型函数宏)       |
| [stdc_bit_ceil (C23)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/numeric/bit/stdc_bit_ceil&action=edit&redlink=1) | 查找不小于给定值的最小 *2* 的整数次幂 (泛型函数宏)       |

## 宏常量

| [__STDC_ENDIAN_LITTLE__ (C23)<br />__STDC_ENDIAN_BIG__ (C23)<br />__STDC_ENDIAN_NATIVE__<br />](https://zh.cppreference.com/w/c/numeric/bit/endian) | 指示所有标量类型的端序 (宏常量) |
| ------------------------------------------------------------ | ------------------------------- |

## 概要

```c
#define __STDC_VERSION_STDBIT_H__ 202311L
 
#define __STDC_ENDIAN_LITTLE__ /* 由实现定义 */
#define __STDC_ENDIAN_BIG__    /* 由实现定义 */
#define __STDC_ENDIAN_NATIVE__ /* 由实现定义 */
 
unsigned int stdc_leading_zeros_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_leading_zeros_us(unsigned short value) [[unsequenced]];
unsigned int stdc_leading_zeros_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_leading_zeros_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_leading_zeros_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_leading_zeros(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_leading_ones_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_leading_ones_us(unsigned short value) [[unsequenced]];
unsigned int stdc_leading_ones_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_leading_ones_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_leading_ones_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_leading_ones(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_trailing_zeros_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_trailing_zeros_us(unsigned short value) [[unsequenced]];
unsigned int stdc_trailing_zeros_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_trailing_zeros_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_trailing_zeros_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_trailing_zeros(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_trailing_ones_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_trailing_ones_us(unsigned short value) [[unsequenced]];
unsigned int stdc_trailing_ones_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_trailing_ones_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_trailing_ones_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_trailing_ones(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_first_leading_zero_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_first_leading_zero_us(unsigned short value) [[unsequenced]];
unsigned int stdc_first_leading_zero_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_first_leading_zero_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_first_leading_zero_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_first_leading_zero(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_first_leading_one_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_first_leading_one_us(unsigned short value) [[unsequenced]];
unsigned int stdc_first_leading_one_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_first_leading_one_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_first_leading_one_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_first_leading_one(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_first_trailing_zero_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_first_trailing_zero_us(unsigned short value) [[unsequenced]];
unsigned int stdc_first_trailing_zero_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_first_trailing_zero_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_first_trailing_zero_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_first_trailing_zero(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_first_trailing_one_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_first_trailing_one_us(unsigned short value) [[unsequenced]];
unsigned int stdc_first_trailing_one_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_first_trailing_one_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_first_trailing_one_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_first_trailing_one(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_count_zeros_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_count_zeros_us(unsigned short value) [[unsequenced]];
unsigned int stdc_count_zeros_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_count_zeros_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_count_zeros_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_count_zeros(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_count_ones_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_count_ones_us(unsigned short value) [[unsequenced]];
unsigned int stdc_count_ones_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_count_ones_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_count_ones_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_count_ones(/*generic_value_type*/ value) [[unsequenced]];
bool stdc_has_single_bit_uc(unsigned char value) [[unsequenced]];
bool stdc_has_single_bit_us(unsigned short value) [[unsequenced]];
bool stdc_has_single_bit_ui(unsigned int value) [[unsequenced]];
bool stdc_has_single_bit_ul(unsigned long int value) [[unsequenced]];
bool stdc_has_single_bit_ull(unsigned long long int value) [[unsequenced]];
bool stdc_has_single_bit(/*generic_value_type*/ value) [[unsequenced]];
unsigned int stdc_bit_width_uc(unsigned char value) [[unsequenced]];
unsigned int stdc_bit_width_us(unsigned short value) [[unsequenced]];
unsigned int stdc_bit_width_ui(unsigned int value) [[unsequenced]];
unsigned int stdc_bit_width_ul(unsigned long int value) [[unsequenced]];
unsigned int stdc_bit_width_ull(unsigned long long int value) [[unsequenced]];
/*generic_return_type*/
stdc_bit_width(/*generic_value_type*/ value) [[unsequenced]];
unsigned char stdc_bit_floor_uc(unsigned char value) [[unsequenced]];
unsigned short stdc_bit_floor_us(unsigned short value) [[unsequenced]];
unsigned int stdc_bit_floor_ui(unsigned int value) [[unsequenced]];
unsigned long int stdc_bit_floor_ul(unsigned long int value) [[unsequenced]];
unsigned long long int stdc_bit_floor_ull(unsigned long long int value) [[unsequenced]];
/*generic_value_type*/
stdc_bit_floor(/*generic_value_type*/ value) [[unsequenced]];
unsigned char stdc_bit_ceil_uc(unsigned char value) [[unsequenced]];
unsigned short stdc_bit_ceil_us(unsigned short value) [[unsequenced]];
unsigned int stdc_bit_ceil_ui(unsigned int value) [[unsequenced]];
unsigned long int stdc_bit_ceil_ul(unsigned long int value) [[unsequenced]];
unsigned long long int stdc_bit_ceil_ull(unsigned long long int value) [[unsequenced]];
/*generic_value_type*/
stdc_bit_ceil(/*generic_value_type*/ value) [[unsequenced]];
unsigned char stdc_rotate_left_uc(unsigned char value, unsigned int count);
unsigned short stdc_rotate_left_us(unsigned short value, unsigned int count);
unsigned int stdc_rotate_left_ui(unsigned int value, unsigned int count);
unsigned long stdc_rotate_left_ul(unsigned long value, unsigned int count);
unsigned long long stdc_rotate_left_ull(unsigned long long value, unsigned int count);
/*generic_value_type*/
stdc_rotate_left(/*generic_value_type*/ value, generic_count_type count);
unsigned char stdc_rotate_right_uc(unsigned char value, unsigned int count);
unsigned short stdc_rotate_right_us(unsigned short value, unsigned int count);
unsigned int stdc_rotate_right_ui(unsigned int value, unsigned int count);
unsigned long stdc_rotate_right_ul(unsigned long value, unsigned int count);
unsigned long long stdc_rotate_right_ull(unsigned long long value, unsigned int count);
/*generic_value_type*/
stdc_rotate_right(/*generic_value_type*/ value, generic_count_type count);
```
