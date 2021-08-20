---
layout: post
title: "Component Design"
subtitle: "component-design"
date: 2021-08-20 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

# Contents

- [Sprint Review](#sprint-review)
  - [1](#1)
  - [2](#2)
  - [3](#3)
  - [4](#4)
  - [5](#5)

---

# <span style="font-size:20px;color:gray">Sprint Review</span>

# <span style="font-size:20px;color:gray">1</span>

<span style="color:gray">Storybook을 활용하면 좋은 이유를 이해하고 활용할 수 있나요?</span>
<br>

storybook은 `컴포넌트 기반 개발을 쉽게 하기 위한 개발 도구`다. 이 도구는 디자이너, PM 분들과의 소통을 원할하게 해준다
코드를 작성하고, 그것을 눈으로 확인하고 동료들과 코드리뷰를 하면, 에러와 문제점을 발견한다.
이때 테스트를 작성하여 코드가 객관적으로 틀렸는지 아닌지 확인한다. 테스트를 작성하는 것은 사실 굉장히 어려운 작업이다.
이때, storybook은 쉽게 컴포넌트 하나(UI)를 유닛 테스트할 수 있게 해준다.

# <span style="font-size:20px;color:gray">2</span>

<span style="color:gray">CSS를 작성하는 방법이 발전된 과정을 이해하고 있나요?</span>
<br>
.

# <span style="font-size:20px;color:gray">3</span>

<span style="color:gray">Styled-Component의 장점을 이해하고 활용할 수 있나요?</span>
<br>

`CSS in JS`기술을 활용하여, `html`, `css`, `javascript`를 `js 파일` 한 컴포넌트에 넣어서 사용할 수 있다.
그 결과, 완벽하게 `컴포넌트로 사고하기`가 가능해졌다.
`CSS in JS`가 잘 구현된 사례가 바로 `Styled-Component`다.
이후, `Styled-Component`가 발전하면서 여러 부가 기능이 생겼다.

# <span style="font-size:20px;color:gray">4</span>

<span style="color:gray">useRef Hook을 어떤 상황에 활용해야 하는지 이해하고 활용할 수 있나요?</span>
<br>
리액트에서는 `DOM 객체`의 주소값에 접근할 수 있는 방법을 제공해주지 않는다.<br>
리액트의 `선언형`이라는 특징 때문이다.<br>
따라서, useRef Hook을 사용하여, `DOM 객체`의 주소값에 접근할 수 있다.<br>
그러나 이는 리액트의 '선언형'에 반하는 것이기 때문에, 사용을 최소화하는 것이 좋다.

# <span style="font-size:20px;color:gray">5</span>

<span style="color:gray">React와 Storybook, Styled-Component를 활용해서 자주 쓰이는 UI 패턴 (Modal, Toggle, Tab 등) 들을 직접 만들어 볼 수 있나요?</span>
<br>
.
