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
    - [1. Algorithm](#1)
    - [2. Greedy Algorithm](#2)
    - [3. Dynamic Programming](#3)
    - [4. Algorithm with Math](#4)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

## <span style="color:DodgerBlue">Algorithm</span>

---

### 알고리즘을 푼다는 것의 의미

`내가 생각한 문제 해결 과정을 컴퓨팅 사고로 변환하여 코드로 구현한다는 것`과 같습니다

# <span style="font-size:20px;color:DodgerBlue">2</span>

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

# <span style="font-size:20px;color:DodgerBlue">3</span>

## <span style="color:DodgerBlue">Dynamic Programming</span>

---

`동적 계획법`

### 정의

<span style="color:indianred">주어진 문제를 여러 개의 하위 문제로 나누어 풀고, 하위 문제들의 해결 방법을 결합하여 최종 문제를 해결</span>하는 방식입니다.

`하위 문제를 계산한 뒤 그 해결책을 저장하고, 나중에 동일한 하위 문제를 만날 경우 저장된 해결책을 적용해 계산 횟수를 줄입니다`. 즉, 하나의 문제는 단 한 번만 풀도록 하는 알고리즘이 바로 이 다이내믹 프로그래밍입니다. 이때 결과를 저장하는 방법을 `Memoization`이라고 합니다.

> 탐욕 알고리즘이 매 순간 최적의 선택을 찾는 방식이라면, DP는 <u>모든 경우의 수를 조합해 최적의 해법을 찾는 방식</u>입니다.

### 사용 조건

- `Overlapping Sub-problems` : 큰 문제를 작은 문제로 나눌 수 있고, 이 작은 문제가 중복해서 발견된다.
  - 큰 문제로부터 나누어진 작은 문제는 큰 문제를 해결할 때 여러 번 반복해서 사용될 수 있어야 한다
- `Optimal Substructure` : 작은 문제에서 구한 정답을 큰 문제에서도 사용할 수 있다.
  - 이 조건에서 말하는 정답은 최적의 해결 방법(`Optimal solution`)을 의미합니다. 즉, 작은 문제들의 최적의 해법(`Optimal solution of Sub-problems`)을 결합하면, 결국 전체 문제의 최적의 해법(Optimal solution)을 구할 수 있습니다. 주어진 문제에 대한 최적의 해법을 구할 때, 주어진 문제의 작은 문제들의 최적의 해법(`Optimal solution of Sub-problems`)을 찾아야 합니다.

### Memoziation

컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술입니다. 즉, <span style="color:indianred">하위 문제의 해결책을 저장하는 방법</span>입니다. 다이내믹 프로그래밍을 적용한 피보나치 수열 문제(`aux(n) => {...}`)가 바로 이 개념의 예시가 됩니다.

# <span style="font-size:20px;color:DodgerBlue">4</span>

## <span style="color:DodgerBlue">Algorithm with Math</span>

### GCD/LCM(최대공약수, 최소공배수)

### 순열/조합

### 멱집합
