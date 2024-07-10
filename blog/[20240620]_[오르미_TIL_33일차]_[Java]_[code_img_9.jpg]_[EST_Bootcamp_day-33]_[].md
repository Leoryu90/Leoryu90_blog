# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 스레드 , 람다 , 스트림](#-스레드--람다--스트림)
  - [스레드](#스레드)
    - [자바에서의 스레드 생성](#자바에서의-스레드-생성)
    - [스레드 생명 주기](#스레드-생명-주기)

## 💡 스레드 , 람다 , 스트림
<a id="-스레드--람다--스트림"></a>

#### 스레드 프로세스 프로그램

스레드 (Thread): 프로세스가 할당받은 자원을 이용하는 실행 흐름의 단위

프로세스 (Process): 운영체제로부터 자원을 할당받은 작업의 단위   

프로그램 (Program): 컴퓨터에서 실행할 수 있는 파일

> 프로그램을 실행하여 돌아가고 있는 상태,   
> 즉 컴퓨터가 무언가를 하고 있는 상태를 프로세스   
> 프로세스 안에서 진행되는 작업들을 스레드라고 한다.
>

### 스레드
<a id="스레드"></a>

<img src="img/day33/thread.png" width="700" height="400" alt="">

만약 크롬을 실행시켰다면 그것이 프로세스가 생성되고 그 안에서 여러 동작을 수행할 수 있다.   
이처럼 프로세스 안에서 수행되는 작업을 스레드라고 하고 스레드가 여러 개 있다면 다중 스레드라고 한다.

#### 프로세스 내부 구조

Code 영역

- 프로그래머가 작성한 `소스코드`가 저장되어 있습니다. 더 자세히 설명하자면 소스코드가 컴퓨터가 이해할 수 있는 기계어 형태로 저장되어 있습니다.

Data 영역

- 코드가 실행되면서 사용하는 `전역 변수나 static 변수`들이 저장되어 있습니다.

Stack 영역

- `함수`가 호출되면 Stack 영역에 할당되며 함수가 **종료되면 소멸**합니다. 함수에서 사용하는 지역 변수도 함께 저장됩니다. 만약 프로세스에 할당된 메모리보다 Stack 영역을 많이 사용하면 stack overflow 에러가 발생합니다.

Heap 영역

- `생성자, 인스턴스`와 같은 동적으로 할당되는 데이터들을 저장합니다.

#### 스레드 내부 구조

<img src="img/day33/thread2.png" width="600" height="450" alt="">

위의 예시처럼 프로세스 메모리의 4가지 영역(Code, Data, Heap, Stack) 중   
스레드는 **Stack 영역만 별도**로 사용하고    
Code, Data, Heap은 다른 스레드들과 공유합니다


### 자바에서의 스레드 생성
<a id="스레드"></a>

자바에서 스레드를 생성하는 두 가지 방법은 `Thread` 클래스를 상속받거나 `Runnable` 인터페이스를 구현하는 것

#### Thread 클래스 상속

실행 순서 보장하지 않음. 랜덤으로 실행됨

```java
public class MyThread extends Thread{
    private String name;

    public MyThread(String name){
        this.name = name;
    }

    @Override
    public void run() {
        System.out.println(this.name);
        super.run();
    }
}
```

```java
public class Main0620 {
   
    public static void main(String[] args){
        MyThread myThread = new MyThread("스레드");
        MyThread myThread1 = new MyThread("스레드1");
        MyThread myThread2 = new MyThread("스레드2");
        MyThread myThread3 = new MyThread("스레드3");

        myThread.start();
        myThread1.start();
        myThread2.start();
        myThread3.start();   
    }
}
// 실행결과는 1,2,3,4 가 순서에 상관없이 프린팅 됨
```


#### Runnable 인터페이스 구현

다른 클래스를 상속받은 경우에도 Runnable을 구현하여 스레드를 생성할 수 있음

````java
public class MyRunnable implements Runnable{
    private int number;

    public MyRunnable(int number){
        this.number = number;
    }

    @Override
    public void run() {
        System.out.println(this.number);
    }
}
````

```java
public class Main0620 {
    public static void main(String[] args){
        Thread thread1 = new Thread(new MyRunnable(1));
        Thread thread2 = new Thread(new MyRunnable(2));
        Thread thread3 = new Thread(new MyRunnable(3));
        Thread thread4 = new Thread(new MyRunnable(4));

        thread1.start();
        thread2.start();
        thread3.start();
        thread4.start();
    }
}
```

### 스레드 생명 주기
<a id="스레드-생명-주기"></a>

<img src="img/day33/thread3.png" width="700" height="300" alt="">


1. **Runnable (준비상태)**
  - 스레드가 실행되기 위한 준비 상태입니다.
  - CPU를 점유하고 있지 않으며, 실행을 위해 대기하고 있는 상태입니다.
  - `start()` 메소드를 호출하면 해당 스레드가 Runnable 상태로 진입합니다. (Ready 상태라고도 합니다.)
2. **Running (실행상태)**
  - CPU를 점유하여 실행 중인 상태입니다.
  - `run()` 메서드는 JVM에서만 호출 가능하며, 우선 순위가 높은 스레드가 결정되면 자동으로 호출됩니다.
3. **Dead (종료상태)**
  - 실행 중인 스레드가 모두 실행을 마친 후의 완료 상태입니다.
  - 종료된 스레드는 "Done" 상태로도 불립니다.
4. **Blocked (지연 상태)**
  - CPU 점유권을 상실한 상태로, 특정 메서드 실행을 통해 Runnable 상태로 전환됩니다.
  - `wait()` 메소드로 Blocked 상태가 된 스레드는 `notify()` 메소드 호출 시 Runnable 상태로 전환됩니다.
  - `sleep(시간)` 메소드로 Blocked 상태가 된 스레드는 지정된 시간이 지나면 Runnable 상태로 전환됩니다.




<details>
<summary> 회고 </summary>



</details>
