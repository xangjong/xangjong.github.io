

# [BackEnd] JSTL





### JSTL (JSP Standard Tag Library)

- JSP 표준 태그 라이브러리
- JSP와 HTML을 같이 사용함으로써 가독성이 떨어지는 것을 보완하고자 만들어진 태그 라이브러리
- JSP 페이지 내에서 자바 코드를 사용하지 않고 태그를 사용하도록 함
- JSP 페이지의 로직을 담당하는 부분인 제어문 및 데이터베이스 처리 등을 표준 커스텀 태그 제공
- 사용하기 위해서는 라이브러리 별도 필요

```jsp
<%@ taglib uri=”..” prefix=”” />
```



##### JSTL 다운로드

1. [https://tomcat.apache.org](https://tomcat.apache.org)
2. Taglibs -> 파일 4개 다운로드 
3. C:\apache-tomcat-9.0.64\lib 폴더에 저장
4. 이클립스 종료했다가 새로 열기



### JSTL 라이브러리 : 5개의 라이브러리로 구성

<img width="452" alt="image-20220701000809283" src="https://user-images.githubusercontent.com/101630615/176719991-45279c63-7753-4144-bc80-3d75b2d26a9b.png">

### Core (코어)

- ``URI : http://java.sun.com/jsp/jstl/core``
- prefix : c
- 제공 기능
  - 변수의 선언 및 삭제 등의 변수와 관련된 작업
  - if, for 문 등과 같은 제어문
  - url 처리 및 그밖에 예외처리 및 화면 출력

#### Core 태그 

##### ``<c:set>``

- JSP의 setAttribute()와 같은 역할. (page|request|session|application) 범위의 변수(속성)를 설정

##### ``<c:remove> ``

- JSP의 removeAttribute()와 같은 역할. (page|request|session|application) 범위의 변수(속성)를 제거

#####  ``<c:out> ``

- -화면 출력. JSP의 표현식 대체

#####  ``<c:redirect> ``

- response.sendRedirect()를 대체하는 태그로 지정한 다른 페이지로 이동

##### ``<c:if>``

- 조건문을 사용할 때 씀 : else문 없을 때

```jsp
<c:if test=”${조건식}” [scope] />
```



##### ``<c:choose>``

- 자바의 switch 문과 같지만, 조건에 문자열 비교도 가능하고 쓰임의 범위가 넓음. 서브 태그로 ``<when>``과 ``<otherwise>``를 가짐 
- else 가 필요할 때

```jsp
<c:choose>
		<c:when test=”조건식1”>내용1</c:when>
<c:when test=”조건식2”>내용1</c:when>
<c:otherwise>내용n</c:otherwise>
</c:choose>
```



##### ``<c:when>``

- choose의 서브 태그로 조건의 비교 시에  조건을 만족한 경우에 사용

##### ``<c:otherwise>``

- 조건을 만족하지 못한 경우에 사용

#####  ``<c:forEach> ``

- 객체 전체에 걸쳐 반복 실행을 할 때 사용

#####  ``<c:forToken> ``

- 자바의 StringTokenizer 클래스를 사용하는 것과 같음

##### ``<c:catch>``

- body 위치에서 실행되는 코드의 예외를 잡아내는 역할을 담당

#####  ``<c:import> ``

- 웹 애플리케이션 내부의 자원 접근은 물론이고, http, ftp 같은 외부에 있는 자원(html, jsp등)을 가져옴

#####  ``<c:param> ``

- 파라미터사용시 필요. ``<import>``태그의 URL뒤에 파라미터로 붙여서 사용되기도 함 

#####  ``<c:url> ``

- 쿼리 파라미터로 부터 URL을 생성

##### ``<c:forEach>``

- 반복문 수행

```jsp
<c:forEach  var=”변수명” begin=”시작값” end=”마지막값” step=”증가값” varStatus=”반복상태변수명”>
```

- varStatus : 반복상태 속성 지정 
  - Index
    - items에서 정의한 항목을 가리키는 index 번호
    - 기본 0부터 시작
    - begin=1로 하면 index도 1부터 시작
  - count : 몇 번째인지 표시. 1부터 시작 
  - first : 첫 번째이면 true
  - last : 마지막 반복이면 true



#### 포매팅 태그 라이브러리

- 숫자 및 날짜와 관련된 포매팅 태그 라이브러리
- 라이브러리 : format
- prefix : fmt
- uri : ``http://java.sun.com/jsp/jstl/fmt``
- 형식
  - ``<fmt:formatNumber>``
  - ``<fmt:formatDate>``
  - ``<fmt:timeZone>``

