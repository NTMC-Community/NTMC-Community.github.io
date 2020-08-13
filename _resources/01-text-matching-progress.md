---
title: "Text Matching Progress"
permalink: /resources/text-matching-progress/
excerpt: "Text matching progress."
last_modified_at: 2020-08-12
redirect_from:
  - /theme-setup/
toc: true
---

Text matching is a core component in many natural language processing tasks, where many task can be viewed as a matching between two texts input.

$$f(s, t)=g(\psi(s), \phi(t), \eta(s, t))$$

Where $s$ and $t$ are source text input and target text input, respectively. The $\psi$ and $\phi$ are representation function for input $s$ and $t$, respectively. The $\eta$ is the interaction function, and $g$ is the aggregation function. More detailed explaination about this formula can be found on [A Deep Look into Neural Ranking Models for Information Retrieval](https://arxiv.org/abs/1903.06902). The representative matching tasks are as follows:

|                                          **Tasks**                                           | **Source Text** |     **Target Text**      |
| :------------------------------------------------------------------------------------------: | :-------------: | :----------------------: |
| [Ad-hoc Information Retrieval](/resources/ad-hoc-information-retrieval/) |      query      | document (title/content) |
| [Community Question Answering](/resources/community-question-answering/) |    question     |     question/answer      |
|     [Paraphrase Indentification](/resources/paraphrase-identification/)     |     string1     |         string2          |
|    [Natural Language Inference](/resources/natural-language-inference/)    |     premise     |        hypothesis        |
|                [Response Retrieval](/resources/response-retrieval/)                |    response     |         response         |

