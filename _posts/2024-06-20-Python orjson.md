---
title: orjson
published: true
date: 2024-06-20
update: 2024-06-20
tags:
  - Python
  - orjson
---

# orjson

## 简介

`orjson` 是一个高性能的JSON编码和解码库，它的速度通常比 Python 标准库 `json` 快得多，且支持一些 `json` 不支持的特性，如读取和写入流式 JSON 数据。

安装：`pip install orjson`

> 如果 Python 版本 >= 3.6，`orjson` 会自动使用优化的实现，否则会回退到纯 Python 实现。

## 基础使用

解码：`orjson.loads()`

```python
import orjson

json_string = '{"name": "John", "age": 30, "city": "New York"}'  
decoded_data = orjson.loads(json_string)  
print(decoded_data)
# 输出: {'name': 'John', 'age': 30, 'city': 'New York'}
```

编码：`orjson.dumps()`

```python
data = {'name': 'John', 'age': 30, 'city': 'New York'}  
json_string = orjson.dumps(data)  
print(json_string)
# 输出: '{"name": "John", "age": 30, "city": "New York"}'
```

处理流式数据：`orjson.Decoder()` & `orjson.Encoder()`

```python
def process_json_stream(json_path):  
    with open(json_path, 'rb') as f:  
        decoder = orjson.Decoder(f)  
        for obj in decoder.iter_objects():  
            print(obj)  

json_path = 'large_json_file.json'
process_json_stream()
```

处理报错：`orjson.JSONDecodeError`

```python
import orjson  
  
try:  
    invalid_json_string = '{"name": "John", "age": "thirty"}'  
    decoded_data = orjson.loads(invalid_json_string)  
except orjson.JSONDecodeError as e:  
    print(f"JSON decode error: {e}")
```

## 进阶使用

优化内存使用：`option=orjson.OPT_STABLE_ASSEMBLY`

如果你不关心解码后的 Python 对象的属性顺序，可以通过 `orjson.loads()` 和 `orjson.dumps()` 的 `option` 参数来优化内存使用。

```python
import orjson  
  
json_string = '{"age": 30, "name": "John", "city": "New York"}'  
decoded_data = orjson.loads(json_string, option=orjson.OPT_STABLE_ASSEMBLY)  
print(decoded_data)
```

## 资料

Github主页：[GitHub - ijl/orjson](https://github.com/ijl/orjson)