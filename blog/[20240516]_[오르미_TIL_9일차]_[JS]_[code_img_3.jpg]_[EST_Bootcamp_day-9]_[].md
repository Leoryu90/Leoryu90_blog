# 목차
- [타입](#타입)
  1. [원시타입 (Primitive Types)](#원시타입)
  2. [객체타입 (Object Types)](#객체타입)
     1. [배열 (Array)](#배열)
        - [push()와 pop()](#pp)
        - [shift()와 unshift()](#suns)
        - [splice()](#splice)
        - [slice()](#slice)
        - [sort()](#sort)
        - [forEach()](#forEach)
        - [map()]((#map))
        - [filter()](#filter)
        - [includes](#includes)
     2. [객체 (Object)](#객체)


## 💡 타입(type)
<a id="타입"></a>

### type 이란?

자료형, 변수가 가지고 있는 데이터의 타입.   

- 원시타입: 단순히 데이터를 저장한 타입
- 참조타입: 객체로 저장되는 타입

> 보통 프로그래밍 언어에서는 변수의 자료형과 함께 변수를 선언하지만   
> 자바스크립트는 자료형을 함께 쓸 필요는 없습니다.
> 

```javascript
String str = "Java"; // Java의 변수 선언식
/* 변수 키워드 let, const */  str = "JavaScript"; // JavaScript의 변수 선언
```

### 1. 원시타입 (Primitive Types)
<a id="원시타입"></a>

원시타입의 특징은 값이 변경 불가능

<img src="img/day9/원시타입.png" width="500" height="500" alt="원시타입에 대한 정리">


> ```
> JavaScript 에서 원시타입 종류   
> string, number, bigint, boolean, undefined, symbol, null
> ```

### 2. 객체타입 (Object Types)
<a id="객체타입"></a>

값의 참조가 지정됨 (자바의 주소값과 같은개념)   
값 자체가 저장되는 것이 아닌 위치값이 저장 됨

#### a. 배열 (Array)
<a id="배열"></a>

변수에 여러 값을 저장하는 방식으로   
추가, 제거, 정렬, 검색 등 다양한 작업이 가능함.

**배열의 메소드**

1. push()와 pop()
   <a id="pp"></a>

배열의 마지막에 데이터를 추가(push()), 제거(pop())가 가능   
```javascript
push(): 배열의 마지막에 요소를 추가하고 길이를 반환
pop(): 마지막 요소를 꺼내어 반환
```

2. shift()와 unshift()
   <a id="suns"></a>

배열의 처음 데이터에 추가(unshift()), 제거(shift())가 가능

```javascript
unshift(): 배열의 첫 번째 요소로 새로운 요소를 추가
shift(): 배열에서 첫 번째 요소를 꺼내고 반환
```

<img src="img/day9/스택과큐.png" width="500" height="500" alt="스택과 큐에 대한 개념">   

> 아직은 이른 개념일 수 있으나 강사님이 개념설명을 해주셨습니다.   
> push(), pop(), shift(), unshift() 로 구현이 가능   
>    
> ⚠️   
> 그림 때문에 push(), pop()으로만 스택을 구현한다고 착각에 빠질 수 있음   
> shift(), unshift()로도 스택을 구현이 가능합니다.   
> 큐도 2가지 방향으로 설계가 가능합니다.

3. splice()
   <a id="splice"></a>

배열의 요소를 추가, 제거 또는 교체

```javascript
const arr = [1, 2, 3];
arr.splice(1, 0, 100);
console.log(arr); // [1, 100, 2, 3]
arr.splice(2, 1, 40);
console.log(arr); // [1, 100, 40, 3]
```

4. slice()
   <a id="slice"></a>

배열에서 요소를 추출해서 새로 배열을 반환

```javascript
const myArray = ["apple", "banana", "cherry", "durian", "elderberry"];
console.log(myArray.slice(1(시작값), 4(숫자의 1개 전 값까지)));
//apple부터 cherry까지
```

5. sort()
   <a id="sort"></a>

배열의 요소를 정렬

> ⚠️   
> 문자열은 잘 작동하지만 숫자형은 값이 이상하게 반환   
> #유니코드 포인트에 따라서 반환된다고 함.

숫자형 정렬의 단점을 해결하기 위한 방법

```javascript
const num3 = [13, 9, 10];

num3.sort(function (a, b) {
  console.log('a: ' + a, 'b: ' + b);
  return a - b;
});
/**
 작동하는 로직
"a: 9"
"b: 13" // a - b는 음수임으로 a를 앞으로 => [9, 13, 10]

"a: 10"
"b: 9" // a - b는 양수임으로 b를 앞으로 => [9, 13, 10]

"a: 10"
"b: 13" // a - b는 음수임으로 a를 앞으로 => [9, 10, 13]

"a: 10"
"b: 9" // a - b 는 양수임으로 b를 앞으로 => [9, 10, 13]
*/
```

솔직히 어떤방식인지 머리로는 이해가 가질 않지만...   
방법만 알고 넘어갑니다..;;


6. forEach()
   <a id="forEach"></a>

배열의 요소를 순환하면서 해당 요소를 함수로 전달   
함수가 각 요소에 대해 실행

좀 반복문같은 ? 배열 내부 순환 메소드?

```javascript
const arr = ['참외', '키위', '감귤'];
arr.forEach(function(item, index) {
  console.log(item, index);
	arr[index] = index;
});

// 결과
// 참외 0
// 키위 1
// 감귤 2

// arr 에 [0,1,2] 값이 들어감.
```

반복적으로 작동하여 결과값을 만드는 예시

```javascript
const avengers = ['spiderman', 'ironman', 'hulk', 'thor'];

const newAvengers = [];
avengers.forEach(function (item) {
    newAvengers.push('💖' + item + '💖');
});
```

결과값!!!

<img src="img/day9/결과값1.png" width="500" height="200" alt="forEach 예시에 대한 결과값">   

7. map()
   <a id="map"></a>

각 요소에 대해 주어진 함수를 실행하고, 그 결과를 새로운 배열로 반환

```javascript
const arr = [1, 2, 3];
const newArr = arr.map(function(item, index) {
   return item * index;
});

console.log(newArr);

// 결과값 [0, 2, 6]
```
<details>
<summary> 오픈! ✨배열 안에 객체에서 데이터를 뽑는 형태</summary>

```javascript
const data = [
    {
        "_id": "642ba3980785cecff3f39a8d",
        "index": 0,
        "age": 28,
        "eyeColor": "green",
        "name": "Annette Middleton",
        "gender": "female",
        "company": "KINETICA"
    },
    {
        "_id": "642ba398d0fed6e17f2f50c9",
        "index": 1,
        "age": 37,
        "eyeColor": "green",
        "name": "Kidd Roman",
        "gender": "male",
        "company": "AUSTECH"
    },
    {
        "_id": "642ba39827d809511d00dd8d",
        "index": 2,
        "age": 39,
        "eyeColor": "brown",
        "name": "Best Ratliff",
        "gender": "male",
        "company": "PRISMATIC"
    }
];

const ages = data.map((item) => item.age);
```

age 값만 뽑아서 새로운 배열을 생성할 수 있다.

</details>

8. filter()
   <a id="filter"></a>

특정 조건을 만족하는 요소들만 추출하여 새로운 배열을 만듬   
숫자나 날자 등 특정한 원소추출에 유용하다.

```javascript
//배열에서 2의 배수를 추출하여 새로운 배열을 만드는 코드
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const newArr = arr.filter(function(el) {
  return el % 2 === 0;
});

console.log(newArr);
```

9. includes
   <a id="includes"></a>

요소가 포함이 되어 있으면 true 아니면 false를 반환합니다.
```javascript
const arr1 = ['hello', 'world', 'hojun']
arr1.includes('world')

//ture
```

#### b. 객체 (Object)
<a id="객체"></a>

배열처럼 여러 데이터를 한 변수에 저장하지만 키-값 쌍으로 이루어져있는 자료형

- [map()](#map) 에서 예시로 사용했습니다. 

구조는 아래와 같습니다.

```javascript
const babaYaga = {      
  name: "John Wick",
  age: 53,
  from: "벨라루스",
	askingHim: function(){
		console.log("Yeah, I'm thinking I'm back!");
	}
};

//접근법
console.log(`${babaYaga.name} from ${babaYaga.['from']}`);

//속성추가법
babaYaga.job = "강아지 사육사";

//속성제거
delete babaYaga.job;
```

--------------------------------------
