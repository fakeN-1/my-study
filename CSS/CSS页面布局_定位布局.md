<h3>默认定位：static</h3><br>
static是元素的默认状态。元素按 HTML 顺序正常排列

```
position: static;
```
<br>
<hr>
<br>
<h3>相对定位：relative</h3>
元素仍保留原来的位置空间，只是在视觉上相对原位置挪动。

```
  position: relative;
  top: 4px;   /* 向下移动 4px */
  left: 8px;  /* 向右移动 8px */
```
<br>
<hr>
<br>
<h3>绝对定位：absolute</h3>
元素会脱离正常文档流，不再占据原来的排版空间。它通常相对最近的、设置了定位的祖先元素定位。

```
.card {
  position: relative; /* 给图片建立定位参照 */
  width: 300px;
  background-color: rgb(151, 151, 151);

}

.card img {
  display: block;
  width: 100%;
}

.badge {
  position: absolute;
  background-color: #f00;
  bottom:0px;
  right:20px;
}
```
<img width="843" height="133" alt="image" src="https://github.com/user-attachments/assets/ec1bb7a8-c995-4e95-9d17-82e339ffcc5b" />
<br>
<hr>
<br>
<h3>固定定位：fixed</h3>
元素通常相对浏览器视口定位。滚动页面时，它会留在屏幕同一位置。<br>
<h3>粘性定位：sticky</h3>
元素在正常流中占有空间，滚动到指定位置后才“粘”在视口边缘。<br>
<br>
<hr>
<br>
<h3>包含块</h3><br>
浏览器计算某些元素的尺寸和位置时，作为参照的区域。
<br>静态和相对定位(static/relative)
<br>绝对定位(absolute)
<br>固定定位(fixed)
<br>
<hr>
<br>
<h3>Z轴顺序:z-index</h3>
z 轴顺序决定元素在屏幕上谁盖在谁上面<br>

```
.box-a{
  left: 50px;
  top: 50px;
  z-index: 1;
  background-color: red;
}
.box-b{
  left: 80px;
  top: 80px;
  z-index: 2;
  background-color: green;
}
```
A的index为1,B的index为2,则B在A 的上方<br>
<img width="843" height="240" alt="image" src="https://github.com/user-attachments/assets/fa844768-f323-4f55-b95c-b9ab09d8f082" />
<br>
<hr>
<br>
<h3>层叠上下文</h3>
浏览器把一组元素当成一个整体，决定它们前后覆盖顺序的规则。<br>

```
<div class="folder-a" >
  <div class="popup">绿色区域</div>
</div>
<div class="folder-b" >黑色区域</div>
```

```
.folder-a {
  position: relative;
  z-index: 1; /* 建立层叠上下文，整个 A 文件夹层级是 1 */
}

.popup {
  position: absolute;
  z-index: 9999; /* 只在 A 文件夹内部比较 */
  background-color: #23e633;
}

.folder-b {
  position: relative;
  z-index: 2; /* B 文件夹整体比 A 高 */
  background-color: #000000;
}
```
z-index 不是全页面的统一排名.。不同上下文之间，浏览器先比较它们所在上下文的层级；内部数值不会越级参与外部比较。

<img width="843" height="108" alt="image" src="https://github.com/user-attachments/assets/2c142ca6-0760-4165-beae-a72b613b2c71" />























