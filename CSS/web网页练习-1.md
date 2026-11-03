## 入门网页项目：个人兴趣介绍页

制作一个单页网页，介绍你的一项兴趣，例如阅读、旅行、摄影、游戏或运动。只使用 **HTML 和 CSS**，不需要 JavaScript。

### 页面结构

按以下顺序制作：

1. **页面标题**
   - 网页顶部显示一个主标题，例如“我的摄影兴趣”。
   - 标题下方写一句简短介绍。

2. **导航栏**
   - 放置 3 个文字链接：关于我、我的兴趣、联系我。
   - 点击链接时，页面可以跳到对应内容区域。
  
3. **关于我**
   - 添加一个小标题和一段 2～3 句话的自我介绍。

4. **我的兴趣**
   - 添加一个小标题。
   - 展示 **3 个兴趣内容卡片**，每张卡片包含：
     - 一张图片
     - 一个兴趣名称
     - 一句介绍

5. **联系我**
   - 添加一个小标题和一行联系信息，例如邮箱地址。

```html
<a href="mailto:hello@example.com">hello@example.com</a>
```

6. **页脚**
   - 写一行版权信息，例如“© 2026 我的兴趣介绍页”。
 
```
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>我的兴趣介绍页</title>
  <link rel="stylesheet" href="题目1 解题.css">
</head>
<body>
  <header class="page-header">
    <h1>我的摄影兴趣</h1>
    <p>用镜头记录生活中的小美好。</p>
  </header>

  <nav class="navigation">
    <a href="#about">关于我</a>
    <a href="#hobbies">我的兴趣</a>
    <a href="#contact">联系我</a>
  </nav>

  <main class="container">
    <section id="about" class="about">
      <h2>关于我</h2>
      <p>
        你好，我是一名喜欢观察生活的学生。平时我喜欢用相机拍下风景、
        美食和有趣的瞬间，也喜欢和朋友分享自己的照片。
      </p>
    </section>

    <section id="hobbies" class="hobbies">
      <h2>我的兴趣</h2>

      <div class="card-list">
        <article class="card">
          <img src="image/1.png" alt="阳光照耀下的自然风景">
          <h3>拍摄风景</h3>
          <p>记录公园、街道和旅途中遇见的美丽景色。</p>
        </article>

        <article class="card">
          <img src="image/2.png" alt="摆放在桌上的美食">
          <h3>拍摄美食</h3>
          <p>用照片记录喜欢的食物，也让日常生活更有趣。</p>
        </article>

        <article class="card">
          <img src="image/3.png" alt="城市街道上的建筑">
          <h3>街头摄影</h3>
          <p>观察城市里的人和事，捕捉生活中的自然瞬间。</p>
        </article>
      </div>
    </section>

    <section id="contact" class="contact">
      <h2>联系我</h2>
      <p>
        欢迎和我交流摄影：
        <a href="mailto:hello@example.com">hello@example.com</a>
      </p>
    </section>
  </main>

  <footer class="page-footer">
    <p>© 2026 我的兴趣介绍页</p>
  </footer>
</body>
</html>
```

```
body{
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f4f7f6;
  color: #263238;
  line-height: 1.6;
  font-size: 16px;
}
.page-header{
  padding:40px 20px;
  text-align: center;
  background-color: #d9eee8
}
.page-header h1{
  margin:0 0 10px;
  font-size:36px;
}
.page-header p{
  margin:0;
  font-size:18px;
}
.navigation{
  display: flex;
  justify-content: center;
  gap: 38px;
  padding:16px;
  background-color: #2f6f64;
}
.navigation a{
  color: white;
  text-decoration: none;
  transition: color 0.3s ease;
}
.navigation a:hover{
  color: #cdebe2;
}
.container{
  width:min(100%-40px,960px);
  margin:0 auto;
}
.hobbies{
  padding:30px 0;
}
section h2 {
  margin-top: 0;
  color: #2f6f64;
}
.card-list {
  display: flex;
  margin:0 20px;
  flex-wrap: wrap;
  gap: 20px;
}
.card{
  flex: 1 1 200px;
  overflow: hidden;
  padding-bottom: 20px;
  border-radius: 12px;
  background-color: white;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
  transition: transform 0.2s, box-shadow 0.2s;
}
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.13);
}
h2{
  margin:0 20px;
}
.card>img{
  height:180px;
  width: 100%;
  display: block;
  object-fit: cover;
}
.contact a {
  color: #2f6f64;
}

.contact a:hover {
  color: #17483f;
}

/* 页脚 */
.page-footer {
  padding: 18px;
  text-align: center;
  color: white;
  background-color: #263f3a;
}

.page-footer p {
  margin: 0;
}

/* 窄屏时调整导航和标题 */
@media (max-width: 500px) {
  .page-header h1 {
    font-size: 28px;
  }

  .navigation {
    gap: 18px;
  }
}

```
