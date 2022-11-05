---
title: "Discussion"
---

> [!note]   
> 여기서는 내 논문에 들어갈 논의를 정리하자. 

## 요약
- KcELECTRA 기반의 혐오표현 탐지 모델은 어느 데이터셋으로 학습하든 테스트 시에 높은 정확도와 F1 점수를 보여주었다(표나 그림). 그러나 훈련 데이터와 같은 연구진이 같은 구축 지침으로 만든 테스트 데이터셋으로는 도메인(트위터, 온라인 커뮤니티, 포털 사이트 뉴스 댓글 등)에 따라 사용 어휘가 조금씩 달라지고, 판단 기준을 빠져나가는 혐오표현들이 산적해 있는 실제 상황을 가정하기 어렵다. 따라서, 본 연구에서는 기구축되어 있는 한국어 혐오표현 데이터셋들을 이용해 서로 학습, 테스트하는 데이터셋 교차 검증을 시도하였다. 아울러 일반화가 잘 되는 데이터셋을 만드는 요인을 찾고자 각 데이터셋 별로 데이터셋 크기와 양성, 음성 샘플의 비율을 성능과 함께 비교하였다.  이번 연구가 발견한 내용과 그 함의는 다음과 같다.

## 발견
- 첫째, 데이터셋 교차 검증의 결과로, Beep 데이터셋에 학습한 모델이 가장 일반화가 잘 되었으며, Apeach, Unsmile 데이터셋에서는 기준이 되는 테스트 데이터셋 정확도와 F1 점수보다 성능이 증가한 것을 보고하였다. 
- 둘째, 더 나아가, 모델의 오분류의 경향을 살피기 위해 오분류된 케이스를 정량적 수치와 함께 예문을 들며 정성적으로도 살펴보았다. 
- 셋째, 일반화가 잘 되는 데이터셋을 만드는 요인으로는, Swamy, Jamatia & Gambäck (2019)의 결과와는 다르게 데이터셋의 크기는 일반화에 큰 영향을 주지 않는 것으로 나타났다. 하지만 Swamy, Jamatia & Gambäck (2019)에서의 결과와 부합하게, 양성 샘플의 비율이 큰 데이터셋은 일반화가 잘 되는 경향이 있었다.  
	- 즉, 더 균형적인 데이터셋이 일반화에 좋다. 이는 추후 데이터셋을 구축할 때 적용하면 좋다. 

## 한계가 여기에 들어가야 하나...?
> 이번 연구의 여러 발견과 함의와 더불어 이번 연구의 한계도 짚어볼 필요가 있다.첫째, 본 연구에서는 한정된 데이터셋의 수와 각 데이터셋이 가지고 있는 클래스를 고려하여, 'hate'와 'non-hate'으로 나뉘도록 라벨을 합치고 이 두개의 라벨만을 구별하는 이진 분류 모델을 훈련하고 평가했다. 그러나 데이터셋 전체를 비교하는 것이 아니라 데이터셋 전반에 걸쳐 개별 클래스 간의 차이를 비교하는 것도 일반화를 다루는 또 다른 방법이 된다(Nejadgholi & Kiritchenko, 2020; Fortuna, Soler & Wanner, 2020; Fortuna, Soler-Company & Wanner, 2021). Nejadgholi & Kiritchenko(2020)와 Fortuna, Soler & Wanner(2021)의 실험에서, 'toxicity', 'offensive', 'abusive'와 같은 더 일반적인 레이블에 대해 최고의 일반화가 달성되었다. 이에 후속 연구에서는 'hate'만이 아니라, 'offensive', 'bias' 등을 분류하는 모델을 학습하고 교차 검증하는 연구를 진행하여, 본 실험의 결과와 어떻게 달라지는지 비교하는 것도 유용할 것이다. 

> 둘째, 결과에 의도하지 않은 편향이 반영되어 있을 수 있다. 본 연구에서 사용한 모델인 KcELECTRA는 한국어 뉴스 기사 댓글 데이터로 사전학습하였는데, 본 실험에 사용한 Beep 데이터셋 또한 한국어 연예 뉴스 댓글 데이터로 구축한 데이터셋이기에 둘 사이에 오버랩(overlap)이 있을 수 있다. 실제로 Yang, Jang ant Cho (2022)에 따르면 KcELECTRA와 사전학습 코퍼스를 공유하는 KcBERT는 Beep 데이터셋과 잠재적인 토큰 오버랩이 존재하며, 이것이 Beep 데이터셋으로 KcBERT를 평가했을 때 성능이 증가했던 것으로 추측된다고 보고하였다. 이에 KcELCTRA의 사전학습 코퍼스와 각 데이터셋 간의 어느 정도의 오버랩이 있는지, 혹은 오버랩의 유무가 일반화에 영향을 주는지는 후속 연구를 통해 알아볼 수 있을 것이다. 

## 첨언

> 데이터셋 교차 검증은 일반화가 잘 되는 데이터셋을 찾는 데 유용한 방법이 될 수 있다. 그러나 Yin and Zubiaga에서 언급된 바 같이, 혐오표현 탐지에서 일반화에 대한 연구를 데이터셋 교차 검증만으로 한정해서는 안 된다. 혐오표현 탐지에서의 일반화는 결국 현실의 혐오표현을 더 잘 탐지하여, 궁극적으로 보호하고자 하는 집단을 보호할 수 있게 하는 것을 의미하는 방향으로 진행되어야 한다. 따라서 혐오표현 탐지를 위한 데이터셋은 현실의 혐오발언이 무엇인지를 대표해야 하고(Swamy, Jamatia & Gambeck, 2019), 탐지 모델은 그들이 보호하고자 하는 소수 집단을 차별해서는 안 된다는 점(Davidson, Bhattacharya & Weber, 2019; Park et al., 2022)이 중요하다. 이러한 사항을 일괄적으로 검증하기 위해서는 자연어이해에서의 'GLUE 벤치마크 데이터셋'처럼, '한국어 혐오표현 탐지 벤치마크 데이터셋'이 필요할 것이다. 현실의 혐오표현의 여러 측면을 반영하고, 한국어 혐오표현에 특징적인 측면들까지 반영해야 실제 상황을 가정할 수 있는 데이터셋이 구축될 수 있을 것이다. 
> 

 
## 향후 연구

> 이와 관련하여 Vidgen et al., 2019 연구는 영어권에서 욕설 컨텐츠(abusive content)를 식별하는 몇 가지의 언어학적 어려움을 제시하였다. 그 장애물들은 모델의 성능에 직접적인 영향을 미치지만, 정량적인 지표로 측정하기 어렵고 보통 정성적으로  다뤄지기 때문에 항상 논의된 것은 아니라고 밝힌다. Vidgen et al., 2019에서 제시한 장애물들 중, 철자 변형(Spelling variations)의 문제를 다루자면 다음과 같다. 

> 혐오표현의 철자 변형은 다량의 단어장 외(Out of vocabulary) 용어를 만들기 때문에 전체적인 오류 가능성을 증가시킨다(Serra et al., 2017). 이에 텍스트 정규화가 해결책으로 제안되었지만, 텍스트 정규화를 사용하면 의미 있는 사회적 정보를 잃을 위험이 있다(Eisenstein, 2013). 
> 
> 그러나 철자 변형은 한국어 혐오표현 및 비어, 비윤리적 표현(박미은 · 정유남)에서 자주 사용되는 방식이다. 특히 축약 방식으로 만들어진 비어, 비윤리적 표현은 단어가  존재 자체로  언어폭력(verbal abuse)을  행사하는 경우가 많다. 이와 관련된 연구로 (박재연, 2017)가 있는데, 이 연구에서는 한 예로 '안여돼'라는 표현에는  '안경  쓰고  여드름  난  뚱뚱한  사람은  혐오스럽다.'와  같은  명제가  포함되어  있으며, 나아가  ‘안여돼’는  이러한  명제를  적극적으로  주장함으로써  이미  발화에  사용된  것과  같은  수행성을  가진다고 주장했다. 즉 '안여돼'라는  단어가  존재하는  것만으로  ‘안경  쓰고  여드름  난  뚱뚱한  사람’에  대한  모욕이  된다는 것이다. 
> 
> 이처럼 혐오표현에서 사용되는 어휘는 혐오, 차별의 대상과 구체적인 내용이 담긴 구 단위 까지 줄여서 말하는 경향이 있다. 구 단위가 줄어들 때는 어휘의 결합 어휘 의미에 더하여 상황 맥락이나 화자의 의도까지 함께 부호화(encoding)된다. 단순하게 명사구나 문장이 단어로 줄어드는 것에서 나아가 비윤리성을 지니는 특정 맥락이 존재하는 사태를 부호화하는 것이다. 예컨대 ‘틀딱’은 단순히 ‘틀니딱딱’의 두음절어로서의 의미가 아니라 틀니를 사용하는 노인 세대를 조롱하는 명칭이다. '틀딱'과 같은 두음절어를 비롯해 혼성어 등은 비윤리적, 혐오적 표현을 만드는 데 많이 쓰인다. 박미은 · 정유남의 사례를 가져오자면, 기레기(←기자 쓰레기)는 혼성어의 예이며, 번탈남(번식 경쟁에서 탈락한 남자)이 두음절어의 예이다. '기레기’는 비윤리적인 감정을 표현하려는 대상과 이를 빗대어 표현하고자 하는 어휘가 결합하여 대상에 대해 부정적인 뜻을 드러내는 단어이다. 
> 
> 이러한 종류의 신어는 그 참신함과 수수께끼 풀이의  재미가  단어의  폭력성을  은폐하여(박재연, 2017), 또다른 신어가 생겨나기 쉽게 만들기 마련이다. 이 경우, 단어장 외 용어는 점점 늘어날 것이며, 결국에는 실제 상황을 반영하지 못하는 데이터셋과 모델로 인해 혐오표현 탐지 모델의 일반화도 어려워질 것이다. 따라서 일반화가 잘 되는 강건한 데이터셋을 구축하려고 한다면 이러한 언어적 특징을 반영하는 것이 좋다.  

### Challenges and frontiers in abusive content detection


- **Spelling variations** increase the likelihood of errors as they create many ‘out of vocabulary’ terms which have to be handled (Serrà et al., 2017). Text normalization has been proposed as a solution, however this risks losing meaningful social information (Eisenstein, 2013). Using larger and more diverse datasets will only partly mitigate this problem as no dataset will ever account for all variations, and language use changes over time. A more promising way of addressing this is to model language at the character or subword level (Devlin, Chang, Lee, & Toutanova, 2018; Mehdad & Tetreault, 2016). More empirical research into why particular spelling variations occur would also be useful.
- **Polysemy.** 
	- This is when a word with a single spelling has multiple meanings. Which meaning is elicited depends on the context. Magu and Luo describe how ‘euphemistic’ code words, such as ‘Skype’ or ‘Bing’, are used to derogate particular groups (Magu, Joshi, & Luo, 2017). Similarly, Palmer et al. describe how adjectival nominalization (e.g. changing ‘Mexicans’ to ‘the Mexicans’) can transform otherwise neutral terms into derogations (Palmer, Robinson, & Phillips, 2017). Polysemy is a particular challenge with abusive content as many users avoid obvious and overt forms of hate (which are likely to be automatically removed by platforms) and instead express hate more subtly (Daniels, 2013). Word representations which explicitly take into account context are one way of overcoming this issue (Devlin et al., 2018).
- **Long range dependencies.** 
	- Much existing research is focused on short posts, such as Tweets (Schmidt & Wiegand, 2017). However, socially generated content can cross over multiple sentences and paragraphs. Abuse may also only be captured through conversational dynamics, such as multi- user threads (Raisi & Huang, 2016). This has been well-addressed within studies of cyberbullying, but is also highly relevant for the field of abusive content detection more widely (Van Hee et al., 2018). Creation of more varied datasets will help to address this problem, such as using data taken from Reddit or Wikipedia.
- **Language change.** 
	- The syntax, grammar, and lexicons of language change over time, often in unexpected and uneven ways. This is particularly true with informal forms of ‘everyday’ language, which proliferate in most online spaces (Eisenstein, O’Connor, Smith, & Xing, 2014). One implication is that the performance of systems trained on older datasets degrades over time as they cannot account for new linguistic traits. Using multiple temporally separated datasets to evaluate systems will help to address this, as well as further research into the impact of time on language.

### 한국어에서는 음절 첫 단위로 줄여서 서술하는 음절축약어(音節縮約語, syllabic abbreviation) 혐오표현이...
- (3나)의  ‘안여돼’에는  ‘안경  쓰고  여드름  난  뚱뚱한  사람은  혐오스럽다.’와  같은  명제가  포함되어  있다.  형식적으로는  단어이지만  내용적으로는 문장에  해당하는  함의를  가지는  것이다.  나아가  ‘안여돼’는  이러한  명제를  적극적으로  주장함으로써  이미  발화에  사용된  것과  같은  수행성을  가진다.  즉 ‘안여돼’라는  단어가  존재하는  것만으로  ‘안경  쓰고  여드름  난  뚱뚱한  사람’에  대한  모욕이  된다.  본고는  이렇듯  단어가  존재  자체로  언어폭력(verbal abuse)을  행사하는  현상에  대해  논의하고자  한다.  박재연. (2017). 한국어 줄임말 비어의 어휘론과 화용론. 한국어 의미학, 56(), 163 page
	- 유행성인 만큼 오래 지속되지는 않을 테지만, 이러한 형식의 비어들은 계속 나타날 것 같다. 내 뇌피셜임. 
- ‘안여돼’류  신어는  대응하는  평어가  존재하지  않으며, 장차  순화어가 만들어질  가능성도  희박하다는  점에서  기존의  비어들과  다른  특성을  보인다.  박재연. (2017). 한국어 줄임말 비어의 어휘론과 화용론. 한국어 의미학, 56(), 172 page

- 그런데  ‘안여돼’류  신어  역시  이러한  특성을  공유한다.  역시  신어의  참신함과  수수께끼 풀이의  재미가  단어의  폭력성을  은폐한다.38)  앞에서  ‘안여돼’류  신어가  기존에  없던  새로운  범주를  창안한다고  하였는데  이전에  묶인  적이  없던  새로운 범주  설정의  참신함이  사용자들에게  더욱  큰  재미를  준다.39) 박재연. (2017). 한국어 줄임말 비어의 어휘론과 화용론. 한국어 의미학, 56(), 183 page

#### AI 텍스트 말뭉치 기반 비윤리적 어휘 연구
비윤리적 어휘에서 나타나는 경향성은 줄임말 형식이 많다는 것이 다. 줄임말 신어 연구는 크게 두 가지로 나누어지는데, 형태론적 형성 절차에 관심을 가진 연구(시정곤, 2006; 조경하, 2012; 양명희‧ 2015; 최형강, 2016; 이선영, 2016 등)와 어휘론적, 화용론적 관점에 주목한 연구(박재연, 2017; 장경현, 2021 등)이다.8)

앞선 연구에서 신어의 줄임말은 형태론적으로 혼성어, 두음절어(頭 音節語) 과정을 통해 형성된 것으로 보았는데, 본 연구에서 살펴보고 자 하는 비윤리적 어휘에서도 이러한 예시들이 다수 관찰된다.9)

(1) ᄀ. 기레기(←기자 쓰레기)10), 초글링(←초등학생 저글링)11), 군캉스 (←군대 바캉스)12), 호갱(←호객←호구 고객)

ᄂ. 틀딱(←틀니 딱딱), 친없찐(←친구 없는 찐따), 지잡대(←지방 잡종 대학), 번탈남(번식 경쟁에서 탈락한 남자), 판새(←판사 새끼)

ᄃ. 한남(←한국 남자), 한녀(←한국 여자)

(1ᄀ)은 혼성어, (1ᄂ)~(1ᄃ)은 두음절어의 예이다. (1ᄀ)의 ‘기레기, 초글링’은 비윤리적인 감정을 표현하려는 대상과 이를 빗대어 표현하 고자 하는 어휘가 결합하여 대상에 대해 부정적인 뜻을 드러낸다.


장경현(2021:14)에서는 ‘갑분싸’, ‘넌씨눈’, ‘답정너’ 등과 같이 문장이나 상황 전체를 축약하여 단어 형식으로 사용하는 신조어에 대해 혐오 감정 및 행위의 약호화 (encoding)라 하였다.

비윤리적 문장의 어휘는 비하의 대상과 사건 내용이 담긴 구 단위 까지 줄여서 말하는 경향이 뚜렷하다. 구 단위가 줄어들 때는 어휘의 결합 어휘 의미에 더하여 상황 맥락이나 화자의 의도까지 함께 부호 화(encoding)된다.33) 단순하게 명사구나 문장이 단어로 줄어드는 것에 서 나아가 비윤리성을 지니는 특정 맥락이 존재하는 사태를 부호화하 는 것이다.

(16) ᄀ. 틀딱(틀니딱딱), 앰생(엄마가 창녀인 밑바닥 인생)34), 싸튀충(일 을 저지르고 나몰라라 내빼는 행위를 하는 벌레), 도태남/녀(자 유 경쟁에서 도태될 만큼 볼품없고 능력 없는 남자/여자)

ᄂ. 보확찢, 칼푹찍, 후빨

(16ᄀ)의 ‘틀딱’은 단순히 ‘틀니딱딱’의 두음절어로서의 의미가 아 니라 틀니를 사용하는 노인 세대를 조롱하는 명칭이다. ‘틀딱’은 주로 (17)과 같이 무능력하면서 잔소리만 일삼는 노인 세대를 조롱하는 맥 락에 주로 쓰인다.

### 그리고 -충의 경우도 탐지가 어렵다. 
- 주로 온라인상에서 사용되는 형태는 이 정도이지만 실제로는 그때그때 ‘－충’을 결합하여 새로운 어형을 만들어 내는 경우가 많다 장경현. (2018). ‘－충’ 결합 신조어의 의미 연구. 어문학, 142(), 93 page
---
비하의  대상이  항상  소수자나  약자인  것은  아니다.  ‘로퀴’와  같은  비어는  사회적  약자를  대상으로  하지  않는다.  이정복(2014:  36)에서도  차별의  핵심은  약자나  소수자에  대한  것이지만 강자에  대한  지나친  우대나  존경,  무작정의  배제도  차별  행위라고  하면서  차별  언어를  정의할  때  굳이  차별  대상을  소수자나  약자에  한정할  필요가  없다고  보았다.  박재연. (2017). 한국어 줄임말 비어의 어휘론과 화용론. 한국어 의미학, 56(), 180 page


### 그러나, 또 이런 캐릭터 레벨에 함몰되어서는 안된다. 
>  **Studying Generalisability Across Abusive Language Detection Datasets.**
>  Other issues such as the adversarial methods used to bypass detection methods (Gro ̈ndahl et al., 2018) also plague this problem space. Character- based features alleviate this complication to some degree, but more work needs to be done to solve this.
>  그 All you need is love 연구. 
>  강건한 혐오표현 탐지 모델을 만드는 것은 아직 갈 길이 멀며, 이 연구는 그 초석이 된다. 
>  이렇게 논의를 끝내자. 