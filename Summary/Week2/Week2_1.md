# JavaScript

# 2-1. 자바스크립트 변수-연산자-타입

### 자바스크립트의 버전
- ECMAScript(ES)의 버전에 따라 결정되고 자바스크립트 실행엔진이 반영함
- ES6문법이 표준으로 쓰임
- 브라우저가 지원해줘야함

### 변수
- var
- let
- const
```javascript
var a = 2;
var a = "aaa";
var a = 'aaa';
var a = true;
var a = [];
var a = {};
var a = undefined;
```
### 연산자
- +,-,*,/,% 등이 있다
```javascript
const name = "crong";
const result = name || "codesquad";
console.log(result);
var name = "";
var result = name || "codesquad";
console.log(result);
```
#### 삼항연산자
```javascript
const data = 11;
const result = (data > 10) ? "ok" : "fail";
console.log(result);
```
#### 비교연산자
```javascript
0 == false;
"" == false;
null == false;
0 == "0";
null==undefined;
```

### 타입
- undefined, null, boolean, number, string, object, function
- 타입은 실행타임에 결정된다
- toString.call을 사용해서 타입을 확인할 수 있음
- typeof로 타입을 체크
- 배열의 경우 isArray함수로 타입체크

# 2-2. 자바스크립트 비교-반복-문자열

### 비교문
#### if문
```javascript
if (condition_1) {
  statement_1;
} else if (condition_2) {
  statement_2;
} else if (condition_n) {
  statement_n;
} else {
  statement_last;
} 
````
#### 삼항연산자
```javascript
var a = true;
var result = (a) ? "ok" : "not ok";
console.log(result);
```
#### swtich 문
```javascript
switch (expression) {
  case label_1:
    statements_1;
    break;
  case label_2:
    statements_2;
    break;
    ...
  default:
    statements_def;
    break;
}
```
#### 거짓으로 취급하는 값
- false
- undefined
- null
- 0
- NaN
- the empty string ("")

### 반복문
```javascript
var arr = [1,2,3];
for(var i=0,len=arr.length;i<len;i++){
    console.log(arr[i]);
}
```
*배열의 경우 forEach 메서드도 있음

### 문자열
```javascript
typeof "abc";  //string
typeof "a";    //string
typeof 'a';    //string. single quote도 사용가능.
```
#### 문자열 메소드
```javascript
"ab:cd".split(":"); //["ab","cd"]
"ab:cd".replace(":", "$"); //"ab$cd"
" abcde  ".trim();  //"abcde"
```

- 추가 자료 : [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Control_flow_and_error_handling#%EC%A1%B0%EA%B1%B4%EB%AC%B8)

# 2-3. 자바스크립트 함수

### 함수 선언
- 여러개의 인자를 받아서 그 결과를 출력함
- 파라미터의 갯수와 인자의 갯수가 일치하지않으면 오류남
- 파라미터에 값이 주어지지않으면 undefined라는 값을 같게됨
```javascript
// 함수의 호출.
function printName(firstname) {
    var myname = "jisu";
    return myname + " " +  firstname;
}
console.log(printName);
```

### 함수표현식
```javascript
function printName(){
    var inner = function(){
        return "inner value";
    }
    var result = inner();
    console.log("name is "+result);
}
```
- 이 경우에는 함수가 정의되어있지않아서 에러가 남
```javascript
function printName(){
    var result = inner();   
    console.log("name is "+result);
    var inner = function(){
        return "inner value";
    }
}
```
- 이와 같이 함수 선언문으로 바꿔줘야함
```javascript
function printName(){
    var result = inner();   
    console.log("name is "+result);
    function inner(){
        return "inner value";
    }
}
```
#### hoisting
 호이스팅에 의해 함수 안에 필요한 변수값들을 미리 모아서 선언하는데   
 이때 함수 선언문은 먼저 정의되지만 함수 표현식은 값이 할당되기 전의 변수값(undefined)만 끌어올려지게 된다.
 
 - 반환값과 undefined
 ```javascript
 function printName(firstname) {
    var myname = "jisu";
    var result = myname + " " +  firstname;
}
```
return 값이 없을 때는 기본 반환값인 undefined가 반환됨

### argument속성
- 함수 내의 arguments라는 특별한 지역변수가 존재함
- 선언한 파라미터보다 더 많은 인자를 보낼 수 있고 이 인자를 arguments로 배열의 형태로 접근이 가능함
```javascript
function a(){
    for(var i=0;i<arguments.length;i++){
        console.log(arguments[i]);
    }
}
a(1,2,3); 
```

### arrow function
```javascript
function getName(name){
  return "Kim" + name;
}
// 위와 동일
var getName = (anme) => "Kim" + name;
```

# 2-4. 자바스크립트 함수 호출 스택

### 함수 호출
```javascript
// 함수의 호출.
function printName(firstname) {
    var myname = "jisu";
    return myname + " ," +  firstname;
}

function run(firstname) {
   firstname = firstname || "Youn";
   var result = printName(firstname);
   console.log(result);
}
```
#### Call Stack
- 메모리에 Call stack에서 순서대로 쌓임
- 함수 내부에서 다른 함수를 호출하면 스택에 쌓이고 결과값을 가져올때까지 메모리공간을 차지
- 다른 함수의 실행이 끝나서 return값을 가져오면 메모리공간에서 사라짐
