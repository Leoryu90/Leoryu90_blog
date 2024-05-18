# 목차
- [this](#this)
  1. [this 란?](#thisIs)
- [객체지향 프로그래밍](#객체지향-프로그래밍)
  1. [생성자 (constructor)](#생성자)
  2. [프로토타입 (prototype)](#프로토타입)
  3. [객체의 상속](#객체의-상속)
  4. [💡class](#classes)
  5. [💡class 상속](#class-상속)


## 💡 this
<a id="this"></a>

### this 란?
<a id="thisIs"></a>

객체를 가리키는 참조 변수   
- 자바의 this와는 조금 다른 개념

제일 이해가 잘 된 예시

```javascript
/ * this */
function sayName(){
  console.log(this.name);
}

var name = 'Hero'; 
// 전역으로 선언한 name 변수의 앞에는 window 가 생략되어 있습니다. 
// 때문에 window.name === "Hero" 가 성립합니다.
let peter = {
  name : 'Peter Parker',
  sayName : sayName
}

let bruce = {
  name : 'Bruce Wayne',
  sayName : sayName
}

sayName(); // Hero
peter.sayName(); // Peter Parker
bruce.sayName(); // Bruce Wayne

```

this는 자기가 속한 곳에서의 위치를 나타내지만 조금 복잡하다....

------------------------------------------------


## 💡 객체지향 프로그래밍
<a id="객체지향-프로그래밍"></a>

자바스크립트 객체: 키,값 쌍으로 이루어진 데이터의 묶음   
객체 지향의 객체: 표현하고자 하는 구체적인 사물을 추상적으로 표현한것

> 추상화: 필요한 최소한의 정보로 대상을 표현하는것

```javascript
const me
    name : 'Leoryu',
    address : '서울시 ㅇㅇ구 우리집 1길',
    phoneNum : '010-1234-5678',
    walk : function(){
        console.log('나는 지금 걷는다.');
    }
    study : function(codingLevel){
       codingLevel.levelUp();
   }
}

const coding = {
   level: 1,
   levelUp : function(){
      this.level++;
   }
}

me.study(coding);
```

> ✨ 객체와 객체가 서로 메소드를 통해 상호작용하게 하는것이 객체지향 프로그래밍

### 1. 생성자 (constructor)
<a id="생성자"></a>

생성자란 객체를 만들 때 new 연산자와 함께 사용하는 함수

```javascript
let myArr = new Array(1,2,3);  // 내장 생성자
```

- 생성자를 사용하는 이유   
  생성자를 통해 생성된 객체는 같은 프로퍼티와 메서드를 공유할 수 있다


```javascript
function NewFactory(name, age){
  this.name = name;
  this.age = age;
  this.sayYourName = function(){
    console.log(`제 이름은 ${this.name}입니다. 반갑습니다.`);
  }
}

let robot1 = new NewFactory('우루루까꿍', 2);

console.log(robot1);
```

> 위의 예시에서 만들어진 객체를 다른 말로 인스턴스(instance) 라고 합니다.
> ```javascript
> robot1 instanceof Factory //생성자 함수의 인스턴스를 확인하는 법
> ```

### 2. 프로토타입 (prototype)
<a id="프로토타입"></a>

생성자에서 배웠던 예시를 통해 인스턴스를 생성하면 **문제점**이 있음.   
**새로운 객체를 생산할 때 마다 함수를 생성**하게 됨   
100개의 객체를 생성할때마다 역시 100개의 함수를 새로 만들고 있는 것

- 문제를 해결하기 위해 필요한 것이 프로토타입

```javascript
function NewFactory() {
    this.sayYourName = function () {
        console.log(`제 이름은 ${this.name}입니다. 반갑습니다.`);
    }
}

// 이와 같은 형식으로 변경
NewFactory.prototype.sayYourName = function(){
    console.log(`제 이름은 ${this.name}입니다. 반갑습니다.`);
}
```

> 프로토타입은 모든 인스턴스가 하나의 메서드를 공유하도록 만들어   
> 자원을 더 효율적으로 사용하도록 해줍니다.
> 

### 3. 객체의 상속
<a id="객체의-상속"></a>

`__proto__ `: 객체 안에 존재하는 숨겨진 프로퍼티

<img src="img/day10/proto.png" width="300" height="200" alt="">
<img src="img/day10/has.png" width="300" height="200" alt="">

이렇게 **존재하지 않는** 프로퍼티와 메서드를 사용할 수 있음.   
prototype이 Object함수를 참조   
자기 자신에게 존재하지 않는 프로퍼티나 메서드를 프로토타입을 통해 추적하는 과정을   
**프로토타입 체이닝** 이라고 함

```javascript
//자바스크립트의 타입들은 기본적으로 Object 타입을 상속받고 있습니다
console.log(Array.prototype.__proto__ === Object.prototype);
console.log(String.prototype.__proto__ === Object.prototype);
```

### 💡 4. class
<a id="classes"></a>

클래스를 성명할 때 제일 많이 예시로 드는 것은   
붕어빵 틀(클래스) -> 붕어빵(인스턴스)

<br>

-  class의 사용법

class 키워드 + 이름 + 중괄호

```javascript
// function Robot(name) {
//     this.name = name;
// }

// Robot.prototype.sayYourName = function () {
//     console.log(`삐리비리. 제 이름은 ${this.name}입니다. 주인님.`);
// }


class Robot {
    // 클래스의 생성자 함수입니다. 하나의 클래스는 하나의 생성자만 정의할 수 있습니다. 
		// 그리고 생성자 함수는 new 키워드가 호출될때 자동으로 실행됩니다.
    constructor(name) {
        this.name = name;
    }

    // 메소드를 정의합니다. 메소드는 클래스가 생성한 인스턴스를 통해 사용할 수 있습니다.
    sayYourName() {
        console.log(`삐리비리. 제 이름은 ${this.name}입니다. 주인님.`);
    }
}
```

자바스크립트만의 사용자 정의 타입 생성(객체 생성) 방법을   
다른 언어의 클래스 문법처럼 바꿔준 것이 바로   
자바스크립트 클래스(classes)


<details>
<summary> 속마음 </summary>
드디어 이해하기 쉬운 개념의 등장!
<br>
프로토 타입에서 멘붕이 왔었다....   
<br>
이해도 억지로 한 느낌!!
<br>
그냥 다른 언어라서 모르는 부분이니까 그냥 외워버린 ...
</details>

<details>
<summary> 자바스크립트에서 Class가 없던 이유 </summary>

🧐 1983년에 C 언어가 객체지향 페러다임을 받아들이면서 C++가 탄생했습니다. <br>
C++가 만들어진 이래 classes의 개념은 모든 객체지향 언어에서 공통적으로 사용되었습니다.

자바스크립트가 2015년 드디어(30년 만에!?) 이 classes 개념을 받아들이고 나서 코드의 모습이 비로소 전통적인 객체지향형의 모습을 가지게 되었습니다.

위의 코드에서 볼 수 있듯, 객체에 필요한 모든 코드가 하나의 코드 묶음으로 통합되었습니다.

처음부터 자바스크립트에 classes 문법을 도입했다면 좋았겠지만 자바스크립트의 창시자인 브랜든 아이크는 아래처럼 회고합니다.

> If I had done classes in JavaScript back in May 1995, I would have been told that it was too much like Java or that JavaScript was competing with Java. [...] I was under marketing orders to make it look like Java but not make it too big for it’s britches […] [it] needed to be a silly little brother language.
>

*Brendan Eich, JavaScript creator*

이러한 이유로 자바스크립트는 classes 문법을 도입하는 대신 prototype 을 이용해 객체지향적인 코드를 구현하는 방식을 택하게 됩니다.

라고 합니다......;;;;

클래스까지 가지고오면 자바를 너무 다 따라한 느낌인가...?

그래도 이건 좀 다른 프로그램인데...ㅎㅎ

</details>




#### class 상속
<a id="class-상속"></a>

extends 키워드를 사용   
상속을 받는 클래스는 ‘파생 클래스’(derived classes)라고 함.

```javascript
class BabyRobot extends Robot {
    constructor(name) {
        super(name);
        this.ownName = '아이크';
    }

    sayBabyName() {
// 또한 상속을 받게되면 부모 클래스의 메소드를 사용할 수 있게 됩니다.
// 때문에 this로 접근 할 수 있습니다.
        this.sayYourName();
        console.log('Suceeding you, Father!');
    }
}
```

super (부모클래스 참조)
- 생성자 함수에서 this 값을 사용할 경우 super 함수는   
  반드시 this 보다 먼저 실행되어야 합니다.