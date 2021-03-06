---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true

layout:
title: "[알고리즘 문제 해결 전략] 3 코딩과 디버깅에 관하여(2)"
excerpt: "3.4 디버깅과 테스팅, 3.5 변수 범위의 이해, 3.6 실수 자료형의 이해"
date: 2021-08-01
last_modified_at: 2021-08-01
categories:
  - Apss
tags:
  - [알고리즘, 알고리즘 문제 해결 전략]

use_math: false
comments: true
share: false
---

📖[알고리즘 문제 해결 전략] 목차

<details>
<summary>01 문제 해결 시작하기</summary>
<div markdown="1">
  - [2 문제 해결 개관](/algorithmicProblemSolvingStrategies_01_2) <br>
  - [3 코딩과 디버깅에 관하여(1)](/algorithmicProblemSolvingStrategies_01_3(1)) <br>
  - [3 코딩과 디버깅에 관하여(2)](/algorithmicProblemSolvingStrategies_01_3(2))
</div>
</details>

<details>
<summary>02 알고리즘 분석</summary>
<div markdown="1">       
   - [4 알고리즘의 시간 복잡도 분석(1)](/algorithmicProblemSolvingStrategies_02_4(1)) <br>
   - [4 알고리즘의 시간 복잡도 분석(2)](/algorithmicProblemSolvingStrategies_02_4(2)) <br>
   - [5 알고리즘의 정당성 증명](/algorithmicProblemSolvingStrategies_02_5) <br>
</div>
</details>

<details>
<summary>03 알고리즘 설계 패러다임</summary>
<div markdown="1">       
   - [6 무식하게 풀기]()<br>
   - [7 분할 정복]()<br>
   - [8 동적 계획법]()<br>
   - [9 동적 계획법 테크닉]()<br>
   - [10 탐욕법]()<br>
   - [11 조합 탐색]()<br>
   - [12 최적화 문제 결정 문제로 바꿔 풀기]()<br>
</div>
</details>

<details>
<summary>04 유명한 알고리즘들</summary>
<div markdown="1">
    - [13 수치 해석]()<br>
    - [14 정수론]()<br>
    - [15 계산 기하]() <br>
</div>
</details>

<details>
<summary>05 기초 자료 구조</summary>
<div markdown="1">
    - [16 비트마스크]()<br>
    - [17 부분 합]()<br>
    - [18 선형 자료 구조]()<br>
    - [19 큐와 스택, 데크]()<br>
    - [20 문자열]()<br>
</div>
</details>
 
<details>
<summary>06 트리</summary>
<div markdown="1">
    - [21 트리의 구현과 순회]()<br>
    - [22 이진 검색 트리]()<br>
    - [23 우선순위 큐와 힙]()<br>
    - [24 구간 트리]()<br>
    - [25 상호 배타적 집합]()<br>
    - [26 트라이]()<br>
</div>
</details>

<details>
<summary>07 그래프</summary>
<div markdown="1">
    - [27 그래프의 표현과 정의]()<br>
    - [28 그래프의 깊이 우선 탐색]()<br>
    - [29 그래프의 너비 우선 탐색]()<br>
    - [30 최단 경로 알고리즘]()<br>
    - [31 최소 스패닝 트리]()<br>
    - [32 네트워크 유량]()<br>
</div>
</details>

---

<div style="text-align: right"> 01 문제 해결 시작하기 </div>

## 3 코딩과 디버깅에 관하여(3)

### 3.4 디버깅과 테스팅

- 디버깅에 관하여

  프로그램을 작성하고 실행했을 때 원하는 결과가 나오지 않는 경우 대개 디버거를 켜고 한 줄씩 읽어가며 오류를 찾습니다. 하지만 프로그래밍 대회에서는 다음의 세 이유로 그 유용성이 제한됩니다.

  > 1. 프로그래밍 대회에서 작성하는 프로그램은 코드가 길지 않기 때문에 디버거를 사용하는 것보다 눈으로 한 줄씩 읽어 검증하는 것이 더 빠를 수 있습니다.
  > 2. 재귀 호출이나 중복 반복문을 많이 사용하는 복잡한 코드에는 디버거를 사용하는 것이 적당하지 않습니다.
  > 3. 특히 `ACM-ICPC`의 경우 세 명이 한 대의 컴퓨터를 나누어 쓰기 때문에 한 사람이 디버거를 사용하며 컴퓨터를 점유하고 있으면 다른 두 사람은 아무것도 할 수 없게 됩니다.

  `ACM-ICPC는 ACM 국제 대학생 프로그래밍 대회(ACM International Collegiate Programming Contest)로 매년 전 세계 대학생들이 참가하여 실력을 겨루는 국제 컴퓨터 프로그래밍 대회입니다.`{: .small}

  따라서 프로그래밍 대회를 준비하는 사람은 디버거 없이 프로그램의 오류를 찾아내는 연습을 해야합니다. 코드가 복잡하다면 눈으로 오류를 찾는 것이 어렵겠지만, 코드를 복잡하게 짜는 것은 적절하지 못하므로 처음부터 잘 분리된 기능적인 코드를 짜는 것이 필요합니다. 디버거를 사용하는 대신 다음의 단계를 밟으면 좋습니다.

  > 1. 작은 입력에 대해 제대로 실행되나 확인하기 : 입력의 크기가 너무 크면 눈으로 오류를 찾아내는 것이 어렵습니다. 프로그램이 오류가 있는지 확인하고 싶다면 오류를 만들어내는 작은 입력을 찾고 오류를 해결하는 것이 좋습니다.
  > 2. 단정문(assertion)을 쓴다 : 단정문이란 주어진 조건이 거짓일 때 오류를 내고 프로그램을 강제 종료시키는 함수 또는 구문을 말합니다. 주어진 조건이 참일 경우에는 무시되고, 거짓일 경우에만 오류를 내므로 프로그램의 내부 상태를 검증할 때 유용하게 사용할 수 있습니다.
  > 3. 프로그램의 계산 중간 결과를 출력한다. : 프로그램이 실행되는 중간 과정 값들을 출력하고 이것이 내가 예상한 것과 일치하는지 검사하면서 어디서 문제가 생긴 것인지 범위를 좁혀나갈 수 있습니다.

  이러한 과정을 거쳐 문제가 일어나는 곳은 찾았지만 왜 오류가 생기는지 모르겠다면 디버거를 사용해도 좋습니다. 디버거를 사용해도 좋은 또 다른 예는 프로그램이 런타임 오류로 종료되는 경우입니다. 런타임 오류가 났을 때 스택 기록을 출력해준다면 괜찮지만 아니라면 디버거를 사용하여 어디서 오류가 생겼는지 간단하게 확인할 수 있습니다.

- 테스트에 관하여  
  당연한 얘기지만 프로그램을 다 작성하였다면 많은 입력 예제를 만들어 테스트를 하는 것이 좋습니다. 다양한 입력 예제를 만들어 테스트한다면 오답률을 줄일 수 있습니다. 주어진 입력 예제를 약간 바꿔서 넣어 보거나, 있을 수 있는 가장 작은 입력과 가장 큰 입력을 만들어 테스트하고 주어진 시간에 실행되는지 확인하는 것이 좋습니다.

  테스트를할 때 유용하게 사용할 수 있는 기법으로 `스캐폴딩(scaffolding)`이 있습니다. `스캐폴딩`은 원래 건물을 짓거나 보수할 때 공사하는 사람들의 이동을 위해 설치하는 임시 구조물을 의미합니다. 프로그래밍에서는 이것을 다른 코드를 작성할 때 뼈대를 잡기 위해 사용하는 임시 코드를 의미합니다. 어떤 코드를 작성했을 때 입력 예제에 대해서는 다 맞지만 알 수 없는 오류가 생긴 경우 코드를 봐도 오류를 찾기 어려울 수 있습니다. 이때 임의의 작은 입력을 자동으로 생성해 프로그램을 실행하여 검증하는 코드를 사용하면 오류를 찾는데 큰 도움이 됩니다. 하지만 `스캐폴딩`이 모든 오류를 찾아낼 수 없고 자칫하면 코딩 시간을 낭비할 수 있으므로 꼭 필요한 경우에만 사용하는 것이 좋습니다.

### 3.5 변수 범위의 이해

- 산술 오버플로  
  컴퓨터는 수학에 따라 만들어진 것이지만 현실 세계에 존재하기 때문에 제한이 있습니다. 그중 가장 대표적인 제한이 바로 유한성입니다. 수학에서는 어떤 변수 n에 담을 수 있는 숫자에는 제한이 없습니다. 하지만 컴퓨터에서의 모든 변수는 담을 수 있는 크기가 제한되어 있습니다. 따라서 작성한 코드가 수학적/논리적으로는 정당한 알고리즘이라도 그것을 프로그램으로 구현했을 때에는 계산한 것과 다르게 작동하는 경우가 있습니다. 산술 오버플로는 계산 값으로 반환되는 값이 자료형의 표현 가능한 범위를 벗어난 경우 발생합니다. 산술 오버플로가 발생하는 경우는 크게 두 가지입니다.

  > 1. 연산이 일어날 때마다 오버플로를 검사하는 것은 비효율적인 일이므로 대부분의 프로그래밍 언어들은 사칙연산 과정에서 오버플로가 일어나더라도 따로 경고하지 않습니다.
  > 2. 프로그램을 검증할 때 논리의 정확성만 생각하다 보면 산술 오버플로를 잊기 쉽습니다.

- 너무 큰 결과  
  프로그램의 결과가 우리가 흔히 사용하는 32비트의 범위를 벗어난다면 다른 방법으로 결과값을 받아야 합니다. 하지만 습관적으로 32비트만을 사용하는 경우가 많습니다. 또한, 계산의 중간 과정에서 변수를 전달할 때 각 변수의 자료형이 다른 경우도 종종 있습니다. 큰 정수를 사용할 때 주의를 기울여 사용하는 습관을을 길러야합니다.

- 너무 큰 중간 값  
  산술 오버플로를 일으키는 또 다른 경우는 결과값은 크지 않지만 중간에 큰 값을 계산해야 하는 경우가 있습니다. 이 경우 중간에 생긴 산술 오버플로에 대해 경고해주지 않고 이상한 결과값만 출력하기 때문에 오류를 찾기 어렵기 때문에 주의해야 합니다.

- 너무 큰 '무한대' 값  
  프로그램을 작성하다보면 무한대에 해당하는 큰 값을 이용하는 것이 편리할 떄가 있습니다. 예외 처리를 하지 않고 보기에 없는 경우로 처리하고 싶을 때 편리하게 사용됩니다. 하지만 무한대에 해당하는 큰 값들이 중간에 더해지거나 곱해지는 등 연산이 된다면 중간에 오버플로가 생길 수 있으므로 주의해서 사용해야 합니다. 저자의 경우 987,654,321을 자주 사용합니다. 이 값은 32비트 내에서 2^30에 가까운 매우 큰 값이면서 연산이 되더라도 오버플로를 내지 않고 1,000,000,000보다 오타를 확인하기 더 유용하기 때문입니다.

- 오버플로 피해가기  
  오버플로가 발생하였다면 더 큰 자료형을 쓰는 것으로 해결할 수 있습니다. 또한 연산의 순서를 바꾸어 오버플로를 피해갈 수 있습니다. 예를 들어 곱셉, 나눗셈의 연산이 있다면 나눗셈을 먼저 계산하여 오버플로를 방지하는 것입니다.

- 자료형의 프로모션  
  사칙연산이나 대소 비교 등의 이항 연산자들은 두 개의 피연산자를 받습니다. 만약 두 피연산자의 자료형이 다르거나 자료형의 범위가 너무 작은 경우 컴파일러들은 이들을 같은 자료형으로 변환하여 계산하는데, 이를 프로모션이라고 합니다. 프로모션은 보통 신경쓰지 않아도 되지만 가끔 알기 어려운 오류를 만들기도 합니다. 프로모션의 과정은 언어마다 다르지만 C++의 경우 다음과 같은 규칙들이 적용됩니다.

  > 1. 한쪽은 정수형 or 한쪽은 실수형일 경우 : 정수형이 실수형으로 변환됩니다.
  > 2. 양쪽 다 정수형 or 양쪽 다 실수형 : 더 넓은 범위를 갖는 자료형으로 변환됩니다.
  > 3. 양쪽 다 int형보다 작은 정수형인 경우 : 양쪽 다 int형으로 변환됩니다.
  > 4. 부호 없는 정수형과 부호 있는 정수형이 섞여 있는 경우 : 부호 없는 정수형으로 반환됩니다.

### 3.6 실수 자료형의 이해

- 실수 연산의 어려움
- 실수와 근사 값
- IEEE 754 표준
- 실수의 이진법 표기
- 부동 소수점 표기
- 실수 비교하기

> 하나. 비교할 실수의 크기들에 비례한 오차 한도를 정한다
> 둘. 상대 오차를 이용한다

- 대소 비교
- 정확한 사칙연산
- 코드의 수치적 안정성 파악하기
