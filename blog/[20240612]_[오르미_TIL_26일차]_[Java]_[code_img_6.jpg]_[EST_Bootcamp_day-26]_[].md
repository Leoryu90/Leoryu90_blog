# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [함수](#함수)
  - [함수 구조](#함수-구조)
  - [함수의 활용 - 매개변수와 전달인자](#매개변수와-전달인자)
  - [메서드](#메서드)
  - [외부 클래스를 가져와 사용하기](#외부-클래스)
-[객체지향 프로그래밍](#객체지향-프로그래밍) 
  - [클래스의 구조와 특징](#클래스의-구조와-특징)



## 💡 함수
<a id="함수"></a>

어떤 매개변수를 받으면 작동하여 어떠한 값을 반환하는 방식


### 함수 구조
<a id="함수-구조"></a>

기본구조
```java
반환타입 함수이름(매개변수) {
    // 메서드 몸체(Body)
    return 반환값;
}
```

- `반환타입`은 함수가 반환하는 값의 타입입니다. 반환값이 없는 경우 `void`를 사용합니다.
- `함수이름`은 함수에 대한 고유한 식별자입니다.
- `매개변수`는 함수에 전달되는 값들로, 필요한 개수만큼 작성할 수 있습니다. 매개변수가 없는 경우 괄호를 비워둡니다.
- `메서드 몸체(Body)`는 실제 작업을 수행하는 코드 블록을 말합니다.
- `return` 키워드는 **함수의 실행을 중단**하고 값을 반환합니다. 반환값이 없는 경우 `return` 문을 사용하지 않습니다.

### 함수의 활용 - 매개변수와 전달인자
<a id="매개변수와-전달인자"></a>


| 용어 | 번역 | 의미 |
| --- | --- | --- |
| Parameter | 매개변수 | 함수와 메서드에 입력 변수 이름 |
| Argument | 전달인자, 인자, 인수 | 함수와 메서드에 실제 입력되는 값 |


> 파선아실(파라미터는 선언, 아규먼트는 실제 값)

### 메서드
<a id="메서드"></a>

기본구조

```java
//메인 메서드
public static void main(String[] args) {
    // 프로그램 실행 코드
}
```

> 주의사항   
> 메서드는 클래스 안에 들어가야 한다.
>

- `public`은 메소드가 어디에서나 접근할 수 있는 **공개적인 메소드**임을 나타냅니다.
- `static`은 메소드가 **정적 메소드**임을 나타냅니다. 정적 메소드는 클래스의 **인스턴스를 생성하지 않고도 호출**할 수 있습니다.
- `void`는 메소드가 **반환하는 값이 없음**을 나타냅니다.
- `main`은 메소드의 이름입니다. (다른 이름이 들어갈 수 있다. 메인이 아니라면)
- `String[] args`는 `main` 메소드에 전달되는 인수를 저장하는 문자열 배열입니다. 이는 프로그램 실행 시 커맨드 라인에서 전달된 인수를 받을 수 있습니다.

<details>
<summary> 잘 모르겠는 점 </summary>

String[] args 이부분의 설명은 잘 모르겠습니다.

</details>

### 외부 클래스를 가져와 사용하기
<a id="외부-클래스"></a>

예시

```java
public class External {
    int add(int a, int b){
        int sum = a + b;
        return sum;
    }
}
```

1. **클래스 파일 가져오기:** 먼저, 사용하려는 클래스가 정의된 .java 파일이 필요합니다. 이 파일은 같은 디렉토리에 있거나, Java의 **`import`** 문을 사용하여 다른 패키지에서 가져올 수 있습니다.
2. **컴파일:** 외부 클래스 파일과 메인 파일 모두를 컴파일합니다. Java 소스 파일(.java)은 Java 컴파일러(javac)에 의해 클래스 파일(.class)로 컴파일됩니다.
3. **클래스 사용:** 메인 파일에서 외부 클래스를 인스턴스화하거나, 외부 클래스의 정적 메서드를 호출하여 사용합니다.

import 예시

<img src="img/day26/import.png" width="500" height="100" alt="">

## 💡 객체지향 프로그래밍
<a id="객체지향-프로그래밍"></a>

현실에있는 어떠한 것을 코드로 추상화하는 것으로

데이터, 기능으로 이루어져 있다.

```java
public class Person {
    // 멤버 변수
    String name;
    String phoneNum;

    // 생성자
    public Person(String name, String phoneNum) {
        this.name = name;
        this.phoneNum = phoneNum;
    }

    // 메서드
    public void sayHello() {
        System.out.println("Hello, my name is " + name);
    }

    public void teaching(Student student){ //여기서 클래스 호출
        student.levelUp();
    }
}
// 다른 클래스
public class Student {
  int level;
  public Student(){
    this.level = 1;
  }

  public void levelUp(){
    level++;
    System.out.println("레벨이 1 상승했습니다!");
  }
}
```

위와 같이 객체와 객체가 서로 상호작용하게 프로그래밍 하는 것이   
**객체지향 프로그램**이라고 한다.

> 💡 **절차 지향 VS 객체 지향**   
> **절차지향 프로그래밍**: 코드의 **재사용성이 낮고 유지보수가 어려움**,   
> 작은 프로그램이나 간단한 작업에는 적합할 수 있습니다.   
> **객체지향 프로그래밍**: 코드의 **재사용성과 유지보수성을 높음**,   
> 복잡한 프로그램을 구조화하고 확장하기 쉽게 만들어줍니다.
>
 
## 클래스의 구조와 특징
<a id="클래스의-구조와-특징"></a>

기본적인 구조

```java
public class ClassName {
    // 멤버 변수 (클래스의 상태를 나타내는 데이터)
    // 생성자 (객체를 초기화하는 메서드)
    // 메서드 (클래스의 동작을 정의하는 코드)
}

```

내가 만든 예시

```java
public class Human {
    // 멤버 변수
    String name;
    int age;
    String place;
    
    //생성자
    public Human(String name, int age, String place) {
        this.name = name;
        this.age = age;
        this.place = place;
    }
    //메서드
    public void sayHello() {
        System.out.println("안녕하세요. 저는 " + name + " 입니다.");
    }
}
```

> 생성자 (Constructor)   
> 클래스 이름과 같은 이름을 가진 특별한 메서드로,객체가 생성될 때 호출됩니다.   
> 생성자는 객체의 초기 상태를 설정하는 데 사용됩니다.
> 생성자는 생략하는게 가능하지만, 생략하는 경우 매개변수를 전달할 수 없기 때문에 복잡한 클래스에는 적절하지 않습니다.
> 


<details>
<summary> 회고 </summary>

본격적인 객체지향의 시작. <br>
살짝 어려워진 느낌은 있지만 이해하는데 무리는 없었다.<br>
자바 따로 듣는 강의가 절실하게 필요한 생각이 든다....<br>
이미 결제는 완료ㅎㅎ

</details>


