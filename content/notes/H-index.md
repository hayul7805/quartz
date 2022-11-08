---
title: "H-index"
tags :
- LV-2 
- 정렬
---
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과[1](https://school.programmers.co.kr/learn/courses/30/lessons/42747/solution_groups?language=python3&type=my#fn1)에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 `n`편 중, `h`번 이상 인용된 논문이 `h`편 이상이고 나머지 논문이 h번 이하 인용되었다면 `h`의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 `citations가` 매개변수로 주어질 때, 이 과학자의 H-Index를 `return` 하도록 `solution` 함수를 작성해주세요.

### 제한사항

-   과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
-   논문별 인용 횟수는 0회 이상 10,000회 이하입니다.

### 입출력 예

| citations | return |
| --------- | ------ |
| [3, 0, 6, 1, 5]          |     3   |

### 입출력 예 설명

이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.

## 나의 풀이

```python
def solution(citations):

    citations.sort()

    h = [len(citations[x:])-1 for x in range(len(citations)) if len(citations[x:]) >= citations[x]]
    if len(h) != 0:
       return h[-1]
    else:
        return len(citations)
```

>[!warning]   
>
>이 문제에서 h는 꼭 citations 안에 있지 않다! 
>예를 들어, citations = [6, 5, 5, 5, 3, 2, 1, 0] 이면, h = 4이다.

문제 정독과 테스트 케이스의 중요함을 느끼십시오...
h가 반드시 주어지는 줄 알고 한참을 헤맸다. 이러면 실전에서는 완전 나가리다. 
솔직히 문제가 헷갈리도록 나왔다고 생각하는데, 
그것과는 별개로 문제를 잘 읽자. 
그리고 반례를 항상 잘 떠올리자. 

## 다른 사람의 코드

```python
def solution(citations):
    citations = sorted(citations)
    l = len(citations)
    for i in range(l):
        if citations[i] >= l-i:
            return l-i
    return 0
```

이게 더 효율적인 코드로 보인다. 괜히 `h list`를 만들 필요가 없다. 