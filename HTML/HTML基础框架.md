HTML的基础框架
    head是网页的标题,页面中需要展示的内容基本都在body中编写.
    meta属性可以增加关键词,描述搜索的关键词
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
html是一种标记语言,采用标签的形式进行编写,所有标签都在尖括号内:
```html
<text>
<div></div>
<div> <div> </div> </div>
```
HTMl的内容排版
    标题:<h1>到<h6>为标题标签,h1为最大的标题标签,h6为最小的标题标签
    内容:段落标签<p>,会进行分段处理
    文本样式:加粗标签<b>    斜体标签<em>    中划线标签<s>    下划线标签:<u>
    其他:分割线标签<hr>
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>标签展示</title>
</head>
    <h1>这是一级标题</h1>
    <h2>这是二级标题</h2>
    <h3>这是三级标题</h3>
    <h4>这是四级标题</h4>
    <h5>这是五级标题</h5>
    <h6>这是六级标题</h6>
    <p>这是段落</p>
    <hr>这是水平线分割</hr>
    <b>这是粗体</b>
    <i>这是斜体</i>
    <s>这是删除线</s>
    <u>这是下划线</u>

</body>
</html>
```
