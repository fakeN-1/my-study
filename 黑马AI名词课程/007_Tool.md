# [Tool工具]
>LLM可以使用的外部工具

---

## LLM的局限性

<img width="973" height="385" alt="image" src="https://github.com/user-attachments/assets/478ae686-7612-4a1f-b751-f9eb8689b35a" />

## Tool的实际运用
查询天气:<img width="305" height="344" alt="image" src="https://github.com/user-attachments/assets/0a893d36-cdb2-4125-9e66-df4f2435a003" />

### 常见的Tool工具
```
网页搜索,代码执行,文件搜索,数据库查询,应用接口(API),电脑操作.
```
## Tool从哪里来
>Tool通常是开发者提前开发,配置或接入的
>Agent可以简化理解为:LLM＋Tool＋循环控制

## Tool的组成
- 工具定义:工具名称,工具需要的限权.
- 工具实现:接收参数,调用外部的服务.
- 返回结果:把执行的结果返回给LLM.
  <img width="1061" height="446" alt="image" src="https://github.com/user-attachments/assets/045b2c1d-8392-41c2-8ab1-829bd53b2000" />

## Tool和RAG的区别
- Tool:让LLM选择调用的工具,解决Ai无法执行的问题(**做事**)
- RAG:获取外部的信息,解决AI知识不足的问题(**思考**)

  



