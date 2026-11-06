<h3>Context Window :上下文窗口</h3>
<hr><br>
上下文窗口:是LLM一次能够处理的最大Token的容量限制.<br>
LLM容量参考(一个中文字符约等于0.6个Token):
<img width="788" height="234" alt="image" src="https://github.com/user-attachments/assets/d29cc7c7-12e4-4498-88a4-955fe9086c2e" />
<hr><br>
<h3>Memory:记忆</h3>
记忆:就是模型在当前对话之外保留或取回信息，以便之后回答时使用
<br>1.参数知识:模型在训练的时候得到的长期知识.
<br>2.上下文信息:当前聊天窗口的上下文消息.(AI 的临时记忆)
<br>3.平台记忆:产品把一些信息保存起来,在本窗口需要的时候使用.
<br>4.Agent记忆:Agent系统为了完成长期系统增加的外部记忆.
<hr><h3>RAG:检索增强生成</h3>
<br>RAG:(给LLM一个外部的资源库)让 LLM 先查资料、再回答的方式.
<br>RAG产生的原因:
<br>1.知识的时效性  2.AI没有用户的私有信息    3.LLM预测的幻觉    4.海量文档的检索效率低
<img width="1103" height="459" alt="image" src="https://github.com/user-attachments/assets/2f3c09d1-7576-4771-99b6-25b651d24303" />

<hr><br><h5>RAG完整流程</h5>
<h6><br>LLM准备:
 <br> 1.将文件的内存完整解析读取
  <br>2.切分文档的内容
  <br>3.向量化(Embedding):便于比较相似度,按照含义查找
<br>4.建立索引:将向量和原文等信息储存,并且做好索引
<br>用户:5.把用户的问题转换为向量,并且搜索
  <br>6.Rerank重排(可选)
  <br>7.整理为上下文
  <br>8.LLM生成答案.</h6>
  <strong>RAG总结:把资料切块并索引；提问时找出相关片段，连同问题交给 LLM 作答</strong>
<img width="899" height="35" alt="image" src="https://github.com/user-attachments/assets/2b549059-ffef-46af-88a7-b96e0e630e44" />







