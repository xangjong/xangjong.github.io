



# [BackEnd] JSP



### JSP (Java Server Page)
- 서버 사이드 스크립트 언어
- Java 기반으로 HTML 문서 내에 자바코드를 삽입해서
- 웹 서버에서 동적으로 웹 페이지를 생성해서 클라이언트에게 반환
- JSP를 통해 HTML과 동적으로 생성된 컨텐츠를 혼합해서 사용
- Servlet을 보완한 스크립트 방식 표준 
  - Servlet 기능 + 추가 기능
- JSP는 실행되면 Servlet(.java)으로 변환되어 컴파일되서 클래스(.class) 파일로 만들어져 실행
- View를 담당하는 페이지로 사용



#### JSP와 서블릿과 차이점

- JSP
  - HTML 내부에 Java 소스코드가 들어 있는 형식
  - 사용하기 편리 : 쉬움
- Servlet
  - Java 코드 내에 HTML 코드 포함
  - 읽고 쓰기 불편



#### JSP 페이지의 구조

- 정적페이지 + 동적페이지 
- 정적 페이지 구현 : 	HTML 태그
- 동적 페이지 구현 : 스크립트 사용
- <%@ %>
- <% %>
- <%! %>
- <%= %>



#### JSP 페이지의 기본 구성 요소

- JSP 페이지 내용
  - HTML 문서 내용 / JSP 태그 / 자바 코드

#### JSP 페이지 구성

- 지시어 : page, include, taglib
- 스크립트 요소
  - 선언문 
  - 표현식
  - 스크립트릿
- 액션 태그

##### JSP 태그

- <% 로 시작하고 %> 로 종료
- @, !, =, -- 문자를 추가하여 태그의 의미 부여



<img width="500" alt="image-20220629202108780" src="https://user-images.githubusercontent.com/101630615/176425437-0728a5ac-1230-4100-b9bf-218c3cd8490a.png">



**지시어**

- JSP 페이지의 전체적인 속성을 지정할 때 사용

- JSP 컨테이너에게 전달하는 JSP 페이지 관련 메시지

```jsp
<%@ 지시어 속성1=값, 속성2=값, ….  %>
```

<img width="500" alt="image-20220629202117297" src="https://user-images.githubusercontent.com/101630615/176425449-659f41dd-8d72-4bd2-a33e-e77cad2dd11c.png">



**page 지시어 : <%@ page ... %>**

- JSP 페이지에 대한 속성 설정 



**include 지시어** 

- <%@ include file = "포함될 파일의 url" %>
- 공통적으로 포함될 내용을 가진 파일을 해당 JSP 페이지 내에 삽입하는 기능을 제공 
- 복사 & 붙여넣기 방식으로 두 개의 파일이 하나의 파일로 합쳐진 후 하나의 파일로서 변환되고 컴파일



**taglib 지시어**

- <span style= color:red><%@ </span> <span style=color:purple>tagline</span> prefix="c" uri="http:....%>"
- 표현 언어(EL : Expression Language),  JSTL(JSP Standard Tag Library)를 JSP 페이지 내에 사용 



### JSP 페이지의 스크립트 요소

#### 선언문 (Declaration)

- JSP 페이지의 멤버 필드 선언 또는 메소드를 정의할 때 사용
- 선언문에서 선언된 변수는 페이지 전체에서 사용 가능 (전역 변수 의미)
- 형식 : <%!  선언 %>

```jsp
예 : <%!  int a = 20; %>
<%!
		int a = 10;
		String str = “문자열”;
	%>
```



#### 표현식 (Expression)

- 변수 값, 계산 결과, 함수 호출 결과를 직접 출력하기 위해 사용
- <%= 식 %>

- <%= 변수명 %>

```jsp
<%= 3*5 %>
<%!  String name = “홍길동”;   %>
<%= name %>
```



#### 스크립트릿 (Scriptlet)

- 자유롭게 자바 코드를 기술할 수 있는 영역
- ``<% 자바코드 %>``
- 스크립트릿에서 선언된 변수는 지역 변수의 개념
  - 선언된 이후부터 사용 가능



#### JSP 내장 객체

- 내장 객체
  - 클라이언트에서 웹 서버에게 JSP 페이지를 요청하면 자동으로 생성
  - 객체 생성하지 않고 바로 사용 가능
- 내장 객체 종류 
  - 입출력 : request / response / out 
  - 서블릿 : page / config
  - 컨텍스트 : session / application / pageContext
  - 예외 처리 : exception





<img width="500" alt="image-20220629202214137" src="https://user-images.githubusercontent.com/101630615/176425452-65f9cbbf-aacf-454b-8779-178328379538.png">





#### request 객체의 파라미터 관련 메소드 



<img width="600" alt="image-20220629202227061" src="https://user-images.githubusercontent.com/101630615/176425457-650ade3d-3a55-487f-8645-12cb0cfba420.png">

- HTML 태그의 name 속성 값을 받음

```html
<input type="text" name="name">
```

