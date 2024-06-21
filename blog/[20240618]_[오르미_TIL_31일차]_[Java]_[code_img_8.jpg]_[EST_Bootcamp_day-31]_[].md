# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 제네릭](#-제네릭)
  - [제네릭이란?](#제네릭이란)




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
<img src="img/day30/" width="500" height="350" alt="">


<details>
<summary> 회고 </summary>



</details>