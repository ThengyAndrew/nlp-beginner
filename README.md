<img width="638" alt="CRF" src="https://github.com/user-attachments/assets/82ebcbcf-70ec-4244-94cd-921f1ec04688" /># nlp-beginner

## Task1

用向量空间法表示文本，原始文本和词袋和 IDF 存在类 Documents 的实例中，再将 doc 载入自定义的 Dataset ，送入 net 中计算。
代码位于(./Task)[https://github.com/ThengyAndrew/nlp-beginner/tree/main/Task1], 目前最新版本为 (./Task/Ver1.1.ipynb)[]

### Documents & Document & Bag & Queries

- train 和 test 产生的词袋来到了惊人的 17000 余词，梯度极高，全部数据无法同时存储，故 doc 实例中只存储了 bag，texts（原始文本）和 idf ，每条文本的 df 动态生成并销毁。
- 可能要考虑简化词袋来降低梯度，进而降低计算难度，但是还没有从数学上得到合适的简化方法

### net

这里直接采用了 pytorch 中集成的 api 来构造 net，结构参考了《动手学深度学习》中的多分类部分 [3.7. softmax回归的简洁实现](https://zh-v2.d2l.ai/chapter_linear-networks/softmax-regression-concise.html)

### 训练结果

无论怎样调整 ls, 激活函数, batch_size, 隐藏层神经元数量, 最终 test_acc 都无法超过 0.4, 在极少情况下可能达到 0.5
