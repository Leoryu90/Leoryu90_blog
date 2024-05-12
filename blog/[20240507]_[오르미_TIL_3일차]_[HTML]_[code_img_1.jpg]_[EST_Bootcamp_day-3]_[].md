## 오르미 백엔드 3일차

### 💡 HTML 이론

#### 백엔드 개발자가 프론트를 공부하는 이유?
개인 프로젝트를 진행을 한다면 더욱 좋다.\
프론트를 알면 협력할 때 더욱 좋고 백엔드를 이해하는 폭이 더욱 넓어짐.

#### HTML 태그
**웹 문서에 정보를 정의해주는 형식**
![요소 이미지](img/day3/tag_element.png)
-   <>시작태그(여는태그)와 </>종료태그(닫는태그)의 쌍으로 구성
-   여는 태그와 닫는 태그 사이에는 컨텐츠가 들어감

#### 개발자도구
사용하는 브라우저에서 HTML,CSS, JS 등의 구조와 결과를 알 수 있음

-   엘리멘츠(HTML,CSS)
-   콘솔(JS)
-   네트워크(백엔드와 어떤정보 받는지)

> F12, ctrl + shift + i 로 알 수 있음.

#### 주석
미래의 나, 동료개발자를 위해 사용한다.

--------------------

### 💡 HTML 실습

#### HTML 기본 구조
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

> **팁** 문서를 새로 만들고 !를 쓰면 탭으로 기본 주조를 만들 수 있습니다.
 
##### <!DOCTYPE html>
이 문서는 html Living Standard 문서!’라는 의미
> 작성하지 않아도 기본적으로 브라우저가 알아서 처리해줌
> 


##### html 태그
`<html>`태그는 HTML 문서의 루트, 최상단 요소\
`<html lang="en">`lang 속성을 통해 해당 페이지의 주 언어 설정

##### head

검색엔진을 위한 다양한 정보들이 담기는 곳\
ex) title, 파비콘, viewport 정보 등

##### body
body 태그는 사용자에게 보이는 영역\
본격적으로 우리가 작성할 영역

#### 블록 레벨 요소 vs 인라인 요소

![블록 레벨 요소 vs 인라인 요소](img/day3/block-inline.png)

##### block
부모 요소의 전체 공간을 차지하여 블록을 만듬\
이전, 이후 요소 사이에 줄 바꿈이 일어남

##### inline
항상 블록 레벨 요소 내에 포함\
콘텐츠의 흐름을 끊지 않으며, 컨텐츠에 따라 할당된 공간만 차지함\
새로운 줄을 만들지 않음

> block / inline / inline-block
> ![block / inline / inline-block 관계도](img/day3/block_inline_inline-block.png)
> 


#### 이후 다양한 태그 실습
과제 코드
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>homework airbnb</title>
    <style>
        #home_logo {
            height: 50px;
            width: 120px;
        }

        #main_post2_img1 {
            height: 200px;
            width: 300px;
        }
        #main_post2_img2 {
            height: 200px;
            width: 300px;
        }
        #main_post2_img3 {
            height: 200px;
            width: 300px;
        }
    </style>
</head>
<body>
    <header>
        <!-- 좌상단 홈으로 이동하는 로고링크 -->
        <a href="homework.html">
            <img id="home_logo" src="https://news.airbnb.com/wp-content/uploads/sites/4/2017/07/airbnb-newsroom-twitter-card-default.png?fit=2400%2C1260" alt="logo">
        </a>

        <a href="">당신의 공간을 에어비엔비하세요</a>

        <a href="">language</a>

        <!-- 우상단 메뉴, 프로필 그룹 -->
        <a href="peofile.html"> profile </a>
    </header>

    <main>
        <div id="main_post1">
            <div id="main_post1_s1">
                <a href="">이번 주 신규 들록 체험</a>
            </div>
            <div id="main_post1_s2">
                <button><</button>
                <button>></button>
            </div>
        </div>

        <div id="main_post2">
            <div id="main_post2_Alls">
                <a href=""><img id="main_post2_img1" src="https://a0.muscache.com/im/pictures/e35bb307-05f4-48a4-bdc5-3b2198bb9451.jpg?im_w=1440" alt=""></a>
                <a href=""><img id="main_post2_img2" src="https://a0.muscache.com/im/pictures/2fe40f4f-5ea3-432f-9fbd-e2ce3c6c3855.jpg?im_w=1440" alt=""></a>
                <a href=""><img id="main_post2_img3" src="https://a0.muscache.com/im/pictures/2fe40f4f-5ea3-432f-9fbd-e2ce3c6c3855.jpg?im_w=1440" alt=""></a>
            </div>
        </div>

        <div id="main_post3">
            <div id="main_post3_s">
                <button>날짜</button>
                <button>일행당 인원 수</button>
                <button>필터 추가하기</button>
                <button>단체로 즐기기에 적합</button>
                <button>동물</button>
                <button>예술 및 글쓰기</button>
                <button>쿠킹</button>
            </div>
        </div>
    </main>

    <footer>
        <div id="footer_ln1">
            <a href="">에어비엔비 지원</a>
        </div>

        <div id="footer_ln2">
            <a href="">호스팅</a>
        </div>

        <div id="footer_ln3">
            <a href="">에어비엔비</a>
        </div>
    </footer>
</body>
</html>
```