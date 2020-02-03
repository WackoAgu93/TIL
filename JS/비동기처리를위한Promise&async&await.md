

## 비동기 처리란?

   특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성을 뜻한다.
   
   - 비동기 처리의 가장 흔한 사례로 JQuery의 ajax를 들수 있는데 화면에 표시할 이미지나 데이터를 서버에서 불러와 ajax통신을 통해 화면에 뿌려줄수 있다.
   
```javascript
  function getData() {
    var tableData;
    $.get('https://domain.com/products/1', function(response) {
      tableData = response;
    });
    return tableData;
  };
  console.log(getData()); //undefined
```
  
  `$.get()` 를 통해 ajax 통신이 이루어 지는데 `https://domain.com` URL에 HTTP GET 으로 데이터를 요청하는것과 같다.
  
  그렇게 서버에서 받아온 데이터는 `response` 인자에 담기고 `tableData`라는 변수에 저장하게 되지만 `console.log(getData());`의 로그상에는 undefined가 찍히게 된다.  
  그 이유는 `$.get()`로 데이터를 요청하고 받아올 때까지 기다려주지 않고 다음 코드인 `return tableData;`를 실행하였기 때문이다. 따라서, `getData()`의 결과 값은 초기 값을 설정하지 않은 tableData의 값 undefined를 출력하게 된다.  
  
 * 이렇게 특정 로직의 실행이 끝날 때까지 기다려주지 않고 나머지 코드를 먼저 실행하는 것을 비동기 처리라고 한다.
 
 * 또 다른 비동기 처리 사례는 `setTimeout()`이다. __setTimeout()는 Web API의 한 종류 __ 로, 코드를 바로 실행하지 않고 지정한 시간만큼 기다렸다가 로직을 실행한다.
