<h3>token词元</h3>
<hr>
Token 是 LLM 处理文本的基本单位（不是字，也不是词）
<br>token影响LLM 的计费
Deepseek v4.1token展示
<img width="734" height="419" alt="image" src="https://github.com/user-attachments/assets/80f03bd7-225e-4060-8e40-3e2eb5da0ace" />
GPT-6.1sol
<img width="758" height="537" alt="image" src="https://github.com/user-attachments/assets/75cec8ce-dccf-48c2-9ff0-9e044ae91dd8" />
<br><hr><br>
<h3>Tokenizer分词器</h3>
把文本拆成模型能处理的较小单位，叫 token。token 可能是一个字、词的一部分，或标点；模型处理文本时会先把它们转换成数字。
<br><hr><br>
<h3>token 的流转过程</h3>
输入信息>分词器(转换为数字tokenID:编码)>LLM预测(预测下一个的tokenID)>Decode(对TokenID解码)>输出信息

<br><hr><br>
<h3>token传入LLM后的过程</h3>
过程1.Embedding向量化:把 token 转换成一串数字组成的向量，让模型能用数字表示它的含义和关系。<br>
过程2.transformer:是一种处理文本等序列数据的神经网络架构，也是许多现代大语言模型的基础。<br>

transformer会利用 注意力机制（Attention），判断当前处理某个词时，输入中的哪些其他词更相关，从而结合上下文理解和生成内容。<br><br><hr>
<strong>transformer能够结合上下文进行计算,最终输出包含上下文信息的新的向量.</strong><br><hr>

过程3.使用新的向量预测Token.得到TokenID.<br>
过程4.新的TokenID加入新序列,再次进行Transformer计算.<br>
<br><h6>不断循环直到生成完整的文本</h6>
**<img width="1096" height="504" alt="image" src="https://github.com/user-attachments/assets/d54e2caf-9544-4e09-be61-bf0b876ec453" />
**
























































