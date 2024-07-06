# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 컬렉션 ](#-컬렉션)
  - [Collection이란??](#Collection이란)
  - [List - ArrayList, LinkedList](#List)
  - [Set - HashSet](#set)
  - [Map - HashMap, Hashtable](#map)


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


HashSet에 String 객체를 추가, 검색, 제거하는 방법

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

### Map - HashMap, Hashtable
<a id="map"></a>

Map

- 키(key)와 값(value)으로 구성된 객체를 저장하는 구조로
- 키와 값은 모두 객체
- 키는 중복될 수 없지만 값은 중복 저장될 수 있다.
- 기존에 저장되었던 키값과 동일한 키값으로 저장하면 기존의 값은 없어지고 새로운 값으로 대치

<img src="img/day32/map.png" width="700" height="400" alt="">




<details>
<summary> 회고 </summary>



</details>
