---
title: "Challenges and frontiers in abusive content detect"
tags:
- Hate-speech-detection
- generalization 
---

이번에 정리하는 논문은 "abusive content detect" 과제가 어떻게 발전했고, 지금 마주하고 있는 어려움은 무엇인지 소개하는 논문이다. 혐오표현 탐지 과제와 (완전히는 아니지만) 비슷한 과제이기에 비슷한 어려움들을 공유하고 있다. 주석 작업의 어려움, 개념 정의의 정확성 등...
개인적으로 인상 깊었던 것은 '훈련 데이터와 다른 도메인에서 테스트가 이루어지면 성능이 어떻게 변할지'를 소개하는 파트였다. 

***

> Developing robust systems to detect abuse is a crucial part of online content moderation and plays a fundamental role in creating an open, safe and accessible Internet.

: 욕설(abuse)을 탐지하기 위한 강력한 시스템을 개발하는 것은 온라인 콘텐츠 조정의 중요한 부분이며 **개방적이고 안전하며 접근 가능한 인터넷을 만드는 데 근본적인 역할을 한다**.


> Advances in machine learning and NLP have led to marked improvements in abusive content detection systems’ performance (Fortuna & Nunes, 2018; Schmidt & Wiegand, 2017). For instance, in 2018 Pitsilis et al. trained a classification system on Waseem and Hovy’s 16,000 tweet dataset and achieved an F-Score of 0.932, compared against Waseem and Hovy’s original 0.739; a 20-point increase (Pitsilis, Ramampiaro, & Langseth, 2018; Waseem & Hovy, 2016).

: **머신 러닝과 NLP의 발전은 모욕 콘텐츠 감지 시스템의 성능을 현저하게 향상시켰다(Fortuna & Nunes, 2018; Schmidt & Wiegand, 2017).** 예를 들어, 2018년 Pitsilis 등은 Wasem과 Hovy의 16,000개의 트윗 데이터 세트에 대한 분류 시스템을 훈련하고 Wasem과 Hovy의 원래 0.739와 비교하여 0.932의 F-Score를 달성했다Pitsilis, Ramampiaro, & Langseth, 2018; Wasem & Hovy, 2016).


> Researchers have also addressed numerous tasks beyond binary abusive content classification, including identifying the target of abuse and its strength as well as automatically moderating content (Burnap & Williams, 2016; Davidson, Warmsley, Macy, & Weber, 2017; Santos, Melnyk, & Padhi, 2018).

: 연구자들은 또한 학대 대상을 식별하는 것뿐만 아니라 콘텐츠 자동 조절을 포함하여 이진 욕설 콘텐츠 분류를 넘어 수많은 과제를 해결했다(Burnap & Williams, 2016; Davidson, Warmsley, Macy, Weber, 2017; Santos, Melnyk, & Padhi, 2018). 


> (…) what type of abusive content it is identified as. This is a social and theoretical task: **there is no objectively ‘correct’ definition** or single set of pre-established criteria which can be applied.

: (...) 어떤 유형의 욕설 콘텐츠로 식별되는지도 중요하다. 이러한 분류는 사회적이고 이론적인 과제이기에, **객관적으로 '올바른' 정의나 적용할 수 있는 사전 설정된 기준의 단일 집합은 없다.**


> Detecting abusive content generically is an important aspiration for the field. However, it is very difficult because abusive content is so varied. Research which purports to address the generic task of detecting abuse is typically actually addressing something much more specific. This can often be discerned from the datasets, which may contain systematic biases towards certain types and targets of abuse. For instance, the dataset by Davidson et al. is used widely for tasks described generically as abusive content detection yet it is highly skewed towards racism and sexism (Davidson et al., 2017).

: 욕설 콘텐츠를 전반적으로 감지하는 것은 현장의 중요한 포부다. 하지만 이는 욕설의 내용이 다양하기 때문에 매우 어렵다. **남용을 탐지하는 일반적인 과제를 해결한다고 주장하는 연구는 일반적으로 훨씬 더 구체적인 것(specific)을 다루고 있다.** 이것은 종종 데이터 세트에서 식별될 수 있으며, 이는 특정 유형 및 욕설 대상에 대한 체계적인 편견을 포함할 수 있다. **예를 들어, Davidson 등의 데이터 세트는 일반적으로 욕설 콘텐츠 탐지로 설명되는 작업에 널리 사용되지만 인종차별과 성차별 쪽으로 크게 치우쳐 있다(Davidson 등, 2017).** 


> Waseem et al. suggest that one of the main differences between subtasks is whether content is ‘directed towards a specific entity or is directed towards a generalized group’ (Waseem et al., 2017).

: Waseem et al.은 하위 작업 간의 주요 차이점 중 하나는 콘텐츠가 '특정 엔티티를 지향하는지, 아니면 일반화된 그룹을 지향하는지'라고 제안한다(Wasee et al., 2017).


> A key distinction is whether abuse is explicit or implicit (Waseem et al., 2017; Zampieri et al., 2019).


> Some of the main problems are (1) researchers use terms which are not well-defined, (2) different concepts and terms are used across the field for similar work, and (3) the terms which are used are theoretically problematic.

: 주요 문제 중 일부는 (1) 연구자들이 잘 정의되지 않은 용어를 사용하고, (2) 유사한 작업에 대해 현장 전반에 걸쳐 다른 개념과 용어를 사용하며, (3) 사용되는 용어가 이론적으로 문제가 있다는 것이다.


> **Annotation.** 
> Annotation is a notoriously difficult task, reflected in the low levels of inter-annotator agreement reported by most publications, particularly on more complex multi-class tasks (Sanguinetti, Poletto, Bosco, Patti, & Stranisci, 2018). Noticeably, van Aken suggests that Davidson et al.’s widely used hate and offensive language dataset has up to 10% of its data mislabeled (van Aken et al., 2018).

: 주석은 악명높게 어려운 작업으로, 특히 더 복잡한 다중 클래스 작업에 대해 대부분의 연구들에서 보고한 주석 간 합의(inter-annotator agreement)의 낮은 수준에 반영된다(Sanguinetti, Poletto, Bosco, Patti, & Stranisci, 2018). 독특하게,  **반 에이켄은 데이비드슨 등의 널리 사용되는 혐오 및 공격적인 언어 데이터 세트가 최대 10%의 데이터 레이블이 잘못 지정되었음을 시사한다(반 에이켄 외, 2018).**


> Few publications provide details of their annotation process or annotation guidelines. Providing such information is the norm in social scientific research and is viewed as an integral part of verifying others’ findings and robustness (Bucy & Holbert, 2013). In line with the recommendations of Sabou et al., we advocate that annotation guidelines and processes are shared where possible (Sabou, Bontcheva, Derczynski, & Scharl, 2014) and that the field also works to develop best practices.

: 주석 프로세스 또는 주석 지침에 대한 자세한 내용을 제공하는 연구들은 거의 없다. **이러한 정보를 제공하는 것은 사회과학 연구의 표준이며**, 타인의 발견과 견고성을 검증하는 데 필수적인 부분으로 간주된다(Bucy & Holbert, 2013). **Sabou 등의 권고에 따라, 우리는 주석 지침과 프로세스가 가능한 곳에서 공유되고(Sabou, Bontcheva, Derczynski, & Scharl, 2014) 이 분야도 모범 사례를 개발하기 위해 노력해야 한다고 주장한다.**


> Ensuring that abusive content detection systems can be applied across different domains is one of the most difficult but also important frontiers in existing research. Thus far, efforts to address this has been unsuccessful. Burnap and Williams train systems on one type of hate speech (e.g. racism) and apply them to another (e.g. sexism) and find that performance drops considerably (Burnap & Williams, 2016)

: 욕설 콘텐츠 탐지 시스템이 서로 다른 영역에 걸쳐 적용될 수 있도록 보장하는 것은 기존 연구에서 가장 어렵지만 중요한 분야 중 하나이다. 지금까지, 이것을 해결하려는 노력은 성공하지 못했다. **Burnap과 Williams는 한 유형의 혐오 발언(예: 인종차별)에 대해 시스템을 훈련시키고 다른 유형의 혐오 발언(예: 성차별)에 적용하며 성능이 상당히 떨어진다는 것을 발견한다(Burnap & Williams, 2016).**


> Karan and Šnajder use a simple methodology to show the huge differences in performance when applying classifiers on different datasets without domain-specific tuning (Karan & Šnajder, 2018). Noticeably, in the EVALITA hate speech detection shared task, participants were asked to (1) train and test a system on Twitter data, (2) on Facebook data and (3) to train on Twitter and test on Facebook (and vice versa). **Even the best performing teams reported their systems scored around 10 to 15 F1 points fewer on the cross-domain task.**

: Karan과 Shnajder는 도메인별 튜닝 없이 서로 다른 데이터 세트에 분류기를 적용할 때 성능에서 큰 차이를 보여주기 위해 간단한 방법론을 사용한다(Karan & Shnajder, 2018). 눈에 띄게, EVALITA 혐오 발언 탐지 공유 작업에서, **참가자들에게 (1) 트위터 데이터에 대한 시스템 훈련 및 테스트, (2) 페이스북 데이터에 대한 시스템 훈련 및 테스트, (3) 트위터에 대한 훈련 및 페이스북에서 테스트(및 그 반대)를 요청하였다.** 최고의 성과를 거둔 팀들조차 그들의 시스템이 교차 도메인 작업에서 약 10-15의 F1 점수를 더 적게 받았다고 보고했다.

***

> [!info] Reference
> Bertie Vidgen, Alex Harris, Dong Nguyen, Rebekah Tromble, Scott Hale, and Helen Margetts. 2019. [Challenges and frontiers in abusive content detection](https://aclanthology.org/W19-3509). In _Proceedings of the Third Workshop on Abusive Language Online_, pages 80–93, Florence, Italy. Association for Computational Linguistics.

