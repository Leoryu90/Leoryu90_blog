# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 제네릭](#-제네릭)
  - [제네릭이란?](#제네릭이란)
  - [제네릭타입을 사용하는 방법과 이유](#제네릭타입을-사용하는-방법과-이유)
  - [제네릭 메소드](#제네릭-메소드)
  - [제한된 타입 파라미터](#제한된-타입-파라미터)
  - [와일드카드 타입](#와일드카드-타입)
  - [제네릭 타입의 상속과 구현](#제네릭-타입의-상속과-구현)


## 💡 제네릭
<a id="-제네릭"></a>

### 제네릭이란?
<a id="제네릭이란"></a>

데이터의 타입(data type)을 일반화(generalize) 한다는 것

**장점**

- 컴파일시 미리 타입이 정해지기 때문에,   
  타입 검사나 변환 같은 번거로운 작업을 생략할 수 있습니다.
- 클래스나 메소드 내부에서 사용하는 타입 안정성을 높일 수 있습니다.

#### 제네릭을 사용하는 이유

잘못된 타입이 사용될 수 있는 문제를 **컴파일 과정에서 제거**할 수 있게 되었습니다.

사용예시
```java
List<Youtube> youtubeList = new ArrayList<Youtube>();

youtubeList.add(new Youtube());   
youtubeList.add(new DisneyPlus());   // 컴파일 에러 발생. Youtube 외에 다른 타입 저장불가
```

그럼 타입을 지정했을 때 좋은점은 뭘까?   
예시로 들면 ArrayList객체를 제네릭 없이 쓰면 타입이 Object라서   
값을 받을 때마다 타입을 변환해야한다.

제네릭 지정 전
```java
List list = new ArrayList();
list.add("Hello");
String str = (String) list.get(0); //타입변환
```
제네릭 지정후
```java
List<String> list = new ArrayList<String>(); //제네릭
list.add("Hello");
String str = list.get(0);
```

### 제네릭타입을 사용하는 방법과 이유
<a id="제네릭타입을-사용하는-방법과-이유"></a>

제네릭 타입은 타입을 파라미터로 가지는 클래스와 인터페이스를 말한다.

사용예시
```java
public class Box<T> {  // String
  private T t;

  public T get() {
    return t;
  }

  public void set(T t) {
    this.t = t;
  }
}
```

```java
public class GenericExample {
    public static void main(String[] args) {
        Box<String> box = new Box<>();
        box.set("hello");

        String str = box.get();
        System.out.println(str);

        Box<Integer> box2 = new Box<>();
        box2.set(9);

        int value = box2.get();
        System.out.println(value);
    }
}
```

위의 예시처럼 1개의 Box 클래스로 여러 타입의 객체를 만들 수 있다.

제네릭은 아래 표의 타입들이 많이 쓰인다.

| 타입    | 설명      |
|-------|---------|
| `<T>` | Type    |
| `<E>` | Element |
| `<K>` | Key     |
| `<V>` | Value   |
| `<N>` | Number  |

반드시 한 글자일 필요는 없고 설명과 반드시 일치해야 할 필요도 없다.  
예로들어 <Ele>라고 해도 전혀 무방하다.   
다만 **대중적**으로 통하는 통상적인 선언이 가장 편하기 때문에   
위와같은 **암묵적인 규칙**이 있을 뿐이다.

### 제네릭 메소드
<a id="제네릭-메소드"></a>

말 그대로 제네릭을 사용한 메서드로   
매개 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드

```java
public <타입파라미터, ..> 리턴타입 메소드명(매개변수, ...) {
}
public <T> Box<T> boxing(T t) {
}
```

예제

```java
public class Util {
	public static <T> Box<T> boxing(T t) {
		Box<T> box = new Box<T>();
		box.set(t);
		return box;
	}
}
```

```java
public class GenericMethodExample {
    public static void main(String[] args) {
        Box<Integer> box1 = Util.boxing(100);
        int intValue = box1.get();

        Box<String> box2 = Util.boxing("홍길동");
        String strValue = box2.get();
    }
}
```

메소드 호출 시 제네릭을 이용하여 유연한 타입생성이 가능하다

### 제한된 타입 파라미터
<a id="제한된-타입-파라미터"></a>

제한된 파라미터는 어떠한 클래스나 인터페이스를 만들때   
그게 숫자 연산이라면 받는 타입을 숫자로 제한할 수 있게 하는 방법이다.

```java
public <T extends 상위타입> 리턴타입 메소드(매개변수, ...) {
}

public <T extends Number> int compare(T t1, T t2) {
  double v1 = t1.doubleValue();
  double v2 = t2.doubleValue();
  return Double.compare(v1, v2)
}
```

위의 예시처럼 Number로 상위타입을 지정한다면 숫자만 들어오게 제한할 수 있다.


### 와일드카드 타입
<a id="와일드카드-타입"></a>

코드에서 `?`를 일반적으로 와일드카드(wildcard)라고 부릅니다.    
제네릭 타입을 매개값이나 리턴 타입으로 사용할 때 구체적인 타입 대신에    
와일드카드를 다음과 같이 세가지 형태로 사용할 수 있습니다.

- 제네릭타입<?> : Unbounded Wildcards (제한 없음)
  - 타입 파라미터를 대치하는 구체적인 타입으로 모든 클래스나 인터페이스 타입이 올 수 있습니다.
- 제네릭 타입<? extends 상위타입> : Upper Bounded Wildcards (상위 클래스 제한)
  - 타입 파라미터를 대치하는 구체적인 타입으로 상위 타입이나 하위 타입만 올 수 있습니다.
- 제네릭 타입<? super 하위타입> : Lower Bounded Wildcards (하위 클래스 제한)
  - 타입 파라미터를 대치하는 구체적인 타입으로 하위 타입이나 상위 타입이 올 수 있습니다.

예시

타입은 다음 4가지 클래스라고 가정해봅시다.   
Person의 하위 클래스로 Worker와 Student가 있고,   
Student의 하위 클래스로 HighStudent가 있습니다.

<img src="img/day32/wild.png" width="500" height="350" alt="">

- Course<?> : 수강생은 모든 타입(Person, Worker, Student, HighStudent)이 될 수 있다.
- Course<? extends Student> : 수강생은 Student와 HighStudent만 될 수 있다.
- Course<? super Worker> : 수강생은 Worker와 Person만 될 수 있다.


이를 이용한 예제 (너무 길어서 접어놨습니다.)
<details>
<summary> 코스등록 </summary>

```java
public class Course<T> {
	private String name;
	private T[] students;

	public Course(String name, int capacity) {
		this.name = name;
		students = (T[]) (new Object[capacity]); //타입 파라미터로 배열을 생성하려면 new T[n] 형태로 배열을 생성할 수 없고 (T[]) (new Object[n])으로 생성해야한다.
	}

	public String getName() {
		return name;
	}

	public T[] getStudents() {
		return students;
	}
	
	public void add(T t) {
// 배열에 비어있는 부분을 찾아서 수강생을 추가하는 메소드 
		for (int i = 0; i < students.length; i++) {
			if (students[i] == null) {
				students[i] = t;
				break;
			}
		}
	}
}
```

</details>


<details>
<summary> 와일드카드로 분류 </summary>

registerCourse() : 모든 수강생들이 들을 수 있는 과정을 등록하고
registerCourseStudent() : 학생만 들을 수 있는 과정을 등록합니다
registerCourseWorker() : 직장인만 들을 수 있는 과정을 등록합니다.

```java
public class WildCardExample {

	public static void registerCourse(Course<?> course) {    //모든 과정
		System.out.println(course.getName() + " 수강생: " + Arrays.toString(course.getStudents()));
	}

	public static void registerCourseStudent(Course<? extends Student> course) {    //학생 과정
		System.out.println(course.getName() + " 수강생: " + Arrays.toString(course.getStudents()));
	}

	public static void registerCourseWorker(Course<? super Worker> course) {    // 직장인과 일반인 과정
		System.out.println(course.getName() + " 수강생: " + Arrays.toString(course.getStudents()));
	}

	public static void main(String[] args) {
		Course<Person> personCourse = new Course<Person>("일반인과정", 5);
		personCourse.add(new Person("일반인"));
		personCourse.add(new Worker("직장인"));
		personCourse.add(new Student("학생"));
		personCourse.add(new HighStudent("고등학생"));

		Course<Worker> workerCourse = new Course<Worker>("직장인과정", 5);
		workerCourse.add(new Worker("직장인"));

		Course<Student> studentCourse = new Course<>("학생과정", 5);
		studentCourse.add(new Student("학생"));
		studentCourse.add(new HighStudent("고등학생"));

		Course<HighStudent> highStudentCourse = new Course<>("고등학생과정", 5);
		highStudentCourse.add(new HighStudent("고등학생"));
		
		
		registerCourse(personCourse);
		registerCourse(workerCourse);
		registerCourse(studentCourse);
		registerCourse(highStudentCourse);				// 모든 과정 등록 가능
		System.out.println();
		
		// registerCourseStudent(personCourse);  (X)
		// registerCourseStudent(workerCourse);	 (X)	
		registerCourseStudent(studentCourse);
		registerCourseStudent(highStudentCourse);		// 학생 과정만 등록 가능
		System.out.println();
		
		registerCourseWorker(personCourse);				
		registerCourseWorker(workerCourse);				// 직장인과 일반인 과정만 등록 가능
		// registerCourseWorker(studentCourse); 	(X)
		// registerCourseWorker(highStudentCourse); (X)
		
	}
}
```

</details>



### 제네릭 타입의 상속과 구현
<a id="제네릭-타입의-상속과-구현"></a>

클래스의 상속 차이와 인터페이스의 구현으로 예시만 보면 이해할 수 있을 것 같다.

**상속(inherit)**

```java
public class ChildProduct<T, M> extends Product<T, M> {
}

public class ChildProduct<T, M, C> extends Product<T, M> {
}
```

만약 Product<T, M> 제네릭 타입을 상속하면 위처럼 자식에서 상속받아서   
타입을 더 받을 수도 있다.

**구현(implements)**

다음과 같이 제네릭 인터페이스가 있다고 가정해보면

```java
public interface Storage<T> {
	void add(T item, int index);

	T get(int index);
}
```

제네릭 인터페이스인 Storage<T> 타입을 구현한 StorageImpl 클래스도 제네릭 타입이어야 한다.

```java
public class StorageImpl<T> implements Storage<T> {
	private T[] array;

	public StorageImpl(int capacity) {
		array = (T[]) (new Object[capacity]);
	}

	@Override
	public void add(T item, int index) {
		array[index] = item;
	}

	@Override
	public T get(int index) {
		return array[index];
	}
}
```

ChildProductAndStorageExample은 ChildProduct<T, M, C>와 StorageImpl<T> 클래스의 사용 방법

```java
public class ChildProductAndStorageExample {

	public static void main(String[] args) {
		ChildProduct<Tv, String, String> product = new ChildProduct<Tv, String, String>();
		product.setKind(new Tv());
		product.setModel("SmartTv");
		product.setCompany("Samsoong");

		Storage<Tv> storage = new StorageImpl<>(100);
		storage.add(new Tv(), 0);
	}
}
```




<details>
<summary> 회고 </summary>

다른 모든 개념 통틀어서 제네릭이 제일 어려웠다.... <br>
좀 늦게 쓴거라 컬랙션도 배웠는데 컬랙션보다 이게 더 어렵다.<br>
간신히 이해만 한 느낌? <br>
와일드카드에서가 제일 오래걸린.....<br>
<br>
보통 실무에서 많이 쓰나? 궁금증이 생깁니다.


</details>