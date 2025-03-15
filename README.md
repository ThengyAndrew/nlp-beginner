<img width="638" alt="CRF" src="https://github.com/user-attachments/assets/82ebcbcf-70ec-4244-94cd-921f1ec04688" /># nlp-beginner

## Task1

用向量空间法表示文本，原始文本和词袋和 IDF 存在类 Documents 的实例中，再将 doc 载入自定义的 Dataset ，送入 net 中计算。
代码位于 [./Task1](https://github.com/ThengyAndrew/nlp-beginner/tree/main/Task1) , 目前最新版本为 [./Task1/Ver1.1.ipynb](https://github.com/ThengyAndrew/nlp-beginner/blob/main/Task1/Ver1.1.ipynb).

### Documents & Document & Bag & Queries

- train 和 test 产生的词袋来到了惊人的 17000 余词，梯度极高，全部数据无法同时存储，故 doc 实例中只存储了 bag，texts（原始文本）和 idf ，每条文本的 df 动态生成并销毁。
- 可能要考虑简化词袋来降低梯度，进而降低计算难度，但是还没有从数学上得到合适的简化方法

### net

这里直接采用了 pytorch 中集成的 api 来构造 net，结构参考了《动手学深度学习》中的多分类部分 [3.7. softmax回归的简洁实现](https://zh-v2.d2l.ai/chapter_linear-networks/softmax-regression-concise.html)

### 训练结果

无论怎样调整 ls, 激活函数, batch_size, 隐藏层神经元数量, 最终 test_acc 都无法超过 0.4, 在极少情况下可能达到 0.5


## Task2

代码位于 [./Task2](https://github.com/ThengyAndrew/nlp-beginner/tree/main/Task2) , 目前最新版本为 [./Task2/Ver1.1.ipynb](https://github.com/ThengyAndrew/nlp-beginner/blob/main/Task2/Ver1.1.ipynb).

用 N-gram 表示原始文本，通过 word-embedding 降维后输入 CNN 中进行分类。  
通过提高 epoch_num 在 train 数据集上的 loss 可以降低至 0.001 ，但是引入 test 数据集测试后发现 test_loss 高达 1.5，产生了过拟合。为减少过拟合引入了 dropout 层，但效果不佳，最终 test_loss 仍然在 1.5 上下。