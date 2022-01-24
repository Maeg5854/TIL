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
    console.log('<h1>Connected</h1>');
});
```
##### Get방식으로 들어온 사용자
```javascript
app.get('/', function(req, res){
    res.send();
});
```
* `/`: 홈으로 Get 메소드로 들어오면 function()에 해당하는 내용을 실행한다.
* `function(req, res)`: Get 메소드에 사용되는 콜백함수에는 사용자로부터의 요청을 나타내는 첫번째 파라미터(`req`)와 사용자로의 응답을 나타내는 두번째 파라미터(`res`)가 주어진다.
* `get()`과 같이 접속한 패스와 메소드에 따라서 함수로 연결 해주는 함수를 *라우터*라고 한다.

## Express, 정적 파일을 서비스 하는 법
* 정적 파일?
  * 정적파일 : 동적이지 않은 것. 이미지, 문서 등등...
  * 동적파일 : 프로그래밍을 통해 만들어진 정보, 변하곤 한다.
``` javascript
app.use(express.static('public'));
```
* `public`: 정적 파일을 제공할 디렉토리를 지정한다. 현재는 public이라는 디렉토리를 지정했다.

```javascript
localhost:3000/시간표.png
```
* public이라는 디렉토리명 없이 바로 정적파일에 접근할 수 있다.

## Express, 웹페이지 표현 방법
* 정적 파일인 html 파일들을 정적파일 디렉토리에 위치 시킨 후 제공한다. (위 예제에서는 `public`디렉토리가 정적파일 디렉토리이다.)
```
localhost:3000/static.html
```
* 위 html을 변경하는 것은 nodejs를 껐다 키는 것과는 상관없다. html이 정적파일이기 때문에 nodejs를 끄지 않아도 html 상의 변경사항은 잘 전달된다.

* router 상에서도 html 코드를 전송할 수있다.
``` javascript
app.get('/dynamic', function(req, res){
    var lis = '';
    for (var i=0; i<5 ;i++){
        lis = lis + '<li>coding</li>';
    }
    var output = `<!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <title>
                my homepage
            </title>
            <body>
                hello, static!
                ${lis}
            </body>
        </head>
    </html>`;
    res.send(output);
});
``` 
* 위와 같이 html 코드를 javascript 상에서 바로 전송하는 것은 동적으로 전송하는 것이다. 변경사항이 생겼을때, 해당 자바스크립트 파일을 node로 다시 실행하지 않으면 변경된 내용으로 전달되지 않는다.
* html 상의 내용이 시시각각에 따라 변경되어야 하는 경우, 프로그래밍 적으로 변화가 필요한 경우에는 위와 같이 html을 동적으로 생성하고 전송하는 것이 유용하다.
  
* 이 동적 서비스와 정적 서비스의 장점을 모아놓을 순 없을까?
* 그렇게 나온것이 **템플릿 엔진**이다.