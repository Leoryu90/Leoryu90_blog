# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 인터페이스](#인터페이스)
  - [인터페이스 구현과 사용](#인터페이스-구현과-사용)
  - [디폴트 메서드](#디폴트-메서드)
  - [인터페이스 상속](#인터페이스-상속)
  - [인터페이스의 다형성](#인터페이스의-다형성)




## 💡 인터페이스
<a id="인터페이스"></a>

전에 배웠던 추상클래스와 비슷하지만 다른 개념으로   
다른 클래스를 작성할 때 기본이 되는 틀을 제공하면서,   
다른 클래스 사이의 중간 매개 역할을 하는 일종의 추상 클래스이다.

기본 양식

```java
//인터페이스의 선언은 class 키워드 대신에 interface 키워드를 사용
//인텔리 제이에서 만들때 인터페이스로 만들면 된다.
[ public ] interface 인터페이스명 { ... }

interface 인터페이스명 {   //인터페이스 생성
}

class Tiger extends 상속 implements 인터페이스명 {

}

```

### 인터페이스 구현과 사용
<a id="인터페이스-구현과-사용"></a>

인터페이스에서 메소드를 구현해보자.

```java
interface 인터페이스명 {
	타입 메소드명();
}

interface 오르미5기 {
    String study();
}
```

위의 예시처럼 인터페이스는 메소드의 내용이 없다.   
이유는 인터페이스를 implements 한 클래스에서 강제적으로 구현하게하는 틀과 같다.

```java
class GoodStudent extends Human implements 오르미5기{
    @Override
    public String study() {
        return "집중해서 공부를 하고 있습니다.";
    }
}

class Ryu {
    private String name = "유석호";
    
    void studyEveryday (GoodStudent student) {
        System.out.println("학생" + this.name + "가 " + student.study());
    }
}


public static void main(String[] args) {
    Ryu ryu = new Ryu();

    GoodStudent student = new GoodStudent();
    ryu.studyEveryday(student);
}
```

### 디폴트 메서드
<a id="디폴트-메서드"></a>

인터페이스에서 구현체를 제공하는 메서드

디폴트 메서드 정의

```java
public interface MyInterface {
    void abstractMethod();

    default void defaultMethod() {
        System.out.println("This is a default method.");
    }
}
```

디폴트 메서드 사용법

```java
public class MyClass implements MyInterface {
    @Override
    public void abstractMethod() {
        System.out.println("Implementing abstract method.");
    }

    public void callDefaultMethod() {
        defaultMethod();
    }
}

MyClass obj = new MyClass();
obj.callDefaultMethod(); // Output: This is a default method.
```

디폴트 메서드 오버라이딩

```java
public class MyOverridingClass implements MyInterface {
    @Override
    public void abstractMethod() {
        System.out.println("Implementing abstract method.");
    }

    @Override
    public void defaultMethod() {
        System.out.println("Overriding default method.");
    }
}

MyOverridingClass obj = new MyOverridingClass();
obj.defaultMethod(); // Output: Overriding default method.

```

다중 상속과 디폴트 메서드

```java
public interface Interface1 {
    default void defaultMethod() {
        System.out.println("Interface1's default method.");
    }
}

public interface Interface2 {
    default void defaultMethod() {
        System.out.println("Interface2's default method.");
    }
}

public class MultipleInheritanceClass implements Interface1, Interface2 {
    @Override
    public void defaultMethod() {
        Interface1.super.defaultMethod();
    }
}

MultipleInheritanceClass obj = new MultipleInheritanceClass();
obj.defaultMethod(); // Output: Interface1's default method.

```

디폴트 메서드는 위의 사용예시를 쭉 보면 이해가 된다.   

- 디폴트 메서드를 사용하면 기존 인터페이스에 새로운 기능을 추가할 수 있습니다.
- 구현 클래스는 디폴트 메서드를 상속받으며, 필요에 따라 오버라이드할 수 있습니다.
- 다중 상속 시 디폴트 메서드 충돌에 주의해야 하며, 명시적으로 사용할 디폴트 메서드를 지정해야 합니다.

### 인터페이스 상속
<a id="인터페이스-상속"></a>

인터페이스는 클래스와다르게 다중 상속이 가능하다.   
하위 인터페이스를 구현하는 클래스는 하위 메소드 뿐만 아니라   
**상위 인터페이스**의 **모든 추상 메소드에 대한 실체 메소드**를 갖고있어야 한다

```java
public interface 하위인터페이스 extends 상위인터페이스1, 상위인터페이스2, ... {
    상위인터페이스1(); // 메서드 구연
    상위인터페이스2(); // 메서드 구현
}
```


### 인터페이스의 다형성
<a id="인터페이스의-다형성"></a>

하나의 타입에 대입되는 객체에 따라 실행 결과가 다양한 형태로 나오는 성질   
예시로 보는게 이해가 빠르다.

<img src="img/day30/repo.png" width="500" height="350" alt="">
다형성은 객체를 ‘부품화’ 시킵니다.

ProfileRepository를 구현한 클래스로 ProfileDBRepository를 선택했습니다.   
개발 완료 후 테스트를 해보니 DB로 저장하는 방식에 문제가 생겨 Memory저장을 사용해야합니다.   
이런 경우에 ProfileRepository 인터페이스를 구현한 ProfileMemoryRepository를 만들고 단 한줄만 수정해서 프로그램을 재실행할 수 있습니다.

```java
public interface ProfileRepository {
    void save();
}
```

아래가 중요한 부분

```java
public class ProfileService {
    ProfileRepository repository;

    public void saveProfile() {
        repository = new ProfileDBRepository();   // 이 부분만 바꿔 끼우면 됨
        repository.save();
    }
}
```

```java
// 구현 클래스
public class ProfileDBRepository implements ProfileRepository {

    @Override
    public void save() {
        System.out.println("DB에 프로필 저장하는 기능");
    }
}
```

```java
// 구현 클래스
public class ProfileMemoryRepository implements ProfileRepository {
    @Override
    public void save() {
        System.out.println("메모리에 프로필 저장하는 기능");
    }
}
```

인터페이스를 이용하면 어떠한 문제가 생긴다면 유지보수가 쉬워진다.





<details>
<summary> 회고 </summary>

인터페이스 시간은 좀 개념이해가 중요한거 같다.   <br>
쓸 내용이 많지는 않은데 이해를 하는게 조금 걸린 느낌. <br>
<br>
인터페이스에서는 궁금한거는 생기지 않았습니다!ㅎㅎ <br>
위클리 퀴즈가 어렵지만...<br>
해결하면서 공부하는....<br>
<br>
주말 상관 안하고 계속 공부하니 오늘이 월요일인지 별로 체감을 못하는<br>
월요병이 딱히 없는 하루였습니다;;


</details>