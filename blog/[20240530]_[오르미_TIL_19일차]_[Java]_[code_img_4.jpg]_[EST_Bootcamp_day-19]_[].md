# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [변수](#variable)
  1. [변수 란?](#whatIsVariable)
  2. [변수의 네이밍 규칙](#nameOfVariable)
- [변수의 타입](#typeOfVariable)
  1. [원시 타입 (Primitive type)](#primitiveType)
     1. [정수타입](#typeOfVariable)
        - [byte 타입](#byteType)
        - [char 타입](#charType)
        - [short 타입](#shortType)
        - [int 타입](#intType)
        - [long 타입](#longType)
     2. [실수 타입 (float, double)](#fAndD)
        - [float](#float)
        - [double](#double)
     3. [논리 타입 (boolean)](#boolean)
  2. [참조타입 (Reference type)](#ReferenceType)
  3. [원시 타입, 참조 타입 비교](#VS)


## 💡 변수
<a id="variable"></a>

### 변수란?
<a id="whatIsVariable"></a>

값을 저장하는 공간.   
Java에서는 변수 선언시 타입을 지정해야한다.

```java
변수타입 변수명 = 값;
  int   number = 10;
```
> 하나의 변수에 **하나의 값**만 저장 가능.(배열 제외)

### 변수의 네이밍 규칙
<a id="nameOfVariable"></a>

1. 숫자로 시작해서는 안됩니다.
2. 예약어를 사용해서는 안됩니다. (String, int 이런것)
3. 대소문자가 구분되며 길이에는 제한이 없습니다. 단, 길이가 너무 길어진다면 가독성 문제가 있습니다.
4. 특수문자는 언더바(_)와 달러($)만 가능합니다.

```java
// 잘못된 방법 예시
int 13a = 2
int int = 2
int whatIsYourNameSirIWantKnowItIsItOkay = 2 //가능하지만 가독성...
int name@# = 2
```

## 변수의 타입
<a id="typeOfVariable"></a>

### 원시 타입 (Primitive type)
<a id="primitiveType"></a>

가장 기본적인 타입으로 직접적으로 데이터를 저장하고 처리한다.

- **스택 메모리**: 원시 타입의 데이터는 스택 메모리에 저장되어 실행 속도가 빠릅니다.
- **값에 의한 전달**: 원시 타입의 변수를 다른 변수에 할당하면, 실제 값이 복사되어 전달됩니다.

#### 정수타입 (byte, char, short, int, long)
<a id="typeOfVariable"></a>

1. byte 타입
<a id="byteType"></a>

8비트의 값을 가짐.   
가장 작은 크기의 단위로 -128 ~ 127 사이의 값을 사용할 수 있다.

2. char 타입
<a id="charType"></a>

16비트 유니코드 문자를 저장하는 데 사용되는 데이터 타입으로   
작은따옴표를 사용한다('1글자')

<details>
<summary> 예시 </summary>

```java
public class CharVariableExample {
	public static void main(String[] args) {
		char c1 = 'A';            // 문자를 직접 저장
		char c2 = 65;            // 10진수로 저장
		char c3 = '\u0041';        // 16진수로 저장

		char c4 = '가';            // 문자를 직접 저장
		char c5 = 44032;        // 10진수로 저장
		char c6 = '\uac00';        // 16진수로 저장

		int unicode = c1;        // 유니코드 얻기

		System.out.println(c1);
		System.out.println(c2);
		System.out.println(c3);
		System.out.println(c4);
		System.out.println(c5);
		System.out.println(c6);
		System.out.println(unicode);
	}
}
```

결과값

<img src="img/day19/char.png" width="300" height="200" alt="">


</details>

3. short 타입
<a id="shortType"></a>

16비트 정수형 데이터 타입 (잘 사용하지 않음.)

4. int 타입
<a id="intType"></a>

자바에서 가장 많이 사용   
-2,147,483,648에서 2,147,483,647까지의 정수 값을 저장

```java
public class IntVariableExample {
	public static void main(String[] args) {
		int result = 10 + 20;
		System.out.println(result);   // 연산 결과 30 출력 
	}
}
```

5. long 타입
<a id="longType"></a>

int를 주로 쓰고 20억이 좀 넘는다면 long을 쓰게 된다고 하셨음.   

```java
long lVal = 12345678900L;
// 값 뒤에 L,l 둘다 사용할 수 있지만 가독성을 위해 대문자를 추천
```

#### 실수 타입 (float, double)
<a id="fAndD"></a>

소수점 숫자를 저장하기 위한 기본 데이터 타입

1. float
<a id="float"></a>

4바이트 표현이 가능, 소수점 표준을 사용하여 숫자를 표현   
7자리 숫자까지는 비교적 정확하게 표현

```java
// 숫자 뒤에 'f'를 붙임
float a = 9.75f;
```

> 값으로 오는 숫자뒤에 f,F 를 붙여야하고 보통 double을 많이 씀.
>

2. double
<a id="double"></a>

8바이트로 소수점 자리 표시.

```java
// 숫자 뒤에 접미사 없음
double myDouble = 19.99;
```

#### 논리 타입 (boolean)
<a id="boolean"></a>

논리값(true/false)을 저장할 수 있는 데이터 타입

```java
public static void main(String[] args) {
    boolean stop = true;
    if (stop) {
        System.out.println("중지합니다!");
    } else {
        System.out.println("시작합니다!");
    }
}
// 결과값: 중지합니다.
```

### 참조타입 (Reference type)
<a id="ReferenceType"></a>

실제 값을 저장하지 않고, 데이터가 저장된 메모리 주소를 참조

1. 클래스 (Classes)
2. 인터페이스 (Interfaces)
3. 배열 (Arrays)

각 설명은 추후 자세히 배운다고 하셨습니다.

### 원시 타입, 참조 타입 비교
<a id="VS"></a>

**저장형태**

<img src="img/day19/save.png" width="300" height="200" alt="">

위의 사진처럼 기본형식은 바로 값을 저장하여 호출하면 빠르게 값을 줌   
참조타입은 주소값을 통하여 객체를 참조!

**초기화**

의문점

```java
String name = "sung yeon";
```

```java
String name = new String("sung yeon");
```
두개가 같다면 어떤 형식으로 많이 쓰는지?


<details>
<summary> 마무리하며 </summary>
자바를 처음 접하고 입문하는 이 시점...
실제로 두통이 생길정도로 이해하는 개념이 조금 힘들었다.
이해는 다 했지만 확실히 새로운 학문을 접한 기분.

지금 코딩테스트 스터디도 들어갔고 CS스터디도 하고 있는데
Java 온라인 수업까지 해볼 수 있으면 해봐야겠다.....

아직 좀 부족함을 많이 느낀다.
</details>
