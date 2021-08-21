---
layout: post
title: "Redux"
subtitle: "상태 관리"
date: 2021-08-13 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [Sprint Review](#12)
    - [1. Class component로 작성된 리액트 앱을 React hooks와 Redux를 이용해서 리팩토링할 수 있나요?](#1)
    - [2. Redux를 통한 상태관리의 장점을 이해하고 있나요?](#2)
    - [3. Redux의 구성요소(action, reducer, store, view 등..)들의 데이터 흐름이 어떤 순서로 이루어지는 지 이해하고 있나요?](#3)
    - [4. Reducer의 주요 규칙을 이해하고 immutable 한 방식으로 state를 변경하는 이유를 이해하고 있나요?](#4)
    - [5. Redux의 3가지 원칙에 대해 이해하셨나요?](#5)

# <span style="font-size:20px;color:gray">주요 개념</span>

- [주요개념](#주요개념)

# <span style="font-size:20px;color:gray">pure redux package</span>

- [pure redux package](#pure-redux-package)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:gray">Class component로 작성된 리액트 앱을 React hooks와 Redux를 이용해서 리팩토링할 수 있나요?</span>
<br>

## <span style="font-size:20px;color:black">React Hooks</span>

class 컴포넌트는 `state`와 `life-cycle`을 가질 수 있었지만,
functional 컴포넌트는 그렇지 못했다.<br>
functional component에서 state, life-cycle를 흉내내서 가질 수 있는 방법이 `React hooks`이다.

- useState 메소드를 통해 'state'를 가질 수 있다
- useEffect 메소드를 통해 'life-cycle-API'를 가질 수 있다

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">Redux를 통한 상태관리의 장점을 이해하고 있나요?</span>
<br>

1. 전역 상태 관리에 용이하다
   - 부모 컴포넌트에서 전역 상태를 'props'로 내려받을 때, 컴포넌트들이 많다면 관리가 어렵게 된다
   - Redux에선 컴포넌트 구조가 복잡하더라도, `useSelector`를 사용하여 `store`에서 상태를 가져올 수 있기 때문에, 전역 상태가 관리가 용이하다
2. 테스트 붙이기 용이하다

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">Redux의 구성요소(action, reducer, store, view 등..)들의 데이터 흐름이 어떤 순서로 이루어지는 지 이해하고 있나요?</span>
<br>

1. `view`를 통해 `action`이 일어나게 되면, `action`은 `dispatch`메소드를 통해서 `reducer`로 전달된다

2. `reducer`는 새로운 상태(`new state`)를 만들어내서 `store`를 업데이트한다.

3. 업데이트된 상태(`new state`)는 `view`를 렌더링(`render`)한다
   
4. 이렇게 `redux`는 `data`가 <span style="color:indianred">단방향</span>으로 흐르는 구조다
   <br/>

![redux-flow](/assets/img/flow2.png)

## <span style="font-size:20px;color:black">Case study</span>

0. `view`에 상태(`state`)를 바꾸는 `Action`을 `trigger`하는 버튼(`button`)이 있다고 하자
1. `view`에서 `+`버튼을 누르면(`event`를 발생시키면), `Action`객체가 만들어진다
2. `Action`은 `dispatch` 메소드의 전달인자로 담겨서 `Reducer`에게 전달된다.
3. `dispatch` 메소드는 `Reducer`를 호출한다
4. `Reducer`는 해당 `Action`의 `type`에 따라 `switch문`에서 분기한다
5. 분기를 한 결과, 새로운 주소값을 가진 상태(`new state`)를 만들어서, 그 상태를 다시 `UI`(`view`)에 업데이트한다
   <br/>

![redux-flow](/assets/img/redux-flow.png)

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">Reducer의 주요 규칙을 이해하고 immutable 한 방식으로 state를 변경하는 이유를 이해하고 있나요?</span>
<br>

- `mutable`하게 기존 state를 고치게 되면, 기존 state가 어땠는지에 대한 트래킹이 불가능해진다
- 따라서, 기존 state들을 트래킹하고, 로그를 확인할 수 있도록 `immutable`한 방식으로 state를 변경해야 한다

## <span style="font-size:20px;color:black"> virtual DOM</span>

- 리액트는 실제 DOM의 바뀐 값을 랜더링하기 전에 virtual DOM에서 전체를 랜더한다.
- 그 랜더를 토대로 이전 상태와 지금 상태의 바뀐 부분을 비교해서 실제 DOM에 그 바뀐 부분만 랜더링해준다.
  - 전체를 리랜더하지 않는다

[출처 유튜브](https://youtu.be/BYbgopx44vo)

- shallow equality checking을 위해 궁극적으로 데이터 핸들링을 안전하게 만들어준다
- 시간 여행 디버깅을 위해선 `reducer`가 순수함수로 만들어져서 `side effect`가 없어야 한다.
- 그래야 각각 다른 state들간 이동이 가능해진다
  [redux-공식문서](https://redux.js.org/faq/immutable-data#why-is-immutability-required-by-redux)

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">Redux의 3가지 원칙에 대해 이해하셨나요?</span>
<br>

1. `Single source of truth`

   - 동일한 데이터는 항상 같은 곳에서 데이터를 가지고 온다
   - 데이터를 저장하는 Store라는 하나 뿐인 공간이 있다

2. `State is read-only`
   - Redux에서는 Action 객체를 통해서 state를 변경할 수 있다.
   - React에서도 setState 메소드를 사용해야만 state 변경이 가능했다
3. `Changes are made with pure functions`
   - 변경은 순수함수(Reducer)로만 가능하다
   - Reducer와 연결되는 개념이다

- 위 세 가지 개념을 `Store`, `Action`, `Reducer` 와 결부시켜 공부하자

# <span style="font-size:20px;color:gray">주요개념</span>

## <span style="font-size:20px;color:black">Store</span>

상태가 관리되는 오직 하나의 공간

## <span style="font-size:20px;color:black">Action</span>

어플리케이션 데이터를 `Store`에 운반하는 자바스크립트 객체

## <span style="font-size:20px;color:black">Dispatch</span>

`Action` 객체는 `Dispatch 메소드`에 인자(`parameter`)로 전달되고,
`Dispatch`는 `Reducer`를 호출해서 새로운 상태(`new state`)를 만들어낸다`

## <span style="font-size:20px;color:black">Reducer</span>

현재 상태(`new state`)와 `Action` 객체를 이용해 새로운 상태(`new state`)를 만들어내는 순수함수(`pure function`)

# <span style="font-size:20px;color:gray">pure redux package</span>

- 블로그 서비스 데이터에 대한 상태 관리 구현 코드

```javascript
const { createStore } = require("redux");
// 초기 state 정의
const initState = {
  name: "이원구",
  posts: [],
};

// action
const changeName = (name) => {
  return {
    type: "CHANGE_NAME",
    name,
  };
};

const addPost = (post) => {
  return {
    type: "ADD_POST",
    post,
  };
};
// reducer => pure functiin
const reducer = (prevState, action) => {
  switch (action.type) {
    case "CHANGE_NAME":
      return {
        ...prevState, // 기존 데이터 copy & paste
        name: action.name, // name만 바꾼다
      };
    case "ADD_POST":
      return {
        ...prevState,
        posts: [...prevState.posts, action.post],
      };
    default:
      return prevState;
  }
};

// store
const store = createStore(reducer, initState);

console.log("현재 state: ", store.getState());
store.dispatch(changeName("정지우"));
console.log("새로운 state: ", store.getState());
store.dispatch(addPost("1"));
store.dispatch(addPost("2"));
console.log("새로운 state: ", store.getState());

/* Terminal(node index.js)
 * 현재 state:  { name: '이원구', posts: [] }
 * 새로운 state:  { name: '정지우', posts: [] }
 * 새로운 state:  { name: '정지우', posts: [ '1', '2' ] }
 */
```
