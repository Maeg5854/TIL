# Nodejs의 역사

### 2008

2008 - Google V8 Engine Open sourced
2009 - Ryan Dahl에 의해 Nodejs 프로젝트 시작

# Node.js

Node.js = V8 Engine + Event-driven + non-blocking I/O

- 웹 브라우저에서 동작하던 Javascript가 서버에서도 동작할 수 있게 됨
- Javascript라는 "언어"와 "문법"을 이용해서 웹 브라우저를 제어할 수도 있고 node.js를 이용해서 서버를 제어할 수도 있다.

  - alert('Hello world')은 Javascript로 쓰인 문장이지만, 웹 브라우저 Runtime이 아닌 Node.js Runtime에서는 정상적으로 작동하지 않는다.
  - Web browser와 Node.js의 Javascript는 서로 다르면서 협력적으로 사용된다.
- Node.js의 경쟁자 : Python, Ruby, php, JAVA

  - DB 접근, 프로그램으로 웹페이지 생성에 있어서 같은 역할을 할 수 있다.
- Node.js의 장점

  - V8 Engine의 고속도
  - Event-driven Programming
  - Non-blocking I/O
  - Javascript를 통해서 웹 서버-클라이언트를 모두 구현할 수 있다는 점

# Installation

[Node.js 홈페이지](https://nodejs.org/) 에서 운영체제에 맞는 설치 방법으로 설치

```
$ node --version
```
