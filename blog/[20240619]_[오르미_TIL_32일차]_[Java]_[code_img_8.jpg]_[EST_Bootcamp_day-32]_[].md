# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 컬렉션 ](#-컬렉션)
  - [Collection이란??](#Collection이란)
  - [List - ArrayList, LinkedList](#List)
    - [ArrayList](#arraylist)


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

| 인터페이스 | 구현클래스 | 특징 |
| --- | --- | --- |
| Set | HashSet
TreeSet | 순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않는다. |
| List | LinkedList
Vector
ArrayList | 순서가 있는 데이터의 집합으로 데이터의 중복을 허용한다. |
| Map | Hashtable
HashMap
TreeMap | 키(Key), 값(Value)의 쌍으로 이루어진 데이터의 집합으로,
순서는 유지되지 않으며 키(Key)의 중복을 허용하지 않으나 값(Value)의 중복은 허용한다. |


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


#### ArrayList, LinkedList
<a id="arrayList"></a>

ArrayList<>()

인덱스로 접근 가능하지만 중간값 삽입,삭제시 빈번한 인덱스 이동 → 빈번한 객체 삭제와 삽입이 일어나는 곳에서는 ArrayList를 사용하는 것이 바람직하지 않다.

<img src="img/day32/collection4.png" width="700" height="500" alt="">

LinkedList<>()

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



<details>
<summary> 회고 </summary>



</details>