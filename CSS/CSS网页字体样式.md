<h3>字体样式</h3>

```
  font-family: Arial, "Microsoft YaHei", sans-serif; /* 字体；按顺序尝试，最后写通用字体 */
  font-size: 16px;        /* 字号 */
  font-weight: 400;       /* 字重：400 正常，700 通常是粗体 */
  font-style: normal;     /* normal 正常；italic 斜体 */
  line-height: 1.6;       /* 行高，常用无单位数值 */
  color: #333333;         /* 文字颜色 */
```
font-family属性:字体<br>
可以按优先顺序写多个字体。浏览器会尝试第一个字体，如果设备没有，就继续尝试后面的字体。<br>

```
font-family: "微软雅黑","Microsoft YaHei", Arial, sans-serif;
```
<hr>
font-size属性:字体大小<br>
常见单位:px 像素, rem 根元素字体, em相对于当前元素的字号

```
div>p:nth-child(1){
    font-size: 5px;
}
div>p:nth-child(2){
    font-size: 5rem;
}
div>p:nth-child(3){
    font-size: 5em;
}

```
<img width="843" height="449" alt="image" src="https://github.com/user-attachments/assets/d76312f7-365b-4dc5-a0ca-a836669e1164" /
<br>
<hr>
font-weight属性:字重<br>
用于表示字体的粗细,可以使用normal和bold表述,也可以用数字表述.

```
div>p:nth-child(1){
    font-weight:normal;
}
div>p:nth-child(2){
    font-weight:bold;
}
div>p:nth-child(3){
    font-weight:300;
}
div>p:nth-child(4){
    font-weight:500;
}
div>p:nth-child(5){
    font-weight:700;
}
```

<img width="843" height="224" alt="image" src="https://github.com/user-attachments/assets/6fdc906a-c972-4d09-bb43-2e5cb7a7a0d1" />
<br>
<hr>
font-style属性:字体样式<br>
主要分为normal(正常)和italic(斜体)
<img width="843" height="101" alt="image" src="https://github.com/user-attachments/assets/1fe81a31-b6eb-4c78-bd90-9e7c426f4be3" />

<br>
<hr>
line-height属性:行高<br>
不带单位的 2.5 表示行高约为字号的2.5 倍，通常比固定写成 16*2.5px 更灵活。<br>

正常行高:<br>
<img width="843" height="91" alt="image" src="https://github.com/user-attachments/assets/3b335197-aeba-4b1b-976d-cff2bb6c1c2e" />

2.5行高:<br>
<img width="843" height="109" alt="image" src="https://github.com/user-attachments/assets/52ed345f-f02e-4af2-b862-07c88d4a99ff" />

<br>
<hr>
color属性:字体颜色<br>

```
color:red
```





































