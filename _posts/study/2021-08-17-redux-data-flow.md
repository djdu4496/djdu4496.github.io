---
layout: post
title: "Redux 데이터 흐름"
subtitle: "redux 구성요소(action, reducer, store, view)들의 data flow"
date: 2021-08-17 01:58:51 +0900
categories: study
tags: react
comments: true
published: true
---

- 목차
  - [1.질문](#1.질문)
  - [2.답](#2.답)
  - [3.caseStudy](#3.caseStudy)

# 1. 질문

Redux에서 구성요소(`action`, `reducer`, `store`, `view` 등..) 들의 데이터 흐름이 어떤 순서로 이루어지는 지 이해하고 있나요?

# 2. 답

1. `view`를 통해 `action`이 일어나게 되면, `action`은 `dispatch`메소드를 통해서 `reducer`로 전달된다

2. `reducer`는 새로운 상태(`new state`)를 만들어내서 `store`를 업데이트한다.

3. 업데이트된 상태(`new state`)는 `view`를 렌더링(`render`)한다
   
4. 이렇게 `redux`는 `data`가 <span style="color:indianred">단방향</span>으로 흐르는 구조다
   <br/>

![redux-flow](/assets/img/flow2.png)

# 3. Case study

0. `view`에 상태(`state`)를 바꾸는 `Action`을 `trigger`하는 버튼(`button`)이 있다고 하자
1. `view`에서 `+`버튼을 누르면(`event`를 발생시키면), `Action`객체가 만들어진다
2. `Action`은 `dispatch` 메소드의 전달인자로 담겨서 `Reducer`에게 전달된다.
3. `dispatch` 메소드는 `Reducer`를 호출한다
4. `Reducer`는 해당 `Action`의 `type`에 따라 `switch문`에서 분기한다
5. 분기를 한 결과, 새로운 주소값을 가진 상태(`new state`)를 만들어서, 그 상태를 다시 `UI`(`view`)에 업데이트한다
   <br/>

![redux-flow](/assets/img/redux-flow.png)
