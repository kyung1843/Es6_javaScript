# Es6_javaScript
Es6 문법 이해


참조 :

[https://learnjs.vlpt.us/basics/](https://learnjs.vlpt.us/basics/)
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
## 템플릿 리터럴
[에브리 저장소 https://eblee-repo.tistory.com/38](https://eblee-repo.tistory.com/38)
- (``)백틱으로 감사줌
  ```js
  `String text line1
   string text line2`
  ```
- 런타임 시점에 문자열로 처리/변환
1. 표현식 삽입법
   ${}를 사용해 표현식 표기 가능(가독성 UP!)
   ```js
   let num1 = 10;
   let num2 = 18;
   let text = '샤브샤브';

   console.log('나는 ${num1+num2} 이고, ${text}를 먹었당');
   //나는 28살이고, 샤브샤브를 먹었당
   ``` 
3. Taged Templates
   ```js
   let person = 'Lee';
   let age = 28;

   let tag = function(strings, personExp, ageExp) {  
     console.log(ageExp);  //28
     console.log(personExp);  //Lee
   
     //Strings는 전달 문자열을 ${}을 기준으로 split
     console.log(strings); // ['that ', ' is a ', '']

     let str0 = strings[0];
     let str1 = strings[1];
     console.log("str0 : " + str0);  //that
     console.log("str1 : " + str1);  //is a

     let ageStr;
     if(ageExp > 99) ageStr = 'centenaian';
       else ageStr = 'youngster';
       return str0 + personExp + str1 + ageStr;    //이 함수 내에서 template literal 반환 가능
   };
    
   let output = tag`that ${person} is a ${age}`;
   console.log(output);    //that Lee is a youngster
   ```
5. Multi-line Strings
  - 리터럴 안에서 개행 해주면 적용됨
  ```js
  `String text line1
   string text line2`
  ```
5. Nesting templates
  - 템플릿 중첩 작성
    ```js
     => const classes  = `header ${isLargeScreen()? '' : `icon-${item.isCollapsed? 'expander' : 'collapser'}`}`;
    ``` 
6. Raw Strings
  - 이스케이프 문자를 해석하지 않은 일반문자열
  - String.raw 태그함수 사용해 입력한대로 출력 가능
  ```js
  let tag = function(strings) {
    return strings.raw[0];
  }
  let str = tag`Hello\nWorld.`;
  console.log(str);       //Hello\nWorld.
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
- forEach
  - for문 대체
  ```js
  const arr = [1,2,3];
  arr.forEach(num => {console.log(num)});
  //1~3
  ```
- map
  - 배열안 원소 변환
  ```js
  const arr = [1,2,3];
  const map = arr.map(n => n*n);
  console.log(map);  //[1,4,9]
  ```
- indexOf
  - 원하는 값의 인덱스 번호 찾기
  ```js
  const arr = [1,2,3];
  let idx = arr.indexOf(2);  //1
  ```
- findIndex
  - 원하는 값의 인덱스 번호 찾기
  ```js
  const arr = [1,2,3];
  let idx = arr.findIndex(2);
  ```
  - 배열 안 원소가 배열/객체인 경우 사용X
  ```js
  const arr = [{id:1, text : '일', done : true}, {id:2, text : ' 이', done : true}];
  let idx = arr.findIndex(arr=>arr.id === 1);
  console.log(idx);  //0
  ```
- find
  - 찾아낸 값 자체를 반환
  ```js
  const arr = [{id:1, text : '일', done : true}, {id:2, text : ' 이', done : true}];
  let idx = arr.find(arr=>arr.id === 1);
  console.log(idx);  // {id:1, text : '일', done : true}
  ```
- filter
  - 조건 만족하는 값들만 모아 새로운 배열 반환
  ```js
  const arr = [{id:1, text : '일', done : true}, {id:2, text : ' 이', done : true}];
  let newOne = arr.filter(arr=>arr.done === true);
  console.log(newOne);  // [{id:1, text : '일', done : true}, {id:2, text : ' 이', done : true}]
  ```
- splice
  - 특정항목 제거
  ```js
  const arr = [1,2,3];
  arr.splice(0,1);
  console.log(arr);  //[2,3]
  arr.splice(idx, n);  //idx : 시작 인덱스 부터 , n : n개 제거
  ```
- slice
  - 특정항목 제거, 기존의 배열 변형X
  ```js
    const arr = [1,2,3];
    const arr2 = arr.slice(0,2);  //0부터 시작해서 2 전까지 자르겠다
    console.log(arr2); // [3]
    console.log(arr);  //[1,2,3]
  ```
- pop
  - 배열 맨 마지막 값 추출&제거
  ```js
  const arr = [1,2,3];
  const value = arr.pop();
  console.log(value);  //3
  console.log(arr);  //[1,2]
  ```
- shift
   배열의 첫번째 값 추출&제거
  ```js
  const arr = [1,2,3];
  const value = arr.shift();
  console.log(value);  //1
  console.log(arr);  //[2,3]
  ```
- unshift
  - 배열 맨앞에 원소 추가
  ```js
   const arr = [1,2,3];
   arr.unshift(4);
   console.log(arr);  //[1,2,3,4]
  ```
- concat
  - 여러개 배열 하나로 합치기, 기존 배열 변화X
  ```js
  arr1 = [1,2,3];
  arr2 = [4,5,6];
  const res = arr1.concat(arr2);
  console.log(res) //[1,2,3,4,5,6]
  console.log(arr1); //[1,2,3]
  console.log(arr2); //[4,5,6]
  ```
- join
  - 배열 안의 값을 문자열로 합치기
  ```js
  const arr = [1,2,3];
  arr.join(' ,'); //'1, 2, 3'
  ```
- reduce함수
  ```js
  const arr = [1,2,3];
  //param1 은 누적값
  let sum = arr.reduce((param1,param2) => return 값, default값);
  ```
- includes
  - 배열의 특정 값 있는지 여부
  ```js
  const arr = [1,2,3];
  arr.includes(4); //false  
  ```

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
## 객체 생성자 vs 클래스
### 객체 생성자
```js
function Animal(type, name, sound) {
  this.type = type;
  this.name = name;
  this.sound = sound;
  this.say = function() {
    console.log(this.sound);
  };
}
const dog = new Animal('개', '멍멍이', '멍멍');
dog.say(); // 멍멍
```
#### 프로토타입
- 같은 생성자 함수 사용시 특정함수/값 재사용 가능
- 생성자 함수 아래 함수.prototype.이름 = 어쩌구;
  ```js
  Animal.prototype.value = 1;
  console.log(dog.value); //1

  dog.prototype.value  = 1 //Error
  ```
- 생성자 상속
  ```js
  Animal.prototype.say = function() {
    console.log(this.sound);
  };
  
  function bird(name, sound) {
    //생성자.call(this, 필요로하는 파라미터);
    Animal.call(this, '독수리', name, sound);
  }
  //추가적으로 prototype 을 공유
  bird.prototype = Animal.prototype;

  const eagle = new bird('독수리', '까악');
  eagle.say();  //까악
  ``` 
### 클래스
- 객체생성자로 구현한 코드를 조금더 깔끔하고 명확하게 구현가능
```js
class AnimalC {
        constructor(type, name, sound){
            this.type = type;
            this.name = name;
            this.sound = sound;
        }

        say(){
            console.log(this.sound);
        }
    }

    const birdy = new AnimalC('갈매기', '끼룩이', '끼룩끼룩');
    birdy.say();  //끼룩기룩
```
- 클래스 상속 : extends 사용
```js
class Cat extends AnimalC{
  constructor(name, sound){
    //super() : 상속받은 클래스의 생성자
    super('고냐미', name, sound);
  }
}
const cat1 = new Cat('야옹이', '애옭애옭');
cat1.say(); //애옭애옭
```
## Truthy / Falsy
- falsy : null, undefined, 0, '', NaN
- 함수 파라미터에 falsy한 값이 들어가게되면 오류 발생!
- !파라미터 사용해 오류 회피
```js
//!falsy를 사용
function some(!thing){
 console.log(thing);
}
```
## 단축 평가 논리 계산법 (&&, ||)
```js
const dog = {
  name: '멍멍이'
};
const cat = {
  name: ''
};

function getName1(animal) {
  return animal && animal.name;
}
//값이 제대로 주어졌을 때만 name 을 조회하고, 나머지는 undefined 를 반환
let name1 = getName1();
console.log(name1); // undefined

name1 = getName1(dog);
console.log(name1); // 멍멍이

//------------------------------------------------------------------------------

function getName2(animal) {
  const res = animal && animal.name;
  return res || 'nothing';
}
const name2 = getName2(cat);
console.log(name2); //'nothing'
```
## 함수 기본 파라미터
- 파라미터 default값 지정
```js
function ex(param = 1){
  return param;
}
//또는
const ex = (param = 1) => param;

console.log(ex()); //1
console.log(ex(2)); //2
```
## 비구조화 할당(구조분해)
- 배열/객체 안의 값 추출 후 선언
  1. 배열
  ```js
  const arr = [1,2];
  const [one,two] = arr;
  console.log(one); //1
  ```
  2. 객체
  ```js
   const obj1 = {a:1, b:2};
   const {a,b} = obj1;
   console.log(a); //1
  ```
  3. 함수의 파라미터
  ```js
  const obj1 = {a:1, b:2};
  function name ({a,b}){
    console.log(a); //1
  }
  ```
- 비구조화 할당시 기본값 설정
  ```js
  const obj1 = {a:1};
  {a,b =2} = obj1
  //또는 
  function name ({a,b =2}){
   console.log(a); //2
   console.log(b); //2
  }
  //또는
  const arr = [1,2,3];
  const[one, two, three =4] = arr;
  console.log(three); //4
  ```
- 비구조화 할당시 이름 변경
```js
const obj1 = {a:1};
const num = obj1.a;
console.log(num); //1
```
- 깊은 값 비구조화 할당
  1. 비구조화 할당 두번
   ```js
    const exObj = {food :{info : {name : '탕후루', type : ['딸기', '귤', '샤인머스켓']}}, price : 3000};
    const {name, type} = exObj.food.info;
    const {price} = exObj;
   
    const extracted = {name, type, price};
    //또는
    const extracted = {name : name, type:type, price:price};
    console.log(extracted); // {name: '탕후루', type: Array(3), price: 3000}
   ```  
  2. 한번에 모두 추출
  ```js
    const exObj = {food :{info : {name : '탕후루', type : ['딸기', '귤', '샤인머스켓']}}, price : 3000};
    const {food:{info:{name, type}},price} = exObj;
   
    const extracted = {name, type, price};
    //또는
    const extracted = {name : name, type:type, price:price};
    console.log(extracted); // {name: '탕후루', type: Array(3), price: 3000}
   ```
## spread vs rest
- 배열, 객체 , 함수 파라미터 에서 사용 가능
- 기존의 것을 건들이지 않고 새로운 객체 만든다.
- ... 연산자 사용
  ### 객체
    - spread
      ```js
      const slime = {
        name: '슬라임'
      };
      const cuteSlime = {
        ...slime,
        attribute: 'cute'
      };
      const purpleCuteSlime = {
        ...cuteSlime,
        color: 'purple'
      };
      console.log(slime);  //{name :'슬라임'}
      console.log(cuteSlime); //{name : '슬라임', attribute : 'cute'}
      console.log(purpleCuteSlime); //{name : '슬라임', attribute : 'cute', color :'purple'}
      ```
    - rest
      ```js
      const purpleCuteSlime = {
        name: '슬라임',
        attribute: 'cute',
        color: 'purple'
      };

      const { color, ...rest } = purpleCuteSlime;
      console.log(color); //purple
      console.log(rest);  //{ name: '슬라임',attribute: 'cute'}

      const { attribute, ...slime } = cuteSlime;
      console.log(attribute); //cute
      console.log(slime); //{name: '슬라임'}
      ```
  ### 배열
    - spread
      ```js
      const animals = ['개', '고양이', '참새'];
      const anotherAnimals = [...animals, '비둘기'];
      console.log(animals);  //[개, 고양이, 참새]
      console.log(anotherAnimals); // [개, 고양이 참새, 비둘기]
      ```
    - rest
      ```js
       const arr = [1,2,3,4,5,6];
       const [one, ...rest1] = arr;
       console.log(one);  //1
       console.log(rest1); //[2,3,4,5,6]
      ```
  ### 함수 파라미터
    - spread
      ```js
      function sum(...rest) {
        return rest.reduce((acc, current) => acc + current, 0);
      }

      const numbers = [1, 2, 3, 4, 5, 6];
      const result = sum(...numbers); 
      console.log(result); //21
      ```
    - rest
      ```js
      function sum(...rest) {
        return rest;
      }

      const result = sum(1, 2, 3, 4, 5, 6);
      console.log(result); //[1,2,3,4,5,6]
      ```
       ```js
      function sum(...rest) {
        return rest.reduce((acc, current) => acc + current, 0);
      }
      const result = sum(1, 2, 3, 4, 5, 6);
      console.log(result); //21
      ```


