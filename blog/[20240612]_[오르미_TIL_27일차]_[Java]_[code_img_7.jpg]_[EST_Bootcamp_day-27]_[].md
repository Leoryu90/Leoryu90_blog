# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
-[객체지향 프로그래밍](#객체지향-프로그래밍) 
  - [자바의 this](#자바의-this)
  - [final & static final](#final-staticFinal)
  - [접근 제어자](#접근-제어자)
  - [Getter, Setter](#getter-setter)



## 💡 객체지향 프로그래밍
<a id="객체지향-프로그래밍"></a>


### 자바의 this
<a id="자바의-this"></a>

`this` 란?   
어떤 인스턴스를 만들면 그 객체 자신을 가르키는 것으로   
this를 이용하여 현재 객체의 맴버변수와 메서드를 호출한다.

사용 예시

```java
public class Person {
    // 멤버 변수
    String name;
    int age;

    // 생성자
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // 메서드
    public void sayHello() {
        System.out.println("Hello, my name is " + this.name); //this
    }

    public void introduce() {
        System.out.println("I am " + this.age + " years old."); //this
    }
}


```


> 주요 특징으로는   
> 같은이름의 지역변수와 맴버변수가 있으면 맴버변수를 호출 할 수 있다.   
> this를 생략하더라도 컴파일러가 자동으로 인스턴스의 맴버변수를 인식하지만   
> 가독성과 명확성을 위해서라도 쓰는 것이 좋다.   
> 

### final & static final
<a id="final-staticFinal"></a>

#### final 필드

final은 초기값이 지정이 되면 런타임중(실행중) 수정을 할 수는 없지만   
처음 초기화 할때 여러 변수로 초기화가 가능하다.

```java
final 타입 필드명 [= 초기값];

public class Person {
    final String nation = "Korea";
	String name;
    
    public Person(String name) {
        this.name = name;
    }
}
```

위의 예시에서 nation은 필드선언시 초기값을 지정한 방식이고   
name은 생성자에서 초기값을 지정한다.

즉 final에서 초기값을 지정하는 방법은 2가지로

- 필드 선언시
- 생성자 에서 초기화

로 생겅이 가능하다.

#### 상수(static final)

static 이라는 키워드 자체가 Java 시스템을 시작하면 바로 올라가기 때문에 여러 값으로   
변경할 수 없다는 특징이 있어 상수라고 말하며 예시로는 파이(3.141592) 를 많이 사용한다.

선언 예시
```java
static final 타입 상수 [= 초기값];

static final 타입 상수;
static {
	상수 = 초기값;
}
```

### 접근 제어자
<a id="접근-제어자"></a>


| 접근 제어자 | 같은 클래스 | 같은 패키지 | 자식 클래스 | 전체 |
| --- | --- | --- | --- | --- |
| public | O | O | O | O |
| protected | O | O | O |  |
| default(packege-private) | O | O |  |  |
| private | O |  |  |  |


- public: 어느 클래스에서나 접근가능
- protected: 자식클래스까지 접근이 가능
- default: 같은 패키지 안에서 접근이 가능
- private: 같은 클래스 안에서만 접근이 가능하다.

보통은 private, public을 많이 쓴다.

### Getter, Setter
<a id="getter-setter"></a>

맴버변수등 클래스의 데이터를 클래스 내부에서 변경하는 것이 아닌 외부에서 변경하는 경우   
치명적인 오류가 발생할 수 있고 그 데이터의 무결성(데이터가 정확한 정보를 가지고 있는지)을   
보장할 수 없어지기 때문에 데이터를 같은 클래스에서 조작을하게 하고 그것을 캡슐화라고 한다.

#### Setter 메소드

설명처럼 외부에서 직접 접근하여 데이터를 바꾸면 오류가 생길 수 있다.   
교안의 예시로는 자동차의 스피드가 있다.

```java
car.speed = -100;
```

속도는 0부터 시작인데 음수로 표현할 수는 없다.   
이런 경우를 방지하기 위해 스피드 맴버변수를 가진 클래스 내부에서  
메소드를 만들어서 변경하는 방법이다.

```java
public class Car {
    private int speed;
		
    public void setSpeed(int speed) {
        if (speed < 0) {
            this.speed = 0;
        } else {
            this.speed = speed;
        }
    }
}
```

이렇게 if를 통해 매개값을 검증해서 유효한 값만 데이터로 저장하게 한다.

#### Getter 메소드

private으로 보호해서 읽는 것도 접근이 제한되어 있어서 이걸 불러줄   
하나의 메서드를 만들어주는 것.

```java
public class Car {
    private int speed;
		
    public double getSpeed() {  //메서드는 퍼블릭으로.
        double km = speed * 1.6;
        return km;
    }
}
```

위의 예시처럼 변환하여 출력을 해줄 수도 있다.

<details>
<summary> 회고 </summary>

TIL을 쓰면서 점점 디테일하게 쓰려고 하는 것 보다는 <br>
복습하면서 리마인드에 초점을 두게 된다.<br>
내용은 조금 적어지지만 이해하는 것에 초점을 두니 <br>
좀 편해졌다.<br>
<br>
TIL 시간할당을 조금 줄이고 이론과 코테에 힘을 주는 것!<br>
공부를 빨리 더 집중해서 진행하여 실력을 늘리고 <br>
잘하는 친구들과 프로젝트도 진행하고 싶습니다.<br>
더 노력하자!

</details>


