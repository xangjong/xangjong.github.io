



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



#### response 객체

- JSP 페이지에서 처리한 결과를 웹 브라우저에 응답할 때 사용
- 헤더 설정, 코드 상태, 쿠키 등 정보 포함되어 있음
- 응답 콘텐츠 설정, 응답 헤더 설정, 상태 코드 설정과 관련된 메소드 제공

<img width="600" alt="image-20220701004711859" src="https://user-images.githubusercontent.com/101630615/176721174-bdb61cc2-7dff-441b-93e2-3ec7d87dd200.png">





#### out 객체

- 웹 서버에서 웹 브라우저에게 출력 스트림으로 응답하기 위해 사용
- ``out.println(“출력 문자열”);``
- 표현식 <%= 출력문자열 %>과 동일
- println() : 줄바꿈 적용되지 않음 
- print()와 동일한 결과 (스페이스 한 칸 정도 차이)
- 줄바꿈 하기 위해서는 ``<br>`` 태그 사용



### 액션 태그

- JSP 페이지 내에서 어떤 동작을 지시하는 태그
- 어떤 동작 또는 액션이 일어나는 시점에 페이지와 페이지 사이에서의 제어 이동 
- 또는 다른 페이지의 실행 결과를 현재 페이지에 포함하는 기능 제공



### 액션 태그 종류

##### include 액션 태그 : ``<jsp:include>``

- 다른 페이지의 실행 결과를 현재 페이지에 포함시킬 때 사용

- 페이지를 모듈화할 때 사용

  ```jsp
  <jsp:include page=”포함될 페이지” flush=”true” />
  ```

- page 속성 : 결과가 포함될 페이지면

- flush 속성

  - 포함될 페이지로 제어가 이동될 때 
  - 현재 포함하는 페이지가 지금까지 출력 버퍼에 저장한 결과를 처리하는 방법을 결정
  - true
    - 현재 페이지가 지금까지 버퍼에 저장한 내용을 웹 브라우저에 출력하고 버퍼를 비움



<img width="600" alt="image-20220701004744519" src="https://user-images.githubusercontent.com/101630615/176721193-3c800480-21a8-409c-a68a-18fdb3af2c2f.png">



<img width="500" alt="image-20220701004753544" src="https://user-images.githubusercontent.com/101630615/176721211-8cc99244-e228-447b-9c99-9b6da973d674.png">





##### forward 액션 태그 : ``<jsp:forward>``

- 현재 페이지에서 다른 특정 페이지로 전환

- 웹 페이지 간의 제어를 이동시킬 때 사용

  ```jsp
  <jsp:forward page=”포워딩할 JSP 페이지” />
  ```

  

##### param 액션 태그 : ``<jsp:param>``

- 이동하는 페이지에 파라미터 값을 전달할 때 사용

##### useBean 액션 태그 : ``<jsp:useBean>``

- 자바빈을 JSP 페이지에서 이용할 때 사용
- DTO / VO에 해당

##### setProperty 액션 태그 : ``<jsp:setProperty>``

- 프로퍼티의 값을 세팅할 때 사용
- setter

##### getProperty 액션 태그 ``<jsp:getProperty>``

- getter



### 자바빈 (JavaBeans)

- DTO / VO와 같은 개념
- 데이터를 다루기 위해 자바로 작성되는 소프트웨어 컴포넌트로 재사용 가능
- 입력 폼의 데이터와 데이터베이스의 데이터 처리 부분에서 활용
- 클래스로 작성
  - 멤버 필드로 속성 (property)이 있고
  - 멤버 메소드로 Getter/Setter 메소드 포함
  - setXXX() : 프로퍼티에 값 저장
  - getXXX() : 프로퍼티 값 반환
- 액션 태그를 이용해서 빈 사용
- 속성 접근 제어자는 private
- Getter/Setter 메소드와 클래스는 public 



#### 자바빈 관련 액션 태그

##### useBean 액션 태그 : ``<jsp:useBean>``

- 자바빈을 JSP 페이지에서 사용할 때 사용

```jsp
 <jsp:useBean id=”” class=”” scope=”” />
```



<img width="500" alt="image-20220701004807031" src="https://user-images.githubusercontent.com/101630615/176721226-e8d1bc0f-c181-4717-9a52-5e29f2f03bb2.png">



##### setProperty 액션 태그 : ``<jsp:setProperty>``

- 프로퍼티(속성) 값을 설정할 때 사용
- 데이터 설정(저장)

<img width="500" alt="image-20220701004814321" src="https://user-images.githubusercontent.com/101630615/176721232-5e156fe9-207b-4feb-90a8-850252f17351.png">





##### getProperty 액션 태그 : ``<jsp:getProperty>``

- 프로퍼티의 값을 얻어낼 때 사용



<img width="500" alt="image-20220701004826090" src="https://user-images.githubusercontent.com/101630615/176721240-273dc227-fbc1-4770-a98d-9a7a5a7a3f3d.png">

#### 모든 속성을 한꺼번에 설정

 form의 ``<input>`` 태그 속성명을 클래스 필드명과 동일하게 지정하고 
``<jsp:setProperty property="*".. />``로 설정



