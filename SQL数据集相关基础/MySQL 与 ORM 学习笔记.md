# MySQL 与 ORM 学习笔记

> 学习日期：2026-11-19\
> 学习主题：MySQL 数据库创建、SQL 基础、SQLAlchemy 连接数据库

## 一、今天学到了什么？

今天主要弄清楚了几个容易混淆的概念：

-   **SQL**：一种操作关系型数据库的语言。
-   **MySQL**：一种数据库管理系统，负责管理和存储数据，并执行 SQL。
-   **ORM**：对象关系映射技术，让我们可以通过 Python 对象操作数据库。
-   **SQLAlchemy**：Python 中常用的数据库工具库，支持
    ORM，也支持直接构建和执行 SQL。

简单记忆：

**SQL 是语言，MySQL 是数据库管理系统，SQLAlchemy 是 Python
操作数据库的工具。**

## 二、SQL 和 MySQL 有什么区别？

SQL（Structured Query
Language，结构化查询语言）是一种数据库操作语言，常见操作包括：

  SQL 语句            作用
  ------------------- ------------
  `CREATE DATABASE`   创建数据库
  `CREATE TABLE`      创建数据表
  `INSERT`            插入数据
  `SELECT`            查询数据
  `UPDATE`            修改数据
  `DELETE`            删除数据

MySQL 则是能够接收并执行 SQL 语句的数据库管理系统。

可以这样理解：

-   SQL：告诉数据库要做什么。
-   MySQL：负责执行操作、管理数据。

## 三、数据库、数据表和字段

它们之间是包含关系：

``` text
MySQL Server（数据库服务）
└── my_project（数据库）
    └── users（数据表）
        ├── id（字段）
        ├── username（字段）
        ├── password（字段）
        └── age（字段）
```

-   **数据库（Database）**：用于组织和存储数据的空间。
-   **数据表（Table）**：数据库中用于存放同类数据的结构。
-   **字段（Column）**：描述每条记录具有哪些信息。
-   **记录（Row）**：表中的一行具体数据。

一个数据库可以包含多张数据表。

## 四、使用 MySQL 创建数据库

### 1. 连接 MySQL

本地 MySQL 服务启动后，可以使用 MySQL Workbench 等客户端连接它。

本次练习使用的连接信息：

-   主机：`localhost`
-   端口：`3306`
-   用户：`root`

注意：数据库密码不要写进公开的学习笔记或上传到 GitHub 的代码中。

### 2. 创建数据库

``` sql
CREATE DATABASE my_project
DEFAULT CHARACTER SET utf8mb4
DEFAULT COLLATE utf8mb4_unicode_ci;
```

这里：

-   `CREATE DATABASE`：创建数据库。
-   `my_project`：数据库名称。
-   `utf8mb4`：常用字符集，可以存储中文和其他 Unicode 字符。
-   `IF NOT EXISTS`
    可以加在数据库名称前，避免数据库已存在时重复创建报错。

### 3. 查看数据库

``` sql
SHOW DATABASES;
```

### 4. 选择数据库

``` sql
USE my_project;
```

选择后，后续 SQL 操作默认针对 `my_project`。

### 5. 创建数据表（示例）

``` sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL,
    password VARCHAR(255) NOT NULL,
    age INT
);
```

常见字段类型：

  类型            含义
  --------------- --------------------------------
  `INT`           整数
  `VARCHAR(50)`   最多 50 个字符的可变长度字符串
  `TEXT`          较长文本
  `DATETIME`      日期和时间

常见约束：

-   `PRIMARY KEY`：主键，用于唯一标识一条记录。
-   `AUTO_INCREMENT`：插入记录时自动生成递增编号。
-   `NOT NULL`：字段不能为空。

查看数据表：

``` sql
SHOW TABLES;
DESC users;
```

## 五、SQL 和 ORM 的关系

SQL 和 ORM 都可以完成数据库操作，但写法不同。

例如，查询年龄大于 18 岁的用户：

**直接使用 SQL：**

``` sql
SELECT * FROM users
WHERE age > 18;
```

**使用 SQLAlchemy ORM：**

``` python
from sqlalchemy import select

stmt = select(User).where(User.age > 18)
users = session.scalars(stmt).all()
```

两种方式都能完成查询。ORM 通过模型和 Python 对象表达操作，SQLAlchemy
会构建相应的 SQL 并通过数据库驱动执行。

## 六、SQLAlchemy 是什么？

SQLAlchemy 是 Python 的数据库工具库，不是 MySQL，也不是数据库本身。

它主要有两个部分：

-   **SQLAlchemy Core**：使用 Python 构建和执行 SQL。
-   **SQLAlchemy ORM**：通过 Python 类和对象映射数据库表和记录。

ORM 中常见的对应关系：

  Python 中的概念     数据库中的概念
  ------------------- ----------------
  类（Class）         表（Table）
  对象（Object）      记录（Row）
  属性（Attribute）   字段（Column）

## 七、使用 SQLAlchemy 连接 MySQL

### 1. 安装依赖

``` bash
pip install sqlalchemy pymysql
```

-   `sqlalchemy`：数据库操作工具库。
-   `pymysql`：Python 连接 MySQL 的驱动。

### 2. 创建数据库引擎

``` python
from sqlalchemy import create_engine

DATABASE_URL = (
    "mysql+pymysql://用户名:密码@localhost:3306/my_project"
)

engine = create_engine(DATABASE_URL)
```

连接地址的组成：

  部分           含义
  -------------- --------------------
  `mysql`        数据库类型
  `pymysql`      Python 数据库驱动
  用户名、密码   MySQL 登录凭据
  `localhost`    数据库服务器地址
  `3306`         MySQL 默认端口
  `my_project`   要连接的数据库名称

### 3. 测试连接

本次在 PyCharm 中使用了下面的代码：

``` python
from sqlalchemy import text

with engine.connect() as conn:
    result = conn.execute(text("SELECT DATABASE()"))
    print(result.scalar())
```

运行后输出：

``` text
my_project
```

这说明 SQLAlchemy 已成功连接 MySQL，并且当前连接使用的数据库是
`my_project`。

**注意：** `create_engine()` 创建的是 SQLAlchemy
的数据库引擎对象；它不会自动创建 MySQL 数据库。MySQL 中的 `my_project`
需要事先存在。

## 八、SQLAlchemy ORM 建表的基本思路

连接数据库之后，就可以使用 ORM 定义模型并创建数据表。

基本流程：

1.  创建数据库连接引擎 `engine`。
2.  定义 ORM 模型基类 `Base`。
3.  定义模型类，例如 `User`。
4.  在模型中定义表名和字段。
5.  调用 `Base.metadata.create_all(engine)` 创建尚不存在的数据表。

示意代码：

``` python
from sqlalchemy import String
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "users"

    id: Mapped[int] = mapped_column(primary_key=True)
    username: Mapped[str] = mapped_column(String(50))
```

``` python
Base.metadata.create_all(engine)
```

`create_all()` 会根据模型创建尚不存在的表，但不会自动创建 MySQL
数据库，也不会自动把已有表结构迁移到最新模型结构。

## 九、今天的核心知识总结

  名称                记忆要点
  ------------------- ---------------------------------------
  SQL                 数据库操作语言
  MySQL               数据库管理系统
  ORM                 对象关系映射技术
  SQLAlchemy          Python 数据库工具库，支持 ORM 和 Core
  PyMySQL             Python 的 MySQL 驱动
  Engine              SQLAlchemy 的数据库引擎对象
  `create_engine()`   创建数据库引擎
  `create_all()`      根据模型创建尚不存在的数据表

### 一句话记忆

**MySQL 负责管理和存储数据，SQL 是操作数据库的语言，SQLAlchemy 让 Python
能够方便地通过 SQL 或 ORM 操作数据库。**

