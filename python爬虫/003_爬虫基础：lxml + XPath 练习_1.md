# 爬虫基础：lxml + XPath 实战练习（一）

## 一、题目要求

使用 Python 的 `lxml` 库解析 HTML 网页，结合 XPath 提取指定信息。

**具体任务：**

1. 提取所有动漫名称。
2. 提取所有动漫评分。
3. 提取所有动漫详情页链接。
4. 只提取第一部动漫的名称。
5. 只提取第二部动漫的评分。

## 二、HTML 网页结构

本次练习使用以下 HTML 作为模拟网页：

```python
html = """
<html>
    <body>
        <div class="container">

            <div class="item">
                <h2>进击的巨人</h2>
                <p class="score">9.8</p>
                <a href="https://example.com/a">详情</a>
            </div>

            <div class="item">
                <h2>咒术回战</h2>
                <p class="score">8.9</p>
                <a href="https://example.com/b">详情</a>
            </div>

            <div class="item">
                <h2>葬送的芙莉莲</h2>
                <p class="score">9.7</p>
                <a href="https://example.com/c">详情</a>
            </div>

        </div>
    </body>
</html>
```

**HTML 结构分析：**

- `div.container`：最外层容器。
- `div.item`：每一部动漫的信息容器。
- `h2`：动漫名称。
- `p.score`：动漫评分。
- `a`：动漫详情页链接。
- `href`：存储详情页网址的属性。

## 三、完整代码

```python
from lxml import etree

html = """
<html>
    <body>
        <div class="container">

            <div class="item">
                <h2>进击的巨人</h2>
                <p class="score">9.8</p>
                <a href="https://example.com/a">详情</a>
            </div>

            <div class="item">
                <h2>咒术回战</h2>
                <p class="score">8.9</p>
                <a href="https://example.com/b">详情</a>
            </div>

            <div class="item">
                <h2>葬送的芙莉莲</h2>
                <p class="score">9.7</p>
                <a href="https://example.com/c">详情</a>
            </div>

        </div>
    </body>
</html>
"""

# 将 HTML 字符串解析成 HTML 树
tree = etree.HTML(html)

# 1. 获取所有动漫名称
name = tree.xpath("//h2/text()")
print(name)

# 2. 获取所有动漫评分
rating = tree.xpath("//div/p/text()")
print(rating)

# 3. 获取所有动漫详情页链接
link = tree.xpath("//div/a/@href")
print(link)

# 4. 获取第一部动漫的名称
name_1 = tree.xpath("(//div/h2)[1]/text()")
print(name_1)

# 5. 获取第二部动漫的评分
rating_2 = tree.xpath("(//div/p)[2]/text()")
print(rating_2)
```

## 四、代码知识点解析

### 1. 导入 lxml

```python
from lxml import etree
```

导入 lxml 中的 etree 模块，用于解析 HTML/XML 文档。

### 2. 解析 HTML

```python
tree = etree.HTML(html)
```

作用：将 HTML 字符串解析成可以使用 XPath 操作的文档树。

基本流程：

HTML 字符串 → etree.HTML() → HTML 文档树 → XPath 定位元素。

### 3. 提取标签内部的文本

```python
name = tree.xpath("//h2/text()")
```

含义：

- `//`：查找所有后代节点。
- `h2`：定位 h2 标签。
- `/text()`：提取标签内部的文本。

输出：

```python
['进击的巨人', '咒术回战', '葬送的芙莉莲']
```

注意：

```python
tree.xpath("//h2")
```

返回的是 Element 元素对象，而不是标签内部的文本。

```python
tree.xpath("//h2/text()")
```

才是提取文本内容。

### 4. 提取标签属性

```python
link = tree.xpath("//div/a/@href")
```

含义：

- `//div/a`：找到 div 内部的 a 标签。
- `@href`：提取 a 标签的 href 属性。

输出：

```python
[
    'https://example.com/a',
    'https://example.com/b',
    'https://example.com/c'
]
```

**记忆：**

- `text()`：获取标签文本。
- `@属性名`：获取标签属性。

### 5. 获取指定位置的元素

```python
name_1 = tree.xpath("(//div/h2)[1]/text()")
```

作用：获取整个网页中第一个符合条件的 h2 标签。

```python
rating_2 = tree.xpath("(//div/p)[2]/text()")
```

作用：获取整个网页中第二个符合条件的 p 标签文本。

**重点：XPath 的位置索引从 1 开始，而 Python 列表索引从 0 开始。**

## 五、XPath 核心语法总结

| XPath | 作用 |
|---|---|
| `//h2` | 获取所有 h2 元素 |
| `//h2/text()` | 获取所有 h2 的文本 |
| `//a/@href` | 获取所有 a 标签的 href 属性 |
| `//div/p` | 获取 div 下的 p 标签 |
| `//div[@class='item']` | 获取 class 为 item 的 div |
| `(//h2)[1]` | 获取整个网页第一个 h2 |
| `(//p)[2]` | 获取整个网页第二个 p |
| `//div/p[1]` | 获取每个 div 中第一个 p |
| `//div[@class='item']//h2/text()` | 获取所有 item 中 h2 的文本 |

## 六、重点易错知识点

### 1. `//div/p[1]` 和 `(//div/p)[1]` 的区别

**第一种：**

```python
tree.xpath("//div/p[1]")
```

含义：找到每个 div 下面的第一个 p 标签。

如果有三个 div，每个 div 都有一个 p，那么可能返回三个元素。

**第二种：**

```python
tree.xpath("(//div/p)[1]")
```

含义：先找到所有符合条件的 p 标签，再整体取第一个。

只返回一个元素。

### 2. XPath 与 Python 列表索引的区别

XPath：

```python
(//h2)[1]  # 第一个
(//h2)[2]  # 第二个
(//h2)[3]  # 第三个
```

Python：

```python
list[0]  # 第一个
list[1]  # 第二个
list[2]  # 第三个
```

注意不要混淆。

### 3. Element 与文本的区别

```python
tree.xpath("//h2")
```

返回元素对象。

```python
tree.xpath("//h2/text()")
```

返回文本列表。

### 4. 使用 class 精准定位

```python
tree.xpath("//div[@class='item']//h2/text()")
```

含义：找到 class 为 item 的 div，再提取内部 h2 的文本。

相比直接使用 `//h2/text()`，这种方式可以更加精准地限定查找范围。

## 七、本题运行结果

```python
['进击的巨人', '咒术回战', '葬送的芙莉莲']

['9.8', '8.9', '9.7']

[
    'https://example.com/a',
    'https://example.com/b',
    'https://example.com/c'
]

['进击的巨人']

['8.9']
```

## 八、本题核心记忆

1. `etree.HTML(html)`：解析 HTML。
2. `xpath()`：定位网页元素。
3. `text()`：提取文本。
4. `@href`：提取属性。
5. `//`：查找后代节点。
6. `[1]`：XPath 中取第一个元素。
7. `(//标签)[1]`：整体查找后取第一个。
8. `//div[@class='item']`：根据 class 属性定位元素。

**本题核心：掌握 lxml 的 HTML 解析，以及 XPath 的文本提取、属性提取和位置定位。**
