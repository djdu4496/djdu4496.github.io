---
layout: post
title: "Algorithm"
subtitle: "algorithm"
date: 2021-08-24 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>

  - [[자료구조/알고리즘] 코딩 테스트 준비](#12)
    - [1. Greedy Algorithm](#1)
    - [2. Algorithm with Math](#2)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

## <span style="color:DodgerBlue">Greedy Algorithm</span>

---

### 정의

문제 해결 과정에서 선택의 순간마다 최적이라 생각되는 해답(`locally optimal solution`)을 찾으며, 이를 토대로 최종 문제의 해답(`globally optimal solution`)에 도달하는 문제 해결 방식

### 단계 절차

탐욕 알고리즘으로 문제를 해결하는 방법은 다음과 같이 단계적으로 구분할 수 있습니다.

1. `선택 절차(Selection Procedure)`: 현재 상태에서의 최적의 해답을 선택합니다.
2. `적절성 검사(Feasibility Check)`: 선택된 해가 문제의 조건을 만족하는지 검사합니다.
3. `해답 검사(Solution Check)`: 원래의 문제가 해결되었는지 검사하고, 해결되지 않았다면 선택 절차로 돌아가 위의 과정을 반복합니다.

### 조건

두 가지의 조건을 만족하는 "특정한 상황" 이 아니면 탐욕 알고리즘은 최적의 해를 보장하지 못합니다. 탐욕 알고리즘을 적용하려면 해결하려는 문제가 다음의 2가지 조건을 성립하여야 합니다.

- `탐욕적 선택 속성(Greedy Choice Property)` : 앞의 선택이 이후의 선택에 영향을 주지 않습니다.
- `최적 부분 구조(Optimal Substructure)` : 문제에 대한 최종 해결 방법은 부분 문제에 대한 최적 문제 해결 방법으로 구성됩니다.
  탐욕 알고리즘은 항상 최적의 결과를 도출하는 것은 아니지만, 어느 정도 최적에 근사한 값을 빠르게 도출할 수 있는 장점이 있습니다. 이 장점으로 인해 탐욕 알고리즘은 근사 알고리즘으로 사용할 수 있습니다.

탐욕 알고리즘은 항상 최적의 결과를 도출하는 것은 아니지만, 어느 정도 최적에 근사한 값을 빠르게 도출할 수 있는 장점이 있습니다. 이 장점으로 인해 탐욕 알고리즘은 근사 알고리즘으로 사용할 수 있습니다.

# <span style="font-size:20px;color:DodgerBlue">2</span>

## <span style="color:DodgerBlue">Algorithm with Math</span>

<br>
