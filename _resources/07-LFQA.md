---
title: "Long Form Question Answering"
permalink: /resources/LFQA/
excerpt: "Generate a proper answer for a question."
last_modified_at: 2023-12-08
redirect_from:
  - /theme-setup/
toc: true
---

**LFQA**/(also known as Non-factoid question answering) involves providing long answers to open-ended questions. It is a fundamental challenge in natural language processing (NLP) that involves retrieving documents relevant to a given question and using them to generate an elaborate paragraph-length answer. While there has been remarkable recent progress in factoid open-domain question answering (QA), where a short phrase or entity is enough to answer a question, much less work has been done in the area of long-form question answering. LFQA is nevertheless an important task, especially because it provides a testbed to measure the factuality of generative text models.

Example:
```
[Question]: Why are the things that taste the best bad for us？

[Relevant Passages]: 
	[1] So why do healthy things often taste bad? The main reason is that our taste buds are not used to them. Our taste buds are used to sweet, salty, and savory flavors, so many healthy foods taste bitter or sour to us.
	[2] There are a few reasons why healthy food might taste bad. Firstly, our taste buds adapt to what we eat, so if we eat a lot of unhealthy foods, our taste buds will start to prefer those flavours over healthier options. Additionally, unhealthy foods are often packed with sugar, salt and unhealthy fats, which can make them taste much more appealing than healthy foods.
	[3] So why does healthy food taste so nasty? I mean, shouldn’t we be inclined to prefer the food that’s good for us and that will help us survive?
	[4] Another reason why healthy foods often taste bad is that we are not used to eating them. Our taste buds are used to eating processed foods, which are full of salt, sugar, and unhealthy fats. When we switch to a healthy diet, our taste buds have to adjust to the new flavors of fresh fruits and vegetables.
	[5] Healthy food sometimes tastes bad while harmful foods taste good because of evolutionary reasons (7). Ancient humans had an abundance of plants around them, so their body didn’t need to develop a mechanism which would spur them to eat more plants. What humans really did require, and what was then in short supply, is sodium. Why does salt make food taste better? Because it triggers serotonin. The same goes for fat and sugar that are great and dense sources of energy. With the modernization humans learned to make foods next-level salty, fatty, and sugary – the combination that sends our brains into a pleasure overdrive. Yet it is simply too much, and inflicts irreparable harm on our body.

[Answer]: There are several reasons why healthy food often tastes bad while unhealthy food tastes good. One is that our taste buds are used to sweet, salty, and savory flavors, so many healthy foods taste bitter or sour to us[1]. Another is that our taste buds adapt to what we eat, so if we eat a lot of unhealthy foods, our taste buds will start to prefer those flavors[2][4]. Additionally, unhealthy foods are often packed with sugar, salt and unhealthy fats, which can make them taste much more appealing than healthy foods[2][5]. Another reason is that we are not used to eating healthy food, so our taste buds have to adjust to the new flavors of fresh fruits and vegetables[1][4]. Lastly, it is also an evolutionary reason, as ancient humans had an abundance of plants around them, so their body didn’t need to develop a mechanism which would spur them to eat more plants[5]. The combination of salt, fat, and sugar triggers serotonin, which sends our brains into a pleasure overdrive, but it is simply too much and inflicts irreparable harm on our body[5].	

```


## Classic Datasets

|Dataset | #Q-A pairs | Avg#docs/question | Avg#Words/question |Avg#Words/answer|Quoted|
|---- | ---- | ---- |---- | ---- | ---- |
|[**ELI5**](https://github.com/facebookresearch/ELI5)| 272K||857.6|130.6|No|


## Performance

### ELI5 dataset

| Model   | Code|MAP|$R_2@1$|$R_{10}@1$|$R_{10}@2$|$R_{10}@5$|Paper| type |
|  ----  | ----  |  ----  | --- | --- | --- | --- | ----  | ----  |
| Multi-View (Zhou et al. 2016)| N/A | — | 0.908 | 0.662 | 0.801 | 0.951 |  [Multi-view Response Selection for Human-Computer Conversation](https://www.aclweb.org/anthology/D16-1036.pdf) | multi-turn |





