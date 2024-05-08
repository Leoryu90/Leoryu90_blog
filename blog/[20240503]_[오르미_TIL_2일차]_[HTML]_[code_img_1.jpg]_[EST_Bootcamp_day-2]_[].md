```
💡 git과 GitHub에 대해서 설명
```

### git

분산 버전관리 시스템

### **GitHub**

git을 기반으로 만든 서비스로 보다 편하게 git을 사용할 수 있음. (보통 GUI로 지원)

```
💡 GUI 실습
```

### **새 repo(저장소) 작성**

내 github home에서 new로 시작

public/private 설정

지금 우리가 하는 프로젝트는 퍼블릭으로

README 체크

안해도 따로 만들 수 있으나 우리는 하는게 좋음.

### **내용물 수정, 변경하기(commit)**

주소창 .com <-> .dev GitHub 사이트 에서 VScode 모드로 변경 가능

버전(commit) 만들기+push 하기

변경사항이 있으면

변경한 메세지 작성하고 커밋, 푸시

ex) :memo: 20240503 README 내용수정-1

- **키포인트**
    - commit에 깃모지(:memo:등)넣으면 프로젝트 구분에 좋음
    - 커밋을 잘못 했을 경우 지우거나 하지말고 새로 커밋하는게 좋음(오류가 발생)

### **Github 자체 퍼블리셔 해보기**

하고자 하는 repo 들어간 후, 우측 상단 settings 클릭

좌측 page 클릭

none>main으로 변경 후 save

새로고침하면 상단에 내 도메인 뜨며 완성

- **도메인관련**
```
  도메인 구매: 카페24 추천

  구매한 도메인 github에 적용법: page>custom domain탭 구매한 도메인 입력>save
  구입한 곳에서도 연결 필요함
```

```
💡 CLI 실습
```

### CLI 명령어(clone, pull, add, commit, push)

-   **git pull**:
     코드를 원격 저장소에서 가져옵니다.


-   **git add**:
    새로운 버전을 만들기 위한 준비작업을 진행합니다. 변경된 소스코드들을 등록합니다.


-   **git commit**:
    새로운 버전을 만듭니다.


-   **git push**:
    원격저장소에 코드를 올립니다.


-   **git clone**:
    원격저장소에 있는 코드 파일들을 로컬저장소에 복제

수많은 명령어가 있지만 위 4+1 개의 명령어가 중요함.

### **clone (Github → 로컬저장소로 가져오기)**

해당 repo 코드 복사

받을 폴더에 마우스 우클릭으로 git bash 연다

git bash에 아래 코드 입력하고 branch 뜨면 repo와 연결 완료

```jsx
$ git clone 복사한 코드 .
```

> 주의사항 : 코드 다음 ^.(한칸 띄우고 dot) 을 해야 편함
안하면 폴더안에 폴더가 또 들어간 상태로 복사가 됨.
>

### add

새로운 버전을 만들기 위한 준비작업 진행, 변경된 소스코드를 등록
어떤 파일을 github에 업로드할지 지정 가능(전체/지정)

전체 파일 업로드

```jsx
$ git add .
```

지정 파일 업로드

```jsx
$ git add 파일명
```

> **팁**
>```jsx
>& git status
>```
>git add로 잡힌 파일 확인 가능

### commit

add 된 목록을 묶어서 하나의 버전으로 저장함

```jsx
$ git commit -m "저장명"
```

> **팁** : 저장명에 깃모지 사용시 알아보기 편함(회사에서도 많이 사용)
>

### push

commit 된 내용을 원격저장소로 동기화 시킴.

```jsx
$ git push
```

> 로그인 창이 뜨는 경우가 있음.(로그인해주면 동기화 진행)
>

### pull

원격 저장소에 업데이트 된 데이터를 가져오고 병합할 때 사용

공동 작업 시 다른 작업자가 먼저 작업물 push 넣은 경우 병합 필요

```jsx
$ git push
```

추가 명령어
- diff ($ git diff): add 하기 전 최근 commit한 내용과 현재 폴더의 변경 사항을 확인
- log ($ git log): 커밋(commit) 히스토리 조회하기
- cd ($ cd 폴더명, cd ..): 폴더이동 명령어
- list ($ git config —list): 변경사항 확인 (username 확인했음)

생성 명령어
- touch($ touch 파일명.확장자): 파일생성
- mkdir($ mkdir 폴더명): 폴더생성
- init($ git init): .git폴더 생성(Git으로 연결한다는 것)