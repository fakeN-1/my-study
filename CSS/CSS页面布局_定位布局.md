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



















