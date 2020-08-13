---
title: "Paraphrase Identification"
permalink: /resources/paraphrase-identification/
excerpt: "Determine whether two sentences have the same meaning, a problem considered a touchstone of natural language understanding."
last_modified_at: 2020-08-11
redirect_from:
  - /theme-setup/
toc: true
---

**Paraphrase Identification** is an task to determine whether two sentences have the same meaning, a problem considered a touchstone of natural language understanding.

Some benchmark datasets are listed in the following.

## Classic Datasets

<table style="width: 300px; margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th>Dataset</th>
<th>pairs of sentence</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://www.microsoft.com/en-us/download/details.aspx?id=52398&amp;from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fdownloads%2F607d14d9-20cd-47e3-85bc-a2f65cd28042%2Fdefault.aspx"><strong>MRPC</strong></a></td>
<td>5800</td>
</tr>
<tr>
<td>STS</td>
<td>1750</td>
</tr>
<tr>
<td>SICK-R</td>
<td>9840</td>
</tr>
<tr>
<td>SICK-E</td>
<td>9840</td>
</tr>
</tbody>
</table>

- [**MRPC**](https://www.microsoft.com/en-us/download/details.aspx?id=52398&from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fdownloads%2F607d14d9-20cd-47e3-85bc-a2f65cd28042%2Fdefault.aspx) is short for Microsoft Research Paraphrase Corpus. It contains 5,800 pairs of sentences which have been extracted from news sources on the web, along with human annotations indicating whether each pair captures a paraphrase/semantic equivalence relationship.
- [**SentEval**](https://arxiv.org/pdf/1803.05449.pdf) encompasses semantic relatedness datasets including
SICK and the STS Benchmark dataset.
For semantic relatedness, which consists of predicting a semantic score between 0 and 5 from two input sentences, it learns to predict the probability distribution of relatedness scores.

- [**Quora Question Pairs**](https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs) is a task released by Quora which aims to identify duplicate questions. It consists of over 400,000 pairs of questions on Quora, and each question pair is annotated with a binary value indicating whether the two questions are paraphrase of each other.

A list of neural matching models for paraphrase identification models are as follows.

## Performance

### MRPC & SentEval

In MRPC, value1/value2 means accuracy/f1 and a single value means only accuracy. 

In STS and SICK, value1/value2 means pearson correlation/accuracy and a single value means only pearson correlation.

|                     Model                     |                             Code                             |     MRPC      |  SICK-R  |  SICK-E  |      STS      |                            Paper                             |
| :-------------------------------------------: | :----------------------------------------------------------: | :-----------: | :------: | :------: | :-----------: | :----------------------------------------------------------: |
|       TF-KLD (Ji and Eisenstein, 2013)        |                             N/A                              |   80.4/85.9   |    —     |    —     |       —       | [Discriminative Improvements to Distributional Sentence Similarity](http://www.aclweb.org/anthology/D/D13/D13-1090.pdf) |
|       Bi-CNN-MI (Yin and Schutze, 2015)       |                             N/A                              |   78.1/84.4   |    —     |    —     |       —       | [Convolutional Neural Network for Paraphrase Identification](https://www.aclweb.org/anthology/N15-1091.pdf) |
|            PWIM (He and Lin, 2016)            | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/lukecq1231/nli) |       —       |    —     |    —     |     76.7      | [Pairwise Word Interaction Modeling with Deep Neural Networks for Semantic Similarity Measurement](https://www.aclweb.org/anthology/N16-1108.pdf) |
|    Attentive Tree-LSTMs (Zhou et al.2016)     | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/yoosan/sentpair) |   75.8/83.7   |    —     |    —     |       —       | [Modelling Sentence Pairs with Tree-structured Attentive Encoder](https://arxiv.org/pdf/1610.02806.pdf) |
|       InferSent (Conneau et al., 2017)        | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/facebookresearch/InferSent) |   76.2/83.1   |   88.4   |   86.3   |   75.8/75.5   | [Supervised Learning of Universal Sentence Representations from Natural Language Inference Data](https://arxiv.org/abs/1705.02364) |
|   AugDeepParaphrase (Agarwal et al., 2017)    |                             N/A                              |   77.7/84.5   |    —     |    —     |       —       | [A Deep Network Model for Paraphrase Detection in Short Text Messages](https://arxiv.org/pdf/1712.02820.pdf) |
|            ABCNN (Yin et al.2018)             | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/yinwenpeng/Answer_Selection) |   78.9/84.8   |    —     |    —     |       —       | [ABCNN: Attention-Based Convolutional Neural Network for Modeling Sentence Pairs](https://arxiv.org/pdf/1512.05193.pdf) |
|       GenSen (Subramanian et al., 2018)       | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/Maluuba/gensen) |   78.6/84.4   | **88.8** | **87.8** |   78.9/78.6   | [Learning General Purpose Distributed Sentence Representations via Large Scale Multi-task Learning](https://arxiv.org/abs/1804.00079) |
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/HazyResearch/metal) |   91.5/88.5   |    —     |    —     |   90.1/89.7   | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) |
|         This work (Lan and Xu, 2018)          |                             N/A                              |     84.0      |    —     |    —     |       —       | [Character-based Neural Networks for Sentence Pair Modeling](https://www.aclweb.org/anthology/N18-2025.pdf) |
|           MT-DNN (Liu et al., 2019)           | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/namisan/mt-dnn) |   91.1/88.2   |    —     |    —     |   89.5/88.8   | [Multi-Task Deep Neural Networks for Natural Language Understanding](https://arxiv.org/pdf/1901.11504.pdf) |
|           ERNIE (Zhang et al. 2019)           | [![official](https://img.shields.io/badge/official-code-brightgreen)]( https://github.com/thunlp/ERNIE) |     88.2      |    —     |    —     |     83.2      | [ERNIE: Enhanced Language Representation with Informative Entities](https://arxiv.org/pdf/1905.07129.pdf) |
|         SpanBert (Joshi et al., 2019)         | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/facebookresearch/SpanBERT) |   90.9/87.9   |    —     |    —     |   89.9/89.1   | [SpanBERT: Improving Pre-training by Representing and Predicting Spans](https://arxiv.org/pdf/1907.10529.pdf) |
|      MT-DNN-ensemble (Liu et al., 2019)       | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/namisan/mt-dnn/) |   92.7/90.3   |    —     |    —     |   91.1/90.7   | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) |
|  XLNet-Large (ensemble) (Yang et al., 2019)   | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/zihangdai/xlnet/) | **93.0/90.7** |    —     |    —     | **91.6/91.1** | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) |


## Quora Question Pair

| Model | Code | F1 | Accuracy | Paper|
| :-----:| :----: | :----: |:----: |:----: |
|         DecAtt (Parikh et al., 2016)          |                             N/A                              |  —   |   86.5   | [A Decomposable Attention Model for Natural Language Inference](https://arxiv.org/pdf/1606.01933.pdf) |
|          This work (Wang et al.2016)          |                             N/A                              | **78.4** |   84.7   | [Sentence Similarity Learning by Lexical Decomposition and Composition](https://www.aclweb.org/anthology/C16-1127/) |
|            MSEM (Wang et al.2016)             |                             N/A                              |  —   |  88.86   | [Multi-task Sentence Encoding Model for Semantic Retrieval in Question Answering Systems](https://arxiv.org/ftp/arxiv/papers/1911/1911.07405.pdf) |
|           BiMPM (Wang et al., 2017)           | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/zhiguowang/BiMPM) |  —   |  88.17   | [Bilateral Multi-Perspective Matching for Natural Language Sentences](https://arxiv.org/abs/1702.03814) |
| pt-DecAtt (Char) (Tomar et al., 2017) | N/A |  —  | 88.40  | [Neural Paraphrase Identification of Questions with Noisy Pretraining](https://arxiv.org/abs/1704.04565) |
|           DIIN (Gong et al., 2018)            | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/YichenGong/Densely-Interactive-Inference-Network) |  —   |  89.06   | [Natural Language Inference over Interaction Space](https://arxiv.org/pdf/1709.04348.pdf) |
| GenSen (Subramanian et al., 2018) | N/A | —  | 87.01	  | [Learning General Purpose Distributed Sentence Representations via Large Scale Multi-task Learning](https://arxiv.org/abs/1804.00079)|
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/HazyResearch/metal) | 73.1 |   89.9   | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) |
|            MwAN (Tan et al., 2018)            |                             N/A                              |  —   |  89.12   | [Multiway Attention Networks for Modeling Sentence Pairs](https://www.ijcai.org/proceedings/2018/0613.pdf) |
|            RE2 (Yang et al., 2019)            | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/alibaba-edu/simple-effective-text-matching) |  —   |   89.2   | [Simple and Effective Text Matching with Richer Alignment Features](https://www.aclweb.org/anthology/P19-1465.pdf) |
| Bi-CAS-LSTM (Choi et al.2019) | N/A | — |   88.6  | [Cell-aware Stacked LSTMs for Modeling Sentences](https://arxiv.org/pdf/1809.02279.pdf)|
|      MT-DNN-ensemble (Liu et al., 2019)       | [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/namisan/mt-dnn/) | 73.7 |   89.9   | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) |
|XLNet-Large (ensemble) (Yang et al., 2019)| [![official](https://img.shields.io/badge/official-code-brightgreen)](https://github.com/zihangdai/xlnet/) | 74.2 | **90.3** | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) |
