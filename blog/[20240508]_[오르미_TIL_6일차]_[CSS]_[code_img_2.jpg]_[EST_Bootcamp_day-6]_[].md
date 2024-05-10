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
   <code style="background-color:#f1f1f1; padding:2px 4px; border-radius:4px;">display:flow-root</code>
### 💡 position

#### position이란?

- HTML 태그의 위치를 지정해주는 속성

#### position의 종류

- position : static
  - 기본값으로 태그 순으로 정상적인 흐름(normal flow)에 따라 위치가 지정



- position : relative
- position : absolute
- position : fixed
- position : sticky
- z-index

