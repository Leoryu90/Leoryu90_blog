## 오르미 백엔드 4일차

### 💡 양식(form)

#### form
-   기본적인 양식

```html
<body>
    <form action=""method="">
        <input type="" name="">
      <button>submit</button>
    </form>
</body>
```

##### method

양식을 제출할 때 사용할 **HTTP 메서드**입니다.

-  post
    - 데이터의 길이제한이 없고, GET 방식보다 보안성이 높습니다.
    - POST 방식의 HTTP 요청에 의한 데이터는 쿼리 문자열과는 별도로 전송 합니다.



- get
  - get 방식의 요청은 브라우저에 의해 캐시되어 저장됩니다.
  - ex) example.com?name=홍길동&age=20

|  | POST | GET |
| --- | --- | --- |
| 전송 | 양식 데이터를 요청 본문으로 전송 | https://example.com?name=홍길동&age=20 |
| 캐시 | X | O |
| 길이제한 | X | O |
| 보안 | GET 방식보다 높음 | 취약 |

##### action

- 작성된 양식 데이터를 처리할 프로그램의 URL를 적어줍니다.
- 속성을 지정하지 않으면 데이터는 form이 있는 페이지의 URL로 보내집니다.

> form은 백엔드 개발자가 프론트엔드 개발자에게\
> 형식을 정해서 요청해야하는 사항으로\
> 백엔드 개발자도 꼭 알아야하는 부분

#### input

- 사용자에게 정보를 입력받음.

##### name/value

- 이름/값(name/value)의 짝으로 양식과 함께 전송됩니다

##### autocomplete

- 입력요소가 **자동완성**된 값을 기본값으로 가질 수 있는지 나타니다.

```html
<input type="email" autocomplete="on" />
```

![자동입력 예시](img/day4/at_r.png)

> 자동입력이 ON이라면 보안상 문제가 될 수 있습니다.

#### label

- 사용자 인터페이스의 항목을 나타냅니다.
- input과 함께 사용합니다.

for-id를 이용해 연결하기:
```html
<label for="user-id">아이디</label>
<input id="user-id" type="text">
```
label 안에 input 중첩하여 연결하기:
```html
<label>
	아이디
	<input type="text">
</label>
```
> label 안에 제목요소를 배치 하지 말 것!\
> form에 제목이 필요한 경우 fieldset / legend 사용하기

#### button
- 사용자가 클릭할수 있는 요소입니다.
- form 내부뿐만 아니라 버튼이 필요한 곳이라면 어디에든 배치할 수 있습니다.
> form 안에 쓰면 초기값은 submit으로 클릭하면 서버로 양식 제출
>  

![HTML form에 대한 예시 이미지](img/day4/Frame_60.png)

위와 같은 방식으로 진행이 됩니다.

> **중요**
> - HTML 여러 속성들을 다 외울 수 없음.
> - MDN에서 참고를 많이 합니다.
> - https://developer.mozilla.org/ko/docs/Web/HTML/Element
ㄴ