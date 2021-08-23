---
layout: post
title: "Linux"
subtitle: "linux"
date: 2021-08-22 09:00:00 +0900
categories: study
tags: sprint-review
comments: true
published: true
---

- <span style="font-size:20px;color:gray">Contents</span>

  - [Sprint Review(기초)](#12)

    - [1. CLI를 이용한 작업과 GUI를 이용한 작업이 동일함을 이해할 수 있다.](#1)
    - [2. 리눅스 터미널에서 기본적인 명령어를 사용할 수 있다.](#2)
    - [3. 루트 디렉토리(/)와 홈 디렉토리(~)를 구분할 수 있다.](#3)
    - [4. 절대 경로와 상대 경로의 차이를 이해할 수 있다.](#4)
    - [5. 텍스트 에디터 nano를 실행하고, 파일을 저장할 수 있다.](#5)
    - [6. 운영체제에 맞는 패키지 매니저를 이용해 패키지를 업데이트, 업그레이드, 리스트 확인, 설치, 삭제할 수 있다.](#6)
    - [7. nvm과 npm의 차이를 이해할 수 있다.](#7)
    - [8. nvm으로 Node.js를 설치할 수 있다.](#8)
    - [9. package.json에 포함된 내용 중 script, dependency, devDependencies가 무엇을 뜻하는 지 이해할 수 있다.](#9)

  - [Sprint Review(심화)](#13)
    - [10. 사용 권한](#10)
    - [11. 환경변수](#11)

---

# <span style="font-size:20px;color:DodgerBlue">1</span>

<span style="color:DodgerBlue">CLI를 이용한 작업과 GUI를 이용한 작업이 동일함을 이해할 수 있다.</span>
<br>

방법의 차이가 있을 뿐, 같은 작업입니다.

# <span style="font-size:20px;color:DodgerBlue">2</span>

<span style="color:DodgerBlue">리눅스 터미널에서 기본적인 명령어를 사용할 수 있다.</span>
<br>

네

# <span style="font-size:20px;color:DodgerBlue">3</span>

<span style="color:DodgerBlue">루트 디렉토리(/)와 홈 디렉토리(~)를 구분할 수 있다.</span>
<br>

홈 디렉토리(`~`)는 최상위 루트 디렉토리 하위에 있는 home 디렉토리가 아니라 그 아래에 있는 사용자의 홈디렉토리를 말합니다. 계정명으로 설정된 폴더(`Users/jiwoo`)를 말하며 보통 리눅스에 처음 로그인하면 접속되는 위치를 말합니다. 루트 디렉토리 하위의 home 디렉토리는 여러 사용자의 홈 디렉토리가 모여있는 디렉토리(`Users`)입니다.<br>

루트 디렉토리(`/`)는 리눅스 파일 체제의 최상위 디렉토리입니다. 모든 디렉토리들의 시작점으로 일반적인 데이터를 저장하지 않습니다. 절대경로로 경로를 표기할 때, 최상위 루트(/)부터 시작합니다.

- [출처: [Linux] 리눅스 파일 시스템 구조 / 루트 디렉토리, 홈 디렉토리](https://dana-study-log.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%8C%EC%9D%BC-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EA%B5%AC%EC%A1%B0-%EB%A3%A8%ED%8A%B8-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC-%ED%99%88-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC)

# <span style="font-size:20px;color:DodgerBlue">4</span>

<span style="color:DodgerBlue">절대 경로와 상대 경로의 차이를 이해할 수 있다.</span>
<br>

절대 경로는 기준점으로부터의 절대적인 위치를 말합니다. 이 기준점을 루트폴더(`/`)라고 합니다. 즉, 특정 폴더나 파일이 루트폴더로부터 어떤 폴더로 진입하는 경우 만날 수 있는지 나타냅니다. <br>

상대 경로는 특정 폴더 또는 파일의 위치를 현재 위치를 기준점으로 나타냅니다. 현재 폴더는 점(`.`)으로 표현하고, 상위 폴더는 두 개의 점(`..`)으로 표현합니다. 명령어 ls를 통해 확인되는 폴더나 파일(hi.js)은, 상대 경로로써 `./hi.js`을 붙여 표현할 수 있습니다

# <span style="font-size:20px;color:DodgerBlue">5</span>

<span style="color:DodgerBlue">텍스트 에디터 nano를 실행하고, 파일을 저장할 수 있다.</span>
<br>

```
1. nano {파일명}
2. 파일 수정
3. ctrl + x + y + Enter
4. cat {파일명}으로 확인
```

# <span style="font-size:20px;color:DodgerBlue">6</span>

<span style="color:DodgerBlue">운영체제에 맞는 패키지 매니저를 이용해 패키지를 업데이트, 업그레이드, 리스트 확인, 설치, 삭제할 수 있다.</span>
<br>

네

# <span style="font-size:20px;color:DodgerBlue">7</span>

<span style="color:DodgerBlue">nvm과 npm의 차이를 이해할 수 있다.</span>
<br>

네

# <span style="font-size:20px;color:DodgerBlue">8</span>

<span style="color:DodgerBlue">nvm으로 Node.js를 설치할 수 있다.</span>
<br>

네

# <span style="font-size:20px;color:DodgerBlue">9</span>

<span style="color:DodgerBlue">package.json에 포함된 내용 중 script, dependency, devDependencies가 무엇을 뜻하는 지 이해할 수 있다.</span>
<br>

네

# <span style="font-size:20px;color:DodgerBlue">10</span>

<span style="color:DodgerBlue">사용 권한</span>
<br>

- Achievement Goals
  - 사용 권한과 소유자에 대해 이해하고, 사용 권한을 변경할 수 있다
    - 파일의 소유자와 파일에 적용된 사용 권한을 확인하고 이해할 수 있다. `ls -l`
    - 파일에 적용된 사용 권한을 변경할 수 있다. `chmod`

---

- 읽기(`Read`), 쓰기(`Write`), 실행(`eXecute`) 권한

  - 폴더와 파일의 권한을 확인하고 이해할 수 있다.
  - 폴더와 파일의 권한으로 폴더인지 파일인지 구분하는 방법을 알 수 있다.
  - `ls -l`을 입력하면 터미널에 나타나는 출력. username은 사용자 이름입니다.

```t
jiwoo@Jiwooui-MacBookPro  ~  ls -l
total 8
...
/*  권한 |  링크 수 | 소유자 | 그룹 | 크기 | 최근 수정일 | (파일/폴더)이름  */
-rw-r--r--    1 jiwoo  staff      29  8 23 11:22 helloworld.js
drwxr-xr-x@   2 jiwoo  staff      64  8 23 11:20 linux
```

- '-rw-r--r--' & 'drwxr-xr-x@'

파일 helloworld.js는 -rw-r--r-- 이라고 출력되었고, 폴더 linux는 drwxr-xr-x 라고 출력되었습니다. 이 표현의 첫 시작인 `-` 와 `d` 는 각각 <span style="color:indianred">not directory</span>와 <span style="color:indianred">directory</span>를 나타냅니다. <span style="color:indianred">폴더</span>이면 'd'로, <span style="color:indianred">파일</span>이면 '-' 로 나타냅니다. 이어지는 `r`, `w`, `x`는 각각 읽기 권한(`read permission`), 쓰기 권한(`write permission`), 실행 권한(`execute permission`)을 나타냅니다. <br> <br>
3번에 걸쳐 나타나는 이유는 <span style="color:indianred">사용자</span>와 <span style="color:indianred">그룹</span>, <span style="color:indianred">나머지</span>에 대한 <span style="color:indianred">권한</span>을 표시하기 때문입니다. 파일 helloworld.js의 권한은 rw-r--r-- 으로, 소유자는 읽기와 쓰기가 가능하고, 다른 사용자 그룹은 읽기만 가능하다는 의미입니다. 폴더 linux의 권한은 rwxr-xr-x 으로, 소유자는 읽기와 쓰기, 실행이 가능하고, 다른 사용자 그룹은 읽기와 실행만 가능합니다.

- user

파일의 소유자입니다. 기본적으로 파일을 만든 사람이 소유자가 됩니다. owner라고 하기도 합니다.

- group

group에는 여러 user가 포함될 수 있습니다. 그룹에 속한 모든 user는 파일에 대한 동일한 <span style="color:indianred">group 액세스 권한</span>을 갖습니다. 많은 사람이 파일에 액세스해야 하는 프로젝트에서, 각 user에게 일일이 권한을 할당하는 대신에, <span style="color:indianred">모든 user를 group에 추가하고, 파일에 group 권한을 할당</span>합니다.

- other

파일에 대한 접근 권한이 있는 다른 user입니다. 파일을 만들지 않은 다른 모든 user를 의미합니다. 따라서 other 권한을 설정하면, 해당 권한을 global 권한 설정이라고 볼 수도 있습니다.

- chmod

폴더나 파일의 읽기, 쓰기, 실행 권한을 변경하는 명령어입니다.

1. owner가 OS에 로그인한 경우 <br>
   `chmod` 로 폴더나 파일의 권한을 변경할 수 있습니다.
2. other가 OS에 로그인한 경우 <br>
   `sudo` 를 이용해 폴더나 파일의 권한을 변경할 수 있습니다.
   - sudo : 관리자 권한을 획득하는 명령어

- Symbolic method
  더하기(+), 빼기(-), 할당(=)과 액세서 유형을 표기해서 권한을 변경하는 방식

  - Access Class : `u`(user), `g`(group), `o`(other), `a`(all, 'u', 'g' and 'o')
  - Operator : `+`(add access), `-`(remove access), `=`(set exact access)
  - Access Type : `r`(read), `w`(write), `x`(execute)
  - 사용 예시

  ```t
  chmod g-r filename # removes read permission from group
  chmod g+r filename # adds read permission to group
  chmod g-w filename # removes write permission from group
  chmod g+w filename # adds write permission to group
  chmod g-x filename # removes execute permission from group
  chmod g+x filename # adds execute permission to group
  chmod o-r filename # removes read permission from other
  chmod o+r filename # adds read permission to other
  chmod o-w filename # removes write permission from other
  chmod o+w filename # adds write permission to other
  chmod o-x filename # removes execute permission from other
  chmod o+x filename # adds execute permission to other
  chmod u+x filename # adds execute permission to user
  ```

- Absolute form <br>
  rwx를 3 bit로 해석하여, 숫자 3자리로 권한을 표기해서 변경하는 방식

  - Read : `r`, `4`
  - Write : `w`, `2`
  - eXecute : `x`, `1`
  - 사용 예시

  ```t
  // 만약, user는 rwx 를, group과 other은 r-- 로 권한을 변경하려고 한다면, 위 표에 나와있는 숫자의 합을 user, group, other 순으로 입력하여 사용합니다.
  # u=rwx (4 + 2 + 1 = 7), go=r (4 + 0 + 0 = 4)
  chmod 744 helloworld.js # -rwxr--r--
  ```

  - ![그림](/assets/img/abs.png)
  - [출처: Manage file permissions on Unix-like systems](https://kb.iu.edu/d/abdb)

# <span style="font-size:20px;color:DodgerBlue">11</span>

<span style="color:DodgerBlue">환경변수</span>
<br>

'환경변수'란 <span style="color:indianred">시스템에 설정한 전역변수</span>입니다. `export`를 통해 환경변수를 설정할 수 있습니다.

- Achievement Goals
  - PC에 저장하는 환경변수가 무엇인지 이해하고, 사용할 수 있다.
    - PC에 저장된 환경변수를 확인할 수 있다. `export`
    - PC에 저장된 환경변수를 불러올 수 있다. `dotenv`
    - Node.js에서 환경변수를 영구적용할 수 있다. `.env`

---

- export
  `환경변수를 확인하는 터미널 명령어` && `환경변수를 임시 적용하는 터미널 명령어`<br>
  - 터미널에 명령어 export 를 입력해, 기록된 환경변수를 확인할 수 있습니다.

```t
 ✘ jiwoo@Jiwooui-MacBookPro  ~  export
HOME=/Users/jiwoo
LANG=ko_KR.UTF-8
LESS=-R
LOGNAME=jiwoo
LSCOLORS=Gxfxcxdxbxegedabagacad
LaunchInstanceID=73227757-AA6A-467E-AD03-C0A905C351FE
NVM_BIN=/Users/jiwoo/.nvm/versions/node/v14.17.0/bin
NVM_CD_FLAGS=-q
NVM_DIR=/Users/jiwoo/.nvm
OLDPWD=/Users/jiwoo/desktop
PAGER=less
PATH=/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/bin:/Users/jiwoo/.nvm/versions/node/v14.17.0/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
PWD=/Users/jiwoo
RBENV_SHELL=zsh
SECURITYSESSIONID=186a6
SHELL=/bin/zsh
SHLVL=1
SSH_AUTH_SOCK=/private/tmp/com.apple.launchd.qRVyY2UAyx/Listeners
TERM=xterm-256color
TERM_PROGRAM=Apple_Terminal
TERM_PROGRAM_VERSION=433
TERM_SESSION_ID=F1B9023F-635D-46DB-B4C9-03A0AF9E0240
TMPDIR=/var/folders/pb/kwnkstzs3_gdp3c5b3jd9tsh0000gn/T/
USER=jiwoo
XPC_FLAGS=0x0
XPC_SERVICE_NAME=0
ZSH=/Users/jiwoo/.oh-my-zsh
```

- export 명령어로 환경변수를 설정합니다
  - 등호 표시(Equal sign, =) 앞뒤에는 반드시 <span style="color:indianred">공백이 없어야</span> 합니다.

```t
export urclass="is good"
```

- echo 명령어와 달러사인을 이용해 설정한 환경변수를 조회할 수 있습니다.
  - 이때 환경변수의 앞에는 달러사인(`$`)을 입력하여, 변수라는 뜻을 터미널에 전달합니다.

```t
export urclass="is good"
echo $urclass
```

- dotenv
  `자바스크립트에서 환경변수 사용하기` <br>

npm 모듈 dotenv를 사용하면, 자바스크립트에서 환경변수를 사용할 수 있습니다. <br>
npm 모듈을 설치하고 사용하기 위해서, 새로운 폴더를 만들고 npm init 을 입력합니다. <br>
그리고 npm i dotenv 를 입력해 모듈을 설치합니다. <br>

```t
/*
 * 0. 새로운 폴더 생성
 * 1. npm init
 * 2. npm install dotenv
*/
jiwoo@Jiwooui-MacBookPro  ~  cd desktop
jiwoo@Jiwooui-MacBookPro  ~/desktop  cd ../
jiwoo@Jiwooui-MacBookPro  ~  mkdir environment_variable
jiwoo@Jiwooui-MacBookPro  ~  cd environment_variable
jiwoo@Jiwooui-MacBookPro  ~/environment_variable  npm init /* 엔터 키를 여러번 입력해 init을 마칩니다. */
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (environment_variable)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to /Users/jiwoo/environment_variable/package.json:

{
  "name": "environment_variable",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable 
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  npm i dotenv /* dotenv 모듈을 설치합니다.*/
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN environment_variable@1.0.0 No description
npm WARN environment_variable@1.0.0 No repository field.

+ dotenv@10.0.0
added 1 package and audited 1 package in 0.426s
found 0 vulnerabilities



   ╭────────────────────────────────────────────────────────────────╮
   │                                                                │
   │      New major version of npm available! 6.14.13 → 7.21.0      │
   │   Changelog: https://github.com/npm/cli/releases/tag/v7.21.0   │
   │               Run npm install -g npm to update!                │
   │                                                                │
   ╰────────────────────────────────────────────────────────────────╯


```

- Node.js 환경에서 내장 객체 `process.env`를 이용해 환경변수를 객체로 받아올 수 있습니다.
  - 명령어 export 로 확인한 내용과 동일한 내용을 객체로 출력합니다.
  - cat 명령어 (`cat {파일명}`) : cat 명령 뒤에 파일 이름을 입력하면 그 파일의 내용을 출력합니다.
  - [출처: 리눅스 cat 명령어 사용법 정리 (파일 내용 출력, 파일 생성, 파일 병합)](https://withcoding.com/109)

```t
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  nano index.js
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  cat index.js
console.log(process.env)
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  node index.js
{
  TMPDIR: '/var/folders/pb/kwnkstzs3_gdp3c5b3jd9tsh0000gn/T/',
  XPC_FLAGS: '0x0',
  LaunchInstanceID: '73227757-AA6A-467E-AD03-C0A905C351FE',
  TERM: 'xterm-256color',
  LANG: 'ko_KR.UTF-8',
  SSH_AUTH_SOCK: '/private/tmp/com.apple.launchd.qRVyY2UAyx/Listeners',
  SECURITYSESSIONID: '186a6',
  XPC_SERVICE_NAME: '0',
  TERM_PROGRAM: 'Apple_Terminal',
  TERM_PROGRAM_VERSION: '433',
  TERM_SESSION_ID: 'F1B9023F-635D-46DB-B4C9-03A0AF9E0240',
  SHELL: '/bin/zsh',
  HOME: '/Users/jiwoo',
  LOGNAME: 'jiwoo',
  USER: 'jiwoo',
  PATH: '/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/shims:/Users/jiwoo/.rbenv/bin:/Users/jiwoo/.nvm/versions/node/v14.17.0/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin',
  SHLVL: '1',
  PWD: '/Users/jiwoo/environment_variable',
  OLDPWD: '/Users/jiwoo',
  ZSH: '/Users/jiwoo/.oh-my-zsh',
  PAGER: 'less',
  LESS: '-R',
  LSCOLORS: 'Gxfxcxdxbxegedabagacad',
  NVM_DIR: '/Users/jiwoo/.nvm',
  NVM_CD_FLAGS: '-q',
  NVM_BIN: '/Users/jiwoo/.nvm/versions/node/v14.17.0/bin',
  RBENV_SHELL: 'zsh',
  urclass: 'is good',
  _: '/Users/jiwoo/.nvm/versions/node/v14.17.0/bin/node',
  __CF_USER_TEXT_ENCODING: '0x1F5:0x3:0x33'
}

```

- .env `Node.js에서 환경변수 영구 적용` <br>
  - 명령어 export 로 적용한 환경변수는 현재 사용 중인 터미널에서만 임시로 사용이 가능합니다.
  - 환경변수를 Linux 운영체제에 저장하는 방법은 여러 가지가 있지만, Node.js에서는 파일 .env를 만들어 저장하는 방법을 사용합니다.

1. `.env` 파일을 생성하고, 사용하고자 하는 환경변수를 입력한 뒤 저장합니다.

2. .env 파일에 저장한 내용을 불러오기 위해서는, `dotenv 모듈`을 사용해야 합니다.
   - index.js를 다음과 같이 수정하고, 저장합니다.
   - index.js에서 dotenv.config 메소드를 이용해, .env를 process.env에 적용할 수 있습니다.

```t
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  nano .env
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  cat .env
myname=kimcoding
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  nano index.js
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  cat index.js
const dotenv = require("dotenv");
dotenv.config();
console.log(process.env.myname);
 jiwoo@Jiwooui-MacBookPro  ~/environment_variable  node index.js
kimcoding
/* index.js 파일을 수정하고, 실행합니다. */
```
