---
layout: post
title: "HTTP Network(basic)"
subtitle: "http"
date: 2021-07-29 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [Sprint Review](#12)
    - [1. 클라이언트와 서버, api 그리고 http의 역할을 그림을 그려가며 설명할 수 있나요?](#1)
    - [2. 자주 사용하는 웹사이트 등에서 어떤 부분이 AJAX 기술을 사용하고 있는지 알아낼 수 있나요?](#2)
    - [3. AJAX를 구성하고 있는 기반 기술이 무엇인지 나열할 수 있나요?](#3)
    - [4. HTTP GET 요청과 POST 요청의 차이를 이해하고 있나요?](#4)
    - [5. IP 주소와 PORT 에 대해 이해하고, 설명할 수 있나요?](#5)
    - [6. URL과 URI의 차이를 설명할 수 있나요?](#6)
    - [7. Domain name과 IP 주소의 상관관계를 DNS와 함께 설명할 수 있나요?](#7)
    - [8. SSR(Server Side Rendering)과 CSR(Client Side Rendering)의 차이점을 설명할 수 있나요?](#8)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">클라이언트와 서버, api 그리고 http의 역할을 그림을 그려가며 설명할 수 있나요?</span>
<br>

![그림](/assets/img/server.png)

- [A] : 클라이언트
  - 브라우저를 열었을 때 웹사이트에 나오는 창 & UI와 상호작용(클릭, 터치 등)을 할 수 있는 부분
- [B] : 서버
  - 사용자가 볼 수 없지만, 서버에 있는 데이터(상품 정보 등)를 api로 노출시키는 리소스를 프론트엔드로 전달하는 역할
  - 로그인, 로그아웃
  - 권한 관리
  - 사용자 인증, 보아
- [C] : api

## 서버 & 클라이언트

- 클라이언트와 서버가 `어떻게` api를 주고 받을 수 있을까?
  - `http`를 이용합니다. 'http'는 요청(`req`)과 응답(`res`)으로 구성됩니다. 클라이언트가 '요청'을 하고, 서버가 '응답'을 하는 쪽입니다. 클라이언트가 요청을 하지 않으면, 서버는 응답할 수 없습니다.
- 'http'?
  - 'hyper text transfer protocol'. 웹 브라우저와 웹 서버의 소통을 위해 디자인된 프로토콜입니다.
    - 초기 [웹사이트](http://info.cern.ch/hypertext/WWW/TheProject.html)
- `http 메시지`

  - 클라이언트와 서버간에 데이터가 교환되는 방식입니다. 클라이언트는 '요청'을 보낼 때 `http request 메시지`를 보내고, 서버는 '응답'을 보낼 때 `http response 메시지`를 보냅니다.
  - [HTTP 메시지 예시](https://mdn.mozillademos.org/files/13827/HTTPMsgStructure2.png)
    - [출처: HTTP 메시지 mdn](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages#http_%EC%9A%94%EC%B2%AD)

## http

- http 특징

  - 무상태성
    - HTTP는 요청과 응답이 이루어지면, 특정 통신의 상태를 유지하지 않습니다.
      - 사용자의 발자취를 http가 추적하지 않습니다.
    - 확장성 때문입니다.
  - 비연결성
    - HTTP는 요청에 대한 응답을 처리하게 되면 연결을 끊어 버립니다.

- http 종류
  - http, https 등을 사용하고 있다.
  - [출처: 곰돌이 놀이터](https://helloworld-88.tistory.com/146)

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">자주 사용하는 웹사이트 등에서 어떤 부분이 AJAX 기술을 사용하고 있는지 알아낼 수 있나요?</span>
<br>
AJAX는 (Asynchronous Javascript And Xml)의 약자로, <span style="color:indianred">자바스크립트와 XML을 이용한, 비동기적 정보 교환 기법</span>으로, 즉 한마디로 `비동기`라 할 수 있습니다.
XML은 예전에 만들어진, 데이터를 교환하기 위해 만들어진 마크업 언어입니다. 그 데이터들을 비동기적으로 교환하기 위해 자바스크립트를 사용한 기법이 AJAX입니다.

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">AJAX를 구성하고 있는 기반 기술이 무엇인지 나열할 수 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">HTTP GET 요청과 POST 요청의 차이를 이해하고 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">IP 주소와 PORT 에 대해 이해하고, 설명할 수 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">URL과 URI의 차이를 설명할 수 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">Domain name과 IP 주소의 상관관계를 DNS와 함께 설명할 수 있나요?</span>
<br>

# <span style="font-size:20px;color:DodgerBlue">8</span>

<span style="color:DodgerBlue">SSR(Server Side Rendering)과 CSR(Client Side Rendering)의 차이점을 설명할 수 있나요?</span>
<br>
