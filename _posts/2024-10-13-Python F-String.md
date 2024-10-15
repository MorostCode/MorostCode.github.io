---
layout: post
title: F-String
date: 2024-10-13 16:00:00
summary: 111
categories: Share
---

# F-String
---
## 简介
---
f-string，亦称为格式化字符串常量（formatted string literals）,主要目的是使格式化字符串的操作更加简便。

## 安装
---
Python 3.6 引入

## 基础使用
---

```python
author = "pawjast"
year = 2022
text = "Data Science Blog"

print(f"Example 1: {author}")  # string
print(f"Example 2: {year}")  # number
print(f"Example 3: {2 + 2}")  # expression
print(f"{text=}")

# output
Example 1: pawjast
Example 2: 2022
Example 3: 4
text='Data Science Blog'
```

有些事情是 f-strings 根本无法做到的， 例如在运行时填充模板，即动态格式，这就是 f-strings 被称为文字字符串格式的原因

## 进阶使用
---
### 浮点数

```python
pi_val = 3.141592
float_val = 1.5
precision = 3

print(f"Example 1: {pi_val:f}")
print(f"Example 2: {pi_val:.0f}")
print(f"Example 3: {pi_val:.1f}")
print(f"Example 4: {pi_val:.3f}")
print(f"{float_val:.{precision}f}")  # 允许嵌套

# output
Example 1: 3.141592
Example 2: 3
Example 3: 3.1
Example 4: 3.142
1.500
```

### 百分比

```python
val1 = 0.5
val2 = 1.255

print(f"Example 1: {val1:%}")
print(f"Example 2: {val1:.0%}")
print(f"Example 3: {val2:.1%}")

# output
Example 1: 50.000000%
Example 2: 50%
Example 3: 125.5%
```

### 整数

将 `,` 添加到代码中将打印千位分隔符

```python
int_1 = 1000
int_2 = 1000_000_000

print(f"{int_1:,d}")
print(f"{int_2:,d}")

# output
1,000
1,000,000,000
```

### 格式填充

用空白空间填充

```python
val = 1

print(f"1: {val:1d}")
print(f"2: {val:2d}")
print(f"3: {val:3d}")

print(f"1: {val:01d}")
print(f"2: {val:02d}")
print(f"3: {val:03d}")

# output
1: 1
2:  1
3:   1

1: 1
2: 01
3: 001
```

## 学习资料
---
官方文档：[7. 输入与输出 — Python 3.12.6 文档](https://docs.python.org/zh-cn/3/tutorial/inputoutput.html)
