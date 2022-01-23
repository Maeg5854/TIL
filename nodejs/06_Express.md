## Express
##### http 모듈을 활용한 서버 제작
```javascript
http.createServer((req, res) => {
 res.writeHead(200, { 'Content-Type': 'text/plain' });
 res.end('Hello World\n');
}).listen(port, hostname, () => {
 console.log(`Server running at http://${hostname}:${port}/`);
});
```
* 위 코드는 아래와 같은 개념의 코드이다.
```javascript
var server = http.createServer(function(req, res){
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello World\n');
});

server.listen(port, hostname, function(){
    console.log(`Server running at http://${hostname}:${port}/`);
});
```
* 이렇게도 웹 서버를 구현하기에 편한 방식이지만, 더 적은 코드로도 더 많은 일을 할 수 있는 모듈이 **Express**이다.

## Express 설치
```
$ npm install express --save
```
* nodejs 패키지로 프로젝트를 초기화 한 후 `--save`을 통해서 express에 대한 Dependancy를 추가할 수 있다.
  * *이를 통해 향후 해당 프로젝트 로드시 빠르게 모듈을 설치할 수 있다.*

## Express 간단한 웹앱 만들기
```
$ vim app.js // 리눅스 or 맥OS
```
* 프로그램이 시작하는 도입 함수가 정의된 자바스크립트파일을 생성한다.
```javascript
const express = require('express');
var app = express();
```
* `express()`함수는 application 객체를 리턴한다.

```javascript
app.listen(port#, function(){
    console.log('Connected');
});
```
##### Get방식으로 들어온 사용자
```javascript
app.get('/', function(req, res){
    res.send();
});
```
* `/`: 홈으로 Get 메소드로 들어오면 function()에 해당하는 내용을 실행한다.
* `function(req, res)`: Get 메소드에 사용되는 콜백함수에는 요청을 나타내는 첫번째 파라미터(`req`)와 응답을 나타내는 두번째 파라미터(`res`)가 주어진다.