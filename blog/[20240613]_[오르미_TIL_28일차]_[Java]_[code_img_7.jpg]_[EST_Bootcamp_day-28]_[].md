# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 상속](#상속)
  - [클래스 상속](#클래스-상속)
  - [부모 생성자 호출](#부모-생성자-호출)
  - [메소드 오버로딩과 오버라이딩](#메소드-오버로딩과-오버라이딩)
  - [추상클래스](#추상클래스)




## 💡 상속
<a id="상속"></a>

`상속`

일반적인 용어로 생각하더라도 부모에게서 물려받는 것을 상속이라고 한다   
자바에서의 상속도 부모클래스가 자식 클래스에게 필드, 메소드 들을 물려주어서   
자식클래스가 사용을 할 수 있다.

<img src="img/day28/inherit.png" width="500" height="350" alt="상속에 대하여 설명하는 그림">

> 제한접근자에서 배웠듯이 default, private 의 접근제어자는 상속 받을 수 없다.
>
### 클래스 상속
<a id="클래스-상속"></a>

현실: 부모가 어떤 자식에게 상속을 할지 정함.
코딩: 자식이 어떤 부모에게 상속을 받을지 정함.

**예시**

```java
class 자식클래스 extends 부모클래스 {}

class SportsCar extends Car {}
```

> 자바는 다중 상속을 지원하지 않음.
>
### 부모 생성자 호출
<a id="부모-생성자-호출"></a>

자식 객체를 생성하면 자식 객체가 생성되고,   
부모의 필드값들을 다음 코드를 메모리에 올라가게 된다.

만약 Dog 라는 자식 객체를 이용한다면

```java
Dog dog = new Dog();
```

<img src="img/day28/inherit_heap.png" width="500" height="400" alt="상속에 대하여 설명하는 그림">

<details>
<summary> 궁금한점 </summary>

위의 그림처럼 하나의 객체가 생성이 된다면 <br>
일반적인 인스턴스처럼 각자의 this와 super가 적용이 되나요? <br>
부모 까지 힙에 올라가면서 객체 1개를 생성할 때 마다 각각 메모리를 차지하는지....?

</details>

위에서 한 예시처럼 객체를 생성하게되면 부모의 생성자를 따로 명시적으로 선언하지 않아도   
자식 생성자 맨 첫줄에서 컴파일러가 자동으로 호출해준다.

```java
// 자동으로 호출되는 것
public Dog {
	super(); // 부모를 호출
}
```

만약 부모 클래스에 기본 생성자가 없고 **매개 변수가 있는 생성자만 있다면**    
자식 생성자에서 반드시 부모 생성자 호출을 위해 super(매개값, …)를   
**명시적으로 호출**해야합니다.

예시

```java
// 부모클래스
public class Person {
	String name;
	String ssn;

	public Person(String name, String ssn) {  // 매개변수가 있는 생성자
		this.name = name;
		this.ssn = ssn;
	}
}
```

```java
//자식 클래스
public class Student extends Person {
	int studentNo;

	public Student(String name, String ssn, int studentNo) {
		super(name, ssn);  // 이 상황에선 필수!
		this.studentNo = studentNo;
	}
}
```

### 메소드 오버로딩과 오버라이딩
<a id="메소드-오버로딩과-오버라이딩"></a>


지금 이 개념을 쓰는 이유는   
부모클래스가 모든 상황에 맞게 설게될 수 없어서   
자식클래스에서 수정, 확장의 기능을 가진다.


- 오버로딩: 동일한 이름의 메서드를 사용하여 파라미터값만 다르게 받을 수 있다.   
  (이름이 같은 메서드를 여러개 쓰면서 값만 다르게 받을 수 있다.)
- 오버라이딩: 재정의 하는것으로 덮어쓰기와 같은 효과를 지닌다.

오버로딩의 예시

```java
// 부모 클래스
public void say() {
    System.out.println("my name is " + name);
}

//자식 클래스 
public void say(String name) {
    System.out.println("my name is " + name);
}
```

위의 예시에서 처럼 say()라는 함수는 2가지를 모두 쓸 수 있다.

오버라이딩 예시
```java
// 부모 클래스
void method2() {
    System.out.println("Parent2.method2");
  }
//자식 클래스 
void method2() {
    System.out.println("Child2.method2");
}
```

오버라이딩은 자식에서 재정의를 했기 때문에 자식의 객체로 생성했다면   
자식의 메서드만 쓸 수 있다.

> 주의할 부분
> - 부모의 메소드와 동일한 시그니처(리턴타입, 메소드이름, 매개변수 리스트)를 가져야 한다.
> - 부모 클래스의 메소드보다 접근 제한을 더 강하게 오버라이딩 할 수는 없다. (private, default)
> - 새로운 예외(Exception)를 throws 할 수 없다. (예외처리 Part에서 배웁니다)
>
### 추상클래스
<a id="추상클래스"></a>

추상 메서드란 **자식 클래스에서 반드시 오버라이드** 해야만 사용할 수 있는 메소드

학습을 들어갈 때 재미있는 말이 써있다.

```java
🖊️ 인터페이스 역할도 하면서, 클래스의 기능도 가지고있는
자바의 돌연변이 같은 클래스인 추상클래스에 대해 알아봅시다.
```

강사님이 역할이 비슷한데 요즘은 인터페이스를 많이 쓴다고 하셨다.   
주요 개념을 살펴보자.

<img src="img/day28/class.png" width="500" height="300" alt="상속에 대하여 설명하는 그림">

위의 예시에는 동물....에 왠 인섹트? 지만    
하나의 종류로 묶어서(사람이라면 성별, 혈액형 등) 공통점을 상속을 할 수 있는 개념이다.


**추상메서드**   
추상클래스란, 추상메서드를 하나 이상 포함하는 클래스로   
다음과 같이 선언한다.

```java
abstract 리턴타입 메소드명();

public abstract void sound();   // 추상 메소드
```

**추상 클래스**

위에서 말한 것처럼 추상메서드가 들어간 클래스도 선언해야한다.

```java
public abstract class 클래스명 {
    // 필드
    // 생성자
    // 메서드
    // 추상메서드
}
```

#### 추상 클래스의 오버라이딩

추상클래스는 공통적인 메서드를 가지고 있지만 그걸 딱정해서 실체 클래스에 넘겨줄 수 없다.   
사람이라고 치면 성별이 남자만 있거나 여자만 있는게 아닌것처럼

그래서 **오버라이딩(재정의)**이 필요하다

예시로 동물의 울음소리를 추상메서드로 정의한다면

```java
public abstract class Animal {
	public abstract void sound();  // 추상메소드 - 메소드의 타입과 이름만 정의
}
```

<img src="img/day28/over.png" width="500" height="350" alt="추상 클래스에서의 오버라이딩에 대하여 설명하는 그림">

```java
public class Dog extends Animal {
	public Dog() {
		this.kind = "포유류";
	}

	@Override
	public void sound() {           // 추상 메소드 재정의
		System.out.println("멍멍");
	}
}
```

위의 예시처럼 강아지로 객체를 만들면 소리에 따라 오버라이딩이 필요하다.

<details>
<summary> 회고 </summary>

점점 개념적인 얘기가 많이 나오는데 이해하는건 무리가 없습니다. <br>
그런데 진짜 공부를 하다보니 점점 공부해야할게 더 많아지고 필요해지다보니 <br>
계속 시간이 더 있었으면 하는 마음이 생깁니다.ㅎㅎ <br>
조급해하지 말고 하나하나 클리어 하면서 화이팅 하겠습니다!

</details>