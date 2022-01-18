# 간단한 웹 서버 만들기

```javascript webserver.js
const http = require('http');
 
const hostname = '127.0.0.1';
const port = 1337;
 
http.createServer((req, res) => {
 res.writeHead(200, { 'Content-Type': 'text/plain' });
 res.end('Hello World\n');
}).listen(port, hostname, () => {
 console.log(`Server running at http://${hostname}:${port}/`);
});
```
```
$ node webserver.js
```
* node.js를 이용해서 webserver.js 파일을 실행

# 인터넷의 통신 방법

* 클라이언트: 콘텐츠의 요청
* 서버: 콘텐츠 제공
  * 클라이언트와 서버는 상대적인 개념
  * 웹 브라우저가 설치된 컴퓨터를 클라이언트라고 부를 것
  * http://a.com 와 같은 주소를 가지고 콘텐츠를 제공하는 컴퓨터를 서버라고 부를 것
* 컴퓨터의 주소 : IP
  * 도메인 네임: 사람이 알기 쉽게 표현한 이름 (http://a.com)
  * IP 주소: 실제로 접속할 때 필요한 주소 (127.0.0.1)
* 포트 : 어떤 컴퓨터에 접속 시 제공받을 서버의 종류 선택
  * 웹서버의 Port# = 80 (http://a.com:80)
    * http://a.com에 해당하는 컴퓨터가 80번 포트를 'listening'
    * 클라이언트 컴퓨터가 http://a.com의 80번 포트로 요청
    * http를 사용했을 경우 포트번호가 없을때 80번 포트로 자동 연결
