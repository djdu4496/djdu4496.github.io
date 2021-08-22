---
layout: post
title: "cmarket-redux-clone-coding"
subtitle: "what I learned newly"
date: 2021-08-22 09:00:00 +0900
categories: etc
tags:
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [나의 지식을 채워줄 정보 부스러기들🍞](#12)
    - [1. npx create-react-app {project name}](#1)
    - [2. '<'Provider'>' 컴포넌트](#2)
    - [3. npm install react-redux](#3)
    - [4. serviceWorker.unregister()](#4)
    - [5. npm install react-router-dom](#5)
    - [6. export default '<'컴포넌트'>'](#6)
    - [7. createStore(reducer, [preloadedState], [enhancer])](#7)
    - [8. import { compose, createStore, applyMiddleware } from 'redux'](#8)
    - [9. combineReducers(reducers)](#9)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">npx create-react-app {project-name}</span>
<br>

리액트 앱을 설치하기 위해 [터미널] 창에서 사용하는 명령어다. 프로젝트 작성을 위해 필요한 패키지들의 목록이 `package.json`, `package-lock.json`에 자세히 나와있다.

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue"> '<'Provider'>' 컴포넌트 </span>
<br>

`<Provider> 컴포넌트`는 모든 하위 컴포넌트에서 `Redux store`에 접근 및 이용 가능하게 만들어준다.

- 사용 예시

```javascript
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";

import { App } from "./App";
import createStore from "./createReduxStore";

const store = createStore();

ReactDOM.render(
  <Provider store={store}> {// 최상위 컴포넌트인 <App /> 컴포넌트를 <Provider> 컴포넌트로 감싸준다. }
    <App />
  </Provider>,
  document.getElementById("root")
);
```

- [출처: Redux 공식 문서](https://react-redux.js.org/api/provider)

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue"> npm install react-redux </span>
<br>

react-redux 패키지를 다운받지 않고 `<Provider>`를 import하면 다음과 같은 에러가 뜹니다.
`Failed to compile`

> ./src/index.js Module not found: Can't resolve 'react-redux' in '/Users/jiwoo/Desktop/code-practice/cmarket-clone-coding/im-sprint-cmarket-redux/src'

`react-redux` 모듈은 `create-react-app`툴에 내장되어있지 않기 때문에 따로 설치해줘야 한다.

- `npm install react-redux`
- [출처: npmjs 사이트](https://www.npmjs.com/package/react-redux)

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue"> serviceWorker.unregister()</span>
<br>

서비스 워커란 브라우저에서 실행되는 스크립트 파일이다. 이 파일에서 직접적으로 DOM을 다뤄서는 안된다. 여기에는 별도 구성 없이 사용할 수 있는 네트워크 관련 기능들이 존재한다. 서비스 워커는 오프라인 경험을 제공하기 위해서 존재한다. 여기에는 푸쉬 알림, 백그라운드 동기화 등이 있다.

리액트에서 서비스 워커를 적절하게 구성할 수 있다면, 네트워크 요청을 가로채서 관리함으로써 다양한 작업등을 할 수 있다. create-react-app을 사용하면 서비스 워커는 SWPrecacheWebpackPlugin를 통해 자동으로 설치된다. 서비스 워커는 네트워크가 새로운 요청을 처리하기 위한 병목현상이 되지않도록 한다.

(...)

- `serviceWorker.unregister()`는 serviceWorker를 사용하지 않는다는 뜻이다.
- 서비스 워커는 HTTPS 프로토콜에서만 실행된다. localhost는 제외.

- [출처: Create React App의 serviceWorker는 무엇일까](https://yceffort.kr/2020/10/service-worker-of-create-react-app)

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue"> npm install react-router-dom</span>
<br>

React SPA는 `React Router`를 이용해서 개발할 수 있습니다. React Router 주요 컴포넌트들과 그들의 역할은 다음과 같습니다. `<BrowserRouter>`는 라우터 역할을 합니다. `<Switch>`, `<Route>`는 경로를 매칭하는 역할을 합니다. 마지막으로 `<Link>`는 경로를 변경하는 역할을 합니다. 이 컴포넌트들을 사용하기 위해서는 React Router 라이브러리에서 따로 불러와야 합니다

- `[terminal]` `npm install react-router-dom` : react-router 라이브러리 설치
- `import {BrowseRouter, Switch, Route, Link} from 'react-router-dom'` : 최상위 컴포넌트로 react-router 컴포넌트 꺼내오기
- 용어 정리

`SPA` : 서버로부터 완전히 새로운 페이지를 불러오는 것이 아니라,
화면을 업데이트하기 위해 필요한 데이터만 서버에서 전달받아 브라우저에서 해당하는 부분만 업데이트하는 방식으로 작동하는 웹 애플리케이션이나 웹 사이트 <br>
`Routing`: 각 주소에 따라 다른 뷰를 보여주는 과정 <br>
`React Router`: React SPA에서는 라우팅을 위해 React Router 라이브러리를 가장 많이 사용합니다 <br>

- 사용 예시

```javascript
<BrowserRouter>
  <div>
  	<nav>
  		<ul>
		  <li>
  		  	<Link to="/">Home</Link>
  		  </li>
		  <li>
		        <Link to="/about">Mypage</Link>
          	  </li>
     	  	  <li>
 	         	<Link to="/dashboard">Dashboard</Link>
          	  </li>
		</ul>
  	</nav>

	<Switch>
    		<Route exact path="/">
    			<Home />
    		</Route>
    		<Route path="/about">
		    	<Mypage />
		</Route>
	        <Route path="/dashboard">
		    	<Dashboard />
                </Route>
        </Switch>

  </div>
<BrowserRouter/>
```

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue"> export default '<'컴포넌트'>'</span>
<br>

react로 코딩을 하다보면 많은 경우에 우리가 쓴 코드를 다른 코드에서 활용하기 위해 import 해오는 경우가 많습니다. 우리가 <span style="color:indianred">다른 파일을 import 해오기 위해선 해당 js 파일에서 export(`내보내기`)를 해주는 것이 중요</span>합니다.<br>

export default는 <span style="color:indianred">변수, 함수, 오브젝트, 클래스 등을 전달할 수 있는 명령어</span>입니다. 이렇게 export 뒤에 default를 붙이게 되면 중괄호 없이 변수 등을 import 해올 수 있습니다.

- 사용 예시

```javascript
const hello = "Hello World!"

export default hello

...

import hello from "경로"
```

- [출처: [TIL] Day 32. export default의 의미에 대해](https://shinejaram.tistory.com/41)

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue"> createStore(reducer, [preloadedState], [enhancer])</span>
<br>

`createStore` : <span style="color:indianred">store를 만들어준다</span>. Reducer들을 store 전달인자로 담아 서로 연결해준다
`preloadedState`: initialstate와 같다
`enhancer` : redux의 기능을 도와주는 미들웨어나 데브 툴즈와 같은 것들

- 사용 예시

```javascript
const hello = "Hello World!"

export default hello

...

import hello from "경로"
```

- [출처: [TIL] Day 32. export default의 의미에 대해](https://shinejaram.tistory.com/41)

# <span style="font-size:20px;color:DodgerBlue">8</span>

<span style="color:DodgerBlue"> import { compose, createStore, applyMiddleware } from 'redux'</span>
<br>

- compose
  compose를 사용해 enhancer를 만들 수 있습니다. compose는 순차적으로 함수를 적용해나가는 gulp의 pipe 같은 역할을 입니다. 미들웨어를 사용할 때 적용해주면 좋습니다.

- applyMiddleware
  dsadad

- [출처: compose(...functions)](https://redux.js.org/api/compose)
- [출처: applyMiddleware(...middleware)](https://redux.js.org/api/applymiddleware)
- [출처: applyMiddleware, compose를 활용하여 enhancer 만들기 사용하기](https://darrengwon.tistory.com/558)
- [출처: ]()

# <span style="font-size:20px;color:DodgerBlue">9</span>

<span style="color:DodgerBlue"> combineReducers(reducers) </span>
<br>
하나 이상의 리듀서들을 함께 관리하기 위한 리듀서

- 사용 예시

```javascript
const rootReducer = combineReducers({potato: potatoReducer, tomato: tomatoReducer})
// This would produce the following state object
{
  potato: {
    // ... potatoes, and other state managed by the potatoReducer ...
  },
  tomato: {
    // ... tomatoes, and other state managed by the tomatoReducer, maybe some nice sauce? ...
  }
}
```

- [출처: combineReducers(reducers)](https://redux.js.org/api/combinereducers)
- [출처: combineReducers(reducers) 번역](https://ko.redux.js.org/recipes/structuring-reducers/using-combinereducers/)
