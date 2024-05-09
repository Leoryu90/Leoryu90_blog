## 오르미 백엔드 5일차

#### HTML 표(table)

- 테이블을 생성한다.

테이블 기본 형식
```html
<table>
    <caption>표에대한 설명</caption>
    <thead></thead>
    <tbody>
        <tr>
            <th></th> or <td></td>
        </tr>
    </tbody>
    <tfoot></tfoot>
</table>
```
표(table)을 이해할 수 있는 예시

![표(table)을 이해할 수 있는 예시](img/day5/table.png)


#### tr, th, td
- **tr**: table row. 테이블의 행
- **th**: table header. 테이블의 행, 열의 제목을 나타내는 셀
- **td**: table data. 셀 내용

#### caption
- 테이블의 제목이나 설명을 쓰는 태그입니다.

#### thead, tbody, tfoot
- **thead**: 테이블 행 블록(row block) 내에 **제목 열 그룹**(column headers)으로 구성할 경우 사용.
- **tbody**: 행 블록 내에 **테이블 데이터**로 구성할 때 사용.
- **tfoot**: 행 블록 내에 **열 요약**(column summaries)로 구성할 때 사용.

#### colspan, rowspan

- colspan: 열 병합
- rowspan: 행 병합

> **주의사항**:\
> 열별합은 열과 열의 병합으로 우리가 생각할 때에는 행병합입니다.\
> 행 병합도 같은 방식의 작용을 가집니다.

#### col, colgroup

- **colgroup**: 테이블 열 그룹을 만들고 싶을 때 사용합니다
- **col**: 테이블 열을 하나 이상 묶을 때 사용, colgroup 요소 내부에 포함.(필수X)

예시
```html
<table>
    <colgroup>
        <col> 
        <col span="2" class="batman">
        <col span="2" class="flash">
    </colgroup>
</table>
```

### 💡 CSS 1일차

#### CSS란?

- Cascading Style Sheets의 약자
- HTML의 스타일, 레이아웃 등을 꾸미는 역할을 합니다.

작성방법
```css
선택자 {
    속성(ex: color) : 속성값(ex: red) ;
}
```

#### 주석

```css
/* 주석 */
```

#### CSS 적용법

1. 인라인 방식
   - 태그 자체에 style 속성으로 스타일을 주는 방식입니다.
   - 일부 스타일 적용에 제한이 있음
```html
<p style="color:yellow; background-color:black;">Hello wold</p>
```
2. 내부 스타일
    - head 태그 안 style 태그를 사용하여 스타일을 주는 방식입니다.
    - 코드가 길어질수록 HTML 파일 길이가 길어지기 때문에 효율적이지 않습니다.
```html
<head>
    <style>
        p {
            color:yellow; 
            background-color:black;
        }
    </style>
</head>
```
3. 외부 스타일
    - 현재 문서와 외부 리소스의 관계를 명시합니다.
    - 해당 방법을 가장 권장

.HTML
```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

style.css(따로 파일 만듬)
```css
p {
    color:yellow; 
    background-color:black;
}
```

#### 상속

```html
<div>
	<h1>Hello</h1>
	<h2>Hello</h2>
	<p>Hello</p>
</div>
```
쉽게 설명하면 위의 예시에서 h1,h2,p 태그를 모두 CSS로 적용시키려면\
각각 지정하거나 인라인 스타일로 적용할 수도 있지만\
Div로 묶여있기 때문에 Div에 스타일을 적용하면 h1,h2,p 태그를 모두\
스타일적용이 됨.

> width, height, margin, padding, border 와 같은 것은 상속되지 않음
>

#### CSS 선택자

종류
- 전체 선택자(*)
- 타입(유형) 선택자(태그명)
- 아이디 선택자(#)
- 클래스 선택자(.)
- 특성 선택자([])
- 그룹 선택자(,)
- 자손(하위) 선택자(상위태그^하위태그) ^=띄어쓰기
- 자식 선택자(상위태그>하위태그)
- 일반 형제 선택자(태그~같은 라인의 태그)
- 인접 형제 선택자(태그+같은 라인의 태그)

> 클래스 선택자(.) 가 제일 중요
>
가상 클래스 선택자

| 키워드      | 작용               |
|----------|------------------|
| :link    | 방문하지 않은 링크       
| :visited | 방문한 링크           |
| :hover   | 마우스 커서를 올려 놓았을 때 |
| :active  | 마우스로 클릭했을 때      |
| :focus   | 포커스 되었을때         |

구조적 가상 선택자
- :first-child - 형제 요소 그룹 중 첫 번째 요소
- :last-child - 형제 요소 그룹 중 마지막 요소
- :nth-child - 형제 사이에서의 순서에 따라 요소를 선택할 수 있습니다.

#### CSS 선택자 우선순위

가중치
1. **inline 스타일 속성**
2. id **#**
3. class ., 가상 클래스, 속성선택자
4. type(tag), 가상 요소 선택자

위와 순서대로 가중치가 높습니다.

우선 순위 계산

| inline-style | 1000점 |
| --- | --- |
| id 선택자 # | 100점 |
| class ., 가상클래스, 속성선택자 | 10점 |
| 타입, 가상요소 선택자 | 1점 |
| 전체선택자 * | 0점 |

> !important : 이 선언은 다른 CSS의 어떤 선언 보다도 우선으로 함\
> **important 사용은 좋지 못한 습관** 웬만하면 지양
> 

#### display 속성

- 박스의 유형을 지정하여 다른 박스들과 어떤 방식으로 배치할지 레이아웃을 설정

![CSS에서 디스플레이를 표현한 예시](img/day5/display.png)
출처: 위니브

- block : 블록단위로 요소 상자를 생성
- inline : 인라인단위로 요소 상자를 생성
- inline-block: inline : 블록 + 인라인 한 줄에 놓이지만 width, height, margin, padding 값을 모두 설정할 수 있습니다.
- flex: 내부 자식 요소들의 위치를 부모 컨테이너 요소 안에서  x, y축 단방향(1차원적)으로 설정합니다.
- grid: 내부 자식 요소들의 위치를 부모 컨테이너 요소 안에서 x, y축 모두 이용해(2차원적) 설정합니다.
- none: 해당 요소, 하위 요소가 사라지고, 스크린리더에도 읽히지 않습니다.

#### CSS Box Model

- HTML 요소를 감싸는 상자입니다.
- 요소, 패딩, 테두리, 마진으로 구성

<img src="img/day5/box.png" width="300" height="200" alt="CSS에서 요소의 box model을 설명하는 그림">

**CSS Box Model 관련 명령어**

- width: 요소의 너비를 설정
- height: 요소의 높이를 설정
> inline 요소는 width, height, 상하 margin 값이 적용되지 않습니다
> 
- padding: 패딩 크기 조절 (px 등 단위가 필요)
- margin: 마진 크기를 조절 (px 등 단위가 필요)
- border: 테두리 지정

