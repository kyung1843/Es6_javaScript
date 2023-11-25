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
## 함수 function
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
## 객체
- 객체 선언
```js
const name = {key : value , key:value, ...}

//key에 공백 포함되어 있는 경우는 ''따옴표로 감싸서 사용
const exp = {'this is key' : value}
```
- 객체에서 추출
```js
const name = {key : value , key:value, ...}
console.log(name.key);

console.log(Object.entries(name)); //객체 배열로 변환  [[key,value],[key,value]]
console.log(Object.keys(name));  //key 모음 배열로 변환 [key, key]
console.log(Object.values(name));  // value 모음 배열로 변환 [value, value]

```


- 객체 비구조화 할당
  - 일일이 객체.key로 불러오지 않기 위해 사용
  ```js
  const name = {first : 'lee', last:'any'};
  function  objSep (name){
	const {first, last} = name
  	const text = `성은 ${first}이고, 이름은 ${last} 이다.`
  	console.log(text);
  }
  //또는
  function  objSep ({first, last}){
  	const text = `성은 ${first}이고, 이름은 ${last} 이다.`
  	console.log(text);
  }
  ```
- 객체 내 함수
  - 화살표 함수 사용X
  - 객체 안 함수의 경우 this는 자신이 속해있는 객체를 가르킴
  - 객체 밖에서 새로운 값 set 할 수 없음 ==> getter, setter 사용
```js
const cat = {
  name: '치즈태비',
  sound: '아옭',
  say: function say() {
    console.log(this.sound);
  }
};
cat.say();  //'아옭'
```
- 객체 내 getter/setter 메서드 설정
  - getter
  ```js
  const numbers = {
    a: 1,
    b: 2,
    get sum() {
      return this.a + this.b;
    }
  };

  console.log(numbers.sum);
  numbers.b = 5;
  console.log(numbers.sum);
  ``` 
  - setter
  ```js
  const numbers = {
    _a: 1,
    _b: 2,
    sum: 3,
    calculate() {
      console.log('calculate');
      this.sum = this._a + this._b;
    },
    get a() {
      return this._a;
    },
    set a(value) {
      console.log('a가 바뀝니다.');
      this._a = value;
      this.calculate();
    },
  };
  
  //setter 사용
  numbers.a = 5;
  console.log(numbers.sum);
  /*
   결과 :
    a가 바뀝니다.
    calculate
    7
  */
  ```
## 배열
### Basic
  - 배열 선언
  ```js
  const arr = [1,2,3];
  const arr2 = [{key:value},{key:value}];
  ```
  - 배열 조회
  ```js
  //arr의 n번체 값
  arr[n];
  arr[n].key;
  ```

  - 배열 항목 추가
  ```js
  const arr = [1,2];
  arr.push(3);

  const arr 2 = [{key:value}];
  arr2.push({key:value});
  ```
  - 배열 크기
  ```js
  const arr = [1,2];
  arr.length
  ```
### 내장함수

## 반복문
- for문
  - for
    ```js
    for (let i = 0; i < 10; i++) {
      console.log(i); //0~9
     }
    
    const alpha = ['a', 'b', 'c'];
    for (let i = 0; i < alpha.length; i++) {
      console.log(alpha[i]);  //a b c
    }
    ```
  - for...in  : 객체 반복문
    ```js
    const cat = {name : '치즈태비', sound : '애옹'};
    for (let key in cat) {
      console.log(`${key}: ${cat[key]}`);
    }
    
    ```
  - for...of : 배열 반복문
    ```js
    const alpha = ['a', 'b', 'c'];
    for (let bet of alpha) {
      console.log(bet);  //a b c
    }
    
    ```
- while문
  ```js
  let i = 0;
  while (i < 10) {
    console.log(i);  //0~9
    i++;
  }
  ```
- break : 반복문 탈출
- continue : ignore



