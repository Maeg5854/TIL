# Query String 소개
* 현재 API 경로에 따라 다른 기능이 서비스 되는 상황. 같은 경로라면, 매번 같은 서비스만 제공된다. 그렇다면 조건에 따라 같은 경로라고 하더라도 다른 서비스를 제공할 수는 없을까? → `Query Stirng`
`http://a.com/topic?id=3`
- http부터 id=3까지 위 문장의 전체를 URL이라고 부른다.
- 또한 `?`뒤에 오는 `id=3`을 **Query String**이라고 부른다.

### Nodejs에서 query string 접근
- query string은 클라이언트에서 URL상에 입력해서 **요청**하는 부분이기에 app.get의 콜백함수의 **request 객체**에 저장되어있다.
- `req.query.<parameter_name>`으로 전달받은 query string의 값에 접근할 수 있다.

### Query string의 입력방식
- query string을 여러개 전달하려면 `&`으로 query string을 연결해야한다.
```
http://a.com/topic?id=1&name=hello
```

# Semantic URL
- Query string은 변수로 보내는 데이터를 결정했다면, Path의 형태로 데이터를 결정한다.
```
http://a.com/topic/1
```
- 위의 path는 `/topic`이라는 path에서는 받을 수 없고, `/topic/:id`와 같이 데이터를 받을 자리를 method의 path 변수에 명시해주어야 한다.
```
app.get('/topic/:id',function(req,res){...});
```
- 위의 `1`이라는 데이터에 접근하려면 `req.params.<parameter_name>`으로 접근할 수 있다.
- 이와 같은 Semanctic URL은 **Restful API**에 대해서 배울 때 더욱 깊이 알 수 있다.

### Semantic URL의 입력방식
- 여러개의 변수를 Semantic URL로 받고싶다면, path에 변수의 자리를 명시해준다. `:<변수명>`
```
app.get('/topic/:id/:mode', function(req, res){...});
```