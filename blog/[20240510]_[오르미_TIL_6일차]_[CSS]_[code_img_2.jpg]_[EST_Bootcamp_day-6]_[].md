## 오르미 백엔드 6일차

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

- `static`: 기본값, 태그 순으로 정상적인 흐름(normal flow)에 따라 위치가 지정

<img src="img/day6/position1.png" width="300" height="400" alt="포지션 속성값 설명1">

- `relative`: 기본적인 자리에서 위치 이동이 가능.

<img src="img/day6/position2.png" width="300" height="400" alt="포지션 속성값 설명2">

- `absolute`: My way, 구애받지 않지만 부모 요소가 있으면 부모박스 내에서 시작

예시 (box3 적용)

<img src="img/day6/position3.png" width="300" height="400" alt="포지션 속성값 설명3">

- `fixed`: 고정 된 상태로 스크롤에 영향을 받지 않습니다.

<img src="img/day6/position4.png" width="300" height="400" alt="포지션 속성값 설명4">

- `sticky`: 속성값이 적용된 요소끼리 달라붙고 그자리를 씀.


- `z-index`: 에프터 이팩트 3D랑 개념이 비슷함.(3D개념을 웹페이지에서 적용 z값을 설정함)

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

> flex 추천 연습사이트\
> https://flexboxfroggy.com/#ko
> 

