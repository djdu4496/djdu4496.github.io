---
layout: post
title: "[coplit] Algorithm03"
subtitle: "(boardGame)"
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

`N * N`의 크기를 가진 보드판 위에서 게임을 하려고 합니다. 게임의 룰은 다음과 같습니다.

1. 좌표 왼쪽 상단(0, 0)에 말을 놓는다.
2. 말은 상, 하, 좌, 우로 이동할 수 있고, 플레이어가 조작할 수 있다.
3. 조작의 기회는 딱 한 번 주어진다.
4. 조작할 때 U, D, L, R은 각각 상, 하, 좌, 우를 의미하며 한 줄에 띄어쓰기 없이 써야 한다.
   - 예시: UDDLLRRDRR, RRRRR
5. 한 번 움직일 때마다 한 칸씩 움직이게 되며, 그 칸 안의 요소인 숫자를 획득할 수 있다.
6. 방문한 곳을 또 방문해도 숫자를 획득할 수 있다.
7. 보드 밖을 나간 말은 OUT 처리가 된다.
8. 칸 안의 숫자는 0 또는 1이다.
   - 단, 좌표 왼쪽 상단(0, 0)은 항상 0이다.
9. 획득한 숫자를 합산하여 숫자가 제일 큰 사람이 이기게 된다.

보드판이 담긴 board와 조작하려고 하는 문자열 operation이 주어질 때, 말이 해당 칸을 지나가면서 획득한 숫자의 합을 구하는 함수를 작성하세요.

## 입력

### 인자 1: board

- `number` 타입의 2차원 배열
- 2 <= board.length <= 1,000
- 예: `[ [0, 0, 1], [1, 0, 1], [1, 1, 1] ]`

### 인자 2: operation

- `string` 타입의 대문자 영어가 쓰여진 문자열
- `1 <= operation.length <= board.length \* 2`
- `U, L, D, R` 이외의 문자열은 없습니다.

## 출력

- `Number` 타입을 반환해야 합니다.
  - board와 op eration이 입력값의 예시 (`[ [0, 0, 1], [1, 0, 1], [1, 1, 1] ], DDR)`일 때, `(0, 0) -> (1, 0) -> (2, 0) -> (2, 1)` 순서로 이동하게 되고, 각 `0, 1, 1, 1`을 얻어 `3`을 반환합니다.

## 주의사항

- 만약, 말이 보드 밖으로 나갔다면 즉시 `"OUT"` 을 반환합니다.

## 입출력 예시

```javascript
const board1 = [
  [0, 0, 0, 1],
  [1, 1, 1, 0],
  [1, 1, 0, 0],
  [0, 0, 0, 0],
];
const output1 = boardGame(board1, "RRDLLD");
console.log(output1); // 4

const board2 = [
  [0, 0, 1],
  [1, 1, 1],
  [1, 0, 0],
];
const output2 = boardGame(board2, "UUUDD");
console.log(output2); // 'OUT'

const board3 = [
  [0, 0, 0, 0, 0],
  [0, 0, 1, 0, 0],
  [0, 0, 0, 0, 0],
  [0, 0, 0, 1, 0],
  [0, 0, 0, 0, 0],
];
const output3 = boardGame(board3, "DDRRRUDUDUD");
console.log(output3); // 0
```

---

# <span style="font-size:20px;color:DodgerBlue">2</span>

# 나의 코드

```javascript
function boardGame(board, operation) {
  // (2차원 배열, 조작순서(문자열)) => 말이 해당 칸을 지나가면서 획득한 숫자의 합(수)

  // 경로가 정해지지 않았기 때문에 각 방향에 따른 row, col의 변화를 객체에 저장한다.(순서x)
  const MOVES = {
    U: [-1, 0],
    D: [1, 0],
    L: [0, -1],
    R: [0, 1],
  };

  const N = board.length;

  const isValid = (row, col) => row >= 0 && row < N && col >= 0 && col < N;

  let row = 0;
  let col = 0;

  let score = 0;
  // (0,0)의 값은 무조건 0이기 때문에 고려하지 않아도 된다.
  for (let i = 0; i < operation.length; i++) {
    const move = MOVES[operation[i]];
    const [rd, cd] = move;
    row += rd;
    col += cd;
    if (!isValid(row, col)) return "OUT";
    score += board[row][col];
  }
  return score;
}
```

---

# <span style="font-size:20px;color:DodgerBlue">3</span>

# 키포인트

- 알고리즘 코플릿 3번 문제(`03_[구현] 보드 게임`)과의 유사성을 파악할 수 있다.
- `Look Up Table`의 개념을 이해할 수 있다.

---
