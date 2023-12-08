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

<table class="infotable">
  <thead>
    <tr>
      <th align="center"><strong>Tasks</strong></th>
      <th align="center"><strong>Source Text</strong></th>
      <th align="center"><strong>Target Text</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><a href="/resources/ad-hoc-information-retrieval/">Ad-hoc Information Retrieval</a></td>
      <td align="center">query</td>
      <td align="center">document (title/content)</td>
    </tr>
    <tr>
      <td align="center"><a href="/resources/community-question-answering/">Community Question Answering</a></td>
      <td align="center">question</td>
      <td align="center">question/answer</td>
    </tr>
    <tr>
      <td align="center"><a href="/resources/paraphrase-identification/">Paraphrase Identification</a></td>
      <td align="center">string1</td>
      <td align="center">string2</td>
    </tr>
    <tr>
      <td align="center"><a href="/resources/natural-language-inference/">Natural Language Inference</a></td>
      <td align="center">premise</td>
      <td align="center">hypothesis</td>
    </tr>
    <tr>
      <td align="center"><a href="/resources/response-retrieval/">Response Retrieval</a></td>
      <td align="center">context/utterances</td>
      <td align="center">response</td>
    </tr>
	<tr>
      <td align="center"><a href="/resources/LFQA/">Long Form Question Answering</a></td>
      <td align="center">question&document</td>
      <td align="center">answer</td>
    </tr>
  </tbody>
</table>

<style scoped>
  .infotable {
      max-width: 90%;
      margin-left: auto;
      margin-right: auto;
    }
  .infotable th {
    text-align: center;
  }
</style>