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
XML은 예전에 만들어진, 데이터를 교환하기 위해 만들어진 마크업 언어입니다. 그 데이터들을 비동기적으로 교환하기 위해 자바스크립트를 사용한 기법이 AJAX입니다. 즉, 페이지 전체를 갱신하는 것이 아니라, 필요한 데이터만 받아서 갱신하는 기법입니다.

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">AJAX를 구성하고 있는 기반 기술이 무엇인지 나열할 수 있나요?</span>
<br>

일단, 정적 웹페이지를 구성하는 `HTML`, `CSS`가 있습니다. 그리고, 'DOM'모델을 사용하여 이러한 정적 웹페이지를 `javascript`로 조작합니다. 마지막으로, 데이터의 교환을 위한 `JSON`으로 기술이 구성됩니다.

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">HTTP GET 요청과 POST 요청의 차이를 이해하고 있나요?</span>
<br>

GET(Read) 요청은 <span style="color:indianred">정보를 조회</span>하는 것, POST(Create)는 <span style="color:indianred">서버에게 전달하고자 하는 정보를 보내는 것</span>입니다.
이외에, `PUT`(Update), `PATCH`(Update), `DELETE`(Delete), `OPTIONS`이 있습니다.

- [출처: HTTP request methods](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">IP 주소와 PORT 에 대해 이해하고, 설명할 수 있나요?</span>
<br>

'IP 주소'는 Internet Protocol Address의 약자로, <span style="color:indianred">네트워크에 연결된 특정 PC를 나타내는 주소를 체계</span>입니다. `IPv4`는 인터넷에 연결된 모든 PC는 IP 주소 체계에 따라 4개 덩어리의 숫자로 구분됩니다. 그 숫자는 0부터 255까지 있습니다. 그러나 컴퓨터가 보편화되면서 'IPv4'의 경우의 수보다 많이 컴퓨터가 많아지면서 `IPv6`가 나왔다. 'IPv6'은 6개 덩어리의 숫자로 구분됩니다.

- 알아두어야 할 IP 주소
  - `127.0.0.1` : 현재 사용중인 로컬 PC 주소
  - `localhost` : 현재 사용중인 로컬 PC 주소
  - `255.255.255.255`: 브로드캐스트 주소
    <br>

'PORT'는 네트워크로 연결하는 통로입니다. 대부분의 PC는 여러 개의 프로그램을 동시에 실행시킵니다. 이때, 각각 어플리케이션이 서로 충돌하지 않도록 만듭니다.

요컨대, IP 주소는 PC를 찾을 때 필요한 주소를 나타내고, PORT는 PC안에서 프로그램을 찾을 때 사용합니다.

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">URL과 URI의 차이를 설명할 수 있나요?</span>
<br>
URL(URI) 는 브라우저 주소창에 있는 주소를 가리킵니다. <span style="color:indianred">서버가 제공되는 환경에 존재하는 파일이 위치한 정보</span>을 의미합니다. <br>
URL은 Uniform Resource Locater의 약자로, <span style="color:indianred">파일이 위치한 경로를 순차적으로 나타낸 것</span>입니다. URI는 Uniform Resource Identifier의 약자로, <span style="color:indianred">URL에서 요청의 범위를 좁히기 위한 쿼리 등의 질문 식별자</span>입니다. URI는 URL의 상위개념입니다.

- `query`는 웹서버에서 보내는 추가적인 질문입니다.

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">Domain name과 IP 주소의 상관관계를 DNS와 함께 설명할 수 있나요?</span>
<br>

한눈에 파악하기 힘든 IP 주소(`232.211.22.422`)를 보다 분명하게 나타내기 위해 `www.naver.com`과 같은 '도메인'이 등장합니다.
`호스트 서버`는 인터넷 회선이 연결된 컴퓨터라서 IP 주소가 할당되어 있습니다. 서버에 할당되어 있는 IP 주소가 실제 웹사이트 주소라 할 수 있습니다.
DNS 서버는 <span style="color:indianred">IP 주소를 특정 도메인 주소와 같다는 기록을 저장해주고, 사용자들이 도메인 주소를 검색했을 때, IP 주소로 연결해줍니다</span>. <br>
브라우저 검색창에 도메인을 입력해서 해당 사이트에 이동하기 위해선 매칭하는 작업이 반드시 필요합니다. 컴퓨터는 0,1밖에 모르기 때문에 인간친화적으로 만들어진 도메인 주소를 해석할 수 없습니다. 네트워크에는 도메인을 위한 서버가 별도로 존재합니다. 그것이 'DNS'입니다. 사용자가 도메인 주소 또는 IP주소를 요청하면, Domain Name Server는 IP 주소 또는 도메인 주소를 찾아서 해당 웹 서버로 요청을 전달합니다. 이러한 시스템을 Domain Name System이라 합니다.

- [출처: DNS란 뭐고, 네임서버란 뭔지 개념정리](https://gentlysallim.com/dns%EB%9E%80-%EB%AD%90%EA%B3%A0-%EB%84%A4%EC%9E%84%EC%84%9C%EB%B2%84%EB%9E%80-%EB%AD%94%EC%A7%80-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC/)

<span style="font-size:20px;color:DodgerBlue">8</span>

<span style="color:DodgerBlue">SSR(Server Side Rendering)과 CSR(Client Side Rendering)의 차이점을 설명할 수 있나요?</span>
<br>

## SSR vs CSR

`브라우저 관점`

### 차이점

<span style="color:indianred">서버에 데이터를 요청했을 때 HTML 파일이 조작되는 위치</span>

### SSR

서버가 서버에 저장되어있던 html 파일 전체를 클라이언트에 제공한다

#### 장점

1. (CSR에 비해) 초기 랜딩 속도가 빠르다
2. 검색 엔진 최적화(`SEO`)가 가능하다

#### 단점

1. 페이지를 요청할 때마다 새로고침이 된다
2. 요청이 많아지면 서버에 부담된다

### CSR

#### 장점

1. 초기 요청을 제외하면 페이지 랜딩 속도가 빠르다
2. 서버에 부담이 적다
3. 사용자 경험(`UX`)이 좋다

#### 단점

1. 최초 로딩 속도가 느리다
2. 검색 엔진 최적화(`SEO`)에 불리하다
   서버로부터 필요한 데이터만 받아서 화면의 일부만 변경할 수 있다
   SSR처럼 매번 서버로부터 html 파일 전체를 받아올 필요가 없어졌다
   브라우저는 처음에만 html 파일 전체를 받는다
   이후, 그 html 파일에서 필요한 부분만 데이터를 서버에서 받아온 다음 적용해준다

## 동적 웹사이트 vs 정적 웹사이트

`서버 관점`

### 동적 웹사이트

서버는 실시간으로 HTML 파일을 만들어서 응답해준다

- 사용자의 상황, 시간, 요청 등에 따라서 다른 HTML 파일을 서버에서 실시간으로 제작해서 전달해준다

### 정적 웹사이트

서버는 이미 완성된 HTML, JavaScript 파일들을 전달하기만 한다

- 이때 사용자는 서버의 데이터 자체가 변경되지 않는 한, 고정된 웹페이지를 보게 된다

### 참조 링크

[Static vs Dynamic Websites - What's the Difference?](https://www.youtube.com/watch?v=_wFJj94kSTU&t=664s)

## 검색 엔진 최적화(`SEO`)

### 정의

<span style="color:red">웹사이트가 검색 결과에 더 잘 보이도록 최적화하는 과정</span>

### SSR이 CSR보다 `SEO`에 유리한 이유

이미 서버에서 html 파일을 저장하고 있다가, 단순하게 보내주기만 하면 되기 때문에, 검색 사이트가 그것을 가져오기만 하면 된다
반면 정적 웹사이트는 html을 브라우저에서 랜더링하기 때문에 SEO하기가 어렵다

![출처:codestates](/assets/img/ssrcsr.png)
