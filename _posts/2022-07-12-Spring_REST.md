# [Spring]  REST



### REST & Ajax

>  #### REST 란?

##### 브라우저에서 페이지 요청 시

- PC에서는 페이지 전체를 다시 전송해서 표시해도 문제 없지만
- 스마트폰 등의 모바일 기기에서는 기존 화면은 그대로 유지하면서 필요한 내용만 추가해서 화면에 표시
  - 모바일 기기가 유선 기기보다 네트워크 전송량이 떨어지므로 현재 화면은 그대로 유지하면서 필요한 데이터만 전송 받아 빠르게 표시하기 위해
- 따라서 데이터만 전송하는 기능의 표준화 필요성이 대두 되었는데 REST 방식이 그 대안으로 사용됨



#### REST (Representational State Transfer)

- URI가 고유한 리소스를 처리하는 공통 방식
- 예 : /board/112로 요청할 경우
  - 게시글 중 112번째 글 의미 
- REST 방식으로 제공되는 API를 REST API (또는 RESTful API)라고 함
- 트위터와 같은 Open API에서 많이 사용됨



#### 스프링에서 REST 방식의 데이터 처리

- 스프링 3버전 
  - @ResponseBody 어노테이션 지원
  - 메소드 레베 : 메소드 위에 붙임
- 스프링 4버전
  - @RestController 어노테이션 이용 : 권장
  - 컨트롤러 레벨 
    - REST 기능을 하는 컨트롤러에 붙임
    - 모든 메소드에 적용



### Synchronous (동기식) 통신 vs Asynchronous (비동기식) 통신

#### Synchronous (동기식) 통신

- Request를 보내고 Request에 대한 Response를 받는 것으로 두 서버 사이의 Transaction을 맞추는 통신 방식
- Request를 보낸 Thread는 Response가 도착하기 전까지는 아무 것도 하지 못하는 Block 상태가 됨을 의미
- Request1 -> Response1, Request -> Response2
- 요청과 응답값의 순서를 보장하고, 보낸 요청에 대한 처리 결과 값을 보장받을 수 있기 때문에

- Response에 대한 처리 결과를 보장받고 처리해야 되는 서비스에 적합



#### Asynchronous (비동기식) 통신

- Request를 보내고 아직 Request에 대한 Response를 받지 않고도 다른 일 처리 가능한 통신 방식
- 처리 속도가 빠름
- Response에 대한 처리 결과를 보장받고 처리해야 되는 서비스에는 적합하지 않음

##### 비동기 통신을 하기 위해서는

- 클라이언트에서 서버로 요청 메시지를 보낼 때, 본문에 데이터를 담아서 보내야 하고, 
- 서버에서 클라이언트로 응답을 보낼때에도 본문에 데이터를 담아서 보내야 함
- 이 본문이 바로 body에 해당
- 즉, 요청 본문은 requestBody, 응답 본문은 responseBody를 담아서 보냄
- ``@RequestBody`` 어노테이션과 ``@ResponseBody`` 어노테이션이 각각 HTTP 요청 바디를 자바 객체로 변환하고, 자바 객체를 다시 HTTP 응답 바디로 변환
- ``@ResponseBody``가 붙은 파라미터에는 HTTP 요청의 본문 body 부분이 그대로 전달





#### Ajax (Asynchronous JavaScript and XML)

- 클라이언트에서 비동기 방식으로 자바스크립트를 이용하여 화면 전환 없이 서버 측에 데이터를 요청할 때 사용 
- TEXT, HTML, XML, JSON 등의 데이터 처리 가능
- 웹 서버 환경에서 실행



#### Ajax 관련 메소드



<img width="600" alt="image-20220712092525169" src="https://user-images.githubusercontent.com/101630615/178438432-f0a53e60-b71f-4027-9fbb-b808c99c6fa3.png">





<img width="600" alt="image-20220712092540644" src="https://user-images.githubusercontent.com/101630615/178438448-01ed2dda-8f05-4120-911f-e801fcb0904e.png">



#### $.ajax() 메소드

- 사용자가 지정한 URL 경로에 있는 파일의 데이터를 전송하고
- 입력한 URL 경로의 파일로부터 요청한 데이터를 불러오는데 사용
- 불러올 수 있는 외부 데이터는 텍스트, HTML, XML, JSON 유형 등 다양



<img width="600" alt="image-20220712092557014" src="https://user-images.githubusercontent.com/101630615/178438451-51824b49-e0df-4bc1-baa5-5668e1882c44.png">







### 검색 기능 2가지 방법

#### (1) 방법1

- ``Ajax / @ResponseBody`` 사용
- 컨트롤러에서 Ajax로 ArrayList 반환
- Ajax에서 자바스크립트로 출력 

```javascript
success:function(resul){
// result가 ArrayList를 받음 : 배열
배열 처리 (복잡)
}
```



#### (2) 방법2 
- ``@ResponseBody`` 없이 뷰 페이지 반환하고
- Ajax에서 현재 페이지에 결과 뷰페이지를 삽입하는 식으로 변경

```java
<div id=”searchResultBox”></div>
$(‘#searchResultBox’).html(result);
```

- JSTL 사용하는 JSP 페이지로 출력



##### 컨트롤러에서 Ajax로 ArrayList 반환 시 ``<dependency>`` 추가

``jackson-databind``

<img width="500" alt="image-20220712101043552" src="https://user-images.githubusercontent.com/101630615/178438455-acffa93e-6c9b-4f5e-a58c-0072f1add77c.png">



소스코드

```jsp
<dependency>
	<groupId>com.fasterxml.jackson.core</groupId>
	<artifactId>jackson-databind</artifactId>
	<version>2.13.3</version>
</dependency>
```



#### @RestController 이용해서 REST 기능 구현

- 컨트롤러 레벨 
  - REST 기능을 하는 컨트롤러에 붙임
  - 모든 메소드에 적용
- 컨트롤러에서 브라우저로 기본형 데이터, VO 객체의 속성값, Map에 저장된 데이터 등의 데이터 전송 가능



#### @Controller vs @RestController 

- @Controller : 결과를 뷰 페이지(jsp)로 표시
  - 뷰 페이지 이름을 반환
- @RestController
  - 별도의 뷰를 제공하지 않은 채 데이터 전달
