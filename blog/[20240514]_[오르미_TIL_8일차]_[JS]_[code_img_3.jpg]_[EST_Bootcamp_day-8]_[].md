# 목차
[JavaScript](#javascript)
- [JavaScript를 사용하는 여러가지 방법](#javascript를-사용하는-여러가지-방법)
- [변수](#변수)
- [함수](#함수)
  1. [함수 구조](#함수-구조)
  2. [매개변수와 전달인자](#매개변수와-전달인자)
  3. [함수를 선언하는 여러가지 방법](#함수를-선언하는-여러가지-방법)
- [조건문](#조건문)
  1. [if문](#if문)
  2. [삼항연산자](#삼항연산자)
  3. [switch문](#switch문)
- [반복문](#반복문)
  1. [for문](#for문)
  2. [while문](#while문)
  3. [break_continue문](#break_continue문)


### 💡 JavaScript
<a id="javascript"></a>

<details>
<summary>JavaScript의 탄생 배경</summary>
자바스크립트는 1995년 넷스케이프사에서 브렌던 아이크 주도하에 만들어진 프로그래밍 언어입니다.
웹페이지에서 동작하는 프로그램을 만들 때 사용됩니다.
</details>

#### JavaScript를 사용하는 여러가지 방법
<a id="javascript를-사용하는-여러가지-방법"></a>

1. HTML 태그 내 삽입
2. script 태그를 통해 삽입
3. HTML 파일 외부에 있는 스크립트 파일을 로드

> CSS와 비슷하지만 태그나 링크할때 body에 작성\
> ⚠️ head 부분에 넣어도 작동은 하지만 오류가 발생할 수 있습니다.
>

--------------------------

#### 변수
<a id="변수"></a>

1. 변수란?\
   변수는 `변할 수 있는 수`, `변할 수 있는 정보`라는 뜻

```jsx
var x = 3;
let y = 4;
const z = 5;

변수의 왼쪽 x, y, z 값과 오른쪽 3, 4, 5 값은 모두 메모리 상에 올라갑니다.
```

변수는 선언하고, 할당하고, 사용할 수 있습니다. 또한,\
변수는 ‘변할 수 있는 수’이므로 const를 제외하고 지정된 값을 계속 바꿀 수 있음


2.변수명을 정할 때

> ⚠️ 변수명 정할 때 주의사항
> - 변수이름은 $, _ 를 제외한 공백, 특수문자, 구두점을 사용할 수 없음
> - 첫 글자는 숫자가 될 수 없음
> - 대소문자를 구별
> - 예약어(JS에 이미 지정한 것 ex: if, for etc...)가 쓰일 수 없음
> - 유니코드 문자도 사용할 수 있습니다. 그러나 실무에는 보통 영어를 사용(간지?)

3. let 과 const.

`let`: 재할당이 가능한 변수를 선언할 때 사용\
`const`: 재할당이 불가능한 상수를 선언할 때 사용


20240513 내용 합침.

----------------------

<details>
<summary>함수</summary>
함수까지 배웠지만 TIL 작성하는걸 나누기는 싫으니 다음시간에 정리~~!!
</details>


## 💡 함수
<a id="함수"></a>

### 함수란?

```
반복적으로 필요한 코드를 묶어서 반복사용하도록 만드는 것
```

### 함수 구조
<a id="함수-구조"></a>

코드 구조

```javascript
function 함수이름(parameter1, parameter2...) { // 함수의 선언
    // 실행코드...
    return 반환값
}

함수이름(argument1, argument2...) // 함수의 호출
```

### 매개변수와 전달인자
<a id="매개변수와-전달인자"></a>

위의 함수 구조에서 용어를 살펴보면

| 용어 | 번역 | 의미 |
| --- | --- | --- |
| Parameter | 매개변수 | 함수와 메서드에 입력 변수 이름 |
| Argument | 전달인자, 인자, 인수 | 함수와 메서드에 실제 입력되는 값 |

> 파선아실(파라미터는 선언, 아규먼트는 실제 값)!!   
> 많은 백엔드 프로그램도 같은 구조.

### 함수를 선언하는 여러가지 방법
<a id="함수를-선언하는-여러가지-방법"></a>

1. 함수 선언문과 함수 표현식

    제목 없이 선언하여 값으로 할당하는 표현식(Expression)으로 선언하는것도 가능

```javascript
// 함수 선언문
function sum(x, y){
  return x + y;
}

// 함수 표현식
let sumXY = function(x, y){
  return x + y;
```

> ✨구문(Statement)과 표현식(Expression)   
> 구문: 작업을 수행하기 위한 코드 블록(ex, if문, switch문, for문)   
> 표현식: 값으로 평가될 수 있는 것

2. 화살표함수

    키워드를 화살표 기호로 대체하여 표현   
   제목을 정할 수 없기 때문에 표현식으로 사용

```javascript
function 함수1(x, y) {
    return x + y
}
// 위 함수를 화살표 함수로 작성하면 아래와 같습니다.
let 함수1 = (x, y) => x + y

// 만악 함수 실행시 전달하는 인자가 한 개라면 소괄호를 생략할 수 있습니다.
let 함수2 = x => x + 10

// 화살표 함수 내부에서 한 줄 표현식만 반환한다면 return 키워드를 생략해도 됩니다.
let 함수3 = x => x + 10
```

3. 즉시실행함수 (IIFE, Immediately Invoked Function Expression)

   함수를 정의함과 동시에 즉시 실행하는 방법

```javascript
(function() {
  console.log('이 함수는 만들어지자마자 바로 실행됩니다!');
})();


(function() {
	document.querySelector(".btn").addEventListener("click", function(){ 
	console.log('click!')
	});
})();
```

<br>

> 🔑함수를 사용 했을 때의 좋은점
> 1. 재사용성이 높아짐
> 2. 유지보수가 용이함
> 3. 구조 파악이 용이함


-------------------

## 💡 조건문과 반복문

### 조건문
<a id="조건문"></a>

#### 1. if문
<a id="if문"></a>

```javascript
let 변수 = 값;

if (조건식){
    // 조건식이 참일 때 실행될 코드
} else if (조건식){
    // else if 조건식이 참일 때 실행될 코드
} else {
    // 위 조건에 참이 없을 경우 실행될 코드
}
```

> ✨중괄호안의 코드가 한 줄 뿐이라면 중괄호를 아래와 같이 생략해서 쓸 수 있음
> ```javascript
> if (true) console.log("중괄호를 생략했습니다.");
> ```
> ⚠️여러사람이 같이 보게 될 경우 가독성을 위해 생략하지 않는 것을 추천
 
#### 2. 삼항연산자 (Conditional ternary operator)
<a id="삼항연산자"></a>

```javascript
조건식 ? 조건식이 참일 때 실행될 코드 : 조건식이 거짓일 때 실행될 코드
true or false ? true라면 실행 : false면 실행;
```

#### 3. switch문
<a id="switch문"></a>

switch문의 구조

```javascript
switch (표현식) {
  case 값1:
    // 값1에 대한 실행 코드
    break;
  case 값2:
    // 값2에 대한 실행 코드
    break;
  ...
  default:
    // 모든 case에 해당하지 않을 때 실행될 코드
    break;
}
```

> ⚠️ break가 없다면 switch문을 탈출하지 않고\
> 해당 case 이후의 모든 케이스의 코드들을 순서대로 실행
>

----------------------------

### 반복문
<a id="반복문"></a>

#### 1. for문
<a id="for문"></a>

```javascript
// 조건식이 참이 될 때까지 반복
for(초기화식; 조건식; 증감식) {
    실행문;
}
-----------------------------------
for(var i=0; i<10; i++){
  document.write(i, '<br>');
```

#### 2. while문
<a id="while문"></a>

```javascript
while (조건식) {
  // 조건식이 참일 때 실행될 코드
}
---------------------------------
let num = 0;

while (num < 11) {
    document.write(num, '<br>');
    num += 1;
}
```

do-while 반복문:  조건식이 거짓이더라도 반복문이 최소한 한 번은 실행되어야 할 때 사용

구조

```javascript
// 만약 num이 11이더라도 1번은 실행
let num = 0;

do {
    document.write(num, '<br>');
    num += 1;
} while (num < 11);
```

#### 3. 반복문의 break & continue
<a id="break_continue문"></a>

`break`: 반복문을 빠져나옴   
`continue`: 반복문의 다음 반복으로 이동

--------------------------------------