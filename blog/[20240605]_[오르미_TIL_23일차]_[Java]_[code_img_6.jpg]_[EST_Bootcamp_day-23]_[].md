# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [사용자의 입력받는 프로그램 작성해보기](#userWrite)
  - [scanner](#scanner)



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


<img src="img/day22/for.png" width="500" height="400" alt="">

<details>
<summary> 회고 </summary>

이번 강의는 실습이 많아서 정리할게 많지는 않았다. <br>
요즘 코테에 좀 집중하고 있어서 정신이 없긴 하지만 <br>
내 실력이 조금씩 발전하고 있다는 것은 많이 느낀다.<br>
아직은 코린이 단계이지만 꾸준하게 롱런한다면 무조건 잘 될 수 있을 것이다.<br>
오르미 5기 부트캠프 모두 화이팅이다.<br>
<br>
좀 피곤하긴 하다...

</details>


