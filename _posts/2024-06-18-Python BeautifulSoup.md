---
title: "BeautifulSoup"
published: true
date: 2024-06-18
tags: [Python, BeautifulSoup]
---

# BeautifulSoup

## 简介

Beautiful Soup 是一个可以从 HTML 或 XML 中提取数据的 Python 库。它可以通过你喜欢的转换器快速帮你解析并查找整个 HTML 文档。

> Beautiful Soup 自动将输入文档转为 Unicode 编码，输出文档转为 UTF-8 编码。因此你不需要考虑编码方式。除非文档没有指定一个编码方式，这时你只要说明一下原始的编码方式就可以了。

```bash
pip install bs4
pip install lxml
```

## 解析器

Beautiful 在解析时依赖解析器，以下是一些支持的解析器：

```python
BeautifulSoup(markup, 'html.parser')
BeautifulSoup(markup, 'lxml')
BeautifulSoup(markup 'xml')
BeautifulSoup(markup, 'html5lib')
```

lxml 解析器可以解析 HTML 和 XML 文档，并且速度快，容错能力强，所有推荐使用它。

## 通用方法

`soup.prettify()`
以标准的缩进格式输出，这一步不是由prettify()方法完成的，而是在创建soup对象时就完成。

## 节点

### 获取节点信息

`.name`
获取节点名称（如：div，span，li，a等）。

`.attrs`
获取节点属性（如：class，id，href等），返回字典对象。

`.string $ .text`
获取节点元素包含的文本内容，返回字符串对象。

`.strings`
获取该节点及其所有子节点的文字，返回生成器对象。

### 按关系查找节点

`.contents`
获取节点所有的子节点，返回列表对象。

`.children`
获取节点所有的子节点，返回生成器对象。

`.parent`
获取节点的直接父节点。

`.parents`
获取节点的所有祖先节点，返回生成器对象。

`previous_sibling`
获取节点的前一个兄弟元素。
`previous_siblings`
获取节点前面的兄弟元素列表，返回生成器对象

`next_sibling`
获取节点的后一个兄弟元素。
`next_siblings`
获取节点后面的兄弟元素列表，返回生成器对象

`previous_element`
获取节点的前一个元素
`next_element`
获取节点的后一个元素

### 按全局查找节点

 `find_all(name ,attrs ,string, limit, recursive, **kwargs )`
- name：节点名称（传入字符串类型）
- attrs：节点属性（传入字典类型）
- string：要查找的元素的文本内容
- limit：限制返回结果的数量
- recursive：是否递归查找，默认为True
- \*\*kwargs：关键字参数形式的属性查找，例如 id='my-id'
多个元素，返回列表。

`find(name ,attrs ,recursive ,string, **kwargs )`
参数释义与 `find_all` 相同，返回单个元素。

## 资料
官方文档：[Beautiful Soup 4.4.0 文档 — Beautiful Soup 4.2.0 中文 文档](https://beautifulsoup.readthedocs.io/zh-cn/v4.4.0/)
