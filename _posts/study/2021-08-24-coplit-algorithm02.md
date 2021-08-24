---
layout: post
title: "[coplit] Algorithm02"
subtitle: "(partTimeJob)"
date: 2021-08-24 09:00:00 +0900
categories: study
tags: algorithm
comments: true
published: false
---

# 개요

- 목차
  - [1.문제✉️](#1)
  - [2.나의 코드🔖](#2)
  - [3.키포인트🔐](#3)

# <span style="font-size:20px;color:DodgerBlue">1</span>

# 문제

편의점에서 아르바이트를 하고 있는 중에, 하필이면 피크 시간대에 손님에게 거스름돈으로 줄 동전이 부족하다는 것을 알게 되었습니다.
현재 가지고 있는 동전은 1원, 5원, 10원, 50원, 100원, 500원으로 오름차순으로 정렬되어 있고, 각 동전들은 서로 배수 관계에 있습니다.
동전 개수를 최소화하여 거스름돈 K를 만들어야 합니다. 이때, 필요한 동전 개수의 최솟값을 구하는 함수를 작성해 주세요.

## 입력

### 인자: k

- `number` 타입의 k
- 1 <= k <= 100,000,000

## 출력

- number 타입의 거스름돈 K원을 만드는데 필요한 동전 개수의 최솟값을 반환해야 합니다.

## 입출력 예시

```javascript
// 4000원을 받았을 때 500원짜리 동전 8개를 반환합니다.
const output1 = test1(4000);
console.log(output1); // --> 8

// 4972원을 받았을 때 500원짜리 동전 9개, 100원짜리 동전 4개, 50원짜리 동전 1개, 10원짜리 동전 2개, 1원짜리 동전 2개, 총 18개를 반환합니다.
const output2 = test1(4972);
console.log(output2); // --> 18
```

---

# <span style="font-size:20px;color:DodgerBlue">2</span>

# 나의 코드

```javascript
function partTimeJob(k) {
  // (거스름돈(수)) => 필요한 동전 개수의 최소값(수)

  // 필요한 동전 개수의 최소값을 담을 변수 numOfCoins를 선언 후 0으로 초기화
  let numOfCoins = 0;

  // * 탐욕 알고리즘의 문제 해결 과정을 적용
  // 1. 선택 절차 - 현재 상태에서의 최적의 해답을 선택합니다.
  // 2. 적절성 검사 - 선택된 해가 문제의 조건을 만족하는지 검사합니다.
  // 3. 해답 검사 - 원래의 문제가 해결되었는지 검사하고, 해결되지 않았다면 선택 절차로 돌아가 위의 과정을 반복합니다.

  const POS = [500, 100, 50, 10, 5, 1];

  for (let i = 0; i < POS.length; i++) {
    const quotient = parseInt(k / POS[i]); // ! 레퍼런스 코드에선 Math.floor
    // 해당 동전을 사용한 수 만큼 numOfCoins에 추가한다
    numOfCoins += quotient;
    // 거스름돈에 대해 사용한 동전의 나머지 금액을 재할당
    k = k % POS[i]; // ! 레퍼런스 코드에선 k -= quotient * POS[i]
    // 거스름돈이 0이하로 떨어졌을 경우 반복문을 끝낸다.
    if (k === 0) {
      break;
    }
  }

  return numOfCoins;
}
```

---

# <span style="font-size:20px;color:DodgerBlue">3</span>

# 키포인트

- 레퍼런스 코드와의 차이 두 가지를 이해해야 한다.

---
