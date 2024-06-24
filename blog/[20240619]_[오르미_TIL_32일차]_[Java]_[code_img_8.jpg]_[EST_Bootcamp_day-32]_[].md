# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 제네릭](#-제네릭)
  - [제네릭이란?](#제네릭이란)
  - [제네릭타입을 사용하는 방법과 이유](#제네릭타입을-사용하는-방법과-이유)


## 💡 제네릭
<a id="-제네릭"></a>

### 제네릭이란?
<a id="제네릭이란"></a>

데이터의 타입(data type)을 일반화(generalize) 한다는 것

**장점**

- 컴파일시 미리 타입이 정해지기 때문에,   
  타입 검사나 변환 같은 번거로운 작업을 생략할 수 있습니다.
- 클래스나 메소드 내부에서 사용하는 타입 안정성을 높일 수 있습니다.

#### 제네릭을 사용하는 이유

잘못된 타입이 사용될 수 있는 문제를 **컴파일 과정에서 제거**할 수 있게 되었습니다.

사용예시
```java
List<Youtube> youtubeList = new ArrayList<Youtube>();

youtubeList.add(new Youtube());   
youtubeList.add(new DisneyPlus());   // 컴파일 에러 발생. Youtube 외에 다른 타입 저장불가
```

그럼 타입을 지정했을 때 좋은점은 뭘까?   
예시로 들면 ArrayList객체를 제네릭 없이 쓰면 타입이 Object라서   
값을 받을 때마다 타입을 변환해야한다.

제네릭 지정 전
```java
List list = new ArrayList();
list.add("Hello");
String str = (String) list.get(0); //타입변환
```
제네릭 지정후
```java
List<String> list = new ArrayList<String>(); //제네릭
list.add("Hello");
String str = list.get(0);
```

### 제네릭타입을 사용하는 방법과 이유
<a id="제네릭타입을-사용하는-방법과-이유"></a>

제네릭 타입은 타입을 파라미터로 가지는 클래스와 인터페이스를 말한다.

사용예시
```java
public class Box<T> {  // String
  private T t;

  public T get() {
    return t;
  }

  public void set(T t) {
    this.t = t;
  }
}
```

```java
public class GenericExample {
    public static void main(String[] args) {
        Box<String> box = new Box<>();
        box.set("hello");

        String str = box.get();
        System.out.println(str);

        Box<Integer> box2 = new Box<>();
        box2.set(9);

        int value = box2.get();
        System.out.println(value);
    }
}
```

위의 예시처럼 1개의 Box 클래스로 여러 타입의 객체를 만들 수 있다.

제네릭은 아래 표의 타입들이 많이 쓰인다.

| 타입    | 설명      |
|-------|---------|
| `<T>` | Type    |
| `<E>` | Element |
| `<K>` | Key     |
| `<V>` | Value   |
| `<N>` | Number  |

반드시 한 글자일 필요는 없고 설명과 반드시 일치해야 할 필요도 없다.  
예로들어 <Ele>라고 해도 전혀 무방하다.   
다만 **대중적**으로 통하는 통상적인 선언이 가장 편하기 때문에   
위와같은 **암묵적인 규칙**이 있을 뿐이다.















<img src="img/day30/" width="500" height="350" alt="">


<details>
<summary> 회고 </summary>



</details>