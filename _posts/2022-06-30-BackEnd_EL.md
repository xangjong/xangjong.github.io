

# [BackEnd] EL



### EL (Expression Language)

- 표현 언어

- 자바 코드가 들어가는 표현식을 좀 더 편리하게 사용하기 위해 JSP 2.0부터 도입된 데이터 출력 기능

- 표현식 또는 액션 태그 대신 값을 표현

  ```jsp
  <%= 값 %>   -=> ${값}
  parameter : ${ param.이름 }
  ```




#### EL 연산자

- 산술 연산자 : +, -, *, /, %, (div, mod)
- 관계 연산자 : >, >=, <, <=, ==, !=
  - (gt, ge, lt, le, eq, ne)
- 논리 연산자 : &&, ||, !, (and, or, not)
- 조건 연산자 : 수식 ? 참일때 값 : 거짓일때 값
- empty 연산자
  - 값이 null 이거나 길이가 0이면 참 (true)
  - ${empty 변수} : 변수가 null 이거나 0이면 참
  - ${not empty 변수} 
    - 변수가 null이 아니거나 0이 아니면 참

***주의! : EL 주석 처리***

```jsp
<%-- 	${"hello" + "world" }   --%>
<!-- 	${"hello" + "world" }   -->
```



### EL 내장 객체

![image-20220701000717161](BackEnd_EL.assets/image-20220701000717161.png)







#### pageContext 내장 객체

- 컨텍스 이름 (프로젝트명) 출력
- ``getContextPath()`` 메소드 이용해서 컨텍스트 이름 가져오기

```jsp
${pageContext.request.contextPath} 

ex) 
<a href="/JSP01/el/login.jsp">로그인</a>
<a href=”<%=request.getContextPath()%>/el/login.jsp”>로그인</a>
<a href="${pageContext.request.contextPath}/el/login.jsp">로그인</a>
```





#### 표현 언어로 바인딩 속성 출력

- request, session, application 내장 객체에 속성을 바인딩한 다른 서블릿이나 JSP에 전달 가능
- 자바 코드 사용하지 않고 바인딩된 속성 이름으로 바로 값 출력

```jsp
request.setAttribute(“바인딩이름”, 값);
=> ${바인딩이름}
```





### 스코프 (scope) 우선순위

- request, session, application 내장 객체에는 데이터를 바인딩해서 다른 JSP로 전달
- 각 내장 객체에 바인딩하는 속성 이름이 같은 경우
- 각 내장 객체에 지정된 출력 우선순위에 따라 순서대로 속성에 접근
  - page < request < session < application 
- pageScope : 현재 페이지 영역의 변수
- requestScope : 이전 페이지에서 받아온 영역의 변수 
- sessionScope : session 영역의 변수
- applicationScope : application 영역의 변수

