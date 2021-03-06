---
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true

layout:
title: "[알고리즘 문제 해결 전략] 4 알고리즘의 시간 복잡도 분석(2)"
excerpt: "4.5 시간 복잡도, 4.6 수행 시간 어림짐작하기, 4.7 계산 복잡도 클래스"
date: 2021-08-15
last_modified_at: 2021-08-15
categories:
  - Apss
tags:
  - [알고리즘, 알고리즘 문제 해결 전략]

use_math: true
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

<div style="text-align: right"> 02 알고리즘 분석 </div>

## 4 알고리즘의 시간 복잡도 분석

### 4.5 시간 복잡도

시간복잡도(time complexity)란 가장 널리 사용되는 알고리즘의 수행 시간 기준으로, 알고리즘의 시간복잡도는 알고리즘이 실행되는 동안 계산되는 기본적인 연산의 수를 입력의 크기에 대한 함수 관계로 나타내 시간을 정량화하는 것입니다. 여기서 기본적인 연산이란 더 작게 쪼갤 수 없는 (반복문이 포함되지 않은) 최소 크기의 연산을 말합니다.

시간복잡도가 높다는 것은 입력의 크기가 증가할수록 알고리즘의 수행 시간 또한 증가한다는 말입니다. 하지만 시간복잡도가 낮다고 항상 더 빠르게 동작하는 것은 아닙니다. 입력의 크기가 충분히 작다면 시간복잡도가 높은 알고리즘이 더 빠르게 동작할 수도 있습니다. 시간복잡도가 낮은 알고리즘은 입력이 커질수록 더 효율적인 알고리즘입니다. <br>

- 입력의 종류에 따른 수행 시간의 변화  
  입력의 크기뿐만 아니라 입력의 형태도 수행 시간에 영향을 미칩니다. 따라서 모든 경우를 고려하기 위해 최선, 최악, 평균적인 경우에 대한 수행 시간을 각각 따로 계산해야 합니다. 이 중에서 가장 많이 사용되는 것은 최악의 수행 시간 혹은 수행 시간의 기대치입니다. 여러 알고리즘에서 두 기준이 거의 같이 때문에 대부분 두 기준을 따로 구분하지 않고 사용합니다. <br>

- 점근적 시간 표기 : $O$ 표기  
  시간복잡도는 계산하기 너무 어렵다는 문제가 있습니다. 알고리즘이 실행될 때 필요한 명령의 수가 애매하고 알고리즘이 복잡할 땐 그것을 세기도 어렵기 때문입니다. 따라서 전체 수행 시간에 큰 영향을 미치지 않는 상수 부분은 무시하고 반복문의 반복 수만 고려하여 수행 시간을 계산합니다. 주어진 함수에서 가장 빨리 증가하는 항만을 남긴 채 나머지는 다 버리는 대문자 $O$ 표현법(Big-O Notation)을 사용합니다. 예를 들어 어떤 알고리즘의 수행 시간이 $$f(N)= \sqrt{5}/3(N^2)-Nlg(N/2)+16N-7$$이라고 할 때, 최고차항인 $$\sqrt{5}/3*N^2$$에서 계수를 뗀 $N^2$을 수행 시간으로 계산하여 $O(N^2)$으로 표기합니다. 또 다른 예로 수행 시간이 $f(N)=42$인 경우 입력의 크기와 상관없이 항상 같은 시간이 걸리기 때문에 $O(1)$로 표기합니다. 이러한 수행 시간을 갖는 알고리즘을 상수 시간(constant-time) 알고리즘이라고 합니다. 이처럼 최고차항만을 수행 시간으로 계산하기 때문에 $O$표기법은 훨씬 간편하게 사용됩니다. <br>
- $O$ 표기법의 의미  
  $O$ 표기법은 계산하기 간편하고, 알아보기 쉽습니다. 하지만 그것만을 원한다면 최고차항이 아니라 빠름, 중간, 느림과 같은 표현을 사용했을 것입니다. $O$ 표기법은 최고차항만을 사용하지만, 함수의 상한을 나타내는 의미가 있습니다. 예를 들어 $f(N)=N^2+100N+1$의 수행 시간을 갖는 알고리즘이 있다면 $O(N^2)$으로 표현할 수 있을 것입니다. 이때 적절한 $N_0$와 $C$를 선택하면$C(N_0)^2≥(N_0)^2+100(N_0)+1$가 항상 성립하기 때문에 함수의 상한을 나타냅니다. 하지만 함수의 상한을 나타내는 것과 최악의 수행 시간은 다른 것입니다. $O$ 표기법은 수행 시간을 간단히 나타내는 표기법이므로 착각하지 않도록 주의해야 합니다. <br>

- 시간복잡도 분석 연습  
   두 가지 예제로 시간복잡도 분석 연습을 해봅시다.

  1. 선택 정렬(selection sort)
     선택 정렬이란 모든 $i$에 대해 $A[i..N-1]$에서 가장 작은 원소를 찾은 뒤, 이것을 $A[i]$와 바꾸는 것을 반복합니다.

  ```c++
  void selectionSort(vector<int>& A){
    for(int i=0; i<A.size(); ++i){
      int minIndex=i=;
      for(int j=i+1; j<A.size(); ++j)
        if(A[minIndex]>A[j]) minIndex=j;
      swap(A[i], A[minIndex]
    }
  }
  ```

  중첩된 for문의 수행 횟수를 계산하기 위해 $i=0$일 때는 $N-1$번, $i=1$일 때 $N-2$번, $i=N-1$일 때 0번이라고 하면 다음과 같은 식으로 정리할 수 있습니다.

    <center>
    $(N-1)+(N-2)+ ... + 1 = 1/2N^2-1/2N=O(N^2)$
    </center>
  <br>
    더 간단하게는 최대 $O(N)$번 실행되는 for문이 두 개 겹쳐있으므로 최종 시간복잡도는 $O(N^2)$라고 계산해도 됩니다. 선택 정렬의 시간복잡도는 배열의 크기 $N$에 의해서만 결정되기 때문에 최악의 경우와 최선의 경우의 시간복잡도가 같다는 것을 유의해야 합니다.

  2. 삽입 정렬(insertion Sort)
     삽입 정렬이란 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분 앞부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘입니다. 즉, 앞에서부터 비교하여 더 작은 값이 뒤에 있다면 작은 값을 비교한 값 앞에 두고 뒤로 한 칸씩 밀어 앞부분을 정렬된 배열로 만드는 것을 반복하여 전체 배열을 정렬하는 것입니다.

  ```c++
  void insertionSort(vector<int>& A){
    for(int io=0; i<A.size(); ++i){
      int j =i;
      while(j>0 && A[j-1]>A[j]){
        swap(A[j-1], A[j]);
        --j;
      }
    }
  }
  ```

  삽입 정렬의 최선의 경우는 이미 정렬된 배열이 입력인 경우입니다. 이때 모든 원소는 모두 제자리이기 때문에 while 문이 종료되어 $i$에 대한 for 문만 계산하여 전체 수행 시간은 선형 시간, 즉 $O(N)$이 됩니다. 반대로 최악의 경우는 역순으로 정렬된 배열인 경우입니다. 이때 while 문을 끝까지 돌아야 하므로 전체 수행 시간은 $O(N^2)$이 됩니다.

<br>

- 시간복잡도의 분할 상환 분석  
  문제의 조건에 따라 반복문의 개수를 세는 것 이외에 더 정확한 시간 시간복잡도를 계산하는 것도 가능한데, 그 대표적인 예가 시간복잡도의 분할 상환 분석(amortized analysis)입니다. 간단하게 설명하자면 $N$개의 작은 작업들을 순서대로 수행하는 작업이 있다고 할 때, 각 작은 작업에 걸리는 시간은 모두 다르지만 전체 작업에 걸리는 시간이 일정한 경우에 각 작은 작업의 평균 시간을 전체 시간/$N$으로 표현하는 것입니다. <br>

<br>

### 4.6 수행 시간 어림짐작하기

- 주먹구구 법칙  
  어떤 알고리즘이 이 문제를 해결할 수 있을지 알기 위해서 프로그램을 작성하기 전에 입력의 최대 크기와 알고리즘의 시간복잡도를 보고 수행 시간을 어림짐작할 수 있어야 합니다. 하지만 프로그램의 수행 시간을 짐작한다는 것은 프로그램 동작 속도에 영향을 끼치는 CPU의 클론 속도, 1클록마다 수행할 수 있는 CPU 명령어의 수, 운영 체제와 컴파일러의 버전 등 많은 요소가 있기에 매우 어려운 일입니다. 하지만 앞에서 언급한 많은 요소는 프로그램 수행 시간에 몇 배의 영향을 미치지만, 알고리즘의 시간복잡도는 수천, 수만 배 영향을 미치기 때문에 시간복잡도와 입력 크기만 알고 있더라도 프로그램의 수행 시간을 예측할 수 있습니다.

  입력의 최대 크기가 $N=10000$이고 테스트 케이스 하나를 푸는데 제한 시간이 1초인 문제를 풀고 있다고 가정합니다. 프로그래밍 대회 참가자들이 사용하는 주먹구구 법칙은 다음과 같습니다.

  > 입력의 크기를 시간복잡도에 대입해서 얻은 반복문 수행 횟수에 대해, 1초당 반복문 횟수가 1억($10^8$)을 넘어가면 제한 시간을 초과할 가능성이 있다.

  위의 법칙으로 쉽게 대략적인 수행 시간을 예측할 수 있지만 다른 요인들로 수행 시간이 달라질 수 있기에 예측한 수행 횟수가 기준의 10% 이하인 경우에만 적용하는 등 충분한 여유를 가지고 적용하는 것이 좋습니다.

<br>

- 주먹구구 법칙은 주먹구구일 뿐이다  
  정확하게 수행 시간을 계산한 것이 아니기에 이 법칙을 맹신해서는 안됩니다. 위 법칙 이외에도 다른 요소들을 참조해 수행 시간을 예측해야 합니다.

  1. 시간복잡도가 프로그램의 실제 수행 속도를 반영하지 못하는 경우  
     $O$ 표기법은 최고차항으로만 계산한 것이기에 실제 프로그램이 수행한 시간과 다를 수 있습니다.<br>

  2. 반복문 내부가 복잡한 경우  
     반복문 내부가 복잡할수록 예측한 시간보다 오래 걸리고 반복문 내부가 간단할수록 예측한 시간보다 빨리 수행됩니다.<br>

  3. 메모리 사용 패턴이 복잡한 경우  
     현대의 CPU는 메모리에 있는 자료를 직접 접근하지 않고 캐시라고 부르는 작고 빠른 메모리로 옮겨 처리합니다. 메모리에서 캐시로 자료를 가져올 때 인접한 자료들을 함께 가져오기 때문에 인접한 자료들을 연속해서 사용하는 프로그램은 더 빠른 수행 시간을 갖습니다.<br>

  4. 언어와 컴파일러의 차이  
     앞의 법칙은 최적화 옵션이 추가된 현대 c++ 컴파일러를 기준으로 합니다. 만약 최적화 옵션이 없고 그보다 느린 언어를 사용한다면 더 느린 수행 시간을 가질 것입니다.<br>

  5. 구형 컴퓨터를 사용하는 경우

<br><br>

### 4.7 계산 복잡도 클래스 : P, NP, NP-완비

시간복잡도는 문제의 특성이 아닌 알고리즘의 특성입니다. 한 문제에 두 가지 이상의 알고리즘이 사용되기도 하기 때문입니다. 각 문제 해결을 위해 얼마나 빠른 알고리즘이 존재하는지를 기준으로 문제들을 분류하고 각 분류의 특성을 연구하는 계산 복잡도 이론 학문이 있습니다. <br>

- 문제의 특성 공부하기  
  계산 복잡도 이론에서는 다항 시간 알고리즘이 존재하는 문제들의 집합을 P 문제라고 부릅니다. P 문제처럼 같은 성질을 갖는 문제들을 모아놓은 집합을 계산 복잡도 클래스(complexity class)라고 부릅니다. 다양하고 많은 복잡도 클래스가 있지만, P와 NP문제가 가장 중요한 클래스입니다. P는 polynomial을 의미하고 NP는 non-polynomial이라고 해서 NP문제는 다항 시간 알고리즘이 존재하지 않는 문제들의 집합이라고 착각하면 안됩니다. <br>

- 난이도의 함정  
  어떤 문제를 다항 시간에 풀 수 있음을 증명하기는 쉽지만 풀 수 없음을 보이기란 어려운 것입니다. $P$ 문제는 다항 시간에 풀 수 있는 알고리즘 하나만 있어도 증명이 되지만 반대인 경우를 증명하려면 모든 알고리즘을 대입해 보아야 하기 때문입니다. 어떤 문제를 다항 시간에 풀 수 있는 알고리즘을 못 찾았다고 해서 없다고 할 수 없기에 계산 복잡도에서는 `어려운 문제`를 다음과 같이 정의합니다.

  > 정말 어려운 문제를 어려운 문제의 기준으로 삼습니다.  
  > 기준 이상으로 어려운 문제만을 어려운 문제라고 부릅니다.

  꼬리에 꼬리를 무는 말처럼 위의 기준으로 분류하는 것 또한 어렵기에 두 문제의 난이도를 비교하기 위해 환산(reduction)이라는 기법을 이용합니다. B의 입력을 적절히 변형하여 A의 입력으로 바꾸는 환산 알고리즘이 있다고 가정합니다. A를 푸는 가장 빠른 알고리즘과 환산 알고리즘을 합하여 B의 문제를 풀게 되면 A와 같은 시간이 걸립니다. 이 시간은 B의 최소 수행 시간보다 크거나 같기에 A가 B 이상으로 어렵다는 것을 알 수 있습니다. <br>

- NP 문제, NP 난해 문제  
  NP 문제는 답을 줬을 때 정답인지를 다항 시간 내에 확인할 수 있는 문제입니다. 문제를 분류할 때 정말 어려운 문제가 너무 쉽거나 너무 어려우면 문제를 분류하는데 의미가 없기에 정말 어려운 문제를 잘 정하는 것이 중요합니다. 정말 어려운 문제의 기준이 되는 것이 바로 SAT 문제(satisfiability problem)입니다. SAT 문제란 $N$개의 불린(Boolean) 값 변수로 구성된 논리식을 참으로 만드는 변숫값들의 조합을 찾는 문제입니다. 예들 들어 불린 값 변수 $a, b, c$로 구성된 다음 논리식은 세 변수의 값이 특정 조합을 이루어야 만족합니다.

  $$((a||b||!c)and(!c||!a)and((!a and b)||(b and!c)))and(!b||(!a and!c))$$

  SAT 문제는 모든 NP 문제 이상으로 어렵다는 의미가 있습니다. SAT 문제를 기준으로 더 어려운 문제를 NP-난해(NP-hard) 문제라고 합니다. NP-난해 문제이면서 NP인 문제들을 NP-완비(NP-Complete)문제라고 합니다. <br>

- P=NP?  
  밀레니엄 7대 수학 난제로 유명해진 P=NP 문제는 P와 NP가 같은지를 확인하는 문제입니다. NP-난해 문제 중 하나를 다항 시간에 풀 수 있다면, 이 알고리즘으로 NP에 속한 모든 문제를 다항 시간에 풀 수 있습니다. 이 경우에 P=NP라고 할 수 있고 반대로 NP 문제 중 하나를 골라 다항 시간에 푸는 방법이 없음을 증명하면 P≠NP임을 보일 수 있습니다. 하지만 아직 아무도 증명하지 못했기에 아직 수학 난제로 남아있습니다.
