# Hoisting

hoist: 들어올리다, 끌어올리다

Hoisting(호이스팅)이란, 변수의 사용 및 함수의 실행 코드가 선언보다 먼저 일어나도 정상 진행이 되도록 하는 것.
(흔히 선언코드가 끌어올려진다고 표현하지만, 실제 메모리에는 변화가 없다.)

함수선언식만 호이스팅이 일어난다. 함수표현식은 NONO!
할당구문은 런타임 과정에서 이루어지기 때문에 호이스팅되지않는다
함수를 끌어올리지만 변수의 값은 끌어올리지않는다

* 함수선언식
```
function foo() {}
```
* 함수표현식 / 함수할당식
```
var foo = function() {}
```

###### 예제1.
```
Name("sohyun");

function Name(name) {
  console.log("My name is " + name);
}

// 결과: "My name is sohyun"
```

###### 예제2.
```
num = 6;
num + 7;
var num; 

// 에러가 나지 않는다
```

###### 예제3.
###### (초기화가 아닌 선언만 끌어올린다. 만약 변수를 선언한 뒤에 나중에 초기화시켜 사용한다면, 그 값은 undefined.)
```
var a = 1;
console.log(a + ' , ' + b);  // '1 , undefined'
var b = 2;
console.log(a + ' , ' + b);  // '1 , 2'

// 위의 코드는 아래와 같은 방식으로 동작합니다.
var a;  // a 변수 선언
a = 1;  // a 변수에 1 할당
var b;  // b 변수 선언
console.log(a + ' , ' + b);  // '1 , undefined'
b = 2;  // b 변수에 2 할당
console.log(a + ' , ' + b);  // '1 , 2'
```
###### 예제4.
```
/ 실행 전
logMessage();
sumNumbers();

function logMessage() {
  return 'worked';
}

var sumNumbers = function () {
  return 10 + 20;
};
JsCopy
호이스팅에 의해 자바스크립트 해석기는 코드를 아래와 같이 인식한다.
// 실행 시
function logMessage() {
  return 'worked';
}

var sumNumbers;

logMessage(); // 'worked'
sumNumbers(); // Uncaught TypeError: sumNumbers is not a function

sumNumbers = function () {
  return 10 + 20;
};
```

코드의 가독성과 유지보수를 위해 호이스팅이 일어나지 않도록 하는게 좋다



