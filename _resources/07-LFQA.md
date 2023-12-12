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
|[**WebCPM**](#webcpmdataset)| 5500|2.795|-|-|Yes|
|[**WebGLM**](#webglmdataset)| 44979 |-|-|-|Yes|
|[**WebGPT**](#webgptdataset)| 272|-|-|-|Yes|
|[**HAGRID**](#hagriddataset)| 4532|-|-|-|Yes|
|[**Natural Questions**](#naturalquestions)| 307,373 |-|-|-|No|

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

- **[WebCPM](https://github.com/thunlp/WebCPM):** The dataset is released by Tsinghua, where the original paper is in [link](http://arxiv.org/abs/2305.06849). It is the first public QA dataset that involves interactive web search, and also the first dataset that targets Chinese LFQA. WebCPM contains 5,500 question-answer pairs, together with 15,372 supporting facts and 125,954 web search actions. Sample:
```
[Question]:是什么决定了彩虹的拱门大小或“周长”？
[Actions]:
	RECORD_START：(result)
	PRESS_SEARCH: (result)
	...
[Documents]: 
	[1] 但一般来说形成彩虹的都是水，折射率的大小差可以忽略不计。当折射率相同时，彩虹的大小一定相同。但为什么平时我们会觉得彩虹有大小呢？\n普通彩虹总是围绕着对日点（antisolar point），当然像反射虹（reflection bow）、三、四次虹这类特殊的，就不考虑了。\n可以理解为，彩虹好像围绕对日点，以40°-42°为半径画圆，这就是彩虹。但绝大多数情况下，会有一部分彩虹出现在地平线以下，导致其部分不可见。\n做个实验：随便画一个圆，然后用一块纸板，从它的下方渐渐水平向上平移，你会发现你画的圆的可见部分越来越少了。\n对日点的位置由太阳在天球上的位置决定。太阳高度角越大，对日点的位置越低，地平线相对彩虹越高，因此彩虹看起来就越“小”；反之亦然。
	[2] 彩虹是因为阳光射到空中接近圆型的小水滴，造成色散及反射而成的。所以它的实际半径取决于空气里水滴的分布面积和大小，空气里水滴的大小决定了虹的色彩鲜艳程度和宽窄。空气中的水滴大，虹就鲜艳。也比较窄；反之，水滴小，虹色就淡，也比较宽。这和你到彩虹的距离没关系,例如你在远处看个汽车很小,但汽车本身其实还是那么大!彩虹的形成和云的密度，浓度，温度基本没什么关系!其实只要有空气中有水滴，而阳光正在观察者的背后以低角度照射，便可能产生可以观察到的彩虹现象。彩虹最常在下午，雨后刚转天晴时出现。这时空气内尘埃少而充满小水滴，天空的一边因为仍有雨云而较暗。而观察者头上或背后已没有云的遮挡而可见阳光，这样彩虹便会较容易被看到。另一个经常可见到彩虹的地方是瀑布附近。在晴朗的天气下背对阳光在空中洒水或喷洒水雾，亦可以人工制造彩虹。\n
	...    
[Answer]: 彩虹是由阳光射到空中接近圆型的小水滴，造成色散及反射而成的，所以其实际大小取决于空气里水滴的分布面积和大小。空气中的水滴大，彩虹就比较窄；反之，水滴小，彩虹就比较宽。【2】当折射率相同时，彩虹的大小一定相同。但大多数情况下，会有一部分彩虹出现在地平线以下，导致其部分不可见。同时，太阳高度角越大，对日点的位置越低，地平线相对彩虹越高，因此彩虹看起来就越“小”；反之亦然。【1】
```

- **[WebGLM](https://github.com/THUDM/WebGLM):** The dataset is released by Tsinghua, where the original paper is in [link](http://arxiv.org/abs/2306.07906). It is the dataset used to train the WebGLM generator module. It consists of 43,579 high-quality data samples for the train split, 1,000 for the validation split, and 400 for the test split. Sample:
```
[Question]: Why is driving into mild to heavy snowfall at night so disorienting?
[Documents]: 
	[1] Driving in snow at night is dangerous because the snow makes it very difficult to see. Your headlights will reflect off of the snowflakes in the air as well as obstruct your view. This means that the harder it’s snowing, the more dangerous it is to drive.
	[2] I'm not sure \"spatial disorientation\" is how I'd put it, but I remember one time when I was driving at night on the Taconic State Parkway at night, and the rain started coming down so hard that I simply couldn't see where I was going. I slowed down, put on the flashers, and found a safe place to pull over and wait it out. It really was that bad.
	[3] I'm not sure \"spatial disorientation\" is how I'd put it, but I remember one time when I was driving at night on the Taconic State Parkway, and the rain started coming down so hard that I simply couldn't see where I was going. I slowed down, put on the flashers, and found a safe place to pull over and wait it out. It really was that bad.
	[4] Why not???? I have been somewhat disoriented in heavy snow at night flashing by in the headlights. (I have been spatially disoriented in establishments that serve adult beverages too.)
	[5] Same thing has happened to me at night occasionally with moderately heavy snow storms that suddenly just start. For some reason, now that I think about it, it tends to happen to me more when there is no snow on the ground--its probably the darker background of a snowless roadway that is helping with the disorientation (blends into the dark sky) and then you have the rapid big flakes coming down in your headlights.
[Answer]: Driving into mild to heavy snowfall at night can be disorienting because the snow can make it difficult to see and the headlights can reflect off of the snowflakes in the air, obstructing the view[1]. Additionally, snow falling heavily can be so disorienting that it can make it hard to determine where you are going. The darkness of a snowless roadway can also contribute to the disorientation, as it can blend into the dark sky and create a sudden contrast when the snow begins to fall[5].
```

- **[WebGPT](https://openaipublic.blob.core.windows.net/webgpt-answer-viewer/index.html):** The dataset is non-cherry-picked samples for the paper [WebGPT: Browser-assisted question-answering with human feedback](https://cdn.openai.com/WebGPT.pdf)([blog post](https://openai.com/research/webgpt)). The questions are from the ELI5 test set, and the answers are those used in the evaluations against human demonstrations in the paper.Sample:
```
[Question]: Why did we decide that certain words were "bad" and shouldn't be used in social settings?
[Documents]: 
	[1] "Words in general that are considered bad tend to relate to parts of our lives that we don't like talking about in public, like bathroom functions," Benjamin Bergen says. Other words that are often considered bad relate to negative ways of talking about people and their religion, skin color, ability, gender etc. Those words are called slurs. And many people consider those the worst kind of bad words.
	[2] Some words are considered “bad” because they offend others. They are words that refer to impolite things, like body parts or bodily functions and most people don’t like to hear about it. Some people believe there are no “bad” words, just inappropriate times and places to say certain words.
	...
[Answer]: In general, words that are considered "bad" relate to parts of life that people don't like talking about in public, like bathroom functions.[1] Other words considered bad relate to negative ways of talking about people and their religion, skin color, ability, gender, etc.[1] These words are called slurs and many people consider them the worst kind of bad words.[1]
Some words are considered "bad" because they offend others.[2] They are words that refer to impolite things, like body parts or bodily functions and most people don't like to hear about it.[2] Some people believe there are no "bad" words, just inappropriate times and places to say certain words.[2]
```

- **[HAGRID](https://github.com/project-miracl/hagrid):** The dataset is released by Waterloo, where the original paper is in [link](http://arxiv.org/abs/2307.16883). It is a dataset for generative information-seeking scenarios. It is constructed on top of MIRACL, an information retrieval dataset that consists of queries along with a set of manually labelled relevant passages (quotes). Sample:
```
[Question]: When is a language considered dead?
[Documents]: 
	[1] A language is often declared to be dead even before the last native speaker of the language has died. If there are only a few elderly speakers of a language remaining, and they no longer use that language for communication, then the language is effectively dead. A language that has reached such a reduced stage of use is generally considered moribund. Half of the spoken languages of the world are not being taught to new generations of children. Once a language is no longer a native language\u2014that is, if no children are being socialized into it as their primary language\u2014the process of transmission is ended and the language itself will not survive past the current generations.
	[2] An endangered language, or moribund language, is a language that is at risk of falling out of use as its speakers die out or shift to speaking another language. Language loss occurs when the language has no more native speakers and becomes a \"dead language\". If no one can speak the language at all, it becomes an \"extinct language\". A dead language may still be studied through recordings or writings, but it is still dead or extinct unless there are fluent speakers. Although languages have always become extinct throughout human history, they are currently dying at an accelerated rate because of globalization, neocolonialism and linguicide (language killing).
	...
[Answer]: This can happen when the language has no more speakers at all, or only a few elderly speakers who no longer use the language for communication [1]. If no one can speak the language, it becomes an \"extinct language\" [2]. Although a dead language may still be studied through recordings or writings, it is still dead or extinct unless there are fluent speakers [2]. It is important to note that linguists distinguish between language \"death\" and the process where a language becomes a \"dead language\" through normal language change, leaving the old form with no native speakers [3].
```

- [**Natural Questions**](https://ai.google.com/research/NaturalQuestions)**: ** The Natural Questions corpus is a question answering dataset containing 307,373 training examples, 7,830 development examples, and 7,842 test examples. Each example is comprised of a google.com query and a corresponding Wikipedia page. Each Wikipedia page has a passage (or long answer) annotated on the page that answers the question and one or more short spans from the annotated passage containing the actual answer. The long and the short answer annotations can however be empty. If they are both empty, then there is no answer on the page at all. If the long answer annotation is non-empty, but the short answer annotation is empty, then the annotated passage answers the question but no explicit short answer could be found. Finally 1% of the documents have a passage annotated with a short answer that is “yes” or “no”, instead of a list of short spans. Sample:

```
[document_text]:[...]and is meant to build loyalty , trust , or brand awareness . Marketing emails can be sent to a purchased lead list or a current customer database . The term usually refers to sending email messages with the purpose of enhancing a merchant 's relationship with current or previous customers , encouraging customer loyalty and repeat business ,[...]
[long_answer_candidates]:[...]{"start_token": 1952, "top_level": true, "end_token": 2019}[...]
[question_text]:which is the most common use of opt-in e-mail marketing
[annotations]:
	[yes_no_answer]:NONE
	[long_answer]:{"start_token": 1952, "candidate_index": 54, "end_token": 2019}
	[short_answers]:[{"start_token": 1960, "end_token": 1969}]
	[annotation_id]:593165450220027640
[document_url]:https://en.wikipedia.org//w/index.php?title=Email_marketing&amp;oldid=814071202
[example_id]:5655493461695504401
```



## Performance

### [ELI5 dataset](https://github.com/facebookresearch/ELI5) <a name="eli5dataset"></a>

| Model   | Code|PPL|ROUGE-1|ROUGE-2|ROUGE-L|Paper| type |
|  ----  | ----  | --- | --- | --- | --- | ----  | ----  |
| Seq2Seq Multi-task (Fan et al. 2019)| N/A | 32.7 | 28.9 | 5.4 | 23.1 |  [ELI5: Long Form Question Answering](https://arxiv.org/pdf/1907.09190.pdf) | abstractive |



### [WikiHowNFQA dataset](https://lurunchik.github.io/WikiHowNFQA/#home) <a name="wikihowdataset"></a>

| Model   | Code|BertScore|ROUGE-1|ROUGE-2|ROUGE-L|Paper| type |
|  ----  | ----  | --- | --- | --- | --- | ----  | ----  |
| DPR + text-davinci-003 (Bolotova et al. 2023)| N/A | 0.868 | 35.4 | 9.2 | 20.2 |  [WikiHowQA: A Comprehensive Benchmark for Multi-Document Non-Factoid Question Answering](https://arxiv.org/pdf/1907.09190.pdf) | generative |


### [WebCPM dataset](https://github.com/thunlp/WebCPM) <a name="webcpmdataset"></a>

|Model|Code|Action Micro-F1|Action Macro-F1|Query Generation Rouge-L|Fact Extraction Rouge-L|Information Synthesis Rouge-L|Paper| type |
|  ----  | ----  |  ----  | --- | --- | --- | --- | ----  | ----  |
| mT5 BASE| N/A | 53.8 | 44.0 | 62.4 | 56.7 | 56.8 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| mT0 BASE| N/A | 58.2 | 52.1 | 64.6 | 60.0 | 51.4 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| Mengzi-T5 BASE| N/A | 58.1 | 51.2 | 62.6 | 61.9 | 57.7 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| mBART LARGE| N/A | 53.6 | 41.1 | 50.4 | 56.5 | 60.2 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| C-BART LARGE| N/A | 43.8 | 31.3 | 56.1 | 49.3 | 50.6 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| CPM 2.6B| N/A | 55.6 | 49.8 | 61.6 | 52.6 | 55.0 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| CPM 7B| N/A | 58.9 | 50.5 | 67.8 | 59.8 | 56.4 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |
| CPM 10B| N/A | 60.4 | 54.5 | 70.0 | 62.4 | 61.2 |  [WebCPM: Interactive Web Search for Chinese Long-form Question Answering](http://arxiv.org/abs/2305.06849) | generative |

### [WebGPT dataset](https://openaipublic.blob.core.windows.net/webgpt-answer-viewer/index.html) <a name="webgptdataset"></a>
human evaluation

|Model|Code|Relevancy|Density|Truthfulness|Toxicity|Social Bias|Fluency|Correctness|Citation Accuracy|Objectivity|Truthfulness|Redundancy|Paper| type |
| ---- | ---- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---- | ---- |
|WebGPT 175B | N/A | 2.512 | 2.660 | 0.996 | 0.015 | 0.006 | 2.457 | 2.889 | 2.837 | 0.990 | 0.975 | 0.087 |[WebGLM: Towards An Efficient Web-Enhanced Question Answering System with Human Preferences](http://arxiv.org/abs/2306.07906) | generative |
|Perplexity.ai | N/A | 1.652 | 1.636 | 0.955 | 0.005 | 0.001 | 2.718 | 2.321 | 2.512 | 0.726 | 0.975 | 0.032 |[WebGLM: Towards An Efficient Web-Enhanced Question Answering System with Human Preferences](http://arxiv.org/abs/2306.07906) | generative |
|WebGPT 13B | N/A | 1.782 | 1.766 | 0.998 | 0.008 | 0.016 | 2.692 | 2.102 | 2.769 | 0.974 | 0.872 | 0.051 |[WebGLM: Towards An Efficient Web-Enhanced Question Answering System with Human Preferences](http://arxiv.org/abs/2306.07906) | generative |
|WebGLM 10B | N/A | 1.980 | 2.226 | 0.983 | 0.002 | 0.002 | 2.829 | 2.810 | 2.757 | 0.943 | 0.998 | 0.021 |[WebGLM: Towards An Efficient Web-Enhanced Question Answering System with Human Preferences](http://arxiv.org/abs/2306.07906) | generative |

### [Natural Questions dataset](https://ai.google.com/research/NaturalQuestions) <a name="naturalquestions"></a>

#### QA task 

| Model   | Code|EM|Paper| type |
|  ----  | ----  |  ----  | ----  | ----  |
| Atlas(full, Wiki-dec-2018 index)(Gautier et al. 2022) | [github](https://paperswithcode.com/paper/few-shot-learning-with-retrieval-augmented#code) | 64.0 | [Atlas: Few-shot Learning with Retrieval Augmented Language Models](https://arxiv.org/pdf/2208.03299v3.pdf) | generative |
| Atlas (full, Wiki-dec-2021+CC index)(Gautier et al. 2022) | [github](https://paperswithcode.com/paper/few-shot-learning-with-retrieval-augmented#code) | 60.4 | [Atlas: Few-shot Learning with Retrieval Augmented Language Models](https://arxiv.org/pdf/2208.03299v3.pdf) | generative |
| FiE(Akhil et al. 2022) | N/A | 58.4 | [ FiE: Building a Global Probability Space by Leveraging Early Fusion in Encoder for Open-Domain Question Answering](https://arxiv.org/pdf/2211.10147v1.pdf) | abstractive |

#### Long Answer

| Model                            | Code | F1      | Precision | Recall  | R@P = 90 | **R@P = 75** | R@P = 50 | Paper                                                        | type        |
| :------------------------------- | ---- | :------ | :-------- | :-----: | :------: | :----------: | :------: | ------------------------------------------------------------ | ----------- |
| PoolingFormer(Zhang et al. 2021) | N/A  | 0.79823 | 0.7847    | 0.81224 | 0.62448  |    0.8379    | 0.88748  | [Poolingformer: Long Document Modeling with Pooling Attention](https://arxiv.org/pdf/2105.04371v2.pdf) | abstractive |
| lsg-bert                         |      | 0.79816 | 0.79659   | 0.79974 | 0.59509  |    0.8333    | 0.88484  |                                                              |             |
| D-FORMER-V3                      |      | 0.79323 | 0.79978   | 0.7868  | 0.59772  |   0.81926    | 0.87168  |                                                              |             |

#### Short Answer

| Model                                    | Code | F1      | Precision | Recall  | R@P = 90 | **R@P = 75** | R@P = 50 | Paper                                                        | type        |
| :--------------------------------------- | ---- | :------ | :-------- | :-----: | :------: | :----------: | :------: | ------------------------------------------------------------ | ----------- |
| ReflectionNet-ensemble(Wang et al. 2020) | N/A  | 0.64114 | 0.70445   | 0.58827 | 0.35046  |   0.54355    | 0.66144  | [No Answer is Better Than Wrong Answer: A Reflection Model for Document Level Machine Reading Comprehension](https://arxiv.org/pdf/2009.12056v2.pdf) | abstractive |
| PoolingFormer(Zhang et al. 2021)         | N/A  | 0.61629 | 0.70369   | 0.5482  | 0.17567  |    0.509     | 0.63995  | [Poolingformer: Long Document Modeling with Pooling Attention](https://arxiv.org/pdf/2105.04371v2.pdf) | abstractive |
| RoBERTa-mnlp-ensemble                    |      | 0.61409 | 0.6961    | 0.54936 | 0.28223  |   0.50436    | 0.62747  |                                                              |             |