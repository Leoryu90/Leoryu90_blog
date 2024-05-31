# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [문자열](#String)
  1. [문자열 내장메서드](#내장메서드)
     1. [equals](#equals)
     2. [indexof](#indexof)
     3. [contains](#contains)
     4. [charAt](#charAt)
     5. [replaceAll](#replaceAll)
     6. [substring](#substring)
     7. [split](#split)
  2. [문자열 포맷팅 메서드 - format](#format)
  3. [StringBuffer / StringBuilder](#StringBuffer-StringBuilder)
  4. [append / insert](#append)
- [배열 타입](#배열-타입)
- [연산자](#연산자)
  1. [단항 연산자](#단항-연산자)
  2. [부호 연산자](#부호-연산자)
  3. [증감 연산자](#증감-연산자)
  4. [논리 부정 연산자(!)](#논리-부정-연산자)


## 💡 문자열
<a id="String"></a>

"" 큰 따옴표를 사용하여 문자로 구성된 문장을 문자열이라고 함.
```java
"123"
"Hello World!"
"s"
// 한글자, 숫자 도 ""큰따옴표 안에 있으면 문자열에 포함

String a = "123";
String a = new String("123");

두가지 방식이 있지만 첫번째 방식을 추천
```

### 문자열 내장메서드
<a id="내장메서드"></a>

#### equals
<a id="equals"></a>

문자열을 비교하는 메서드.   
true / false로 반환해줍니다.

```java
System.out.println(변수명.equals(비교할_변수명));
```

> == 을 쓰면 같은거 아닌가 하는 의문을 가졌는데 설명해주셨습니다.   
> == : 같은 주소값을 갖는지를 판별   
> 

#### indexOf
<a id="indexOf"></a>

지정하는 문자열이 시작되는 **위치값**을 반환

```java
String a = "Hello World!";
System.out.println(a.indexOf("!")); // 11 을 반환
```

#### contains
<a id="contains"></a>

특정 문자열이 포함되어있는지 여부를 true / false로 리턴

```java
String a = "Hello World!";
System.out.println(a.contains("World")); // true 를 반환
```

#### charAt
<a id="charAt"></a>

문자열에서 특정 위치의 **문자**(1글자)를 리턴

```java
String findChar = "What is your job";
System.out.println(findChar.charAt(13)); // j를 반환
// What is your job에서 W를 0, h 는 1, 순서로 0부터 시작! 
```

#### replaceAll
<a id="replaceAll"></a>

문자열에서 특정 문자열을 다른 문자열로 바꿀 때 사용

```java
String a = "Hello World!";
System.out.println(a.replaceAll("World", "Spring")); //Hello Spring! 반환
```
> replace는 인자값을 문자열을 받고   
> replaceAll은 정규식을 받는다   
> 
> 정규식을 찾아보니 특정한 형태나 규칙을 가진 문자열을 찾아내기 위해 나타내는 패턴이라고
> 설명 되어있다.   
> 
> 즉 replace는 해당 문자열만 딱 찾을 수 있고    
> replaceAll은 정규표현식을 통하여 다양한 형태의 문자열을 찾을 수 있다.

#### substring
<a id="substring"></a>

문자열에서 **특정 문자열**을 뽑아낼 때 사용

```java
String a = "WEEEE ASKE ;ND";
System.out.println(a.substring(0, 3) + a.substring(8, 10) + a.substring(12, 14));
// WEEKEND 반환
```

> 많이 쓴다고 함.   
> 어떠한 자료를 받았을 때에 원본을 해치지 않고 사용할 수 있게 해줌.
> 

#### split
<a id="split"></a>

문자열을 특정한 구분자로 나누어 **배열**로 반환.

```java
String a = "a:b:c:d";
String[] result = a.split(":");  // result는 {"a", "b", "c", "d"}
// :를 기준으로 나눠서 배열로 만든 식
```

#### concat
<a id="concat"></a>

문자열을 합치는 역할을 하고, 결과값은 문자열로 반환

```java
String result = "Hello";
result = "Hello" + "!";

System.out.println(result); //Hello!
System.out.println(result.concat("!")); //Hello!!
System.out.println(result); //Hello!
```

위에서 정리한 메서드 목록

| 메서드명 | 역할 |
| --- | --- |
| equals(비교 문자열) | 두개의 문자열이 같은지 비교하여 결과를 true/false로 반환 |
| indexOf(문자) | 인자로 받은 문자가 시작되는 위치(인덱스)를 반환 |
| contains(특정 문자열) | 특정 문자열이 포함되어있는지를 true/false로 반환 |
| charAt(특정위치 인덱스) | 인자로 받은 특정 위치(인덱스)의 문자를 반환 |
| replaceAll(문자열, 문자열) | 인자로 정규식(regex)을 받아서 해당 형태로 문자열을 변경할 때 사용 |
| replace(regex, 문자열) | 문자열에서 특정 문자열을 다른 문자열로 바꿀 때 사용 |
| substring(시작인덱스, 끝인덱스) | 문자열에서 특정 문자열을 뽑아낼 때 사용 |
| toUpperCase() | 문자열을 모두 대문자로 변경할 때 사용 |
| toLowerCase() | 문자열을 모두 소문자로 변경할 때 사용 |
| split(구분자) | 문자열을 특정한 구분자로 나누어 문자열 배열로 반환 |
| concat(”합치고자 하는 문자열”) | 인자로 받은 문자열을 이전 문자열과 합쳐서 반환 |

------------------

### 문자열 포맷팅 메서드 - format
<a id="format"></a>

문자열 안의 특정한 값을 바꿀 수 있게 해주는 것

```java
String.format("... %s.. %s..", 치환값1, 치환값2);
```

> 치환의 개수는 제한이 없음   
> 한계는 없지만 가독성의 문제가 있다고 하심.
> 

### StringBuffer / StringBuilder
<a id="StringBuffer-StringBuilder"></a>

자바에서 대표적으로 문자열을 다루는 클래스로   
String, StringBuffer, StringBuilder 3가지를 지원   
StringBuffer와 StringBuilder는 문자열을 추가하거나 변경할 때(연산) 주로 사용하는 자료형
<br>

String 자료형으로 +연산이나 concat() 메소드로 문자열을 이어 붙일 수 있지만,   
이때 String 특성상 새로운 객체를 생성하고 String 공간을 할당하기 때문에    
공간의 낭비 뿐만 아니라 속도면에서도 비효율적이라는 단점

```java
String result = "";

    result += "Hello";
    result += " Java";
    result += " World!";

    System.out.println(result);

    // 간단한 문자는 스트링  더 넣고 하는건 빌더, 버퍼
    StringBuilder sb = new StringBuilder();
    sb.append("Hello");
    sb.append(" Java");
    sb.append(" World!");

    System.out.println(sb);

    StringBuffer sb2 = new StringBuffer();
    sb2.append("Hello");
    sb2.append(" Java");
    sb2.append(" World!");

    System.out.println(sb2);
```

> StringBuffer와 StringBuilder의 가장 큰 차이점   
> 
> Stringbuffer는 멀티스레드 환경에서 thread safe 하다는 장점   
> StringBuilder는 성능이 우수하다는 장점 이라고 써있고   
> 
> 찾아보니 Stringbuffer는 Synchronized Keyword가 있어서 동기화를 지원 멀티스레드 환경에서도
> 동기화가 가능하여 안전한 프로그램이 필요할 때, 스레드에 안전이 걱정되면 쓴다고 함.   
> 동기화 처리로 인하여 성능이 빌더보다 느림.
>


#### append / insert
<a id="append"></a>

문자열을 생성(추가)하는 메서드

````java
StringBuffer sb = new StringBuffer();
sb.append("Hello");
sb.insert(0, "World");
sb.insert(6, "2");
sb.insert(1, "3");
sb.insert(10, "4");

System.out.println(sb); // 출력값 : W3orldH2el4lo

insert와 비슷 기능을 하지만 위치지정이 가능한 insert
````

#### substring
<a id="substring"></a>

String 자료형의 subString과 동일한 역할을 합니다.   

```java
subString(시작 인덱스, 끝 인덱스)

StringBuffer buffer = new StringBuffer();
buffer.append("Hello ");
buffer.append("Java ");
buffer.append("World!");
System.out.println(buffer.substring(6));      // Java World!
System.out.println(buffer.substring(6, 7));   // J
```

## 💡 배열 타입
<a id="배열-타입"></a>

배열은 자바에서 여러 개의 값을 저장하는 데 사용되는 데이터 구조  
각 요소는 인덱스를 사용하여 액세스할 수 있습니다. 배열은 크기가 고정되어 있으며,    
한 번 생성된 후에 크기를 변경할 수 없습니다



```java
// 배열 선언
type[] arrayName;

// 배열 초기화
arrayName = new type[length];

// int형 100크기의 배열
int[] arr = new int[100];

// String형 1000크기의 배열
String[] arr2 = new String[1000];
```

> 추가적인 배열 공부는 추후 조건,반복문 이후에 나가기로 하셨습니다.
>


## 💡 연산자
<a id="연산자"></a>


### 단항 연산자
<a id="단항-연산자"></a>

단항 연산자는 피연산자가 하나뿐인 연산자를 말합니다.   
여기에는 부호 연산자(+, -), 증감 연산자(++, --), 논리 부정 연산자(!) 등

#### 부호 연산자(+, -)
<a id="부호-연산자"></a>

부호 연산자에는 양수나 음수를 표시하는 +, -가 있습니다.   

**양의 부호 연산자**: 변수나 값 앞에 +를 붙여서, 수치를 명시적으로 양수로 표현할 때 사용(대부분의 경우 생략)   
**음의 부호 연산자**: 변수나 값 앞에 -를 붙여서, 해당 수치의 부호를 반전

```java
int positive = 10;
int negative = -10;

System.out.println("양의 부호 연산자 적용: " + (+positive)); // 10
System.out.println("음의 부호 연산자 적용: " + (-positive)); // -10
System.out.println("음의 부호 연산자로 부호 반전: " + (+negative)); // -10
System.out.println("음의 부호 연산자로 다시 부호 반전: " + (-negative)); // 10
```

#### 증감 연산자(++, --)
<a id="증감-연산자"></a>

1. 전위 증감 연산자 (Prefix Increment and Decrement)
```java
++값: 변수의 값을 1 증가시킨 후, 표현식을 이행
--값 : 변수의 값을 1 감소시킨 후, 표현식을 이행
```


2. 후위 증감 연산자 (Postfix Increment and Decrement)
```java
- 변수++: 표현식을 이행 후, 변수의 값을 1 증가
- 변수--: 표현식을 이행 후, 변수의 값을 1 감소
```

**예시**
```java
int a = 100;
int b = 100;

System.out.println("전위 감소 연산자: " + (--a));
System.out.println("후위 감소 연산자: " + (b--));
System.out.println("전위 감소 연산자: " + (--a));
System.out.println("후위 감소 연산자: " + (b--));
System.out.println("전위 감소 연산자: " + (--a));
System.out.println("후위 감소 연산자: " + (b--));

// 결과값
// 전위 감소 연산자: 99
// 후위 감소 연산자: 100
// 전위 감소 연산자: 98
// 후위 감소 연산자: 99
// 전위 감소 연산자: 97
// 후위 감소 연산자: 98
```


#### 논리 부정 연산자(!)
<a id="논리-부정-연산자"></a>

불리언 값의 반대 값을 반환하는 단항 연산자

- !true: false
- !false: true

```java
boolean isRaining = true;

    if (isRaining) {
      System.out.println("하늘에서 비가 옵니다");
    }

    if (!isRaining) {
      System.out.println("김태희가 옵니다");
    }

    boolean isSunny = false;

    if (!isSunny) {
      System.out.println("날씨가 맑습니다.");
    } else {
      System.out.println("졸려...ㅋㅋㅋ");
    }
```


<details>
<summary> 회고  </summary>
자바를 입문하고 TIL 시간이 늘었다....<br>
너무 바쁘다 <br>
<br>
CS 스터디, Java 스터디, 코테 스터디<br>
3개의 스터디로 인한 피곤이 몰려옵니다.<br>
<br>
정신력이 부디 버텨주길 바라며 TIL 마무리<br>
<br>
수업중 점점 궁금한게 많아지고 개인 공부시간이 늘어가고 있습니다.<br>
살려주세요.
</details>
