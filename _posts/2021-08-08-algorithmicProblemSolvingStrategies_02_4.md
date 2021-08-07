---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true

layout:
title: "[알고리즘 문제 해결 전략] 4 알고리즘의 시간 복잡도 분석"
excerpt: "02 알고리즘 분석 - 4 알고리즘의 시간 복잡도 분석"
date: 2021-08-08
last_modified_at: 2021-08-08
categories:
  -
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
   - [5 알고리즘의 정당성 증명]() <br>
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

<div style="text-align: right"> 02 알고리즘 분석 </div>

## 4 알고리즘의 시간 복잡도 분석

[알고리즘](https://ko.wikipedia.org/wiki/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)이란 어떠한 문제를 풀기 위해 정해진 일련의 절차나 방법을 공식화한 형태로 표현한 것, 계산을 실행하기 위한 단계적 절차를 의미합니다. 즉, 문제 풀이에 필요한 계산 절차 또는 처리 과정의 순서를 뜻합니다. 가능한 한 명료하고 모호하지 않은 표현을 위해 사람들은 알고리즘을 대개 [수도 코드(pseudo-code)](https://ko.wikipedia.org/wiki/%EC%9D%98%EC%82%AC%EC%BD%94%EB%93%9C)나 그것을 구현한 소스 코드의 상태로 표현합니다. 그래서 처음에는 소스 코드와 알고리즘이 같은 것이라고 여기기 쉽습니다.

### 4.2 선형 시간 알고리즘

-
