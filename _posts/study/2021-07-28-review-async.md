---
layout: post
title: "Asynchronous JavaScript"
subtitle: "async-javascript"
date: 2021-07-28 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [Sprint Review](#12)
    - [1. blocking 과 non-blocking을 설명할 수 있나요?](#1)
    - [2. 중첩된 callback이 발생하는 사례를 이해하고 있나요?](#2)
    - [3. 여러개의 비동기 함수가 존재할 때 Promise를 이용해 함수 실행 순서를 자유자재로 프로그래밍할 수 있나요?](#3)
    - [4. Promise의 세가지 상태를 이해하셨나요?](#4)
    - [5. Promise.all 의 사용법을 이해하셨나요?](#5)
    - [6. 어떤 종류의 함수에 await 키워드를 사용할 수 있는지 알고 있나요?](#6)
    - [7. 해당 도메인 지식(예를 들어, 파일/디렉토리에 대한 개념)이 있다면 node.js 공식 문서를 읽고 문제를 해결할 수 있나요?](#7)
    - [8. map, filter, reduce의 사용법에 대해서 알고 있고, 이게 Higher Order Function이라는 것을 이해하고 있다.](#7)
    - [9. callback 함수라는 용어와 활용법에 대해서 이해하셨나요?](#7)
    - [10. underbar 문제를 푸는데 필요한 개념을 모두 이해하셨다고 생각하시나요?](#7)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">blocking 과 non-blocking을 설명할 수 있나요?</span>
<br>
'blocking'이란 하나의 작업이 끝날 때까지, 다음 작업의 시작되는 것을 막는 성질입니다. `non-blocking`은 <span style="color:indianred">비동기 등 다른 작업으로 인해 자바스크립트가 작업의 통제권을 뺏기지 않는 자바스크립트의 성질</span>입니다.

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">중첩된 callback이 발생하는 사례를 이해하고 있나요?</span>
<br>
자바스크립트에서 비동기로 작업을 할 경우, 그 작업들의 순서를 제어할 수 없다. 이때, 순서를 제어하기 위해 필요한 것이 `콜백함수`다. 그러나, 순서를 제어해야 할 비동기 작업들의 양이 많아질 경우, 중첩된 callback이 발생하게 된다.

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">여러개의 비동기 함수가 존재할 때 Promise를 이용해 함수 실행 순서를 자유자재로 프로그래밍할 수 있나요?</span>
<br>

Promise를 사용하여 오래 걸리는 작업(비동기)을 미리 시켜두고, 작업(비동기) 결과를 나중에 확인할 것을 약속한다

- promise 탄생 배경

시간이 오래 걸리는 작업에 대해 `비동기`로 작업을 처리하려 했더니,
Javascript 로직에서 `setTimeout(() => {}, 3000)`에 있는 콜백함수(`() => {}`)를 리턴하는 것이 불가능해지는 문제가 생겼다.
그래서 return 가능한 `promise` 객체가 필요지게 되었다.

- 사용 이유

<span style="color:indianred">비동기적 작업 구현할 때, 동기적 작업처럼 작업의 결과를 기다려줘야 할 경우 Promise를 </span>사용합니다.
기다리지 않고, 바로 작업의 결과를 확인한다면 undefined가 뜨기 때문입니다. <br>

- 사용 방법

Promise는 이전 비동기 작업을 이미 다 실행을 해놓고, 결과값을 잘 가지고 있다가, `then 메서드`로 실행을 시켰을 때 비로소 결과값을 사용한다.
![](/assets/img/promise.png)

```javascript
function readStringAsync(str) {
  return new Promise((resolve, reject) => {
    try {
      setTimeout(() => {
        resolve(str); // 시간이 지나고 나서 fulfilled가 되면, 이 친구가 fulfilled 상태로 나옴
      }, 3000); // then()
    } catch (e) {
      reject("error"); // 시간이 지나고 나서 rejected가 되면, 이 친구가 rejected 상태로 나옴
      // catch()
    }
  });
}
const result = readStringAsync("hello world");

console.log(result);
console.log(result);
// result는 Promise 객체({})가 출력되는 것을 알 수 있다.
// 지금 result는 Promise {<pending>} 상태에서, 3초후 Promise {<fulfilled>: 'hello world'}로 이행(fulfilled)된 상태로 바뀐다.
// vscode에서는 상태 변화가 도출되지 않는 모양이다 ㅠ

// ? 우리가 애초에 원했던건 'hello world'라는 문자열이지, Promise 객체가 아니었는데

// ! 문자열 'hello world'를 받으려면 'then()' 메소드를 사용해야 한다.
// ! 약속 : then메소드의 콜백함수의 첫 번째 인자에 '성공한 결과'가 들어와야 한다.

let string = result.then((str) => {
  console.log(str);
});
```

### promise 객체

<span style="color:indianred">작업(`비동기`)의 최종 완료 또는 실패를 나타내는 객체</span>

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">Promise의 세가지 상태를 이해하셨나요?</span>
<br>

1. 대기(`pending`) : 이행하거나 거부되지 않은 초기 상태

2. 이행(`fulfilled`) : 연산이 성공적한 상태(`resolve('성공한 결과')`)

3. 거부(`rejected`) : 연산이 실패한 상태(`reject('에러')`)

- resolve
  `비동기` 작업이 성공한 경우, `성공한 결과`에 해당하는 `Promise` 객체를 전달(
  주어진 값으로 이행하는 Promise 객체를 반환하는 메소드
  `then`메소드를 통해 가져온다
- reject
  `비동기` 작업이 실패한 경우, `실패한 결과`에 해당하는 `error`를 전달(`reject(error)`)
  주어진 이유로 거부하는 Promise 객체를 반환하는 메소드
  `catch`메소드를 통해 가져온다
- then
  Promise 객체를 리턴하고 두 개의 콜백 함수를 인수로 받는 메소드

객체인 `Promise`는 `resolve(성공한 결과)`를 깔끔하게 전달해주지는 못한다.
`문법(syntax)`: `resolve(성공한 결과)`로 작업을 할 경우 ,`then` 메소드를 써야 한다.

- .then(('성공한 결과') => {})
  '성공한 결과'를 `then` 메소드의 첫 번째 콜백함수의 인자로 전달해야 한다.
- catch()
  Promise 객체를 리턴하고 거부되었을 때만 활용되는 메소드
  ![](https://images.velog.io/images/djdu4496/post/36cf1d6f-6823-4f96-acad-c450eb9d7ea4/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-07-26%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.26.19.png)

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">Promise.all 의 사용법을 이해하셨나요?</span>
<br>

- 사용 이유

굳이 끝나는 순서를 제어할 필요가 없을때 사용합니다(배열의 순서는 시작, 종료 시점과 무관)

`.then()`메소드를 사용할 경우, 전의 `Promise`객체가 종료되면 다음 `Promise`객체가 시작된다.
한편, `Promise.all([P1, P2])`에서 사용되는 `Promise`객체들을 <span style="color:indianred"> 시작, 종료 시간 순서와 상관없이 담은 배열을 사용</span>할 수 있는 메서드가 `Promise.all`이다.

```javascript
const readAllUsersChaining = () => {
  // TODO: 여러개의 Promise를 then으로 연결하여 작성합니다
  return getDataFromFilePromise(user1Path, "utf-8").then((data1) => {
    // data1을 잘 받아왔다.
    return getDataFromFilePromise(user2Path, "utf-8").then((data2) => {
      // data2를 잘 받아왔다.
      // 방법 1 return '[' + data1 + data2 + ']'
      //       .then((string) => JSON.parse(string))
      // 방법 2 return `[${data1}, ${data2}]`
      //       .then((string) => JSON.parse(string))
      // 방법 3 return [data1, data2].map((el) => JSON.parse(el))
      return [data1, data2].map((el) => JSON.parse(el));
    });
  });
};
/*
* promise 객체 호출을 따로따로 하면 안 되는 이유
* 1. 비동기 작업이 'readAllUsersChaing'함수가 끝나버리면, 원하는 결과(성공한 결과)가 올 수 없다.
* 2. 비동기 작업의 순서를 제어할 수 없기 때문에, 원하는 형태의 배열을 리턴할 수 없다. 

const readAllUsersChaining = () => {
    // TODO: 여러개의 Promise를 then으로 연결하여 작성합니다
    return getDataFromFilePromise(user1Path, 'utf-8') // 비동기 함수 시작
    .then((data1) => {})
    return getDataFromFilePromise(user2Path, 'utf-8') // 비동기 함수 시작
      .then((data2) => {})
    return [data1, data2].map((el) => JSON.parse(el)) // 비동기: "어? 나 아직 안끝났는데? ㅂㅇ"
                                                      물론 async 키워드를 사용하면 해결된다
  }
*/
```

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">어떤 종류의 함수에 await 키워드를 사용할 수 있는지 알고 있나요?</span>
<br>

- async

`Promise`화된 함수뿐만 아니라`Promise`화되지 않은 함수도
`async`를 통해 강제로 `Promise`를 반환하게 만들 수 있습니다.

- await

'await'은 비동기 함수 안에서 다른 `Promise`들을 기다리게 만들어주는 키워드입니다.
<span style="color:indianred">비동기 함수들의 순서를 제어</span>할 수 있다.

- 사용 이유
  promise 일종이지만, promise 함수 보다, 훨씬 <span style="color:indianred">코드 가독성</span>이 높아진다.

```javascript
function gotoCodestates() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("1. go to codestates");
    }, 100);
  });
}

function gotoCodestates() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("1. go to codestates");
    }, 100);
  });
}

function sitAndCode() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("2. sit and code");
    }, 100);
  });
}

function eatLunch() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("3. eat lunch");
    }, 100);
  });
}

function goToBed() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("4. goToBed");
    }, 100);
  });
}

const result = async () => {
  const one = await gotoCodestates();
  console.log(one);

  const two = await sitAndCode();
  console.log(two);

  const three = await eatLunch();
  console.log(three);

  const four = await goToBed();
  console.log(four);
};

result();
```

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">해당 도메인 지식(예를 들어, 파일/디렉토리에 대한 개념)이 있다면 node.js 공식 문서를 읽고 문제를 해결할 수 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">8</span>

<span style="color:DodgerBlue">map, filter, reduce의 사용법에 대해서 알고 있고, 이게 Higher Order Function이라는 것을 이해하고 있다.</span>
<br>
네

# <span style="font-size:20px;color:DodgerBlue">9</span>

<span style="color:DodgerBlue">callback 함수라는 용어와 활용법에 대해서 이해하셨나요?</span>
<br>
네

# <span style="font-size:20px;color:DodgerBlue">10</span>

<span style="color:DodgerBlue">underbar 문제를 푸는데 필요한 개념을 모두 이해하셨다고 생각하시나요?</span>
<br>
네
