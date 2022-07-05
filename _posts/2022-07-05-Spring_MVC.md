



# [Spring] MVC



### MVC 패턴

- 웹 애플리케이션 개발
- 화면 : 프론트엔드 개발자(디자이너)
- 비즈니스 로직 : 백엔드 개발자
- 처음부터 새로 개발하는 것이 아니라 기존의 웹 애플리케이션 개발 방법에 따라 개발
- 많이 사용하는 표준화 소스 구조를 만들어 개발 진행



#### 웹 애플리케이션 모델

- 표준화된 소스 구조
  - 모델1 방식
  - 모델2 방식



#### 모델1 방식

- 모든 클라이언트의 요청과 비즈니스 로직을 JSP가 담당
- 클라이언트 요청 -> JSP(화면 기능/로직처리) -> DAO -> 데이터베이스
- 기능 구현이 쉽고 편리
- 웹 사이트 화면 기능이 복잡해지고 화면 기능과 비즈니스 로직 기능이 섞이면서 유지보수 문제 발생
- 코드 재사용성도 떨어짐
- 비효율적



<img width="500" alt="image-20220705175158966" src="https://user-images.githubusercontent.com/101630615/177291225-9bbc8b60-4663-4147-9a3b-e9af6ca2fd96.png">

#### 모델2 방식 (MVC 패턴)

- 모델1 방식의 단점 보완
- 웹 애플리케이션의 각 기능을 분리해서 구현
  - 클라이언트 요청 처리
  - 응답 처리
  - 비즈니스 로직 처리
- 각 기능이 분리되어 모듈화되어 있으므로 모듈별 개발이 가능
- 모듈을 비슷한 프로그램 개발에 사용할 수 있어 코드 재사용성도 높음
- 응용프로그램 확장성 및 이식성이 좋아짐
- 개발 후 서비스 제공 시 유지보수 편리
- 현재 모든 웹 프로그램은 모델2 방식으로 개발

##### MVC 패턴

- M : Model (DTO / DAO)
- V : View (JSP 페이지)
- C : Controller



<img width="500" alt="image-20220705175328047" src="https://user-images.githubusercontent.com/101630615/177291238-a11970c2-c3e3-4d22-b9f2-65a7d66e8956.png">









#### FrontController 패턴
- 모든 클라이언트 요청을 한 곳에서 처리하도록 하나의 대표 컨트롤러사용
- 별도의 클래스를 추가하지 않고 Front Controller가 다 처리 (FrontController 내용이 길고 복잡해짐)
- 클라이언트의 요청을 한 곳으로 집중시켜서 효율적으로 개발 및 유지보수 가능





#### Command 패턴

- FrontController가 모든 클라이언트 요청을 직접 다 처리하지 않고
- 각 작업에 해당되는 클래스가 처리
- FrontController가 수행하던 작업을 각 클래스로 분산 처리
- 각 클래스는 통일된 형식(규격)으로 처리하도록 interface로 구현



<img width="500" alt="image-20220705175341997" src="https://user-images.githubusercontent.com/101630615/177291241-36c04817-3124-4199-881e-6aeafc9a8e59.png">



### Spring MVC 구조

- <span style=color:red>DispatcherServlet (프론트 컨트롤러)</span>
  - 컨트롤러 선택  (HandlerMapping을 통해)해서 요청을 컨트롤러에게 전달
  - View 검색 (ViewResolver)해서 해당되는 View로 서비스 응답





<img width="600" alt="image-20220705175351856" src="https://user-images.githubusercontent.com/101630615/177291247-1b370b61-d879-4215-a692-ea75bc9124b7.png">



#### Spring MVC Project 

- 프로젝트 생성
- 패키지 입력
  - 패키지 이름에서 맨 마지막에 있는 단어가 컨텍스명이 됨
  - com.spring_mvc.<span style=color:red>project</span>
  - ``http://localhost:8080/project``

- 기본 컨트롤러와 뷰 페이지 자동 생성되어 있음
  - 컨트롤러 : HomeController.java
  - 뷰 페이지 : home.jsp
- 전체 구조 파악
  - 컨트롤러 위치
  - View 페이지 위치
- pom.xm (설정 파일)
  - Java Version 11
  - Spring Framework 5.2.22.RELEASE
  - Maven compiler : 1.8
- 오류 : Maven / Update Project / Force update 체크
- 프로젝트 설정 변경 (Properties)
  - Java Compiler : 11로 변경
  - Java Build Path : Workspace default JRE (jdk-11.0.15)
  - Project Facets 
    - Java Version : 11
    - Runtimes : Apache Tomcat v9.0 체크
  - web.xml 확인
    - DispatcherServlet 
    - 스프링 컨테이너 설정 파일 위치 확인
  - servlet-conext.xml (스프링 컨테이너 설정 파일)
    - VeiwResolver





### 스프링의 디렉터리 구조

<img width="700" alt="image-20220705175402137" src="https://user-images.githubusercontent.com/101630615/177291250-ca4c2691-2e69-4865-bc69-43835e4870dc.png">



### url에서 context명 확인

- ``http://localhost:8080/project/``
- server.xml에서 ``<Context path=”/project” … />``
- 프로젝트에서 패키지명 :  ``com.spring_mvc.project``



### View의 요청 경로(path) 설정

- 원하는 경로로 View 경로 설정

- views 폴더 안에  원하는 폴더 생성하고 .jsp 페이지 저장



### <span style=color:blue>스프링 컨트롤러</span>

- 스프링 컨트롤러는 빈으로 등록되어야 하며
- 비즈니스 로직이 실행되지 위해 비즈니스 객체를 의존성 주입(DI) 해야 함
- @Controller 어노테이션 사용
- @RequestMapping 어노테이션을 사용하여 url 맵핑 
- 요청 처리 메소드 구현
  - @RequestMapping 아래에 작업을 처리할 메소드 추가
  - 필요한 클래스(객체)는 파라미터로 받아서 사용
- 뷰 페이지 이름 반환 
  - return “뷰페이지 이름민(확장자 없음)”;





### 컨트롤러 클래스 작성

- (1) 클래스 생성하고 @Controller 어노테이션 붙임
- (2) @RequestMapping 어노테이션을 사용하여 요청 경로 지정
- (3) 요청 처리 메소드 구현
- (4) 뷰 페이지 이름 반환



***주의!!!***
<span style=color:red>프로젝트 절대 복사 X</span>



### 데이터 전달

- (1) Controller  => View 페이지
- (2) View => Controller 
  - Form을 통한 데이터 전달 : Form 데이터 처리 
  - url을 통한 데이터 전달



#### (1) Controller  => View 페이지

##### View 페이지로 데이터 전달 방법

- Model 사용
- ModelAndView 사용



##### Model 사용
- Model 인터페이스
- Model Attribute 추가하기 위해 고안
- key/value 형태로 값을 임시 저장
- Controller에서 Model에 데이터를 저장하고
- View 이름을 return 하면
- View 페이지로 Model이 전달되고
- View 페이지에서 key를 사용해서 Model에 저장된 Data 사용



##### Model 사용 형식

- 요청 처리 메소드에서 Model 객체를 파라미터로 받아서 
  - ``public String home(Locale locale, Model model) ``
-  ``addAttribute()`` 메소드로 key / value 설정
  - ``model.addAttribute("serverTime", formattedDate );``
- (return 되는 뷰페이지로 전달)
  - ``${serverTime}``



##### ModelAndView 사용

- ModelAndView 클래스 사용
- 데이터와 뷰 둘 다 설정
- 반환값으로 ``ModelAndView`` 객체 반환

```java
ModelAndView mv = new ModelAndView();

mv.addObject(“name”, “홍길동”); // 데이터 설정

mv.setViewName(“showInfo2”); // 뷰 이름 설정

return mv; // ModelAndView 객체 반환
```

- Model과 ModelAndView 같이 사용 가능
- 동일한 key(이름)이 있는 경우 ModelAndView가 우선



