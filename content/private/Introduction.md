---
title: "Introduction"
---

#### Hate speech detection is not as easy as you may think

> Despite the apparent difficulty of the hate speech detection problem evidenced by social-media providers, current state-of- the-art approaches reported in the literature show near-perfect performance. Within-dataset experiments on labeled hate speech datasets using supervised learning achieve F1 scores above 93% [3, 7–9]. Nevertheless, there are only a few studies towards deter- mining how generalizable the resulting models are, beyond the data collection upon which they were built on, nor on the factors that may affect this property [10]. Furthermore, recent literature that surveys current work also views the state-of-the-art under a more conservative and cautious light [3,10].
- 이거 내 서론에 넣어도 되겠다. 일반적인 내용이기도 하고.

#### 한국어 줄임말 비어의 어휘론과 화용론.
> Austin  (1962)는  말이  힘을  가지는  현상을  주목하였다.  언어는  존재하는  세계를  모사(模寫)하는  데에  그치지  않고  그  자체가  어떤  행위를  수행한다 박재연. (2017). 한국어 줄임말 비어의 어휘론과 화용론. 한국어 의미학, 56(), 174 page
- 이건 그냥 간지난다...
- 하지만 틀린 인용이다. 

#### Transfer Learning for Hate Speech Detection in Social Media
> Hate speech has also been linked to the deterioration of its victims’ health. Several studies confirmed that racism and sexism are associated with poorer mental health, including depression, isolation, anxiety, and poor self- esteem [4], [5].

#### Towards generalisable hate speech detection
> 인터넷, 혐오표현 이야기. 나도 홍성수 연구 인용하면 되겠다.
> The Internet saw a growing body of user-generated content as social media platforms flourished (Schmidt & Wiegand, 2017; Chung et al., 2019). While social media provides a platform for all users to freely express themselves, offensive and harmful contents are not rare and can severely impact user experience and even the civility of a community (Nobata et al., 2016). One type of such harmful content is hate speech, which is speech that directly attacks or promotes hate towards a group or an individual member based on their actual or perceived aspects of identity, such as ethnicity, religion, and sexual orientation (Waseem & Hovy, 2016; Davidson et al., 2017; Founta et al., 2018; Sharma, Agrawal & Shrivastava, 2018).

> 신생이지만 잘 크고 있다.
> Since the automatic detection of hate speech was formulated as a task in the early 2010s (Warner & Hirschberg, 2012), the field has been constantly growing along the perceived importance of the task.

> 일반화란 무엇인가?
> Most if not all proposed hate speech detection models rely on supervised machine learning methods, where the ultimate purpose is for the model to learn the real relationship between features and predictions through training data, which generalises to previously unobserved inputs (Goodfellow, Bengio & Courville, 2016). The generalisation performance of a model measures how well it fulfils this purpose.

> 우리는 혐오표현 탐지 연구를 왜 하는가? 
> The ultimate purpose of studying automatic hate speech detection is to facilitate the alleviation of the harms brought by online hate speech. To fulfil this purpose, hate speech detection models need to be able to deal with the constant growth and evolution of hate speech, regardless of its form, target, and speaker.
> 최근의 시작된 논의는 무엇인가. 왜 시작되었는가?
> Recent research has raised concerns on the generalisability of existing models (Swamy, Jamatia & Gambäck, 2019). Despite their impressive performance on their respective test sets, the performance significantly dropped when the models are applied to a different hate speech dataset. This means that the assumption that test data of existing datasets represent the distribution of future cases is not true, and that the generalisation performance of existing models have been severely overestimated (Arango, Prez & Poblete, 2020).

## 홍성수 2016
혐오표현은 “소수자에 대한 편견 또는 차별을 확산시키거나 조장하는 행위 또는 어떤 개인, 집단에 대해 그들이 소수자로서의 속성을 가졌다는 이유로 멸시・모욕・위협하거나 그들에 대한 차별・적의・폭력을 선동하는 표현”으로 정의할 수 있다{홍성수, 2016}. 혐오표현의 해악은 포용의 공공선을 파괴하고 각 구성원이 자유롭고 평등하게 더불어 살 수 있는 “사회적 환경”을 파괴한다는 점에 있다{홍성수. (2019)}. 

**<홍성수 2019>**
국가인권위원회의 <혐오표현 리포트>에 따르면, 혐오표현(hate speech)은 “성별, 장애, 종교, 나이, 출신지역, 인종, 성적지향 등을 이유로 어떤 개인·집단에게 1) 모욕, 비하, 멸시, 위협 또는 2) 차별·폭력의 선전과 선동을 함으로써 차별을 정당화·조장·강화하는 효과를 갖는 표현”을 뜻한다.

**홍성수 2019에 따르면**, 그동안 논의된 혐오표현의 해악은 세 가지로 분류된다. 첫째, 혐오표현이 그 대상집단의 구성원들에게 정신적 고통을 야기한다는 것은 의학적, 사회과학적 연구를 통해 상당 부분 입증되어 왔다. 둘째, 그 개인적인 정신적 고통은 사회 참여를 주저하게 만들고 더 나아가 한 사회의 동등한 구성원으로서의 존엄한 삶을 파괴하고, 다양한 정체성을 가진 구성원들이 함께 살아가야 한다는 공공선을 붕괴시킨다. 셋째, 혐오표현은 차별과 폭력을 야기하는 선동적 성격을 갖기 때문에 그 자체로 해악이 있거나 차별과 폭력이 임박한 단계로 간주된다.


## 케이스 정리

**케이스 1.**
1. 하려고 하는 것을 밝힌다. 
2. 배경 간략히 소개, 현 사태, 
3. 그와 관련된 논의들
4. **그러나, 그 논의들에 한계**
5. 본 연구의 특수성
6. 특히 무엇에 집중하는지
7. 앞으로의 차례 서술

**케이스 2**
1. 배경, 현 사태 (인터넷 이야기를 하네.)
2. 하려고 하는 것
3. 현 사태의 한계
4. 특수성
5. 개별 결과 보고
6. 그 결과에 이어서 한 것 보고
7. 공헌

**케이스 3**
1. 현 사태(인터넷, 혐오표현)
2. 현 기술의 한계
3. 그러나 시급한 문제이다. 
4. 일반화 정의
5. 혐오표현 탐지 모델의 제1목표
6. 공헌


## 나의 서론 정리


이 연구는 한국어 혐오표현과 관련하여 공개되어 있는 데이터셋 각각에 모델을 학습시키고, 학습에 사용하지 않은 다른 데이터셋을 통해 학습한 모델의 성능을 테스트하는 데이터셋 교차 검증(cross-dataset testing)을 수행한다. 실험 전반에 걸쳐서
정량적으로 데이터셋에 따른 성능 변화를 보는 한편, 정성적으로 오분류 케이스를 살핀다. 최종적으로는 데이터셋에 관계없이 성능 변화가 일정한 모델, 즉 교차 데이터셋 일반화(cross-dataset generalizability)가 잘 되는 모델을 찾고, 데이터셋의 크기와 양성 샘플의 비율 측면에서 일반화에 영향을 주는 요인을 찾아본다. 

온라인 혐오표현은 여러 해악을 갖고 있다. 일반적인 혐오표현을 다룬 홍성수(2019)에 따르면, 혐오표현은 그것의 대상이 되는 집단의 구성원들에게 정신적 고통을 야기하며, 그 개인적인 고통은 사회 참여를 주저하게 만든다. 더 나아가, 한 사회의 동등한 구성원으로서의 존엄한 삶을 파괴하고, 다양한 정체성을 가진 구성원들이 함께 살아가야 한다는 공공선을 붕괴시킨다. 혐오표현은 또한 선동적인 성격을 갖고 있어, 단지 말에 그치지 않고 직접적인 차별과 폭력을 야기하기도 한다. 그리고 온라인 공간에서, 혐오표현의 해악은 한층 심화된다. 온라인이라는 매체의 특성상 동시간에, 그리고 광범위하게 영향이 퍼지며, 또한 온라인 공간이 제공하는 익명성은 유저들이 공격과 차별, 배제를 좀 더 쉽게 표현할 수 있게 한다. 

자연어처리 분야는 이러한 온라인 혐오표현의 해악을 완화시켜 모두에게 안전하고, 개방적인 온라인 환경을 만들기 위해 혐오표현 탐지 연구를 발전시켰다. 혐오표현 탐지 연구는 2010년대 초에 과제로 공식화되어(Warner & Hirschberg, 2012), 이후로도 그 중요성이 점점 대두됨에 따라 지속적으로 성장하고 있는 분야이다. 기술적으로도 전통적인 통계 기법 모델부터, 최근에는 딥러닝 기반의 첨단 모델을 사용하여 93% 이상의 F1 점수를 보고하는 등 빠르게 개선이 이루어지고 있다. 

혐오표현 탐지 모델은 지도학습(supervised learning)을 기반으로 하기 때문에, 라벨(label)과 문장으로 이루어진 데이터셋이 필요하다. 이에 국외와 국내를 비롯하여 여러 연구들에서는 혐오표현과 관련된 데이터셋을 구축, 배포하고 있다. 데이터셋은 크게 두 단계로 구축되는데, 먼저 연구자가 세운 지침(guideline)에 따라 포털 사이트, 소셜네트워크서비스(SNS) 등에서 문장을 수집하거나, 연구자나 연구에 참여하는 일반 대중이 직접 문장을 생성한다. 그리고는 수집, 혹은 생성된 문장에 연구자나 연구에 참여하는 일반 대중이 혐오표현이나 일반문장 등의 라벨을 붙이는 방식으로 데이터셋이 구축된다. 이후로는 구축된 데이터셋을 훈련 데이터와 테스트 데이터로 나누어 훈련 데이터로는 모델을 학습시키고, 테스트 데이터셋으로 모델이 훈련에 사용한 데이터 이외에 대해서도 잘 분류를 하는지, 일반화 가능성을 평가한다. 

그러나, 최근 몇몇 연구들은 이러한 방식으로 모델의 일반화 가능성을 측정하는 것에 대한 우려를 제기했다(Swamy, Jamatia & Gambeck, 2019). 테스트 데이터셋에서 성능이 잘 나왔던 모델이라도, 그 모델을 다른 혐오표현 데이터셋에 적용하면 성능이 크게 하락한다는 것이다. 이는 훈련 데이터셋과 테스트 데이터셋이 원천적으로 같은 데이터셋을 분할한 것이기 때문인데, 훈련 데이터셋으로 학습한 모델은 훈련 데이터의 문장들의 구조, 어휘 등과 주석자(annotator)의 편향을 함께 학습하게 된다. 따라서 비슷한 구조와 어휘, 편향을 공유하는 테스트 데이터셋에서는 뛰어난 성능을 내는 모델이더라도, 다른 구조와 어휘, 다른 편향이 내재된 외부 데이터에는 그 성능이 변화하는 것이다. 이러한 결과는 테스트 데이터셋이 미래의 사례 분포를 대표할 수 없으며, 또한 기존 모델의 일반화 성능이 심각하게 과대 평가되었다는 것을 의미하게 된다(Arango, Pres & Poblete, 2020).

그러나 일반화와 관련된 논의들은 주로 이용 가능한 데이터셋과 공개되어 있는 구축 지침이 많은 국외, 영어권을 중심으로 이루어지고 있다. 한국어 혐오표현 데이터셋의 경우 대부분 비교적 최근에 구축, 공개된 까닭에, 서로 다른 지침과 플랫폼을 이용하였음에도 불구하고 이들 간의 데이터셋 교차 검증 연구는 아직 진행되지 않았다. 데이터셋 교차 검증이 진행되지 않으면 한 혐오표현 데이터셋으로 학습한 모델이 완전히 다른, 새로운 데이터에 대해서 어느 정도의 분류 성능을 보일지 알 수 없다. 이에 본 연구는 구축 지침이 명확하며, 공개되어 있는 한국어 혐오표현 관련 데이터셋 간의 교차 검증 연구를 진행하였다. 이를 바탕으로, 일반화에 강한 혐오표현 탐지 모델을 만드는 요건을 논의하였다. 본 연구의 공헌은 따라서 다음 3가지이다. 

1. 한국어 혐오표현 관련 데이터셋 간의 데이터셋 교차 검증을 처음으로 시도하였다. 총 4개의 데이터셋을 교차 검증하여 12개의 결과를 확보하였다. 
2. 검증 결과를 정확도와 F1 점수로 정량적으로 보고하고, 또한 정성적 분석을 위한 오분류 케이스를 제시하였다.
3. 일반화 요건에 관해 한국어 특징적인 결과를 보고하였다. 영어권 연구와는 다르게, 한국어의 경우 데이터셋의 크기는 일반화에 큰 영향을 주지 않았으나,  양성 샘플의 비율이 클 수록 일반화가 잘 되었던 것은 영어권 연구 결과와 일치함을 확인하였다.  