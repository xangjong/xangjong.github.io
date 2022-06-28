# [BackEnd] 서블릿



### JSP와 Servlet

- JSP (Java Server Page)
  - 서버측 스크립트 언어
  - 형식 : HTML 내에 Java 언어를 삽입한 문서 형태
  - ``.jsp``
- Servlet(Server + Applet)
  - Java 언어로 이루어진 웹 프로그래밍 문서
  - 자바 코드에 의존적
  - ``.java``



### JSP 페이지의 실행 과정 

<img width="452" alt="image-20220628173352410" src="https://user-images.githubusercontent.com/101630615/176135409-fe2e6b98-b8c5-4219-a8f6-aa21cad8c536.png">



### 서블릿

- 서버 측에서 실행되면서 클라이언트의 요청에 따라 동적으로 서비스를 제공하는 자바 클래스 (응답 : HTML  형식)
- 자바 플랫폼에서 컴포넌트 기반의 웹 애플리케이션을 개발하는 핵심 기술 (동적 웹  애플리케이션 컴포넌트)
- 컨테이너 종류에 상관없이 실행됨 (플랫폼 독립적)
- 독자적으로 실행되지 못하고 톰캣과 같은 JSP/Servlet 컨테이너에서 실행
- 자바로 만들어져 자바의 특징(객체 지향)을 가짐
- 스레드 기반
- JSP 페이지처럼 화면에 내용을 표시할 목적으로 사용하는 것이 아니라 MVC 패턴에서 로직인 모델(Model)과 화면에 결과를 표시하는 view 사이에서 제어를 하는 컨트롤러로 사용됨 
- java 파일이기 때문에 src/main/java 폴더에 위치
  - webapp 폴더 - HTML 문서



#### 서블릿 처리 순서

- 클라이언트에서 서블릿 요청이 들어오면
- 서버에서 서블릿 컨테이너를 만들고 스레드 생성
- 요청 시 마다 스레드 생성
- 서블릿 컨테이너는 스레드를 가동하여 서블릿 객체 생성
- 서블릿 객체의 실행이 종료되면 스레드 종료되고 반환
- 서블릿 실행 결과가 웹 서버에 전송 
- 이 결과를 웹 서버가 웹 브라우저에게 전송 

<img width="500" alt="image-20220628173402966" src="https://user-images.githubusercontent.com/101630615/176135429-5bea49ad-30c3-4554-a986-e78ec91827e4.png">

- 같은 Servlet class에 대한 요청을 처리하는 모든 thread는 같은 Servlet 객체 공유
- 로컬 변수가 각 요청 스레드마다 각 스택영역에 저장되어 동시성 문제를 발생시키지 않음



#### 서블릿 라이프 사이클 (생명주기)

<img width="400" alt="image-20220628173514261" src="https://user-images.githubusercontent.com/101630615/176135435-995cd749-f7e6-4ffe-9f97-dec1f6721b6d.png">



#### 서블릿 패키지

- ``javax.servlet.*``
  - 서블릿 작성을 위한 인터페이스와 클래스 제공
- ``javax.servlet.http.*``
  - HTTP 프로토콜을 이용한 서블릿 작성에 필요한 인터페이스 제공 (GET/POST)



#### 서블릿 클래스

- Servlet 인터페이스
- GenericServlet 추상 클래스
- HttpServlet 클래스를 상속 받음



##### Servlet 많이 사용하는 이유 : 빠른 응답 속도 때문

- 서블릿은 최초 요청 시 객체가 만들어져 메모리에 로드되고 이후 요청 시에는 기존의 객체 재활용
- 따라서 동작 속도가 빠름



#### 서블릿 장점

- 신뢰성
- 확장성 - 기능 확장 용이
- 플랫폼과 서버에 독립적 (자바 기반)
  - 한 번 개발된 애플리케이션은 다양한 서버 환경에서 실행 가능
- Java에서 제공되는 다른 기술을 같이 사용 가능
  - 예 : Servlet과 JDBC 연동



#### 서블릿 생성 과정

<img width="350" alt="image-20220628173530128" src="https://user-images.githubusercontent.com/101630615/176135440-0055f5dd-790a-4a53-acfc-a8757d01e26e.png">





#### 서블릿 매핑 (Mapping)

- 서블릿 경로 연결
- 서블릿 파일 경로 노출로 인한 보안 문제를 없애고
- url을 간단하게 줄일 수 있음
- 웹 브라우저에서 서블릿을 요청하기 위해서는 서블릿 맵핑 필요



#### 서플릿 매핑 방법

1. web.xml에서 설정
2. 어노테이션 이용 : 이클립스에서 자동 지정
   - 변경 가능
   - 변경해서 사용하는 방법



#### 서블릿 프로젝트 생성

- 새 프로젝트 : Dynamic Web Project
  - 프로젝트명 : Servlet01
    - Generate web.xml 체크
- 패키지 생성 
  - Src/main/java 폴더에 패키지 추가
  - 패키지명 : sec01
- 클래스 생성
  - sec01 패키지에 서블릿 추가
  - 클래스명 : FirstServlet
  - Next 누르고 URL mappings 이름 한 번 확인하고
  - Next 누르고 아래에서 다음 메소드 추가 체크
    - ``init / destroy / doGet``
    - doPost는 체크 해제
  - Finish 



#### 이클립스 프로젝트에서 서블릿 사용

- **servlet-api.jar** 추가 
- C:\apache-tomcat-9.0.64\lib에 들어 있음
- 프로젝트의 Properties 창 열고
- Java Build Path / Libraries 탭  -> Classpath에 [Add External JARs]로 추가할 것임



##### 프로젝트 실행 결과 확인

- url : ``http://localhost:8080/Servlet01/FirstServlet``
- ``/FirstServlet``  : 서블릿 맵핑 이름
- 콘솔창 출력 내용
  - 처음 실행 시 초기화되고 ``doGet()`` 메소드 호출
  - init 메소드 호출됨
  - doGet 메소드 호출됨
- 웹 브라우저 새로고침하면 다시 초기화는 안 되고  ``doGet()`` 메소드만 호출됨
  - init 메소드 호출됨
  - doGet 메소드 호출됨
  - doGet 메소드 호출됨
- ``init()`` 메소드안에서 라인 추가 엔터누르고 저장(Ctrl+S)한 후 조금 기다리면 콘솔창에 ``destroy()`` 메소드 호출됨
- : 서블릿 수정 시 호출됨



#### 서블릿 맵핑 이름을 다른 이름으로 추가(변경)

- web.xml 에서 추가 
- /first 이름으로 추가

```
<servlet></servlet> 
<servlet-mapping>
```

- web.xml 내용 변경했으면 반드시 톰캣 서버 중단했다가 다시 실행



#### 요청 처리 객체 / 응답 처리 객체

- 톰캣에서 request 객체와 response 객체 생성해서 doGet() 메소드 안에 인자 값으로 넣어 줌
- request 객체 : 요청 처리 객체
  - 클라이언트에서 입력한 데이터가 request 객체에 담겨서 서버로 전달 
- response 객체 : 응답 처리 객체
  - 서버 측에서 처리한 결과를 response 객체에 담아서 클라이언트로 전달

- ``doGet()``과 ``doPost()`` 메소드 둘 다 매개변수로 request/response 객체를 가짐



### 컨텍스트 (Context)

- 톰캣의 server.xml에 등록하는 웹 애플리케이션을 컨텍스트
- 즉, 톰캣 입장에서 인식하는 한 개의 웹 애플리케이션
- 웹 애플리케이션 당 하나의 컨텍스트가 등록됨
- 웹 애플리케이션 이름과 같을 수도 다를 수도 있음
- 컨텍스트 이름은 중복되면 안 됨
- 웹 애플리케이션의 의미를 가장 잘 나타낼 수 있는 명사형으로 지정
- 대소문자 구분
-  server.xml에 등록

- 모든 설정 정보를 xml 로 저장한 후 실행 시 정보를 읽어와 설정대로 실행
- 이클립스에서 프로젝트를 생성하면 자동으로 server.xml에 추가
- Servers / server.xml 열고 확인 : ``<Context>`` 태그



<img width="500" alt="image-20220628173609671" src="https://user-images.githubusercontent.com/101630615/176135443-48833a7a-790c-4541-89ce-5f9b1c9d3351.png">



#### URL / URI / ContextPath / ServletPath

- URL : 전체 주소 
  - ``http://localhost:8080/Servlet01/first``
  - 프로토콜 + IP + 포트번호 + URI

- URI : ContextPath + ServletPath
  - /Servlet01/first
  - 프로젝트명 + 서블릿 맵핑 이름

- ContextPath : 프로젝트명 
  - /Servlet01

<img width="460" alt="image-20220628173627749" src="https://user-images.githubusercontent.com/101630615/176135450-2e6bca2d-bb58-44f5-8f89-251519516da9.png">



##### URI (Uniform Resource Identifier : 통합 자원 식별자)

- 특정 리소스를 구분하는 식별자
- 논리적 또는 물리적 리소스 (접근할 리소스 위치를 알 수 있음)
- 인터넷, 모바일 기기 등 다양한 곳에서 사용

##### URL (Uniform Resource Locator) : 웹 주소

- 리소스 위치
- URI가 서브넷



#### 어노테이션을 이용한 서블릿 맵핑

- web.xml에서 여러 서블릿 맵핑 설정 시 복잡
- 서블릿 클래스에서 직접 어노테이션으로 서블릿명을 설정하면 가독성도 좋고 편리
- @WebServlet을 이용해서 서블릿 맵핑 구현
- 어노테이션이 적용되는 클래스는 반드시 HttpServlet 클래스를 상속 받아야 함

<img width="422" alt="image-20220628173718753" src="https://user-images.githubusercontent.com/101630615/176135462-8921bbd4-be4b-421b-8f17-cb2bc1643d9b.png">



### 서블릿 요청 API

#### 서블릿 기본 기능

- (1) 클라이언트로부터 요청을 받음
- (2) 데이터베이스 연동과 같은 비즈니스 로직을 처리함
- (3) 처리된 결과를 클라이언트에 응답



(1) 클라이언트로부터 요청을 받음

- 서블릿 요청과 응답 수행 API 
- javax.servlet.http 패키지에 포함
- 요청과 관련된 API
  - ``javax.servlet.http.HttpServletRequest`` 클래스
- 응답과 관련된 API
  - ``javax.servlet.http.HttpServletResponse`` 클래스



<img width="418" alt="image-20220628173654875" src="https://user-images.githubusercontent.com/101630615/176135454-4f2ba873-e9f2-4291-893a-cbdeda56f278.png">



#### ``<form>`` 태그로 서블릿 요청

- 서블릿 데이터를 웹 브라우저를 통해서 전송하는 방법
- ``<form>`` 태그를 사용해서 브라우저에서 서블릿으로 사용자의 요청이나 데이터를 전송
- ``<form>`` 태그
- action 속성 : 서블릿 또는 JSP 이름 지정
- method : GET 또는 POST (디폴트 : GET)
- ``<input>`` 태그
- 데이터 입력 받아서 전송
- name 속성 사용





##### 서블릿에서 클라이언트의 요청 받기

- ``HttpServletRequest`` 클래스의 여러 가지 메소드를 이용해서 전송된 데이터를 받음 

- ``<form>`` 태그로 전송된 데이터를 받아오는 메소드



<img width="700" alt="image-20220628173802858" src="https://user-images.githubusercontent.com/101630615/176135464-7c2ffb24-9301-4dd9-a88d-3a36a3701661.png">



#### Get 방식

- 데이터를 전송할 때 데이터가 URL 뒤에 name=value 형태로 전송
- 여러 개의 데이터를 전송할 때는 &로 구분해서 전송
- 전송 데이터 노출 : 보안 취약
- 전송 데이터 길이 제한 : 최대 255자 
- 기본 전송 방식
- 서블릿에서는 doGet() 이용해서 데이터 처리 
- 웹 브라우저에서 직접 url에 입력해서 doGet() 메소드 호출 가능



#### Post 방식

- 데이터를 전송할 때 TCP/IP 프로토콜 데이터의 HEAD 영역에 숨겨서 전송됨
- 보안에 유리
- 전송 데이터 길이 : 용량이 무제한
- 서블릿에서는 doPost() 메소드 이용해서 데이터 처리 
- Get 방식보다 느림

***주의!***

- 폼에 입력되어 서버로 전송되는 값들은 모두 문자열로 전송 (연산이 필요한 경우 숫자로 형변환 필요)

- 1개의 값을 받을 경우 : ``getParameter()`` 메소드 사용
- 여러 개의 값을 받을 경우 (동일한 name 값이 여러 개인 경우 : checkbox name이 다 동일한 경우)
  - ``getParameterValues()`` 메소드 사용
  - 반환되는 값이 배열이므로 배열 처리해서 사용



### 서블릿 응답 처리

#### 서블릿의 응답 처리 방법

- doGet()이나 doPost() 메소드 안에서 처리함

  - ```
    javax.servlet.http.HttpServletResponse
    ```

  - 객체를 이용함

- 클라이언트에게 전송할 데이터 타입 인코딩

  - ```
    response.setContentType(“text/html;charset=utf-8”);
    ```

- MIME-TYPE

  - 미리 지정해놓은 데이터 종류로 서블릿에서 브라우저로 전송 시 설정해서 사용함
  - HTML로 전송 시 : text/html
  - 일반 텍스트로 전송 : text/plain
  - XML 데이터로 전송 : application/xml

- 클라이언트(웹 브라우저)와 서블릿의 통신은 자바 I/O의 스트림 이용

  - PrintWriter 클래스 사용

    - ```
      PrintWriter out = response.getWriter();
      
      out.print(data);
      ```

  - // data : 웹 브라우저로 보내는 데이터







#### 서블릿의 응답 처리 순서



<img width="300" alt="image-20220628173815159" src="https://user-images.githubusercontent.com/101630615/176135467-11edd227-c7e1-4118-8b62-3139402b7cde.png">





#### ``doGet()`` /`` doPost()`` 방식 둘 다 처리

-	일반적으로 ``doHandle()`` 또는 ``doProcess()`` 메소드를 새로 추가해서
-	doGet() 또는 doPost() 방식으로 요청이 들어오면
-	doGet() 또는 doPost() 메소드에서 doHandle() 호출하고 request와 response 객체 전달
-	doHandle() 메소드에서 처리

