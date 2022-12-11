---
title: "Call for Customized Conversation-Customized Conversation Grounding Persona and Knowledge"
tags: 
- focus-dataset
- persona
- conversational-ai
---

## Abstarct
> Humans usually have conversations by making use of prior knowledge about a topic and background information of the people whom they are talking to. **However, existing conversational agents and datasets do not consider such comprehensive information, and thus they have a limitation in generating the utterances where the knowledge and persona are fused properly.** To address this issue, we introduce a call For Customized conversation **(FoCus) dataset** where the customized answers are built with the user’s persona and Wikipedia knowledge. (...)
- 현재 상황과 한계를 찾아보자. 
	- 사람은 대화의 주제나, 자기와 말하고 있는 사람의 배경 정보 등에 기대어 대화를 이어나간다. 그러나 현재 대화 시스템이나 데이터셋은 이러한 정보들을 이해하지 못하고 있으며, 따라서 지식이나 성격이 함께 적절히 융합된 발화를 생성하는 데에 한계가 있다. 
- 그래서 본 논문의 목적은?
	- 이에 본 논문은 이용자의 성격(persona)와 Wikipedia과 함께 구축된 FoCus 데이터셋을 발표했다.

> We examine whether the model reflects adequate persona and knowledge with our proposed two sub-tasks, **persona grounding (PG) and knowledge grounding (KG)**.
- 그래서 그걸로 뭘 한 건데?
	- 모델이 적절히 페르소나와 지식을 반영하는지 확인해볼 것이다. 
	- `Persona grounding (PG)` 와 `Knowledge grounding (KG)`라고 하는 서브 태스크를 통해서!

## FoCus Dataset

![Figure 2: Example dialog between Human and Machine in FoCus dataset](Example-dialog.png)
- 그래서 이런 대화가 가능하도록 하고 싶다는 것이다. 
- 이용자와 대화를 진행하는 시스템이 실제 지식에 기반하면서('This place is called Sentosa'), 또한 이용자의 페르소나에 근거하여 말을 이어나가는 것('I believe you wish to visit Singapore.')!

## Model

![](Overview-of-model.png)
> We introduce the baseline models trained on our FoCus dataset, consisting of a `retrieval module` and a `dialog module`. The `retrieval module` retrieves the knowledge paragraphs related to a question, and the `dialog module` generates utterances of the machine by taking the retrieved knowledge paragraphs, human’s persona, and previous utterances as inputs.
- 그래서 모델 아키텍쳐에는 두 개의 모듈이 들어간다. `retrieval module` 과 `dialog module` 이다. `retrieval module` 은 질문과 관련된 지식 파라그래프를 검색하고, `dialog module` 은 이것과 이용자의 페르소나 정보에 근거해서 모델의 발화를 생성해내는 것이다.

![Table 3: Experimental results](Experimental-results.png)
- 실험 결과, PG, KG에 모두 훈련된 BART와 GPT-2가 generation에서는 조금 성능이 낮지만 전반적으로 비슷한 성능을 보여주며, Grouding 서브 태스크에서는 가장 뛰어난 성능을 보여주었다. 

## Conclusion
> We hope that the researches aim to make dialog agents more attractive and knowledgeable with grounding abilities to be explored.
- 우리는 연구자들이 더 있을 실제적 능력들과 함께, 대화 에이전트를 더욱 매력적이고 지식을 풍부히 가지도록 만드는 것을 목적으로 하기를 희망한다. 
- 끝맺음은 훈훈하게 하는구나. 대화 시스템은 더욱 매력적이게 될 수 있다. **감정 뿐만 아니라 지식, 페르소나를 모두 고려한 대화 시스템은 어떤 모습이 될까?**