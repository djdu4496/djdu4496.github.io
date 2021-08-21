---
layout: post
title: "React Data Flow & Effect Hook"
subtitle: "react"
date: 2021-08-03 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [Sprint Review](#12)
    - [1. 공식 문서 React로 사고하기 문서에서 이해한 항목을 전부 선택하세요.](#1)
    - [2. React의 데이터 흐름을 한마디로 설명할 수 있나요?](#2)
    - [3. 두 컴포넌트가 하나의 상태를 사용하고 있을 때, 어디에 상태가 위치해야 하는지 알고 있나요?](#3)
    - [4. 어떤 함수에 Side Effect가 있는 경우, 순수 함수로 불릴 수 없는 이유를 알고 있나요?](#4)
    - [5. 언제 useEffect로 설정한 Effect Hook 함수가 실행되는 지 세가지 사례를 알고 있나요?](#5)
    - [6. 만일, 컴포넌트가 생성될 때 단 한번만 AJAX 요청을 해야 한다면, useEffect를 어떻게 사용해야 하는지 알고 있나요?](#6)
    - [7. Effect Hook을 사용할 때의 주의해야 할 내용을 이해하고 있나요?](#7)
    - [8. API문서를 참고하고, fetch를 이용해서 AJAX 요청을 보낼 수 있나요?](#8)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">공식 문서 React로 사고하기 문서에서 이해한 항목을 전부 선택하세요.</span>
<br>

1.  ✅ [1단계]UI를 컴포넌트 계층 구조로 나누기

2.  ❎ [2단계]React로 정적인 버전 만들기

3.  ❎ [3단계] UI state에 대한 최소한의 (하지만 완전한) 표현 찾아내기

4.  ✅ [4단계]State가 어디에 있어야 할 지 찾기

5.  ❎ [5단계]역방향 데이터 흐름 추가하기

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">React의 데이터 흐름을 한마디로 설명할 수 있나요?</span>
<br>

React의 데이터는 `단방향`으로, 위에서 아래로 흐릅니다.

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">두 컴포넌트가 하나의 상태를 사용하고 있을 때, 어디에 상태가 위치해야 하는지 알고 있나요?</span>
<br>

두 컴포넌트가 하나의 상태를 공유할 땐, `부모 컴포넌트`에 상태가 위치해야 합니다.

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">어떤 함수에 Side Effect가 있는 경우, 순수 함수로 불릴 수 없는 이유를 알고 있나요?</span>
<br>

`순수함수`는 <span style="color:indianred">오직 함수의 입력만이 함수의 결과에 영향을 주는 함수</span>를 뜻합니다.
함수의 입력이 아닌 다른 값이 함수의 결과에 영향을 미치는 경우 순수 함수라 부를 수 없습니다.

- `Math.random()`은 순수함수가 될 수 없습니다.
  - 함수를 호출했을 때 응답을 예측할 수 없기 때문입니다. <br>
- `fetch API를 이용해 AJAX요청을 하는 경우`도 순수함수가 아닙니다.
  - 네트워크 상황이나 서버 상태에 따라 응답이 달라지기 때문입니다. <br> <br>

함수가 `side effect`가 있을 경우에도, 순수 함수라 할 수 없습니다. side effect는 <span style="color:indianred">함수 내에서 어떤 구현이 함수 외부에 영향을 미치는 경우</span>를 말합니다.

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">언제 useEffect로 설정한 Effect Hook 함수가 실행되는 지 세가지 사례를 알고 있나요?</span>
<br>
함수 컴포넌트는 props가 입력으로, JSX 요소가 출력으로 나가기 때문에, 순수함수입니다.
하지만 리액트를 작성할 때, `AJAX 요청`이 필요하거나, LocalStorage 또는 타이머와 같은 `React와 상관없는 API`를 사용하는 경우가 많습니다. 이는 React의 입장에서는 전부 Side Effect 입니다. React는 Side Effect를 다루기 위한 Hook인 Effect Hook을 제공합니다.
<br>

1. 컴포넌트 생성 후 `처음` 화면에 렌더링(표시)될 때
2. 컴포넌트에 `새로운 props가 전달`되며 리렌더링될 때
3. 컴포넌트에 `상태(state)가 바뀌며` 리렌더링될 때

매 번 새롭게 컴포넌트가 렌더링될 때, 실행되는 `side effect`를 `useEffect`에 넣어주면 이를 편하게 관리할 수 있습니다.

- [(예제) 명언을 보여주는 간단한 애플리케이션](https://codesandbox.io/s/useeffect-1-lj4p9?from-embed)
  - 이 컴포넌트에서 실행하는 Side effect는 `브라우저 API를 이용하여, 타이틀을 변경하는 것`입니다

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">만일, 컴포넌트가 생성될 때 단 한번만 AJAX 요청을 해야 한다면, useEffect를 어떻게 사용해야 하는지 알고 있나요?</span>
<br>
'side effect'는 useEffect의 첫 번째 인자에 들어가는 콜백함수안에 넣어줍니다. 그리고 두 번째 인자에는 `종속성 배열`이 들어갑니다. '종속성 배열'은 변경이 일어나는 상태(`status`)들이 들어있습니다. <br>
컴포넌트가 생성될 때 단 한번만 AJAX 요청을 해야 할 경우엔, 빈 배열(`[]`)을 useEffect의 두 번째 인자로 사용하면, 컴포넌트가 처음 생성될때만 effect 함수가 실행됩니다. <br>
이와 달리, 두 번째 인자를 아예 안넘기는 긴다면(`useEffect(effect 함수)`), 컴포넌트가 처음 생성되거나, props가 업데이트되거나, 상태(state)가 업데이트될 때 effect 함수가 실행됩니다(`기본형`)

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">Effect Hook을 사용할 때의 주의해야 할 내용을 이해하고 있나요?</span>
<br>

1. 최상위에서만 Hook을 호출해야 합니다.
   - 반복문, 조건문 혹은 중첩된 함수 내에서 Hook을 호출하지 마세요.
   - `App.js`와 같이 최상위 함수 컴포넌트에서만 Hook을 호출합니다.
2. React 함수 내에서 Hook을 호출합니다.ㅠ
   - Hook을 일반적인 JavaScript 함수에서 호출하지 마세요.
     - `handleClick 함수` 안에서 호출하지 마세요.
3. [공식 문서](https://ko.reactjs.org/docs/hooks-rules.html#only-call-hooks-at-the-top-level)를 통해 이 내용에 대해 더 공부하세요.

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">API문서를 참고하고, fetch를 이용해서 AJAX 요청을 보낼 수 있나요?</span>
<br>

우선, 서버API에 접근을 해야 한다. 서버에 접근하는 방법은 여러 가지가 있다. <br>

1. 브라우저 주소창에 endpoint 주소 입력
2. [Terminal] `curl {endpoint 주소}`
3. postman 이용
4. fetch API 활용 <br>

이번 스프린트에선 항공편을 조회하기 위해 `fetch API`를 사용해야 한다. <br>
우선, `/flight`url에 대해 `GET` 요청을 하기 위해 다음과 같이 코드를 작성한다.

```javascript
`서버 api home address/flight?`;
```

그리고, 출발지가 '인천', 도착지가 '제주'이기 때문에 다음과 같이 파라미터(`query string parameters`)를 추가한다. <br>
그 url 주소를 변수 `url`에 담는다.

```javascript
const url = `서버 api 홈 주소/flight?departure=${인천을 가리키는 변수}&destination=${제주를 가리키는 변수}`
```

fetch 메소드에 url을 전달인자로 담는다. 그 실행값을 then으로 받아 json화해서 리턴한다.

```javascript
...
return fetch(url).then((data) => data.json())
```

[json처리 mdn](https://developer.mozilla.org/en-US/docs/Web/API/Response/json)
