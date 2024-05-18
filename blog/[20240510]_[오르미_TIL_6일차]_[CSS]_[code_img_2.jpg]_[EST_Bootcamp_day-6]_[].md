## 오르미 백엔드 6일차

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

20240509 내용 주제로 합침.

------------------

### 💡 복습

#### 마진병합 현상 (전 시간 추가설명)

1. 요소와 요소의 사이에 마진 탑(margin-top) 혹은\
마진 바텀(margin-bottom)의 공간이 있을 경우\
더 높은 값의 마진 값이 적용되는 현상

<img src="img/day6/margin1.png" width="300" height="200" alt="1번째 마진 병합현상">

2. 부모 요소와 자식 요소가 존재할 때,\
   자식 요소의 마진 탑 혹은 마진 바텀 값이\
   부모의 높이에 영향을 미치지 않는 현상

<img src="img/day6/margin2.png" width="300" height="200" alt="2번째 마진 병합현상">

해결방법
1. 부모 요소에 `overflow` 속성 값을 적용해줍니다.
2. 부모 요소에 `display: inline-block` 값을 적용해줍니다.
3. 부모 요소에 `border` 값을 적용해줍니다.
4. 부모 요소에 `display:flow-root`을 사용합니다. (IE 지원 불가)

> **추가 학습**\
> ir 기법 : 그림이나 어떠한 기능이 있는 곳에 글귀를 숨겨서 표현하는 방식\
><img src="img/day6/plus.png" width="300" height="200" alt="ir기법을 설명하는 예시">
>  

------------------

### 💡 position

#### position이란?

- HTML 태그의 위치를 지정해주는 속성

기본틀
```css
 선택자 {
   position:static;
}
```

#### position의 종류

`static`: 기본값, 태그 순으로 정상적인 흐름(normal flow)에 따라 위치가 지정

<img src="img/day6/position1.png" width="300" height="400" alt="포지션 속성값 설명1">

`relative`: 기본적인 자리에서 위치 이동이 가능.

<img src="img/day6/position2.png" width="300" height="400" alt="포지션 속성값 설명2">

`absolute`: My way, 구애받지 않지만 부모 요소가 있으면 부모박스 내에서 시작

예시 (box3 적용)

<img src="img/day6/position3.png" width="300" height="400" alt="포지션 속성값 설명3">

`fixed`: 고정 된 상태로 스크롤에 영향을 받지 않습니다.

<img src="img/day6/position4.png" width="300" height="400" alt="포지션 속성값 설명4">

`sticky`: 속성값이 적용된 요소끼리 달라붙고 그자리를 씀.


`z-index`: 에프터 이팩트 3D랑 개념이 비슷함.(3D개념을 웹페이지에서 적용 z값을 설정함)

<img src="img/day6/position5.png" width="300" height="300" alt="포지션 속성값 설명5">

------------

### 💡  flex(중요)

#### flex-container에 사용하는 속성

``display:flex`` :자식 요소들이 컨테이너 안 공간을 맞추기 위해서 크기를 키우거나 줄이는 방법을 설정하는 방법

부모 요소 flex-container
자식 요소 flex-item

<img src="img/day6/flex1.png" width="500" height="500" alt="플랙스 다이랙션의 방향에 대한기본 설명">

#### flex-direction

`row` : 기본값. 왼쪽에서 오른쪽 (주축이 행 방향)\
`column`: 위에서 아래 방향 (주축이 열 방향)\
`row-reverse`: 오른쪽에서 왼쪽\
`column-reverse`: 아래에서 위 방향

#### justify-content

주축을 기준으로 배열의 위치를 조절하거나 아이템 간의 간격을 설정

종류

>`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`


#### align-items, align-content

- `align-items`: 교차 축을 기준으로 정렬합니다.
- `align-content`: 컨테이너의 교차 축의 아이템들이 여러 줄일때 사용 가능합니다.
   - `flex-wrap:wrap` 인 상태에서 사용해야 합니다.


#### gap

- 아이템 사이의 간격을 설정할 때 사용 할 수 있는 속성입니다. 


#### flex-wrap

- 한 줄에 배치되게 할 것인지, 가능한 영역 내에서 여러 행으로 나누어 표현할 것인지 결정

#### flex-flow

- flex-direction flex-wrap 단축속성 (한번에 작성하는 속성)

```css
flex-flow: row wrap;
```

-----------------


> flex 추천 연습사이트\
> https://flexboxfroggy.com/#ko
> 

