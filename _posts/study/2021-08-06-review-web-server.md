---
layout: post
title: "Web Server"
subtitle: "web-server"
date: 2021-08-06 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>
  - [Sprint Review](#12)
    - [1. mini-node-server의 작동 원리와 코드를 이해하고 있나요?](#1)
    - [2. 서버가 CORS를 허용하기 위한 HTTP 헤더 각각의 목적을 이해하고 있나요?](#2)
    - [3. 라우팅이 무엇인지 이해하고 있나요?](#3)
    - [4. 내장 http 모듈 대신, Express 라이브러리를 사용해서 구현할 수 있나요?](#4)
    - [5. 미들웨어의 개념을 이해하고 있나요?](#5)
    - [6. CORS가 왜 필요한 것인지 이해하고 있나요?](#6)
    - [7. CORS의 작동 원리를 이해하고 있나요?](#7)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">mini-node-server의 작동 원리와 코드를 이해하고 있나요?</span>

1. node http 모듈 사용법
2. 라우팅
3. stream, buffer
4. 요청 관련 주요 속성
5. 응답 관련 주요 메소드
6. cors, cors 관련 헤더

```javascript
const express = require("express"); // express 불러옴
const app = express(); // express 사용
const port = 3000; // 포트 지정
const jsonParser = express.json(); // 바디-파서 불러옴(express에 내장) 미들웨어 예제
const cors = require("cors");

// '미들웨어' 작성 실습
const myLogger = (req, res, next) => {
  console.log("LOGGED");
  next();
};

app.use(myLogger);

// 'jsonparser'를 미들웨어로 app.use()를 이용하여 넣어보자
app.use(jsonParser);
app.use(cors());
// 라우팅에 따른 요청 처리
app.get("/", (req, res) => {
  res.send("Hello, world");
}) /
  // mini-node-server 라우팅
  app.post("/lower", (req, res) => {
    let text = req.body.text;
    res.send(text.toLowerCase());
  });

app.post("/upper", (req, res) => {
  let text = req.body.text;
  res.send(text.toUpperCase());
});

// 3000번 포트에 해당 웹 서버를 열었음
app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">서버가 CORS를 허용하기 위한 HTTP 헤더 각각의 목적을 이해하고 있나요?</span>
<br>

```javascript
const defaultCorsHeaders = {
  'access-control-allow-origin': '*'; // 1
  'access-control-allow-methods': 'GET, POST, PUT, DELETE, OPTIONS'; // 2
  'access-control-allow-headers': 'content-type, accept'; // 3
  'access-control-max-age': 10 // 4
}
```

#### 코드 해석

1. 모든 도메인(`*, wildcard character`)을 허용한다
2. 메소드는 `GET`, `POST`, `PUT`, `DELETE`, `OPTIONS`만 허용한다
3. 헤더에는 `content-type`, `accept`만 쓸 수 있다
4. `preflight request`는 10초까지 허용한다

이러한 조건들을 갖춘 요청(`request`)들은 cross domain에서 자원(`resource`) 요청이 가능하도록 허용된다

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">라우팅이 무엇인지 이해하고 있나요?</span>
<br>

<span style="color:indianred">클라이언트의 요청에 해당하는 메소드와 URL(`Endpoint`)에 따라 서버가 응답하는 방법을 결정하는 것</span>
<br>

라우팅의 기준은 다음과 같습니다.

1. 클라이언트의 요청에 해당하는`메소드`
2. 클라이언트의 요청에 해당하는 `URL`

클라이언트는 특정한 HTTP 요청 메소드(GET, POST 등)나 서버의 특정 URI(또는 경로)로 HTTP 요청을 보냅니다.
각 라우트는 하나 이상의 핸들러 함수를 가질 수 있으며, 이러한 함수는 라우트가 일치할 때 실행됩니다.

라우트 구조는 다음과 같습니다. <br>

```javasciprt
app.METHOD(PATH, HANDLER)
```

- app - <span style="color:indianred">express의 인스턴스</span>
- METHOD - HTTP 요청 메소드
- PATH - <span style="color:indianred">서버에서의 경로</span>
- HANDLER - <span style="color:indianred">라우트가 일치할 때 실행되는 함수</span>

[출처: express '기본 라우팅'](https://expressjs.com/ko/starter/basic-routing.html) <br>

express 라이브러리를 사용하지 않고, 순수한 node.js 코드로 라우팅을 작성하면 이렇습니다.

```javascript
const requestHandler = (req, res) => {
  if (req.url === "/lower") {
    if (req.method === "GET") {
      res.end(data);
    } else if (req.method === "POST") {
      req.on("data", (req, res) => {
        // do something ...
      });
    }
  }
};
```

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">내장 http 모듈 대신, Express 라이브러리를 사용해서 구현할 수 있나요?</span>
<br>

1. [teminal] `mkdir EXPRESS-DEMO`, `cd EXPRESS-DEMO`
2. [teminal] `npm init` - 새로운 npm 프로젝트, npm 패키지(`package.json`)를 만든다
3. [teminal] `npm install express` - 'express'를 설치한다(`package.json/dependencies`)
4. [teminal] `node app.js` - 'Hello, world' 실행
5. 같은 방식으로, Express 라이브러리로 'mini-node-server'를 구현할 수 있다

```javascript
// app.js 파일 생성후 소스 코드를 작성한 다음, Hello, world를 실행한다
// Hello, world 실행 코드
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">미들웨어의 개념을 이해하고 있나요?</span>
<br>

미들웨어는 <span style="color:indianred">요청과 응답 사이에 추가된 하나의 중간 과정(프로그램)</span>입니다.<br> <br> 미들웨어는 크게 두 가지로 나눌 수 있습니다. `어플리케이션 레벨 미들웨어`와 `라우팅 레벨 미들웨어`입니다.<br> 전자는, 모든 요청에 반드시 이 미들웨어가 포함되길 원하는 경우에 사용합니다. 후자는, 특정 라우팅에 한하여 포함할 경우입니다.

- 어플리케이션 레벨 미들웨어 예시 코드

```javascript
// 어플리케이션 레벨 미들웨어
const express = require("express");
const app = express();

const myLogger = function (req, res, next) {
  console.log("LOGGED"); // 이 부분을 req, res 객체를 이용해 고치면, 여러분들은 모든 요청에 대한 로그를 찍을 수 있습니다.
  next();
};

app.use(myLogger); // 모든 요청에 동일한 미들웨어를 적용하기 위해 app.use 메소드를 사용

// 생략
```

- 라우팅 레벨 미들웨어 예시 코드

```javascript
// 라우팅 레벨 미들웨어
const express = require("express");
const jsonParser = expess.json();
// jsonParser는 express 내장 메소드다
// parsing을 해주지 않으면 req.body가 'undefined'로 출력된다

// 생략

app.post("/api/users", jsonParser, function (req, res) {
  // 특정 라우팅과 관련해서만 미들웨어를 적용하기 위해 사용
  // req.body에는 JSON의 형태로 payload가 담겨져 있습니다.
});
```

<br> 미들웨어를 사용하는 상황은 다음과 같습니다.

**A.** 모든 요청에 대해 url이나 메소드를 확인할 때

**B.** POST 요청 등에 포함된 `body(payload)`를 구조화할 때(쉽게 얻어내고자 할 때)`

- `const jsonParser = express.json()`
- `app.use(jsonParser)`

**C.** 모든 요청/응답에 CORS 헤더를 붙여야 할 때

- `const cors = require('cors')`
- `app.use(cors)`

**D.** 요청 헤더에 사용자 인증 정보가 담겨있는지 확인할 때

이중 mini-node-server에서 사용한 예는 `B`, `C`입니다.

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">CORS가 왜 필요한 것인지 이해하고 있나요?</span>
<br>

<span style="color:gray">CORS</span>

CORS는 <span style="color:indianred">같은 origin이 아닌, 다른 origin에서 리소스를 요청하여 사용하는 것</span>입니다. <br>
<span style="color:gray">예전의 클라이언트</span>

예전에는 서버에서 클라이언트 파일을 가지고 있고,
유저가 서버에 요청을 하면 서버에 있던 클라이언트 파일을 유저가 받아가고, 유저는 클라이언트에서 서버와 통신을 하거나 클라이언트 파일에 담겨져있던 데이터를 일방적으로 보는 방식으로 진행을 했습니다.
서버에서 내려주는 클라이언트는 서버에 위해가 되는 행동을 하지 않을 것이다는 믿음이 있었습니다.
origin이 서버에서 나와서 그 서버의 것으로 다시 서버에 요청을 하는 것이기 때문에, origin이 같아서(same origin) 굳이 이 서버는 이 요청을 막을 필요가 없었습니다.
그래서 의심의 여지 없이 통신이 진행이 됐습니다. <br>

<span style="color:gray">최근 웹의 고도화</span>

최근에 웹 어플리케이션이 점점 고도화되면서(`SPA 등`) 이제는 우리 서버에만 요청하는 것이 아니라, 다른 서버의 자원(`resource`)을 필요로 하게 되는 복잡한 웹 어플리케이션이 많아졌습니다.
즉, 이제는 `same origin 요청`이 아니라,
<span style="color:indianred">다른 서버에 있는 자원(`resource`)을 요청하여 사용</span>하기 위해서 <span style="color:indianred">cross origin 요청</span>이 필요하게 되었습니다.

<span style="color:gray">cross origin 요청 제한</span>

기본적으로, <span style="color:indianred">브라우저는</span> 보안상의 이유로 cross origin HTTP 요청을 제한하고 있습니다
내 서버에서 내려준 클라이언트가 아닌데, 우리 서버로의 요청을 개방해놓으면, 서버에 어떤 자원(`resource`)를 생성할지 확인할 수 없기 때문입니다

<span style="color:gray">개발자의 요청</span>

개발자들은 웹 어플리케이션을 보다 더 고도화하기 위해서 브라우저 회사들에게 cross domain 요청을 할 수 있게 해달라고 요청했다

그 결과, <span style="color:indianred">서버가 허용한 범위 내에서 cross origin 요청이 허용</span>됐다.

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">CORS의 작동 원리를 이해하고 있나요?</span>
<br>
네
