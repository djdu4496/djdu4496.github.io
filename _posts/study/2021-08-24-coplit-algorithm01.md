---
layout: post
title: "[coplit] Algorithm01"
subtitle: "(movingStuff)"
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

김코딩과 박해커는 사무실 이사를 위해 짐을 미리 싸 둔 뒤, 짐을 넣을 박스를 사왔다. 박스를 사오고 보니 각 이사짐의 무게는 들쭉날쭉한 반면, 박스는 너무 작아서 한번에 최대 2개의 짐 밖에 넣을 수 없었고 무게 제한도 있었다.

예를 들어, 짐의 무게가 `[70kg, 50kg, 80kg, 50kg`]`이고 박스의 무게 제한이 100kg이라면 2번째 짐과 4번째 짐은 같이 넣을 수 있지만 1번째 짐과 3번째 짐의 무게의 합은 150kg이므로 박스의 무게 제한을 초과하여 같이 넣을 수 없다.

박스를 최대한 적게 사용하여 모든 짐을 옮기려고 합니다.

짐의 무게를 담은 배열 stuff와 박스의 무게 제한 limit가 매개변수로 주어질 때, 모든 짐을 옮기기 위해 필요한 박스 개수의 최소값을 return 하도록 movingStuff 함수를 작성하세요.

## 입력

### 인자 1: stuff

- `Number` 타입의 40 이상 240 이하의 자연수를 담은 배열
  - ex) `[70, 50, 80, 50]`

### 인자 2: limited

- `Number` 타입의 40 이상 240 이하의 자연수

## 출력

- `Number` 타입을 리턴해야 합니다.
- 모든 짐을 옮기기 위해 필요한 박스 개수의 최솟값을 숫자로 반환합니다.

## 주의사항

- 옮겨야 할 짐의 개수는 1개 이상 50,000개 이하입니다.
- 박스의 무게 제한은 항상 짐의 무게 중 최대값보다 크게 주어지므로 짐을 나르지 못하는 경우는 없습니다.

## 입출력 예시

```javascript
let output = movingStuff([70, 50, 80, 50], 100);
console.log(output); // 3

let output = movingStuff([60, 80, 120, 90, 130], 140);
console.log(output); // 4
```

---

# <span style="font-size:20px;color:DodgerBlue">2</span>

# 나의 코드

```javascript
// 나의 코드
function movingStuff(stuff, limit) {
  // (짐의 무게(배열), 무게제한(수)) => 모든 짐을 옮기기 위해 필요한 박스 개수의 최소값(수)

  // stuff는 무작위로 정렬
  // 오름차순으로 정렬
  stuff.sort((a, b) => a - b);
  let numOfBoxes = 0;
  while (stuff.length) {
    // 최대값과 최소값을 선언 후 할당
    let min = stuff[0];
    let max = stuff[stuff.length - 1];
    // 최대값과 최소값의 합이 무게제한보다 작거나 같은 경우,
    // 최대값과 최소값을 배열에서 제거
    // 박스 개수를 추가한다
    if (min + max <= limit) {
      stuff.shift();
      stuff.pop();
      numOfBoxes++;
    } else {
      stuff.pop();
      numOfBoxes++;
    }
  }
  return numOfBoxes;
}

// 레퍼런스 코드 따라잡기
// function movingStuff(stuff, limit){
//   // 짐을 두개 담을 수 있는 박스의 개수를 담을 변수 twoStuff 선언 후 0으로 초기화
//   let twoStuff = 0;
//   // 최소값, 최대값을 표현하기 위해 stuff를 오름차순으로 정렬한다.
//   stuff.sort((a, b) => a - b)

//   // 최대값과 최소값의 인덱스를 담을 변수를
//   // 각각 leftIdx, rightIdx으로 선언 후 각각 0, stuff.length - 1을 할당
//   let leftIdx = 0;
//   let rightIdx = stuff.length - 1
//   // leftIdx와 rightIdx가 같아질 때까지 while반복문을 돌린다
//   while(leftIdx < rightIdx){
//   // stuff 배열의 각 인덱스에 해당하는 값들의 합이 제한 무게보다 작거나 같다면,
//   // 왼쪽 인덱스는 1을 더해주고, 오른쪽 인덱스는 1을 빼준다.
//   // 그리고, 두 짐을 한꺼번에 박스에 담았기 때문에, twoStuff에 1을 추가한다.
//     if(stuff[leftIdx] + stuff[rightIdx] <= limit){
//       leftIdx++
//       rightIdx--
//       twoStuff++
//     }
//     else{
//       rightIdx--
//     }
//   }
//   // 모든 짐들이 하나씩 담았을 경우 가방의 개수는 stuff.length이다.
//   // stuff.length에서 twoStuff를 뺀 값이 필요한 박스 개수의 최소값이 된다.
//   return stuff.length - twoStuff

// }
```

---

# <span style="font-size:20px;color:DodgerBlue">3</span>

# 키포인트

- 정렬의 필요성을 이해해야 한다.
- index로 푸는 방법과 값 자체로 푸는 방법의 차이를 이해해야 한다.
- 최소값을 구하는 방식 두 가지를 이해해야 한다.

---
