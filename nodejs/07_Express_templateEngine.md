# Template
* 정적 웹 페이지와 동적 웹페이지의 서로의 절충 -> 템플릿 엔진
* 템플릿 엔진 자체로 큰 주제이고 독립적인 엔진으로 생각해야함.

```jade
html
    head
        title Hello world
    body
        h1 Hello Template & Jade
        ul
            - for(var i=0; i<5 ;i++)
                li coding
            div= time
```
`= time` : 템플릿 엔진에 time이라는 변수를 입력해 구성할 수 있다.

# 템플릿 엔진 사용법
https://expressjs.com/ko/guide/using-template-engines.html
* 템플릿 엔진은 여러가지가 있다. jade, handlebar 등. *수업에서는 jade*사용할 예정
```
$ npm install jade --save
``` 
* 템플릿 엔진을 사용하기 위해서는 express에게 _템플릿 엔진을 사용여부_ 와 *사용할 템플릿 엔진*을 알려주어야 한다. 함수다 다음과 같다.
``` javascript
app.set('view engine', 'jade');
``` 
* 템플릿이 저장될 디렉토리를 express에게 알려주어야한다.
``` javascript
// app.set('views', '{viewDirectoryName}');
app.set('views', './views');
```
* 라우팅된 패스에서 `res.render()`를 사용하면, 템플릿 디렉토리에서 템플릿을 렌더해 response로 전송한다.
```javascript
app.get('/template', function(req, res){
    res.render('temp');
});
```
# Jade의 문법
* 들여쓰기를 하면 앞 쪽 태그 내에 html 태그를 작성할 수 있다.
* 들여쓰기를 한다는 것은 새로운 html 태그를 생성한다는 의미이므로 데이터에 해당하는 내용은 들여쓰기로 시작하지 않는다.
```jade
html
    head
    body
        hello jade // hello는 태크로 인식된다.
        ul
            -for(var i=0; i<5; i++)
                li coding
```