---
title: "Overview"
permalink: /resources/overview/
excerpt: "Overview."
last_modified_at: 2020-08-11
redirect_from:
  - /theme-setup/
toc: true
---

<div align="center">
    <img width="300" src="/assets/images/awesome.svg" alt="Awesome">
    <br><br>
    <p><b>Awesome Neural Models for Semantic Match</b></p>
</div>
<br>
<p align="center">
    <sub>A collection of papers maintained by MatchZoo Team.</sub>
    <br>
    <sub>Checkout our open source toolkit <a href="https://github.com/NTMC-Community/MatchZoo-py">MatchZoo</a> for more information!</sub>
</p>
<br>

Text matching is a core component in many natural language processing tasks, where many task can be viewed as a matching between two texts input.

<div align="center">
    <img width="300" src="/assets/images/equation.svg" alt="equation">
</div>


Where **s** and **t** are source text input and target text input, respectively. The **psi** and **phi** are representation function for input **s** and **t**, respectively. The **f** is the interaction function, and **g** is the aggregation function. More detailed explaination about this formula can be found on [A Deep Look into Neural Ranking Models for Information Retrieval](https://arxiv.org/abs/1903.06902). The representative matching tasks are as follows:

|                                          **Tasks**                                           | **Source Text** |     **Target Text**      |
| :------------------------------------------------------------------------------------------: | :-------------: | :----------------------: |
| [Ad-hoc Information Retrieval](/resources/ad-hoc-information-retrieval/) |      query      | document (title/content) |
| [Community Question Answering](/resources/community-question-answering/) |    question     |     question/answer      |
|     [Paraphrase Indentification](/resources/paraphrase-identification/)     |     string1     |         string2          |
|    [Natural Language Inference](/resources/natural-language-inference/)    |     premise     |        hypothesis        |
|                [Response Retrieval](/resources/response-retrieval/)                |    response     |         response         |

