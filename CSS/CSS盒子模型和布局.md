<h3>盒子模型</h3><br>
CSS 盒子模型可以把网页里的每个元素想象成一个矩形盒子。盒子从内到外由四部分组成：<br>
<strong>内容 content → 内边距 padding → 边框 border → 外边距 margin<br></strong>
<img width="386" height="202" alt="image" src="https://github.com/user-attachments/assets/18c83ab9-3adb-441c-9ea8-dbd4b1032de1" />
<br>
<hr>
<br>
<h3>两种盒子计算方式</h3>
<br>
<h5>content-box：默认模式</h5><br>
设置的 width 和 height 只计算内容区域，内边距和边框会额外加上去。

```
    height:100px;
    width:100px;
    padding: 10px;
    border: 2px solid red;
```
<img width="843" height="179" alt="image" src="https://github.com/user-attachments/assets/763c9598-7cf0-4a6d-a2ff-21a0fc9f0a2f" />
<img width="416" height="201" alt="image" src="https://github.com/user-attachments/assets/1d37a638-0544-40ee-a395-bd5c54ce6529" />
此时盒子的实际宽度为:100＋左右边距10*2+左右边框2*2=124px<br>
<br>
<hr>
border-box：更直观的模式

```
    box-sizing: border-box;
    height:100px;
    width:100px;
    padding: 10px;
    border: 2px solid red;
```
此时盒子的实际宽度为:100px<br>
<br>
<hr>
<br>
<h5>内边距padding和外边距margin</h5><br>
padding 在盒子里面，margin 在盒子外面。

```
  padding: 20px; /* 卡片内部留白 */
  margin: 20px;  /* 卡片外部与其他元素拉开距离 */
```

<h5>盒子的嵌套</h5>

```
.content{
    width: 200px;
    height: 100px;
    background-color: antiquewhite;
}
.content>div{
    width: 50%;
    height: 50%;
    background-color: aqua;
}
```

<img width="843" height="252" alt="image" src="https://github.com/user-attachments/assets/53a9b9cd-c41e-4608-9d3b-e1561666dba5" />

<h5>滚动区域:overflow</h5><br>
CSS 中的滚动区域，就是内容超出元素可显示范围时，用户可以在元素内部滚动查看内容的区域

```
<body>
<div class="comments">
  <p>第一条评论……</p>
  <p>第二条评论……</p>
  <p>第三条评论……</p>
  <p>第四条评论……</p>
  <p>第五条评论……</p>
  <p>第六条评论…… </p>
  <p>第七条评论……</p>
  <p>第八条评论……</p>
  <p>第九条评论……</p>
  <p>第十条评论……</p>
  <p>第十一条评论……</p>
  <p>第十二条评论……</p>
  <p>第十三条评论……</p>
  <p>第十四条评论……</p>
</div>
</body>
```

```
.comments{
    height: 300px;
    width: 100px;
    border: 1px solid black;
    overflow: auto;
}
```
<img width="843" height="383" alt="image" src="https://github.com/user-attachments/assets/825c427e-bbee-4b9c-b619-36ddfe04d8a3" />









