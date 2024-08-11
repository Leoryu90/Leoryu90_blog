# [5기] 백엔드 개발자 부트캠프 오르미

**목차**

- [💡 Lightsail 인스턴스내 SpringBoot 실행](#Lightsail)
  - [환경셋팅](#환경셋팅)
    - [git 설치](#git-설치)
    - [Java 17 설치](#java-17-설치)
    - [Springboot 실행](#springboot-실행)
    - [nohup](#nohup)



## 💡 Lightsail 인스턴스내 SpringBoot 실행
<a id="Lightsail"></a>

### 환경셋팅
<a id="환경셋팅"></a>

#### git 설치
<a id="git-설치"></a>

```shell
sudo apt update
sudo apt install git -y
```

```shell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

깃 설정

```shell
git clone https://github.com/{username}/{your-repo}.git

# 예시
# git clone https://github.com/weniv/est-backend-5.git
```
깃 레포지토리 클론

#### Java 17 설치
<a id="java-17-설치"></a>

Azul Zulu 저장소 추가

```shell
sudo apt install gnupg ca-certificates curl

curl -s https://repos.azul.com/azul-repo.key | sudo gpg --dearmor -o /usr/share/keyrings/azul.gpg

echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://repos.azul.com/zulu/deb stable main" | sudo tee /etc/apt/sources.list.d/zulu.list
```

시스템 업데이트
```shell
sudo apt update && sudo apt upgrade -y
```

JDK 설치
```shell
sudo apt install zulu17-jdk
```

설치 확인
```shell
java -version
```

<img src="img/day47/aws1.png" width="700" height="200" alt="">

#### Springboot 실행
<a id="Springboot 실행"></a>

```shell
chmod +x gradlew
```

빌드를 위한 그래이들 실행 권한 설정

```shell
./gradlew build -Pprofile=dev
```

빌드 실행 (application-dev.yml 기반)

<img src="img/day47/aws2.png" width="700" height="200" alt="">

```shell
cd build/libs
java -jar basic-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev
```

<img src="img/day47/aws3.png" width="700" height="350" alt="">

> 주의사항으로는 AWS lightsail에서 포트를 허용해야한다.  
> 네트워킹에서 IPv4에서 내 포트번호를 추가할 것.
> 

실행을 완료하고 들어가보면 잘 작동하는 것을 볼 수 있다.

<img src="img/day47/aws4.png" width="700" height="350" alt="">

하지만 이걸 계속 틀어놓고 있어야할까?   
라고 생각한다면

#### nohup
<a id="nohup"></a>

`nohup`이란?

- "no hang up"의 약자입니다.
- 프로세스를 백그라운드에서 실행하고, 터미널 세션이 종료되어도 계속 실행되도록 합니다.

스프링부트 실행 시 `nohup` 사용 이유:

1. 세션 독립성:
  - SSH 연결이 끊어져도 애플리케이션이 계속 실행됩니다.
  - 서버 관리자가 로그아웃해도 서비스가 중단되지 않습니다.
2. 장기 실행:
  - 서버 애플리케이션은 지속적으로 실행되어야 합니다.
  - `nohup`은 이를 보장합니다.
3. 로그 관리:
  - 출력을 파일로 리다이렉트하여 로그를 저장할 수 있습니다.
  - 예: `nohup java -jar app.jar > output.log 2>&1 &`
4. 리소스 효율:
  - 터미널 세션을 차지하지 않아 서버 리소스를 절약합니다.
5. 원격 관리 용이성:
  - 관리자가 애플리케이션을 시작하고 안전하게 연결을 종료할 수 있습니다.


**nohup + Springboot**

```shell
nohup java -jar basic-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev > output.log 2>&1 &
```

<img src="img/day47/aws5.png" width="700" height="200" alt="">

이렇게뜨게 되는데

실행이 되고 있는지 확인은 아래와 같이 한다.

```shell
ps -ef
```

<img src="img/day47/aws6.png" width="700" height="200" alt="">

위에서 8689번호가 똑같이 떠있다.


> 추가 명령어   
> `kill` 
> 
> ```shell
> kill option PID
> kill 8689 
> ```
> 
> 8689 프로세스 종료를 할 수 있다.   
> 
> 옵션으로는   
> 2 : 인터럽트 시그널을 보낸다.   
> 9 : 프로세스를 강제 종료한다.   
> 15 : 프로세스와 관련된 파일을 정리한 후 종료한다. 종료되지 않는 프로세스가 남아있을 수 있다.  
> (설정이 없으면 15로 실행된다) 
>  



<details>
<summary> 회고 </summary>

조금 신기한 시간이었습니다. <br>
이제 진짜 뭔가 한발 다가선 느낌이 듭니다.<br>
<br>
힘들었던 시간이 조금 지나고 계단이 한개 올라간 느낌?<br>
이직은 많은 계단이 남았지만 성취감이 조금 드는 시간이었습니다.

</details>

