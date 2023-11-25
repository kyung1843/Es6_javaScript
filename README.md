# Es6_javaScript
Es6 문법 이해
## 변수와 상수
### 변수
  * var
    - 변수 재할당O, 변수 중복 인식X
    ```js
    var hi = "안녕";
    var hi = "잘가";
    ```
  * let
    - 변수 재할당X, 변수 중복 인식O
    ```js
    let hi = "안녕";
    let bye = "잘가";
    ```
### 상수
  * const
    - 값 변경X, 재할당X, 선언시 반드시 값 할당 해야함
    ```js
    const hi = "this is const";
    ```
## 원시 데이터 타입
객체가 아니면서 메소드도 가지지 않는 데이터
  * String
    -  문자열
    ```js
    let str1 = '문자열1';
    let str2 = "문자열2";
    ```
  * Number
    - 숫자
    ```js
    let num = 123;
    ```
  * Boolean
    - 참/거짓
    ```js
    let good = true;
     let bad = false;
    ```
  * Null
    - 값이 없다
    ```js
    let value = null;
    ```
  * Undefined
    - 값이 설정되지 않음
    ```js
    let value;
    ```
## 비교연산자
### == 와 ===
  * ==
    - 값 일치
  * ===
    - 값과 타입 일치
  ```js
  let num1 = 1;
  let str = '1';

  num1 == str  //true
  num1 === str //false
  ```
## 조건문
### if / else if / else
```js
if(조건1){
  //do something
}else if(조건2){
  //do something
}else{
  //do something
}
```
### switch/case
```js
switch ("iphone") {
  case 'iphone':
    console.log('아이폰!');
    break;
  case 'ipad':
    console.log('아이패드!');
    break;
  case 'galaxy note':
    console.log('갤럭시 노트!');
    break;
  default:
    console.log('else');
}
```
## 함수 functiono
### 함수
  ```js
  function 함수명() {
    
  }
  ```
  - 함수 호출방식에 따라 this에 바인딩 객체 동적 결정
### 화살표함수
  ```js
  const 함수명 = () => {

  };
  ```
  - 함수 선언시 this 바인딩 객체 정적 결정
  - this는 항상 상위 스코프의 this
  - this 변경X
  - 생성자 함수X
    ```js
    function basic() {
	    this.num = 1234;
    }
    
    const arrow = () => {
	  this.num = 1234;
    };

    const Basic = new basic();
    console.log(Basic.num); // 1234

    const Arrow = new arrow(); // Error
    ```
  - arguments변수 전달X
    ```js
    function tran1() {
	    console.log(arguments); // Arguments(2) [[1, 2, callee: ƒ, Symbol(Symbol.iterator): ƒ]
    }
    const tran2 = () => {
	    console.log(arguments); // Uncaught ReferenceError: arguments is not defined
    };
    tran1(1,2);
    tran2(1,2);
    ```


