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
<br>
<hr>
<br>
<h3>在网页中嵌入另外的页面</h3>

```HTML
<body>
    <iframe src="https://www.bilibili.com/" width="100%" height="100%"></iframe> 
</body>
```
网页的嵌入代码<br>
<img width="726" height="424" alt="image" src="https://github.com/user-attachments/assets/2259231b-4b4a-4b73-8e6e-54f22a455d0b" />

```HTML
<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=1706416465&bvid=BV1UT42167xb&cid=1641702404&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
```
<br>
<hr>
<br>
<h3>其他标签</h3>
header:定义页面或部分的头部，通常包含标题和导航。<br>
nav:定义导航链授的部分。<br>
article:表示独立的内容块，通常是可以独立分发的文章。<br>
section>:定义文档中的区域或章节，用于组织内容。<br>
aside:表示与主内容相关的附加信息，通常用于侧边栏。<br>
footer:定义页面或部分的底部，通常包含版权信息和联系信息。<br>
<h3>最后用一个代码总结html的基础框架</h3>

```HTML
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的 HTML 学习总结</title>
</head>

<body>
    <!-- header：网页顶部，通常放标题和导航 -->
    <header>
        <h1>我的 HTML 学习总结</h1>
        <p>这是我今天学习 HTML 后制作的第一个小网页。</p>

        <!-- nav：网页导航；点击链接会跳转到对应 id 的区域 -->
        <nav>
            <a href="#basic">基础标签</a> |
            <a href="#media">图片和视频</a> |
            <a href="#list">列表</a> |
            <a href="#table">学习计划</a> |
            <a href="#about">关于我</a>
        </nav>
    </header>

    <hr>

    <!-- main：页面的主要内容 -->
    <main>
        <!-- section：把相关内容组织成一个区域 -->
        <section id="basic">
            <h2>一、HTML 基础标签</h2>

            <p>
                HTML 使用<strong>标签</strong>组织网页内容。
                一个标签可以包含文字，也可以包含其他标签。
            </p>

            <h3>文本格式</h3>
            <p>
                这是普通文字，
                <b>这是粗体</b>，
                <i>这是斜体</i>，
                <s>这是删除线</s>，
                <u>这是下划线</u>。
            </p>

            <p>
                行内标签可以放在段落中，例如用
                <span>span 标记一小段内容</span>。
            </p>

            <h3>div 区域示例</h3>
            <!-- div 常用于把一组相关内容放在一起 -->
            <div>
                <p>这段内容放在一个 div 区域中。</p>
                <p>div 本身不会自动显示边框。</p>
            </div>
        </section>

        <hr>

        <section id="media">
            <h2>二、图片和视频</h2>

            <h3>图片</h3>
            <!-- src 是图片地址；alt 是图片无法显示时的替代文字 -->
            <img
                src="https://placehold.co/640x240?text=HTML+Learning"
                alt="HTML 学习主题占位图片"
                title="我的 HTML 学习页面"
                width="640"
            >

            <h3>链接</h3>
            <p>
                点击下面的链接访问
                <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML"
                   target="_blank">
                    MDN 的 HTML 文档
                </a>。
                target="_blank" 表示在新标签页打开。
            </p>

            <h3>视频</h3>
            <p>把视频文件放到这个 HTML 文件旁边，并将文件名改成 my-video.mp4，就可以尝试播放：</p>

            <!-- 将 my-video.mp4 替换成你自己的视频文件名 -->
            <video width="480" controls muted loop>
                <source src="my-video.mp4" type="video/mp4">
                你的浏览器不支持 video 标签。
            </video>

            <!--
            自动播放常会被浏览器拦截。
            若要测试自动播放，可尝试在 video 上增加 autoplay muted。
            -->
        </section>

        <hr>

        <section id="list">
            <h2>三、列表</h2>

            <h3>我今天学到的标签</h3>
            <!-- ul 是无序列表，每一项使用 li -->
            <ul>
                <li>标题：h1 到 h6</li>
                <li>段落：p</li>
                <li>链接：a</li>
                <li>图片：img</li>
            </ul>

            <h3>制作网页的步骤</h3>
            <!-- ol 是有序列表 -->
            <ol>
                <li>创建 HTML 文件</li>
                <li>编写页面结构</li>
                <li>用浏览器打开页面</li>
            </ol>
        </section>

        <hr>

        <section id="table">
            <h2>四、我的学习计划</h2>

            <!-- table 表示表格；tr 是行，th 是表头单元格，td 是普通单元格 -->
            <table>
                <caption>前端学习安排</caption>
                <tr>
                    <th>学习内容</th>
                    <th>学习状态</th>
                    <th>备注</th>
                </tr>
                <tr>
                    <td>HTML</td>
                    <td>正在学习</td>
                    <td>今天完成基础标签总结</td>
                </tr>
                <tr>
                    <td>CSS</td>
                    <td>准备学习</td>
                    <td>之后学习网页样式</td>
                </tr>
                <tr>
                    <td>JavaScript</td>
                    <td>准备学习</td>
                    <td>之后学习网页交互</td>
                </tr>
            </table>
        </section>

        <hr>

        <article id="about">
            <h2>五、关于这篇总结</h2>
            <p>
                这是一篇独立的学习记录。我会继续整理每天学到的知识，
                并尝试把知识点做成可以直接打开的小网页。
            </p>
            <p><a href="#top">返回页面顶部</a></p>
        </article>
    </main>

    <!-- footer：网页底部，通常放作者或版权信息 -->
    <footer>
        <hr>
        <p>我的 HTML 学习笔记</p>
    </footer>
</body>
</html>
```


























