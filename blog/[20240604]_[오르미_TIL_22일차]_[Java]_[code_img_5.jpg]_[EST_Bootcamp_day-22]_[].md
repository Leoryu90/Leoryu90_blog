# [5기] 백엔드 개발자 부트캠프 오르미

  **목차**
- [while 문](#-while-문)
- [for 문](#-for문)
  - [for 반복문](#for-반복문)
  - [이중 반복문과 break, continue](#break-continue)
  - [향상된 반복문](#향상된-반복문)

## 💡 while 문
<a id="-while-문"></a>

**while 반복문**

조건이 참인 동안 코드 블록을 반복적으로 실행한다

```java
while (조건) {
    // 조건이 참일 때 실행되는 코드
}

int i = 1;

while (i <= 5) {
  System.out.println("현재 i의 값: " + i);
  i++;
}
// 결과값:
// 현재 i의 값: 1
// 현재 i의 값: 2
// 현재 i의 값: 3
// 현재 i의 값: 4
// 현재 i의 값: 5
```

## 💡 for문
<a id="-for문"></a>

### for 반복문
<a id="-for-반복문"></a>

특정 횟수만큼 반복적으로 코드를 실행할 수 있다.

```java
for (초기식; 조건식; 증감식) {
    // 조건식이 참인 동안 실행되는 코드
}

for (int i = 1; i <= 5; i++) {
    System.out.println("현재 i의 값: " + i);
}

// 결과값:
// 현재 i의 값: 1
// 현재 i의 값: 2
// 현재 i의 값: 3
// 현재 i의 값: 4
// 현재 i의 값: 5
```

for 반복문의 실행 순서

<img src="img/day22/for.png" width="500" height="400" alt="">

1. 초기화(Initialization): for 문 시작시 1번 실행 ex) for(int i = 0; ; )
2. 조건 평가(Condition Evaluation): 조건을 평가 조건이 true일 때 루프를 계속 실행 for(; i < 10;)
3. 루프 본문 실행(Loop Body Execution): 조건이 true면 실행되는 코드
4. 업데이트(Update): 본분이 끝나면 초기식 변수를 업데이트 for( ; ; i++)
5. 조건 재평가(Re-evaluation of Condition): 엡데이트 후 3단계로 다시 돌아감

<details>
<summary> 코테에 자주나오는 피보나치!!  </summary>

```java
int[] arr = new int[100];
// 피보나치 수열의 첫 번째와 두 번째 항을 초기화
arr[0] = 1;
arr[1] = 1;

// for문을 사용하여 피보나치 수열을 계산하고 배열에 저장
for (int i = 2; i < arr.length; i++) {
    arr[i] = arr[i - 2] + arr[i - 1];
}

// 출력
System.out.println(Arrays.toString(arr));
```

</details>

### 이중 반복문과 break, continue
<a id="break-continue"></a>

2중 반복문

```java
// 바깥쪽 반복문의 본문
for (초기식1; 조건식1; 증감식1) {
        // 안쪽 반복문의 본문
    for (초기식2; 조건식2; 증감식2) {
    }
}
```

실행순서

1. 바깥쪽 반복문이 1번 실행
2. 안쪽 반복문을 끝까지 반복
3. 바깥쪽 반복문 2증가
4. 다시 안쪽 끝까지
5. 위 과정이 바깥쪽 반복문이 끝날 떄까지

-----------------------------

**break 와 continue**

break: 반복문을 즉시 종료, 반복문의 조건식과 상관없이 반복문을 완전히 빠져나오는 역할

```java
int number = 0;

while (number < 10) {
    System.out.println("현재 숫자 : "+number);
    if (number == 5) {
        System.out.println("숫자 5가 되어 반복문을 종료합니다.");
        break;
    }

    number++;
}
```

continue: 반복문의 현재 반복중에 실행되는 코드를 즉시 종료하고, 다음 반복을 시작

```java
int number = 0;

while (number < 10) {
  number++;
  if (number == 3) {
    continue;
  } else {
    System.out.println("현재 숫자 : " + number);
  }

}
```

> 이중 반복문에서 안쪽 반복문에 break 시 안쪽만 적용!   
> 이중 반복문이나 다중 반복문 내에서 break와 continue를 적절하게 활용하면,   
> 특정 조건에 따라 반복문의 흐름을 제어할 수 있습니다
> 

### 향상된 반복문
<a id="향상된-반복문"></a>

향상된 반복문이란?

- 향상된 반복문은 배열이나 컬렉션의 요소를 순차적으로 처리하는 반복문입니다.
- 기존의 for문에 비해 간결하고 가독성이 좋습니다.
- 인덱스를 사용하지 않고 요소에 직접 접근합니다.

예시코드

```java
// 배열 예시
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}

// 컬렉션 예시
List<String> fruits = Arrays.asList("apple", "banana", "orange");
for (String fruit : fruits) {
    System.out.println(fruit);
}

```


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


