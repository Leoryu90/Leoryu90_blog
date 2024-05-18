# 목차
- [this](#this)
  1. [this 란?](#thisIs)
- [객체지향 프로그래밍](#객체지향-프로그래밍)


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



