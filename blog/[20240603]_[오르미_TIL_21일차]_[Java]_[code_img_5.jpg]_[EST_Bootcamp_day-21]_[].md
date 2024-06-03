# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [이항 연산자](#이항-연산자)
  1. [산술 연산자](#산술-연산자)
  2. [문자열 연결 연산자](#문자열-연결-연산자)
  3. [비교 연산자](#비교-연산자)
  4. [논리 연산자](#논리-연산자)
     -[AND (&&)](#AND)
     -[OR (논리합)](#OR)
     -[XOR (배타적 논리합)](#XOR)
     -[NOT (논리 부정)](#NOT)
  5. [비트 연산자 (&, |, ^, ~, <<, >>, >>>)](#비트-연산자)
     -[비트 논리 연산자](#비트-논리-연산자)
     -[논리 부정](#논리-부정)
  6. [비트 이동 연산자(쉬프트 연산자)](#비트-이동-연산자)
- [삼항 연산자](#삼항-연산자)
- [if문](#if)
  1. [if 조건문](#if-조건문)
  2. [논리 연산자](#if-논리-연산자)
- [switch 문](#switch)

## 💡 이항 연산자
<a id="이항-연산자"></a>

### 산술 연산자
<a id="산술-연산자"></a>

자바에서는 다양한 산술 연산자를 사용하여 수학적인 계산을 수행할 수 있습니다.

- 덧셈(`+`): 두 개의 값을 더합니다.
- 뺄셈(`-`): 첫 번째 값에서 두 번째 값을 뺍니다.
- 곱셈(`*`): 두 개의 값을 곱합니다.
- 나눗셈(`/`): 첫 번째 값을 두 번째 값으로 나눕니다.
- 나머지(`%`): 첫 번째 값을 두 번째 값으로 나눈 **나머지를 반환**합니다.

> 기본적으로 수학 개념으로 생각하면 되지만   
> %는 중요함. (나머지 값만 반환)   
> 추가 포인트는 자바에서는 자료형이 굉장히 중요해서   
> 기본은 int로 적용되며 다른 자료형끼리 연산할 경우   
> 메모리값이 큰쪽, 그리고 정수와 실수끼리 연산은 실수로 반환됩니다.
> 

### 문자열 연결 연산자
<a id="문자열-연결-연산자"></a>

자바에서 `+`는  산술 연산자, 부호 연산자인 동시에 문자열 연결 연산자

```java
System.out.println("Hello" + 123 + 456);  // 출력값: Hello123456
// 문자열 "Hello"와 123이 먼저 연산되어 "Hello123"이 되고,
// 이것을 다시 456과 연산하여 "Hello123456"이 됩니다.

System.out.println(123 + 456 + "Hello");  // 출력값: 579Hello
// 숫자 123과 456이 먼저 연산되어 579가 되고,
// 이것을 문자열 "Hello"와 연산하여 "579Hello"가 됩니다.
```
문자열과 숫자값을 연결한다면 주의할 것

### 비교 연산자
<a id="비교-연산자"></a>

비교 연산자는 피연산자들을 비교하여 boolean 타입인 `true`, `false` 를 산출

크기 비교

| 연산식 | 설명 |
| --- | --- |
| A > B | A가 B보다 큰 지 검사 |
| A >= B | A가 B보다 크거나 같은지 검사 |
| A < B | A가 B보다 작은 지 검사 |
| A <= B | A가 B보다 작거나 같은지 검사 |

동등 비교

| 연산식 | 설명 |
| --- | --- |
| A == B | A와 B가 같은지 검사 |
| A != B | A와 B가 다른지 검사 |


> ✨ 특이사항   
> char 타입은 유니코드값으로 변환   
> float 이랑 double 을 비교하면 double 로 변환
> 

**추가 주의사항 케이스**

```java
String str1 = "Hello";
String str2 = "Hello";
String str3 = new String("Hello");

System.out.println(str1 == str2);  // true
System.out.println(str1 == str3);  // false
```

위 예시처럼 `new`로 생성한 String은 객체로써 새로운 주소값을 가지기 때문에   
false 값을 반환

<img src="img/day21/heap.png" width="600" height="400" alt="">

해결 방법

```java
System.out.println(str1.equals(str3));  // true
```

이런식으로 equals 를 써야함


### 논리 연산자 (&&, ||, &, |, ^, !)
<a id="논리-연산자"></a>

#### AND (&&)
<a id="AND"></a>

두 항의 값이 모두 true면 true를 반환하고 나머지는 false

| x | y | x && y |
| --- | --- | --- |
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

#### OR (||)
<a id="OR"></a>

두 항의 값중 하나라도 true라면 true를 반환.

| x | y | x or(ㅣㅣ) y |
| --- | --- |------------|
| true | true | true       |
| true | false | true       |
| false | true | true       |
| false | false | false      |


#### XOR (배타적 논리합)
<a id="XOR"></a>

두 항이 각각 true와 false를 가지면 true를 반환.   
(이건 언제 쓰는 것일까....)

| 연산식 | 결과 |
| --- | --- |
| true ^ true | false |
| true ^ false | true |
| false ^ false | false |


#### NOT (논리 부정)
<a id="NOT"></a>

피연산자의 값을 반전시킴

| 연산식 | 결과 |
| --- | --- |
| !true | false |
| !false | true |


### 비트 연산자 (&, |, ^, ~, <<, >>, >>>)
<a id="비트-연산자"></a>

#### 비트 논리 연산자
<a id="비트-논리-연산자"></a>

2진수를 이용한 논리 연산자.

| x | y | x & y (논리곱) | x ㅣ y (논리합) | x ^ y (배타적 논리합) |
| --- | --- |-------------|-------------|-----------------|
| 1 | 1 | 1           | 1           | 0               |
| 1 | 0 | 0           | 1           | 1               |
| 0 | 1 | 0           | 1           | 1               |
| 0 | 0 | 0           | 0           | 0               |


#### NOT (논리 부정)
<a id="논리-부정"></a>

0은 1로, 1은 0으로 바꿉니다.

| 연산식 | 결과 |
| --- | --- |
| ~1 | 0 |
| ~0 | 1 |


### 비트 이동 연산자(쉬프트 연산자)
<a id="비트-이동-연산자"></a>

2진수로 표현된 비트를 좌, 우로 이동

| 연산식 | 결과 |
| --- | --- |
| a << b | 정수 a의 각 비트를 b만큼 왼쪽으로 이동 (빈자리는 0으로 채워짐) |
| a >> b | 정수 a의 각 비트를 b만큼 오른쪽으로 이동 (빈자리는 최상위 부호 비트(MSB)와 같은 값으로 채워짐) |
| a >>> b | 정수 a의 각 비트를 b만큼 오른쪽으로 이동시키며, 새로운 비트는 전부 0으로 채워짐 |


> 비트 연산자는 이해를 잘 하고 있습니다.
>


## 💡삼항 연산자
<a id="삼항-연산자"></a>

세 개의 피연산자가 있는 연산자

<img src="img/day21/3way.png" width="600" height="400" alt="">

**예시**

```java
int score = 95;

String grade = (score == 95 && score % 5 == 0) ? "good" : "bad";
System.out.println(grade); // 결과값 good
```

## 💡if 문
<a id="if"></a>

### if 조건문
<a id="if-조건문"></a>

if 조건문: 특정 조건이 참일 때에만 코드 블록을 실행

```java
if (조건1) {
    조건1이 참일 때 실행되는 코드
} else if (조건2) {
    조건1이 거짓이고 조건2가 참일 때 실행되는 코드
} else {
    모든 조건이 거짓일 때 실행되는 코드
}


int number = 10;

if (number > 10) {
    System.out.println("number는 10보다 큽니다.");
} else if (number < 10) {
    System.out.println("number는 10보다 작습니다.");
} else {
    System.out.println("number는 10입니다.");
}
```


### 논리 연산자
<a id="if-논리-연산자"></a>

if문에서 논리연산자를 사용함으로서 조건식을 다양하게 활용할 수 있습니다.

```java
boolean x = true;
boolean y = false;
boolean z = true;

if (x && !y) {System.out.println("조건1 충족");}; //충족

if ((y && z) || !(x || z)) {System.out.println("조건2 충족");}; //충족 X

if (x || y || z) {System.out.println("적어도 하나는 참");}; // 충족

if (!(x || y || z)) {System.out.println("모두 거짓");}; // 충족 X
```


## 💡switch 문
<a id="switch"></a>

다중 분기를 처리하기 위해 switch 문을 사용할 수 있음   
if 와 비슷하지만 if가 더 많이 사용 됨.

```java
switch (변수) {
    case 값1:
        // 변수가 값1과 일치하는 경우 실행할 코드
        break;
    case 값2:
        // 변수가 값2와 일치하는 경우 실행할 코드
        break;
    case 값3:
        // 변수가 값3과 일치하는 경우 실행할 코드
        break;
    default:
        // 변수와 일치하는 어떤 case 문도 없는 경우 실행할 코드
}
```


<details>
<summary> switch 수업중 퀴즈 정답중 내가 맘에 드는 것  </summary>

```java
import static java.lang.System.*;

public class Java_20240603_12_switch_quiz5 {
  public static void main(String[] args) {

    int score = (int) (Math.random() * 101);

    switch (score / 10) {
      case 10:
        out.println("A+ 만점입니다0");
        break;
      case 9:
        out.println("A");
        break;
      case 8:
        out.println("B");
        break;
      case 7:
        out.println("C");
        break;
      case 6:
        out.println("D");
        break;
      default:
        out.println("F");
    }
  }
}
```

</details>

--------------------------------------

<details>
<summary> 회고  </summary>
자바에 점점 익숙해지면서 이것저것 찾아보고 적용을 해 보기 시작.<br>
스터디의 효과가 조금씩 나오고 있어서 뿌듯한 느낌.<br>
하지만 매일 2시쯤 자기 시작하면서 요일개념이 없어졌다.....<br>
롱런하자고 스스로에게 말하며 마음을 잡고있다.<br>
물론 우리 5기 사람들 다 같이 롱런하기를!!
</details>
