<h3>HTML的基础框架</h3>
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

<br>
<hr>
<br>
html是一种标记语言,采用标签的形式进行编写,所有标签都在尖括号内:

```html
<text>
<div></div>
<div> <div> </div> </div>
```

<br>
<hr>
<br>
<h3>HTMl的内容排版</h3>
标题:h1到h6为标题标签,h1为最大的标题标签,h6为最小的标题标签<br>
内容:段落标签p,会进行分段处理<br>
文本样式:加粗标签b   斜体标签em    中划线标签s    下划线标签u<br>
其他:分割线标签hr<br>
    
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
    <!-- 注释 -->

</body>
</html>
```
<br>
<hr>
<br>
<h3>行内元素和块级元素</h3>
标签又可以称为元素, 块级元素会独占一行,行内元素囊括的元素会自动加粗.<br>
下面的h3和p为块级元素而b和u为行内元素

```html
<h3>十七张牌<p>你能<b>秒</b>我?</p>我当场就把<u>屏幕</u>吃了</h3>
```

<br>
<hr>
<br>
<h3>div和span</h3>
div和span用于结构化和样式化内容(划分区域)<br>

```html
<body>
    <div>
        <span><h1>这是一级标题</h1></span>
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
        <!-- 注释 -->
    </div>
</body>
```
<br>
<hr>
<br>
<h3>图片标签img</h3>
src属性:填写图片的路径<br>
alt属性:在图片无法加载的时候出现的文本<br>
title属性:用于在鼠标停留的时候,展示图片的描述

```html
    <img src="图片名称.jpg" alt="图片好像已经不存在了" title="图片的描述">
```

<br>
图片的分辨率:可以通过height和width属性去修改图片的分辨率

```html
<img src="图片名称.jpg" height="200" width="200" >
```
<br>
<hr>
<br>
<h3>链接标签a</h3>
a标签的href属性:可以实现页面的跳转<br>
target属性:默认_selif正常打开,_blank可以另外打开一个窗口



```html
    <div>
        給你康一個好康的
        <a href="https://www.bilibili.com/video/BV1UT42167xb/?spm_id_from=333.337.search-card.all.click&vd_source=518611c018aea9be639c19407f18f2c4" 
        target="_blank">
        視頻</a>
    </div>
```

<img width="843" height="66" alt="image" src="https://github.com/user-attachments/assets/b6111ef2-677a-4af8-a914-27d5e4e1ff34" />
<br>
a标签的href属性:同时也可以跳转到本网页对应的界面(#＋标签名),锚点链接

```html
<body>
    <div>
        <a href="#div1">第一個
        <a href="#div2">第二個
        <a href="#div3">第三個
    </div>
   <div id="div1">
        給你康一個好康的
        <a href="https://www.bilibili.com/video/BV1UT42167xb/?spm_id_from=333.337.search-card.all.click&vd_source=518611c018aea9be639c19407f18f2c4" 
        target="_blank">
        視頻</a>
    </div>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <div id="div2">
        康第二個好康的
        <a href="https://www.bilibili.com/video/BV1UT42167xb/?spm_id_from=333.337.search-card.all.click&vd_source=518611c018aea9be639c19407f18f2c4" 
        target="_blank">
        視頻</a>
    </div>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <div id="div3">
        康第三個好康的
        <a href="https://www.bilibili.com/video/BV1UT42167xb/?spm_id_from=333.337.search-card.all.click&vd_source=518611c018aea9be639c19407f18f2c4" 
        target="_blank">
        視頻</a>
    </div>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
</body>
```

<h3>视频标签video</h3>
video标签:<br>
controls属性:增加控制(开始暂停)<br>
autoplay属性:自动播放<br>
loop属性:循环播放<br>
muted属性:静音播放<br>
poster属性:展示视频的封面<br>
track标签用于添加字幕

```html
<body>
    <video width="720" height="540" controls autoplay loop>
        <source src="..\【4K珍藏】诈骗神曲《Never Gonna Give You Up》！愿者上钩！.mp4">
    </video>
</body>
```

<br>
<hr>
<br>
<h3>列表</h3>
ol标签:有序列表<br>
tape属性:可以选择排列的方式<br>

```THML
<div>
    <h4>下面属于前端语言的是:</h4>
    <ol type="A">
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ol>
</div>
```
<br>
ul标签:无序列表
type属性: disc实心圆(默认) circle空心圆心

```HTMl
<div>
    <h4>下面属于前端语言的是:</h4>
    <ul type="circle">
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
    </ul>
</div>
```
<br>
<hr>
<br>
<h3>表格table</h3>
table标签: table <br>
内部的tr标签为行,th表示表头的单元格<br>
caption标签:可以为表格添加清单

```HTML
<div>
    <table>
         <caption>前端基础框架</caption>
        <tr>
            <th>HTML</th>
            <td>CSS</td>
            <td>JavaScript</td>
        </tr>
        <tr>
            <td>1</td>
            <td>2</td>
            <td>3</td>
        </tr>
        <tr>
            <td>♥</td>
            <td>🐕</td>
            <td>🐱</td>
        </tr>
    </table>
</div>
```
<img width="843" height="157" alt="image" src="https://github.com/user-attachments/assets/53085975-3905-4413-a5b7-c52e80d3c993" />
























