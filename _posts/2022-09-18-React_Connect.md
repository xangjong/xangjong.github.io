# [React] 스프링 + DB연동(MyBatis)



## (1) 리액트 + 스프링 연결 테스트

-	스프링 부트 프로젝트 생성
  -	``@RestController``인 ReactController 생성
-	리액트 프로젝트 생성
  -	axios로 http://localhost:8080 접속해서 결과 받아서 출력
-	오류 발생 (CORS 오류)
  -	리액트 3000 포트 사용 스프링 8080 포트 사용하는 다른 사이트(출처)
-	오류 해결 : WebConfig.java 설정
-	실행해서 오류없이 반환 값 잘 받아오는지 확인



#### CORS 

- Cross-Origin Resource Sharing

- 추가 HTTP 헤더를 사용해서

- 한 출처(origin)에서 실행 중인 웹 애플리케이션이

- 다른 출처(origin)의 선택한 자원에 접근할 수 있는 권한을 부여하도록

-	브라우저에게 알려주는 체제



##### 스프링 부트 프로젝트 생성

-	프로젝트명 : spring_boot_react
-	Name : spring_boot_react
-	Group : com.spring_boot_react
-	Artifact : project
-	Package : comspring_boot_react.project
  -	JDBC API
  -	MyBatis Framework
  -	MYSQL Driver
  -	Spring Web



<hr>



#### 리액트 프로젝트 생성

- 프로젝트명 : react-spring-app

- 비동기 통신 라이브러리 axios 설치

  -	``npm install axios``

- components 폴더 / AxiosString.js 컴포넌트 생성

  

#### 비동기 작업

-	네트워크 송수신 과정에서 시간이 걸리기 때문에 작업을 즉시처리하지 못하고 응답을 기다렸다가 전달받은 데이터를 처리하는 방식
-	시간이 많이 걸리는 작업 
  -	서버로부터 데이터를 요청하고 기다리는 작업
-	서버에게 API 호출해서 결과를 수신
-	이런 과정에서 해당 작업을 비동기적으로 처리



#### 콜백 지옥 (Callback Hell)

-	비동기 호출이 자주 일어나는 프로그램에서 발생하는 문제
-	함수의 매개변수가 전달되는 콜백 함수가 반복되어서 코드 들여쓰기 수주의 깊이가 무한 반복되는 경우
-	해결 방안 : Promise 사용
  -	비동기 메소드에서 동기 메소드처럼 값을 반환해서
  -	비동기 연산이 종료된 이후의 결과 값을 처리하기위한 처리기를 연결해서 문제를 해결
  -	대기 / 이행 / 거부 
  -	Promise … then()




#### Axios

-	자바스크립트 라이브러리 중 하나인 Fetch API와 같은 비동기 통신 라이브러리
-	리액트에서는 Axios를 더 많이 사용
-	Promise 기능을 쉽게 해주는 문법으로 async / await 사용
-	이렇게 하면 Promise 끝날 때까지 기다리고, 결과값을 특정 변수에 저장할 수 있음



##### async : 함수 앞에 붙여 사용

-	async를 사용하게 되면 함수는 항상 Promise를 반환



##### await 

-	async 함수 안에서만 사용 가능
-	함수 안에서 await을 만나면 Promise가 처리될때까지 대기
-	await을 이용하면 콜백함수 처리 없이 비동기 처리 가능
	



##### useEffect()

- 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook

- 설정한 함수를 컴포넌트가 화면에 맨 처음 렌더링 할 때만 실행하고 업데이트 될 때는 실행하지 않으려면, 두 번째 파라미터를 빈 배열 사용 ([])

- 렌더링될 때 한 번만 호출

- 서버를 호출하거나 컴포넌트가 마운트되면서 1회만 수행되는 동작이 필요할 때 사용

  



## (2) 백엔드 프로그램 준비



-	spring_boot_mybatis의 product 관리 코드 사용
-	컨트롤러만 새로 작성 (기존 컨트롤러 코드 복사해서 일부 수정)
-	Service / DAO / VO / Mapper 그대로 사용



## (3) 리액트 홈/메뉴 작성

-	라우팅 기능 추가
  -	``npm install react-router-dom``
  -	index.js , ``<BrowerRouter>``로 변경
  -	Home.js와 Top.js(메뉴) 컴포넌트 생성




## (4) 리액트에서 스프링 백엔드를 통한 CRUD 기능 구현



### 생성할 컴포넌트

1. 상품 정보 조회
   - ``<ProductList>``
   - ``<ProductListItem>`` : 행 (반복 : map() 안에서)

2. 상품 상세 정보 조회 : ``<ProductDetailView>``
3. 상품 정보 등록 : ``<ProductInsert>``
4. 상품 정보 수정 : ``<ProductUpdate>``



#### 1. 상품 정보 조회

-	스프링에 컨틀롤러 추가하고
-	리액트에서 ``<ProductList>`` 컴포넌트 생성
-	``<ProductList>``에서 받아온 데이터를 
-	테이블 형태로 출력
-	반복되는 각 행은 ``<ProductListItem>`` 컴포넌트로 출력
-	``<ProductList>``에서 map() 함수 사용해서 ``<ProductListItem>``으로 출력



##### 날짜 포맷 변경

-	moment 라이브러리 설치
  -	``npm install moment``




#### 2. 상품 상세 정보 조회 :`` <ProductDetailView>``

-	컨트롤러에 추가
-	상품번호에 링크 추가
-	Top.js에 ``<Route>`` 추가
-	``<ProductDetailView> ``컴포넌트 추가



#### 3. 상품 정보 등록 : ``<ProductInsert>``

- 컨트롤러에 추가
- ``<productInsert>`` 컴포넌트 추가
- Top.js에 ``<Route>`` 추가



#### 4. 상품 정보 수정 : ``<ProductUpdate>``

- 상품번호 전달하고, 해당 상품정보 받아와서, 입력된 값으로 변경
- ProductDetail + ProductInsert : url이 update로 요청해서 DB 작업을 update 처리
- 컨트롤러 추가
- ``<ProductUpdate>`` 컴포넌트 추가
- ``<ProductList>``에 수정 항목 추가
- ``<ProductListItem>``에도 수정 항목 추가
- Top.js에 ``<Route>`` 추가 
  - 주의 : 파라미터 있음



#### 5. 상품 정보 삭제 : ``<ProductDelete>``

- 컨트롤러에 추가
- ``<ProductList>``에 삭제 항목 추가
- ``<ProductListItem>``에도 삭제 항목 추가
  - onClick 이벤트 속성 추가
- ``<ProductListItem>``에서 삭제 이벤트 처리



### 리액트 + 스프링 프로젝트 배포

- 리액트 프로젝트 빌드
  - npm run build
- build 폴더 안의 파일들을 스프링 views 폴더로 이동
  - index.html은 index.jsp로 변경
    - <%> 추가
- static 폴더 파일들은 스프링 resources/static 폴더로 이동
- 컨트롤러 생성 : index.jsp 매핑 추가
- 새로 고침 오류 처리
  - SPA의 문제
  - 웹 브라우저에서 액세스 하는 색인 파일은 index.html 하나로
  - history API를 사용해서 페이지 이동 처리
  - 새로 고침하거나 URL 직접 입력는 웹 서버에서 위치를 찾을 수 없음
  - 에러 처리 -> 에러 발생 시 index 페이지로 다시 열기
