# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 컬렉션 ](#-컬렉션)
  - [Collection이란??](#Collection이란)
  - [List - ArrayList, LinkedList](#List)
  - [Set - HashSet](#set)
  - [Map - HashMap, Hashtable](#map)
  - [LIFO , FIFO 컬렉션](#LIFO-FIFO)


## 💡 컬렉션
<a id="-컬렉션"></a>

### Collection이란?
<a id="Collection이란"></a>

컬렉션(Collection) 이란 사전적 의미로 **요소를 수집해서 저장하는 것**

배열의 단점인 고정된 자원과 비어있는 인덱스를 확인해야 하는 것을 없애줄 수 있다.

<img src="img/day32/collection.png" width="700" height="500" alt="">

- List 인터페이스를 구현한 클래스 : ArrayList, Vector, LinkedList
- Set 인터페이스를 구현한 클래스 : HashSet, TreeSet
- Map 인터페이스를 구현한 클래스 : HashMap, Hashtable, TreeMap, Properties

| 인터페이스 | 구현클래스                                     | 특징                                                                                                |
|---|-------------------------------------------|---------------------------------------------------------------------------------------------------|
|Set| HashSet <br/> TreeSet <br/> LinkedHashSet | 순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않는다.                                                          |
|List| ArrayList <br/> Vector<br/> LinkedList    | 순서가 있는 데이터의 집합으로 데이터의 중복을 허용한다.                                                                   |
|Map| Hashtable <br/> HashMap <br/> TreeMap     | 키(Key), 값(Value)의 쌍으로 이루어진 데이터의 집합으로, <br/> 순서는 유지되지 않으며 키(Key)의 중복을 허용하지 않으나 값(Value)의 중복은 허용한다. |


<img src="img/day32/collection2.png" width="700" height="500" alt="">

### List - ArrayList, LinkedList
<a id="List"></a>

List 컬렉션은 객체를 일렬로 늘어놓은 구조로   
List 컬렉션은 객체 자체를 저장하는게 아니라 다음 그림과 같이 객체의 번지를 참조,   
null도 저장이 가능한데, 이 경우 해당 인덱스는 객체를 참조하지 않습니다.

<img src="img/day32/collection3.png" width="700" height="500" alt="">


사용 예시

```java
List<String> list = ...;
list.add("홍길동");
list.add(1, "삼길동");
String str = list.get(1);
list.remove(0);
list.remove("삼길동");
```

List 컬렉션에서 공통적으로 사용 가능한 List 인터페이스의 메소드

| 기능 | 메소드 | 설명 |
| --- | --- | --- |
| 객체 추가 | boolean add(E e) | 주어진 객체를 맨 끝에 추가 |
|  | void add(int index, E element) | 주어진 인덱스에 객체를 추가 |
|  | set(int index, E element) | 주어진 인덱스에 저장된 객체를 주어진 객체로 바꿈 |
| 객체 검색 | boolean contains(Object o) | 주어진 객체가 저장되어있는지 여부 |
|  | E get(int index) | 주어진 인덱스에 저장된 객체를 리턴 |
|  | isEmpty() | 컬렉션이 비어있는지 여부 |
|  | int size() | 저장되어 있는 전체 객체 수 리턴 |
| 객체 삭제 | void clear() | 저장된 모든 객체를 삭제 |
|  | E remove(int index) | 주어진 인덱스에 저장된 객체를 삭제 |
|  | boolean remove(Object o) | 주어진 객체를 삭제 |



#### ArrayList<>()

인덱스로 접근 가능하지만 중간값 삽입,삭제시 빈번한 인덱스 이동 → 빈번한 객체 삭제와 삽입이 일어나는 곳에서는 ArrayList를 사용하는 것이 바람직하지 않다.

<img src="img/day32/collection4.png" width="700" height="500" alt="">

#### LinkedList<>()

LinkedList는 인접 참조를 링크해서 체인처럼 관리 → LinkedList에서 특정 인덱스의 객체를 제거하면 앞뒤 링크만 변경되고 나머지 링크는 변경되지 않는다.

<img src="img/day32/collection5.png" width="700" height="500" alt="">

선언 예시

```java
List<String> list = new ArrayList<>();

List<String> linkedList = new LinkedList<>();
```

10,000개의 객체를 삽입하는 실행 시간 비교

```java
public class LinkedListExample {

	public static void main(String[] args) {
		List<String> arrayList = new ArrayList<>();
		List<String> linkedList = new LinkedList<>();

		long startTime;
		long endTime;

		startTime = System.nanoTime();
		for (int i = 0; i < 10000; i++) {
			arrayList.add(0, String.valueOf(i));
		}
		endTime = System.nanoTime();
		System.out.println("ArrayList 걸린시간: " + (endTime - startTime) + "ns");

		startTime = System.nanoTime();
		for (int i = 0; i < 10000; i++) {
			linkedList.add(0, String.valueOf(i));
		}
		endTime = System.nanoTime();
		System.out.println("LinkedList 걸린시간: " + (endTime - startTime) + "ns");
	}
}
```

```java
ArrayList 걸린시간: 56252133ns
LinkedList 걸린시간: 3332620ns
```

### Set - HashSet
<a id="set"></a>

- set 컬렉션은 저장 순서가 유지되지 않습니다.
- 객체를 중복해서 저장할 수 없습니다.

Set 인터페이스의 메소드

| 기능 | 메소드 | 설명 |
| --- | --- | --- |
| 객체 추가 | boolean add(E e) | 주어진 객체를 저장, 객체가 성공적으로 저장되면 true를 리턴하고 중복 객체면 false를 리턴 |
| 객체 검색 | boolean contains(Object o) | 주어진 객체가 저장되어 있는지 여부 |
|  | isEmpty() | 컬렉션이 비어 있는지 조사 |
|  | Iterator<E> iterator() | 저장된 객체를 한 번씩 가져오는 반복자 리턴 |
|  | int size() | 저장되어 있는 전체 객체 수 리턴 |
| 객체 삭제 | void clear() | 저장된 모든 객체를 삭제 |
|  | boolean remove(Object o) | 주어진 객체를 삭제 |


사용 예시

```java
Set<String> set = ..;
set.add("카리나");
set.add("윈터");
set.remove("카리나");
```

Set 컬렉션은 저장 순서가 유지되지 않기 때문에 인덱스로 객체를 가져올 수 없습니다.   
그래서 인덱스로 객체를 검색해서 가져오는 메소드가 없죠.   
대신, 전체 객체를 대상으로 한번씩 반복해서 가져오는 반복자(iterator)를 제공합니다.   
반복자는 Iterator 인터페이스를 구현한 객체를 말하는데,   
iterator() 메소드를 호출하면 얻을 수 있습니다.

```java
Set<String> set = ...;
Iterator<String> iterator = set.iterator();
```

Iterator 인터페이스에 선언된 메소드

| 리턴 타입 | 메소드명 | 설명 |
| --- | --- | --- |
| boolean | hasNext() | 가져올 객체가 있으면 true를 리턴하고 없으면 false를 리턴합니다 |
| E | next() | 컬렉션에서 하나의 객체를 가져옵니다 |
| void | remove() | Set 컬렉션에서 객체를 제거합니다 |


```java
Set<String> set = ...;

Iterator<String> iterator = set.iterator();
while (iterator.hasNext()) {		// 저장된 객체 수만큼 루핑
	String str = iterator.next(); // String 객체 하나를 가져옴
}

Set<String> set = ...;
        for (String str : set) {  //저장된 객체 수만큼 루핑

        }
```

#### HashSet

HashSet은 Set 인터페이스의 구현 클래스

```java
Set<E> set = new HashSet<E>();
```

<img src="img/day32/set.png" width="700" height="400" alt="">

<details>
<summary> 예제 HashSet에 String 객체를 추가, 검색, 제거하는 방법 </summary>

```java
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class HashSetExample {
	public static void main(String[] args) {
		Set<String> set = new HashSet<>();
		set.add("Java");
		set.add("Spring");
		set.add("Servlet/JSP");
		set.add("Java");
		set.add("DBMS");

		System.out.println("총 객체수: " + set.size());  // 저장된 객체수 출력

		Iterator<String> iterator = set.iterator();    // 반복자 얻기
		while (iterator.hasNext()) {              // 객체 수 만큼 루핑
			String element = iterator.next();       // 한 개의 객체를 가져온다
			System.out.println("\t" + element);
		}

		set.remove("DBMS");      // 한 개의 객체 삭제
		set.remove("Java");      // 한 개의 객체 삭제
		System.out.println("총 객체수: " + set.size());

		iterator = set.iterator();
		while (iterator.hasNext()) { 
			String element = iterator.next();
			System.out.println("\t" + element);
		}

		set.clear();       // 모든 객체를 제거하고 비움
		if (set.isEmpty()) {
			System.out.println("비어있음");
		}
	}
}
```

실행결과

```java
총 객체수: 4
	Java
	Servlet/JSP
	DBMS
	Spring
총 객체수: 2
	Servlet/JSP
	Spring
비어있음
```

</details>

### Map - HashMap, Hashtable
<a id="map"></a>

Map

- 키(key)와 값(value)으로 구성된 객체를 저장하는 구조로
- 키와 값은 모두 객체
- 키는 중복될 수 없지만 값은 중복 저장될 수 있다.
- 기존에 저장되었던 키값과 동일한 키값으로 저장하면 기존의 값은 없어지고 새로운 값으로 대치

<img src="img/day32/map.png" width="700" height="400" alt="">

Map의 종류

- HashMap
- Hashtable
- LinkedHashMap
- Properties
- TreeMap

메서드

| 기능 | 메소드 | 설명 |
| --- | --- | --- |
| 객체추가 | V put(K key, V value) | 주어진 키와 값을 추가, 저장되면 값을 리턴 |
| 객체검색 | boolean containsKey(Object key) | 주어진 키가 있는지 여부 |
|  | boolean containsValue(Object value) | 주어진 값이 있는지 여부 |
|  | Set(Map.Entry<K,V>> entrySet() | 키와 값의 쌍으로 구성된 모든 Map.Entry 객체를 Set에 담아서 리턴 |
|  | V get(Object key) | 주어진 키가 있는 값을 리턴 |
|  | boolean isEmpty() | 컬렉션이 비어 있는지 여부 |
|  | Set<K> keySet() | 모든 키를 Set 객체에 담아서 리턴 |
|  | int size() | 저장된 키의 총 개수 리턴 |
|  | Collection<V> values() | 저장된 모든 값을 Collection에 담아서 리턴 |
| 객체삭제 | vold clear() | 모든 Map.Entry(키와 값)를 삭제 |
|  | V remove(Object key) | 주어진 키와 일치하는 Map.Entry를 삭제하고 값을 리턴 |


#### HashMap

Map 인터페이스를 구현한 대표적인 Map 컬렉션

사용예시

```java
Map<K, V> map = new HashMap<K, V>(); // K: 키 타입 파라미터, V: 값 타입 파라미터

Map<String, Integer> map = new HashMap<String, Integer>();
```
<details>
<summary> 전체 예제 HashMap </summary>

```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class HashMapExample {
	public static void main(String[] args) {
		// 1. Map 컬렉션 생성
		Map<String, Integer> map = new HashMap<>();

		map.put("홍길동", 80);
		map.put("카리나", 85);
		map.put("제시카", 95);
		map.put("홍길동", 80);        // "홍길동" 키가 같기 때문에 가장 마지막에 저장한 값으로 엎어씀
		System.out.println("총 Entry 수: " + map.size());    // 저장된 총 Entry 수 얻기

		// 2. 객체 찾기
		System.out.println("\t홍길동: " + map.get("홍길동"));
		System.out.println();

		// 3. 객체를 하나씩 처리
		Set<String> keySet = map.keySet();
		Iterator<String> iterator = keySet.iterator();
		while (iterator.hasNext()) {
			String key = iterator.next();
			Integer value = map.get(key);
			System.out.println("\t" + key + ": " + value);
		}
		System.out.println();

		// 4. 객체 삭제
		map.remove("홍길동");
		System.out.println("총 Entry 수: " + map.size());

		// 5. 객체를 하나씩 처리
		Set<Map.Entry<String, Integer>> entrySet = map.entrySet(); // Map.EntrySet 얻기
		for (Map.Entry<String, Integer> entry : entrySet) {
			String key = entry.getKey();
			Integer value = entry.getValue();
			System.out.println("\t" + key + ": " + value);
		}
		System.out.println();

    // 6. 모든 Map.Entry 삭제
		map.clear();
		System.out.println("총 Entry 수: " + map.size());
	}
}
```

```java
총 Entry 수: 3
	홍길동: 80

	제시카: 95
	홍길동: 80
	카리나: 85

총 Entry 수: 2
	제시카: 95
	카리나: 85

총 Entry 수: 0
```

</details>


#### Hashtable

Hashtable은 동기화된(synchronized) 메소드로 구성되어 있기 때문에   
멀티 스레드가 동시에 이 메소드를 실행할 수 없다.

<img src="img/day32/map2.png" width="700" height="400" alt="">

<details>
<summary> 예제 </summary>

```java
import java.util.Hashtable;
import java.util.Map;
import java.util.Scanner;

public class HashtableExample {
	public static void main(String[] args) {
		Map<String, String> map = new Hashtable<>();
		map.put("spring", "qwer");
		map.put("summer", "qwer1234");
		map.put("fall", "qwer123");
		map.put("winter", "qwe123");

		Scanner scanner = new Scanner(System.in);    // 키보드로 부터 입력된 내용을 받기 위해 생성

		while (true) {
			System.out.println("아이디와 비밀번호를 입력해주세요");
			System.out.println("아이디: ");
			String id = scanner.nextLine();        // 키보드로 입력한 아이디를 읽는다

			System.out.println("비밀번호: ");
			String password = scanner.nextLine();
			System.out.println();

			if (map.containsKey(id)) {
				if (map.get(id).equals(password)) {
					System.out.println("로그인이 되었습니다");
					break;
				} else {
					System.out.println("비밀번호가 일치하지 않습니다!");
				}
			} else {
				System.out.println("입력하신 아이디가 존재하지 않습니다!\n");
			}
		}
	}
}
```

결과값

```java
아이디와 비밀번호를 입력해주세요
아이디: 
fall
비밀번호: 
qwer123

로그인이 되었습니다
```

</details>

### LIFO , FIFO 컬렉션
<a id="LIFO-FIFO"></a>

스택과 큐!

#### Stack (후입선출, LIFO)

후입선출 (LIFO: Last In First Out): 나중에 넣은 객체가 먼저 빠져나가는 자료구조

기본구조

```java
Stack<E> stack = new Stack<E>();
```

<img src="img/day32/stack.png" width="700" height="500" alt="">

stack의 메소드

| 리턴 타입 | 메소드 | 설명 |
| --- | --- | --- |
| E | push(E item) | 주어진 객체를 스택에 넣는다 |
| E | peek() | 스택의 맨 위 객체를 가져온다. 객체를 스택에서 제거하지 않는다. |
| E | pop() | 스택의 맨 위 객체를 가져오고, 객체를 스택에서 제거한다. |

스택을 이용한 백준 코딩테스트 풀이!
https://www.acmicpc.net/problem/1874

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.Stack;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        Stack<Integer> stack = new Stack<>();
        List<String> list = new ArrayList<>();

        int n = Integer.parseInt(br.readLine());
        int count = 1;

        for (int i = 0; i < n; i++) {
            int num = Integer.parseInt(br.readLine());

            for (;count <= num;count++) {
                stack.push(count);
                list.add("+");
            }

            if (num == stack.peek()) {
                stack.pop();
                list.add("-");
            }else {
                System.out.println("NO");
                return;
            }
        }

        for (String s : list) {
            System.out.println(s);
        }
    }
}
```


#### Queue (선입선출, FIFO)

선입선출(First In First Out)은 먼저 넣은 객체가 먼저 빠져나가는 구조

<img src="img/day32/queue.png" width="700" height="400" alt="">

큐의 기본 구조

```java
Queue<E> queue = new LinkedList<E>();
```

queue 의 메소드

| 리턴 타입 | 메소드 | 설명 |
| --- | --- | --- |
| boolean | offer(E e) | 주어진 객체를 넣는다. |
| E | peek() | 객체 하나를 가져온다. 객체를 큐에서 제거하지 않는다. |
| E | poll() | 객체 하나를 가져온다. 객체를 큐에서 제거한다. |





<details>
<summary> 큐 예시 </summary>

```java
public class Message {
	private String command;
	private String to;

	public String getCommand() {
		return command;
	}

	public String getTo() {
		return to;
	}

	public Message(String command, String to) {
		this.command = command;
		this.to = to;
	}
}
```

```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
	public static void main(String[] args) {
		Queue<Message> messageQueue = new LinkedList<>();

		messageQueue.offer(new Message("sendMail", "홍길동"));
		messageQueue.offer(new Message("sendSms", "제니"));
		messageQueue.offer(new Message("sendKakaoTalk", "리사"));

		while (!messageQueue.isEmpty()) {        // 메시지 큐가 비었는지 확인 
			Message message = messageQueue.poll(); // 메시지 큐에서 하나의 메시지 꺼냄
			switch (message.getCommand()) {
				case "sendMail":
					System.out.println(message.getTo() + "에게 메일을 보냅니다.");
					break;
				case "sendSms":
					System.out.println(message.getTo() + "에게 SMS를 보냅니다.");
					break;
				case "sendKakaoTalk":
					System.out.println(message.getTo() + "에게 카톡을 보냅니다.");
					break;
			}
		}
	}
}
```

실행결과

```java
홍길동에게 메일을 보냅니다.
제니에게 SMS를 보냅니다.
리사에게 카톡을 보냅니다.
```

</details>


<details>
<summary> 회고 </summary>

개인적으로 제네릭 이해가 가장 오래 걸렸고.<br>
그 이해를 못하다보니 컬렉션에서 한참 헤맸던 것 같습니다...<br>
<br>
개인적인 공부를 하다보니 TIL이 너무 밀렸지만 우선 스프링 나가는거부터 쭉 정리하면서 <br>
DBMS 정리를 차근차근 하겠습니다.<br>
<br>
조금 힘든 시기가 좀 있었던 거 같지만 나름 쉼을 가졌으니 그것을 발판삼아<br>
다시 불태워보겠습니다!

</details>