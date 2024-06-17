# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [에러, 예외처리](#에러-예외처리)
- [💡 Java에서의 예외 처리 방법](#java에서의-예외-처리-방법)
  - [부모 생성자 호출](#부모-생성자-호출)
  - [메소드 오버로딩과 오버라이딩](#메소드-오버로딩과-오버라이딩)
  - [추상클래스](#추상클래스)



## 에러, 예외처리
<a id="에러-예외처리"></a>

### 에러란?

에러(Error)란 프로그램 실행 중에 발생하는 심각한 문제로,   
프로그램의 비정상적인 종료를 야기합니다.

### 예외란?

예외(Exception)란 프로그램 실행 중에 발생하는 비정상적인 상황으로,   
프로그래머가 적절히 처리할 수 있습니다.

<img src="img/day29/error.png" width="500" height="350" alt="">

- 체크드예외는 컴파일 시점에서 예외처리를 강제하는것
(이라고 설명했는데 조금 애매하게 이해가 되는 것 같아서 찾아보니 보통 우리가 코딩을 하면
빨간 밑줄이 쳐지고 실행조차 못하게 되는 현상이 종종 있는데 그걸 처리하는게 체크드 예외였다.)


- 언체크드예외는 실행하는건 상관없고 실행 후 발생되는 예외처리 시점.
(대표적으로 NullPointerException, ArithmeticException 등이 있다.)


## 💡 Java에서의 예외 처리 방법
<a id="java에서의-예외-처리-방법"></a>

1. try-catch문으로 예외를 처리한다
2. throws 키워드로 예외를 호출한 쪽으로 전파한다   
   (라고 써있지만  throws는 예시가 있어야 잘 이해가 된다.)

```java
public static void main(String[] args) {
    try {
		divide(10, 0);
	} catch (ArithmeticException e) {
		System.out.println("0으로 나눌 수 없습니다.");
	}
	        
	public static int divide(int a, int b) throws ArithmeticException {
		return a / b;
	}
}
```

**finally 블록**

finally 블록은 예외 발생 여부와 관계없이 항상 실행

```java
try {
int i = scanner.nextInt();
int result = i / 0;
System.out.println(result);

} catch (NullPointerException e) {
    System.out.println("0으로 나눌 수 없습니다.");
    
} finally {
    System.out.println("스캐너를 종료");
    scanner.close();
}
```

보통 자원을 해제할 때 사용한다.

<details>
<summary> 자바 예외처리 방법 -심화 예시 </summary>

```java
public class BankAccount {
    private int balance;

    public void withdraw(int amount) throws InsufficientBalanceException {
        if (balance < amount) {
            throw new InsufficientBalanceException("잔액이 부족합니다.");
        }
        balance -= amount;
    }
}

public class InsufficientBalanceException extends Exception {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}

public class BankApplication {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        try {
            account.withdraw(10000); // InsufficientBalanceException 발생
        } catch (InsufficientBalanceException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

</details>

> throws를 붙이는 이유   
> 메소드에서 발생할 수 있는 체크드 예외(checked exception)를 호출자에게 알리기 위함
> 


<details>
<summary> 회고 </summary>

인터페이스는 조금 나가긴 했는데 다음에 완전 나가면 한번에 정리하려고 합니다.<br>
<br>
개인적으로 예외처리에서 궁금한건<br>
예외처리는 에러상황에서 종료가 되는 대신 어떤 작업을 하고 해당 작업만 마무리하나요?<br>
아님 프로그램 종료까지 되는건가요?<br>
<br>
의문을 가지게 된 이유는 반복문중에서 예외처리를 했을때 오류를 표시하고<br>
다시 반복분으로 돌아가는 기능은 없나? 하는 의문이었습니다.

</details>