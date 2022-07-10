

# [Spring] 환경설정





설치 전 기본적으로 자바랑 톰캣이 필요하기 때문에 

설치 되었다고 가정하고 진행하겠다.



먼저 본인이 사용하고 있는 경로에 WokSpace를 생성한다

필자는 springWorkspace 폴더를 생성하여 라이브러리 안에 추가하였다.



### STS 설치

[https://spring.io/tools/](https://spring.io/tools/) 사이트 접속



#### STS3
- 스프링 개발 도구
- 모든 유형의 프로젝트 생성 가능 

#### STS4

- Spring Boot만 포함
- Legacy Project(Spring MVC Project)를 사용하려면 Add-On 추가 설치해야 하고
  - Spring Tools 3 Add-On for Spring Tools 4
- JSP 사용하기 위한 Eclipse Enterprise Java and Web Developer Tools 설치 필요



그렇기 때문에 필자는 STS3를 설치하겠다

위 사이트에 접속하여 스크롤을 내리다 보면 아래와 같은 창이 있다

Spring Tool Suite 3 wiki 링크를 클릭한다.



![스크린샷 2022-07-10 오후 4 48 22](https://user-images.githubusercontent.com/101630615/178136673-64455b78-9552-44ca-8caa-d0640816d16c.png)



사이트에 접속 후 우측 탭 바를 보면 버전 별로 나와있다

필자는 3.9.18 버전을 설치하였다.

![스크린샷 2022-07-10 오후 4 49 39](https://user-images.githubusercontent.com/101630615/178136674-afb540e9-f491-4921-9b76-f49555180155.png)



클릭하여 이클립스 4.21 버전의 본인의 운영체제에 맞는 파일을 다운로드하면 된다

현재 m1을 사용하고 있기 때문에 tar.gz를 다운로드하였다.



![스크린샷 2022-07-10 오후 4 51 55](https://user-images.githubusercontent.com/101630615/178136676-148b49c3-969b-4478-b55d-914f3a8f493e.png)



파일명이 길어 그대로 압축 해제하면 오류가 발생한다

파일명을 ``s.tar.gz`` 파일 형식에 맞게 변경한다.

윈도우는 파일을 C 또는 D 드라이브 바로 아래로 이동, 

맥은 라이브러리 안에 파일을 이동 후 압축 해제한다.



실행 후 전에 생성해둔 Wokrspace 경로에 맞는 폴더를 선택 후 Launch

<img width="628" alt="스크린샷 2022-07-10 오후 4 55 38" src="https://user-images.githubusercontent.com/101630615/178136677-66a933bb-3698-40b1-82c6-a74f786135ac.png">





![스크린샷 2022-07-10 오후 4 57 53](https://user-images.githubusercontent.com/101630615/178136682-6f851cb3-9639-4550-b5e6-50cc3d0f6f11.png)

실행 후 대시보드 화면이 나오는데 넘어가면 된다.



Perspective 설정을 위해 



메뉴 탭 -> Window -> Perspective -> Open Perspective -> Other..



<img width="681" alt="스크린샷 2022-07-10 오후 4 56 57" src="https://user-images.githubusercontent.com/101630615/178136678-d17b0dee-72b9-4331-9a35-e141193c29d8.png">

Spring을 Defult값으로 지정하고 Open 클릭



<img width="340" alt="스크린샷 2022-07-10 오후 4 58 41" src="https://user-images.githubusercontent.com/101630615/178136683-091247fa-9aba-4846-853d-906ebbdd62c2.png">





인코딩을 한글로 설정하기 위해 

Preferences 설정에 들어간다. 

General -> Worksapce : Other : UTF-8 (현재 디폴트 값이 UTF-8로 설정되어 있으면 상관없다.)

Web -> HTML / CSS / JSP 

모두 UTF-8로 설정한다.



#### Workspace

<img width="752" alt="스크린샷 2022-07-10 오후 5 01 45" src="https://user-images.githubusercontent.com/101630615/178136684-2d5e51d4-0bb8-41a8-8a81-baa4b84ebbf7.png">





#### HTML

<img width="752" alt="스크린샷 2022-07-10 오후 5 02 04" src="https://user-images.githubusercontent.com/101630615/178136688-7da00a0c-3dd4-461f-871e-c62a4022824a.png">





#### CSS 

<img width="752" alt="스크린샷 2022-07-10 오후 5 02 01" src="https://user-images.githubusercontent.com/101630615/178136687-e01480d3-c9f6-4d13-aaff-6467dde3293b.png">





#### JSP

<img width="752" alt="스크린샷 2022-07-10 오후 5 02 07" src="https://user-images.githubusercontent.com/101630615/178136689-298e5857-116b-415c-958c-081645e3406e.png">





서버  설정을 위해 톰캣을 추가한다.

Server -> Runtime Environments  -> Add



<img width="752" alt="스크린샷 2022-07-10 오후 5 02 27" src="https://user-images.githubusercontent.com/101630615/178136690-61c1e6e7-fec5-454a-9e26-3051928670a6.png">





본인이 설치한 톰캣 버전에 맞춰 Create a new local server를 체크 후 Next



<img width="586" alt="스크린샷 2022-07-10 오후 5 02 47" src="https://user-images.githubusercontent.com/101630615/178136692-ea4ff42b-586d-4dfa-9d37-9c966f123de6.png">





톰캣을 설치한 경로를 지정해주면된다.

(현재 톰캣을 이미 설치한 상태라 이름 중복 오류)

<img width="586" alt="스크린샷 2022-07-10 오후 5 02 57" src="https://user-images.githubusercontent.com/101630615/178136693-1de8705c-3f57-4fa7-8a4a-c36df0d09bc2.png">





STS 초기 설정 완료