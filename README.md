# 孪生LSTM网络(Siamese-LSTM)
本项目是基于孪生LSTM网络+注意力机制+曼哈顿距离(Manhattan distance)实现的句对相似度计算。<br>
中文训练数据为蚂蚁金服句对数据，约4万组，正负样本比例1:3.6；英文训练数据来自Kaggle上的Quora句对数据，约40万组，正负样本比例1:1.7。新增一组翻译数据：使用Google Translator将Quora数据翻译成中文。
![](https://cloud.githubusercontent.com/assets/9861437/20479493/6ea8ad12-b004-11e6-89e4-53d4d354d32e.png)

## 资料
- 参考文献
    - [Siamese Recurrent Architectures for Learning Sentence Similarity](http://www.mit.edu/~jonasm/info/MuellerThyagarajan_AAAI16.pdf)
    - [How to predict Quora Question Pairs using Siamese Manhattan LSTM](https://medium.com/mlreview/implementing-malstm-on-kaggles-quora-question-pairs-competition-8b31b0b16a07)
    - 中国大陆可能无法访问《How to predict...Manhattan LSTM》一文，请直接查看本项目中附件之参考博客
- 其它数据
    - 英文词向量：[GoogleNews-vectors-negative300.bin.gz](https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?usp=sharing)
    - 英文词向量：[GoogleNews-vectors-negative300.bin.gz的百度网盘地址](https://pan.baidu.com/s/1dEENGPV)
    - 中文词向量：[基于120G中文语料训练的64维、128维词向量](https://weibo.com/p/23041816d74e01f0102x77v)
- 工程参考
    - [likejazz/Siamese-LSTM](https://github.com/likejazz/Siamese-LSTM) Original author's GitHub
    - [做个聊天机器人/智能客服](https://zhuanlan.zhihu.com/p/31638132) 一些网络设计思路

## 使用
### 训练
```
$ python3 train.py
$ type cn for Chinese Data or en for English Data
```

### 验证
```
$ python3 predict.py
$ type cn for Chinese Data or en for English Data
```

### 预测
```
$ python3 score.py
$ type cn for Chinese Data or en for English Data
```

### 效果
```
$ 根据数据比例来看，中文训练集的基准准确率应为0.783，英文与翻译数据为0.630
$ =================================================================================================
$ 中文 数据实际训练 5 轮时的效果：使用随机词向量时，训练集十折交叉0.778；使用CN120G词向量时，训练集十折交叉0.789
$ 英文 数据实际训练 5 轮时的效果：使用随机词向量时，训练集十折交叉0.774；使用Google词向量时，训练集十折交叉0.771
$ 翻译 数据实际训练 5 轮时的效果：使用随机词向量时，训练集十折交叉0.755；使用CN120G词向量时，训练集十折交叉0.756
$ =================================================================================================
$ 中文 数据实际训练 8 轮时的效果：使用随机词向量时，训练集十折交叉0.777；使用CN120G词向量时，训练集十折交叉0.787
$ 英文 数据实际训练 8 轮时的效果：使用随机词向量时，训练集十折交叉0.774；使用Google词向量时，训练集十折交叉0.778
$ 翻译 数据实际训练 8 轮时的效果：使用随机词向量时，训练集十折交叉0.786；使用CN120G词向量时，训练集十折交叉0.786
$ =================================================================================================
$ 总结：1.有无预训练词向量几乎不影响结果;2.中文数据上训练几乎没有效果，和英文形成鲜明对比--这可能是因为蚂蚁金服数据间太相似了或者数据量太小，翻译数据集上的实验证明了这一点。
```
