# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [사용자의 입력받는 프로그램 작성해보기](#userWrite)
  - [scanner](#scanner)
- [자바 라이브러리](#Library)
  - [Random 라이브러리](#randomLibrary)



## 💡 사용자의 입력받는 프로그램 작성해보기
<a id="userWrite"></a>


### scanner
<a id="scanner"></a>

자바에서 사용자에게 입력을 받기 위해서는 `Scanner` 클래스를 사용해야한다.   
`Scanner` 클래스는 `java.util` 패키지에 포함되어 있다.

예시

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
      Scanner sc = new Scanner(System.in);

      System.out.println("정수를 입력하세요.");
      int a = sc.nextInt();
      sc.nextLine();

      System.out.println("문자열을 입력하세요");
      String b = sc.nextLine();


      sc.close();
    }
}
```

> 스트림(stream) 이란?   
> 사용자의 입력을 받거나, 무언가를 출력하는 과정을 하나의 흐름을   
> 영어로 스트림이라 표현한다.   
> `System.out` 을 표준 출력(output)   
> `System.in` 을 표준 입력(input)   
> 이라고 말한다.
> 

**특징 및 유의사항**

1. `nextLine()` 메서드는 Enter 키를 누르기 전까지의 문자열을 읽어들입니다.   
  다른 메서드(예: `nextInt()`)와 함께 사용할 때는 주의가 필요합니다.   
  `nextInt()` 이후에 `nextLine()`을 사용하면,   
  개행 문자(\n)가 남아있어 의도치 않은 동작이 발생할 수 있습니다.   
  이를 방지하기 위해 `nextInt()` 후에 `nextLine()`을 한 번 호출하여   
  개행 문자를 제거해야 합니다.
2. Scanner를 사용한 후에는 `close()` 메서드를 호출하여 자원을 해제하는 것이 좋습니다.   
   이는 메모리 누수를 방지하고 프로그램의 성능을 향상시킵니다.
3. Scanner는 입력 값의 유효성을 검사하지 않으므로,   
   잘못된 타입의 데이터가 입력되면 예외(InputMismatchException)가 발생할 수 있습니다.   
   따라서 적절한 예외 처리가 필요합니다.

## 자바 라이브러리
<a id="Library"></a>

- 자바 라이브러리는 미리 작성된 코드의 모음
- 라이브러리는 클래스, 인터페이스, 메서드 등으로 구성되어 있습니다.
- 자바는 다양한 내장 라이브러리를 제공하며, 개발자는 필요에 따라 외부 라이브러리를 추가로 사용할 수 있습니다.
- 라이브러리를 사용하려면 해당 라이브러리를 import 문을 통해 불러와야 합니다.

### Random 라이브러리
<a id="randomLibrary"></a>

- Random 클래스는 java.util 패키지에 포함되어 있습니다.
- Random 클래스를 사용하려면 `import java.util.Random;`을 코드 상단에 추가해야 합니다.
- Random 클래스의 인스턴스를 생성하여 사용할 수 있습니다. 예: `Random random = new Random();`
- Random 클래스는 다양한 메서드를 제공하여 난수를 생성할 수 있습니다.
  - `nextInt()`: int 타입의 난수를 생성합니다.
  - `nextInt(int bound)`: 0부터 bound 미만의 int 타입 난수를 생성합니다.
  - `nextLong()`: long 타입의 난수를 생성합니다.
  - `nextFloat()`: float 타입의 난수를 생성합니다.
  - `nextDouble()`: double 타입의 난수를 생성합니다.
  - `nextBoolean()`: boolean 타입의 난수를 생성합니다.

랜덤을 이용한 로또 추첨
```java
Random random = new Random();
ArrayList<Integer> list = new ArrayList<Integer>();

while (list.size() != 6) {
    int number = random.nextInt(45) + 1;
    if (!list.contains(number)) {
        list.add(number);
      }
    }

    Collections.sort(list);

    for(int data:list){
      System.out.print(data + " ");
    }
```

## .class, JVM, GC
<a id="Library"></a>

### 자바의 실행과정

우리가 코드를 작성하면 먼저

1. javac(자바 컴파일러) 라는 프로그램을 이용하여
   programName.java → programName.class
   .java프로그램에서 .class 프로그램으로 컴파일 한다.

   이 과정에서 자바 코드는 **자바 바이트코드**로 컴파일 된다.


- 주의할 점은 그냥 바이트코드가 아닌 **자바 바이트코드** 라는 것.

2. 이 자바 바이트 코드를 JVM의 클래스 로더에게 전달하고,

3. 클래스 로더는 동적 로딩을 통하여 런타임 데이터 영역(Runtime Data area)에 올린다. (JVM 메모리에 올린다)

4. 실행엔진은 JVM 메모리로 전달된 바이트코드를 명령어 단위로 하나씩 실행한다.

> **런타임 데이터 영역**: JVM은 프로그램 실행에 필요한 메모리를 할당받습니다.
> - 메서드 영역: 클래스 정보, 상수, static 변수 등이 저장됩니다.
> - 힙: 객체와 배열이 생성되는 공간입니다.
> - 스택: 메서드 호출 시 지역 변수, 매개변수, 리턴 값 등이 저장됩니다.
> - PC 레지스터: 현재 실행 중인 명령의 주소를 저장합니다.
> - 네이티브 메서드 스택: 자바 외의 언어(보통 C/C++)로 작성된 네이티브 코드를 위한 공간입니다.
>

<img src="img/day23/java_code.PNG" width="500" height="400" alt="">

위사진은 제일 이해하기 쉬웠던 이미지를 가지고 왔습니다.


## 가비지 컬렉터

우리가 객체를 생성하면 힙(heap) 메모리에 데이터가 올라가고 그 주소값을 참조하게 되는데   
그 객체를 null 을 할당하는 것처럼 더이상 그 메모리를 참조하지 않는 객체를 찾아 제거하여   
메모리를 확보한다.



<details>
<summary> 회고 </summary>

어제에 이어서 오늘도 실습 위주라 많지 않은 분량이었습니다. <br>
오늘은 코테 스터디 모임하고 저녁먹고 CS 스터디 모임하니 시간이....<br>
열심히 롱런을 위하여 이것저것 배우면서 진행!! <br>
<br>
계속 배우면서 느끼는 점은<br>
배운 지식도 금방 까먹으니 열심히 코드를 쳐보고<br>
익숙해지는게 제일 중요한 것 같다고 느낌니다.<br>
손으로 한번이라도 쳐보거나 말로 누구에게 설명하는 것은<br>
기억에 오래 남는 것 같습니다.<br>
<br>
더욱 열심히 하지만 건강 지키면서 잘 코딩해보겠습니다!

</details>


