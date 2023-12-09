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

|Dataset | #QA pairs | Avg#docs/question | Avg#Words/question |Avg#Words/answer|Quoted|
|---- | ---- | ---- |---- | ---- | ---- |
|[**ELI5**](#eli5dataset)| 272K|-|857.6|130.6|No|
|[**WikiHowNFQA**](#wikihowdataset)| 11746|-|-|113.05|No|


- **[ELI5](https://github.com/facebookresearch/ELI5):** The dataset is released by Meta, where the original paper is in [link](https://arxiv.org/pdf/1907.09190.pdf). It is the first large-scale corpus for long-form question answering, a task requiring elaborate and in-depth answers to openended questions. The dataset comprises 270K threads from the Reddit forum “Explain Like I’m Five” (ELI5) where an online community provides answers to questions which are comprehensible by five year olds. Compared to existing datasets, ELI5 comprises diverse questions requiring multi-sentence answers. Sample:
```
[Question]:How do Jellyﬁsh function without brains or nervous systems? [...] (60 words)
[Documents]: [...] Jellyﬁsh do not have brains, and most barely have nervous systems. They have primitive nerve cells that help them orient themselves in the water and sense light and touch. [...] While they dont possess brains, the animals still have neurons that send all sorts of signals throughout their body. [...] They may accomplish this through the assistance of their nerve rings. Jellyﬁsh don’t have brains, and that’s just where things begin. They don’t have many of the body parts that are typical in other animals. [...] (1070 words)
[Answer]: Jellyﬁsh may not have a brain, but they have a rough nervous system and innate behaviours. However, they are very simple creatures. They’re invertebrate: creatures without a backbone. Most jellyﬁsh have really short life spans. Sometimes just a couple of hours. [...] As their name im-plies, they are largely composed of basically jelly inside a thin membrane. They’re over 95% water. (327 words)
```

- **[WikiHowNFQA](https://lurunchik.github.io/WikiHowNFQA/#home):** The WikiHowNFQA dataset is derived from WikiHow, a popular online platform that provides how-to guides on a wide range of topics. The dataset is structured to include a question, a set of related documents, and a human-authored answer. The questions are non-factoid, requiring comprehensive, multi-sentence answers. The related documents provide the necessary information to generate an answer. Sample:
```
[Question]: How To Seal Concrete Floors?
[Documents]: 
	[1] Title: "Make Your Garage Floor Last — The Family Handyman"; URL: "https://www.familyhandyman.com/garage/make-your-garage-floor-last-with-concrete-sealer/view-all"; PASSAGE: "Sealing your concrete garage floor is the best way to prevent damage from road salt and freezing temperatures. With so many concrete sealing/waterproofing products on the market, choosing the right product can be confusing."
	[2] Title: "Clean Garage Floors – Remove Oil Stains From Concrete"; URL: "https://www.familyhandyman.com/garage/clean-garage-floors-remove-oil-stains-from-concrete/view-all/"; PASSAGE: "Oil and grease stains don’t just make a garage floor look bad- they can also cause falls, ruin your shoes and get tracked into the house. And if you want to finish your floor with a coating, it’s essential to get rid of oil deposits for a good bond. Solvent-based remedies are harmful to the environment and can damage the concrete surface. Cat litter, sawdust and other absorbent materials remove standing oil but do nothing about the oily stain left behind. Commercial and household detergents require a lot of scrubbing and can leave behind residue or discolor the concrete. Here are two product that actually work."    
	...                
[Answer]:  To seal concrete floors, use an epoxy sealer if you want something durable that comes in a variety of colors. For indoor concrete floors that won't be exposed to oil or grease, use an acrylic sealer, which is easy to apply. If you want to seal over concrete floors that already have a seal, try a polyurethane sealer. To seal concrete floors without changing their appearance, you can use a silane or siloxane sealer, which won't alter the color or finish of the floors.
```


## Performance

### [ELI5 dataset](https://github.com/facebookresearch/ELI5) <a name="eli5dataset"></a>



| Model   | Code|PPL|ROUGE-1|ROUGE-2|ROUGE-L|Paper| type |
|  ----  | ----  |  ----  | --- | --- | --- | --- | ----  | ----  |
| Seq2Seq Multi-task (Fan et al. 2019)| N/A | 32.7 | 28.9 | 5.4 | 23.1 |  [ELI5: Long Form Question Answering](https://arxiv.org/pdf/1907.09190.pdf) | abstractive |



### [WikiHowNFQA dataset](https://lurunchik.github.io/WikiHowNFQA/#home) <a name="wikihowdataset"></a>

| Model   | Code|BertScore|ROUGE-1|ROUGE-2|ROUGE-L|Paper| type |
|  ----  | ----  |  ----  | --- | --- | --- | --- | ----  | ----  |
| DPR + text-davinci-003 (Bolotova et al. 2023)| N/A | 0.868 | 35.4 | 9.2 | 20.2 |  [WikiHowQA: A Comprehensive Benchmark for Multi-Document Non-Factoid Question Answering](https://arxiv.org/pdf/1907.09190.pdf) | generative |





