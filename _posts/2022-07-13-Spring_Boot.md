

# [Spring] 스프링 부트



### 스프링 부트 (Spring Boot) 

> 스프링 프레임워크를 사용하는 프로젝트를 아주 간편하게 설정할 수 있는 스프링 프레임워크의 서브프로젝트



#### 스프링 부트의 특징
- XML 기반 설정 과정 없이 간단히 프로젝트를 시작할 수 있음
- 메이븐의 pom.xml 파일에 의존성 라이브러리의 버전을 일일이 지정하지 않아도 됨 (스프링 부트가 권장 버전 관리)
- 단독 실행되는 스프링 애플리케이션 구현 가능
- 프로젝트 환경 구축에 필요한 서버 외적인 툴들이 내장되어 있어서 별도 설치 필요 없음
  - 톰캣 내장되어 있음



<hr> 



### 스프링 부트 프로젝트 생성 과정

#### 1. 스프링 부트 프로젝트 생성

- File / New . Spring Starter Project
- (1) 프로젝트명 / Group / Artifact / 패키지명
- (2) Dependencies 선택
  - SQL : JDBC API / MyBatis Framework / MySQL Driver
  - Web : Spring Web
  - Java Version : 11
  - Package : War





<img width="600" alt="스크린샷 2022-07-12 오전 10 33 27" src="https://user-images.githubusercontent.com/101630615/178656667-e5e95210-bc26-4581-979d-214919295f6a.png">



<hr>



#### 2. 프로젝트 생성 후 확인

- (1) pom.xml 내용 확인

  - java.version / jdbc / mysql-connector / tomcat

- (2) 자동 생성된 클래스 파일 확인

- ``ServletInitializer.java``

  - 스프링 부트 애플리케이션을 web.xml 없이 톰캣에서 실행하게 해주는 클래스
  - 따라서 스프링 부트에는 web.xml, context.xml 설정 파일 없음

- ``…….Application.java ``

  - ``@SpringBootApplication`` 붙어 있음
  - 스프링 부트 애플리케이션으로 설정하는 어노테이션
  - main() 메소드 포함

  

  

  <img width="582" alt="스크린샷 2022-07-12 오전 10 33 59" src="https://user-images.githubusercontent.com/101630615/178656680-b8831d93-d417-4c8c-8a14-cc63850808a6.png">

  

  

  

  <img width="582" alt="스크린샷 2022-07-12 오전 10 34 02" src="https://user-images.githubusercontent.com/101630615/178656683-2edda5d5-7378-4eda-9266-8a6028ff4675.png">







<hr>



#### 3. 스프링 설정 파일

- application.properties 파일이 자동 생성됨
- (내용이 없는 빈 파일로 생성)
- 추가할 내용
  - 포트 번호
  - 데이터베이스 연결 정보
  - mapper.xml 위치 지정 
    - src/main/resources 파일에 생성할 것임
- 여기서 컨트롤러 추가하고 (“/”) 실행시켜서 오류 있는지 확인





#### application.properties db 설정

src -> main -> resources -> application.properties 

본인의 Db 설정에 맞춰서 입력



application.properties에서 한글을 사용하지 않으면 주석은 ``#``을 사용

<img width="564" alt="스크린샷 2022-07-12 오전 11 23 29" src="https://user-images.githubusercontent.com/101630615/178656694-257d82f7-0e70-4957-a1b9-2ae7fcc0f701.png">

소스 코드

```java
# 포트 번호
server.port=8080
  
# db connection
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver  #db driver
spring.datasource.url=jdbc:mysql: # localhost:3306/springdb
spring.datasource.username=root  # db 아이디 
spring.datasource.password=1234  # db 패스워드
```



src -> main -> java -> (프로젝트 생성 시 입력한 패키지) -> 클래스 생성 -> 클래스 명 HelloController  추가 



<img width="831" alt="스크린샷 2022-07-12 오전 11 20 00" src="https://user-images.githubusercontent.com/101630615/178656692-4e9dcef7-9f6d-4d42-9a05-11814ce39c0b.png">



warn 오류는 패키지 mapper를 설정하지 않아 나는 오류입니다.

이는 후에 패키지 mapper 설정을 하면 해결됩니다.

정상적으로 되었다면 결과는 아래와 같습니다 

<img width="831" alt="스크린샷 2022-07-12 오전 11 17 08" src="https://user-images.githubusercontent.com/101630615/178656690-7a7ad0ac-f377-4dee-8c3a-214b70a2f219.png">

***Port 8080 is already in use***

가장 자주 나는 톰캣 에러입니다.

포트번호 8080을 이미 사용중라 에러가 나는 것입니다.

포트번호 8080을 점유중인 프로세스를 찾아 제거한 후 다시 실행하면 됩니다.



맥의 명령어입니다. 

``sudo lsof -i: 포트번호`` 

포트번호를 조회하는 명령어입니다.

명령어 입력 후 계정 비밀번호를 입력하면 포트번호 8080을 점유하고 있는 프로세스가 나옵니다.

``kill`` : 점유하고 있는 프로세스 번호





<img width="712" alt="스크린샷 2022-07-12 오전 11 58 42" src="https://user-images.githubusercontent.com/101630615/178656715-2589dea1-2992-43d6-abb0-5e7edc496011.png">



저는 1993 프로세스가 8080을 점유하고 있어 kill 하였습니다.





<hr>



#### 4. JSP 뷰 설정

- 스프링 부트는 JSP 뷰가 기본이 아니기 때문에
- JSP 뷰를 사용할 경우 추가 설정 필요
- application.properties 파일에 JSP 설정 추가
- pom.xml 의존성 라이브러리 추가
- src/main/webapp 폴더에 WEB-INF/views 폴더 추가
- hello.jsp 생성하고
- 컨트롤러에서 @RequestMapping 추가해서 hello.jsp 실행되는지 확인
- 스프링 부트에서 리소스 파일 경로 확인



#### JSP 설정



<img width="564" alt="스크린샷 2022-07-12 오전 11 33 10" src="https://user-images.githubusercontent.com/101630615/178656699-914235a3-5a54-4f53-88d8-a1a996456737.png">



jsp view 소스코드 

```
# jsp view 
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp
```



<hr>



#### pom.xml 의존성 추가

pom.xml 클릭 후 하단 메뉴 Dependencies 클릭 Add 



<img width="531" alt="스크린샷 2022-07-12 오전 11 34 20" src="https://user-images.githubusercontent.com/101630615/178656701-6b0cdd82-4492-4abb-b2b8-3eb84736bf51.png">





##### javax.servlet jstl



<img width="526" alt="스크린샷 2022-07-12 오전 11 35 25" src="https://user-images.githubusercontent.com/101630615/178656705-59315373-8f43-40f7-bf80-885447ca5d1a.png">



검색 결과 로딩이 오래 걸리나 창이 나오지 않는 분들은 아래 소스 코드를 

pom.xml의 소스의 ``</dependencies>``안에 추가하시면 됩니다.



소스 코드

```
<dependency>
	<groupId>javax.servlet</groupId>
	<artifactId>jstl</artifactId>
</dependency>
```



<hr>


##### tomcat-embed-jasper



<img width="526" alt="스크린샷 2022-07-12 오전 11 36 51" src="https://user-images.githubusercontent.com/101630615/178656706-89c5d7b5-c328-4da9-bf74-381cf2b2fc6c.png">





소스 코드

```
<dependency>
	<groupId>org.apache.tomcat.embed</groupId>
	<artifactId>tomcat-embed-jasper</artifactId>
</dependency>
```



<hr>


입력이 잘 되었다면 아래 결과창과 같습니다.



<img width="453" alt="dependency_result" src="https://user-images.githubusercontent.com/101630615/178656722-7e3a66d7-2d83-4a10-ae4a-df9e9126cf32.png">





##### jsp view 경로 설정에 맞게 파일을 생성합니다.

src -> main -> webapp -> 폴더 생성(WEB INF) -> 폴더 생성(views) 



<img width="351" alt="스크린샷 2022-07-12 오전 11 39 43" src="https://user-images.githubusercontent.com/101630615/178656710-f20f605e-a456-44db-9964-44efc15ca86f.png">





<hr>



view 폴더 안에 jsp 파일 추가 (파일명 :hello.jsp)



<img width="712" alt="스크린샷 2022-07-12 오후 12 09 32" src="https://user-images.githubusercontent.com/101630615/178656717-96fd7739-d8be-42ca-ae6c-7f9c3b582372.png">

파일을 생성했으니 컨트롤러에서 hello 페이지로 이동하는 ``@RequestMappong``을 작성합니다.



<img width="712" alt="스크린샷 2022-07-12 오후 12 10 27" src="https://user-images.githubusercontent.com/101630615/178656719-05536ec8-c5ec-4ac4-9d59-3afe48b94e47.png">

소스 코드 

```java
@RequestMapping("/hello")
	public String hello(Model model){
		model.addAttribute("message","안녕하세요");
		return "hello"; // 뷰 페이지 이름 : hello.jsp
}
```



실행 : Run As / Spring Boot App

웹 브라우저에 url 직접 입력 : ``http://localhost:8080/hello``



아래와 같은 결과 창이 나타납니다.



<img width="395" alt="image-20220713141551550" src="https://user-images.githubusercontent.com/101630615/178656724-006501f0-b1b9-425a-a5da-18c7db81cf29.png">





#### 5. DB 연동 CRUD 기능 구현

- spring_mvc_mybatis 에서 product 코드는 그대로 사용 (일부 경로 수정)
- 파일 위치 주의



##### (1) 패키지 생성 

- controller / dao / model / service
- 클래스 / 인터페이스 파일 (mapper 제외)
  - VO / service / DAO / Controller
- 복사 시 주의! - 이전 패키지 import 삭제할 것



##### (2) mapper 파일 폴더 생성

- src/main/resources 폴더에 mappers 폴더 생성하고, 그 안에 product 폴더 생성

- product 폴더 안에 ProductMapper.xml 파일 복사

  - DAO/VO 경로 수정

- application.properties에 mapper 위치 설정

- `````
  mybatis.mapper-locations=classpath:mappers/**/*.xml
  `````



##### (3) …Application.java 클래스에 추가

- 컴포넌트 클래스(Controller와 Service)에 대해 추가
- ``@ComponentScan``
- ``@MapperScan``
- 추가하지 않으면 bean이 없다는 오류 발생



<img width="500" alt="image-20220713142558283" src="https://user-images.githubusercontent.com/101630615/178657352-0726bf0a-6dc1-4472-9efb-2966b951f0fa.png">



##### (4) view 페이지 복사

- product 폴더 복사
- index.jsp 복사
- 모든 경로 (요청 경로) 변경



<img width="300" alt="image-20220713141823339" src="https://user-images.githubusercontent.com/101630615/178656728-42759e71-0523-4749-85f3-1d8553d34a7a.png">



##### (5) HelloController 삭제 

- (삭제) 또는 내용 주석 처리)

##### (6) js 폴더 생성

- src/main/resources/static 폴더에 js 폴더 복사

##### (7) 외부 경로 설정 : 상품 이미지 출력

WebConfig 클래스 생성 

- MVC 프로젝트에서 spring-context.xml에 설정한  내용 추가

```
<resources mapping="/images/**" location="file:///C:/springWorkspace/product_images/" />
```

- WebMvcConfigurer 인터페이스 구현
- 맵핑 이름과 이미지 위치 설정



<img width="500" alt="image-20220713141833378" src="https://user-images.githubusercontent.com/101630615/178656730-6e8cabc5-b71b-474e-ba7e-0f70f184a66a.png">
