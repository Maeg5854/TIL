# Callback
##### EX) array.sort()
```javascript
let a = [2,3,1];
a.sort(); //[1,2,3]
function b (v1,v2) {return v2-v1};
a.sort(b); //[3,2,1]
```
* `array.sort()`라는 함수는 (선택적으로) **매개변수로 함수**를 받는다.
  * 정렬시에 순서를 결정할 때 필요할 때마다 매개변수 함수를 호출해서 정렬순서를 결정한다.
  * 이런 함수를 **Callback 함수**라고 부른다.
* Callback function: 인자로 전달된 함수
  * 이 함수는 사용자가 호출하는 것이 *아닌*, 다른 것에 의해서 호출받는다.
  * callback function을 여러 번 사용하고 싶을 때, 위와 같이 이름이 갖게끔 작성하면 유용하다. 만약 일회성으로 사용되는 callback function의 경우는 다음과 같이 작성할 수도 있다.
  ```javascript
  a.sort(function(v1, v2){return v2-v1;});
  ```
  * 이렇게 이름이 정해지지 않은 함수를 **익명 함수**라고 부른다.
* Callback function을 포함하는 함수는 다음과 같이 인자로 받은 함수를 호출하는 형태로 정의한다.
``` javascript
function sort(callback){callback();};
```



