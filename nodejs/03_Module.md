# Module

* `const http = require('http');`
  * const : 상수를 선언하는 키워드
  * require(module_name) : module_name에 해당하는 모듈을 가져오는 메소드

## NPM

* NPM = Node Package Manager: 타인이 만든 패키지에 대해서 관리하는 기능
  * 모듈: 프로그램의 부품의 역할을 하는 프로그램
    * Node.js가 제공하는 모듈
    * JavaScript가 제공하는 모듈
    * 타인이 만든 모듈
  * Module의 설치, 삭제, 업그레이드, 의존성 관리의 역할을 한다.
  * Node.js 패키지 뿐만 아니라 다른 환경의 패키지 관리에도 사용되곤 한다.
* 패키지는 크게 **모듈**과 **독립적 어플리케이션**으로 나눠진다.

## NPM을 이용한 패키지 설치
### 독립적인 앱 설치
##### EX) Uglyfy 설치

```
$ npm install uglify-js -g
```

* `-g` = global
  * 컴퓨터 전역에서 사용되는 독립적인 소프트웨어로 사용
  * 해당 옵션이 없으면, npm을 실행하는 해당 프로젝트 내부의 부품으로 사용
* Uglyfy : 컴파일, 데이터 전송시에 불필요하게 차지하는 Identation, space 등을 삭제해주는 프로그램
  * 스페이스도 다 데이터 이기 때문에 전송용량을 줄이는데 유용하다!
    ```
    $ uglify fileName.js -m -o outputFileName.js
    ```
  * `-m` = mangle : 지역변수와 같이 이름이 상관없는 변수명을 가장 짧은 문자로 치환한다.
  * `-o outputFileName.js` : 프로그램 결과를 뒤에 입력되는 문자열을 이름으로 하는 파일로 출력한다.
  
### 모듈 설치
##### EX) Underscore 설치
```
$ npm init
```
* `npm init` : npm 상에서 현재 디렉토리를 패키지로 지정하는 명령
  * 타모듈도 패키지이고, 현재의 나의 프로젝트도 패키지이기 때문에 npm을 이용해 모듈을 설치하기 전에 수행해주어야 한다.
  * 다음과 같은 입력 시퀀스가 실행된다.
    * `name: ()`: 패키지의 이름 입력한다. 별도로 입력하지 않을 경우 괄호 안의 이름으로 설정된다.
    * `version:(1.0.0)`: 버전을 입력한다.
    * `descrpiption:`: 패키지에 대한 설명을 입력한다.
    * `entry point: (.js file)`: 해당 패키지를 구동시키는 .js 파일 지정
    * `test command:`: 테스트를 수행할 커맨드 입력
    * `git repository: (http://.../~.git)`: 패키지를 깃 상에 올릴 경우 해당 깃 레포지토리 입력
    * `keywords:`, `author:`, `license:` :해당 패키지를 설명하기 위한 키워드, 저자, 라이센스 입력
  * 결과로 `package.json`파일이 생성되고, 모듈을 설치하면 된다.
```
$ npm install underscore
```
* 결과로 `node_module` 폴더가 생성되고, `underscore`디렉토리가 위치하며 모듈을 설치한다.
  * 커맨드 창에 나타난 `extraneous`는 모듈을 온전하게 포함하지 않았다는 것을 의미하고, 온전히 포함시키기 위해서는 다음과 같이 `--save` 옵션을 추가해야한다.
    ```
    $ npm install underscore --save
    ```
    * 이 결과로 `package.json`에 depandencies항목이 추가되고, 추후에 우리의 프로젝트를 로드할 때 해당 패키지를 손쉽게 가져올 수 있다.
    * 잠깐 사용할 경우에는 `--save`를 제거하고, 우리의 패키지에서 계속 사용되는 모듈의 경우에는 붙이는 것이 좋다.

## 모듈 사용법
##### EX) underscore 사용
```javascript
const _ = require('underscore');
```
* `require()`: 괄호 안에 해당하는 모듈을 오브젝트 형태로 로드한다.
  * 그렇기 때문에 모듈 오브젝트를 받을 변수나 상수를 선언한다.
  * underscore 모듈 오브젝트의 이름은 통상적으로 `_`를 사용한다.
* underscore는 Javascript의 빈약한 배열의 기능을 채워준다. 
  ``` javascript
  let arr = [1, 2, 3];
  arr[0] //1
  _.first(arr); // 1
  
  arr[arr.length-1]; //3
  _.last(arr); //3
  ```