## 동기와 비동기
* 동기(Synchronous)와 비동기(Asynchronous)
  * 동기적 일처리: 각 태스크의 종료와 시작이 순차적으로 일어나는 것
    * 각 태스크의 종료 여부를 체크한 후 다음 태스크를 시작한다.
  * 비동기적 일처리: 각 태스크의 종료와 시작이 순차적이지 않는 것
    * 태스크의 종료 여부는 불확실하다.
  * 시스템의 종류에 따라서 동기의 개념이 달라진다. Node.js에서는 **파일 작업**에 있어서 동기적 처리와 비동기적 처리의 차이를 살펴볼 예정이다.

## Filesystem module
```javascript
const fs = require('fs'); // file system library

// sync
let data = fs.readFileSync('data.txt', {encoding:'utf-8'});
console.log(data);

// async
fs.readFile('data.txt', {encoding:'utf-8'}, function(err, data){
    console.log(data);
});
```
* 같은 함수인데 *Sync*가 붙은 **동기 함수**와 붙지 않은 **비동기 함수**가 있다.
  * 동기함수를 실행하면 동기함수가 종료된 후에 다음 코드가 실행된다.
  * 대부분적으로 시간이 필요한 작업(I/O 등)은 비동기로 처리하고, 선택적으로 동기함수를 사용한다. 동기함수 사용은 권해지지는 않는다.
* **비동기함수**에 전달된 콜백함수는 비동기 함수가 종료된 후에 실행되는 함수이다.

```javascript
console.log(2);
fs.readFile('data.txt', {encoding:'utf-8'}, function(err, data){
    console.log(3);
    console.log(data);
});
console.log(4);
```
* 위 비동기함수에서 실행 순서는 **2 -> 4 -> 3 -> data** 이다.
  * `readFile()`이 비동기로 수행되기 때문에 `readFile()`이 시작되고 종료되기 이전에 `readFile()`이후의 `console.log(4);`가 실행된 것이다.
  * 이런 비동기를 지원하기 때문에 Javascript는 빠른 편이다. 물론 안정성에 대한 Trade-off는 존재한다.

  